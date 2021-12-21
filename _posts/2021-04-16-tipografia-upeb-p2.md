---
layout:      post
title:       "modificando la tipografía de upeb, p.2"
date:       2021-04-16 09:00:32 -0600
categories:  post
tags: [jekyll, latex, typography]
---
Continuación del [post pasado](/post/2021/04/08/upeb-new-hope.html), donde mencioné que quería hacer algo respecto a los tags. Obviamente no soy el primero en pensar en esto y la solución ya estaba en línea, así que antes de reinventar la rueda decidí seguir los pasos mencionados [en este post](https://longqian.me/2017/02/09/github-jekyll-tag/). Implementar los cambios me tomó menos de 10m.

Hecho eso, modifiqué un poco más la apariencia del sitio, empezando por las notas al pie de página. Quería que el tamaño de la fuente fuera más pequeño que el texto normal y que estuvieran separados por una línea horizontal. Con un simple agregado a `custom-styles.scss` obtuve lo que quería,
```
.footnotes p {
  font-size: $small-font-size;
  margin-top: 1rem;
}
.footnotes {
  font-size: $small-font-size;
  border-top: 1px solid hsl(0, 0%, 75%);
}
a.footnote {
  font-size: 14px;
}
```
El último bloque se refiere al número que incrustamos en el texto, que se comporta como un link; el primer bloque se refiere al número presente en la nota en sí y el bloque del medio es para el texto en la nota[^1].

El siguiente cambio que hice fue para deshacerme de algo que me molesta: siento que subrayar links, o texto en general, es *muy* noventero. Para quitar ese comportamiento definí el color `$link-hover-color`, que por defecto es negro, en el archivo `custom-variables.scss`. Ese será el color al que cambie el texto cuando me detengo sobre él, escogí un rojo oscuro que me parece tiene 2 virtudes: resalta sin lugar a dudas el texto y no se desvía mucho de la identidad visual que quiero dar a la página. Luego modifiqué el comportamiento de los links cuando me detengo sobre ellos. En el archivo `custom-styles.scss` agregué lo siguiente,
```
a {
  color: $link-base-color;
  text-decoration: none;

  &:visited {
    color: $link-visited-color;
  }

  &:hover {
    color: $link-hover-color;
    text-decoration: none;
  }

  .social-media-list &:hover {
    text-decoration: none;

    .username {
      text-decoration: underline;
    }
  }
}
```
El código lo copié directamente de los temas de *minima* y el único cambio necesario fue poner `text-decoration: none`

### intento de puntuación colgante

Un par de agregados simples a `custom-styles.scss`, para que las listas y los bloques de citas no tengan indentación. *Intento* porque una implementación verdadera sería un script que analice el texto y tire la puntuación al margen, dejando todo el texto alineado.

```
ul, ol {
  margin-left: 0em;
}

blockquote {
  margin-left: -1em;
  margin-right: -1em;
  padding-left: 1em;
  padding-right: 1em;
  border-left: -4px solid $border-color-01;
  border-right: -4px solid $border-color-01;
}
```

[^1]: Como ejemplo, acá abajo se ve el efecto de cambiar los primeros 2 bloques, el link que nos envía a esta nota tiene el tamaño definido en el tercer bloque. En el segundo bloque, `border-top` agrega la línea de separación entre el texto y las notas.
