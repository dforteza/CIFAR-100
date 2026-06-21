# CIFAR-100

## Descripción

Proyecto de clasificación de imágenes sobre el dataset **CIFAR-100** (100 clases, 60.000 imágenes de 32x32 píxeles) mediante redes neuronales convolucionales (CNN) con Keras/TensorFlow.

El objetivo es maximizar la precisión en el conjunto de test siguiendo una metodología progresiva: se parte de un modelo base sencillo y se mejora en dos pasos sucesivos, comparando el rendimiento en cada etapa mediante accuracy y F1-score.

## Instrucciones

1. Abrir el notebook directamente en Colab:

   [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/dforteza/CIFAR-100/blob/main/cifar100.ipynb)

   O clonar el repositorio y abrirlo localmente con Jupyter:
   ```bash
   git clone https://github.com/dforteza/CIFAR-100.git
   ```
2. Instalar las dependencias:
   ```bash
   pip install tensorflow keras numpy pandas matplotlib scikit-learn scikit-image seaborn opencv-python
   ```
3. Ejecutar las celdas de `cifar100.ipynb` en orden.

## Modelos y resultados

Se entrenaron y compararon tres modelos de forma incremental:

| Modelo | Accuracy (test) | F1-score | Técnicas |
|---|---|---|---|
| Base | 37.95% | — | CNN simple (2 bloques conv + pooling) |
| Base + Data Augmentation | 44.37% | — | + `ImageDataGenerator` (rotación, zoom, brillo...) |
| Optimizado + Data Augmentation | **63.05%** | **62.46%** | + optimizador Nadam (lr=0.0001), Dropout, Batch Normalization |

**Nota sobre el resultado final:** la mayor parte de la mejora entre el segundo y el tercer modelo (~20 puntos de accuracy) viene del cambio de optimizador (comparado contra RMSProp y Adam) y de las técnicas de regularización (Dropout, Batch Normalization), no solo de Data Augmentation — esta última, aplicada sola sobre el modelo base, solo aportó ~6 puntos.

## Recursos

- [CIFAR-100 dataset](https://www.cs.toronto.edu/~kriz/cifar.html) — página oficial del dataset (Krizhevsky)
- [Keras](https://keras.io) / [TensorFlow](https://www.tensorflow.org) — documentación oficial
- [ImageDataGenerator](https://www.tensorflow.org/api_docs/python/tf/keras/preprocessing/image/ImageDataGenerator) — referencia de Data Augmentation usado en el proyecto
