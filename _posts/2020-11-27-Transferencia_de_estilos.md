---
layout: post
title: Un algoritmo neuronal de estilo artístico
---
Transferencia de estilos con Redes Neuronales Convolucionales

Los humanos han dominado la habilidad de crear experiencias visuales únicas mediante la composición de una interacción compleja entre el contenido y el estilo de una imagen (La Pintura), sin embargo, en otras áreas clave de la percepción visual, como el reconocimiento de objetos y rostros, el desempeño fue demostrado recientemente por una clase de modelos de visión inspirados biológicamente llamados Redes Neuronales Profundas. 

Este campo de las redes neuronales es algo que está evolucionando constantemente y el tipo de estructura utilizada para está técnica nos lleva especificamente al sistema de **Redes Neuronales Convolucionales** el cual utiliza representaciones neuronales para separar y recombinar el contenido y el estilo de imágenes arbitrarias, proporcionando un algoritmo neuronal para la creación de imágenes artísticas.

Estructura básica de una RNC o CNN

### Video recomendado 
* (click) en la imagen 

[![CNN](https://ia-latam.com/wp-content/uploads/2019/02/n8-1.jpg)](https://www.youtube.com/watch?v=HyZFfBU0ADg&list=PL9E7H1rzXKFKV9XIXBxwlgubk_2EZMrcB&ab_channel=codificandobits)


### ejemplo 1

![](https://raw.githubusercontent.com/Azhura/Cursos/master/imagenes/DL/suquia_01.png)

* La imagen original de la izquierda pertenece a una fotografía de la cañada por el cual pasa el río suquía en la Provincia de Córdoba Argentina.     

* La imagen central llamada "La noche estrellada" Obra de Vincent van Gogh , es la imagen tomada para la transferencia del estilo.

* La imagen resultante es la combinación del estilo de van Gogh aplicada a la fotografía original, logrando una perfecta adaptación.

### Ejemplo 2

![](https://raw.githubusercontent.com/Azhura/Cursos/master/imagenes/DL/cba_Plza01.png)

* La imagen original de la izquierda pertenece a una fotografía de la plaza San Martín en la Provincia de Córdoba Argentina.     

* La imagen central llamada "El grito" Obra de Edvard Munch , es la imagen tomada para la transferencia del estilo.

* La imagen resultante es la combinación del estilo de Edvard Munch aplicada a la fotografía original.

Realmente he pasado varias horas de diversión con este código, y no deja de sorprenderme la complejidad de cosas que se pueden lograr. Te invito a ingresar [aquí](https://www.tensorflow.org/hub/tutorials/tf2_arbitrary_image_stylization) para implementarlo con TensorFlow.

![](https://raw.githubusercontent.com/Azhura/Cursos/master/imagenes/DL/calito_cnn.jpg)

## Recursos

[TF](https://www.tensorflow.org/)   
[TF Doc](https://tensorflowdoc.readthedocs.io/es/latest/6tet.html)  
[paper](https://arxiv.org/abs/1705.06830)   
[magenta](https://github.com/magenta/magenta/tree/master/magenta/models/arbitrary_image_stylization)   
