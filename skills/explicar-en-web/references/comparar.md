# Modo comparar

Sirve para elegir entre varias formas de hacer algo: diseños, enfoques técnicos, planes, textos. La
persona ve todas a la vez, elige una (o mezcla) y te la devuelve.

## Las opciones

- **De verdad distintas.** Si dos opciones caben en la misma frase, júntalas y busca otra más distinta.
  Que varíen en varios ejes a la vez (estructura, tono, coste, riesgo), no solo en un detalle.
- Entre 2 y 6. Más de 6 no se comparan, se hojean.
- Cada opción se **enseña**, no se describe: la pantalla dibujada, el texto escrito, el diagrama del
  enfoque, el número calculado.
- La etiqueta dice qué gana y qué pierde ("la más rápida de montar, la más difícil de ampliar"), nunca
  "Opción A". Debajo, los pros y contras en una o dos líneas, y "mejor cuando...".

## La rejilla

- 2 o 3 opciones en fila, 4 en 2×2, 5 o 6 en 2×3. En móvil, una columna.
- Todas las celdas del mismo tamaño y con la misma estructura, para que no parezca que hay un orden ni
  una favorita.
- Arriba, una línea: qué se ha variado entre ellas y qué se mantiene fijo.
- No elijas tú. Si la persona pidió tu recomendación, va en una sección aparte, debajo, con su porqué.

## Lo que devuelve

Cada celda se puede marcar (una o varias) y hay un campo de nota ("me quedo con la 2 pero con el color
de la 4"). El botón "Enviar elección" devuelve `kind: "eleccion"` con
`data: {elegidas: [...], nota: "..."}`, usando el identificador y la etiqueta de cada opción. Cómo se
devuelve: [devolver.md](devolver.md).
