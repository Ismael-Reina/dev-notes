# 02. Navegación por Teclado y Gestión del Foco

Cualquier persona que no pueda usar un ratón (ya sea por discapacidad motora permanente, temporal, o por usar un lector de pantalla) debe poder acceder a **todo** el contenido y las funciones de la web usando únicamente el **teclado**.

La tecla principal de navegación es el **Tabulador** (`Tab`).

## 1. El Orden Lógico del Foco (`Tab Order`)

El foco visual (el recuadro que indica dónde estás) se mueve por la página en un orden secuencial cuando pulsas `Tab`.

* **Orden por defecto:** Los elementos interactivos nativos (`<a>`, `<button>`, `<input>`, etc.) reciben el foco de forma automática. El orden natural del teclado sigue el **orden de aparición en el HTML (DOM)**.
* **El error común:** Usar CSS (`float`, `flex-direction: reverse`, `order`) para cambiar la posición visual de un elemento, sin cambiar su posición en el código HTML. Esto crea un "salto" ilógico e impredecible para el usuario de teclado.
    * **Regla:** El orden visual y el orden del DOM deben coincidir.

## 2. Indicador Visual del Foco (`Outline`)

Cuando un elemento recibe el foco, el navegador lo rodea por defecto con un **`outline`** (contorno).

* **Nunca ocultar:** El error más grave es añadir `*:focus { outline: none; }` en CSS. Esto hace que el usuario de teclado se quede "ciego" y no sepa dónde está.
* **Personalizar, no eliminar:** Si el `outline` por defecto es feo, debes reemplazarlo con algo más atractivo (un `box-shadow` o un `border` más grueso), pero nunca quitarlo sin sustitución.

```css
/* ¡MAL! NUNCA HAGAS ESTO */
*:focus {
  outline: none; 
}

/* ¡BIEN! Reemplazar por un estilo personalizado */
a:focus, button:focus, input:focus {
  outline: 2px solid #0056b3; /* Usar un color con buen contraste */
  outline-offset: 2px; /* Separar el contorno del elemento */
}
```

## 3. Controlando el Flujo del Foco

Solo los elementos interactivos deben recibir foco.

### `tabindex`

El atributo `tabindex` controla si un elemento puede recibir foco y en qué orden.

| Valor | Descripción | Uso |
| :--- | :--- | :--- |
| **`tabindex="0"`** | El elemento se añade al orden de tabulación natural (del DOM). | Útil para hacer que un elemento **no interactivo** (`<div>`, `<span>`) sea focuseable (ej. si le hemos añadido un evento `onclick` y lo hemos convertido en un componente interactivo). |
| **`tabindex="-1"`** | El elemento es *saltado* por el `Tab`, pero puede recibir foco mediante JavaScript (ej. `.focus()`). | Útil para gestionar el foco en modales o mensajes de error, llevando al usuario directamente al punto necesario. |
| **`tabindex="1+"`** | (Mayor de 0) El elemento entra en un orden de tabulación manual que **anula el orden del DOM**. | **EVITAR A TODA COSTA.** Genera confusión y hace el código insostenible. Que sea el HTML quien defina el orden. |

### Enlaces de Salto (`Skip Links`)

Un usuario de teclado tiene que pulsar `Tab` muchas veces para pasar por todos los elementos de navegación (menús, banners) hasta llegar al contenido principal.

Un **Skip Link** es un enlace oculto al inicio de la página que, al pulsarlo, lleva el foco directamente al `<main>`.

1.  El enlace es visible solo cuando recibe el foco (usando `:focus`).
2.  El destino del enlace es un ID del elemento `<main>` (`<main id="main-content">`).

```html
<body>
  <a href="#main-content" class="skip-link">Saltar al contenido principal</a>

  <header>
    <nav>...</nav>
  </header>

  <main id="main-content">...</main>
</body>
```

```css
/* Estilo del Skip Link */
.skip-link {
  position: absolute;
  top: -40px; /* Oculto fuera de la pantalla */
  left: 0;
  padding: 8px;
  background-color: #fff;
  z-index: 1000;
  transition: top 0.3s;
}

.skip-link:focus {
  top: 0; /* Aparece solo al recibir foco */
}
```

## Recursos

* **[Guía de Navegación por Teclado (MDN)](https://developer.mozilla.org/es/docs/Web/Accessibility/Guides/Understanding_WCAG/Keyboard)**: Documentación exhaustiva sobre los principios del teclado.
* **[Skip Link Design Pattern](https://www.w3.org/WAI/test-evaluate/easy-checks/skip-link/)**: La mejor explicación del patrón de enlaces de salto.

---

[◀ Volver: Semántica](./01-semantica-y-estructura.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: WAI-ARIA ▶](./03-wai-aria.md)
