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
