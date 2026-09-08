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
