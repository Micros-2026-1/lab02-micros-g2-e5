[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/KzqfxGd5)
[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=22828225&assignment_repo_type=AssignmentRepo)
# Lab02 - Caracterización de osciladores (externo vs. interno)


## 1. Integrantes

* [Liliana Carreño](https://github.com/Liliana-Carreno)
* [Salome Ramirez](https://github.com/salomeramirezpi-eng)
* [Gabriel Ortega](https://github.com/gabrieldaortegaro-arch)

### 1.1 Introducción
<p align="justify" style="text-indent:40px;">
Los osciladores son elementos fundamentales en la mayoría de dispositivos electrónicos ya que estos ayudan a sincronizar y generar las diferentes señales, asimismo al ser periodicos sirven como un referente de tiempo. En esta práctica se utilizo el microcontrolador <code>PIC18F45K22</code> y se realizaron tres montajes diferentes de osciladores para analizar las diferencias entre estos, ver cual es más estable y con cual podemos llegar a alcanzar mayor precisión.
</p>

<p align="justify" style="text-indent:40px;">
Para la realización de nuestros montajes se utilizó el oscilador interno del microcontrolador, un oscilador externo basado en cristal acompañado de dos condensadores y un oscilador RC conformado por una resistencia y un condensador. Despues, se analizó el comportamiento de cada uno de ellos frente a cambios bruscos de temperatura, especificamente al aumentarla. Igualmente se observó como cada uno de estos circuitos trabajaba junto con el PLL que es un multiplicador de frecuencia. 
</p>


### 1.2 Objetivos

* Comprender el concepto de oscilador a la vez que se identifica y reconoce la importancia de este elemento en sistemas electrónicos.

* Identificar los diferentes tipos de osciladores (RC, con cristal, INTOSC).

* Comprender como los factores externos como la temperatura pueden afectar la precisión del oscilador.

* Desarrollar habilidades de simulación, manipulación de códigos y montaje de circuitos.


## 2. Documentación

<p align="justify" style="text-indent:40px;">
Para nuestra práctica se utilizaron las mismas <b>herramientas</b> de la practica anterior junto con algunas más, vale resaltar que en este caso, un elemento fundamental para lograr el oscilador exterior fue el <b>Cristal de 16MHz</b>, este elemento es un componente diseñado para generar una señal eléctrica con una frecuencia estable y precisa. Esto funciona aplicando un voltaje al cristal, el cual se deforma y empieza  a vibrar de manera física en determinada frecuencia, que depende de la forma en la que este cortado, esta vibración se convierte en una señal eléctrica que es lo que finalmente utilizamos como referencia. Este elemento es utilizado en diferentes circuitos por su bajo costo y gran presición.
</p>

<p align="center">
  <img src="Airbrush-IMAGE-ENHANCER-1773375072946-1773375072946.jpg" width="700"><br>
  <em> <b> Figura 1.</b> Imagen de referencia del Cristal de 16MHz. </em>
</p>

### 2.1 Descripción del laboratorio

<p align="center">
  <img src="external1.png" width="700"><br>
  <em> <b> Figura 2.</b> Imagen de referencia de la conexión del Oscilador con Cristal. </em>
</p>

<p align="center">
  <img src="external2.png" width="700"><br>
  <em> <b> Figura 3.</b> Imagen de referencia de la conexión del Oscilador Interno (INTOSC). </em>
</p>

<p align="center">
  <img src="Airbrush-IMAGE-ENHANCER-1773374322024-1773374322024.png" width="700"><br>
  <em> <b> Figura 4.</b> Imagen de referencia de la conexión del Oscilador RC. </em>
</p>


### 2.2 Explicación del código implementado

### 2.3 Análisis y comparación

#### Tabla 1: Medición en frío

| Modo de oscilador | Freq. teórica Fosc | RA6 medible (CLKO)? | Freq. medida RA6 (Hz) | Freq. teórica RC0 (Hz)| Freq. medida RC0 (Hz) | Error RC0 (%) |  
|------------------|------------------|---------------------|---------------|---------------------|---------------|---------------|
| INTOSC (interno) | 16,000,000       | Sí                 |           77          |                500                 |   79            |         84.2      | |
| HS (cristal externo 16 MHz) | 16,000,000 | No |     NA      |               500                 |509.4               |       1.88        |
| RC externo       | ~16,000,000*     | No                                    |       N/A        | 500                 |   407.3            |       18.54        | |

<p align="justify" style="text-indent:40px;">
La tabla muestra la comparación entre la frecuencia teórica y la frecuencia medida de tres modos de oscilador del microcontrolador PIC18F45K22 en temperatura normal, antes de calentarlo. El oscilador interno (INTOSC) presentó un error muy alto (84.2 %), ya que la frecuencia medida fue mucho menor que la teórica. El cristal externo (HS) fue el más preciso, con una frecuencia muy cercana a la esperada y un error pequeño de 1.88 %. Por otro lado, el oscilador RC externo tuvo un error intermedio de 18.54 %. En general, el cristal externo fue el más estable, mientras que el oscilador interno fue el menos preciso en esta prueba.
</p>

#### Tabla 2: Medición con calor

| Modo de oscilador | Freq. teórica Fosc | RA6 medible (CLKO)? | Freq. medida RA6 (Hz) | Freq. teórica RC0 (Hz)| Freq. medida RC0 (Hz) | Error RC0 (%) |  
|------------------|------------------|---------------------|---------------|---------------------|---------------|---------------|
| INTOSC (interno) | 16,000,000       | Sí                 |                     |                500                 |        32.6       |          93.48     | |
| HS (cristal externo 16 MHz) | 16,000,000 | No |     NA      |               500                 |503.8               |         0.76      |
| RC externo       | ~16,000,000*     | No                                    |       N/A        | 500                 |           422.39    |        15.522       | |

<p align="justify" style="text-indent:40px;">
La tabla muestra las mediciones cuando se calentó el oscilador del microcontrolador PIC18F45K22. El oscilador interno (INTOSC) presentó un error aún mayor, llegando a 93.48 %, ya que la frecuencia medida fue de 32.6 Hz en lugar de 500 Hz. El cristal externo (HS) siguió siendo el más estable, con una frecuencia de 503.8 Hz y un error muy pequeño de 0.76 %. Por su parte, el oscilador RC externo tuvo un error de 15.52 %, mostrando una variación moderada. En general, incluso con el aumento de temperatura, el cristal externo sigue siendo el más preciso, mientras que el oscilador interno es el más afectado por el calor.
</p>

#### Tabla 3: Deriva
           
<div align="center">

| Modo de oscilador | RC0 deriva (Hz) |
|------------------|----------------|
| INTOSC (interno) | 421 |
| HS (cristal externo 16 MHz) | 9.4 |
| RC externo | 92.4 |

</div>

<p align="justify" style="text-indent:40px;">
La tabla muestra la deriva de frecuencia, es decir, la diferencia entre la frecuencia teórica y la medida para cada modo de oscilador del microcontrolador. El oscilador interno (INTOSC) presentó la mayor variación con 421 Hz, lo que indica que es el más afectado por cambios como la temperatura. El cristal externo (HS) tuvo la menor deriva con 9.4 Hz, mostrando una alta estabilidad y precisión. Por otro lado, el oscilador RC externo presentó una deriva intermedia de 92.4 Hz. En conclusión, el análisis general nos muestra que el cristal externo es el más estable y preciso, mientras que el oscilador interno es el que más se ve afectado por las condiciones externas.
</p>

<!-- Agregar tablas para valores usando PLL -->


## 2.4 Diagramas

## 2.5 Formas de onda

### INTOSC (interno) 

### HS

### RC

## 3. Evidencias de implementación

<p align="justify" style="text-indent:40px;">
Al presentar la práctica, se iba mostrando a su vez el circuito montado y funcionando a una <b>frecuencia de 500Hz</b>, esta frecuencia no es perceptible para el ojo humano, por lo tanto la siguientes evidencias son de la implementación de cada uno de los osciladores a una frecuencia menor para que se logre percibir el parpadeo de un LED.
</p>

### INTOSC (interno):  

<p align="justify" style="text-indent:40px;"> 
Nuestro primer circuito con la utilización del <b>oscilador interno</b>, consta de el PIC la conexión basica de este al PICKIT, acompañado de la resistencia y el LED. Es una conexión simple y para que funcionase este modo primero lo más importante era ajustar la _XTAL_FREQ dependiendo de que valor de frecuencia nesecitasemos.
</p>

<p align="center">
  <img src="Interno.gif" width="700"><br>
  <em> <b> Figura 1.</b> Imagen de referencia del Cristal de 16MHz. </em>
</p>

### HS Oscilador con Cristal:

<p align="justify" style="text-indent:40px;"> 
Nuestro primer circuito con la utilización del <b>oscilador interno</b>, consta de el PIC la conexión basica de este al PICKIT, acompañado de la resistencia y el LED. Es una conexión simple y para que funcionase este modo primero lo más importante era ajustar la _XTAL_FREQ dependiendo de que valor de frecuencia nesecitasemos.
</p>

<p align="center">
  <img src="oscilador.gif" width="700"><br>
  <em> <b> Figura 1.</b> Imagen de referencia del Cristal de 16MHz. </em>
</p>


### RC

<p align="justify" style="text-indent:40px;"> 
Nuestro primer circuito con la utilización del <b>oscilador interno</b>, consta de el PIC la conexión basica de este al PICKIT, acompañado de la resistencia y el LED. Es una conexión simple y para que funcionase este modo primero lo más importante era ajustar la _XTAL_FREQ dependiendo de que valor de frecuencia nesecitasemos.
</p>

<p align="center">
  <img src="rc.gif" width="700"><br>
  <em> <b> Figura 1.</b> Imagen de referencia del Cristal de 16MHz. </em>
</p>


## 4. Preguntas

* ¿En qué modo se obtuvo la medición más cercana a la frecuencia teórica?

* ¿Fue posible evidenciar el fenómeno de deriva? ¿Qué factores podrían explicar la variación de frecuencia al calentar el PIC?

* ¿Cuál es más preciso en cuanto a frecuencia teórica vs. medida?


* Explique cómo usar RC0 para estimar la frecuencia del oscilador cuando RA6 no está disponible.

* Si se quisiera duplicar la frecuencia del PIC usando PLL, ¿en qué modos se podría aplicar?

* Enliste ventajas y desventajas de cada modo.

## 5. Conclusiones

## 6. Referencias

* Agarwal, T. (2020, June 4). Overview of Crystal Oscillator Circuit Working with applications. ElProCus - Electronic Projects for Engineering Students. https://www.elprocus.com/crystal-oscillator-circuit-and-working/

* Microcontroladores_ECCI_2026-I/labs/02_lab02/README.md at main · jharamirezma/Microcontroladores_ECCI_2026-I. (n.d.). GitHub. https://github.com/jharamirezma/Microcontroladores_ECCI_2026-I/blob/main/labs/02_lab02/README.md

