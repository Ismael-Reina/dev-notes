# 07. Guía Esencial de Flexbox

Flexbox (o *Flexible Box Layout*) es un modelo de diseño **unidimensional**. Es la herramienta moderna de CSS para alinear, distribuir y ordenar elementos a lo largo de un solo eje (ya sea una fila o una columna).

## Los Conceptos Clave: Ejes

Todo en Flexbox gira en torno a dos ejes:

* **Eje Principal (Main Axis)**: Es la dirección principal en la que se colocan los elementos (por defecto, en horizontal).
* **Eje Cruzado (Cross Axis)**: Es el eje perpendicular al principal (por defecto, en vertical).

## La Magia: Contenedor e Hijos

Para usar Flexbox, solo necesitas dos cosas:

1.  Un **Contenedor** (el elemento padre).
2.  **Hijos** (los elementos que quieres alinear).

Aplicando `display: flex;` al contenedor, todos sus hijos directos se convierten en "hijos flex" y empiezan a obedecer las reglas de Flexbox.

```html
<div class="contenedor-flex">
  <div class="hijo">1</div>
  <div class="hijo">2</div>
  <div class="hijo">3</div>
</div>
```

## Propiedades del Contenedor (Padre)

Estas propiedades se aplican al elemento contenedor (ej. `.contenedor-flex`).

### `display: flex;`
El interruptor. Activa Flexbox en el contenedor.

### `flex-direction`
Define la dirección del **Eje Principal**.

* `row`: (Por defecto) Los hijos se colocan en una fila horizontal, de izquierda a derecha.
* `row-reverse`: En fila, de derecha a izquierda.
* `column`: Los hijos se colocan en una columna vertical, de arriba a abajo.
* `column-reverse`: En columna, de abajo a arriba.

```css
.contenedor-flex {
  display: flex;
  flex-direction: column; /* Apila los hijos verticalmente */
}
```

### `flex-wrap`
Define si los hijos pueden "saltar" a la siguiente línea si no caben.

* `nowrap`: (Por defecto) Todos los hijos se fuerzan a estar en una sola línea (pueden desbordarse).
* `wrap`: Los hijos saltan a la línea siguiente si no hay espacio.
* `wrap-reverse`: Saltan a la línea siguiente, pero en orden inverso.

### `justify-content`
Alinea a los hijos a lo largo del **Eje Principal**.

* `flex-start`: (Por defecto) Los hijos al principio.
* `flex-end`: Los hijos al final.
* `center`: Los hijos al centro.
* `space-between`: Espacio uniforme *entre* los hijos (el primero y el último se pegan a los bordes).
* `space-around`: Espacio uniforme *alrededor* de cada hijo (hay espacio en los bordes).
* `space-evenly`: Espacio uniforme *entre* hijos y *en los bordes*.

### `align-items`
Alinea a los hijos a lo largo del **Eje Cruzado**.

* `stretch`: (Por defecto) Los hijos se estiran para ocupar todo el alto/ancho del eje cruzado.
* `flex-start`: Los hijos al principio del eje cruzado.
* `flex-end`: Los hijos al final del eje cruzado.
* `center`: Los hijos al centro del eje cruzado.

### `gap`
Es la forma moderna de añadir espacio *entre* los hijos, sin tener que usar márgenes.

```css
.contenedor-flex {
  display: flex;
  gap: 10px; /* 10px de espacio entre cada hijo */
}
```

---

## Propiedades de los Hijos

Estas propiedades se aplican directamente a los elementos hijos (ej. `.hijo`).

### `flex-grow`
Define la capacidad de un hijo para "crecer" si hay espacio sobrante. Es un número sin unidad.

* `flex-grow: 0;` (Por defecto): El hijo no crece.
* `flex-grow: 1;`: El hijo crecerá para ocupar el espacio sobrante disponible.

Si todos los hijos tienen `flex-grow: 1;`, el espacio sobrante se reparte en partes iguales.

### `flex-shrink`
Define la capacidad de un hijo para "encogerse" si no hay espacio.

* `flex-shrink: 1;` (Por defecto): El hijo se encoge si es necesario.
* `flex-shrink: 0;`: El hijo no se encoge, mantendrá su tamaño original.

### `flex-basis`
Define el tamaño "ideal" o inicial de un hijo antes de que `flex-grow` o `flex-shrink` actúen.

* `flex-basis: auto;` (Por defecto): El tamaño se basa en el contenido del hijo.
* `flex-basis: 200px;`: El hijo "intentará" medir 200px.

### El atajo: `flex`
Es la propiedad abreviada que combina `flex-grow`, `flex-shrink` y `flex-basis`.

```css
.hijo {
  /* grow | shrink | basis */
  flex: 0 1 auto; /* Este es el valor por defecto */
}

/* El atajo más común: */
.hijo {
  flex: 1;
}
/* Esto es un atajo para: flex: 1 1 0; */
/* Significa: "Crece (1), Encógete (1), y tu tamaño base es 0" */
/* Resultado: Todos los hijos con "flex: 1" ocuparán el mismo espacio. */
```

### `order`
Permite cambiar el orden visual de los hijos sin cambiar el HTML.

* `order: 0;` (Por defecto).
* `order: -1;` (Se coloca antes).
* `order: 1;` (Se coloca después).

### `align-self`
Permite que un hijo *ignore* el `align-items` del contenedor y tenga su propia alineación en el eje cruzado.

```css
.hijo-especial {
  /* El contenedor tiene "align-items: center"
     pero este hijo se irá al final. */
  align-self: flex-end;
}
```

## Recursos para Profundizar

* **Flexbox Froggy (Juego Interactivo)**: ¡Imprescindible! El mejor recurso para aprender y practicar Flexbox de forma visual y divertida.
    * [Jugar a Flexbox Froggy](https://flexboxfroggy.com/#es)
* **CSS-Tricks (Guía Visual)**: La guía de referencia más famosa sobre Flexbox (en inglés, pero muy visual).
    * [A Complete Guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
* **MDN (Mozilla Developer Network)**:
    * [Conceptos básicos de Flexbox](https://developer.mozilla.org/es/docs/Web/CSS/CSS_Flexible_Box_Layout/Basic_Concepts_of_Flexbox)

---

[◀ Volver: Layout Básico](./06-layout-basico.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Grid ▶](./08-grid.md)
