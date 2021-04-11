---
layout: page
title: running
permalink: /running/
---
{% assign row = site.data.dailymilesque_stats[1] %}

| tiempo (dd:hh:mm:ss) | distancia (km) | ascenso (km) | paso (min/km) | calorías (kcal) |
|:--------------------:|:--------------:|:------------:|:-------------:|:----------------:|
| {{ row["tiempo (dd:hh:mm:ss)"] }} | {{ row["distancia (km)"] }} | {{ row["ascenso (km)"] }} | {{ row["paso (min/km)"] }} | {{ row["calorías (kcal)"] }} |

<figure>
  <img src="/assets/img/running_2021.png" alt="" style="width:100%">
  <figcaption><b>Fig. 1.</b> Concentración de km durante el año.</figcaption>
</figure>
## totales[^1]
Sección inspirada por las estadísticas anuales que presentaba *dailymile*. Muchas de las virtudes de ese servicio---y más---las veo ahora en [*Strava*](https://www.strava.com/).

{% assign row = site.data.dailymilesque_stats[0] %}

| tiempo (dd:hh:mm:ss) | distancia (km) | ascenso (km) | paso (min/km) | calorías (kcal) |
|:--------------------:|:--------------:|:------------:|:-------------:|:----------------:|
| {{ row["tiempo (dd:hh:mm:ss)"] }} | {{ row["distancia (km)"] }} | {{ row["ascenso (km)"] }} | {{ row["paso (min/km)"] }} | {{ row["calorías (kcal)"] }} |

La distancia recorrida / escalada equivale a...

| radio Tierra (%) | circunferencia Tierra (%) | Muralla China (%) | Chirripó (%) | Everest (%) |
|:----------------:|:-------------------------:|:-----------------:|:------------:|:-----------:|
| {{ row["radio Tierra (%)"] }} | {{ row["circunferencia Tierra (%)"] }} | {{ row["Muralla China (%)"] }} | {{ row["Chirripó (%)"] }} | {{ row["Everest (%)"] }} |

Las calorías quemadas equivalen a...

| grasa corporal (kg) | cerveza (latas) | Trits | donas | Big Mac | Double Whopper w/Cheese |
|:-------------------:|:---------------:|:-----:|:-----:|:-------:|:-----------------------:|
| {{ row["grasa corporal (kg)"] }} | {{ row["cerveza (latas)"] }} | {{ row["Trits"] }} | {{ row["donas"] }} | {{ row["Big Mac"] }} | {{ row["Double Whopper w/Cheese"] }} |

<figure>
  <img src="/assets/img/running_2010-2020.png" alt="" style="width:100%">
  <figcaption><b>Fig. 2.</b> Concentración de km través de los años.</figcaption>
</figure>

[^1]: Los datos fueron recopilados del 2010 al 2013 y luego a partir de Febrero 2020. Del 2014 hasta el 2019 no corrí regularmente debido a una lesión en la espalda. Volví a correr en Octubre del 2019, pero no tengo los datos.