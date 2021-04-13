---
layout: page
title: running
permalink: /running/
---
<figure>
  <img src="/assets/img/running_2021.png" alt="" style="width:100%">
  <figcaption><b>Fig. 1.</b> Concentración de km durante el año.</figcaption>
</figure>

{% assign row = site.data.dailymilesque_stats[5] %}
<center><table class="run_display">
	<tbody>
		<tr>
			<td class="run_display"><span class="run_display">{{ row["calorías (kcal)"] }}</span> <span class="run_unit">km</span><br>distancia más larga</td>
			<td class="run_display"><span class="run_display">{{ row["radio Tierra (%)"] }}</span> <span class="run_unit">m/km</span><br>paso más rápido</td>
			<td class="run_display"><span class="run_display">{{ row["circunferencia Tierra (%)"] }}</span> <span class="run_unit">m</span><br>ascenso más alto</td>
		</tr>
	</tbody>
</table>
{% assign row = site.data.dailymilesque_stats[1] %}
<table class="run">
<tbody>
		<tr>
			<td class="run"><span class="run_unit">{{ row["total workouts"] }}</span><br>sesiones</td>
			<td class="run"><span class="run_unit">{{ row["distancia (km)"] }} km</span><br>recorridos</td>
			<td class="run"><span class="run_unit">{{ row["tiempo (dd:hh:mm:ss)"] }}</span><br>corriendo</td>
			<td class="run"><span class="run_unit">{{ row["ascenso (km)"] }} km</span><br>escalados</td>
			<td class="run"><span class="run_unit">{{ row["paso (min/km)"] }} m/km</span><br>paso promedio</td>
		</tr>
	</tbody>
</table></center>
## totales[^1]
Sección inspirada por las [estadísticas que presentaba](/assets/img/running_dailymile.png) *dailymile*. Muchas de las virtudes de ese servicio las veo presentes en [*Strava*](https://www.strava.com/).
{% assign row = site.data.dailymilesque_stats[3] %}
<center><table class="run_display">
	<tbody>
		<tr>
			<td class="run_display"><span class="run_number">{{ row["calorías (kcal)"] }}</span> <span class="run_unit">km</span><br>distancia más larga</td>
			<td class="run_display"><span class="run_number">{{ row["radio Tierra (%)"] }}</span> <span class="run_unit">m/km</span><br>paso más rápido</td>
			<td class="run_display"><span class="run_number">{{ row["circunferencia Tierra (%)"] }}</span> <span class="run_unit">m</span><br>ascenso más alto</td>
		</tr>
	</tbody>
</table>
{% assign row = site.data.dailymilesque_stats[0] %}
<table class="run">
<tbody>
		<tr>
			<td class="run"><span class="run_unit">{{ row["total workouts"] }}</span><br>sesiones</td>
			<td class="run"><span class="run_unit">{{ row["distancia (km)"] }} km</span><br>recorridos</td>
			<td class="run"><span class="run_unit">{{ row["tiempo (dd:hh:mm:ss)"] }}</span><br>corriendo</td>
			<td class="run"><span class="run_unit">{{ row["ascenso (km)"] }} km</span><br>escalados</td>
			<td class="run"><span class="run_unit">{{ row["paso (min/km)"] }} m/km</span><br>paso promedio</td>
		</tr>
	</tbody>
</table>

<table class="run">
<tbody>
		<tr>
			<td class="run"><span class="run_unit">{{ row["circunferencia Tierra (%)"] }}</span><br>vuelta al mundo</td>
			<td class="run"><span class="run_unit">{{ row["Muralla China (%)"] }}</span><br>Muralla China</td>
			<td class="run"><span class="run_unit">{{ row["Chirripó (%)"] }}</span><br>Cerro Chirripó</td>
			<td class="run"><span class="run_unit">{{ row["Everest (%)"] }}</span><br>Monte Everest</td>
		</tr>
	</tbody>
</table>
<table class="run">
<tbody>
		<tr>
			<td class="run"><span class="run_unit">{{ row["grasa corporal (kg)"] }} kg</span><br>grasa corporal</td>
			<td class="run"><span class="run_unit">{{ row["cerveza (latas)"] }}</span><br>cervezas</td>
			<td class="run"><span class="run_unit">{{ row["Trits"] }}</span><br>Trits</td>
			<td class="run"><span class="run_unit">{{ row["donas"] }}</span><br>donas</td>
			<td class="run"><span class="run_unit">{{ row["Big Mac"] }}</span><br>Big Mac</td>
		</tr>
	</tbody>
</table></center>
<figure>
  <img src="/assets/img/running_2010-2020.png" alt="" style="width:100%">
  <figcaption><b>Fig. 2.</b> Concentración de km través de los años.</figcaption>
</figure>

[^1]: Los datos fueron recopilados del 2010 al 2013 y luego a partir de Febrero 2020. Del 2014 hasta el 2019 no corrí regularmente debido a una lesión en la espalda. Volví a correr en Octubre del 2019, pero no tengo los datos.
