[![Python](https://img.shields.io/badge/Python-3.8%2B-blue?logo=python)](https://www.python.org/)[![Pandas](https://img.shields.io/badge/Pandas-1.5%2B-yellow?logo=pandas)](https://pandas.pydata.org/)[![NumPy](https://img.shields.io/badge/NumPy-1.23%2B-blueviolet?logo=numpy)](https://numpy.org/)[![scikit-learn](https://img.shields.io/badge/scikit--learn-1.1%2B-f7931e?logo=scikit-learn)](https://scikit-learn.org/)[![imbalanced-learn](https://img.shields.io/badge/imbalanced--learn-0.10%2B-9cf?logo=python)](https://imbalanced-learn.org/)[![XGBoost](https://img.shields.io/badge/XGBoost-1.7%2B-00bfff?logo=xgboost)](https://xgboost.readthedocs.io/)[![Matplotlib](https://img.shields.io/badge/Matplotlib-3.5%2B-11557c?logo=matplotlib)](https://matplotlib.org/)[![Seaborn](https://img.shields.io/badge/Seaborn-0.12%2B-76b900?logo=python)](https://seaborn.pydata.org/)[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter)](https://jupyter.org/)

# Predicción de Supervivencia de Pacientes con Cirrosis mediante Machine Learning
## [Video presentación del proyecto](https://youtu.be/k5Q1-Ky92Hg).

## Resumen del Proyecto

Este repositorio contiene el desarrollo completo de un sistema de predicción de supervivencia para pacientes con cirrosis hepática, utilizando técnicas avanzadas de aprendizaje automático. El proyecto abarca desde la limpieza y preprocesamiento de datos clínicos reales, hasta la comparación de modelos, análisis de reducción de dimensionalidad y la generación de un informe científico en LaTeX y PDF.

## Estructura del Repositorio

- **notebook.ipynb**: Notebook principal con todo el flujo de trabajo: carga de datos, preprocesamiento, balanceo de clases (SMOTE), entrenamiento y validación de modelos, reducción de dimensionalidad (PCA), análisis de resultados y generación de gráficas.
- **resultados.md**: Documento markdown que resume y organiza todos los resultados obtenidos en el notebook, con explicaciones y visualizaciones clave.
- **Cirrosis.tex**: Informe científico completo en formato LaTeX, listo para compilar. Contiene toda la metodología, resultados, discusión y referencias, incluyendo las figuras generadas.
- **Predicción_de_Supervivencia_de_Pacientes_con_Cirrosis_mediante_Machine_Learning.pdf**: Versión final en PDF del informe, generada a partir del archivo LaTeX.
- **graficas/**: Carpeta con todas las figuras y gráficas generadas automáticamente por el notebook (en formato PNG), listas para ser incluidas en el informe.

## ¿Cómo reproducir los resultados?

1. **Instala los requisitos** (recomendado: entorno virtual):

   - Python 3.8+
   - Instala dependencias con:
     ```bash
     pip install -r requirements.txt
     ```
   - O instala manualmente: pandas, numpy, scikit-learn, imbalanced-learn, xgboost, matplotlib, seaborn, ucimlrepo

2. **Ejecuta el notebook**:

   - Abre `notebook.ipynb` en Jupyter o VSCode.
   - Ejecuta todas las celdas desde el inicio. Esto generará automáticamente todas las gráficas en la carpeta `graficas/`.

3. **Compila el informe LaTeX** (opcional):
   - Asegúrate de tener instalado un compilador LaTeX (por ejemplo, TeX Live o MikTeX).
   - Compila `Cirrosis.tex` para obtener el PDF final.

## Archivos principales

- `notebook.ipynb`: Código y experimentos reproducibles.
- `resultados.md`: Resumen y visualización de resultados.
- `Cirrosis.tex` / `PDF`: Informe científico final.
- `graficas/`: Figuras generadas automáticamente.

## Créditos y referencias

- Datos: UCI Machine Learning Repository, Mayo Clinic.
- Autores: David C. García-Echavarría, Juan E. Aristizábal-Aristizábal.
- Para referencias completas, ver la sección de bibliografía en el informe LaTeX.

---

Si tienes dudas o deseas reproducir algún experimento, consulta el notebook o el informe para detalles metodológicos.

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
