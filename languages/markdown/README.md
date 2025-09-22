# Guía de Referencia Rápida de Markdown

Markdown es un lenguaje de marcado ligero creado en 2004 por John Gruber con el objetivo de permitir a las personas "escribir usando un formato de texto plano fácil de escribir y fácil de leer, para luego convertirlo a HTML estructuralmente válido".

Su simplicidad y versatilidad lo han convertido en un estándar para la escritura de documentación, la toma de apuntes y, especialmente, para la creación de archivos `README.md` en plataformas como GitHub.

---

## Índice

1.  [Encabezados](#1-encabezados)
2.  [Estilos de Texto](#2-estilos-de-texto)
3.  [Listas](#3-listas)
4.  [Enlaces](#4-enlaces)
5.  [Imágenes](#5-imágenes)
6.  [Citas](#6-citas)
7.  [Código](#7-código)
8.  [Líneas Horizontales](#8-líneas-horizontales)
9.  [Tablas](#9-tablas)
10. [Listas de Tareas (Github)](#10-listas-de-tareas-github)
11. [Saltos de Línea](#11-saltos-de-línea)
12. [Recursos Adicionales](#11-recursos-adicionales)

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

Los subelementos se crean con indentación (generalmente 2 o 4 espacios).

### Listas no Ordenadas

Se crean con *, + o -. 

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

### Enlaces en línea

La sintaxis básica, donde el texto visible y la URL se definen en el mismo lugar.

```markdown
[Visita Google](https://www.google.com "Título opcional al pasar el ratón")
```

### Enlaces por referencia

Son útiles para mantener el texto limpio, definiendo las URLs al final del documento.

```markdown
Este es un [enlace a GitHub][github-ref] y este otro a [Wikipedia][wiki-ref].

[github-ref]: [https://github.com/](https://github.com/)
[wiki-ref]: [https://www.wikipedia.org/](https://www.wikipedia.org/) "La enciclopedia libre"
```

### Anclas (enlaces internos)

Sirven para navegar a otras secciones del mismo documento. Se enlaza a un encabezado usando #. El ID del ancla se genera automáticamente a partir del texto del encabezado (en minúsculas y cambiando espacios por guiones -).

```markdown
[Ir a la sección de Estilos de Texto](#2-estilos-de-texto)
```

## 5 Imágenes

Similar a los enlaces, pero con una exclamación ! al principio. El texto entre corchetes es el texto alternativo.

```markdown
![Logo de Markdown](https://markdown-guide.imgix.net/asset/icon.svg)
![Logo de mi proyecto](./img/mi-logo.png)
```

## 6 Citas

Se crean con >. Se pueden anidar usando >>.

```markdown
> "Lo único que podemos decidir es qué hacer con el tiempo que se nos ha dado."
> > - Gandalf
```

El bloque de código anterior se renderizaría así:

> "Lo único que podemos decidir es qué hacer con el tiempo que se nos ha dado."
> > - Gandalf

## 7 Código

### Código en Línea

Se envuelve entre acentos graves ` y se usa para resaltar pequeños fragmentos de código, comandos o nombres de teclas.

```markdown
Para instalar una dependencia en Node.js, usa el comando `npm install nombre-paquete`.
```

### Bloques de Código

Se envuelven en tres acentos graves ```. Puedes especificar el lenguaje para que se coloree la sintaxis.

``````javascript
```javascript
function helloWorld() {
  console.log("Wake up, Neo...");
}
```
``````

Para escapar los acentos graves (backticks) deben envolverse en un bloque con un número mayor de acentos.

## 8 Líneas Horizontales

Para crear un separador temático, se usan tres o más guiones, asteriscos o guiones bajos en una línea. No hay ninguna diferencia funcional entre ellos.

```markdown
---
***
___
```

## 9 Tablas

Requieren una línea de encabezado, una línea que separe el encabezado del contenido y las filas de datos.   Las celdas se separan con |.  Los dos puntos (:) en la línea separadora definen la alineación del texto en esa columna.

```markdown
| Encabezado 1 | Encabezado 2 | Encabezado 3 |
| :----------- | :----------: | -----------: |
| Alineado a la izquierda | Centrado     | Alineado a la derecha |
| Contenido    | Contenido    | Contenido    |
```

La tabla anterior se renderizaría así:

| Encabezado 1 | Encabezado 2 | Encabezado 3 |
| :----------- | :----------: | -----------: |
| Alineado a la izquierda | Centrado     | Alineado a la derecha |
| Contenido    | Contenido    | Contenido    |

## 10 Listas de Tareas (Github)

Forman parte de GitHub Flavored Markdown (GFM). Puede que no funcionen en todos los editores.

```markdown
- [x] Tarea completada
- [ ] Tarea pendiente
- [ ] Otra tarea por hacer
```

El bloque de código anterior se renderizaría así:

- [x] Tarea completada
- [ ] Tarea pendiente
- [ ] Otra tarea por hacer

## 11 Saltos de Línea

Por defecto, Markdown ignora los saltos de línea simples. Para que el texto fluya, une las líneas consecutivas en un solo párrafo. Para controlar los saltos, tienes dos opciones:

### Párrafos nuevos

Para empezar un párrafo nuevo, simplemente deja una **línea completamente en blanco** entre los textos.

* **Ejemplo:**
    ```markdown
    Línea del primer párrafo.

    Línea del segundo párrafo.
    ```

### Saltos de línea simples

Si solo quieres que el texto baje a la línea siguiente sin crear un párrafo nuevo (un salto `<br>`), añade **dos espacios en blanco** al final de la línea.

* **Ejemplo:**
    ```markdown
    Esta es la primera línea.[espacio][espacio]
    Y esta es la segunda, justo debajo.
    ```
    
## 12 Recursos Adicionales

### Tutoriales Interactivos y Guías

* [TutorialMarkdown.com](https://tutorialmarkdown.com/): Guías completas y directas en español.
* [Markdown Guide](https://www.markdownguide.org/): Una guía muy completa y detallada (en inglés).
* [GitHub Guide: Mastering Markdown](https://docs.github.com/es/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax): La documentación oficial de GitHub sobre su versión de Markdown (GFM).

### Vídeo Tutorial

* [Tutorial de Markdown por MoureDev](https://youtu.be/77Ggk1uzO2A): Un excelente recorrido en vídeo por la sintaxis de Markdown.

### Editores Online

* [Dillinger.io](https://dillinger.io/): Editor online con vista previa en tiempo real.
* [StackEdit.io](https://stackedit.io/): Otro potente editor online que se sincroniza con la nube.

