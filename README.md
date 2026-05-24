# Machine Learning - Predicción de Salario

## Descripción del proyecto

Este proyecto consiste en el desarrollo de un sistema de Machine Learning que permite preparar datos, entrenar un modelo, evaluar su desempeño y mejorarlo.

El objetivo principal es construir un modelo capaz de predecir el salario de estudiantes con base en diferentes características académicas, habilidades técnicas, experiencia y otros factores relacionados con su perfil profesional.

## Dataset seleccionado

Para este proyecto se seleccionó el dataset **Student Placement and Salary Dataset - Skills Based**, disponible en Kaggle.

Este conjunto de datos contiene información relacionada con estudiantes, sus calificaciones, habilidades, experiencia en proyectos, prácticas profesionales, tipo de empresa, rol laboral y salario estimado. Debido a estas características, el dataset es adecuado para aplicar técnicas de regresión y construir un modelo predictivo enfocado en la estimación de salario.

**Dataset:**  
https://www.kaggle.com/datasets/amaymishra11/student-placement-and-salary-dataset-skills-based

## Objetivo del primer avance

En este primer avance se trabajó principalmente en la preparación inicial del conjunto de datos. Las actividades realizadas incluyen:

- Selección del dataset.
- Carga y exploración inicial de los datos.
- Separación de variables independientes y variable objetivo (variable a predecir).
- División del dataset en conjuntos de entrenamiento y prueba.
- Identificación de variables numéricas y categóricas. 
- Preprocesamiento de los datos.
- Aplicación de técnicas de escalamiento.

## Metodología inicial

Para la separación de los datos en conjuntos de entrenamiento y prueba, así como para el preprocesamiento inicial, se tomó como referencia una guía del dataset Titanic en Kaggle.

**Guía de referencia:**  
https://www.kaggle.com/code/reighns/titanic-a-complete-beginner-s-guide#4)-Feature-Engineering/Selection-

Con esta guía pude aplicar un analisis inicial, el escalamiento de los datos y aplicar el One Hot Encoding para variables categóricas. De igual manera todas las librerias fueron tomadas de la guía.

## Etapas del proyecto

El proyecto se desarrollará de forma progresiva siguiendo las siguientes etapas:

### 1. Generación o selección del set de datos

Se seleccionó un dataset relacionado con colocación laboral y salarios de estudiantes. Además, se realizará la separación de los datos en conjuntos de entrenamiento y prueba para poder evaluar correctamente el desempeño del modelo.

### 2. Preprocesamiento de los datos

Se aplicarán técnicas de limpieza, transformación y escalamiento de datos. Esto incluye el tratamiento de valores nulos, codificación de variables categóricas y normalización o estandarización de variables numéricas cuando sea necesario.

### 3. Implementación del modelo

Se seleccionará un modelo de Machine Learning respaldado por literatura o artículos relacionados con el estado del arte. Posteriormente, se implementará utilizando un framework adecuado, como Scikit-learn.

### 4. Evaluación inicial del modelo

Se elegirán métricas apropiadas para evaluar el desempeño del modelo. En el caso de un problema de regresión, se pueden utilizar métricas como MAE, MSE, RMSE o R². Los resultados obtenidos serán reportados e interpretados.

### 5. Refinamiento del modelo

Se medirá el desempeño del modelo inicial y se realizarán ajustes de hiperparámetros o modificaciones en la arquitectura del modelo. Finalmente, se compararán los resultados antes y después del refinamiento para identificar posibles mejoras.

### 6. Entrega final y correcciones

Se documentarán las correcciones realizadas, los cambios aplicados al modelo y los resultados finales obtenidos.

## Tecnologías utilizadas

- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- Seaborn
- Jupyter Notebook / Google Colab

## Estado actual del proyecto

Actualmente, el proyecto se encuentra en la etapa inicial de selección del dataset, separación de datos, preprocesamiento y escalamiento. En las siguientes fases se implementará el modelo predictivo, se evaluará su desempeño y se realizarán ajustes para mejorar los resultados.
