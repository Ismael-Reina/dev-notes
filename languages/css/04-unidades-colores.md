# 04. Unidades y Colores

## Unidades

Las unidades en CSS definen el tamaño de las propiedades (como `font-size`, `width`, `margin`, etc.). Se dividen en dos grandes grupos:

### 1. Unidades Absolutas

Su valor es fijo y no depende de ningún otro elemento.

* **`px` (Píxeles)**: La unidad absoluta más común. Es un "punto" en la pantalla. Es útil para elementos que *nunca* deben cambiar de tamaño, como un `border` de 1px.

### 2. Unidades Relativas

Su valor es flexible y se calcula en relación a otra cosa. Son **esenciales** para el diseño responsivo.

* **`%` (Porcentaje)**: Relativo al tamaño de su **contenedor padre**. Si un `div` tiene `width: 50%;`, ocupará la mitad del ancho de su padre.
* **`em`**: Relativo al **tamaño de fuente del elemento** (o del padre si no está definido). Si un elemento tiene `font-size: 16px`, entonces `2em` son `32px`.
* **`rem` (Root EM)**: Esta es la unidad relativa **más recomendada** para tipografías y espaciado. Es relativa al tamaño de fuente del **elemento raíz (`<html>`)**.
    * **Ventaja:** Si el usuario cambia el tamaño de fuente en su navegador (por accesibilidad), tu diseño se escalará proporcionalmente. Si usas `px`, el texto se quedará fijo.
* **`vw` (Viewport Width)**: 1vw es el 1% del ancho de la ventana del navegador.
* **`vh` (Viewport Height)**: 1vh es el 1% del alto de la ventana del navegador.

**Recomendación:** Usa `rem` para `font-size`, `padding` y `margin`. Usa `%` o `vw` para anchos de `layout` (columnas). Usa `px` solo para bordes o decoraciones muy pequeñas.

## Colores

Hay varias formas de definir colores en CSS.

* **Keywords (Nombres)**
  `color: red;`
  `background-color: steelblue;`

* **HEX (Hexadecimal)**
  `color: #FF0000;` /* `#RRGGBB` */
  `color: #F00;` /* Abreviado: `#RGB` */
  `color: #FF000080;` /* Con transparencia: `#RRGGBBAA` */

* **RGB (Red, Green, Blue)**
  `color: rgb(255, 0, 0);` /* De 0 a 255 */

* **RGBA (Con transparencia)**
  `color: rgba(255, 0, 0, 0.5);` /* El 0.5 es 50% de opacidad */

* **HSL (Hue, Saturation, Lightness)**
  Es una forma más intuitiva de definir colores.
  `color: hsl(0, 100%, 50%);` /* (Tono, Saturación, Luminosidad) */
  `color: hsla(0, 100%, 50%, 0.5);` /* Con transparencia */

**Nota:** En CSS moderno, ya no necesitas usar `rgba` o `hsla`. Puedes pasar la transparencia directamente a `rgb` y `hsl` usando una barra (`/`):
`color: rgb(255 0 0 / 0.5);`
`color: hsl(0 100% 50% / 0.5);`

## Recursos para Profundizar

* **MDN (Mozilla Developer Network)**:
    * [Unidades de longitud en CSS](https://developer.mozilla.org/es/docs/Web/CSS/length)
    * [El tipo de dato `<color>`](https://developer.mozilla.org/es/docs/Web/CSS/color_value)
* **Google Color Picker**: Una herramienta visual para obtener valores HEX, RGB y HSL.
    * (Simplemente busca "color picker" en Google)

---

[◀ Volver: Modelo de Caja](./03-box-model.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Tipografía ▶](./05-tipografia-texto.md)
