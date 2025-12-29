# 06. Accesibilidad Cognitiva e Internacionalización

La accesibilidad no es solo para ciegos o personas con movilidad reducida. También debemos diseñar para la mente humana (con sus limitaciones de atención y memoria) y para usuarios de diferentes culturas e idiomas.

## 1. Accesibilidad Cognitiva

Se centra en hacer que el contenido sea fácil de entender y la interfaz fácil de usar. Beneficia a personas con dislexia, TDAH, autismo, o simplemente a un usuario cansado o estresado.

### Lenguaje Claro y Sencillo
* **Escribe para humanos:** Evita tecnicismos innecesarios. Usa frases cortas y párrafos breves.
* **Estructura predecible:** Mantén la navegación y los botones importantes en el mismo lugar en todas las páginas. La consistencia reduce la carga cognitiva.
* **Sin prisas:** Evita límites de tiempo estrictos (como "Tu sesión caduca en 30 segundos") a menos que sea imprescindible por seguridad.

### Animaciones y Distracciones
El movimiento excesivo puede distraer o incluso causar malestar.
* **Pausar/Detener:** Si tienes un carrusel automático o un vídeo de fondo, el usuario debe tener un control para pausarlo.
* **Respetar preferencias:** Ya vimos `prefers-reduced-motion` en el capítulo 04, pero aquí es vital para la concentración.

## 2. Internacionalización (i18n)

Preparar tu web para funcionar en diferentes idiomas y regiones es una parte clave de la accesibilidad universal.

### El atributo `lang`
Es **obligatorio** declarar el idioma principal de la página en la etiqueta `<html>`.

```html
<html lang="es">
```

* **¿Por qué?** Le dice al lector de pantalla qué motor de voz usar. Si tienes una web en español pero no pones `lang="es"`, un lector configurado en inglés intentará leer tu texto con acento inglés, haciéndolo ininteligible.
* **Cambios de idioma:** Si tienes un párrafo en inglés dentro de una página en español, etiquétalo:
  `<span lang="en">Welcome to our site</span>`.

### Soporte RTL (Right-to-Left)
Idiomas como el árabe o el hebreo se leen de derecha a izquierda. Tu interfaz debe ser capaz de "voltearse".

1.  **Dirección:** Usa el atributo `dir="rtl"` en el `<html>` o en el contenedor específico.
2.  **Propiedades Lógicas de CSS:** Deja de usar `margin-left` o `padding-right`. Estas propiedades son físicas y no cambian con el idioma. Usa las lógicas:

| Propiedad Física (Evitar) | Propiedad Lógica (Recomendada) | Comportamiento |
| :--- | :--- | :--- |
| `margin-left` | **`margin-inline-start`** | Margen izquierdo en LTR, derecho en RTL. |
| `padding-right` | **`padding-inline-end`** | Padding derecho en LTR, izquierdo en RTL. |
| `text-align: left` | **`text-align: start`** | Alinea al inicio según el idioma. |

## Recursos

* **[W3C Internationalization (i18n)](https://www.w3.org/International/)**: Recursos oficiales sobre cómo diseñar para todo el mundo.
* **[Guía de Lectura Fácil](https://www.plenainclusion.org/publicaciones/buscador/lectura-facil-metodos-de-redaccion-y-evaluacion/)**: Pautas para hacer textos comprensibles (muy útil para administraciones públicas).

---

[◀ Volver: Formularios](./05-formularios-y-componentes.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Herramientas y Testing ▶](./07-herramientas-y-testing.md)
