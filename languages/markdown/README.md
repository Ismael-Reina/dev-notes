# Guía de Referencia Rápida de Markdown

Markdown es un lenguaje de marcado ligero creado por John Gruber con el objetivo de permitir a las personas "escribir usando un formato de texto plano fácil de escribir y fácil de leer, para luego convertirlo a HTML estructuralmente válido".

[cite_start]Su simplicidad y versatilidad lo han convertido en un estándar para la escritura de documentación, la toma de apuntes y, especialmente, para la creación de archivos `README.md` en plataformas como GitHub[cite: 5, 30].

---

## Índice

1.  [Encabezados](#encabezados)
2.  [Estilos de Texto](#estilos-de-texto)
3.  [Listas](#listas)
4.  [Enlaces](#enlaces)
5.  [Imágenes](#imágenes)
6.  [Citas](#citas)
7.  [Código](#código)
8.  [Líneas Horizontales](#líneas-horizontales)
9.  [Tablas](#tablas)
10. [Listas de Tareas](#listas-de-tareas-github)
11. [Recursos Adicionales](#recursos-adicionales)

---

## 1 Encabezados

Se crean con `#`. El número de almohadillas indica el nivel del encabezado (del 1 al 6).

```markdown
# Encabezado Nivel 1 (H1)
## Encabezado Nivel 2 (H2)
### Encabezado Nivel 3 (H3)
#### Encabezado Nivel 4 (H4)
##### Encabezado Nivel 5 (H5)
###### Encabezado Nivel 6 (H6)
```

## 2 Estilos de Texto

### Cursiva

```markdown
*Este texto estará en cursiva*
_Este texto también estará en cursiva_
```

### Negrita

```markdown
**Este texto estará en negrita**
__Este texto también estará en negrita__
```

### Negrita y cursiva

```markdown
***Este texto estará en negrita y cursiva***
**_Este texto también lo estará_**
```

### Tachado

```markdown
~~Este texto estará tachado~~
```

## 3 Listas

### Listas no Ordenadas

Se crean con *, + o -. Los subelementos se crean con indentación (generalmente 2 o 4 espacios).

```markdown
* Elemento 1
* Elemento 2
  * Subelemento 2.1
  * Subelemento 2.2
* Elemento 3
```

### Listas Ordenadas

Se crean con números seguidos de un punto.

```markdown
1. Primer elemento
2. Segundo elemento
   1. Subelemento 2.1
   2. Subelemento 2.2
```

## 4 Enlaces

La sintaxis es `[Texto del enlace](URL "Título opcional")`.
Los enlaces internos, por referencia o anclas se crean automáticamente a partir de los encabezados: `[Texto del Enlace](URL-del-enlace/#nombre-del-ancla)`.

```markdown
[Visita Google](https://www.google.com "Ir a Google")
```

## 5 Imágenes

Similar a los enlaces, pero con una exclamación ! al principio. El texto entre corchetes es el texto alternativo.

```markdown
![Logo de Markdown](https://markdown-guide.imgix.net/asset/icon.svg)
![Logo de mi proyecto](./img/mi-logo.png)
```

## 6 Citas

Se crean con >.

```markdown
> Lo único que podemos decidir es qué hacer con el tiempo que se nos ha dado.
>
> - Gandalf
```

## 7 Código

### Código en Línea

Se envuelve entre acentos graves `. Para escapar los acentos graves (backticks) deben envolverse en un bloque con un número mayor de acentos.

```markdown
Para instalar una dependencia en Node.js, usa el comando `npm install nombre-paquete`.
```

### Bloques de Código

Se envuelven en tres acentos graves ```. Puedes especificar el lenguaje para que se coloree la sintaxis.

``````markdown
```javascript
function helloWorld() {
  console.log("Wake up, Neo...");
}
```
``````

## 8 Líneas Horizontales

Para crear un separador temático, usa tres o más guiones, asteriscos o guiones bajos.

```markdown
---
***
___
```

## 9 Tablas

Requieren una línea de encabezado, una línea que separe el encabezado del contenido y las filas de datos.

```markdown
| Encabezado 1 | Encabezado 2 | Encabezado 3 |
| :----------- | :----------: | -----------: |
| Alineado a la izquierda | Centrado     | Alineado a la derecha |
| Contenido    | Contenido    | Contenido    |
```

*Los dos puntos (:) en la línea separadora definen la alineación de la columna.*

## 10 Listas de Tareas (Github)

Una extensión muy popular en GitHub para crear listas de tareas con casillas de verificación.

```markdown
- [x] Tarea completada
- [ ] Tarea pendiente
- [ ] Otra tarea por hacer
```
- [x] Tarea completada
- [ ] Tarea pendiente
- [ ] Otra tarea por hacer

## 11 Recursos Adicionales

### Tutoriales Interactivos y Guías

* [TutorialMarkdown.com](https://tutorialmarkdown.com/): Guías completas y directas en español.
* [Markdown Guide](https://www.markdownguide.org/): Una guía muy completa y detallada (en inglés).
* [GitHub Guide: Mastering Markdown](https://docs.github.com/es/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax): La documentación oficial de GitHub sobre su versión de Markdown (GFM).

### Vídeo Tutorial

* [Tutorial de Markdown por MoureDev](https://youtu.be/77Ggk1uzO2A): Un excelente recorrido en vídeo por la sintaxis de Markdown.

### Editores Online

* [Dillinger.io](https://dillinger.io/): Editor online con vista previa en tiempo real.
* [StackEdit.io](https://stackedit.io/): Otro potente editor online que se sincroniza con la nube.

