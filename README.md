# Clasificaci-n-de-Razas-de-Perros-con-Transfer-Learning-YOLOv8-
# Clasificación de Razas de Perros con Transfer Learning (YOLOv8)

## Resumen del Proyecto

Este proyecto implementa la técnica de **Transfer Learning (Aprendizaje por Transferencia)** para crear un modelo de **Clasificación de Imágenes** capaz de identificar diversas razas de perros.

Se utilizó un modelo de **Red Neuronal Convolucional (CNN)** previamente entrenado en el vasto *dataset* ImageNet (la **tarea fuente**) y se reajustó (o "fine-tuned") para la tarea específica de clasificación de razas de perros (la **tarea objetivo**). Esto permite alcanzar una alta precisión con un tiempo de entrenamiento significativamente reducido.

###  Dataset Utilizado

* **Nombre:** Dog Breeds
* **Fuente:** [Kaggle - mohamedchahed/dog-breeds](https://www.kaggle.com/datasets/mohamedchahed/dog-breeds/data)
* **Objetivo:** Clasificar una imagen dada en su raza de perro correspondiente.

---

##  Transfer Learning: Metodología

El proceso de Transfer Learning se realizó siguiendo los siguientes pasos metodológicos, basados en el *notebook* de referencia:

1.  **Carga del Modelo Base:** Se utilizó una arquitectura robusta (ej., VGG16, ResNet o Inception) pre-entrenada con los pesos de **ImageNet**. Las capas convolucionales de este modelo son expertas en extraer características visuales genéricas (bordes, texturas).
2.  **Congelamiento de Capas:** Las capas convolucionales iniciales del modelo base se **congelaron** (`layer.trainable = False`). Esto previene que los pesos de las características genéricas sean alterados por el *dataset* de perros, preservando el conocimiento previamente adquirido.
3.  **Adición de Cabezal Clasificador:** Se retiró la capa de salida original del modelo y se reemplazó por un nuevo "cabezal" clasificador, compuesto por capas `Flatten` y `Dense`. 
4.  **Ajuste Fino (Fine-Tuning):** El modelo se entrenó con el *dataset* de razas de perros, actualizando **solo** los pesos de las capas del nuevo cabezal clasificador.

---

## Conclusiones del Estudio

La ejecución de este laboratorio de Transfer Learning demostró la eficiencia de esta técnica:

1.  **Eficiencia Computacional:** Se confirmó una **reducción drástica en el tiempo de entrenamiento** y en los recursos computacionales requeridos, ya que no fue necesario entrenar millones de parámetros desde cero.
2.  **Rendimiento Mejorado:** El modelo adaptado alcanzó rápidamente una **alta precisión** en la clasificación de razas de perros, validando la hipótesis de que las características aprendidas en tareas de clasificación de imágenes generales son transferibles a tareas más específicas.
3.  **Prevención de Overfitting:** La reutilización de la base pre-entrenada, junto con el congelamiento de sus pesos, ayudó a **mitigar el sobreajuste** (*overfitting*) al trabajar con un *dataset* de tamaño limitado.

---

##  Cómo Ejecutar el Notebook

1.  **Requisitos:** Asegúrate de tener **Python** y las librerías listadas en `requirements.txt` instaladas (`tensorflow`/`keras`, `numpy`, `matplotlib`).
2.  **Descargar Datos:** Descarga el *dataset* de Kaggle y organízalo en carpetas `train` y `validation` según la estructura necesaria para Keras.
3.  **Abrir Notebook:** Ejecuta el archivo `Transfer_Learning.ipynb` (o el nombre que hayas usado para el notebook) en un entorno como Jupyter o Google Colab.
4.  **Ejecutar Celdas:** Sigue y ejecuta secuencialmente las celdas del *notebook* para cargar el modelo, construir el nuevo clasificador y ejecutar el proceso de entrenamiento.

---

##  Resultados Obtenidos

* **Precisión de Validación:** Después de **[Número]** épocas, el modelo alcanzó una precisión de validación de aproximadamente **[Ej. 90% - 95%]**.
* **Tiempo por Época:** El tiempo de entrenamiento por época fue de **[Ej. 30 segundos]** (dependiendo del hardware), confirmando la eficiencia del método.

El modelo entrenado es una prueba exitosa del **poder del Transfer Learning** para resolver tareas complejas de visión por computadora con una inversión mínima de tiempo y datos.
