# Dibujos

Los dibujos van en **SVG dentro del HTML**, uno por idea, con un pie de texto debajo que diga qué hay
que mirar.

## Qué tipo de dibujo

| La idea es... | Dibujo |
|---|---|
| Por dónde pasa algo | Flujo: cajas y flechas de izquierda a derecha o de arriba abajo |
| Quién habla con quién y en qué orden | Secuencia: columnas por actor y pasos numerados |
| En qué situación puede estar algo | Estados: círculos y flechas con lo que provoca el cambio |
| De qué está hecho | Capas: bandas apiladas |
| Qué depende de qué | Dependencias: nodos y flechas hacia lo que se necesita |
| Cuándo pasa cada cosa | Línea de tiempo |

## Que se lea

- Una sola dirección de lectura. Como mucho unas 8 cajas por dibujo; si salen más, una vista general y
  dibujos aparte para cada parte.
- Verbos de acción en las flechas ("cobra la cuota", "guarda el archivo") en vez de nombres internos.
- **Textos que no se salgan.** Para etiquetas de más de unos 12 caracteres o de longitud variable usa
  `<foreignObject>` con un `<div>` (el texto salta de línea solo). `<text>` solo para etiquetas cortas,
  con una caja de al menos 8 px por carácter más 32 px. Si un texto es largo, la caja crece; nunca
  encojas la letra. Prueba con la etiqueta más larga que pueda salir.
- Al menos 8 px de margen dentro de cada caja y 40 px entre cajas. Las etiquetas de las flechas llevan un
  rectángulo de fondo para que la línea no las tache.
- Como mucho 3 colores con significado, y una leyenda si el color o la forma significan algo.
- `<title>` y `<desc>` en cada SVG para lectores de pantalla.
- En móvil, un dibujo ancho se apila en vertical en vez de encogerse.

## Antes y después

Lo mismo a los dos lados, con la misma escala y posición, y solo la diferencia resaltada. Si cambia el
camino, marca el punto donde se separa.
