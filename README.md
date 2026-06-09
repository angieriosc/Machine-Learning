# Machine Learning - Predicción de Salario

Proyecto de Machine Learning para predecir el salario anual de estudiantes recién egresados utilizando el dataset **Student Placement & Salary**. El salario se encuentra expresado en **LPA** (*Lakhs Per Annum*), donde 1 LPA equivale aproximadamente a $18,100 pesos anuales.

El objetivo principal es desarrollar modelos de regresión capaces de estimar el salario de un estudiante con base en sus características académicas, habilidades técnicas, experiencia, proyectos realizados y tipo de compañía.

---

## Descripción del proyecto

Este proyecto aplica un flujo completo de Machine Learning para resolver un problema de regresión. El proceso incluye desde la limpieza y preparación de los datos hasta el entrenamiento, comparación y evaluación de diferentes modelos.

Las etapas principales del proyecto fueron:

* Análisis exploratorio de datos.
* Revisión de variables numéricas y categóricas.
* Limpieza de valores nulos.
* Eliminación de variables no relevantes.
* Codificación de variables categóricas.
* Normalización de variables numéricas.
* Separación de datos en entrenamiento, validación y prueba.
* Entrenamiento de modelos de regresión.
* Evaluación mediante MAE, RMSE y R².
* Generación de gráficas para analizar resultados.

Se implementó un modelo inicial de regresión, una red neuronal de regresión y un modelo **Random Forest Regressor**. El objetivo fue comparar su desempeño y seleccionar el modelo con mejor comportamiento en datos no vistos.

---

## Dataset

El dataset utilizado fue **Student Placement & Salary**, compuesto por información académica, técnica y laboral de estudiantes recién egresados.

El conjunto de datos original contiene:

* **9000 registros**
* **20 columnas**
* Variables numéricas y categóricas
* Variable objetivo: `salary_lpa`

La variable `salary_lpa` representa el salario anual del estudiante en LPA.

---

## Variables del dataset

| Variable              | Tipo                       | Descripción                                                                                                                                        |
| --------------------- | -------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| `student_id`          | Categórica / Identificador | Identificador único de cada estudiante.                      |
| `cgpa`                | Numérica                   | Promedio académico del estudiante.                                                                             |
| `branch`              | Categórica                 | Rama o especialidad de ingeniería del estudiante.       |
| `college_tier`        | Numérica / Ordinal         | Nivel o categoría de la universidad del estudiante. Puede influir en oportunidades laborales.                                                      |
| `python_skill`        | Binaria                   | Cuenta con habilidad en Python.                                                                                   |
| `dsa_skill`           | Binaria                   | Cuenta con habilidad en estructuras de datos y algoritmos.                                                                                           |
| `ml_skill`            | Binaria                   | Cuenta con habilidad en Machine Learning.                                                                                                            |
| `web_dev_skill`       | Binaria                   | Cuenta con habilidad en desarrollo web.                                                                                                              |
| `coding_score`        | Numérica                   | Puntaje general de programación del estudiante.                                                                                   |
| `communication_score` | Numérica                   | Puntaje de habilidades de comunicación.                                                                                       |
| `aptitude_score`      | Numérica                   | Puntaje de aptitud lógica o razonamiento.                                                                                        |
| `internships`         | Numérica                   | Número de prácticas profesionales realizadas por el estudiante.                                                                                    |
| `projects`            | Numérica                   | Número de proyectos realizados.                                                                                                  |
| `backlogs`            | Numérica                   | Número de materias reprobadas o pendientes.                                                                                   |
| `resume_score`        | Numérica                   | Puntaje del currículum del estudiante.                                                                                            |
| `skill_score`         | Numérica                   | Puntaje global de habilidades.                                                                                                                      |
| `placed`              |  Binaria         | Indica si el estudiante fue colocado laboralmente.  |
| `company_type`        | Categórica                 | Tipo de compañía donde fue colocado el estudiante. Se conservó y se transformó mediante One Hot Encoding.                                          |
| `job_role`            | Categórica                 | Rol laboral del estudiante.                                                                 |
| `salary_lpa`          | Numérica                   | Variable objetivo. Representa el salario anual en LPA.                                                                                             |

---

## Preprocesamiento de datos

Durante la etapa de preprocesamiento se identificó que el dataset contenía aproximadamente **1.4% de celdas vacías**. Estos valores faltantes correspondían principalmente a estudiantes que no fueron colocados laboralmente.

Debido a que el objetivo del modelo es predecir el salario de estudiantes colocados, se eliminaron las filas con valores faltantes.

También se eliminaron columnas que no aportaban información útil para la predicción:

| Columna eliminada | Motivo                                                                      |
| ----------------- | --------------------------------------------------------------------------- |
| `student_id`      | Es un identificador único y no representa características del estudiante.   |
| `placed`          | Después de limpiar los datos, todos los registros restantes tenían valor 1. |
| `branch`          | No mostró una relación significativa con `salary_lpa`.                      |
| `job_role`        | No mostró una relación significativa con `salary_lpa`.                      |

La variable `company_type` fue conservada porque presentó una relación importante con el salario. Esta variable fue transformada mediante **One Hot Encoding** para convertir sus categorías en columnas binarias.

![Tabla de Correlación](img/correlacion.png)

---

## Normalización

Las variables numéricas fueron normalizadas utilizando **StandardScaler**, con el objetivo de transformar los valores para que tuvieran una media cercana a 0 y una desviación estándar cercana a 1.

Esto ayuda a que las variables con escalas más grandes no tengan mayor influencia durante el entrenamiento del modelo.

Variables normalizadas:

* `cgpa`
* `coding_score`
* `communication_score`
* `aptitude_score`
* `projects`
* `resume_score`
* `backlogs`
* `skill_score`

---

## División de datos

Para entrenar y evaluar los modelos se utilizaron diferentes divisiones del dataset.

Primero se trabajó con una división tradicional:

| Conjunto      | Porcentaje | Uso                                        |
| ------------- | ---------: | ------------------------------------------ |
| Entrenamiento |        80% | Entrenar el modelo                         |
| Prueba        |        20% | Evaluar el rendimiento con datos no vistos |

Después, para mejorar la evaluación y reducir el overfitting, se utilizó una división en tres conjuntos:

| Conjunto      | Porcentaje | Uso                                                |
| ------------- | ---------: | -------------------------------------------------- |
| Entrenamiento |        70% | Entrenar el modelo                                 |
| Validación    |        15% | Revisar el comportamiento durante el entrenamiento |
| Prueba        |        15% | Evaluar el modelo final                            |

---

## Modelos implementados

### Modelo inicial

Se implementó un modelo inicial de regresión para tener una primera aproximación al problema y establecer una base de comparación.

Este modelo permitió observar qué tan bien se podía estimar el salario utilizando las variables disponibles del dataset.

---

### Red neuronal de regresión

Posteriormente, se implementó una red neuronal utilizando TensorFlow/Keras.

La arquitectura general incluyó:

* Capas densas ocultas.
* Función de activación ReLU.
* Una capa de salida con una sola neurona.
* Optimizador Adam.
* Función de pérdida MSE.
* Métrica principal MAE.

La función ReLU fue utilizada en las capas ocultas porque permite que la red aprenda relaciones más complejas entre las variables predictoras.

La capa de salida tiene una sola neurona porque el problema busca predecir un único valor numérico: `salary_lpa`.

---

### Red neuronal ajustada

Después de evaluar el modelo inicial, se realizaron ajustes para mejorar su comportamiento.

Los principales cambios fueron:

* Ajuste en la división de datos.
* Uso de conjunto de validación.
* Modificación del número de épocas.
* Cambio en el tamaño del batch.
* Agregado de capas densas.
* Revisión del MAE de entrenamiento, validación y prueba.

Con estos ajustes se buscó reducir el overfitting y obtener un modelo con mejor capacidad de generalización.

---

### Random Forest Regressor

También se implementó un modelo **Random Forest Regressor** como alternativa a la red neuronal.

Random Forest funciona combinando varios árboles de decisión. Cada árbol aprende patrones diferentes de los datos y, al combinar sus resultados, el modelo puede generar predicciones más estables.

Este modelo fue utilizado porque suele tener buen desempeño en problemas con datos tabulares y puede capturar relaciones no lineales entre las variables.

---

## Métricas de evaluación

El desempeño de los modelos fue evaluado utilizando métricas de regresión.

| Métrica | Descripción                                                                                      |
| ------- | ------------------------------------------------------------------------------------------------ |
| MAE     | Error Absoluto Medio. Indica cuánto se equivoca el modelo en promedio.                           |
| RMSE    | Raíz del Error Cuadrático Medio. Penaliza más los errores grandes.                               |
| R²      | Coeficiente de determinación. Indica qué tan bien el modelo explica la variabilidad del salario. |

El **MAE** fue utilizado como métrica principal porque permite interpretar el error en la misma escala de la variable objetivo.

Por ejemplo, si el modelo obtiene un MAE de 5 LPA, significa que el error promedio es de aproximadamente 5 LPA.

---

## Resultados

Se generó una tabla comparativa con una muestra de valores reales y valores predichos por el modelo. Esta tabla permite observar el comportamiento individual de las predicciones y el error de cada caso.

![Muestra de valores reales y valores predichos](img/muestra_valores_reales_predichos.png)

También se generó una gráfica de **valores reales vs. valores predichos**. En esta gráfica, la línea diagonal representa la predicción ideal. Mientras más cerca estén los puntos de esta línea, mejor es el desempeño del modelo.

![Valores reales vs predichos](img/valores_reales_vs_predichos.png)

Además, se analizó la evolución del **MAE durante el entrenamiento**. Esta gráfica permitió identificar si el modelo estaba aprendiendo correctamente o si presentaba señales de overfitting.

![MAE durante el entrenamiento](img/mae_entrenamiento.png)

---

## Comparación de modelos

Los modelos fueron evaluados principalmente con MAE y R².

| Modelo                  | MAE aproximado | Observación                                          |
| ----------------------- | -------------: | ---------------------------------------------------- |
| Red neuronal ajustada   |       5.57 LPA | Buen comportamiento entre entrenamiento y validación |
| Random Forest Regressor |       5.35 LPA | Mejor resultado general                              |

El modelo **Random Forest Regressor** obtuvo el mejor desempeño general, con un MAE aproximado de **5.35 LPA** y un R² cercano a **0.85**.

Esto significa que el modelo logra explicar aproximadamente el 85% de la variabilidad del salario dentro del conjunto de prueba.

---

## Gráficas generadas

Durante el proyecto se utilizaron diferentes gráficas para analizar el comportamiento de los modelos:

* Tabla de correlación.
* Comparación de valores reales y predichos.
* Gráfica de valores reales vs. valores predichos.
* Evolución del MAE durante el entrenamiento.
* Resultados del modelo Random Forest.

---

## Tecnologías utilizadas

* Python
* Pandas
* NumPy
* Matplotlib
* Scikit-learn
* TensorFlow
* Keras
* Jupyter Notebook / Google Colab

---

## Estructura del repositorio

```text
Machine-Learning-Prediccion-Salario/
│
├── img/
│   ├── correlacion.png
│   ├── muestra_valores_reales_predichos.png
│   ├── valores_reales_vs_predichos.png
│   ├── mae_entrenamiento.png
│   └── random_forest_valores_reales_vs_predichos.png
│
├── Students_salary_FINAL.ipynb
├── Pruebas_modelos.ipynb
├── Articulo_Machine_Learning.pdf
├── student_salary.csv
└── README.md
```

---

## Conclusión

El proyecto permitió aplicar un flujo completo de Machine Learning para resolver un problema de regresión. Se trabajó desde la limpieza y preparación de datos hasta la evaluación de diferentes modelos predictivos.

La red neuronal ajustada logró un comportamiento más estable que el modelo inicial, reduciendo señales de overfitting y mejorando la relación entre entrenamiento y validación.

Sin embargo, el modelo **Random Forest Regressor** obtuvo el mejor resultado general, ya que presentó el menor MAE y un R² cercano a 0.85. Por esta razón, se considera el modelo más conveniente para este conjunto de datos.

Aunque el modelo logra identificar patrones entre las características de los estudiantes y su salario, también se reconoce que el salario puede depender de factores externos que no están incluidos en el dataset, como ubicación, experiencia real, demanda laboral, habilidades blandas y condiciones específicas de cada empresa.

---

## Referencias

Mishra, A. (2026). *Student Placement & Salary Dataset (Skills Based)* [Data set]. Kaggle.
[https://www.kaggle.com/datasets/amaymishra11/student-placement-and-salary-dataset-skills-based](https://www.kaggle.com/datasets/amaymishra11/student-placement-and-salary-dataset-skills-based)

Pedregosa, F., Varoquaux, G., Gramfort, A., Michel, V., Thirion, B., Grisel, O., Blondel, M., Prettenhofer, P., Weiss, R., Dubourg, V., Vanderplas, J., Passos, A., Cournapeau, D., Brucher, M., Perrot, M., & Duchesnay, E. (2011). Scikit-learn: Machine learning in Python. *Journal of Machine Learning Research, 12*, 2825–2830.

TensorFlow. (2024). *El modelo secuencial*. TensorFlow.
[https://www.tensorflow.org/guide/keras/sequential_model?hl=es-419](https://www.tensorflow.org/guide/keras/sequential_model?hl=es-419)

Scikit-learn. (s. f.). *RandomForestRegressor*. Scikit-learn documentation.
[https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestRegressor.html](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestRegressor.html)

Matplotlib Development Team. (2026). *scatter(x, y)*. Matplotlib documentation.
[https://matplotlib.org/stable/plot_types/basic/scatter_plot.html](https://matplotlib.org/stable/plot_types/basic/scatter_plot.html)
