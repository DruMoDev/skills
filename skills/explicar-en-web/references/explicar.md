# Modo explicar

El objetivo: que la persona **entienda en un minuto** lo que no entendía, sin saber nada antes, y que
pueda **tocarlo**: cambiar un número y ver qué pasa.

## Qué lleva la página

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

## Explicar un cambio de código o un plan

- Di en qué estado está lo que explicas y no lo mezcles: **propuesto** (sale del plan; nada está hecho),
  **hecho** (sale del diff; di la rama o el commit y si hay cambios sin guardar), **comprobado** (con
  qué prueba) o **pendiente**.
- Lee el código de alrededor y quién lo usa; no te fíes de la memoria. Enlaza cada afirmación a su
  `ruta:línea` o a su fuente.
- Sigue **la misma entrada de ejemplo** por el antes y por el después, enseñando la decisión intermedia
  donde cambia el camino. Un caso límite o de error solo si hace falta para entenderlo.
- En una refactorización sin cambio visible, enseña que el resultado se mantiene; no inventes mejoras.
- Si una interacción real enviaría o cambiaría datos, simúlala y etiquétala como simulación. Una
  simulación demuestra la explicación, no que el código funcione.
- Si ya había una explicación anterior del mismo tema, actualízala o márcala como superada; no
  reutilices un dibujo viejo sin volver a comprobarlo.

## Compartir una conversación

Resume lo decidido, no la transcripción: una portada con la conclusión, las decisiones con su porqué,
los pasos siguientes y, si los hay, los números con su ejemplo tocable.

## Con fuentes

Si la explicación sale de una investigación (webs, documentos), pon al final la lista de fuentes con la
cita concreta (URL sin parámetros de seguimiento, documento y página, commit). Distingue lo oficial de
la opinión.
