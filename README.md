
<p align="center">
<img src="https://www.fiec.espol.edu.ec/sites/all/themes/fiec/fiec.png" alt="Logo FIEC-ESPOL" height="150px">
</p>

# Plantilla de Trabajo Final de Grado para las carreras de ESPOL

[![made-with-latex](https://img.shields.io/badge/Made%20with-LaTeX-1f425f.svg)](https://www.latex-project.org/) [![GitHub release](https://img.shields.io/github/release/hc2twv/templateTFG.svg)](https://GitHub.com/hc2twv/templateTFG/releases/) [![GitHub watchers](https://img.shields.io/github/watchers/hc2twv/templateTFG.svg?label=Watch&style=social)](https://GitHub.com/hc2twv/templateTFG)

Esta plantilla está basada en la creada por *jonatanlv* y tiene algunas modificaciones.

Para empezar a usarla simplemente escribe
```bash
git clone https://github.com/hc2twv/templateTFG.git
```
desde una terminal y comenzar a modificar los archivos o directamente con el botón de `Clonar o descargar` en la página del proyecto o mediante el enlace: https://github.com/hc2twv/templateTFG/archive/master.zip.

Si detectas un fallo o crees que algo se puede/debe hacer de otra forma te invito a colaborar en la plantilla, cualquier sugerencia será bienvenida.

# Compilación en OVERLEAF 
- `Compilador`: XelaTex
- `Archivo Principal`: TemplateTFG.tex


## Estructura de la plantilla simplificada

Los comandos `\frotmatter`, `\mainmatter`, `\appendix` y `\backmatter` simplifican la estructura del TFG ya que hacen los cambios en los estilos automáticamente:
- `\frontmatter`: Numeración de páginas usando números romanos y los capítulos no son numerados. En esta parte irán (en este orden) la página de título, agradecimientos, resumen, abstract y los índices: de figuras, de tablas y de algoritmos.
- `\mainmatter`: Se reinicia la numeración de páginas, se usan números arábigos y los capítulos están numerados. En esta parte va el cuerpo de la tesis.
- `\appendix`: La numeración de las páginas continúa sin ninguna modificación y los capítulos pasan a numerarse con letras desde la A. En esta parte se incluye material no esencial para la exposición principal. Algunos ejemplos pueden ser detalles de implementación no relevantes, anexos incluidos en el trabajo...
- `\backmatter`: La numeración de las páginas continúa sin ninguna modificación y los capítulos dejan de numerarse. Aquí suele incluirse únicamente el índice de términos (si se usa) y la bibliografía (esto no puede faltar).

## Compilación separada del documento

A medida que la tesis va aumentando en tamaño, y sobre todo tras la inclusión de imágenes, el tiempo de compilado aumenta considerablemente. Lo normal, sobre todo al principio, es que la mayoría del tiempo se escriba en un solo capítulo.

La plantilla se ha estructurado de forma modular para permitir la compilación de los capítulos por separado. Para esto hemos usado el paquete `newclude` que incluye los comandos `\includeonly` y `\include*`.

Su uso es bastante sencillo, cada capítulo lo ponemos en un fichero aparte (excepto los capítulos de agradecimientos, resumen y abstract que van en un mismo fichero ya que no deben ser muy extensos). En el punto donde queramos incluir el capítulo, en el archivo principal (*TemplateTFG.tex*), usamos `\include*{nombre_fichero_sin_extension}`. Cuando queramos compilar solamente dicho capítulo, en el preámbulo usamos `\includeonly{nombre_fichero_sin_extension}`.

> **AVISO IMPORTANTE**: Cuando se usa la compilación separada, el resto de capítulos *no existen* con lo cual las referencias a dichos capítulos (los no incluidos) aparecerán con el típico **??**. Además, a veces cuando se modifica el `\includeonly` la numeración de las páginas hace saltos erróneos, los índices muestran información incorrecta,... mi consejo es que cada vez que se modifique el comando `\includeonly`, ya sea el capítulo incluido o si se quita o pone de nuevo, se haga una compilación limpia, es decir, borrar los archivos temporales y compilar.

## Referencia Cruzada

- `hyperref`: al cargar este paquete todas las referencias y los índices se convierten en hiperenlaces lo que facilita la lectura del trabajo en un ordenador.
- `tablas`: algunas simplificaciones en las tablas:
  - Los comandos para cambiar el tamaño de las fuentes en las tablas se usan sobre el entorno `tabular` en lugar de ser aplicados celda a celda.



