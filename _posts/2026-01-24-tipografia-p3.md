---
layout:      post
title:       "modificando la tipografía de upeb, p.3"
date:        2026-01-24 11:16:52 -0600
categories:  post
katex: true
---
Intentando una vez más reactivar este blog.

El cambio más reciente es pasarme de MathJax a KaTeX para desplegar la poca matemática que tengo desparramada en varios posts. Además, me deshice del sistema de tags---al final no agregaba valor.

Activar KaTeX fue algo sufrido, afortunadamente está bien documentado en la web
- [How to LaTeX in Jekyll using KaTeX](https://www.xuningyang.com/blog/2021-01-11-katex-with-jekyll)
- [How I blog about math: an update on KaTeX with Jekyll](https://gendignoux.com/blog/2020/05/23/katex.html)

Yo seguí la ruta de menos resistencia: usar la extensión de auto-render.

El primer paso es modificar `_config.yml` para evitar que Jekyll transforme las fórmulas antes de tiempo
```yaml
markdown: kramdown
kramdown:
  math_engine: null
```

Luego solamente agregué el siguiente código a `_includes/custom_head.html`

```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/katex@0.16.10/dist/katex.min.css">
<script defer src="https://cdn.jsdelivr.net/npm/katex@0.16.10/dist/katex.min.js"></script>
<script defer src="https://cdn.jsdelivr.net/npm/katex@0.16.10/dist/contrib/auto-render.min.js"></script>

<script>
    document.addEventListener("DOMContentLoaded", function() {
        // 1. Renderizado estándar de delimitadores
        renderMathInElement(document.body, {
            delimiters: [
                {left: "$$", right: "$$", display: true},
                {left: "$", right: "$", display: false},
                {left: "\\(", right: "\\)", display: false},
                {left: "\\[", right: "\\]", display: true}
            ],
            throwOnError : false
        });

        // 2. Fix para GitHub Pages / Kramdown
        // A veces Kramdown envuelve las fórmulas en <script type="math/tex">
        document.querySelectorAll('script[type="math/tex"]').forEach(function(el) {
            let tex = el.innerText;
            let span = document.createElement('span');
            katex.render(tex, span, { displayMode: false });
            el.parentNode.replaceChild(span, el);
        });

        document.querySelectorAll('script[type="math/tex; mode=display"]').forEach(function(el) {
            let tex = el.innerText;
            let div = document.createElement('div');
            katex.render(tex, div, { displayMode: true });
            el.parentNode.replaceChild(div, el);
        });
    });
</script>
```

El problema de Kramdown y Jekyll: GitHub Pages usa Kramdown, que intenta ser muy inteligente y a veces "disfraza" las fórmulas. El script de arriba busca esos "disfraces" y los fuerza a renderizarse.

En particular: Jekyll de forma local reconoce bien los delimitadores `$$` para `display: true`, sin embargo en GitHub Pages Jekyll traduce `$$` a la sintaxis tradicional de $\mathrm{\LaTeX}$, `\[` y `\]`. No solo eso, sino que aunque la sintaxis tradicional se defina como delimitadores, el parsing no se hace en todas las secciones, resultando en errores de renderizado. Por eso fue también necesario incluir los `querySelectorAll`.