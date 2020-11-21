---
layout: post
title: Redes Neuronales Artificiales
---
Parte 1: Introducción al Deep Learning

## Contenido

[1.Introducción](#1.Introducción)
   * [1.1.La Neurona](#1.1.La_Neurona)
   * [1.2.El Perceptrón](#1.2.El_Perceptrón)

[2.Recursos](#2.Recursos)   


## 1.Introducción

Hablar de [Redes Neuronales Artificiales](https://en.wikipedia.org/wiki/Artificial_neural_network) , [Machine Learning](https://en.wikipedia.org/wiki/Machine_learning) o [Deep Learning](https://en.wikipedia.org/wiki/Deep_learning) es algo que está muy de moda. Desde imagenes generadas en forma artificial [GANS](https://thispersondoesnotexist.com/) hasta [chatbots](https://www.youtube.com/watch?v=otvqkWFvUZU&ab_channel=DotCSV) que nos dan conversaciónes muy reales o modelos predictivos muy precisos, autos autónomos y muchas cosas que en un pasado cercano parecía lejano. Estamos en una ciclo de crecimiento exponencial [Ley de moore](https://en.wikipedia.org/wiki/Moore%27s_law), en el cual el cálculo computacional cada vez es mas rápido y los componentes son mas pequeños. Un dispositivo celular de esta epoca "2020" es mucho mas rápido que el hardware que se uso para ir a la luna, gracias a los avances técnológicos y las personas involucradas en muchos años de estudio prueba y error; Entender la complejidad de los algoritmos y todas las partes involucradas por completo lleva su tiempo, sin embargo hay mucho software desarrollado para que alguien que está aprendiendo con o sin experiencia en programación ya pueda estar experimentando con esta técnología. Aprender algo nuevo hoy es tan fácil como abrir el navegador y escribir lo que necesitamos saber o pedirle a una máquina que lo haga por nosotros.

![](https://www.iartificial.net/wp-content/uploads/2019/06/monalisa.gif)

<br>
<br>

![](https://raw.githubusercontent.com/jjups96/fast-style-transfer/master/examples/thumbs/johnson.png)

_[Michael Nielsen](http://neuralnetworksanddeeplearning.com/index.html) nos da una introducción en su libro: las Redes neuronales son un hermoso paradigma de programación inspirado en la biología que permite que una computadora aprenda de los datos de observación.El aprendizaje profundo, es un poderoso conjunto de técnicas para aprender en redes neuronales, actualmente ambos brindan las mejores soluciones a muchos problemas en el reconocimiento de imágenes, reconocimiento de voz y procesamiento del lenguaje natural._


### 1.1.La_Neurona    

Una neurona biológica es una célula (componente principal del sistema nervioso), cuya función principal es recibir, procesar y transmitir información a través de señales químicas y eléctricas gracias a la excitabilidad eléctrica de su membrana plasmática. Están especializadas en la recepción de estímulos y conducción del impulso nervioso entre ellas mediante conexiones llamadas sinapsis, o con otros tipos de células como, por ejemplo, las fibras musculares de la placa motora. 

**Morfología:** Las neuronas presentan características que sustentan sus funciones: un cuerpo celular, llamado soma opericario central; una o varias prolongaciones cortas que generalmente transmiten impulsos hacia el soma celular, denominadas dendritas; y una prolongación larga, denominada axón o cilindro-eje, que conduce los impulsos desde el soma hacia otra neurona u órgano.

**Red Neuronal** se define como una población de neuronas físicamente interconectadas o un grupo de neuronas aisladas que reciben señales que procesan a la manera de un circuito reconocible. La comunicación entre neuronas implica un proceso electroquímico, mediante el cual una neurona es excitada a partir de cierto umbral.



<br>
<br>
<br>

![](https://i.imgur.com/kj5i6dH.gif)

<br>
<br>
<br>

En el siglo XIX [Santiago Ramón y Cajal](https://es.wikipedia.org/wiki/Neurona#:~:text=y%20las%20sinapsis.-,Funci%C3%B3n%20de%20las%20neuronas,se%C3%B1ales%20el%C3%A9ctricas%20denominadas%20impulsos%20nerviosos) situó por primera vez a las neuronas como elementos funcionales del sistema nervioso y propuso que actuaban como entidades discretas que, intercomunicándose, establecían una especie de red mediante conexiones especializadas. 

---

### 1.2.El_Perceptrón

En base a la información conocida en las décadas de 1950 y 1960 fue elaborado el concepto de perceptrones por el científico [Frank Rosenblatt](https://en.wikipedia.org/wiki/Frank_Rosenblatt) , inspirado en trabajos anteriores de [Warren McCulloch](https://en.wikipedia.org/wiki/Warren_Sturgis_McCulloch) y [Walter Pitts](https://es.wikipedia.org/wiki/Walter_Pitts). 

En el Laboratorio Aeronáutico de Cornell en el año 1957 , [Frank Rosenblatt](https://en.wikipedia.org/wiki/Frank_Rosenblatt) construyó un dispositivo electrónico, siguiendo los principios biológicos de las neuronas demostrando capacidad para aprender. los cuales se simularon inicialmente en una computadora [IBM 704](https://en.wikipedia.org/wiki/IBM_704), cuando se sostenía un triángulo ante el ojo del perceptrón, este captaba la imagen y la transmitía a lo largo de una sucesión aleatoria de líneas a las unidades de respuesta, donde se registró la imagen. 

![](https://www.simplilearn.com/ice9/free_resources_article_thumb/emergence-of-perceptron-with-diagram-of-simplified-model.jpg)

**"Perceptron Research from the 50's & 60's :"** En el siguiente video podemos ver un fragmento de un documental llamado "The Machine that Changed the World" en donde se muestra el funcionamiento del dispositivo, el cual desde imagenes de hombres y mujeres predice su género. [ver video](https://www.youtube.com/watch?v=cNxadbrN_aI&ab_channel=ArxivInsights)

[![Perceptrón](https://upload.wikimedia.org/wikipedia/commons/7/7d/IBM_704_mainframe.gif)](https://www.youtube.com/watch?v=cNxadbrN_aI&ab_channel=ArxivInsights)

Mucho tiempo en el cajon guardado esta tecnología no fue explotada y fue descartada dado que aun faltaban piezas claves para el desarrollo inteligente de los modelos matemáticos y la complejidad de cálculo estaba limitada al hardware de la época.

**La neurona artificial o perceptrón**  
 Modelo lineal


![](https://raw.githubusercontent.com/Azhura/Cursos/master/imagenes/DL/Neurona.png)   

![](https://raw.githubusercontent.com/Azhura/Cursos/master/imagenes/Latex/latex_01.jpg)
---

## 2.Recursos

[Neurona](https://es.wikipedia.org/wiki/Neurona)     
[The Machine that Changed the World](https://www.youtube.com/watch?v=enWWlx7-t0k&ab_channel=LeonardoRomandaRosa)   
[Deep Tutorial ANN](https://www.kaggle.com/shrutimechlearn/deep-tutorial-1-ann-and-classification)
[ryanholbrook](https://www.kaggle.com/ryanholbrook/a-single-neuron)   
[Michael Nielsen](http://neuralnetworksanddeeplearning.com/index.html)

