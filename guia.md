# Guía para el desarrollo del proyecto del curso

**Julián D. Arias-Londoño**  
Departamento de Ingeniería de Sistemas e Informática  
Universidad de Antioquia

## Resumen

Las actividades propuestas para el desarrollo del proyecto buscan que cada uno de los grupos de estudiantes aborden todo el análisis, el diseño, y la simulación de un sistema de predicción basado en técnicas de aprendizaje de máquina; describiendo el problema, evaluando sus similitudes con otros proyectos y soluciones reportados en la literatura especializada, especificando cada una de las etapas del desarrollo del trabajo, los modelos usados con sus respectivas restricciones, el ajuste de hiperparámetros, la metodología de validación, los resultados de las simulaciones y las conclusiones obtenidas.

## Índice

1. [Introducción](#1-introducción)
2. [Descripción del problema (20%)](#2-descripción-del-problema-20)
3. [Estado del arte (10%)](#3-estado-del-arte-10)
4. [Entrenamiento y Evaluación de los Modelos (30%)](#4-entrenamiento-y-evaluación-de-los-modelos-30)
   - 4.1. [Configuración experimental](#41-configuración-experimental)
   - 4.2. [Resultados del entrenamiento de Modelos](#42-resultados-del-entrenamiento-de-modelos)
5. [Reducción de dimensión (20%)](#5-reducción-de-dimensión-20)
   - 5.1. [Selección de características](#51-selección-de-características)
   - 5.2. [Extracción de características](#52-extracción-de-características)
6. [Evaluación (20%)](#6-evaluación-20)

---

## 1. Introducción

Cada equipo de trabajo debe seleccionar un problema que pueda ser abordado a partir de las técnicas y aproximaciones vistas en el curso de Modelos y Simulación II. Los problemas abordados pueden ser propuestos por el grupo de estudiantes, o seleccionado a partir del listado que será compartido por el profesor del curso.

**Importante:** Sólo se permite que un proyecto/dataset sea desarrollado por un equipo de trabajo. El listado de proyectos sugeridos puede ser consultado en el enlace proporcionado.

### Requisitos del repositorio

Cada equipo de trabajo debe crear un repositorio GitHub en el cual se debe alojar:

- Un reporte del proyecto (en formato PDF)
- Al menos un notebook en el que se puedan reproducir los resultados incluidos en el reporte
- Un README con indicaciones claras de cómo interactuar correctamente con el repositorio

### Formato del reporte

Para el reporte se debe usar la plantilla IEEE para los artículos publicados en Transactions. Se recomienda usar un editor de texto LaTeX, en particular Overleaf. Tanto el reporte como el/los notebooks deben contener las secciones descritas a continuación.

---

## 2. Descripción del problema (20%)

La primera parte del informe está destinada a realizar una descripción del problema, hacer un análisis exploratorio de los datos que permita comprender cómo está compuesta la base de datos y a definir la aproximación que desde el punto de vista de Machine Learning (ML) será seguida por parte del equipo para la solución del problema.

### Todos los informes deben contener:

1. **Una descripción clara del contexto del problema**, donde se refleje la utilidad de desarrollar una solución basada en ML para dicho problema.

2. **Una descripción de la composición de la base de datos** incluyendo (pero no limitándose):

   - El número de muestras
   - El número de variables y su significado
   - La existencia de datos faltantes y, si es del caso, la estrategia de imputación de datos seguida
   - El tipo de codificación usado para las diferentes variables del problema

3. **El tipo de configuración o paradigma de aprendizaje** que el equipo de trabajo decidió como apropiado para el abordaje del problema y su justificación.

---

## 3. Estado del arte (10%)

El propósito fundamental de esta fase del proyecto es que los grupos de trabajo revisen literatura especializada del campo de ML en la que se presenten soluciones a problemas similares al descrito en la sección 2.

### Requisitos

Realice una búsqueda de **al menos 4 artículos** que hayan abordado el mismo problema que ustedes están trabajando. Incluya, en la medida de lo posible, trabajos que hayan empleado la misma base de datos.

### Para cada artículo, describa brevemente:

- ¿Qué configuración o paradigma de aprendizaje se usa en el trabajo?
- ¿Qué técnica(s) de aprendizaje usan los autores para solucionar el problema planteado?
- ¿Qué metodología de validación usaron?
- ¿Cuáles fueron las métricas empleadas para evaluar el desempeño del sistema? En caso de que alguna métrica no haya sido vista en clase, se debe describir en qué consiste y presentar su definición matemática.
- ¿Cuáles fueron los resultados obtenidos en cada uno de los trabajos citados?

### Fuentes recomendadas

Se recomienda buscar trabajos en las bases de datos:

- **Elsevier**
- **IEEE**
- **Springer** (http://link.springer.com) - acceso limitado para la Universidad

**Preferiblemente incluir artículos publicados en revista, no en congresos o conferencias.**

Se recomienda utilizar el buscador **Google Scholar** para encontrar artículos que hayan citado la base de datos seleccionada.

**Importante:** No utilice más de una página del informe para esta descripción.

---

## 4. Entrenamiento y Evaluación de los Modelos (30%)

En esta sección se debe describir el diseño experimental y los resultados obtenidos durante las simulaciones.

### 4.1. Configuración experimental

1. **Describa la metodología de validación** escogida para entrenar y evaluar los modelos de ML. En caso de requerir etapas adicionales, como la utilización de técnicas de sub o sobre muestreo, la forma en la que fueron usadas debe estar descrita en este apartado.

2. **Incluya una tabla** en la que especifique el conjunto de hiperparámetros que fueron analizados durante el proceso de evaluación de cada modelo, junto con la descripción de la malla de valores usada para cada uno.

### Modelos requeridos

Cada proyecto debe comparar **al menos 5 modelos de aprendizaje**, entre los que se deben incluir:

- Un modelo **paramétrico** basado en funciones discriminantes gausianas o en regresión (lineal o logística según se requiera)
- Un modelo **no paramétrico**
- Un modelo basado en el **ensamble de árboles de decisión**
- Una **red neuronal artificial**
- Una **máquina de vectores de soporte**

3. **Describa cuáles serán las métricas de desempeño** que se usarán para evaluar el sistema y justifique su utilización.

### 4.2. Resultados del entrenamiento de Modelos

Presente los resultados de la experimentación para cada uno de los modelos evaluados, en los que se evidencie el efecto de los hiperparámetros en el desempeño del modelo.

### Requisitos de presentación

- Haga uso de **tablas y gráficas** que ayuden al lector a comprender de manera clara los resultados
- **TODAS las figuras y tablas** deben ser introducidas en el texto del informe y contener un caption que las describa
- **Todas las figuras** deben incluir el nombre de los ejes para que el lector pueda comprender la información que se presenta
- Las **medidas de desempeño** deben incluir los correspondientes intervalos de confianza estimados durante la fase de validación
- **Recuerde incluir resultados** de entrenamiento, validación y test

---

## 5. Reducción de dimensión (20%)

En esta fase del proyecto se deben evaluar diferentes técnicas de reducción de dimensión y establecer si es posible reducir la complejidad del modelo final.

### 5.1. Selección de características

1. **Realice un análisis individual** de cada una de las características, a partir de medidas de correlación e índices que reflejen la capacidad discriminativa de las variables (según sea el caso). Identifique de acuerdo con este análisis: ¿si existen y cuáles son las características candidatas a ser eliminadas?

2. **Realice selección de características** por el método de búsqueda secuencial ascendente o descendente y evalúe el subconjunto de características encontrado, en los **2 mejores modelos predictivos** encontrados en la sección 4.

### Requisitos

- Cada grupo debe **decidir la función criterio** a usar en el algoritmo de selección, justificando su decisión
- **Incluya una tabla** con los resultados, indicando el porcentaje de reducción alcanzado y las demás medidas de desempeño
- **Recuerde incluir** en el informe cuál fue el criterio de selección usado y por qué

### 5.2. Extracción de características

**Use el método PCA** para encontrar un conjunto de componentes principales inferior al número de variables original y evalúe nuevamente en los **2 mejores modelos de predicción** encontrados en la sección 4.

### Requisitos

- Cada grupo debe **decidir el criterio** para seleccionar el número de componentes principales justificando su decisión
- **Incluya una tabla** con los resultados, indicando el porcentaje de reducción alcanzado y las demás medidas de desempeño
- **Incluya una sección de discusión y conclusiones** sobre la evaluación completa de la solución desarrollada
- **Incluya una comparación** de sus resultados con los descritos en la sección 3

---

## 6. Evaluación (20%)

Para la evaluación final del proyecto se tendrán en cuenta los siguientes criterios:

### Criterios de evaluación

1. **Alcance de los objetivos** de cada una de las secciones anteriores
2. **No superar las 10 páginas** en el reporte
3. **Orden y claridad del repositorio GitHub** para la reproducción de los resultados
4. **Sustentación**: cada grupo debe preparar un **video de 10 minutos** en el que se presente un resumen del proyecto. El video será proyectado en una sesión de clase y los estudiantes deberán responder a las preguntas del público. La capacidad de cada integrante del grupo de responder a las preguntas será evaluada de manera individual.

### Nota importante

**La sección 2 y la mitad de la sección 3** serán evaluadas en la primera entrega de avance del proyecto.

---

_Introduction to Machine Learning_
