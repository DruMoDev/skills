---
name: explicar-en-web
description: Convierte una explicación que no se entiende (un concepto, unas finanzas, un contrato, un código, un cambio en un proyecto o una conversación entera) en una sola página web visual e interactiva, con un ejemplo práctico que puedes tocar. Úsala cuando el usuario diga que no entiende algo, pida "explícamelo en una web", "hazme una web de esto", "con dibujos" o "en HTML", o quiera compartir lo hablado en una página.
---

# Explicar en una web

El texto te lo cuenta; una web te lo enseña. El objetivo es que la persona **entienda en un minuto** lo
que no entendía, sin saber nada antes, y que pueda **tocarlo**: cambiar un número y ver qué pasa.

Una web que solo es el mismo texto con colores no enseña nada nuevo. Si no hay nada que dibujar ni que
tocar, dilo y explícalo mejor en texto.

## 1. Entiende qué no se entiende

- Localiza el punto exacto de la duda: qué parte, qué palabra, qué paso. Si no está claro, haz **una**
  pregunta corta antes de construir nada; si está claro, no preguntes.
- Saca los hechos de la conversación, del documento o del código que te den. Lo que no sepas seguro,
  márcalo como "suposición" en la página. Nunca inventes cifras para que el ejemplo quede bonito: si el
  ejemplo usa datos inventados, di que son de ejemplo.

## 2. Qué lleva la página

Por este orden, y solo lo que aporte:

| Bloque | Qué responde | Forma |
|---|---|---|
| La idea | ¿Qué es y para qué me sirve? | Dos frases llanas: el problema y la respuesta |
| El mapa | ¿Dónde pasa esto? ¿Qué piezas hay? | Un dibujo de 4 a 8 cajas con flechas que dicen qué se mueve |
| Antes y después | ¿Qué cambia? | Lo mismo a los dos lados, con la diferencia resaltada |
| El ejemplo que se toca | ¿Qué pasa si lo uso de verdad? | Un caso concreto con controles: barra, botones, campos |
| Lo que queda | ¿Qué es seguro y qué no? | Etiquetas cortas: "comprobado", "suposición", "depende de ti" |
| Detalles | Fórmulas, letra pequeña, código, fuentes | Desplegables cerrados por defecto |

**El ejemplo que se toca es lo más importante.** Elige un caso realista con valores concretos
(10.000 € al 5 % durante 20 años; un contrato con permanencia de 12 meses; una función con una lista de
3 elementos) y deja que la persona cambie las entradas y vea el resultado al momento, con el paso
intermedio visible, no solo el final. Si el orden importa, usa botones de "siguiente paso".

**Para compartir una conversación:** resume lo decidido, no la transcripción. Una portada con la
conclusión, las decisiones con su porqué, los pasos siguientes y, si los hay, los números con su
ejemplo tocable.

## 3. Cómo se escribe

- En el idioma de la persona (español por defecto) y con palabras de la calle. El término técnico va
  entre paréntesis la primera vez, nunca como etiqueta suelta de un dibujo.
- Frases cortas. Nada de párrafos largos en la vista principal: lo largo, a los desplegables.
- Verbos de acción en los dibujos ("cobra la cuota", "guarda el archivo") en vez de nombres internos.
- El color ayuda pero nunca es la única pista: acompáñalo de texto o icono.

## 4. Cómo se construye

- **Un solo archivo HTML** con el CSS y el JS dentro. Sin librerías ni fuentes externas ni paso de
  compilación: tiene que abrirse con doble clic, sin internet, y verse igual en el chat.
- Dibujos en **SVG en línea**, uno por idea, con textos grandes que no se salgan de las cajas (si un
  texto es largo, la caja crece; nunca encojas la letra). Una sola dirección de lectura.
- Se lee bien en el **móvil** (una columna por debajo de 700 px), los controles se usan con teclado y
  la página impresa sigue teniendo sentido.
- Seguridad: si metes texto que viene de fuera, escápalo (en JS, `textContent`, nunca `innerHTML`).
  Nunca pongas contraseñas, claves, datos personales ni nada privado; usa datos de ejemplo.

## 5. Mi estilo

Ajusta esta sección a tu gusto y la skill lo hará siempre así a la primera:

- Diseño limpio y claro: fondo claro, un color de acento, mucho aire, esquinas redondeadas.
- Más dibujo que texto: si algo se puede enseñar con un diagrama, va en diagrama.
- Títulos que dicen la conclusión ("Tu dinero se duplica en 14 años"), no el tema ("Interés compuesto").

## 6. Antes de entregarla

- Prueba cada control: mueve la barra, pulsa cada botón y comprueba que el número y el dibujo cambian
  de verdad y que el resultado es correcto (haz la cuenta aparte).
- Mira que no haya textos cortados, cajas que se pisen ni scroll horizontal en móvil.
- Si puedes abrirla en un navegador, hazlo y mira una captura de escritorio y otra de móvil.

## 7. Entrega

- **En un chat** (Claude, ChatGPT, Gemini...): muéstrala como artefacto o en el Canvas para que se abra
  ahí mismo. Si la herramienta puede publicarla con un enlace (por ejemplo, Sites en ChatGPT), ofrécelo
  cuando la persona quiera compartirla.
- **En un agente con archivos** (Claude Code, Codex...): guárdala en una carpeta temporal del proyecto
  que no se suba al repositorio, con un nombre que diga el tema (`explicacion-interes-compuesto.html`),
  y da la ruta.
- Acaba con una sola frase: lo que la persona debería haber entendido. Y pregunta si quiere otro
  ejemplo o más detalle en alguna parte.
