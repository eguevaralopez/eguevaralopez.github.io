---
layout: page
title: running
permalink: /running/
---
<figure>
  <img src="/assets/img/running_2021.png" alt="" style="width:100%">
  <figcaption><b>Fig. 1.</b> Concentración de km durante el año.</figcaption>
</figure>

{% assign row = site.data.dailymilesque_stats[1] %}

| distancia (km) | paso (min/km) | tiempo (dd:hh:mm:ss) | ascenso (km) | calorías (kcal) |
|:--------------:|:-------------:|:--------------------:|:------------:|:---------------:|
| {{ row["distancia (km)"] }} | {{ row["paso (min/km)"] }} | {{ row["tiempo (dd:hh:mm:ss)"] }} | {{ row["ascenso (km)"] }} | {{ row["calorías (kcal)"] }} |

## totales[^1]
Sección inspirada por las estadísticas que presentaba *dailymile*. Muchas de las virtudes de ese servicio las veo presentes en [*Strava*](https://www.strava.com/).

{% assign row = site.data.dailymilesque_stats[0] %}

| distancia (km) | paso (min/km) | tiempo (dd:hh:mm:ss) | ascenso (km) | calorías (kcal) |
|:--------------:|:-------------:|:--------------------:|:------------:|:---------------:|
| {{ row["distancia (km)"] }} | {{ row["paso (min/km)"] }} | {{ row["tiempo (dd:hh:mm:ss)"] }} | {{ row["ascenso (km)"] }} | {{ row["calorías (kcal)"] }} |

{::comment}
| radio Tierra (%) 
|:----------------:
| {{ row["radio Tierra (%)"] }} 
{:/comment}

| circunferencia Tierra (%) | Muralla China (%) | Chirripó (%) | Everest (%) |
|:-------------------------:|:-----------------:|:------------:|:-----------:|
| {{ row["circunferencia Tierra (%)"] }} | {{ row["Muralla China (%)"] }} | {{ row["Chirripó (%)"] }} | {{ row["Everest (%)"] }} |

| grasa corporal (kg) | cerveza (latas) | Trits | donas | Big Mac | Double Whopper w/Cheese |
|:-------------------:|:---------------:|:-----:|:-----:|:-------:|:-----------------------:|
| {{ row["grasa corporal (kg)"] }} | {{ row["cerveza (latas)"] }} | {{ row["Trits"] }} | {{ row["donas"] }} | {{ row["Big Mac"] }} | {{ row["Double Whopper w/Cheese"] }} |

<figure>
  <img src="/assets/img/running_2010-2020.png" alt="" style="width:100%">
  <figcaption><b>Fig. 2.</b> Concentración de km través de los años.</figcaption>
</figure>

[^1]: Los datos fueron recopilados del 2010 al 2013 y luego a partir de Febrero 2020. Del 2014 hasta el 2019 no corrí regularmente debido a una lesión en la espalda. Volví a correr en Octubre del 2019, pero no tengo los datos.