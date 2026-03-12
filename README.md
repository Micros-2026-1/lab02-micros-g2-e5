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
  <img src="osci.jpg" width="700"><br>
  <em> <b> Figura 1.</b> Imagen de referencia del Cristal de 16MHz. </em>
</p>

### 2.1 Descripción del laboratorio

### 2.2 Explicación del código implementado

### 2.3 Análisis y comparación

#### Tabla 1: Medición en frío

| Modo de oscilador | Freq. teórica Fosc | RA6 medible (CLKO)? | Freq. medida RA6 (Hz) | Freq. teórica RC0 (Hz)| Freq. medida RC0 (Hz) | Error RC0 (%) |  
|------------------|------------------|---------------------|---------------|---------------------|---------------|---------------|
| INTOSC (interno) | 16,000,000       | Sí                 |                     |                500                 |               |               | |
| HS (cristal externo 16 MHz) | 16,000,000 | No |     NA      |               500                 |               |               |
| RC externo       | ~16,000,000*     | No                                    |       N/A        | 500                 |               |               | |

#### Tabla 2: Medición con calor

| Modo de oscilador | Freq. teórica Fosc | RA6 medible (CLKO)? | Freq. medida RA6 (Hz) | Freq. teórica RC0 (Hz)| Freq. medida RC0 (Hz) | Error RC0 (%) |  
|------------------|------------------|---------------------|---------------|---------------------|---------------|---------------|
| INTOSC (interno) | 16,000,000       | Sí                 |                     |                500                 |               |               | |
| HS (cristal externo 16 MHz) | 16,000,000 | No |     NA      |               500                 |               |               |
| RC externo       | ~16,000,000*     | No                                    |       N/A        | 500                 |               |               | |

#### Tabla 3: Deriva

| Modo de oscilador |RC0 deriva (Hz) |
|------------------|--------------------|
| INTOSC (interno) |                    |                
| HS (cristal externo 16 MHz) |                |                |
| RC externo       |                 |                


<!-- Agregar tablas para valores usando PLL -->

<!-- Complemente con análisis de lo registrado en tablas -->

## 2.4 Diagramas

## 2.5 Formas de onda

### INTOSC (interno) 

### HS

## RC

## 3. Evidencias de implementación

## 4. Preguntas

* ¿En qué modo se obtuvo la medición más cercana a la frecuencia teórica?

* ¿Fue posible evidenciar el fenómeno de deriva? ¿Qué factores podrían explicar la variación de frecuencia al calentar el PIC?

* ¿Cuál es más preciso en cuanto a frecuencia teórica vs. medida?


* Explique cómo usar RC0 para estimar la frecuencia del oscilador cuando RA6 no está disponible.

* Si se quisiera duplicar la frecuencia del PIC usando PLL, ¿en qué modos se podría aplicar?

* Enliste ventajas y desventajas de cada modo.

## 5. Referencias

* Agarwal, T. (2020, June 4). Overview of Crystal Oscillator Circuit Working with applications. ElProCus - Electronic Projects for Engineering Students. https://www.elprocus.com/crystal-oscillator-circuit-and-working/

* Microcontroladores_ECCI_2026-I/labs/02_lab02/README.md at main · jharamirezma/Microcontroladores_ECCI_2026-I. (n.d.). GitHub. https://github.com/jharamirezma/Microcontroladores_ECCI_2026-I/blob/main/labs/02_lab02/README.md

