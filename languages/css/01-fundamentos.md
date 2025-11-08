# 01. Fundamentos de CSS

Antes de empezar a crear estilos complejos, necesitamos entender los tres pilares sobre los que se construye CSS: la **Cascada**, la **Especificidad** y la **Herencia**.

Pero primero, lo más básico.

## Sintaxis Básica

[cite_start]Una regla de CSS se compone de dos partes principales: un **selector** y un **bloque de declaración**[cite: 77].

```css
/* Esto es un comentario en CSS */

/* SELECTOR (a quién) */
p {
  /* BLOQUE DE DECLARACIÓN (qué) */
  color: blue; /* Declaración (Propiedad: valor;) */
  font-size: 16px; /* Declaración */
}
````

  * **Selector (`p`)**: Apunta al elemento (o elementos) HTML que queremos estilizar.
  * **Bloque de Declaración (`{...}`)**: Contiene una o más declaraciones.
  * **Declaración (`color: blue;`)**: La combinación de una **propiedad** (`color`) y un **valor** (`blue`), separados por dos puntos (`:`) y terminados con un punto y coma (`;`).

## Cómo Añadir CSS a HTML

Hay tres formas de conectar CSS con HTML:

### 1\. Externo (Recomendado)

Se enlaza un archivo `.css` independiente usando la etiqueta `<link>` dentro del `<head>` del HTML. Esta es la mejor práctica, ya que separa el contenido (HTML) de la presentación (CSS).

```html
<!DOCTYPE html>
<html>
<head>
  <title>Mi Página</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  ...
</body>
</html>
```

### 2\. Interno

Se escriben las reglas de CSS directamente en el HTML usando la etiqueta `<style>` dentro del `<head>`. Es útil para prototipos rápidos o estilos muy específicos de una sola página.

```html
<head>
  <title>Mi Página</title>
  <style>
    body {
      background-color: #f0f0f0;
    }
    p {
      color: darkblue;
    }
  </style>
</head>
```

### 3\. En Línea (No recomendado)

Se aplica el estilo directamente a una etiqueta HTML usando el atributo `style`. [cite\_start]**Se debe evitar** en la medida de lo posible, ya que rompe la separación de responsabilidades y tiene una especificidad muy alta[cite: 376], lo que dificulta el mantenimiento.

```html
<p style="color: red; font-size: 20px;">
  Este es un párrafo estilizado en línea.
</p>
```

## La "Magia" de CSS: Cascada, Especificidad y Herencia

Estos tres conceptos definen cómo CSS decide qué estilos aplicar cuando hay reglas en conflicto.

### Cascada

La "C" de CSS. [cite\_start]La cascada define el orden en que se aplican las reglas[cite: 370]. [cite\_start]Si dos reglas tienen la misma importancia (especificidad), **la última regla declarada gana**[cite: 372].

```css
p { color: blue; }
p { color: red; } /* Gana esta, el párrafo será rojo */
```

### Especificidad

[cite\_start]Es el sistema de puntuación que usa CSS para decidir qué regla es más importante[cite: 374]. Si una regla es más específica, "gana" a las demás, sin importar el orden (la Cascada).

La jerarquía de especificidad, de más a menos importante, es:

1.  [cite\_start]**`!important`**: Una "bomba nuclear" que anula todo lo demás[cite: 380]. Debe evitarse casi siempre, ya que dificulta la depuración.
2.  [cite\_start]**Estilos en Línea**: (Ej: `<p style="...">`)[cite: 376].
3.  [cite\_start]**ID**: (Ej: `#mi-id`)[cite: 377].
4.  [cite\_start]**Clases, Pseudo-clases, Atributos**: (Ej: `.mi-clase`, `:hover`, `[type="text"]`)[cite: 378].
5.  [cite\_start]**Elementos, Pseudo-elementos**: (Ej: `p`, `div`, `::before`)[cite: 379].

Un selector de ID (`#id`) siempre ganará a un selector de clase (`.clase`).

### Herencia

[cite\_start]Algunas propiedades de CSS, como `color` [cite: 196] [cite\_start]y `font-family` [cite: 197][cite\_start], se pasan ("heredan") de los elementos padres a sus hijos[cite: 195]. [cite\_start]Otras, como `border` [cite: 200] o `padding`, no se heredan.

  * Si `<body>` tiene `color: blue;`, todos los párrafos `<p>` dentro de él serán azules, a menos que una regla más específica diga lo contrario.

[cite\_start]Podemos controlar esto con valores especiales[cite: 201]:

  * [cite\_start]`inherit`: Forza a un elemento a heredar el valor de su padre[cite: 202].
  * [cite\_start]`initial`: Resetea la propiedad a su valor por defecto del navegador[cite: 204].
  * [cite\_start]`unset`: Actúa como `inherit` si la propiedad se hereda, o como `initial` si no[cite: 206].

## Recursos para Profundizar

  * **MDN (Mozilla Developer Network)**: La biblia de CSS.
      * [Conceptos básicos de CSS](https://www.google.com/search?q=https://developer.mozilla.org/es/docs/Learn/CSS/First_steps/What_is_CSS)
      * [La Cascada y la Herencia](https://developer.mozilla.org/es/docs/Learn/CSS/Building_blocks/Cascade_and_inheritance)
  * [cite\_start]**Calculadora de Especificidad**[cite: 386]: Una herramienta visual para entender cuánto "pesa" un selector.
      * [Calculadora de Keegan.st](https://specificity.keegan.st/)
  * [cite\_start]**Learn CSS (Google)**[cite: 71]: Un curso moderno y muy visual sobre todos los conceptos de CSS.
      * [Curso "Learn CSS" de web.dev](https://web.dev/learn/css?hl=es)

-----

[🏠 Ir al Índice](https://www.google.com/search?q=./README.md) | [Siguiente: Selectores 🠒](https://www.google.com/search?q=./02-selectores.md)

```
```
