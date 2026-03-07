# 📊 Predicción de Cancelación de Clientes (Churn) en Telecomunicaciones

## 📌 Descripción del Proyecto
Este proyecto tiene como objetivo desarrollar modelos predictivos capaces de identificar clientes con alta probabilidad de cancelar los servicios de telecomunicaciones (**Churn**).

La cancelación de clientes representa un problema importante para las empresas del sector, ya que adquirir nuevos clientes suele ser más costoso que retener a los actuales. Contar con modelos predictivos permite anticipar la cancelación y aplicar estrategias de retención.

Se desarrolló un **pipeline completo de análisis de datos y machine learning**, que incluye:
- Limpieza de datos
- Análisis exploratorio
- Selección de variables
- Entrenamiento de modelos
- Evaluación de resultados

---

## 🎯 Objetivos
- Preparar los datos para el modelado (limpieza, codificación y normalización).
- Analizar la correlación entre variables y la cancelación de clientes.
- Entrenar modelos de clasificación para predecir churn.
- Evaluar el desempeño de los modelos utilizando diferentes métricas.
- Identificar las variables más influyentes en la cancelación.
- Proponer estrategias de retención basadas en los resultados obtenidos.

---

## 📂 Dataset
El dataset contiene información sobre clientes de una empresa de telecomunicaciones, incluyendo:
- Características demográficas
- Servicios contratados
- Información de facturación
- Comportamiento del cliente

### 🔑 Variables relevantes
- `tenure` → tiempo que el cliente lleva en la empresa  
- `MonthlyCharges` → cargos mensuales  
- `TotalCharges` → cargos acumulados  
- `Contract` → tipo de contrato  
- `PaymentMethod` → método de pago  
- `InternetService` → tipo de servicio de internet  
- `SeniorCitizen` → si el cliente es adulto mayor  
- `Churn` → variable objetivo (cancelación)  

---

## 🛠️ Preparación de Datos
### Eliminación de columnas irrelevantes
Se eliminaron variables que no aportan valor predictivo, como identificadores únicos.  
Ejemplo: `CustomerID`

### Codificación de variables categóricas
Las variables categóricas fueron transformadas a formato numérico utilizando **One-Hot Encoding** (`pd.get_dummies()`).

### Creación de variable binaria de churn
La variable `Churn` fue transformada en una variable binaria (`Churn_bin`):
- `1` → cliente canceló
- `0` → cliente permanece activo

### Tratamiento de valores faltantes
Se identificaron valores faltantes en `TotalCharges`.  
Estos registros fueron eliminados debido a que representaban una proporción mínima del dataset.

---

## 🔎 Análisis Exploratorio de Datos
### Distribución de Cancelación
Se analizó la proporción de clientes que cancelaron vs. los que permanecieron activos, evaluando el **desbalance de clases**.

### Matriz de Correlación
Se analizó la relación entre variables numéricas y la cancelación utilizando un **heatmap de correlación**.

#### Resultados principales
| Variable        | Correlación con Cancelación |
|-----------------|-----------------------------|
| tenure          | -0.35 |
| TotalCharges    | -0.19 |
| MonthlyCharges  | 0.19  |
| Cuentas_Diarias | 0.19  |
| SeniorCitizen   | 0.15  |

---

## 📈 Modelado Predictivo
El dataset fue dividido en:
- **Entrenamiento:** 70%  
- **Prueba:** 30%  

### Modelos utilizados
1. **Regresión Logística**  
   - Modelo lineal sensible a la escala de variables.  
   - Requiere normalización.  

2. **Random Forest**  
   - Algoritmo basado en múltiples árboles de decisión.  
   - Captura relaciones no lineales.  
   - Identifica importancia de variables.  
   - No requiere normalización.  

---

## 📊 Evaluación de Modelos
Se utilizaron las métricas:
- Accuracy  
- Precision  
- Recall  
- F1-score  
- Matriz de confusión  

### Importancia de Variables (Random Forest)
| Variable                        | Importancia |
|---------------------------------|-------------|
| TotalCharges                     | 0.167 |
| tenure                           | 0.152 |
| MonthlyCharges                   | 0.129 |
| Cuentas_Diarias                  | 0.128 |
| PaymentMethod_Electronic check   | 0.039 |
| InternetService_Fiber optic      | 0.036 |

---

## 📌 Principales Factores de Cancelación
- **Antigüedad del cliente (tenure):** menor tiempo → mayor probabilidad de cancelar.  
- **Cargos mensuales elevados:** asociados a mayor churn.  
- **Método de pago:** Electronic Check se relaciona con mayor cancelación.  
- **Tipo de servicio de internet:** fibra óptica presenta mayor churn.  
- **Tipo de contrato:** contratos de largo plazo reducen la cancelación.  

---

## 💡 Estrategias de Retención
- Programas de fidelización para clientes nuevos.  
- Incentivos para contratos de largo plazo.  
- Revisión de precios en planes con cargos altos.  
- Mejorar experiencia en servicios de fibra óptica.  

---

## ⚙️ Instalación y Uso
### Requisitos
- Python 3.8 o superior  
- Librerías: `pandas`, `numpy`, `matplotlib`, `seaborn`, `scikit-learn`

### Instalación de dependencias
```bash
pip install pandas numpy matplotlib seaborn scikit-learn
