---
layout:      post
title:       "cable RGB 15 kHz/31 kHz para el Dreamcast"
date:       2021-12-20 21:06:09 -0600
categories:  post
tags: [hardware, mod, retro, toretto]
---

```
'toretto': no detalla motivaciones, no explica detalles intermedios y no se
preocupa por la prosa. Es un post rápido y furioso sobre un tema específico.
```

El puerto AV del Dreamcast tiene la capacidad de tirar señales RGB, Vsync, Hsync y Csync. Los estados del pin 6 (S1) y el pin 7 (S2) controlan qué señales salen del GPU. Estos pines tienen lógica negativa y su tabla es la siguiente;

| S1   | S2   | salida                     | sync out                |
|:----:|:----:|:--------------------------:|:-----------------------:|
| H    | H    | cVid, YC<br>15 kHz         | cVid, Y                 |
| H    | L    | RGB<br>15 kHz              | Hsync & Vsync,<br>Csync |
| L    | H    | ~~cVid, YC~~<br>~~31 kHz~~ | --                      |
| L    | L    | RGB<br>31 kHz              | Hsync & Vsync           |

Al usar RGB siempre salen Hsync y Vsync porque vienen directamente del GPU, mientras que Csync se forma en el DAC solamente cuando se considera necesario (RGB 15 KHz). Una forma sencilla de fabricar un cable "multiscan" es usar un sync-combiner pasivo para generar Csync a partir de Hsync y Vsync. Tal circuito se describe en un post de RetroRGB titulado [*Building A Passive Sync Combiner*](https://www.retrorgb.com/building-a-passive-sync-combiner.html).

---
Esto es lo que queda de mi viejo VGA Box, está completo a excepción del conector *AV* hacia el Dreamcast y un switch de 3 posiciones;
{:refdef: style="text-align: center;"}
![](/assets/img/2021-12-20-dreamcast_rgbBox_1.jpg){:width="70%"}
{: refdef}

La mayoría de componentes<!---—18 resistores, 21 caps, 3 opAmps y 1 pot—---> son para el circuito de audio[^1], que proviene de los pines 2 y 3. El circuito de video es el siguiente;

{:refdef: style="text-align: center;"}
![](/assets/img/2021-12-20-dreamcast_rgbBox_2.jpg){:width="100%"}
{: refdef}

El `74HCT244N` es un buffer de 3 estados y está conectado de forma que cuando los pines 6 y 7 están *H* el buffer tira *High-Z* en sus salidas. Se prescinde del integrado para simplificar el circuito y se añade el sync-combiner;

{:refdef: style="text-align: center;"}
![](/assets/img/2021-12-20-dreamcast_rgbBox_3.jpg){:width="100%"}
{: refdef}

En el 2012 [mmmonkey implementó un circuito similar](https://mmmonkey.co.uk/dreamcast-internal-vga-mod/) en un PCB de pistas—en ese circuito se inspiró la siguiente construcción;

{:refdef: style="text-align: center;"}
![](/assets/img/2021-12-20-dreamcast_rgbBox_4.jpg){:width="70%"}
{: refdef}

- PCB de 13 filas, 19 columnas
- Las pistas sobre las filas, cortes se muestran en rojo.
- S2 se aterrizó dentro del conector que se conecta al Dreamcast.
- Los pines externos de SW1 corresponden a la carcasa, reconectan la pista cortada.
- No se instaló LED, pero se puede hacer en la parte superior.

{:refdef: style="text-align: center;"}
![](/assets/img/2021-12-20-dreamcast_rgbBox_5.jpg){:width="70%"}
{: refdef}

[^1]: Posiblemente—algún día—actualice el post con el circuito de audio.
