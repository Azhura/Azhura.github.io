
# Redes Neuronales Artificiales
**Autor:** Carlos Alberto Gómez Prado | 9-11-2020

## Contenido

[1.Introducción](#1.Introducción)
   * [1.1.La Neurona](#1.1.La_Neurona)
   * [1.2.El Perceptrón](#1.2.El_Perceptrón)  
   * [1.3.Redes Neuronales Artificiales](#1.3.Redes_Neuronales_Artificiales )  

[2.Programando una RNA](#2.Programando_una_RNA)    
   * [2.1 Información y recursos](#2.1.Información)
   * [2.2 Pre procesado de datos](#2.2.Preprocesado)
   * [2.3 Construcción de la RNA](#2.3.Construcción_de_la_RNA)   
   * [2.4 Evaluación del modelo](#2.4.Evaluación)   
   
[3.Conclusión](#3.Conclusión)   

[4.Recursos](#4.Recursos)   


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

**"Perceptron Research from the 50's & 60's :"** En el siguiente video podemos ver un fragmento de un documental llamado "The Machine that Changed the World" en donde se muestra el funcionamiento del dispositivo, el cual desde imagenes de hombres y mujeres predice su género.

[![Perceptrón](https://upload.wikimedia.org/wikipedia/commons/7/7d/IBM_704_mainframe.gif)](https://www.youtube.com/watch?v=cNxadbrN_aI&ab_channel=ArxivInsights)

![](https://www.simplilearn.com/ice9/free_resources_article_thumb/emergence-of-perceptron-with-diagram-of-simplified-model.jpg)

Mucho tiempo en el cajon guardado esta tecnología no fue explotada y fue descartada dado que aun faltaban piezas claves para el desarrollo inteligente de los modelos matemáticos y la complejidad de cálculo estaba limitada al hardware de la época.

**La neurona artificial o perceptrón**  
 Modelo lineal


![](https://raw.githubusercontent.com/Azhura/Cursos/master/imagenes/DL/Neurona.png)   

**Entradas:** $x_1,x_2,x_3$ son las entradas de información de la neurona.Una perceptrón, puede tener una o mas entradas binarias("1" o "0").  

**Pesos:** $ w_1, w_2, w_3$ son números reales que expresan la importancia de las respectivas entradas a la salida.Cada vez que un valor fluye a través de una conexión, se multiplica el valor por el peso de la conexión. Para la entrada x, lo que llega a la neurona es $w * x$. 

**Umbral:** La $b$ es un tipo especial de peso que llamamos el sesgo y en su lugar, ponemos un $w_0 = 1$ en el diagrama para que el valor que llega a la neurona sea sólo b ya que $ 1b = b $. El sesgo permite al perceptrón modificar la salida independientemente de sus entradas.   

**Salida:** La $y$ es la salida de la neurona en la cual se determina por la suma ponderada de $\sum w_1x_1+w_2x_2...$ donde $ Y = \begin{Bmatrix} 0 \ si \ wx + b \leq 0  \\ 1 \ si \ wx + b > 0 \end{Bmatrix}$     

**¿Que podemos hacer con una neurona?**   
- Permite hacer funciones lógicas   
- Primera aproximación a las redes neuronales   
- Capacidad de computación universal    

Este modelo básico tiene sus limitaciones para resolver problemas complejos ya que una neurona por si sola,solo puede resolver pequeñas pruebas y al tener varias entradas los resultados siempre son lineales, con los años se desarrollaron varios modelos y para dar mayor poder de cálculo y la no linealidad que se necesita para el desarrollo actual de los proyectos de hoy en día se utilizan funciones de activación, tema que trataremos en la proxima parte.

### 1.3.Redes_Neuronales_Artificiales 

#### ¿Qué es el aprendizaje profundo ?  

Con el tiempo el poder de cálculo fue creciendo y las computadoras se hicieron mucho mas potentes, apareció el señor [Geoffrey Hinton](https://es.wikipedia.org/wiki/Geoffrey_Hinton) y agregó el condimento ideal para que todo esto sea inteligente [Deep Learning](https://en.wikipedia.org/wiki/Deep_learning).

El aprendizaje profundo(Deep Learning) es un enfoque del aprendizaje automático(Machine Learning) caracterizado por pilas profundas de cálculos. Esta profundidad de cómputo es lo que ha permitido a los modelos de aprendizaje profundo desenmarañar los tipos de patrones complejos y jerárquicos.La traducción del lenguaje natural, el reconocimiento de imágenes y el juego son tareas en las que los modelos de aprendizaje profundo se han acercado o incluso han superado el rendimiento a nivel humano.
Gracias a su potencia y escalabilidad, las redes neuronales se han convertido en el modelo que define el aprendizaje profundo.


**Descripción:** Las redes Neuronales Artificiales (RNA) son una de las principales herramientas más utilizadas en el Machine Learning. Inspirados en el cerebro, tienen como objetivo replicar la forma en que los humanos aprendemos. Las **RNA** se consideran herramientas de modelado de datos estadísticos no lineales en las que se modelan las complejas relaciones entre las entradas y las salidas.

**Capas** Las redes neuronales suelen organizar sus neuronas en capas. Cuando reunimos unidades lineales que tienen un conjunto común de entradas obtenemos una capa densa.Resulta, sin embargo, que dos capas densas sin nada entre ellas no son mejores que una sola capa densa por sí misma. Las capas densas por sí mismas nunca pueden sacarnos del mundo de las líneas y los planos. Lo que necesitamos es algo no lineal, necesitamos una función de activación. 

![](https://i.imgur.com/2MA4iMV.png)

**Función de activación** La función de activación es simplemente una función que aplicamos a cada una de las salidas de una capa. 

![](https://imgstore.nyc3.cdn.digitaloceanspaces.com/bccmort/1594155648872.jpeg)

En la siguiente imagen de ejemplo podemos ver como son ingresados valores a una neurona, la cual ajusta sus pesos de acuerdo a su función de activación modificando la salida. Una neurona por si sola no genera mucha complejidad, pero una red neuronal es mas compleja en cálculo.


![](https://c.mql5.com/2/35/artificialneuron__1.gif)

#### Construcción de modelos secuenciales
El modelo secuencial que hemos estado usando conectará una lista de capas en orden del primero al último: la primera capa recibe la entrada, la última capa produce la salida.

![](https://www.atriainnovation.com/wp-content/uploads/2019/10/Redes_neuronales_esquema.png)

![](https://i.imgur.com/Y5iwFQZ.png)


**Tipos de redes:** Existen múltiples tipos de redes neuronales, cada una de las cuales tiene sus propios casos de uso específicos y niveles de complejidad. La elección de la red adecuada para su tarea depende de los datos con los que se la entrene y de la aplicación específica que tenga en mente. En algunos casos, puede ser conveniente utilizar múltiples enfoques.

![](https://i.stack.imgur.com/LgmYv.png)

## 2.Programando_una_RNA
Implementando una Red Neuronal Artificial aplicada a un problema real de negocio.

### 2.1.Información

Problema de negocio: Modelado de abandono    
Objetivo: se creará un modelo que predecirá si un cliente dejara o no el banco, por medio de una **RNA**.

[**DataSet**](https://www.kaggle.com/shrutimechlearn/churn-modelling) Este conjunto de datos contiene detalles de los clientes de un banco y la variable objetivo es una variable binaria que refleja el hecho de si el cliente abandonó el banco (cerró su cuenta) o si continúa siendo un cliente.   

Información de variables:

**RowNumber:** Número de fila.   
**CustomerId:** Identificación del cliente.   
**Surname:** Apellido del cliente.   
**CreditScore:** La puntuación de crédito del cliente.   
**Geography:** El país del cliente (Alemania/Francia/España).   
**Gender:** El género del cliente (Female/Male).   
**Age:** La edad del cliente.   
**Tenure:** El número de años del cliente en el banco.     
**Balance:** El saldo de la cuenta del cliente.     
**NumOfProducts:** El número de productos bancarios que el cliente utiliza.    
**HasCrCard:** ¿El cliente tiene una tarjeta? (0=No,1=Si)    
**IsActiveMember:** ¿Tiene el cliente una participación activa? (0=No,1=Si)      
**EstimatedSalary:** salario estimado del cliente     
**Exited:** ¿Abandona o no abandona? (0=No,1=Yes)    

Para la creación del modelo se utilizará:   

[TensorFlow 2.0](https://www.tensorflow.org/guide/effective_tf2) es una plataforma de aprendizaje automático de código abierto que Combina cuatro habilidades clave:    
* Ejecución eficiente de operaciones de tensor de bajo nivel en CPU, GPU o TPU.   
* Calcular el gradiente de expresiones diferenciables arbitrarias.    
* Escalar la computación a muchos dispositivos (por ejemplo, la supercomputadora Summit en Oak Ridge National Lab, que abarca 27.000 GPU).   
* Exportación de programas ("gráficos") a tiempos de ejecución externos como servidores, navegadores, dispositivos móviles e integrados. 

[Keras](https://keras.io/) es la **API** de alto nivel de [TensorFlow 2.0](https://www.tensorflow.org/guide/effective_tf2) una interfaz accesible y altamente productiva para resolver problemas de aprendizaje automático, con un enfoque en el aprendizaje profundo moderno. 

### 2.2.Preprocesado
Para que los  datos puedan ser suministrados a una red neuronal la informacion debe ser procesada:   
**a).** En esta primera parte cargaremos el data set y se eliminaran las columnas "RowNumber","CustomerId","Surname", ya que su información para este ejemplo no es relevante.


```python
# librerías
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt
import pandas as pd
# Importar el data set
dataset = pd.read_csv('Churn_Modelling.csv')
# descartamos las columnas RowNumber,CustomerId,Surname,Exited
# y se asigna a la variable "X" como valores independientes.
X = dataset.iloc[:, 3:13].values
# Asignamos "Exited" la variable y para poder predecir.
y = dataset.iloc[:, 13].values
dataset.iloc[:, 3:14].head()
```

    C:\ProgramData\Anaconda3\lib\site-packages\statsmodels\tools\_testing.py:19: FutureWarning: pandas.util.testing is deprecated. Use the functions in the public API at pandas.testing instead.
      import pandas.util.testing as tm
    




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>CreditScore</th>
      <th>Geography</th>
      <th>Gender</th>
      <th>Age</th>
      <th>Tenure</th>
      <th>Balance</th>
      <th>NumOfProducts</th>
      <th>HasCrCard</th>
      <th>IsActiveMember</th>
      <th>EstimatedSalary</th>
      <th>Exited</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>619</td>
      <td>France</td>
      <td>Female</td>
      <td>42</td>
      <td>2</td>
      <td>0.00</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>101348.88</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>608</td>
      <td>Spain</td>
      <td>Female</td>
      <td>41</td>
      <td>1</td>
      <td>83807.86</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>112542.58</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>502</td>
      <td>France</td>
      <td>Female</td>
      <td>42</td>
      <td>8</td>
      <td>159660.80</td>
      <td>3</td>
      <td>1</td>
      <td>0</td>
      <td>113931.57</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3</th>
      <td>699</td>
      <td>France</td>
      <td>Female</td>
      <td>39</td>
      <td>1</td>
      <td>0.00</td>
      <td>2</td>
      <td>0</td>
      <td>0</td>
      <td>93826.63</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>850</td>
      <td>Spain</td>
      <td>Female</td>
      <td>43</td>
      <td>2</td>
      <td>125510.82</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>79084.10</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>



**b).** Se aplicará un OneHotEncoder para la transformación de la información categórica a binaria.


```python
# Codificar datos categóricos
from sklearn.preprocessing import LabelEncoder, OneHotEncoder
labelencoder_X_1 = LabelEncoder()
X[:, 1] = labelencoder_X_1.fit_transform(X[:, 1])
labelencoder_X_2 = LabelEncoder()
X[:, 2] = labelencoder_X_2.fit_transform(X[:, 2])
onehotencoder = OneHotEncoder(categorical_features=[1])
X = onehotencoder.fit_transform(X).toarray()
X = X[:, 1:]
```

    C:\ProgramData\Anaconda3\lib\site-packages\sklearn\preprocessing\_encoders.py:415: FutureWarning: The handling of integer data will change in version 0.22. Currently, the categories are determined based on the range [0, max(values)], while in the future they will be determined based on the unique values.
    If you want the future behaviour and silence this warning, you can specify "categories='auto'".
    In case you used a LabelEncoder before this OneHotEncoder to convert the categories to integers, then you can now use the OneHotEncoder directly.
      warnings.warn(msg, FutureWarning)
    C:\ProgramData\Anaconda3\lib\site-packages\sklearn\preprocessing\_encoders.py:451: DeprecationWarning: The 'categorical_features' keyword is deprecated in version 0.20 and will be removed in 0.22. You can use the ColumnTransformer instead.
      "use the ColumnTransformer instead.", DeprecationWarning)
    

**c).** se dividirá la informacion en conjunto de prueba , test y se aplicará un escalado de variables.     


```python
# Dividir el data set en conjunto de entrenamiento y conjunto de testing
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size = 0.2, random_state = 0)
# Escalado de variables
from sklearn.preprocessing import StandardScaler
sc_X = StandardScaler()
X_train = sc_X.fit_transform(X_train)
X_test = sc_X.transform(X_test)
X_train
```




    array([[-0.5698444 ,  1.74309049,  0.16958176, ...,  0.64259497,
            -1.03227043,  1.10643166],
           [ 1.75486502, -0.57369368, -2.30455945, ...,  0.64259497,
             0.9687384 , -0.74866447],
           [-0.5698444 , -0.57369368, -1.19119591, ...,  0.64259497,
            -1.03227043,  1.48533467],
           ...,
           [-0.5698444 , -0.57369368,  0.9015152 , ...,  0.64259497,
            -1.03227043,  1.41231994],
           [-0.5698444 ,  1.74309049, -0.62420521, ...,  0.64259497,
             0.9687384 ,  0.84432121],
           [ 1.75486502, -0.57369368, -0.28401079, ...,  0.64259497,
            -1.03227043,  0.32472465]])



* La información del dataframe una vez pre procesada quedará un array listo para ser suministrado a nuestra **RNA**.

### 2.3.Construcción_de_la_RNA
**a).** Luego de importar las librerías necesarias Inicializamos una red con Keras, agregando sus entradas y capas ocultas con su función de activación definida para cada capa, agregamos una salida y por último definimos Un "optimizador" que pueda decirle a la red cómo cambiar sus pesos , definiremos su función de perdida para poder medir que tan buenas son las predicciones de la red de acuerdo a la métrica evaluada en este caso elegiremos presición.


```python
#librería Keras 
import keras
from keras.models import Sequential
from keras.layers import Dense

# Inicializar la RNA
classifier = Sequential()

# Añadir las capas de entrada y primera capa oculta
classifier.add(Dense(units = 6, kernel_initializer = "uniform",  
                     activation = "relu", input_dim = 11))

# Añadir la segunda capa oculta
classifier.add(Dense(units = 6, kernel_initializer = "uniform",  activation = "relu"))

# Añadir la capa de salida
classifier.add(Dense(units = 1, kernel_initializer = "uniform",  activation = "sigmoid"))

# Compilar la RNA
classifier.compile(optimizer = "adam", loss = "binary_crossentropy", metrics = ["binary_accuracy"])
```

    Using TensorFlow backend.
    

    WARNING:tensorflow:From C:\ProgramData\Anaconda3\lib\site-packages\tensorflow\python\ops\nn_impl.py:180: add_dispatch_support.<locals>.wrapper (from tensorflow.python.ops.array_ops) is deprecated and will be removed in a future version.
    Instructions for updating:
    Use tf.where in 2.0, which has the same broadcast rule as np.where
    

**b).** Ajustamos nuestro modelo a nuestro conjunto de entrenamiento 


```python
# Modelo RNA con bloques de 10 y 100 vueltas.
model_ANN = classifier.fit(X_train, y_train,  batch_size = 10, epochs = 30)
```

    Epoch 1/30
    8000/8000 [==============================] - 0s 56us/step - loss: 0.3980 - binary_accuracy: 0.8359
    Epoch 2/30
    8000/8000 [==============================] - 0s 55us/step - loss: 0.3983 - binary_accuracy: 0.8363
    Epoch 3/30
    8000/8000 [==============================] - 0s 55us/step - loss: 0.3989 - binary_accuracy: 0.8350
    Epoch 4/30
    8000/8000 [==============================] - 0s 56us/step - loss: 0.3983 - binary_accuracy: 0.8356
    Epoch 5/30
    8000/8000 [==============================] - 0s 56us/step - loss: 0.3982 - binary_accuracy: 0.8360
    Epoch 6/30
    8000/8000 [==============================] - 0s 55us/step - loss: 0.3987 - binary_accuracy: 0.8369
    Epoch 7/30
    8000/8000 [==============================] - 0s 56us/step - loss: 0.3982 - binary_accuracy: 0.8351
    Epoch 8/30
    8000/8000 [==============================] - 0s 55us/step - loss: 0.3987 - binary_accuracy: 0.8364
    Epoch 9/30
    8000/8000 [==============================] - 0s 56us/step - loss: 0.3982 - binary_accuracy: 0.8361
    Epoch 10/30
    8000/8000 [==============================] - 0s 56us/step - loss: 0.3987 - binary_accuracy: 0.8365
    Epoch 11/30
    8000/8000 [==============================] - 0s 56us/step - loss: 0.3987 - binary_accuracy: 0.8365
    Epoch 12/30
    8000/8000 [==============================] - 0s 56us/step - loss: 0.3987 - binary_accuracy: 0.8351
    Epoch 13/30
    8000/8000 [==============================] - 0s 56us/step - loss: 0.3989 - binary_accuracy: 0.8366
    Epoch 14/30
    8000/8000 [==============================] - 0s 56us/step - loss: 0.3981 - binary_accuracy: 0.8366
    Epoch 15/30
    8000/8000 [==============================] - 0s 56us/step - loss: 0.3987 - binary_accuracy: 0.8357
    Epoch 16/30
    8000/8000 [==============================] - 0s 56us/step - loss: 0.3987 - binary_accuracy: 0.8369
    Epoch 17/30
    8000/8000 [==============================] - 0s 56us/step - loss: 0.3985 - binary_accuracy: 0.8351
    Epoch 18/30
    8000/8000 [==============================] - 0s 55us/step - loss: 0.3986 - binary_accuracy: 0.8365
    Epoch 19/30
    8000/8000 [==============================] - 0s 55us/step - loss: 0.3990 - binary_accuracy: 0.8369
    Epoch 20/30
    8000/8000 [==============================] - 0s 55us/step - loss: 0.3986 - binary_accuracy: 0.8346
    Epoch 21/30
    8000/8000 [==============================] - 0s 55us/step - loss: 0.3980 - binary_accuracy: 0.8366
    Epoch 22/30
    8000/8000 [==============================] - 0s 54us/step - loss: 0.3985 - binary_accuracy: 0.8354
    Epoch 23/30
    8000/8000 [==============================] - 0s 55us/step - loss: 0.3982 - binary_accuracy: 0.8357
    Epoch 24/30
    8000/8000 [==============================] - 0s 55us/step - loss: 0.3987 - binary_accuracy: 0.8347
    Epoch 25/30
    8000/8000 [==============================] - 0s 55us/step - loss: 0.3987 - binary_accuracy: 0.8355
    Epoch 26/30
    8000/8000 [==============================] - 0s 55us/step - loss: 0.3984 - binary_accuracy: 0.8364
    Epoch 27/30
    8000/8000 [==============================] - 0s 55us/step - loss: 0.3986 - binary_accuracy: 0.8381
    Epoch 28/30
    8000/8000 [==============================] - 0s 55us/step - loss: 0.3986 - binary_accuracy: 0.8361
    Epoch 29/30
    8000/8000 [==============================] - 0s 55us/step - loss: 0.3985 - binary_accuracy: 0.8363
    Epoch 30/30
    8000/8000 [==============================] - 0s 55us/step - loss: 0.3987 - binary_accuracy: 0.8354
    

### 2.4.Evaluación
En esta sección compararemos nuestro resultado con datos que no han sido entrenados en la red,
con un umbral del 0.5% filtraremos las predicciones y evaluaremos que tan bien le a ido a nuestro modelo.


```python
# Show the learning curves
history_df = pd.DataFrame(model_ANN.history)
history_df.loc[:, ['loss', 'binary_accuracy']].plot();

```


![png](output_19_0.png)



```python
history_df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>loss</th>
      <th>binary_accuracy</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0.398880</td>
      <td>0.834875</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0.399374</td>
      <td>0.837375</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0.399755</td>
      <td>0.834750</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0.399430</td>
      <td>0.837000</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0.398913</td>
      <td>0.835250</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>95</th>
      <td>0.397985</td>
      <td>0.835125</td>
    </tr>
    <tr>
      <th>96</th>
      <td>0.398988</td>
      <td>0.837125</td>
    </tr>
    <tr>
      <th>97</th>
      <td>0.398162</td>
      <td>0.834875</td>
    </tr>
    <tr>
      <th>98</th>
      <td>0.398601</td>
      <td>0.835500</td>
    </tr>
    <tr>
      <th>99</th>
      <td>0.398709</td>
      <td>0.835375</td>
    </tr>
  </tbody>
</table>
<p>100 rows × 2 columns</p>
</div>




```python
# 3 - Evaluar el modelo y calcular predicciones finales
# Predicción de los resultados con el Conjunto de Testing
y_pred  = classifier.predict(X_test)
y_pred = (y_pred>0.5)
# Elaborar una matriz de confusión
from sklearn.metrics import confusion_matrix
cm = confusion_matrix(y_test, y_pred)
cm 
```




    array([[1521,   74],
           [ 193,  212]], dtype=int64)




```python
# Calculate the Accuracy
from sklearn.metrics import accuracy_score
score = accuracy_score(y_test, y_pred)
score
```




    0.8665



Podemos verificar que nuestro modelo a tenido un 86% de precisión en la predicción.


```python
# convert the training history to a dataframe
history_df = pd.DataFrame(model_ANN.history)
# use Pandas native plot method
history_df['loss'].plot()
```




    <matplotlib.axes._subplots.AxesSubplot at 0x1ce8d617ba8>




![png](output_24_1.png)


## 3.Conclusión


```python
y_pred
```




    array([[False],
           [False],
           [False],
           ...,
           [False],
           [False],
           [False]])



## 4.Recursos

[Neurona](https://es.wikipedia.org/wiki/Neurona)     
[The Machine that Changed the World](https://www.youtube.com/watch?v=enWWlx7-t0k&ab_channel=LeonardoRomandaRosa)   
[Deep Tutorial ANN](https://www.kaggle.com/shrutimechlearn/deep-tutorial-1-ann-and-classification)


```python

```
