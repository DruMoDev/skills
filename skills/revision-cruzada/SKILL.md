---
name: revision-cruzada
description: Pide a un modelo de otra empresa (GPT por defecto, vía OpenCode) que revise el trabajo que acabas de hacer, sin que pueda tocar nada, y aplica solo lo que compruebes que es verdad. Úsala al terminar una tarea que importe (una app, una función nueva, un arreglo delicado), antes de dar algo por bueno, o cuando quieras una segunda opinión sobre una decisión. Admite rondas de seguimiento con el mismo revisor.
---

# Revisión cruzada entre IAs

Un modelo que no ha hecho el trabajo, y que además es de otra empresa y está entrenado
distinto, ve los fallos que el autor ya no ve. Pasa incluso cuando el revisor es peor modelo.
Tú (el agente que ha hecho el trabajo) eres el **autor**; el otro modelo es el **revisor**.

El revisor **solo lee**: no puede editar ficheros, ni navegar, ni ejecutar nada que no sea
de lectura. Tú decides qué se aplica.

## Requisitos (compruébalos antes de empezar)

1. **OpenCode instalado.** `opencode --version`. Si no está, pide permiso al usuario e instálalo:
   - macOS / Linux: `curl -fsSL https://opencode.ai/install | bash` (o `brew install opencode`)
   - Windows: `npm install -g opencode-ai`
   Si tras instalar no aparece el comando, prueba con la ruta completa (`~/.opencode/bin/opencode`).
2. **Sesión iniciada con la cuenta del revisor.** Para GPT con la suscripción de ChatGPT (Plus o
   superior): `opencode auth login`, elegir **OpenAI** y el método de **ChatGPT Plus/Pro**; se abre el
   navegador y el usuario acepta. Es una sola vez. Si no puedes completarlo tú (pide elegir en un menú
   o confirmar en el navegador), díselo al usuario y espera a que lo haga.
3. **Modelo disponible.** `opencode models openai` lista los modelos de su cuenta. Usa el GPT más
   potente que aparezca (por ejemplo `openai/gpt-6.1-sol`) y guarda el elegido en la sección
   "Configuración" de abajo para no volver a buscarlo.

### Configuración

- Revisor: `openai/<el GPT más potente de la lista>`
- Esfuerzo: `high` (opciones: `low`, `medium`, `high`, `max`)

Otros revisores, mismo método: cambia el modelo (`opencode auth login` con su proveedor y
`opencode models <proveedor>`). Por ejemplo Gemini (`google/...`) o modelos chinos como DeepSeek,
Qwen, Kimi o GLM. La regla es que el revisor sea **de otra empresa** que tú.

## Cuándo usarla

- Al terminar algo que importa: una app, una función nueva, un arreglo con riesgo, una migración.
- Antes de decir al usuario que algo "está listo".
- Para una segunda opinión sobre una decisión (modo **consulta**, abajo).
- **No** para cambios triviales (un texto, un color, una errata): gasta suscripción y tiempo para nada.

## Paso 1: escribe el contexto

Crea `.revision/contexto.md` en la carpeta del proyecto. Es lo que hace buena la revisión:

- El objetivo en dos líneas y lo que pidió el usuario, con sus palabras.
- Las decisiones ya tomadas con el usuario y por qué (para que el revisor no las vuelva a discutir).
- Los ficheros que has creado o cambiado. Si el proyecto usa git, basta con indicar el rango
  (`git diff <base>..HEAD` o los cambios sin commitear); si no, lista las rutas.
- Lo que ya has comprobado (pruebas, lo que abriste en el navegador) para que no lo repita.
- Dónde tienes **menos confianza**. Es lo más valioso que le puedes dar.

No le pidas "encuentra fallos": eso le empuja a inventarlos.

## Paso 2: lanza al revisor

Prepara el prompt en `.revision/prompt.md` con la plantilla de "Prompt del revisor" (abajo),
rellenando el contexto. Después ejecuta, desde la carpeta del proyecto:

```bash
OPENCODE_CONFIG_CONTENT='{"agent":{"revisor":{"mode":"primary","description":"revisor de solo lectura","permission":{"edit":"deny","webfetch":"deny","external_directory":"deny","task":"deny","bash":{"*":"deny","cat*":"allow","ls*":"allow","head*":"allow","tail*":"allow","wc*":"allow","grep*":"allow","rg*":"allow","find*":"allow","git diff*":"allow","git log*":"allow","git show*":"allow","git status*":"allow"}}}}}' \
opencode run --pure --agent revisor -m <modelo> --variant high --format json --dir . \
  "$(cat .revision/prompt.md)" < /dev/null > .revision/ronda-1.jsonl
```

Importante:

- **`< /dev/null` es obligatorio**: sin él, `opencode run` se queda esperando para siempre.
- Una revisión tarda de 3 a 10 minutos. Usa un tiempo límite de al menos 30 minutos o ejecútalo en
  segundo plano y sigue con otra cosa; nunca dejes que tu herramienta lo corte a los 2 minutos.
- En Windows (PowerShell) la variable se pone antes con `$env:OPENCODE_CONFIG_CONTENT='...'`.

Al acabar, lee `.revision/ronda-1.jsonl`: cada línea es un evento JSON. La respuesta es el texto de
los eventos `"type":"text"` del último mensaje, y el `sessionID` sirve para las rondas siguientes.
Si hay un evento `"type":"error"`, para y cuéntaselo al usuario.

## Paso 3: comprueba cada hallazgo antes de tocar nada

El revisor es **una segunda opinión, no una autoridad**.

- Por cada hallazgo, lee el código o reprodúcelo tú. Si es real y entra en lo que te pidieron,
  arréglalo. Si no lo es, descártalo y apunta el motivo concreto.
- Sus preguntas son preguntas para ti: respóndelas desde el código o pásaselas al usuario.
- Que no encuentre nada es un resultado bueno y normal, no una señal de que ha revisado mal.

## Paso 4: informa al usuario

Breve y en este orden: qué modelo revisó, su veredicto, cada hallazgo con lo que hiciste
(**arreglado** / **descartado porque...**) y las sugerencias que merezcan la pena.
Si la revisión no terminó (tiempo agotado, error), dilo así: "revisión sin confirmar", nunca
"no ha encontrado nada".

## Rondas de seguimiento

Para que el revisor compruebe tus arreglos o discutirle un hallazgo, continúa **la misma sesión**
(recuerda todo lo que leyó) con `-s <sessionID>` y un mensaje nuevo:

```bash
OPENCODE_CONFIG_CONTENT='<el mismo de arriba>' \
opencode run --pure --agent revisor -m <modelo> --variant high --format json --dir . -s <sessionID> \
  "Arreglado el 1 en <fichero>. Descartado el 2 porque <evidencia>. Vuelve a comprobarlo." \
  < /dev/null > .revision/ronda-2.jsonl
```

Para como mucho a las **3 rondas**, o antes si ya no aporta nada nuevo. Si seguís en desacuerdo
después de darle tu evidencia, enséñale al usuario las dos posturas y que decida él; no entres en bucle.

## Modo consulta (segunda opinión sobre una decisión)

Mismo comando, pero el prompt es una pregunta neutral con las opciones que barajas y los ficheros
que debería leer. Pídele una respuesta directa, una recomendación, su nivel de confianza y los riesgos.
Si la pregunta va dirigida ("¿verdad que X es mejor?"), te devolverá el eco.

## Prompt del revisor

```text
Eres un revisor independiente del trabajo que ha hecho otra IA en este proyecto. Eres un modelo
distinto a propósito: tu valor está en ver lo que el autor no ve. No editas nada; informas.

## Qué se ha hecho
<objetivo, ficheros cambiados o rango de git>

## Contexto del autor
<decisiones ya tomadas con el usuario, lo ya comprobado, lo que queda fuera>
No vuelvas a discutir una decisión ya tomada salvo que tengas evidencia nueva y concreta de que causa
un fallo.

## Dónde mirar con más cuidado
<dónde el autor tiene menos confianza>

## Cómo revisar
1. Entiende primero qué tenía que hacer y lee los ficheros tú mismo.
2. Busca fallos reales: comportamiento incorrecto con alguna entrada o situación, casos límite,
   datos que se pierden, errores que se tragan en silencio, cosas que se rompen fuera de lo cambiado.
3. Puedes leer ficheros y usar comandos de solo lectura. No puedes editar.

## Qué devolver
- Un hallazgo necesita un caso concreto (esta entrada o situación -> este resultado incorrecto) y la
  evidencia que has leído (fichero:línea). Si no puedes describir cómo falla, no es un hallazgo: como
  mucho una pregunta o una sugerencia.
- No encontrar nada es un resultado normal y bueno. No inventes problemas ni rellenes con detalles
  de estilo.
- Responde en este formato:

VEREDICTO: sin_hallazgos | hallazgos | bloqueado (no has podido revisar; explica por qué)
RESUMEN: 2-4 frases.
HALLAZGOS: (uno por bloque)
  - [grave|medio|leve] (confianza alta|media|baja) fichero:línea. Título.
    Cómo falla: ...
    Evidencia: ...
    Arreglo sugerido: ...
SUGERENCIAS: pocas y concretas, o "ninguna".
PREGUNTAS: dudas reales para el autor, o "ninguna".
COMPROBADO: qué has verificado y cómo.
```

## Si eres GPT (Codex u OpenCode) y quieres que revise Claude

El método es el mismo con los papeles al revés: el revisor se lanza con Claude Code en modo no
interactivo y solo con herramientas de lectura:

```bash
claude -p --tools "Read,Grep,Glob" --permission-mode dontAsk < .revision/prompt.md > .revision/ronda-1.txt
```

## Errores típicos

- `opencode: command not found`: no está instalado o no está en el PATH (ver Requisitos).
- Error de autenticación: `opencode auth login` otra vez. No reintentes en bucle; avisa al usuario.
- El modelo no existe en su cuenta: `opencode models openai` y elige otro de la lista.
- Se queda colgado sin hacer nada: falta `< /dev/null`.
- Respuesta vacía o tiempo agotado: revisión sin confirmar. Díselo al usuario tal cual.
