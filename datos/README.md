# Conjuntos de datos

Datos usados por los notebooks del curso. Los notebooks los leen con la ruta relativa `datos/archivo.csv`, así que basta con ejecutarlos desde la raíz del repositorio clonado.

Desde Colab, el mismo archivo se lee por URL:

```python
pd.read_csv("https://raw.githubusercontent.com/husseinlopez/icd2026/main/datos/weather.numeric.csv")
```

## Inventario

### weather.numeric.csv

14 instancias, 6 atributos. Cada fila es un día descrito por sus condiciones meteorológicas y si se jugó o no.

| Columna | Escala de medición | Valores |
|---|---|---|
| Day | Identificador | 1 a 14 |
| Outlook | Nominal | sunny, overcast, rain |
| Temperature | Intervalo (°F) | 64 a 85 |
| Humidity | Razón (%) | 65 a 96 |
| Wind | Ordinal | weak, strong |
| Play | Nominal binaria, variable objetivo | True, False |

Es la versión numérica del dataset *weather* que Quinlan usó para ilustrar la inducción de árboles de decisión, y que se distribuye con Weka.

Quinlan, J. R. (1986). Induction of decision trees. *Machine Learning*, 1(1), 81-106.

Se usa en: [icd-02-datos.ipynb](../icd-02-datos.ipynb), [icd-13-arboles-decision.ipynb](../icd-13-arboles-decision.ipynb), [icd-14-aprendizaje-bayesiano.ipynb](../icd-14-aprendizaje-bayesiano.ipynb), [icd-15-aprendizaje-instancias.ipynb](../icd-15-aprendizaje-instancias.ipynb) y [icd-16-maquinas-soporte-vectorial.ipynb](../icd-16-maquinas-soporte-vectorial.ipynb)

### weather.nominal.csv

14 instancias, 6 atributos. Son los mismos días de `weather.numeric.csv`, con la temperatura y la humedad discretizadas. Es la tabla 3.2 de Mitchell (1997) y la diapositiva 20 de la sesión 13.

| Columna | Escala de medición | Valores |
|---|---|---|
| Day | Identificador | 1 a 14 |
| Outlook | Nominal | sunny, overcast, rain |
| Temperature | Ordinal | cool, mild, hot |
| Humidity | Ordinal | normal, high |
| Wind | Ordinal | weak, strong |
| Play | Nominal binaria, variable objetivo | True, False |

Se obtiene de `weather.numeric.csv` con los cortes de la versión original: la temperatura es cool hasta 69 °F, mild de 70 a 76 y hot desde 77; la humedad es high por encima de 82 %. Los nombres siguen los de `weather.numeric.csv`. La versión de Weka usa *rainy*, *windy* (TRUE/FALSE) y *yes*/*no*.

Mitchell, T. M. (1997). *Machine Learning*, capítulo 3. McGraw-Hill.

Se usa en: [icd-13-arboles-decision.ipynb](../icd-13-arboles-decision.ipynb), [icd-14-aprendizaje-bayesiano.ipynb](../icd-14-aprendizaje-bayesiano.ipynb), [icd-15-aprendizaje-instancias.ipynb](../icd-15-aprendizaje-instancias.ipynb) y [icd-16-maquinas-soporte-vectorial.ipynb](../icd-16-maquinas-soporte-vectorial.ipynb)

### weather.prueba.csv

14 instancias, 6 atributos. Días de prueba para los modelos entrenados con `weather.numeric.csv`, con las mismas columnas.

| Columna | Escala de medición | Valores |
|---|---|---|
| Day | Identificador | 15 a 28 |
| Outlook | Nominal | sunny, overcast, rain |
| Temperature | Intervalo (°F) | 66 a 88 |
| Humidity | Razón (%) | 60 a 95 |
| Wind | Ordinal | weak, strong |
| Play | Nominal binaria, variable objetivo | True (9), False (5) |

Viene del caso de estudio del curso Aprendizaje Automático Supervisado (Licenciatura en Ciencia de Datos, UABC). Sus etiquetas siguen el árbol J48 de la sesión 13 salvo en los días 18 y 27. En ese curso, los días 3 y 14 del entrenamiento tenían humedad 78 y 80 (la versión «golf» de C4.5); aquí se usan los de `weather.numeric.csv`, 86 y 91.

Se usa en: [icd-15-aprendizaje-instancias.ipynb](../icd-15-aprendizaje-instancias.ipynb) y [icd-16-maquinas-soporte-vectorial.ipynb](../icd-16-maquinas-soporte-vectorial.ipynb)


### sensores-participantes.csv · sensores-mediciones.csv

Dos tablas de un estudio ficticio de sensado con dispositivos vestibles, generadas para la sesión 3. **No corresponden a ningún estudio real y no deben usarse fuera del curso.**

Contienen defectos deliberados: cada uno ilustra un punto de la sesión y se corrige dentro del notebook.

**`sensores-participantes.csv`** — 12 instancias, 8 atributos. Una fila por participante.

| Columna | Escala de medición | Valores |
|---|---|---|
| id | Identificador, clave primaria | P01 a P12 |
| nombre | Nominal | Nombre y apellido en un solo campo |
| sexo | Nominal | F, f, Femenino, M, m, Masculino — seis niveles para dos categorías |
| edad | Razón (años) | 23 a 62; P11 sin dato |
| grupo | Ordinal | bajo < medio < alto, almacenado como texto |
| dispositivo | Nominal | Empatica E4, Actigraph GT3X, Fitbit Charge |
| fecha_registro | Intervalo | Texto en formato `dd-mm-aaaa hh:mm` |
| fc_reposo | Razón (lpm) | 61 a 80; P05 sin dato |

**`sensores-mediciones.csv`** — 11 instancias, 5 atributos. Formato ancho: una columna por día de medición.

| Columna | Escala de medición | Valores |
|---|---|---|
| id | Identificador, clave foránea | P01 a P10 y P13 |
| dia_1 … dia_4 | Razón (pasos) | 4110 a 12500 |

Los identificadores no coinciden entre las dos tablas: P11 y P12 no tienen mediciones, y P13 tiene mediciones pero no ficha de registro. Es a propósito, para que el argumento `how` de `merge` tenga consecuencias visibles.

Se usan en: [icd-03-representacion.ipynb](../icd-03-representacion.ipynb)


### cafe-calidad.csv

1339 instancias, 43 atributos. Cada fila es un lote de café verde evaluado por catadores certificados.

El notebook trabaja con 21 columnas; las 22 restantes son administrativas —número de lote, dirección y contacto de la certificadora, fechas de expiración— y no aportan al análisis. La tabla describe solo las que se usan.

| Columna | Escala de medición | Valores |
|---|---|---|
| total_cup_points | Intervalo (0 a 100) | 59.83 a 90.58, más un registro en 0; es la suma de las diez subescalas |
| species | Nominal binaria | Arabica (1311), Robusta (28) |
| country_of_origin | Nominal | 36 niveles; 1 sin dato |
| harvest_year | Intervalo (año), almacenado como texto | 46 valores distintos en formatos mezclados: `2012`, `2013/2014`, `2017 / 2018`, `4T/10`, `March 2010`, `Fall 2009`, `mmm`, `TEST`; 47 sin dato |
| variety | Nominal | 29 niveles; 226 sin dato |
| processing_method | Nominal | Washed / Wet, Natural / Dry, Pulped natural / honey, Semi-washed / Semi-pulped, Other; 170 sin dato |
| color | Nominal | Green, Bluish-Green, Blue-Green — los dos últimos son la misma categoría escrita de dos formas; 270 sin dato |
| aroma, flavor, aftertaste, acidity, body, balance | Intervalo (0 a 10) | 5.08 a 8.83 |
| uniformity, clean_cup, sweetness | Intervalo (0 a 10) | Saturadas contra el máximo: mediana 10 en las tres |
| cupper_points | Intervalo (0 a 10) | 5.17 a 10 |
| moisture | Razón (fracción) | 0 a 0.28; 264 registros en 0 |
| category_one_defects | Razón (conteo) | 0 a 63 |
| category_two_defects | Razón (conteo) | 0 a 55 |
| altitude_mean_meters | Razón (m) | 1 a 190 164; 230 sin dato |

A diferencia de los datos de sensores, este conjunto **no fue ensuciado**: viene tal cual de su fuente, con los defectos que ya traía. Se eligió justamente por eso. Contiene los cuatro tipos de imperfección que un análisis exploratorio real tiene que enfrentar, y ninguno fue puesto a propósito:

- **Faltantes con patrón no aleatorio.** La altitud falta en el 14% de los lotes de Guatemala y en el 97% de los de Hawái.
- **Valores imposibles.** Un lote con cero en las diez subescalas, y 264 lotes con humedad exactamente 0.
- **Valores fuera de rango.** Altitudes de hasta 190 164 metros, veintiún veces la altura del Everest.
- **Codificación inconsistente.** `Bluish-Green` y `Blue-Green` como niveles separados, y cinco formatos de año de cosecha conviviendo en la misma columna.

Recopilado por el Coffee Quality Institute y extraído por James LeDoux en [jldbc/coffee-quality-database](https://github.com/jldbc/coffee-quality-database). La versión aquí incluida es la redistribuida por [TidyTuesday](https://github.com/rfordatascience/tidytuesday/tree/master/data/2020/2020-07-07) el 7 de julio de 2020. Cubre cosechas de 2009 a 2018.

El repositorio de origen no declara licencia explícita. Uso académico citando la fuente; cualquier otro uso requiere verificar los términos con el CQI. El archivo se renombró respecto de la fuente (`coffee_ratings.csv`) para seguir la convención del repositorio; su contenido no fue modificado.

Se usa en: [icd-04-visualizacion.ipynb](../icd-04-visualizacion.ipynb)


### winequality-red.csv

1599 instancias, 12 atributos. Cada fila es un vino tinto portugués de la denominación de origen *Vinho Verde*, descrito por once mediciones fisicoquímicas y la calificación que le dieron catadores.

| Columna | Escala de medición | Valores |
|---|---|---|
| fixed acidity | Razón (g/dm³ de ácido tartárico) | 4.6 a 15.9 |
| volatile acidity | Razón (g/dm³ de ácido acético) | 0.12 a 1.58 |
| citric acid | Razón (g/dm³) | 0 a 1 |
| residual sugar | Razón (g/dm³) | 0.9 a 15.5 |
| chlorides | Razón (g/dm³ de cloruro de sodio) | 0.012 a 0.611 |
| free sulfur dioxide | Razón (mg/dm³) | 1 a 72 |
| total sulfur dioxide | Razón (mg/dm³) | 6 a 289 |
| density | Razón (g/cm³) | 0.990 a 1.004 |
| pH | Intervalo | 2.74 a 4.01 |
| sulphates | Razón (g/dm³ de sulfato de potasio) | 0.33 a 2 |
| alcohol | Razón (% vol.) | 8.4 a 14.9 |
| quality | Ordinal, variable objetivo | 3 a 8 |

`quality` es la mediana de al menos tres evaluaciones de catadores, en una escala de 0 (muy malo) a 10 (excelente). En la práctica solo aparecen valores de 3 a 8, y el 82 % de los vinos tiene 5 o 6.

Hay 240 filas duplicadas exactas. Vienen así de la fuente y no se eliminaron.

Recopilado por Cortez *et al.* (2009) con muestras certificadas entre 2004 y 2007. Se distribuye en el [UC Irvine Machine Learning Repository](https://archive.ics.uci.edu/dataset/186/wine+quality), junto con un archivo de 4898 vinos blancos que aquí no se incluye. Licencia CC BY 4.0.

La versión aquí incluida usa coma como separador; el original de UCI usa punto y coma. Los valores no se modificaron.

Cortez, P., Cerdeira, A., Almeida, F., Matos, T., & Reis, J. (2009). Modeling wine preferences by data mining from physicochemical properties. *Decision Support Systems*, 47(4), 547-553.

Se usa en: [icd-10-regresion.ipynb](../icd-10-regresion.ipynb), [icd-11-regresion-logistica.ipynb](../icd-11-regresion-logistica.ipynb) y en la Tarea 3.


### vinos-3clases.csv · vinos-3clases.arff

1599 instancias, 12 atributos. Son los vinos de `winequality-red.csv` con sus once mediciones sin modificar; solo `quality` se reemplazó por `calidad`:

| Columna | Escala de medición | Valores |
|---|---|---|
| calidad | Ordinal, variable objetivo | baja (quality 3 a 5): 744 · media (6): 638 · alta (7 y 8): 217 |

Conserva las filas duplicadas del original. El CSV se usa con pandas y Orange; el ARFF, que declara `calidad` como nominal, con Weka. Derivado de Cortez *et al.* (2009), licencia CC BY 4.0.

Se usa en: [icd-12-clasificacion.ipynb](../icd-12-clasificacion.ipynb), [icd-13-arboles-decision.ipynb](../icd-13-arboles-decision.ipynb), [icd-14-aprendizaje-bayesiano.ipynb](../icd-14-aprendizaje-bayesiano.ipynb), [icd-15-aprendizaje-instancias.ipynb](../icd-15-aprendizaje-instancias.ipynb), [icd-16-maquinas-soporte-vectorial.ipynb](../icd-16-maquinas-soporte-vectorial.ipynb) y en las demostraciones de Weka y Orange de la sesión 12.


### desercion-entrenamiento.csv · desercion-prueba.csv

4424 estudiantes de licenciatura del Instituto Politécnico de Portalegre, en Portugal, que ingresaron entre los ciclos 2008/09 y 2018/19. Cada fila es un estudiante, descrito con lo que se sabía al inscribirse y con su desempeño en el primer y el segundo semestres. La variable objetivo es su situación al final de la duración normal de la carrera: tres años, cuatro en Enfermería.

Los estudiantes se reparten en dos archivos, con una partición estratificada por `Target`:

- **`desercion-entrenamiento.csv`**: 3539 estudiantes, 38 columnas: `id`, los 36 atributos y `Target`.
- **`desercion-prueba.csv`**: 885 estudiantes, 31 columnas: `id` y los 30 atributos que se conocen al cierre del primer semestre. No trae `Target` ni los seis atributos del segundo semestre. Las etiquetas las conservan los profesores.

| Columna | Escala de medición | Valores |
|---|---|---|
| id | Identificador | 1 a 4424, asignado al azar |
| Marital status | Nominal, código entero | 6 niveles |
| Application mode | Nominal, código entero | 18 niveles |
| Application order | Ordinal | 0 (primera opción) a 9 |
| Course | Nominal, código entero | 17 carreras, con códigos de 33 a 9991 |
| Daytime/evening attendance | Nominal binaria | 1 diurno, 0 vespertino |
| Previous qualification | Nominal, código entero | 17 niveles |
| Previous qualification (grade) | Intervalo (0 a 200) | 95 a 190 |
| Nacionality | Nominal, código entero | 21 niveles; el nombre viene así en la fuente |
| Mother's qualification · Father's qualification | Nominal, código entero | 29 y 34 niveles |
| Mother's occupation · Father's occupation | Nominal, código entero | 32 y 46 niveles |
| Admission grade | Intervalo (0 a 200) | 95 a 190 |
| Displaced · Educational special needs · Debtor · Tuition fees up to date · Scholarship holder · International | Nominal binaria | 1 sí, 0 no |
| Gender | Nominal binaria | 1 hombre, 0 mujer |
| Age at enrollment | Razón (años) | 17 a 70 |
| Curricular units 1st sem (credited, enrolled, evaluations, approved, without evaluations) | Razón (conteo de unidades) | 0 a 45 |
| Curricular units 1st sem (grade) | Intervalo (0 a 20) | Promedio del semestre; 0 si no aprobó ninguna unidad (718 estudiantes) |
| Curricular units 2nd sem (las mismas seis) | Las mismas que en el primer semestre | Solo en el archivo de entrenamiento |
| Unemployment rate | Razón (%) | 7.6 a 16.2 |
| Inflation rate · GDP | Intervalo (%) | −0.8 a 3.7 y −4.06 a 3.51; entre los tres indicadores solo hay diez combinaciones de valores |
| Target | Nominal, variable objetivo | Graduate 1767 · Dropout 1137 · Enrolled 635, en el entrenamiento |

El significado de cada código de los atributos nominales está en la [ficha del dataset en UCI](https://archive.ics.uci.edu/dataset/697). *Dropout* incluye los cambios de carrera o de institución, sin importar cuándo ocurrieron. No hay valores faltantes ni filas duplicadas.

Recopilado por Realinho *et al.* (2022) y distribuido en el [UC Irvine Machine Learning Repository](https://archive.ics.uci.edu/dataset/697), licencia CC BY 4.0. La versión aquí incluida usa coma como separador (el original usa punto y coma), agrega el identificador `id` y quita los espacios sobrantes de los nombres de columna. Los valores no se modificaron.

Realinho, V., Machado, J., Baptista, L., & Martins, M. V. (2022). Predicting student dropout and academic success. *Data*, 7(11), 146. https://doi.org/10.3390/data7110146

Se usa en: la Práctica 3.
