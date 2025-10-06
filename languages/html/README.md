# **Guía de Referencia Rápida de HTML**

HTML (HyperText Markup Language) es el lenguaje estándar para crear y estructurar el contenido de las páginas web. Creado por Tim Berners-Lee en 1991, define el significado y la estructura del contenido mediante un sistema de "etiquetas" que el navegador interpreta para mostrar los elementos visuales.

## **Índice**

1. [Conceptos Fundamentales](#1-conceptos-fundamentales)
2. [Estructura Básica de un Documento](#2-estructura-básica-de-un-documento)
3. [Etiquetas de Texto Comunes](#3-etiquetas-de-texto-comunes)
4. [Enlaces e Imágenes](#4-enlaces-e-imágenes)
5. [Listas](#5-listas)
6. [Tablas](#6-tablas)
7. [Contenido Multimedia](#7-contenido-multimedia)
8. [Etiquetas de Agrupamiento](#8-etiquetas-de-agrupamiento)
9. [HTML Semántico](#9-html-semántico)
10. [Formularios](#10-formularios)
11. [Otros Elementos Útiles](#11-otros-elementos-útiles)
12. [Notas Importantes](#12-notas-importantes)
13. [Recursos Adicionales](#13-recursos-adicionales)

## **1. Conceptos Fundamentales**

### **Elementos y Etiquetas**

Un **elemento** es la unidad básica de HTML y generalmente consta de una etiqueta de apertura, contenido y una etiqueta de cierre. La **etiqueta** es la parte que va entre `<` y `>`.

```html
<h1>Esto es un elemento completo</h1>
```

- **Elementos Vacíos**: No tienen etiqueta de cierre ni contenido, como `<img>`, `<br>` o `<hr>`.
- **Elementos Reemplazables**: Su contenido es reemplazado por un objeto externo, como `<img>` o `<video>`.

### **Atributos**

Los atributos proporcionan información adicional sobre un elemento y se especifican en la etiqueta de apertura.

```html
<a href="https://www.ejemplo.com" target="_blank" title="Ir a Ejemplo">Visitar Ejemplo</a>
```

El valor asignado a un atributo debe ir entre **comillas dobles o simples**.
En HTML5 pueden omitirse si el valor no contiene espacios, pero la buena práctica es usarlas siempre para evitar errores.

Los atributos pueden clasificarse en:  
- **Globales**: Se pueden usar en cualquier etiqueta (ej: `id`, `class`, `title`, `hidden`).
- **Específicos**: Solo aplican a ciertos elementos (ej: `href` en `<a>` o `src` en `<img>`).
- **Booleanos**: Su presencia implica un valor `true`. No necesitan un valor asignado (ej: `controls`, `autoplay`, `required`).

### **Comentarios**

Los comentarios permiten dejar notas en el código que no serán visibles en la página.

```html
<!-- Esto es un comentario -->
<p>Este párrafo sí se muestra.</p>
<!-- <p>Este párrafo está comentado y no se verá.</p> -->
```

## **2. Estructura Básica de un Documento**

Todo documento HTML sigue una estructura estándar. La sección `<head>` contiene metadatos y enlaces a recursos, mientras que el `<body>` contiene el contenido visible de la página.

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <title>Título de la Página</title> <!-- Título en la pestaña y buscadores -->
    <!-- Aquí van las etiquetas meta -->
</head>
<body>
    <header>
        <h1>Título Principal de la Página</h1>
    </header>
    <main>
        <p>Aquí va el contenido principal.</p>
    </main>
    <footer>
        <p>© 2024 - Mi Sitio Web</p>
    </footer>
</body>
</html>
```

### **Etiquetas `<meta>` importantes**

| Etiqueta | Descripción |
| :---- | :---- |
| `<meta charset="UTF-8">` | Define la codificación de caracteres universal (UTF-8). |
| `<meta name="viewport" content="width=device-width, initial-scale=1.0">` | Permite diseño adaptable en dispositivos móviles. |
| `<meta name="description" content="Descripción del sitio web">` | Breve descripción del sitio para buscadores y SEO. |
| `<meta name="robots" content="index, follow">` | Indica a los buscadores que indexen y sigan los enlaces de la página. |
| `<meta name="theme-color" content="#09f">` | Define un color para la barra de herramientas del navegador en móviles. |
| `<link rel="icon" href="/img/favicon.ico">` | Especifica el favicon de la página. |
| `<link rel="canonical" href="URL">` | Especifica la URL preferida de una página para evitar contenido duplicado. |
| `<link rel="alternate" href="https://hydra.dev/en" hreflang="en-GB">` | Señala la versión en otro idioma del sitio. |

### **Open Graph (Para Redes Sociales)**

Protocolo para controlar cómo se muestra una vista previa de tu página cuando se comparte en redes sociales.

```html
<meta property="og:title" content="Título para compartir">
<meta property="og:description" content="Descripción para compartir">
<meta property="og:image" content="URL_de_la_imagen_preview.jpg">
<meta property="og:image:alt" content="Descripción de la imagen para accesibilidad">
```

Puedes previsualizar cómo se verá con herramientas como [OpenGraph.xyz](https://www.opengraph.xyz/).

## **3. Etiquetas de Texto Comunes**

- `<h1>` a `<h6>`: Encabezados, del más al menos importante.  
- `<p>`: Párrafo.  
- `<strong>`: Indica importancia fuerte en el texto (negrita por defecto).  
- `<em>`: Aplica énfasis al texto (cursiva por defecto).  
- `<small>`: Para contenido secundario o de menor importancia.  
- `<blockquote>`: Para citas largas o bloques de texto citados.  
- `<br>`: Salto de línea simple.  
- `<hr>`: Línea horizontal o separador temático.  

## **4. Enlaces e Imágenes**

### **Enlaces `<a>`**

```html
<a href="https://www.ejemplo.com" target="_blank" rel="noreferrer">Visita Ejemplo.com</a>
```

- `href`: La URL de destino.
- `download`: Indica al navegador que descargue el recurso enlazado.  
- `target="_blank"`: Abre el enlace en una nueva pestaña.  
- `rel="noopener"`: Evita que la nueva pestaña acceda a la página que la abrió a través de `window.opener`.  
- `rel="noreferrer"`: Impide que se envíe información sobre la página de origen (referer) al sitio de destino.  

En la práctica, `target="_blank"`, `rel="noopener"` y `rel="noreferrer"` se suelen usar juntos:  

```html
<a href="https://ejemplo.com" target="_blank" rel="noopener noreferrer">Abrir enlace seguro</a>
```

#### **Enviar un correo electrónico**

Puedes crear un enlace que abra el cliente de correo predeterminado del usuario con el campo “Para” (y opcionalmente “Asunto” o “Mensaje”) rellenado.

```html
<a href="mailto:contacto@ejemplo.com?subject=Consulta&body=Hola,%20quisiera%20más%20información.">
  Enviar correo
</a>
```

#### **Crear un enlace de WhatsApp**

Puedes crear un enlace que abra una conversación de WhatsApp con un número y un mensaje predefinido.

```html
<!-- Enlace simple -->
<a href="https://wa.me/34600123456">Enviar mensaje a este número</a>

<!-- Enlace con mensaje predefinido -->
<a href="https://wa.me/34600123456?text=Hola,%20quiero%20más%20información">Contactar por WhatsApp</a>
```

### **Imágenes `<img>`**

```html
<img src="/img/mi-foto.jpg" alt="Descripción de la foto" title="Texto al pasar el ratón" loading="lazy">
```

- `src`: Ruta a la imagen.  
- `alt`: Texto alternativo (esencial para accesibilidad y SEO).  
- `title`: Información adicional que aparece al pasar el cursor.  
- `loading="lazy"`: Carga diferida para mejorar rendimiento.  

## **5. Listas**

### **Listas Ordenadas `<ol>`**

```html
<ol start="5" reversed>
  <li value="10">Elemento 1 (empieza en 10)</li>
  <li>Elemento 2 (sigue en 9)</li>
</ol>
```

- `start`: Define el número de inicio de la lista.  
- `reversed`: Numera la lista en orden descendente.  
- `value` (en `<li>`): Fuerza un valor específico para un elemento.  

### **Listas No Ordenadas `<ul>`**

```html
<ul>
  <li>Elemento con viñeta</li>
  <li>Otro elemento</li>
</ul>
```

## **6. Tablas**

Las tablas permiten organizar información en filas y columnas.

| Etiqueta | Descripción |
| :---- | :---- |
| `<table>` | Define la tabla. |
| `<thead>` | Contiene las filas de encabezado (opcional). |
| `<tbody>` | Contiene las filas de datos principales. |
| `<tfoot>` | Contiene las filas de pie de tabla (opcional). |
| `<tr>` | Fila de la tabla. |
| `<th>` | Celda de encabezado (texto en negrita y centrado por defecto). |
| `<td>` | Celda de datos. |

| Atributo | Descripción |
| :---- | :---- |
| `colspan` | Une varias columnas en una celda. |
| `rowspan` | Une varias filas en una celda. |

Por ejemplo:

```html
<table>
  <thead>
    <tr>
      <th>Nombre</th>
      <th>Edad</th>
      <th>Ciudad</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Ana</td>
      <td>25</td>
      <td>Madrid</td>
    </tr>
    <tr>
      <td>Lucas</td>
      <td>30</td>
      <td>Sevilla</td>
    </tr>
  </tbody>
</table>
```

## **7. Contenido Multimedia**

### **Vídeo `<video>`**

El formato recomendado es MP4 (H.264).

```html
<video src="/videos/mi-video.mp4" controls muted autoplay loop poster="/img/preview.jpg"></video>
```

- `controls`: Muestra controles de reproducción.
- `muted`: Silencia el audio por defecto. Es necesario para que `autoplay` funcione en la mayoría de navegadores.  
- `autoplay`: Intenta reproducir el vídeo automáticamente.  
- `loop`: Repite el vídeo en bucle.  
- `poster`: Imagen previa mientras carga el vídeo.  

### **Audio `<audio>`**

Funciona de manera similar a `<video>`, con atributos como `controls`, `autoplay`, `loop`. El formato recomendado es MP3.  

## **8. Etiquetas de Agrupamiento**

- `<div>`: Contenedor genérico de **bloque**. Se usa para agrupar elementos y aplicarles estilos con CSS o manipularlos con JavaScript. No tiene valor semántico.
- `<span>`: Contenedor genérico **en línea**. Se usa para agrupar una parte de un texto o de un elemento en línea, generalmente para aplicarle un estilo específico.

## **9. HTML Semántico**

Usar etiquetas semánticas ayuda a los navegadores y buscadores a entender la estructura del contenido.

- `<header>`: Cabecera de una página o sección.  
- `<footer>`: Pie de página de una página o sección.  
- `<main>`: Contenido principal y único de la página.  
- `<nav>`: Para menús de navegación principal.  
- `<section>`: Agrupa contenido temáticamente relacionado.  
- `<article>`: Para contenido independiente y autocontenido (un post de blog, una noticia).  
- `<aside>`: Contenido complementario o tangencialmente relacionado (una barra lateral).  

### **Atributo `role`**

Sirve para dar un significado semántico explícito a elementos que no lo tienen, o para redefinir el de un elemento existente. Es una herramienta clave para la **accesibilidad**.

```html
<div role="search">
  <!-- Contenido de un widget de búsqueda -->
</div>
```

- **¿Cuándo usarlo?** Úsalo cuando no exista una etiqueta HTML nativa que describa la función de tu elemento. La primera regla de ARIA es: si puedes usar un elemento nativo (`<button>`, `<nav>`), úsalo.
- **¿Con qué etiquetas?** Principalmente con etiquetas genéricas como `<div>` y `<span>` para convertirlas en componentes accesibles (ej: un `<div>` que actúa como un botón o una alerta).
- **Roles comunes**: `presentation` (elimina la semántica), `button`, `search`, `navigation`, `main`, `banner`, `dialog`, `alert`.
- **Recomendación**: Usa `role` con moderación y solo cuando sea necesario. Un mal uso puede empeorar la accesibilidad. [Aquí puedes consultar la lista completa de roles](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Roles).

## **10. Formularios**

### **Estructura**

```html
<form action="/procesar-datos" method="post">
  <fieldset>
    <legend>Datos Personales</legend>

    <label for="nombre">Nombre:</label>
    <input type="text" id="nombre" name="nombre" required>
  </fieldset>
  <button type="submit">Enviar</button>
</form>
```

| Etiqueta | Descripción |
| :---- | :---- |
| `<form>` | Contenedor principal del formulario. |
| `<fieldset>` | Agrupa campos relacionados. |
| `<legend>` | Título para un `<fieldset>`. |
| `<label>` | Etiqueta descriptiva para un campo. El atributo `for` lo asocia con el id del `input`. |
| `<input>` | El campo de entrada de datos. El atributo `type` define su comportamiento (`text`, `email`, `password`, `checkbox`, `file`, etc.). |
| `<textarea>` |Campo de texto multilínea. |
| `<select>` y `<option>` | Lista desplegable. |
| `<button>` | Botón para enviar el formulario o realizar acciones con JavaScript. |

### **Tipos de entrada comunes**
| Tipo | Descripción |
| :---- | :---- |
| `text` | Campo de texto de una línea. |
| `email` | Valida formato de correo. |
| `password` | Oculta los caracteres introducidos. |
| `number` | Campo numérico con controles. |
| `range` | Selector deslizante (mín. / máx.). |
| `date`, `time`, `datetime-local` | Campos para seleccionar fechas y horas. |
| `file` | Permite subir archivos. |
| `color` | Selector de color. |
| `checkbox` | Casilla de verificación. |
| `radio` | Botón de selección única. |
| `hidden` | Campo oculto que no se muestra al usuario. |

### **Atributos útiles**
| Atributo | Descripción |
| :---- | :---- |
| `placeholder` | Texto guía dentro del campo. |
| `required` | Campo obligatorio. |
| `readonly` | Solo lectura. |
| `disabled` | Desactiva el campo. |
| `pattern` | Expresión regular para validación personalizada. |
| `min`, `max`, `step` | Límites y saltos para valores numéricos. |
| `multiple` | Permite seleccionar varios archivos u opciones. |
| `autofocus` | Coloca el foco automáticamente al cargar el formulario. |

### **Autocompletado con `<datalist>`**

Puedes proporcionar una lista de sugerencias a un campo de texto.  
```html
<label for="lenguaje">Elige un lenguaje:</label>
<input list="lenguajes" id="lenguaje" name="lenguaje">
<datalist id="lenguajes">
  <option value="JavaScript">
  <option value="Python">
  <option value="Java">
</datalist>
```

## **11. Otros Elementos Útiles**

- `<iframe>`: Incrusta otra página web dentro de la actual.  
- `<dialog>`: Permite crear ventanas modales o pop-ups nativos. Tiene un buen soporte en navegadores modernos.  
- `<details>` y `<summary>`: Crean un widget de contenido desplegable (acordeón). Son nativamente accesibles.  
- `<figure>` y `<figcaption>`: La forma semántica correcta de agrupar una imagen, diagrama o bloque de código con su pie de foto o leyenda.
```html
<figure>
  <img src="/img/mi-foto.jpg" alt="Descripción de la foto">
  <figcaption>Este es el pie de foto de la imagen.</figcaption>
</figure>
```

## **12. Notas Importantes**

### **User-Agent Stylesheet**

Cada navegador aplica un conjunto de estilos por defecto a los elementos HTML para que tengan una apariencia básica sin necesidad de CSS. Por ejemplo, los `<h1>` son grandes y en negrita, y los enlaces `<a>` son azules y subrayados. A este conjunto de reglas se le llama **User-Agent Stylesheet**.

Puedes inspeccionar estos estilos con las herramientas de desarrollador de tu navegador. Es el motivo por el cual a menudo se usan "resets" o "normalizadores" de CSS al inicio de un proyecto, para anular estas reglas y asegurar una apariencia consistente en todos los navegadores.

## **13. Recursos Adicionales**

- **Documentación de Referencia (Imprescindible):**  
  - [MDN Web Docs (Mozilla)](https://developer.mozilla.org/es/docs/Web/HTML)  
- **Guías y Tutoriales:**  
  - [W3Schools HTML Tutorial](https://www.w3schools.com/html/)  
  - [freeCodeCamp](https://www.freecodecamp.org/)  
- **Validadores y Herramientas:**  
  - [W3C Markup Validation Service](https://validator.w3.org/)  
  - [Can I use...](https://caniuse.com/)  
