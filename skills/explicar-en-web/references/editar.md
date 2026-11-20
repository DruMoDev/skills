# Modo editar y devolver

Sirve cuando la persona tiene que poner orden con sus manos y es más rápido en una pantalla que
dictándolo: priorizar una lista de tareas, repartir cosas en columnas, quitar filas que sobran,
corregir textos o valores de una configuración.

## La página

- Una vista que encaje con la tarea. Para ordenar o priorizar, por defecto **columnas** tipo tablero
  (por ejemplo "Hoy", "Esta semana", "Más adelante", "Descartar"), con orden dentro de cada columna: es
  más intuitivo que una lista larga. Lista única solo si pide un ranking estricto del 1 al N; **tabla**
  con celdas editables y casilla para descartar filas cuando son datos. Todo se mueve arrastrando y
  también con botones o teclas (sin ratón); en móvil, las columnas se apilan.
- Cada elemento enseña lo justo para decidir (título, una línea de contexto, la etiqueta que importe) y
  se puede desplegar para ver más.
- Campo de nota por elemento y otro general.
- Contador visible de lo que ha cambiado ("3 movidas, 2 descartadas") y botón para deshacer todo.
- Si los datos vienen de un fichero de configuración o de un `.env`, los secretos **no se meten** en la
  página: se enseñan como `[OCULTO]` y no se pueden editar desde aquí.

## Lo que devuelve

El botón "Enviar cambios" devuelve `kind: "edicion"` con `data` = la lista o la tabla final más un
resumen de cambios (`movidos`, `descartados`, `editados`, `notas`), usando los identificadores
originales para que puedas aplicarlo sin ambigüedad. Cómo se devuelve: [devolver.md](devolver.md).
Antes de aplicar un cambio que borre o mande algo, confírmalo con la persona.
