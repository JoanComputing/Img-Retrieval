# Recuperación de Imágenes Basada en Contenido

## Descripción
Este proyecto implementa y evalúa distintos métodos de procesamiento de imágenes avanzados, como **RootSIFT**, **ResNet50**, y una versión mejorada de **CNN** con *GeM pooling* y *PCA whitening*. El objetivo es comparar su desempeño en la tarea de recuperación de imágenes utilizando los datasets **ROxford** y **RParis**.

## Requisitos
Es necesario descargar el dataset desde el siguiente enlace:

[Descargar Dataset](https://drive.google.com/file/d/1dF4dcq3HobxMg57uM-ZN70wD1pjtYlok/view)

### Preparación del Dataset:
1. Descarga el archivo ZIP desde el enlace.
2. Descomprime el archivo en la misma carpeta donde se encuentran los scripts.

## Integrantes
- **Juan Vergara R.**

## Metodología

1. **Extracción de Características**  
   Se implementaron tres métodos principales para la extracción de características:
   - **RootSIFT**: Mejora de SIFT utilizando normalización L1 y transformación raíz cuadrada.
   - **ResNet50**: Red convolucional preentrenada en ImageNet para extracción de características globales.
   - **CNN Mejorada**: Versión optimizada de ResNet50 utilizando *GeM pooling* y reducción dimensional con *PCA whitening*.

2. **Agrupamiento y Codificación**  
   Se aplicó el algoritmo **K-means** para agrupar características y generar histogramas visuales:
   - Diccionario de palabras visuales con **5000 clústeres**.
   - Representación de imágenes como histogramas codificados.

3. **Búsqueda Eficiente**  
   Se implementaron optimizaciones para acelerar la búsqueda:
   - **KD-Tree**: Estructura eficiente para búsqueda de vecinos cercanos.
   - **PCA Whitening**: Reducción de dimensionalidad para mejorar la eficiencia.

4. **Evaluación**  
   Los métodos se evaluaron en términos de **Mean Average Precision (mAP)** para tres niveles de dificultad:
   - **Easy**, **Medium** y **Hard**.

## Resultados

### Métricas de Desempeño
| Método              | Dataset  | mAP Easy | mAP Medium | mAP Hard |
|---------------------|----------|----------|------------|----------|
| **RootSIFT**        | ROxford  | 0.242    | 0.188      | 0.058    |
| **RootSIFT**        | RParis   | 0.437    | 0.339      | 0.146    |
| **CNN (ResNet50)**  | ROxford  | 0.121    | 0.087      | 0.021    |
| **CNN (ResNet50)**  | RParis   | 0.110    | 0.089      | 0.036    |
| **CNN Mejorada**    | ROxford  | 0.206    | 0.140      | 0.042    |
| **CNN Mejorada**    | RParis   | 0.226    | 0.154      | 0.044    |

### Observaciones
- **RootSIFT** mostró un mejor rendimiento general al capturar características locales robustas.
- La **CNN Mejorada** logró mejoras significativas respecto a la versión estándar gracias a *GeM pooling* y *PCA whitening*.
- El uso de **KD-Tree** y **PCA** permitió optimizar el tiempo de búsqueda sin sacrificar precisión.

## Conclusiones
El proyecto demostró que:
- Métodos tradicionales como **RootSIFT** siguen siendo efectivos para tareas de recuperación de imágenes.
- La optimización de redes neuronales, mediante técnicas como *GeM pooling* y *PCA whitening*, puede cerrar la brecha entre métodos clásicos y modernos.
- Las optimizaciones de búsqueda son clave para aplicaciones a gran escala.

## Referencias
1. A. Rosebrock, *Implementing RootSIFT in Python and OpenCV*, 2015.
2. F. Radenović et al., *Revisiting Oxford and Paris: Large-scale image retrieval benchmarking*, 2018.
