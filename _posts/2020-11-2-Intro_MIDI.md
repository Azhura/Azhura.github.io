---
layout: post
title: Explorando archivos MIDI en Python
---

Extracción y manejo de información con archivos digitales **MIDI** | **2-11-2020**

## Contenido

1.Introducción   
  * 1.1 Reseña (**MIDI**)    
  * 1.2 Conexión (Hardware)   
  * 1.3 Topologías (IN,OUT,THRU)   
  
2.Archivo **MIDI**  

  * 2.1 Exploración (Estructura del archivo)
  * 2.2 Almacenamiento (mid,txt,csv)   

3.Conclusión   

4.Recursos   


## Introducción

### 1.1 Reseña
**MIDI**(Musical Instrument Digital Interface), es un estándar tecnológico creado como convenio entre fabricantes en el año **1983**, que constituyeron la [MMA](https://www.midi.org/about)  (Midi Manufacturers Association), que describe un protocolo de comunicación por medio de conectores y cables permitiendo la comunicación entre varios instrumentos electrónicos,ordenadores o dispositivos entre sí,tales como secuenciadores, computadoras, controles de iluminación, mezcladoras, etc.   

Los instrumentos MIDI pueden ser físicos o emulados por computadora ; se agrupan generalmente en controladores MIDI, que son dispositivos que producen señales MIDI basadas en acciones humanas, y sintetizadores, incluidos samplers, secuenciadores, etc, al tratarse con software son conocidos como DAW y VST, los cuales cumplen las mismas funcionalidades aceptando datos MIDI y creando sonidos.  
[Ejemplo: DAW - Ableton Live](https://www.ableton.com/en/products/live-lite/)   
[Ejemplo: VST - Native Instruments](https://www.native-instruments.com/en/products/komplete/samplers/kontakt-6/)   

![MIDI1](https://blog.landr.com/wp-content/uploads/2016/11/What-Is-Midi_C_Midi-Midi_1200x627-1.jpg)

### 1.2 Conexión 

**Cable:**  Para la conexion de los distintos equipos físicos se utilizan cables MIDI con conector DIN de 180º de 5 pines con una sola orejeta de ubicación en el cuerpo en ambos lados.

![MIDI1](https://www.elpedaldelguitarrista.com/wp-content/uploads/2019/10/mejores-cables-midi.png) 

**Conectores:**  El conector MIDI se conoce como tipo DIN 5 pines (180º), con receptáculo hembra para montaje.El conector “MIDI IN” es de entrada y “MIDI OUT” es de salida. De manera opcional se puede tener un conector “MIDI THRU”, el cual provee copia de los datos que llegan a través de MIDI IN para poder encadenar varios dispositivos. Sin embargo,cuando hay más de tres instrumentos conectados, el pulso cuadrado tiende a degradarse entre los tiempos de subida y bajada.

![MIDI1](https://www.electroschematics.com/wp-content/uploads/2019/11/2-MIDI-in-and-out.jpg?w=547&resize=547%2C343) 

### 1.3 Topologías

Podemos observar que pines se desactivan o transmiten información de acuerdo al tipo de canal utilizado.

![MIDI1](https://www.electroschematics.com/wp-content/uploads/2019/11/1-MIDI-Pin-Out.jpg)  

**Protocolo** [MIDI 1.0](https://www.midi.org/specifications-old/item/the-midi-1-0-specification)     

Un sistema Midi básico permite mantener 16 canales independientes. Así, a través del mismo conector, pueden transmitirse de forma separada el producto de 16 intérpretes, cada uno de ellos actuando sobre un controlador; cada interpretación será procesada por el receptor asociado al canal apropiado. 

![MIDI1](http://www.disca.upv.es/adomenec/IASPA/tema5/dibus/muntatge-midi.png) 

Los mensajes MIDI 1.0 van en una dirección, de un transmisor a un receptor , estructurados en octetos. Cuando se transmiten, a cada octeto se le añade un bit de paridad para detección de errores. El primer octeto de un mensaje contiene un comando codificado en cuatro bits de la forma1MMM. (en hexadecimal, 0x8 a 0xF) y un identificador de canal de forma CCCC (por eso hay 16 canales, que generalmente se numeran del 1 al 16).Cada comando va compañado de sus parámetros característicos. Los parámetros se alojan en octetos cuyo bit más significativo es siempre 0. Los siete bits restante codifican un valor comprendido entre 0 y 127. 

![MIDI11](http://www.disca.upv.es/adomenec/IASPA/tema5/dibus/NoteNumbers.png)


**Protocolo** [MIDI 2.0](https://www.midi.org/midi-articles/details-about-midi-2-0-midi-ci-profiles-and-property-exchange)   

[![ScreenShot](https://i.blogs.es/4f13cb/midi-2.0/450_1000.png)](https://www.youtube.com/watch?v=klun6WMxryU&feature=youtu.be&ab_channel=MIDIAssociation)


Los mensajes MIDI 1.0 van en una dirección de un transmisor a un receptorn mientras qye MIDI 2.0 es bidireccional.
Por ejemplo, con los nuevos mensajes MIDI-CI (Consulta de capacidad), los dispositivos MIDI 2.0 pueden comunicarse entre sí y autoconfigurarse para trabajar juntos. También pueden intercambiar información sobre la funcionalidad, que es clave para la compatibilidad con versiones anteriores: el equipo MIDI 2.0 puede averiguar si un dispositivo no es compatible con MIDI 2.0 y luego simplemente comunicarse usando MIDI 1.0.

## 2. Archivo - MIDI
Para la exploración de la información se utilizo el archivo "MoonlightSonata.mid" ya digitalizada en formato **MIDI** obtenido de [freemidi](https://freemidi.org/).    
Librerías: [py_midicsv](https://pypi.org/project/py-midicsv/) , [mido](https://pypi.org/project/mido/) , [numpy](https://numpy.org/) , [pandas](https://pypi.org/project/pandas/).

### 2.1 Exploración


```python
# Librerías
import mido
import numpy as np
import pandas as pd
from mido import MidiFile

# carga de archivo y visualización de la estructura
archivo_midi = MidiFile('MoonlightSonata.mid')
print('info',archivo_midi)
print('length',archivo_midi.length)
print('charset',archivo_midi.charset)
print('ticks_per_beat',archivo_midi.ticks_per_beat)
```

    info <midi file 'MoonlightSonata.mid' type 1, 2 tracks, 2642 messages>
    length 306.4472479999999
    charset latin1
    ticks_per_beat 120
    

La información relevante nos dice que el archivo posee 2 canales que empiezan en el mismo tiempo con ticks_per_beat de 120 y posee 2642 mensajes almacenados.

**Tipos de mensajes**   
* type 0 (pista única): todos los mensajes se guardan en una pista.   
* type 1 (síncrono): todas las pistas comienzan al mismo tiempo.   
* type 2 (asincrónico): cada pista es independiente de las demás.  

#### Mensajes Almacenados     
* Sabiendo que nuestro archivo tiene 2 track´s podemos acceder a la info directamente.


```python
print(archivo_midi.tracks[0])# Track 1
print(archivo_midi.tracks[1])# Track 2
```

    <midi track '' 7 messages>
    <midi track '1st' 2635 messages>
    

#### Track 0 


```python
#Primer pista
for msg in archivo_midi.tracks[0]:
    print(msg)
```

    <meta message time_signature numerator=4 denominator=4 clocks_per_click=24 notated_32nd_notes_per_beat=8 time=0>
    <meta message key_signature key='E' time=0>
    <meta message set_tempo tempo=1090909 time=0>
    <meta message marker text='1st mvmt' time=0>
    <meta message marker text='Transcribed by Edward Grant' time=0>
    <meta message set_tempo tempo=2400000 time=32640>
    <meta message end_of_track time=0>
    

* La información que podemos visualizar en este track es con respecto a metadatos sobre el tiempo de la pista el autor, notas por beat, tiempo , etc. con un total de 7 mensajes en este track.
# Código opcional : Para recorrer todo el archivo 
for i, track in enumerate(archivo_midi.tracks):
    print('Track {}: {}'.format(i, track.name))
    for msg in track:
        print(msg)
* Con este código podremos visualizar el archivo completo en ambos track´s

#### Conviertiendo "archivo_midi" a una lista 


```python
# Transformando a una lista para poder observar las 15 primeras filas.
lista = list(archivo_midi)
lista[0:15]
```




    [<meta message time_signature numerator=4 denominator=4 clocks_per_click=24 notated_32nd_notes_per_beat=8 time=0>,
     <meta message key_signature key='E' time=0>,
     <meta message set_tempo tempo=1090909 time=0>,
     <meta message marker text='1st mvmt' time=0>,
     <meta message marker text='Transcribed by Edward Grant' time=0>,
     <meta message midi_port port=0 time=0>,
     <meta message track_name name='1st' time=0>,
     <message program_change channel=0 program=0 time=0>,
     <meta message text text='\r' time=0>,
     <message control_change channel=0 control=67 value=127 time=0>,
     <message control_change channel=0 control=64 value=127 time=0>,
     <message note_on channel=0 note=56 velocity=35 time=0.054545449999999995>,
     <message note_on channel=0 note=49 velocity=42 time=0>,
     <message note_on channel=0 note=37 velocity=42 time=0>,
     <message note_on channel=0 note=56 velocity=0 time=0.38181814999999997>]



* Otra alternativa para poder visualizar contenido RAW.

### 2.2 Almacenamiento 
#### Copia de información en archivo .txt


```python
archivomid = 'MoonlightSonata.mid'
archivotxt = 'MoonlightSonata.txt'

info_mid = MidiFile(archivomid)

# SALIDA
pistas = info_mid.tracks
n = len(pistas)
for i in range(0,n,1):
    print(i, pistas[i])

# ARCHIVO DE TEXTO
archivo = open(archivotxt,'w')
for dato in partitura:
    archivo.write(str(dato) + '\n')
archivo.close()
```

    0 <midi track '' 7 messages>
    1 <midi track '1st' 2635 messages>
    

De esta forma puedo obtener toda la información cruda volcada en un archivo txt.

#### Conversiones
* Transformando los datos de MIDI a CSV
* Transformando los datos de CSV a MIDI


```python
import py_midicsv as pm

# Cargar archivo midi y lo convierte a csv
csv_string = pm.midi_to_csv("MoonlightSonata.mid")

# Parsea el archivo csv a midi 
midi_object = pm.csv_to_midi(csv_string)

# guardando el archivo modificado a la ruta raiz
with open("example_converted.mid", "wb") as output_file:
    midi_writer = pm.FileWriter(output_file)
    midi_writer.write(midi_object)
# El archivo generado example_converted.mid si se reproduce en un reproductor midi deberia funciona perfectamente
```

**Creando un Data Frame con los datos crudos**


```python
df_midi_object = pd.DataFrame(midi_object)
df_midi_object.transpose()
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
      <th>0</th>
      <th>1</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>midi.TimeSignatureEvent(tick=0, data=[4, 2, 24...</td>
      <td>midi.PortEvent(tick=0, data=[0])</td>
    </tr>
    <tr>
      <th>1</th>
      <td>midi.KeySignatureEvent(tick=0, data=[4, False])</td>
      <td>midi.TrackNameEvent(tick=0, text=b'1st', data=...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>midi.SetTempoEvent(tick=0, data=[16, 165, 93])</td>
      <td>midi.ProgramChangeEvent(tick=0, channel=0, dat...</td>
    </tr>
    <tr>
      <th>3</th>
      <td>midi.MarkerEvent(tick=0, text=b'1st mvmt', dat...</td>
      <td>midi.TextMetaEvent(tick=0, text=b'\r', data=b'...</td>
    </tr>
    <tr>
      <th>4</th>
      <td>midi.MarkerEvent(tick=0, text=b'Transcribed by...</td>
      <td>midi.ControlChangeEvent(tick=0, channel=0, dat...</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>2630</th>
      <td>None</td>
      <td>midi.NoteOnEvent(tick=0, channel=0, data=[52, 0])</td>
    </tr>
    <tr>
      <th>2631</th>
      <td>None</td>
      <td>midi.NoteOnEvent(tick=0, channel=0, data=[61, 0])</td>
    </tr>
    <tr>
      <th>2632</th>
      <td>None</td>
      <td>midi.NoteOnEvent(tick=0, channel=0, data=[37, 0])</td>
    </tr>
    <tr>
      <th>2633</th>
      <td>None</td>
      <td>midi.NoteOnEvent(tick=0, channel=0, data=[44, 0])</td>
    </tr>
    <tr>
      <th>2634</th>
      <td>None</td>
      <td>midi.EndOfTrackEvent(tick=0, data=[])</td>
    </tr>
  </tbody>
</table>
<p>2635 rows × 2 columns</p>
</div>



La información generalmente de esta manera es mas dificil de entender.
En la columna 0 es referente a la pista 1 tenemos 7 mensajes por lo cual lo que aparece en none es autocompletado por la librería para que no quede vacía. En la columna referente a la pista 2 esta la información de los mensajes del instrumento debe hacer para producir los sonidos.

**Creando un Data Frame con datos filtrados**


```python
df_csv_string = pd.DataFrame(csv_string,columns=['Data'])
df_csv_string
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
      <th>Data</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0, 0, Header, 1, 2, 120\n</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1, 0, Start_track\n</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1, 0, Time_signature, 4, 2, 24, 8\n</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1, 0, Key_signature, 4, "major"\n</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1, 0, Tempo, 1090909\n</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
    </tr>
    <tr>
      <th>2641</th>
      <td>2, 33126, Note_on_c, 0, 61, 0\n</td>
    </tr>
    <tr>
      <th>2642</th>
      <td>2, 33126, Note_on_c, 0, 37, 0\n</td>
    </tr>
    <tr>
      <th>2643</th>
      <td>2, 33126, Note_on_c, 0, 44, 0\n</td>
    </tr>
    <tr>
      <th>2644</th>
      <td>2, 33126, End_track\n</td>
    </tr>
    <tr>
      <th>2645</th>
      <td>0, 0, End_of_file</td>
    </tr>
  </tbody>
</table>
<p>2646 rows × 1 columns</p>
</div>



De esta manera filtramos los datos por fila de un mensaje entero en una sola columna a modo de ejemplo.   
Para poder desarrollar exploraciones mas avanzadas o realizar gráficas con datos que sean de interes deberemos realizar una limpieza de los datos con el fin de ordenar cada información separada por la coma en una columna independiente. Este trabajo quedará pendiente para otro cuaderno.

## 3. Conclusión

Hoy en día todos los dispositivos y hasta los celulares se utilizan para crear música, proyectos o controlar dispositivos por medio de multiples formas , sean físicas o intangibles la información siempre es creada almacenada y enviada. Ya sea para manejar un instrumento virtual o utilizar algun patch o setting particular. Cada fabricante crea su propio manual instructivo siguiendo las normas mencionadas anteriormente.

## 4. Recursos
[WIKI - MIDI](https://es.wikipedia.org/wiki/MIDI)   
[MIDI Association](https://www.midi.org)  
[Síntesis del sonido](http://www.disca.upv.es/adomenec/IASPA/tema5/Midi.html)    
[MIDI – An Introduction](https://www.electroschematics.com/midi-introduction/)    
[Tésis en tecnología MIDI - UNAM](http://www.ptolomeo.unam.mx:8080/xmlui/bitstream/handle/132.248.52.100/12833/409065363.pdf?sequence=3)    
