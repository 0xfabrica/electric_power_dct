# Household Electric Power Consumption Analysis

[![Python](https://img.shields.io/badge/Python-3.12-blue?logo=python&logoColor=white)](https://www.python.org/)
[![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-yellow?logo=pandas&logoColor=black)](https://pandas.pydata.org/)
[![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualization-orange?logo=matplotlib&logoColor=white)](https://matplotlib.org/)
[![Seaborn](https://img.shields.io/badge/Seaborn-Visualization-blue?logo=seaborn&logoColor=white)](https://seaborn.pydata.org/)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-ML-orange?logo=scikit-learn&logoColor=white)](https://scikit-learn.org/)
[![Open Database License](https://img.shields.io/badge/License-ODbL-green)](https://opendatacommons.org/licenses/odbl/)

Este proyecto analiza el consumo eléctrico de un hogar utilizando datos de series de tiempo, regresión y modelos de árbol de decisión. El análisis se realiza en el notebook [`notebook_luz.ipynb`](notebook_luz.ipynb).

---

## Tabla de Contenidos

- [Descripción del Dataset](#descripción-del-dataset)
- [Tecnologías Usadas](#tecnologías-usadas)
- [Análisis Realizado](#análisis-realizado)
  - [Preprocesamiento](#preprocesamiento)
  - [Visualizaciones](#visualizaciones)
  - [Modelos Predictivos](#modelos-predictivos)
- [Resultados](#resultados)
- [Ejecutar el Notebook](#ejecutar-el-notebook)
- [Licencia](#licencia)
- [Referencias](#referencias)

---

## Descripción del Dataset

**Fuente:** [Household Electric Power Consumption Dataset](https://archive.ics.uci.edu/ml/datasets/individual+household+electric+power+consumption)

- **Contexto:** Medidas de consumo eléctrico en un hogar, con frecuencia de muestreo de 1 minuto durante casi 4 años (2075259 mediciones, de diciembre 2006 a noviembre 2010).
- **Características:** Multivariado, Serie de Tiempo.
- **Tareas asociadas:** Regresión, Clustering.
- **Atributos:**
  1. `date`: Fecha en formato dd/mm/yyyy
  2. `time`: Hora en formato hh:mm:ss
  3. `global_active_power`: Potencia activa promedio por minuto (kW)
  4. `global_reactive_power`: Potencia reactiva promedio por minuto (kW)
  5. `voltage`: Voltaje promedio por minuto (V)
  6. `global_intensity`: Intensidad de corriente promedio por minuto (A)
  7. `sub_metering_1`: Submedición 1 (cocina)
  8. `sub_metering_2`: Submedición 2 (lavadero)
  9. `sub_metering_3`: Submedición 3 (calentador agua y aire acondicionado)

- **Notas Importantes:**
  - El 1.25% de los registros contienen valores nulos.
  - Todos los timestamps de calendario están presentes, pero algunas mediciones faltan (representadas por ausencia de valor entre dos “;”).
  - La variable objetivo para regresión es `Global_active_power`.

---

## Tecnologías Usadas

- **Python:** Análisis y modelado.
- **Pandas:** Manipulación y limpieza de datos.
- **Matplotlib & Seaborn:** Visualización.
- **scikit-learn:** Modelos de regresión y árboles de decisión.

---

## Análisis Realizado

### Preprocesamiento

- Lectura del dataset (`.csv`).
- Conversión de fechas y creación de índices de tiempo.
- Imputación de valores nulos por mediana.
- Detección y manejo de outliers.
- División cronológica de datos en entrenamiento (80%) y prueba (20%).
- Escalado de variables para regresión lineal.

### Visualizaciones

- Series temporales de consumo (`Global_active_power`).
- Promedio diario de consumo.
- Suma de sub-mediciones (`Sub_metering_1`, `Sub_metering_2`, `Sub_metering_3`).
- Matriz de correlación.
- Boxplots para detección de outliers.

### Modelos Predictivos

#### Regresión Lineal

- Entrenamiento sobre datos escalados.
- Métricas evaluadas:
  - Error Cuadrático Medio (MSE): **0.1532**
  - Raíz del Error Cuadrático Medio (RMSE): **0.3914**
  - Coeficiente de Determinación (R²): **0.8058**

#### Árbol de Decisión (DecisionTreeRegressor)

- Entrenamiento con hiperparámetros ajustados (`max_depth=11`, `min_samples_leaf=120`, `min_samples_split=380`).
- Métricas evaluadas:
  - Error Cuadrático Medio (MSE): **0.1176**
  - Coeficiente de Determinación (R²): **0.8509**

---

## Resultados

- El árbol de decisión mejora la predicción respecto a la regresión lineal (mayor R², menor MSE).
- El notebook incluye visualizaciones comparando datos reales vs. predicciones para ambos modelos.

---

## Ejecutar el Notebook

1. Clona el repositorio:
   ```bash
   git clone https://github.com/0xfabrica/electric_power_dct.git
   ```
2. Instala las dependencias (recomendado usar un entorno virtual):
   ```bash
   pip install pandas matplotlib seaborn scikit-learn
   ```
3. Abre y ejecuta el notebook:
   ```bash
   jupyter notebook notebook_luz.ipynb
   ```

---

## Licencia

- **Base de datos:** Open Database License (ODbL).
- **Contenido:** Open Database Contents License.

---

## Referencias

- [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/individual+household+electric+power+consumption)
- [scikit-learn documentation](https://scikit-learn.org/)
- [Pandas documentation](https://pandas.pydata.org/)
