# Detección de Manipulación de Imágenes usando Ingeniería de Características (CASIA 2.0)

## Descripción del proyecto

Este proyecto forma parte del curso CC3094 – Security Data Science y tiene como objetivo realizar un análisis exploratorio de datos (EDA) e ingeniería de características sobre un dataset de imágenes, con el fin de preparar la información para futuras etapas de modelado.

El problema abordado consiste en la detección de imágenes manipuladas, diferenciando entre imágenes auténticas y alteradas. Este tipo de problema es relevante en el contexto de seguridad informática, análisis forense digital y verificación de contenido multimedia.

---

## Objetivo

El objetivo de esta primera fase es:

* Analizar el dataset seleccionado mediante técnicas de análisis exploratorio de datos.
* Extraer y construir características relevantes a partir de las imágenes.
* Seleccionar un conjunto inicial de variables que puedan ser utilizadas en modelos de clasificación en etapas posteriores.

---

## Dataset

Se utilizó el dataset **CASIA Image Tampering Detection Evaluation Database (CASIA 2.0)**, el cual contiene imágenes clasificadas en dos categorías:

* **Au (Authentic):** imágenes originales sin modificaciones.
* **Tp (Tampered):** imágenes que han sido manipuladas mediante distintos métodos.

El dataset está compuesto por imágenes en distintos formatos y tamaños, lo cual permite analizar características relacionadas con dimensiones, color y estructura de archivo.

Para efectos de este proyecto, se trabajó con una muestra del dataset con el fin de facilitar el procesamiento y análisis, manteniendo reproducibilidad mediante el uso de una semilla fija en la selección de datos.

---

## Metodología

El desarrollo del proyecto se llevó a cabo en un Jupyter Notebook siguiendo las siguientes etapas:

1. **Carga y preparación de datos**

   * Lectura de imágenes desde el dataset.
   * Filtrado por extensiones válidas.
   * Organización de las clases (Au y Tp).

2. **Análisis exploratorio de datos (EDA)**

   * Distribución de clases.
   * Análisis de dimensiones (width, height).
   * Análisis de tamaño de archivo.
   * Visualización de imágenes de ejemplo.
   * Distribución de variables relacionadas con color y brillo.

3. **Ingeniería de características**

   * Extracción de métricas básicas de cada imagen.
   * Cálculo de estadísticas por canal de color (RGB).
   * Generación de variables derivadas.

4. **Análisis de correlación**

   * Identificación de relaciones entre variables.
   * Evaluación de redundancia entre características.

5. **Selección de características**

   * Definición de un conjunto inicial de variables relevantes para modelado.

---

## Características utilizadas

A partir del dataset se extrajeron las siguientes características:

* **width / height:** dimensiones de la imagen.
* **aspect_ratio:** relación entre ancho y alto.
* **file_size_kb:** tamaño del archivo en kilobytes.
* **brightness:** brillo promedio de la imagen.
* **mean_r, mean_g, mean_b:** promedio de intensidad por canal de color.
* **std_r, std_g, std_b:** desviación estándar por canal de color.

Después del análisis exploratorio y de correlación, se seleccionaron como características principales:

* `file_size_kb`
* `aspect_ratio`
* `brightness`
* `std_r`
* `std_g`
* `std_b`

Estas variables fueron elegidas por su capacidad de capturar variaciones estructurales y de color en las imágenes, además de presentar menor redundancia entre sí.

---

## Hallazgos principales

Durante el análisis exploratorio se observaron los siguientes puntos:

* La distribución de clases se mantiene relativamente balanceada en la muestra utilizada.
* Las dimensiones de las imágenes no presentan diferencias claras entre clases.
* El tamaño del archivo (`file_size_kb`) muestra cierta variabilidad que podría estar asociada a manipulación.
* Las variables relacionadas con color y brillo presentan diferencias leves entre imágenes auténticas y manipuladas.
* Existe correlación entre algunas variables (por ejemplo, entre dimensiones), lo cual motivó la selección de un subconjunto de características más representativas.

En general, aunque existe solapamiento entre clases, algunas variables muestran potencial para ser utilizadas en modelos de clasificación.

---

## Estructura del proyecto

```
├── notebook.ipynb
├── data/
└── README.md
```

---

## Cómo ejecutar

1. Clonar el repositorio o descargar los archivos.
2. Asegurarse de tener instalado Python 3 y las siguientes librerías:

   * pandas
   * numpy
   * matplotlib
   * seaborn
   * opencv o PIL
3. Abrir el archivo `notebook.ipynb` en Jupyter Notebook o Jupyter Lab.
4. Ejecutar las celdas en orden.

---

## Tecnologías utilizadas

* Python
* Jupyter Notebook
* pandas
* numpy
* matplotlib
* seaborn

---

## Próximos pasos

En la siguiente fase del proyecto se planea:

* Entrenar modelos de clasificación utilizando las características seleccionadas.
* Evaluar el desempeño de los modelos mediante métricas apropiadas.
* Explorar nuevas características que puedan mejorar la separación entre clases.
* Optimizar el proceso de selección de variables.

---

## Autores

Gabriel García y Sebas Juarez
Universidad del Valle de Guatemala
CC3094 – Security Data Science
