# 09. Diseño Responsivo (Media Queries)

El **Diseño Responsivo** (*Responsive Design*) es la técnica que nos permite crear sitios web que se ven y funcionan bien en **todos los dispositivos**: móviles, tablets y ordenadores de escritorio.

No se trata de hacer diseños separados, sino de tener **un único diseño flexible** que se adapta.

## 1. El Viewport (Fundamental)

Para que el diseño responsivo funcione, lo primero que *siempre* debes añadir en el `<head>` de tu archivo HTML es la metaetiqueta "viewport".

```html
<head>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  </head>
```

Esta línea le dice al navegador (especialmente al del móvil): "No finjas ser un ordenador. Tu ancho es el ancho del dispositivo, y no hagas zoom al empezar". Sin esto, tus media queries no funcionarán correctamente.

## 2. Media Queries

Las **Media Queries** son la herramienta principal de CSS para el diseño responsivo. Son "condicionales" (`if...then...`) que nos permiten aplicar estilos *solo* si se cumplen ciertas condiciones (como el ancho de la pantalla).

La sintaxis básica es:
`@media (condición) { ...tus estilos aquí... }`

```css
/* Estilos que se aplican SIEMPRE */
body {
  font-family: Arial, sans-serif;
}

/* Estilos que se aplican SOLO si la ventana
   mide 600px de ancho O MENOS */
@media (max-width: 600px) {
  body {
    background-color: lightblue;
  }
}
```

## 3. El enfoque "Mobile-First"

Esta es la **filosofía recomendada** hoy en día. En lugar de diseñar para escritorio y luego "quitar cosas" para el móvil (desktop-first), lo haces al revés:

1.  **Estilos Base:** Escribes primero los estilos más simples para pantallas pequeñas (móviles).
2.  **Media Queries (`min-width`)**: Usas `min-width` (ancho mínimo) para *añadir* estilos o modificar los existentes a medida que la pantalla se hace más grande.

**Ejemplo de "Mobile-First":**

```html
<div class="columna">Columna 1</div>
<div class="columna">Columna 2</div>
```

```css
/* 1. Estilos base (Móvil) */
.columna {
  background-color: #f0f0f0;
  width: 100%; /* Por defecto, ocupan todo el ancho (se apilan) */
  margin-bottom: 10px;
}

/* 2. Estilos para Tablets (y más grandes) */
/* Si la pantalla mide 768px O MÁS... */
@media (min-width: 768px) {
  .contenedor {
    display: flex; /* Empezamos a usar flex */
    gap: 10px;
  }
  .columna {
    width: 50%; /* ...ponemos las columnas al 50% */
    margin-bottom: 0;
  }
}

/* 3. Estilos para Escritorio (y más grandes) */
/* Si la pantalla mide 1024px O MÁS... */
@media (min-width: 1024px) {
  .contenedor {
    max-width: 1200px;
    margin: 0 auto;
  }
  .columna {
    /* Los estilos de 768px se siguen aplicando,
       así que no necesitamos repetir 'display: flex' */
    background-color: lightgreen; /* Solo cambiamos lo que necesitamos */
  }
}
```

## Recursos para Profundizar

* **MDN (Mozilla Developer Network)**:
    * [Introducción a Media Queries](https://developer.mozilla.org/es/docs/Web/CSS/Media_Queries/Using_media_queries)
    * [Conceptos básicos del diseño responsivo](https://developer.mozilla.org/es/docs/Learn/CSS/CSS_layout/Responsive_Design)

---

[◀ Volver: Grid](./08-grid.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Recursos ▶](./10-recursos-herramientas.md)
