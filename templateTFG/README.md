<p align="center">
<img src="http://www.upm.es/sfs/Rectorado/Gabinete%20del%20Rector/Logos/UPM/Escudo%20con%20Leyenda/ESCUDO%20leyenda%20color%20PNG%20p.png" alt="Logo UPM" height="150px">
<img src="http://www.upm.es/sfs/Rectorado/Gabinete%20del%20Rector/Logos/FAC_INFORMATICA/FacInformatica.jpg" alt="Logo FI" height="150px">
</p>

# Plantilla TFM para el máster universitario en inteligencia artificial de la UPM

[![made-with-latex](https://img.shields.io/badge/Made%20with-LaTeX-1f425f.svg)](https://www.latex-project.org/) [![GitHub release](https://img.shields.io/github/release/jonatanlv/templateTFM.svg)](https://GitHub.com/jonatanlv/templateTFM/releases/) [![GitHub watchers](https://img.shields.io/github/watchers/jonatanlv/templateTFM.svg?label=Watch&style=social)](https://GitHub.com/jonatanlv/templateTFM)

Esta es la plantilla que yo usé parar redactar la memoria del máster universitario en inteligancia artifical (MUIA) de la UPM.

Esta plantilla está basada en la creada por *Francisco Laport López* y tiene algunas modificaciones.

Para empezar a usarla simplemente escribe
```bash
git clone https://github.com/jonatanlv/templateTFM.git
```
desde una terminal y comenzar a modificar los archivos o directamente con el botón de `Clonar o descargar` en la página del proyecto o mediante el enlace https://github.com/jonatanlv/templateTFM/archive/master.zip.

Si detectas un fallo o crees que algo se puede/debe hacer de otra forma te invito a colaborar en la plantilla, cualquier sugerencia será bienvenida.

Las principales modificaciones hechas sobre la plantilla de Francisco son las siguientes.

## `book` en lugar de `article`

La `documentClass` se declara como `book`. Esto permite usar el seccionado empezando por `\chapter`.

El comando `\chapter` no necesita redefiniciones adicionales para hacer saltos de página previos como se estaba haciendo en la plantilla original.

Además, la tabla de contenidos se ve estéticamente mejor, sin necesidad de recurrir a las mayúsculas parar resaltar los capítulos.

## Estructura de la plantilla simplificada

Los comandos `\frotmatter`, `\mainmatter`, `\appendix` y `\backmatter` simplifican la estructura del TFM ya que hacen los cambios en los estilos automáticamente:
- `\frontmatter`: Numeración de páginas usando números romanos y los capítulos no son numerados. En esta parte irán (en este orden) la página de título, agradecimientos, resumen, abstract y los índices: de figuras, de tablas y de algoritmos.
- `\mainmatter`: Se reinicia la numeración de páginas, se usan números arábigos y los capítulos están numerados. En esta parte va el cuerpo de la tesis.
- `\appendix`: La numeración de las páginas continúa sin ninguna modificación y los capítulos pasan a numerarse con letras desde la A. En esta parte se incluye material no esencial para la exposición principal. Algunos ejemplos pueden ser detalles de implementación no relevantes, anexos incluidos en el trabajo...
- `\backmatter`: La numeración de las páginas continúa sin ninguna modificación y los capítulos dejan de numerarse. Aquí suele incluirse únicamente el índice de términos (si se usa) y la bibliografía (esto no puede faltar).

## Eliminado capítulo de trámites administrativos

Este capítulo presentaba información desactualizada. Para consultar información *actualizada* relativa a los procesos de matrícula y defensa es mejor consultar directamente en la página del MUIA: http://www.dia.fi.upm.es/masteria/ o consultar a la secretaría de la ETSIInf.

## Compilación separada del documento

A medida que la tesis va aumentando en tamaño, y sobre todo tras la inclusión de imágenes, el tiempo de compilado aumenta considerablemente. Lo normal, sobre todo al principio, es que la mayoría del tiempo se escriba en un solo capítulo.

La plantilla se ha estructurado de forma modular para permitir la compilación de los capítulos por separado. Para esto hemos usado el paquete `newclude` que incluye los comandos `\includeonly` y `\include*`.

Su uso es bastante sencillo, cada capítulo lo ponemos en un fichero aparte (excepto los capítulos de agradecimientos, resumen y abstract que van en un mismo fichero ya que no deben ser muy extensos). En el punto donde queramos incluir el capítulo, en el archivo principal (*TemplateTFM.tex*), usamos `\include*{nombre_fichero_sin_extension}`. Cuando queramos compilar solamente dicho capítulo, en el preámbulo usamos `\includeonly{nombre_fichero_sin_extension}`.

> **AVISO IMPORTANTE**: Cuando se usa la compilación separada, el resto de capítulos *no existen* con lo cual las referencias a dichos capítulos (los no incluidos) aparecerán con el típico **??**. Además, a veces cuando se modifica el `\includeonly` la numeración de las páginas hace saltos erróneos, los índices muestran información incorrecta,... mi consejo es que cada vez que se modifique el comando `\includeonly`, ya sea el capítulo incluido o si se quita o pone de nuevo, se haga una compilación limpia, es decir, borrar los archivos temporales y compilar.

## Algunas mejoras menores

- `hyperref`: al cargar este paquete todas las referencias y los índices se convierten en hiperenlaces lo que facilita la lectura de la tesis en un ordenador.
- `tablas`: algunas simplificaciones en las tablas:
  - Los comandos para cambiar el tamaño de las fuentes en las tablas se usan sobre el entorno `tabular` en lugar de ser aplicados celda a celda.
  - Se introduce un nuevo entorno, `stripedtable` que pinta de diferentes colores filas alternas. Es necesario usar los comandos `\showrowcolors` y `\hiderowcolors` para que tenga efecto. Esto facilita la lectura de tablas muy anchas.
  - Se usa un ejemplo de uso del entorno `threeparttable` que sirve para incluir notas a pie de tabla en lugar de notas a pie de página.
- Se usa un ejemplo del entorno `align` que se recomienda usar en lugar de `equation`. También se han hecho algunos arreglos menores en las expresiones.

## Mejoras por hacer (ayuda bienvenida)

- Incluir `biblatex` para la gestión de bibliografías. Es mucho más cómodo que andar incluyendo las referencias una a una.
- Hacer un estilo de bibliografía UPM. Esto se escapa un poco de mis conocimientos de latex, pero estaría bien hacer algo tomando como base el paquete `biblatex-apa` (esto es completamente inútil si no se usa `biblatex`).
- Hacer algún tipo de `lint` con errores habituales. O por lo menos una lista de errores comunes, errores del tipo escribir `tabla 5.1` (incorrecto) en lugar de `Tabla 5.1`(correcto). Esto nos puede ahorrar tiempo en la fase de corrección.
