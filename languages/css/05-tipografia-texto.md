# 05. Tipografía y Texto

Controlar la tipografía es uno de los aspectos más importantes del diseño web. CSS nos da un control total sobre las propiedades de la fuente (cómo se ve la letra) y del texto (cómo se alinea y decora).

## Propiedades de Fuente (font)

Estas propiedades definen la apariencia de los caracteres.

### `font-family`

Define el tipo de letra. Es una "pila": el navegador intentará usar la primera fuente de la lista. Si no la tiene, pasará a la siguiente, y así sucesivamente.

**Es vital** terminar siempre con una palabra clave genérica (`serif` o `sans-serif`) como "plan B".

```css
body {
  /* El navegador buscará "Roboto". Si no la encuentra,
     buscará "Arial". Si tampoco, usará cualquier
     fuente "sans-serif" que tenga el sistema. */
  font-family: "Roboto", Arial, sans-serif;
}
```

### `font-size`

Define el tamaño del texto. La unidad más recomendada es **`rem`**, ya que escala de forma predecible y es accesible (respeta el tamaño de fuente preferido por el usuario en su navegador).

```css
html {
  /* Establecemos la base: 1rem = 16px (por defecto) */
  font-size: 16px; 
}

h1 {
  font-size: 3rem; /* 3 * 16px = 48px */
}

p {
  font-size: 1rem; /* 1 * 16px = 16px */
}
```

### `font-weight`

Define el "grosor" de la fuente.

```css
p {
  font-weight: normal; /* Grosor estándar (equivale a 400) */
}

strong {
  font-weight: bold;   /* Texto en negrita (equivale a 700) */
}

.subtitulo {
  font-weight: 300;    /* Un peso más ligero (si la fuente lo soporta) */
}
```

### Importar Fuentes (Web Fonts)

Rara vez usarás solo las fuentes del sistema. Lo normal es importar fuentes externas, como las de **Google Fonts**. Esto se hace en el `<head>` del HTML o al principio del CSS.

**Ejemplo con `@import` en CSS:**
```css
/* Al principio de tu archivo style.css */
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

body {
  font-family: 'Roboto', sans-serif;
}
```

## Propiedades de Texto (text)

Estas propiedades definen cómo se comporta el bloque de texto.

### `color`

Define el color del texto. (Lo vimos en el capítulo 04).

```css
p {
  color: #333; /* Un gris oscuro, más legible que el negro puro */
}
```

### `text-align`

Define la alineación horizontal del texto.

* `left`: Alineado a la izquierda (por defecto).
* `right`: Alineado a la derecha.
* `center`: Centrado.
* `justify`: Justificado (alineado a ambos márgenes).

```css
h1 {
  text-align: center;
}
```

### `line-height`

Define la altura de la línea (el "interlineado"). Para una mejor legibilidad y escalabilidad, **se recomienda usar un valor sin unidad** (ej. `1.5`). Esto significa "1.5 veces el `font-size` del elemento".

```css
p {
  font-size: 1rem;     /* 16px */
  line-height: 1.6;  /* 1.6 * 16px = 25.6px de altura de línea */
}
```

### `text-decoration`

Añade (o quita) líneas decorativas. El uso más común es quitar el subrayado de los enlaces.

```css
a {
  text-decoration: none; /* Quita el subrayado */
  color: steelblue;
}

a:hover {
  text-decoration: underline; /* Añade el subrayado solo al pasar el ratón */
}
```

## Recursos para Profundizar

* **Google Fonts**: El directorio más grande y popular para explorar e importar fuentes web.
    * [Explorar Google Fonts](https://fonts.google.com/)
* **MDN (Mozilla Developer Network)**:
    * [Fundamentos de texto y fuentes tipográficas](https://developer.mozilla.org/es/docs/Learn_web_development/Core/Text_styling/Fundamentals)
    * [Guía de `line-height`](https://developer.mozilla.org/es/docs/Web/CSS/line-height)

---

[◀ Volver: Unidades y Colores](./04-unidades-colores.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Layout Básico ▶](./06-layout-basico.md)
