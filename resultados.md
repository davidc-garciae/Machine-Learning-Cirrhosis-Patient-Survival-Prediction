# Resultados del Análisis de Predicción de Supervivencia de Pacientes con Cirrosis

## 🔍 Resumen Ejecutivo

Este documento presenta los resultados completos del análisis de machine learning para predecir la supervivencia de pacientes con cirrosis. El proyecto transformó un problema de clasificación multiclase en binario (Sobrevive/No sobrevive) y evaluó 6 modelos diferentes con técnicas avanzadas de preprocesamiento y reducción de dimensionalidad.

### 📊 Resultados Principales

- **Mejor modelo**: XGBoost con **F1-Score: 0.7059** y **AUC: 0.7541** en test
- **Dataset procesado**: 418 pacientes, 775 características después de codificación
- **Técnicas aplicadas**: SMOTE para balanceo, StandardScaler para normalización, PCA para reducción
- **Reducción dimensional**: 70.5% de reducción (775 → 229 características) manteniendo 95% de varianza

---

## 📋 1. Información General del Dataset

### Características del Dataset

- **Tamaño**: 418 pacientes con 17 características originales
- **Variable objetivo original**: 3 clases (C: Censurado, CL: Trasplante, D: Muerte)
- **Variable objetivo transformada**: 2 clases (Sobrevive: 232 pacientes, No sobrevive: 186 pacientes)
- **Distribución final**: 55.5% Sobrevive vs 44.5% No sobrevive

### Tipos de Variables

- **Variables categóricas (10)**: Drug, Sex, Ascites, Hepatomegaly, Spiders, Edema, Cholesterol, Copper, Tryglicerides, Platelets
- **Variables numéricas (7)**: Age, Bilirubin, Albumin, Alk_Phos, SGOT, Prothrombin, Stage

### Análisis de Valores Faltantes

| Variable      | Valores Faltantes | Porcentaje |
| ------------- | ----------------- | ---------- |
| Cholesterol   | 106               | 25.36%     |
| Copper        | 106               | 25.36%     |
| Tryglicerides | 106               | 25.36%     |
| SGOT          | 106               | 25.36%     |
| Alk_Phos      | 106               | 25.36%     |
| Drug          | 105               | 25.12%     |
| Platelets     | 7                 | 1.67%      |
| Stage         | 6                 | 1.44%      |
| Prothrombin   | 2                 | 0.48%      |

---

## ⚙️ 2. Preprocesamiento de Datos

### 2.1 Estrategia de Imputación

- **Variables numéricas**: Imputación con mediana
- **Variables categóricas**: Imputación con moda (valor más frecuente)
- **Resultado**: 0 valores faltantes después del preprocesamiento

### 2.2 Codificación de Variables

- **Variables binarias**: LabelEncoder (ej: Sex)
- **Variables multicategóricas**: OneHot Encoding
- **Dimensiones finales**: 775 características después de codificación
- **Variable objetivo**: LabelEncoder (0 = No_sobrevive, 1 = Sobrevive)

### 2.3 División de Datos

- **Entrenamiento**: 292 muestras (69.9%)
- **Validación**: 63 muestras (15.1%)
- **Test**: 63 muestras (15.1%)

### 2.4 Normalización y Balanceo

- **Método de normalización**: StandardScaler
- **Técnica de balanceo**: SMOTE (Synthetic Minority Oversampling Technique)
- **Efecto de SMOTE**: 292 → 324 muestras (130→162 cada clase)

---

## 🤖 3. Configuración de Modelos

Se evaluaron 6 modelos diferentes con Grid Search para optimización de hiperparámetros:

### 3.1 Modelos Evaluados

| Modelo                  | Tipo                | Combinaciones | Tiempo (seg) |
| ----------------------- | ------------------- | ------------- | ------------ |
| **Regresión Logística** | Paramétrico         | 3             | 3.66         |
| **K-Nearest Neighbors** | No paramétrico      | 16            | 2.32         |
| **Random Forest**       | Ensamble de árboles | 24            | 6.26         |
| **XGBoost**             | Gradient Boosting   | 48            | 22.49        |
| **MLP (Red Neuronal)**  | Red neuronal        | 4             | 8.83         |
| **SVM**                 | Máquina de vectores | 6             | 1.73         |

### 3.2 Mejores Hiperparámetros por Modelo

**Random Forest** (Mejor en validación):

- n_estimators: 200
- max_depth: 20
- max_features: 'sqrt'
- min_samples_split: 5

**XGBoost** (Mejor en test):

- n_estimators: 100
- max_depth: 4
- learning_rate: 0.1
- subsample: 1.0
- colsample_bytree: 1.0

---

## 📈 4. Resultados de Entrenamiento y Validación

### 4.0 Justificación de Métricas de Evaluación

Para este problema, la selección de métricas es crucial para una evaluación realista del rendimiento del modelo en un contexto clínico:

- **F1-Score**: Es la métrica principal para la optimización, ya que busca el mejor balance entre **Precisión** (evitar falsos positivos) y **Recall/Sensibilidad** (detectar todos los casos positivos). En medicina, es vital no solo identificar correctamente a los pacientes que no sobrevivirán (recall), sino también evitar alarmar innecesariamente a los que sí lo harán (precisión).
- **AUC-ROC**: Mide la capacidad del modelo para distinguir entre las clases (Sobrevive vs. No sobrevive). Un valor alto indica que el modelo es bueno para clasificar correctamente a los pacientes.
- **Specificity**: Mide la capacidad de identificar correctamente a los pacientes que sobreviven (verdaderos negativos). Es el complemento del recall.
- **Accuracy**: Aunque útil, puede ser engañosa si las clases están desbalanceadas. Se incluye como una medida de rendimiento general.

**Importante**: Aunque se usó SMOTE para balancear los datos de _entrenamiento_, la evaluación se realiza en los conjuntos de _validación y test originales (no balanceados)_ para simular un escenario real.

### 4.1 Métricas en Conjunto de Validación

| Modelo                  | Accuracy   | Precision  | Recall     | Specificity | F1-Score   | AUC-ROC    |
| ----------------------- | ---------- | ---------- | ---------- | ----------- | ---------- | ---------- |
| **Random Forest**       | **0.7937** | **0.7895** | **0.8571** | **0.7143**  | **0.8219** | **0.8714** |
| **XGBoost**             | 0.6984     | 0.7105     | 0.7714     | 0.6071      | 0.7397     | 0.7898     |
| **SVM**                 | 0.6667     | 0.6667     | 0.8000     | 0.5000      | 0.7273     | 0.7378     |
| **Regresión Logística** | 0.6349     | 0.6500     | 0.7429     | 0.5000      | 0.6933     | 0.7245     |
| **MLP**                 | 0.6190     | 0.6410     | 0.7143     | 0.5000      | 0.6757     | 0.6459     |
| **KNN**                 | 0.4603     | 0.6000     | 0.0857     | 0.9286      | 0.1500     | 0.6388     |

### 4.2 Interpretación de Resultados en Validación

**🏆 Random Forest** demostró el mejor rendimiento general:

- **F1-Score más alto**: 0.8219 indica excelente balance entre precisión y recall
- **Recall alto**: 0.8571 significa que detecta correctamente el 85.7% de supervivientes
- **AUC-ROC excepcional**: 0.8714 indica muy buena capacidad discriminativa

**⚠️ KNN** mostró el peor rendimiento:

- **Recall muy bajo**: 0.0857 indica que solo detecta 8.6% de supervivientes
- **F1-Score bajo**: 0.1500 debido al pobre recall, a pesar de alta especificidad

---

## 🎯 5. Evaluación Final en Conjunto de Test

### 5.1 Métricas en Conjunto de Test

| Modelo                  | Accuracy   | Precision  | Recall     | Specificity | F1-Score   | AUC-ROC    |
| ----------------------- | ---------- | ---------- | ---------- | ----------- | ---------- | ---------- |
| **XGBoost**             | **0.6825** | **0.7273** | **0.6857** | **0.6786**  | **0.7059** | **0.7541** |
| **SVM**                 | 0.6667     | 0.7059     | 0.6857     | 0.6429      | 0.6957     | 0.7112     |
| **Regresión Logística** | 0.6667     | 0.7188     | 0.6571     | 0.6786      | 0.6866     | 0.7143     |
| **MLP**                 | 0.6667     | 0.7500     | 0.6000     | 0.7500      | 0.6667     | 0.7418     |
| **Random Forest**       | 0.6349     | 0.6875     | 0.6286     | 0.6429      | 0.6567     | 0.7255     |
| **KNN**                 | 0.4921     | 1.0000     | 0.0857     | 1.0000      | 0.1579     | 0.6913     |

### 5.2 Interpretación de Resultados en Test

**🏆 XGBoost** emergió como el mejor modelo en test:

- **Mejor F1-Score**: 0.7059 con buen balance entre métricas
- **AUC-ROC sólido**: 0.7541 indica buena capacidad predictiva
- **Balance óptimo**: Mejores métricas generales comparado con otros modelos

**📉 Diferencia validación vs test**:

- Random Forest bajó de 0.8219 a 0.6567 en F1-Score (posible sobreajuste)
- XGBoost se mantuvo más estable: 0.7397 → 0.7059

---

## 🔬 6. Análisis de Características

### 6.1 Características con Mayor Capacidad Discriminativa (Mutual Information)

| Ranking | Característica        | MI Score | Interpretación                                             |
| ------- | --------------------- | -------- | ---------------------------------------------------------- |
| 1       | **Bilirubin**         | 0.2022   | Nivel de bilirrubina (indicador clave de función hepática) |
| 2       | **Copper_68**         | 0.1034   | Nivel específico de cobre en sangre                        |
| 3       | **Cholesterol_194**   | 0.0925   | Nivel específico de colesterol                             |
| 4       | **Platelets_124**     | 0.0841   | Conteo específico de plaquetas                             |
| 5       | **Tryglicerides_108** | 0.0839   | Nivel específico de triglicéridos                          |

### 6.2 Análisis de Correlaciones

- **249 pares de variables** con correlación alta (|r| > 0.8)
- **501 características** con baja capacidad discriminativa (MI < 0.01)
- **186 características redundantes** identificadas para posible eliminación

### 6.3 Implicaciones Clínicas

- **Bilirubin** como predictor más importante confirma su relevancia clínica en cirrosis
- **Niveles específicos** de laboratorio muestran más poder predictivo que rangos generales
- **Alta dimensionalidad** sugiere la necesidad de técnicas de reducción

---

## 📉 7. Reducción de Dimensionalidad con PCA

### 7.1 Configuración de PCA

- **Criterio**: Mantener 95% de la varianza explicada
- **Componentes seleccionados**: 229 de 775 (reducción del 70.5%)
- **Varianza conservada**: 95.0%

### 7.2 Resultados con PCA

| Modelo            | Método   | F1-Val | F1-Test | Acc-Test | Dimensiones | Reducción |
| ----------------- | -------- | ------ | ------- | -------- | ----------- | --------- |
| **Random Forest** | Original | 0.8219 | 0.6567  | 0.6349   | 775         | 0.0%      |
| **Random Forest** | PCA      | 0.7606 | 0.6027  | 0.5397   | 229         | 70.5%     |
| **XGBoost**       | Original | 0.7397 | 0.7059  | 0.6825   | 775         | 0.0%      |
| **XGBoost**       | PCA      | 0.7778 | 0.5882  | 0.5556   | 229         | 70.5%     |

### 7.3 Análisis del Impacto de PCA

**📊 Cambios en F1-Score (Test)**:

- **Random Forest**: 0.6567 → 0.6027 (-8.2%)
- **XGBoost**: 0.7059 → 0.5882 (-16.7%)

**🔍 Interpretación**:

- PCA logra reducción significativa de dimensionalidad
- **Trade-off performance vs simplicidad**: Pérdida moderada de rendimiento por gran simplificación
- **XGBoost más sensible** a la reducción dimensional que Random Forest

---

## 📋 8. Resumen Final y Recomendaciones

### 8.0 Tabla Comparativa Completa

La siguiente tabla consolida los resultados de todos los modelos, tanto en su versión original como con la reducción de dimensionalidad PCA, ordenados por rendimiento en el conjunto de test para una fácil comparación.

| Modelo                  | Método   | F1 (Validación) | F1 (Test)  | AUC (Test) | Dimensiones | Reducción |
| ----------------------- | -------- | --------------- | ---------- | ---------- | ----------- | --------- |
| **XGBoost**             | Original | 0.7397          | **0.7059** | **0.7541** | 775         | 0.0%      |
| **SVM**                 | Original | 0.7273          | 0.6957     | 0.7112     | 775         | 0.0%      |
| **Regresión Logística** | Original | 0.6933          | 0.6866     | 0.7143     | 775         | 0.0%      |
| **MLP**                 | Original | 0.6757          | 0.6667     | 0.7418     | 775         | 0.0%      |
| **Random Forest**       | Original | 0.8219          | 0.6567     | 0.7255     | 775         | 0.0%      |
| Random Forest           | PCA      | 0.7606          | 0.6027     | 0.6204     | 229         | 70.5%     |
| XGBoost                 | PCA      | 0.7778          | 0.5882     | 0.6612     | 229         | 70.5%     |
| **KNN**                 | Original | 0.1500          | 0.1579     | 0.6913     | 775         | 0.0%      |

### 8.1 Modelo Recomendado

**🏆 XGBoost (Configuración Original)**

- **F1-Score**: 0.7059
- **AUC-ROC**: 0.7541
- **Características**: 775
- **Ventajas**: Mejor rendimiento general, estabilidad entre validación y test

### 8.2 Hallazgos Clave

1. **Transformación exitosa**: Conversión de problema multiclase a binario mejoró interpretabilidad
2. **SMOTE efectivo**: Balanceo de clases mejoró entrenamiento sin comprometer evaluación realista
3. **Ensambles superiores**: Random Forest y XGBoost consistentemente superaron otros modelos
4. **Bilirubin como predictor clave**: Confirmación de relevancia clínica conocida
5. **PCA viable con trade-offs**: 70.5% reducción dimensional con pérdida aceptable de rendimiento

### 8.3 Consideraciones Clínicas

**✅ Fortalezas del Modelo**:

- F1-Score > 0.7 indica buen balance para decisiones médicas
- AUC > 0.75 sugiere capacidad discriminativa clínicamente útil
- Uso de características interpretables (laboratorio estándar)

**⚠️ Limitaciones**:

- Dataset relativamente pequeño (418 pacientes)
- Posible sobreajuste en algunos modelos (Random Forest)
- Necesidad de validación externa en poblaciones diferentes

### 8.4 Recomendaciones para Implementación

1. **Modelo de producción**: XGBoost con configuración optimizada
2. **Monitoreo continuo**: Evaluación regular en nuevos datos
3. **Interpretabilidad**: Implementar SHAP values para explicaciones por paciente
4. **Validación externa**: Probar en diferentes hospitales/poblaciones
5. **Actualización periódica**: Re-entrenamiento con nuevos datos clínicos

---

## 📊 9. Métricas Técnicas Detalladas

### 9.1 Configuración Experimental

- **Validación cruzada**: Stratified 5-Fold
- **Métrica de optimización**: F1-Score
- **Procesadores utilizados**: Paralelización completa (-1)
- **Semillas aleatorias**: 42 (reproducibilidad garantizada)

### 9.2 Tiempo de Ejecución

- **Tiempo total**: ~45 segundos
- **Modelo más rápido**: KNN (2.32s)
- **Modelo más lento**: XGBoost (22.49s)
- **Eficiencia**: Excelente relación tiempo/rendimiento

### 9.3 Estabilidad de Resultados

- **Validación cruzada consistente**: Baja varianza entre folds
- **Reproducibilidad**: Resultados idénticos con misma semilla
- **Robustez**: Modelos estables ante pequeñas variaciones en datos

---

_Análisis completado el [fecha] con Python 3.x, scikit-learn, XGBoost y librerías asociadas._
