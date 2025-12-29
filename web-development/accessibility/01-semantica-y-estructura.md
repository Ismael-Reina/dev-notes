# 01. Estructura Semántica

La regla número uno de la accesibilidad es: **Usa HTML nativo siempre que sea posible.**

El HTML semántico no es solo "código bonito"; es la información que el navegador entrega a las Tecnologías de Asistencia (lectores de pantalla como NVDA, VoiceOver o TalkBack). Si la estructura HTML es mala, la accesibilidad será imposible, por mucho ARIA o JavaScript que añadas después.

## Etiquetas Semánticas vs. Genéricas

* **Etiquetas Genéricas (`<div>`, `<span>`):** No significan nada. Para un lector de pantalla, son solo cajas vacías. Solo sirven para aplicar CSS.
* **Etiquetas Semánticas (`<header>`, `<nav>`, `<button>`, `<article>`):** Tienen significado ("rol") y comportamiento integrados.

**Ejemplo clásico:** Un `<div>` con un evento `onclick` NO es un botón. Un lector de pantalla no sabrá que es clicable ni se podrá activar con el teclado. Un `<button>`, sí.

## Landmarks (Regiones de la página)

Los usuarios ciegos no ven la página de un vistazo; la "escanean". HTML5 nos permite definir las regiones principales (Landmarks) para que puedan saltar directamente a ellas.

```html
<body>
  <header>
    <nav aria-label="Menú principal">...</nav>
  </header>

  <main>
    <h1>Título de la página</h1>
    
    <article>...</article>
    
    <section>...</section>
  </main>

  <aside>...</aside>

  <footer>...</footer>
</body>
```

## Jerarquía de Encabezados (Headings)

Los encabezados (`h1` - `h6`) son el índice o esqueleto de tu contenido.

* **Un único `<h1>`:** Debe describir de qué trata la página actual (no el sitio web).
* **Sin saltos:** No pases de un `h2` a un `h4` solo porque "se ve mejor". Usa CSS para el tamaño, usa HTML para la estructura.
* **Navegación:** Muchos usuarios navegan saltando de titular en titular (tecla `H` en lectores de pantalla) para encontrar lo que buscan.

## Botones vs. Enlaces (La gran confusión)

Este es el error más común en desarrollo web. Visualmente pueden parecer iguales, pero semánticamente son opuestos:

| Elemento | Etiqueta HTML | Función | Comportamiento Teclado |
| :--- | :--- | :--- | :--- |
| **Enlace** | `<a href="...">` | **Navegar** a otro sitio o a otra parte de la página. | Se activa con `Enter`. |
| **Botón** | `<button>` | **Realizar una acción** (abrir menú, enviar form, guardar). | Se activa con `Enter` y `Espacio`. |

**Regla de oro:** Si cambia la URL, es un `<a>`. Si hace algo en la página, es un `<button>`.

## Elementos HTML potentes (Nativos)

Antes de crear un componente complejo con `<div>` y JavaScript, revisa si HTML ya lo ha inventado. Los elementos nativos ya son accesibles (foco, teclado y lectura) de fábrica:

* **`<dialog>`**: Para modales y popups. Gestiona el foco automáticamente.
* **`<details>` y `<summary>`**: Para acordeones o contenido desplegable "ver más".
* **`<fieldset>` y `<legend>`**: Para agrupar opciones en formularios (vital para radio buttons).

---

[◀ Volver: Índice](./README.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Navegación y Teclado ▶](./02-navegacion-y-teclado.md)
