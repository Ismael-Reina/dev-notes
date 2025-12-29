# 04. Accesibilidad Visual y Sensorial

No todos los usuarios perciben la web a través de la vista, y aquellos que sí lo hacen no siempre ven de la misma manera (daltonismo, baja visión, deslumbramiento). Este capítulo trata de garantizar que el contenido sea **perceptible** para todos.

## 1. El Color y el Contraste

El texto debe tener suficiente contraste respecto al fondo para ser legible. Si el contraste es bajo, el texto se vuelve invisible para muchas personas.

### Ratios de Contraste (WCAG AA)

* **Texto Normal:** Ratio mínimo de **4.5:1**.
* **Texto Grande (18pt+ o 14pt negrita):** Ratio mínimo de **3:1**.
* **Componentes de UI (Bordes de inputs, iconos):** Ratio mínimo de **3:1**.

> **Herramienta:** Usa la pestaña "CSS Overview" o el selector de color de las DevTools de tu navegador para comprobar el contraste automáticamente.

### No depender solo del color

**Regla de Oro:** Nunca uses el color como el *único* medio para transmitir información.

* *Mal:* "Los campos obligatorios están en rojo". (Un daltónico no distinguirá el rojo).
* *Bien:* "Los campos obligatorios están marcados con un asterisco (*)".
* *Mal:* Un gráfico de líneas donde solo cambian los colores de las líneas.
* *Bien:* Un gráfico donde las líneas tienen colores Y patrones diferentes (puntos, guiones) o etiquetas directas.

## 2. Imágenes y Texto Alternativo (`alt`)

El atributo `alt` es la voz de la imagen para quien no puede verla.

### ¿Cuándo usar `alt`?

Hazte esta pregunta: **"Si elimino esta imagen, ¿el usuario pierde información?"**

1.  **Imagen Informativa:** Aporta contenido.
    * *Solución:* `alt="Descripción concisa de lo que se ve o la función que cumple"`.
2.  **Imagen Decorativa:** Solo es estética (bordes, formas abstractas, fotos de stock genéricas).
    * *Solución:* `alt=""` (vacío). Esto le dice al lector de pantalla: "Ignora esta imagen".
    * *Nota:* Si *no* pones el atributo `alt`, el lector leerá el nombre del archivo (ej: `IMG_2034.jpg`), lo cual es una pésima experiencia.

### Imágenes con Texto

Evita usar imágenes que contengan texto (como banners promocionales diseñados en Photoshop).
* **Problema:** Al hacer zoom se pixelan y el lector de pantalla no puede leer el texto interior.
* **Solución:** Usa texto real HTML y CSS para el estilo. Si es inevitable (ej. un logo), el `alt` debe decir exactamente lo que dice el texto de la imagen.

## 3. Iconos Accesibles (SVG)

Los iconos (como una lupa de búsqueda o una "X" de cerrar) suelen ser invisibles para los lectores si no se etiquetan.

**Patrón para botones de solo icono:**

```html
<button>
  <svg aria-hidden="true" focusable="false">...</svg>
  
  <span class="sr-only">Cerrar menú</span>
</button>
```

* `aria-hidden="true"`: Oculta el SVG al lector (para que no intente describirlo como "gráfico").
* `.sr-only`: Una clase CSS que oculta el texto visualmente pero lo mantiene en el DOM accesible.

## 4. Preferencias del Usuario (Media Queries)

CSS nos permite adaptarnos a las necesidades sensoriales del usuario detectando su configuración del sistema operativo.

### Modo Oscuro (`prefers-color-scheme`)
Respeta si el usuario prefiere una interfaz clara u oscura.

### Reducción de Movimiento (`prefers-reduced-motion`)
Fundamental para usuarios con trastornos vestibulares (mareos, vértigos) a quienes las animaciones bruscas pueden causarles malestar físico.

```css
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
    scroll-behavior: auto !important;
  }
}
```

## Recursos

* **[WebAIM Contrast Checker](https://webaim.org/resources/contrastchecker/)**: Herramienta online para verificar contrastes.
* **[Simulador de Daltonismo (Toptal)](https://www.toptal.com/designers/colorfilter)**: Para ver tu web como la vería una persona daltónica.

---

[◀ Volver: WAI-ARIA](./03-wai-aria.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Formularios ▶](./05-formularios-y-componentes.md)
