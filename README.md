# Introducción a la Ciencia de Datos 2026

Posgrado en Ciencias de la Computación, CICESE.  
Dr. Irvin Hussein López Nava · M.C. Joan Raygoza Romero  
Martes y jueves, 10:20 a 12:00

Este repositorio reúne las diapositivas y los notebooks del curso. Se actualiza conforme avanzan las sesiones.

## Contenido

| | |
|---|---|
| [`clases/`](clases/) | Diapositivas de cada sesión en PDF |
| [`datos/`](datos/) | Conjuntos de datos usados en los notebooks |
| `icd-NN-tema.ipynb` | Notebook de la sesión NN, en la raíz |

## Sesiones

| # | Tema | Diapositivas | Notebook |
|---|---|---|---|
| 1 | Presentación del curso · La ciencia de datos | [PDF](clases/icd-01-intro.pdf) | — |
| 2 | Datos | [PDF](clases/icd-02-datos.pdf) | [icd-02-datos.ipynb](icd-02-datos.ipynb) |

## Cómo trabajar con los notebooks

Cada notebook tiene un botón que lo abre en Google Colab. Es la vía más rápida y no requiere instalar nada; solo hay que descomentar la línea que lee el dataset desde GitHub, según se indica en el propio notebook.

Para trabajar en tu máquina, clona el repositorio y ejecuta desde la carpeta clonada, así las rutas a `datos/` funcionan sin cambios:

```bash
git clone https://github.com/husseinlopez/icd2026.git
cd icd2026
pip install -r requirements.txt
jupyter lab
```

Los notebooks se versionan **con sus salidas**, para que puedan leerse directamente en GitHub, con tablas y gráficas, sin ejecutar nada.

## Evaluación

| Rubro | Peso |
|---|---|
| Lecturas y tareas | 20% |
| Prácticas | 50% |
| Proyecto final | 30% |

Las lecturas, tareas y prácticas son obligatorias y deben entregarse en tiempo y forma. Cada lectura requiere un reporte de máximo una cuartilla. Cada práctica requiere un notebook, que se agrega al **repositorio personal de cada estudiante**, no a este. El reporte del proyecto se entrega en formato de artículo.

## Libro del curso

VanderPlas, J. (2022). *Python Data Science Handbook*, 2a edición. O'Reilly.  
Disponible en línea: https://jakevdp.github.io/PythonDataScienceHandbook/
Notebooks del libro: https://github.com/jakevdp/PythonDataScienceHandbook

## Repositorios de datos

- [Kaggle](https://www.kaggle.com/datasets)
- [UC Irvine Machine Learning Repository](https://archive.ics.uci.edu/)
- [Microsoft Research Open Data](https://www.microsoft.com/en-us/research/tools/?facet%5Btax%5D%5Bproduct_type%5D%5B%5D=dataset)

## Licencia

El repositorio mezcla material de distinta procedencia, así que la licencia se separa en tres casos.

**Código.** Los notebooks y cualquier script se distribuyen bajo la [licencia MIT](LICENSE).

**Contenido instruccional.** El texto de las diapositivas y de los notebooks se distribuye bajo [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/deed.es): puedes usarlo, adaptarlo y redistribuirlo, incluso con fines comerciales, siempre que des crédito.

**Material de terceros.** Las presentaciones incluyen figuras, gráficas, capturas y logotipos cuyos derechos pertenecen a sus autores. Ese material queda fuera de las licencias anteriores y se reproduce aquí con fines educativos, citando la fuente en la diapositiva correspondiente. Si vas a reutilizar una diapositiva completa, revisa qué contiene.

Los conjuntos de datos conservan sus propias condiciones; cada uno se documenta en [`datos/`](datos/).

## Contacto

Instructores:
hussein@cicese.edu.mx, jraygoza@cicese.edu.mx 
Ayudante:
jnavarrete@cicese.edu.mx 
