# 06. Layout Básico (Display y Position)

Antes de que Flexbox y Grid dominaran el mundo, el layout en CSS se controlaba con dos propiedades clave: `display` y `position`. Siguen siendo absolutamente esenciales.

## La propiedad `display`

La propiedad `display` define cómo se comporta la "caja" de un elemento y cómo interactúa con las cajas a su alrededor. Los valores más importantes son:

### `display: block`

* **Comportamiento:** Ocupa **todo el ancho** disponible y se coloca en una **nueva línea**.
* **Acepta:** `width`, `height`, `margin` y `padding`.
* **Ejemplos comunes:** `<div>`, `<p>`, `<h1>` a `<h6>`, `<section>`, `<header>`, `<footer>`, `<li>`.

```css
.caja-block {
  display: block;
  width: 100px;
  height: 100px;
  background: steelblue;
  margin: 10px;
}
/* Dos de estas cajas se apilarán una encima de otra. */
```

### `display: inline`

* **Comportamiento:** Ocupa **solo el ancho de su contenido** y se coloca en la **misma línea** que otros elementos `inline`.
* **NO ACEPTA:** `width` o `height`. Ignora `margin` y `padding` vertical.
* **Ejemplos comunes:** `<a>`, `<span>`, `<strong>`, `<img>`.

```css
.texto-inline {
  display: inline;
  background: gold;
  padding: 10px; /* Solo funcionará el padding horizontal */
  width: 300px; /* Esta línea será ignorada */
}
/* Dos de estos textos se pondrán uno al lado del otro. */
```

### `display: inline-block`

* **Comportamiento:** Es el híbrido perfecto. Se coloca en la **misma línea** (como `inline`) pero...
* **Acepta:** `width`, `height`, `margin` y `padding` (como `block`).
* **Uso:** Perfecto para botones, elementos de navegación, o cualquier cosa que quieras que esté en línea pero que necesite dimensiones específicas.

### `display: none`

* **Comportamiento:** Oculta el elemento por completo. El elemento **desaparece** de la página como si nunca hubiera existido en el HTML (no ocupa espacio).

---

## La propiedad `position`

La propiedad `position` define cómo se coloca un elemento en la página, permitiéndonos sacarlo del "flujo" normal del documento.

### `position: static`
Es el valor por defecto. El elemento simplemente sigue el flujo normal de la página.

### `position: relative`
* **Comportamiento:** El elemento se queda en su sitio original, pero ahora puedes "moverlo" con `top`, `bottom`, `left` y `right` **relativo a su posición inicial**.
* **Importante:** El espacio que ocupaba originalmente se mantiene reservado.
* **Uso principal:** Se usa casi siempre como **contexto de posicionamiento** para un hijo `absolute`.

### `position: absolute`
* **Comportamiento:** El elemento **se saca del flujo normal** (los otros elementos actúan como si no existiera).
* **Posicionamiento:** Se posiciona usando `top`, `bottom`, `left` y `right` con respecto a su **ancestro posicionado más cercano** (cualquier padre que tenga `position` distinto de `static`).
* **Si no hay un padre posicionado**, se posiciona con respecto al `<body>`.

```html
<div class="contenedor-relative">
  <div class="caja-absolute">
    </div>
</div>
```

```css
.contenedor-relative {
  position: relative;
  width: 300px;
  height: 300px;
}

.caja-absolute {
  position: absolute;
  top: 10px;
  right: 10px;
  width: 50px;
  height: 50px;
}
/* La caja se pondrá a 10px del borde superior y derecho
   de su "contenedor-relative" */
```

### `position: fixed`
* **Comportamiento:** El elemento **se saca del flujo normal** y se posiciona con respecto a la **ventana del navegador** (el *viewport*).
* **Efecto:** El elemento **no se mueve** cuando el usuario hace scroll.
* **Uso:** Perfecto para barras de navegación "pegajosas", banners de cookies o botones de "Volver arriba".

### `position: sticky`
* **Comportamiento:** Es un híbrido. Se comporta como `relative` hasta que el usuario hace scroll y "choca" con un umbral (definido por `top`, `bottom`, etc.).
* **Efecto:** En ese momento, se "pega" y se comporta como `fixed`.
* **Uso:** Ideal para cabeceras de tablas o índices de blog que quieres que se queden fijos al hacer scroll.

## Recursos para Profundizar

* **MDN (Mozilla Developer Network)**:
    * [La propiedad `display`](https://developer.mozilla.org/es/docs/Web/CSS/display)
    * [La propiedad `position`](https://developer.mozilla.org/es/docs/Web/CSS/position)
* **CSS-Tricks**:
    * [Guía de `position` (Inglés, muy visual)](https://css-tricks.com/almanac/properties/p/position/)

---

[◀ Volver: Tipografía](./05-tipografia-texto.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Flexbox ▶](./07-flexbox.md)
