# 03. El Modelo de Caja (Box Model)

El **Modelo de Caja** (o *Box Model*) es el concepto más fundamental de CSS. La idea es simple: **cada elemento en una página web es una caja rectangular**.

Esta caja está compuesta por cuatro capas, de adentro hacia afuera:

1.  **Content (Contenido)**: El área donde se muestra tu texto, imágenes, etc.
2.  **Padding (Relleno)**: Un espacio transparente alrededor del contenido, *dentro* del borde.
3.  **Border (Borde)**: Una línea que rodea el padding y el contenido.
4.  **Margin (Margen)**: Un espacio transparente *fuera* del borde, que empuja a otros elementos.



## `box-sizing`: El interruptor clave

Por defecto, los navegadores usan un `box-sizing: content-box`. Esto causa un problema: si defines una caja con `width: 100px;` y luego añades `padding: 10px;` y `border: 1px;`, el ancho *total* de la caja será:

`100px (content) + 20px (padding izq/der) + 2px (border izq/der) = 122px`

Esto es muy poco intuitivo y dificulta el diseño.

### La solución: `box-sizing: border-box`

Casi todos los desarrolladores modernos aplican esta regla a todos los elementos.

`box-sizing: border-box;` le dice al navegador: "Cuando yo digo `width: 100px;`, quiero que la caja mida 100px en total, incluyendo `padding` y `border`".

Si ahora defines `width: 100px;` con `padding: 10px;`, el navegador calculará automáticamente que el área de *contenido* debe ser de 80px para que el total siga siendo 100px.

### "El Reset Universal"

Por esta razón, la mayoría de los proyectos comienzan con este código para aplicar `border-box` a todo:

```css
* {
  box-sizing: border-box;
}
```

(Algunas personas prefieren un método ligeramente diferente, pero la idea es la misma: hacer que `border-box` sea el comportamiento por defecto).

## Recursos para Profundizar

* **MDN (Mozilla Developer Network)**:
  * [El Modelo de Caja (Explicación detallada)](https://www.google.com/search?q=https://developer.mozilla.org/es/docs/Learn/CSS/Building_blocks/Box_Model)
  * [La propiedad box-sizing](https://developer.mozilla.org/es/docs/Web/CSS/box-sizing)

---

[◀ Volver: Selectores](./02-selectores.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Unidades y Colores ▶](./04-unidades-colores.md)

