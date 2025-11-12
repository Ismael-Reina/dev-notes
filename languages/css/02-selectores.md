# 02. Selectores de CSS

Un **selector** es la parte de la regla de CSS que "selecciona" el elemento o elementos HTML a los que queremos aplicar los estilos. Dominarlos es la clave para controlar tu página.

## 1. Selectores Básicos

Son los más comunes y forman la base de todo lo demás.

| Tipo | Sintaxis | Ejemplo | Descripción |
| :--- | :--- | :--- | :--- |
| **Elemento** | `etiqueta` | `p { ... }` | Selecciona todas las etiquetas `<p>`. |
| **Clase** | `.nombreclase` | `.btn-primario { ... }` | Selecciona todos los elementos con `class="btn-primario"`. Es la forma más usada y flexible de aplicar estilos. |
| **ID** | `#nombreid` | `#header { ... }` | Selecciona el único elemento con `id="header"`. **Importante:** Un ID debe ser único en toda la página. |
| **Universal** | `*` | `* { ... }` | Selecciona **todos** los elementos de la página. (Usado con precaución, por ejemplo, para resetear márgenes). |

## 2. Selectores de Atributo

Permiten seleccionar elementos basándose en sus atributos HTML.

* `[href]` - Selecciona elementos que tengan un atributo `href`.
* `[target="_blank"]` - Selecciona elementos que tengan `target="_blank"`.
* `[href*="google.com"]` - Selecciona elementos cuyo `href` *contenga* "google.com".

## 3. Pseudo-clases

Son selectores que aplican estilos a un elemento en función de su **estado** o **posición**. Se escriben con dos puntos (`:`).

* `:hover` - Cuando el ratón está encima del elemento.
* `:focus` - Cuando el elemento está "seleccionado" (ej. un campo de formulario).
* `:first-child` - Selecciona el primer hijo de un contenedor.
* `:last-child` - Selecciona el último hijo.
* `:nth-child(n)` - Selecciona el enésimo hijo (ej. `:nth-child(2)`, `:nth-child(even)` para los pares).
* `:not(.clase)` - Selecciona los elementos que *no* tengan esa clase.

## 4. Pseudo-elementos

Permiten estilizar una **parte específica** de un elemento. Se escriben con dos puntos dobles (`::`).

* `::before` - Crea un "falso" elemento justo antes del contenido del elemento seleccionado.
* `::after` - Crea un "falso" elemento justo después del contenido.
* `::first-letter` - Estiliza la primera letra de un texto.
* `::first-line` - Estiliza la primera línea de un texto.

## 5. Combinadores

Permiten crear selectores más complejos combinando selectores simples.

* **Descendiente (espacio)**
  * `div p { ... }` - Selecciona **todos** los `<p>` que estén *dentro* de un `<div>`, sin importar lo profundo que estén.
* **Hijo Directo (`>`)**
  * `div > p { ... }` - Selecciona solo los `<p>` que sean **hijos directos** (primer nivel) de un `<div>`.
* **Hermano Adyacente (`+`)**
  * `h2 + p { ... }` - Selecciona el `<p>` que esté **inmediatamente después** de un `<h2>` (y que sean hermanos).
* **Hermano General (`~`)**
  * `h2 ~ p { ... }` - Selecciona **todos** los `<p>` que vengan después de un `<h2>` (y que sean hermanos).

## Recursos para Profundizar

* **CSS Diner (Juego Interactivo)**: El mejor recurso para aprender selectores de forma práctica y divertida. Es un juego donde tienes que "seleccionar" platos usando CSS.
    * [Jugar a CSS Diner](https://flukeout.github.io/)
* **MDN (Mozilla Developer Network)**: La referencia completa de todos los selectores.
    * [Referencia de Selectores CSS en MDN](https://developer.mozilla.org/es/docs/Web/CSS/CSS_Selectors)

---

[◀ Volver: Fundamentos](./01-fundamentos.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Modelo de Caja ▶](./03-box-model.md)
