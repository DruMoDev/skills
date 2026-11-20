# Modo prototipo

Sirve para ver y ajustar algo visual antes de programarlo de verdad: una animación, unos colores, unos
tamaños, una tarjeta, una pantalla. La persona mueve controles, ve el cambio al momento y te devuelve
los valores que le gustan.

## La página

- **Vista previa grande** a un lado (arriba en móvil) y los controles al otro.
- **Valores de partida = los que hay ahora** en su proyecto (léelos del código), no unos inventados,
  para que vea primero lo que ya tiene.
- Cada control enseña su **valor actual con unidades** (`240 ms`, `16 px`, `80 %`) y cambia la vista al
  momento, sin botón de "Aplicar".
- Botón **"Volver al principio"** que restaura los valores de partida.
- Un panel con los valores como código listo para copiar (variables CSS, JSON o lo que use su proyecto),
  que se actualiza al mover los controles.
- **Contenido realista**: sus textos, sus datos, sus nombres. Si algo se mueve en la realidad, el
  prototipo se mueve; respeta `prefers-reduced-motion` con una alternativa sin movimiento.
- Si son varias variantes de la misma pieza, ponlas en rejilla como en [comparar.md](comparar.md).

## Lo que devuelve

El botón "Enviar valores" devuelve `kind: "valores"` con
`data: {objetivo: "<qué pieza y dónde>", valores: {...}, nota: "..."}`. Cómo se devuelve:
[devolver.md](devolver.md). Al recibirlo, aplica esos valores en su código y dile qué fichero has
tocado.
