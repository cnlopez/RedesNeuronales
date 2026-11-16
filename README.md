# Deep Vision in classification tasks

**07MIAR - Redes Neuronales y Deep Learning** · Proyecto de programación

**Grupo 11** · Cesar Nikolai López Martínez

Comparación experimental de dos estrategias de clasificación de imágenes con redes neuronales convolucionales:

1. **CNN diseñada y entrenada desde cero**, construida con experimentación progresiva sobre arquitectura, regularización, optimizador y tamaño de batch.
2. **Redes preentrenadas en ImageNet** (MobileNetV2, ResNet50V2 y Xception) con *transfer learning* y *fine-tuning* progresivo.

## Dataset

[Intel Image Classification](https://www.kaggle.com/datasets/puneet6060/intel-image-classification) (Kaggle): unas 17.000 imágenes de escenas de 150x150 px en 6 clases (*buildings*, *forest*, *glacier*, *mountain*, *sea* y *street*). El dataset no se incluye en el repositorio; el notebook lo descarga con la API de Kaggle.

## Resultados en test (3.000 imágenes)

| Modelo | Accuracy | F1 macro | Parámetros |
|---|---|---|---|
| Clasificador trivial | 17,5 % | - | - |
| CNN base | 80,8 % | 0,807 | 5,4 M |
| CNN final desde cero | 88,6 % | 0,887 | 0,42 M |
| ResNet50V2 | 91,8 % | 0,920 | 23,6 M |
| Xception | 92,2 % | 0,923 | 20,9 M |
| **MobileNetV2 (*fine-tuning* del 15 % final)** | **92,5 %** | **0,927** | 2,3 M |

El *transfer learning* supera a la CNN desde cero de forma estadísticamente significativa (prueba de McNemar, p = 7,7e-12). MobileNetV2 iguala a arquitecturas 9-10 veces mayores, con menos tiempo de entrenamiento.

## Contenido

| Archivo | Descripción |
|---|---|
| `11_LopezMartinez_CesarNikolai.ipynb` | Notebook completo y ejecutado: código, logs de entrenamiento, gráficas, análisis y conclusiones |
| `11_LopezMartinez_CesarNikolai.pdf` | Versión en PDF del notebook, que es el documento entregado |

## Reproducción

1. Abrir el notebook en [Google Colab](https://colab.research.google.com/) con un entorno de GPU.
2. Ejecutar todas las celdas. Se pedirá acceso a Google Drive, donde se guardan los pesos y las métricas de cada experimento, y el archivo `kaggle.json` personal para descargar el dataset.

Requisitos: Python 3, TensorFlow 2.x/Keras 3, scikit-learn, pandas, matplotlib y Pillow (todos disponibles por defecto en Colab).
