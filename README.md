# 📡 Challenge Telecom X — Parte 2

Análisis de **churn** (cancelación de clientes) de una empresa de telecomunicaciones mediante técnicas de Machine Learning, con el objetivo de identificar los principales factores que influyen en la cancelación y proponer estrategias de retención.

## 📋 Descripción del Proyecto

Este proyecto forma parte del **Challenge Telecom X** y se centra en la segunda etapa del análisis: la construcción y evaluación de modelos predictivos de abandono de clientes. A partir de un dataset previamente limpiado y tratado, se desarrollan modelos de clasificación para predecir si un cliente cancelará el servicio.

## 🗂️ Estructura del Proyecto

```
Challenge-Telecom-X---part-2/
├── Challenge_Telecom_X_- parte 2.ipynb   # Notebook principal con el análisis completo
└── README.md
```

## 🔧 Tecnologías y Librerías

| Librería | Uso |
|---|---|
| **pandas** | Manipulación y análisis de datos |
| **numpy** | Operaciones numéricas |
| **matplotlib** | Visualización de gráficos |
| **seaborn** | Visualizaciones estadísticas |
| **scikit-learn** | Modelos de Machine Learning, métricas y preprocesamiento |
| **imbalanced-learn** | Balanceo de clases con SMOTE |

## 🚀 Flujo de Trabajo

### 1. Preparación de los Datos
- Carga del dataset tratado en la primera parte del challenge.
- Análisis de correlación entre variables numéricas.

### 2. Análisis Exploratorio Dirigido
Visualizaciones comparativas entre variables clave y la variable objetivo (`Abandono`):
- Ciudadano mayor
- Tipo de servicio de internet
- Seguridad en línea
- Soporte técnico
- Tipo de contrato
- Forma de pago
- Meses de permanencia, cuenta mensual y cargo total (boxplots)

### 3. Preprocesamiento
- **Eliminación de columnas irrelevantes** (ej. `Cliente_ID`, `Genero`, `Pareja`).
- **Separación** en conjuntos de entrenamiento (70 %) y prueba (30 %) con estratificación.
- **Encoding**: `OneHotEncoder` para variables categóricas (`Tipo_servicio_internet`, `Tipo_contrato`, `Forma_pago`).
- **Balanceo de clases**: SMOTE para sobremuestreo de la clase minoritaria.
- **Normalización**: `MinMaxScaler` para modelos basados en distancia.

### 4. Creación de Modelos
| Modelo | Descripción |
|---|---|
| **DummyClassifier** | Baseline — estrategia estratificada |
| **Árbol de Decisión** | `max_depth=4`, `random_state=123` |
| **KNN** | `n_neighbors=15`, `weights='distance'` |

### 5. Evaluación
- Métricas: **Accuracy**, **Recall**, **Precision**, **F1-Score**.
- **Matrices de confusión** para cada modelo.

### 6. Importancia de Variables
- `permutation_importance` en KNN y Árbol de Decisión.
- `feature_importances_` del Árbol de Decisión.

## 📊 Resultados Principales

| Modelo | Accuracy | Recall |
|---|---|---|
| Dummy (Baseline) | ~0.50 | Bajo |
| KNN | **0.77** | 0.58 |
| Árbol de Decisión | 0.74 | **0.80** |

- El **Árbol de Decisión** fue seleccionado como el modelo más adecuado por su alto recall (0.80), lo cual es prioritario para detectar clientes que van a cancelar.
- El **KNN** tiene mejor accuracy pero menor capacidad de detección de cancelaciones.

## 🔑 Variables Más Influyentes en la Cancelación

1. **Tipo de contrato mensual (Month-to-month)** — Principal predictor de churn.
2. **Forma de pago: cheque electrónico** — Asociada a mayor tasa de abandono.
3. **Meses de permanencia** — Clientes con menor antigüedad cancelan más.
4. **Cuenta mensual** — Cuentas más altas se correlacionan con mayor abandono.
5. **Seguridad en línea / Soporte técnico** — La ausencia de estos servicios aumenta el riesgo.

## 💡 Estrategias de Retención Propuestas

1. **Incentivar contratos de largo plazo** con descuentos y paquetes bonificados.
2. **Promover métodos de pago automáticos** (tarjeta de crédito, débito bancario).
3. **Fortalecer los servicios de seguridad y soporte técnico** como herramientas de fidelización.
4. **Monitorear clientes con facturación alta** y baja antigüedad para intervención temprana.

## ▶️ Cómo Ejecutar

1. Abre el notebook en [Google Colab](https://colab.research.google.com/) o Jupyter Notebook.
2. Asegúrate de tener instaladas las dependencias:
   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn imbalanced-learn
   ```
3. Carga el dataset tratado (`df_final`) en la ruta esperada por el notebook.
4. Ejecuta las celdas de forma secuencial.

## 📝 Conclusión

El modelo de **Árbol de Decisión** demostró ser el más adecuado para el objetivo del negocio, maximizando la detección de clientes que cancelan. El análisis reveló que los factores contractuales (tipo de contrato y forma de pago) son los principales impulsores de la cancelación, lo que permite diseñar estrategias de retención enfocadas y efectivas.
