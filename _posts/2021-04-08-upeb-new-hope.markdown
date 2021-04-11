---
layout:      post
title:       "upeb: a new hope"
date:       2021-04-08 09:15:00 -0600
categories:  post
tags: [blogging, jekyll, latex, tipography]
---
Gracias a un pequeño empujón de mi amigo [Hans](https://hansga.vercel.app/), quien me explicó cómo montar fácilmente un blog utilizando **Jekyll** y **GitHub Pages**, he decidido empezar a escribir de nuevo.

Aunque estoy bastante satisfecho con el tema por defecto de Jekyll, decidí modificar la **tipografía** del sitio: quiero que se parezca lo más posible a un libro escrito en $$\mathrm{\LaTeX}$$, *sin importar el dispositivo donde se lea*.  Lo primero que hice fue agregar el siguiente código al final del archivo `_includes/custom-head.html`;
```html
<script type="text/javascript" id="MathJax-script" async
  src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
</script>
```
Esto me permite usar $$\mathrm{\LaTeX}$$---mediante **MathJax**---para escribir ecuaciones matemáticas. Aunque MathJax es algo lento en desplegar páginas con *muchas* ecuaciones, tiene la ventaja que el código es visible al inspeccionarlas.

El siguiente paso fue descargar la fuente [**Computer Modern**](https://www.fontsquirrel.com/fonts/computer-modern) y agregarla al sitio. Resulta que esto no es trivial, porque el archivo descargado incluye 29 archivos `.woff` con *estilos distintos* para 1 sola fuente---¿cuál o cuáles hay que usar?

Computer Modern es más que una fuente, es una *familia de fuentes*. Dentro de esa familia de fuentes hay una fuente con serifa (Roman), una sin serifa (Sans Serif) y otras variaciones. Cada una de esas fuentes tiene, generalmente, 4 estilos básicos: normal, cursiva, negrita y cursiva-negrita. Entonces, para agregar una fuente al sitio, necesito definir esa fuente dentro del `css` y decir cómo se va a comportar en cada uno de los 4 casos mencionados.

Añadí los archivos pertinentes de *Computer Modern Roman* al directorio `/assets/fonts/` y modifiqué el archivo `_sass/minima/custom-variables.scss`, añadiendo el siguiente código:
```css
/*	Computer Modern Roman	*/
@font-face {
  font-family: 'CM Roman';
  font-style: normal;
  font-weight: 400;
  src: url('/assets/fonts/cmunrm-webfont.woff') format('woff'); 
}

@font-face {
  font-family: 'CM Roman';
  font-style: italic;
  font-weight: 400;
  src: url('/assets/fonts/cmunti-webfont.woff') format('woff'); 
}

@font-face {
  font-family: 'CM Roman';
  font-style: normal;
  font-weight: 700;
  src: url('/assets/fonts/cmunbx-webfont.woff') format('woff'); 
}

@font-face {
  font-family: 'CM Roman';
  font-style: italic;
  font-weight: 700;
  src: url('/assets/fonts/cmunbi-webfont.woff') format('woff'); 
}

$base-font-family: "CM Roman";
```
Los primeros 4 *bloques* definen la fuente en cada uno de los casos usuales---normal, cursiva, negrita, cursiva--negrita---, la última línea cambia la fuente por defecto del tema a la fuente que recién definí. Hice exactamente los mismo para la fuente *Computer Modern Typewriter*, referenciando a los archivos relevantes y haciéndola fuente por defecto para desplegar código, `$code-font-family: "CM Typewriter";`

Tengo la intención de agregar otras fuentes al sitio, las familias [Source Serif Pro](https://www.fontsquirrel.com/fonts/source-serif-pro), [Source Sans Pro](https://www.fontsquirrel.com/fonts/source-sans-pro) y [Source Code Pro](https://www.fontsquirrel.com/fonts/source-code-pro) de **Adobe**, por ejemplo; o la familia [Plex](https://www.fontsquirrel.com/fonts/ibm-plex) de **IBM**. Me resulta atractivo el poder cambiar sutilmente el aspecto de cada post con fuentes distintas.

Otros pequeños ajustes hechos en el archivo `_sass/minima/custom-variables.scss` son variar el tamaño de la fuente, variar el tamaño de la fuente pequeña[^1], variar el espacio de interlineado y cambiar el color de los bloques de código. Todo eso lo hice añadiendo estas líneas
```css
$base-font-size: 20px;
$small-font-size: $base-font-size * 0.8;
$base-line-height: 1.3;
$code-background-color: lighten($brand-color, 43%);
```
También probé añadir *justificación* al texto, pero de momento he decidido no usarlo. Se puede lograr modificando `_sass/minima/custom_styles.scss` con el código
```css
.post-content {
	text-align: justify;
}
```

Un último añadido, en el que aún estoy trabajando, tiene que ver con los `tags` que Jekyll permite adherir a cada post. Por defecto no hacen nada y no se ven reflejados en ningún lado. Me gustaría cambiar eso, pero de la forma menos intrusiva posible. De momento estoy feliz con el resultado de los cambios hechos.

He intentado recuperar algunos posts interesantes---al menos para mí---que escribí en el pasado, con el fin de ir poblando el sitio. Cualquier contenido previo al 2021 fue escrito en otro lugar y migrado acá

[^1]: El tamaño de este comentario, por ejemplo.