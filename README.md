# Predicción de Supervivencia de Pacientes con Cirrosis mediante Machine Learning

## Descripción

Este proyecto desarrolla un modelo de clasificación binaria para predecir la supervivencia de pacientes con cirrosis hepática primaria biliar, utilizando técnicas de aprendizaje automático como Random Forest, XGBoost y regresión logística. El análisis se realiza sobre el conjunto de datos del Mayo Clinic, que contiene 418 muestras y 17 indicadores clínicos y demográficos.

## Objetivo

Diseñar, desarrollar y evaluar un sistema de predicción de supervivencia (sobrevive / no sobrevive) en pacientes con cirrosis, empleando modelos de Machine Learning y comparando su desempeño con los puntajes clínicos tradicionales (MELD, CTP).

## Metodología

- **Preprocesamiento:** Imputación de valores faltantes, codificación de variables categóricas y normalización/estandarización de variables numéricas.
- **Modelado:** Entrenamiento y ajuste de modelos Random Forest, XGBoost y regresión logística.
- **Validación:** Validación cruzada y ajuste de hiperparámetros.
- **Comparación:** Evaluación frente a puntajes clínicos tradicionales.

## Resultados

Los modelos basados en ensamblados de árboles (Random Forest, XGBoost) superan en desempeño a los puntajes clínicos tradicionales, alcanzando un AUC de hasta 0.89 en validación interna.

## Estado del Arte

Diversos estudios han demostrado que los modelos de aprendizaje automático, especialmente los ensamblados de árboles, superan a los métodos clínicos clásicos en la predicción de supervivencia en pacientes con cirrosis.

## Conjunto de Datos

- **Fuente:** [UCI Machine Learning Repository: Cirrhosis Patient Survival Prediction Dataset](https://archive.ics.uci.edu/dataset/878/cirrhosis+patient+survival+prediction+dataset-1)
- **Instancias:** 418 pacientes
- **Variables:** 19 independientes (edad, sexo, etiología, variables clínicas y bioquímicas) y 1 dependiente (estado final: muerte, censurado, trasplante).

## Estado del desarrollo

Actualmente, el proyecto se encuentra en desarrollo. Próximamente se incluirán instrucciones detalladas sobre cómo instalar las dependencias, ejecutar el código y reproducir los experimentos.

## Impacto

El uso de modelos de Machine Learning puede mejorar la precisión en la predicción de supervivencia de pacientes con cirrosis, optimizando la toma de decisiones clínicas y la asignación de recursos hospitalarios.

## Autores

- David C. García-Echavarría (Estudiante, UdeA)
- Juan E. Aristizábal-Aristizábal (Estudiante, UdeA)

## Palabras clave

Aprendizaje automático, cirrosis hepática, supervivencia de pacientes, Random Forest, XGBoost, validación cruzada.
