# 03. WAI-ARIA (Web Accessibility Initiative - Accessible Rich Internet Applications)

**WAI-ARIA** es un conjunto de atributos HTML especiales (roles, propiedades y estados) que se utilizan para complementar y extender la semántica nativa del HTML.

**El principio fundamental de ARIA es:** Si puedes usar HTML nativo, **NO uses ARIA**. ARIA solo debe usarse cuando los componentes nativos no existen (ej. un *slider* de rango avanzado, un *tooltip* o un *tab* personalizado).

> 💡 **La Primera Regla de ARIA:** Si puedes usar un elemento HTML nativo con la semántica o el comportamiento requerido, en su lugar, **hazlo**.

## 1. Roles ARIA

Un `role` define el **tipo** de elemento que es el componente, si no es obvio. Le dice al lector de pantalla: "Esta `div` no es solo una caja, es un **botón**" o "Esta sección es una **barra de progreso**".

| Role (Función) | Etiqueta nativa equivalente | Uso en ARIA |
| :--- | :--- | :--- |
| `role="button"` | `<button>` | Si construyes un botón con `<div>` (mala práctica, pero a veces inevitable en frameworks). |
| `role="link"` | `<a>` | Si usas un `<span>` como enlace (mala práctica). |
| `role="alert"` | (No existe) | Para mensajes de error o éxito que aparecen dinámicamente y deben ser anunciados inmediatamente por el lector de pantalla. |
| `role="tablist"` | (No existe) | Para el contenedor de un grupo de pestañas. |

## 2. Propiedades ARIA (Attributes)

Las propiedades (prefijo `aria-`) describen la **naturaleza** del elemento.

| Propiedad | Descripción | Ejemplo de Uso |
| :--- | :--- | :--- |
| **`aria-label`** | Proporciona una etiqueta de texto invisible para los usuarios videntes, pero clave para lectores de pantalla. | Útil en botones que solo tienen un icono (ej. `<button aria-label="Cerrar">X</button>`). |
| **`aria-labelledby`** | Usa el texto de otro elemento de la página como etiqueta. | Para formularios complejos, se puede usar el `id` del titular del formulario como su etiqueta. |
| **`aria-describedby`** | Proporciona texto informativo adicional (instrucciones, detalles). | Útil para vincular un campo de formulario con el texto de ayuda o las reglas de validación. |
| **`aria-hidden="true"`** | Oculta un elemento **solo** de los lectores de pantalla (no del CSS). | Para iconos puramente decorativos o texto duplicado. |

## 3. Estados ARIA

Los estados son atributos dinámicos que cambian con el tiempo y describen el **estado actual** del elemento (generalmente se gestionan con JavaScript).

| Estado | Descripción | Ejemplo |
| :--- | :--- | :--- |
| **`aria-expanded`** | Indica si un elemento que se puede expandir (ej. acordeón o menú) está abierto o cerrado. | `aria-expanded="true"` (Abierto) o `"false"` (Cerrado). |
| **`aria-disabled`** | Indica que un elemento está inactivo (deshabilitado). | `aria-disabled="true"`. |
| **`aria-current`** | Indica el elemento actual dentro de un conjunto (ej. la página activa en una paginación). | `<a aria-current="page">4</a>`. |
| **`aria-live`** | Hace que el lector de pantalla anuncie los cambios de contenido sin que el usuario tenga que interactuar. | Se usa en mensajes de error o notificaciones. |

## Estados Nativos vs. ARIA

No uses ARIA si la etiqueta nativa ya tiene la funcionalidad.

| Uso | Opción preferida (Nativa) | Opción a evitar (ARIA) |
| :--- | :--- | :--- |
| **Campo deshabilitado** | `<input disabled>` | `<input aria-disabled="true">` |
| **Campo de solo lectura** | `<input readonly>` | `<input aria-readonly="true">` |
| **Campo requerido** | `<input required>` | `<input aria-required="true">` |

Usar la opción nativa es más robusto y requiere menos código JavaScript.

## Recursos

* **[WAI-ARIA Authoring Practices (W3C)](https://www.w3.org/WAI/ARIA/apg/)**: La guía oficial para implementar patrones de interfaz complejos (menús, pestañas, etc.) de forma accesible.
* **[A11Y Checklist: ARIA](https://www.a11yproject.com/checklist/#aria)**: Casos de uso comunes.

---

[◀ Volver: Navegación y Teclado](./02-navegacion-y-teclado.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Contenido Visual ▶](./04-contenido-visual.md)
