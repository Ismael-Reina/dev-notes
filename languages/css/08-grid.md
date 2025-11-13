# 08. Guía Esencial de CSS Grid

CSS Grid es un modelo de diseño **bidimensional** (o 2D). A diferencia de Flexbox, que trabaja en un solo eje (fila *o* columna), Grid fue diseñado para manejar ambos ejes (filas *y* columnas) al mismo tiempo.

Es la herramienta más potente que tenemos en CSS para crear maquetas (layouts) complejas, como la estructura de una página entera, una galería de imágenes o un dashboard.

## Los Conceptos Clave: La Rejilla

El concepto central de Grid es la "rejilla": un conjunto de **líneas horizontales y verticales** que dividen el espacio en **filas**, **columnas** y "celdas".

Al igual que en Flexbox, todo se basa en la relación entre un **Contenedor** (el padre) y sus **Hijos** (los *items*).

## Propiedades del Contenedor (Padre)

Estas propiedades se aplican al elemento que define la rejilla.

### `display: grid;`
El interruptor. Convierte el contenedor en una rejilla y a sus hijos directos en *grid items*.

### `grid-template-columns`
Esta es la propiedad más importante. Define las columnas de tu rejilla.

* **Unidades Fijas (`px`)**:
  `grid-template-columns: 200px 100px 300px;` (Crea 3 columnas con esos anchos).
* **Unidades Flexibles (`fr`)**: La unidad `fr` (fracción) es la estrella de Grid. Reparte el espacio disponible.
  `grid-template-columns: 1fr 1fr 1fr;` (Crea 3 columnas del mismo ancho).
  `grid-template-columns: 2fr 1fr;` (Crea 2 columnas; la primera es el doble de ancha que la segunda).
* **Función `repeat()`**: Un atajo para no escribir lo mismo varias veces.
  `grid-template-columns: repeat(3, 1fr);` (Es idéntico a `1fr 1fr 1fr`).

```css
.contenedor-grid {
  display: grid;
  /* Crea una rejilla de 12 columnas,
     cada una ocupando 1 fracción del espacio.
     Esta es la base de los layouts clásicos. */
  grid-template-columns: repeat(12, 1fr);
}
```

### `grid-template-rows`
Exactamente igual que el anterior, pero para definir la altura de las **filas**.

* `grid-template-rows: 100px 300px;` (Dos filas de alturas fijas).
* `grid-template-rows: repeat(4, 100px);` (Cuatro filas, todas de 100px de alto).

### `gap`
Igual que en Flexbox, define el espacio (canaleta) *entre* las celdas de la rejilla.

```css
.contenedor-grid {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  gap: 20px; /* 20px de espacio entre filas Y columnas */
  
  /* También puedes ser específico: */
  /* row-gap: 20px; */
  /* column-gap: 10px; */
}
```

---

## Propiedades de los Hijos (Items)

Estas propiedades se aplican directamente a los elementos hijos para decirles **dónde deben colocarse** dentro de la rejilla.

Grid funciona con un sistema de **líneas numeradas**. Si tienes 3 columnas, tienes 4 líneas de columna (la del inicio, las dos del medio y la del final).

### `grid-column-start` / `grid-column-end`
Define en qué línea de columna empieza y termina el hijo.

### `grid-row-start` / `grid-row-end`
Define en qué línea de fila empieza y termina el hijo.

```html
<div class="contenedor-grid">
  <div class="header">Header</div>
  <div class="sidebar">Sidebar</div>
  <div class="main">Main Content</div>
</div>
```

```css
.contenedor-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr); /* 4 columnas, 5 líneas */
  grid-template-rows: 100px 500px; /* 2 filas, 3 líneas */
  gap: 10px;
}

.header {
  /* Empieza en la línea 1 y termina en la línea 5
     (ocupa las 4 columnas) */
  grid-column-start: 1;
  grid-column-end: 5;
  
  /* Se ubica en la primera fila */
  grid-row-start: 1;
}

.sidebar {
  /* Se ubica en la primera columna de la segunda fila */
  grid-column-start: 1;
  grid-row-start: 2;
}

.main {
  /* Empieza en la línea 2 de columna y
     ocupa hasta la línea 5 */
  grid-column-start: 2;
  grid-column-end: 5;
  grid-row-start: 2;
}
```

### Los atajos: `grid-column` y `grid-row`
Son los atajos para las propiedades anteriores (`inicio / fin`).

```css
.header {
  /* (inicio) / (fin) */
  grid-column: 1 / 5;
  grid-row: 1 / 2;
}

/* También puedes usar "span" para decir "ocupa X celdas" */
.main {
  grid-column: 2 / span 3; /* Empieza en 2, ocupa 3 columnas */
}
```

## Recursos para Profundizar

* **Grid Garden (Juego Interactivo)**: ¡El hermano de Flexbox Froggy! Imprescindible para aprender a posicionar elementos en la rejilla.
    * [Jugar a Grid Garden](https://cssgridgarden.com/#es)
* **CSS-Tricks (Guía Visual)**: La guía de referencia más famosa sobre Grid (en inglés, muy visual).
    * [A Complete Guide to Grid](https://css-tricks.com/snippets/css/complete-guide-grid/)
* **MDN (Mozilla Developer Network)**:
    * [Conceptos básicos de CSS Grid](https://developer.mozilla.org/es/docs/Web/CSS/CSS_Grid_Layout/Basic_Concepts_of_Grid_Layout)

---

[◀ Volver: Flexbox](./07-flexbox.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Diseño Responsivo ▶](./09-responsive-design.md)
