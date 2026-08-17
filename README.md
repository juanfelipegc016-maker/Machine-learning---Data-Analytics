# Proyectos de Machine Learning — Curso de Inteligencia Artificial

Repositorio con dos proyectos aplicados de machine learning, desarrollados en Google Colab. Ambos cubren el ciclo completo de un proyecto de datos: carga y limpieza, análisis exploratorio, preparación de variables, modelado y evaluación.

## 📁 Contenido

| Notebook | Problema | Dataset | Modelo | Resultado |
|---|---|---|---|---|
| `Machine_Learning_VENTAS.ipynb` | Regresión — predicción de costo de venta | VENTAS_NL (62.113 registros, 8 columnas) | Random Forest Regressor | R² = 0.97 · MAE = $165.437 |
| `finca_raiz_modificado.ipynb` | Clasificación — precio alto vs. bajo de apartamentos | FincaRaíz / Kaggle (8.428 registros, 31 columnas) | Árbol de Decisión (Decision Tree Classifier) | Accuracy = 89.8% |

---

## 1. Predicción de Costo de Venta (VENTAS_NL)

**Objetivo:** estimar el costo de venta (`costo_venta`) a partir de variables del cliente y de la transacción, en el momento en que la venta ya fue registrada pero el costo contable todavía no está disponible.

**Proceso:**
- Carga del dataset (`VENTAS NL.xlsx`) y estandarización de nombres de columnas.
- Limpieza: eliminación de 15 registros duplicados y validación de rangos (edad, tallas, género, ingresos, ventas, costos y descuentos).
- Tratamiento de datos faltantes basado en el coeficiente de asimetría de cada variable (mediana para variables con sesgo alto, regresión para `ventas`/`costo_venta` cuando ambas faltaban).
- Estandarización (`StandardScaler`) y normalización (`MinMaxScaler`) de variables numéricas.
- Ingeniería de características: ventas netas, margen bruto y porcentaje de margen.
- Análisis de correlación entre variables numéricas.
- Entrenamiento de un `RandomForestRegressor` (pipeline con preprocesamiento de variables numéricas y categóricas) sobre 57.910 registros con datos reales (no imputados).

**Resultado:**
- **R² = 0.97**, **MAE ≈ $165.437**, **RMSE ≈ $296.928** sobre el conjunto de prueba.
- Análisis de importancia de variables para identificar los principales predictores del costo de venta.

**Visualización:** los resultados del modelo se llevaron a un dashboard en Power BI para facilitar su interpretación por parte de usuarios no técnicos.

---

## 2. Clasificación de Precio en Apartamentos (FincaRaíz)

**Objetivo:** predecir si el precio de un apartamento es alto o bajo (respecto a la mediana del dataset) a partir de sus características físicas y amenidades.

**Proceso:**
- Carga del dataset (`housing_fincaraiz.csv`, obtenido de Kaggle) y limpieza de columnas (extracción de valores numéricos de área, conversión de tipos).
- Definición de la variable objetivo `precio_alto` a partir de la mediana de precios ($490.500.000 COP), con distribución balanceada (49.4% / 50.6%).
- Análisis exploratorio: distribución de área construida y presencia de amenidades por categoría de precio.
- División de datos en entrenamiento (6.375 registros) y prueba (1.594 registros), con estratificación por clase.
- Entrenamiento de un `DecisionTreeClassifier` (profundidad máxima limitada para evitar sobreajuste).

**Resultado:**
- **Accuracy = 89.8%** sobre el conjunto de prueba (1.432 de 1.594 apartamentos clasificados correctamente).
- La variable más influyente fue el número de **parqueaderos**, seguida del área construida.

---

## 🛠️ Tecnologías

Python · Pandas · NumPy · Scikit-learn (Random Forest, Decision Tree, pipelines, ColumnTransformer) · Matplotlib · Seaborn · Google Colab · Power BI

[LinkedIn](https://linkedin.com/in/juan-felipe-gonzalez-castro) · [GitHub](https://github.com/juanfelipegc016-maker)
