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

Se usa en: [icd-02-datos.ipynb](../icd-02-datos.ipynb)

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
