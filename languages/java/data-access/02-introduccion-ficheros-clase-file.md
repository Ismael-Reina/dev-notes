# Introducción a Ficheros y la Clase File

## 1. El Concepto de Persistencia
Hasta ahora, todos los datos que guardábamos en variables o colecciones desaparecían al cerrar el programa (memoria RAM). La **persistencia** consiste en almacenar esos datos en un soporte no volátil (disco duro, SSD) para poder recuperarlos más tarde.

En Java, esto se gestiona mediante el paquete `java.io` (Input/Output).

---

## 2. La Clase `File`
La clase `File` no sirve para leer el *contenido* de un archivo, sino para gestionar el archivo como objeto del sistema operativo: comprobar si existe, ver su tamaño, crearlo, borrarlo o listar carpetas.



### Operaciones más comunes:
```java
import java.io.File;

File f = new File("datos.txt");

if (f.exists()) {
    System.out.println("Nombre: " + f.getName());
    System.out.println("Ruta: " + f.getAbsolutePath());
    System.out.println("Tamaño: " + f.length() + " bytes");
} else {
    System.out.println("El archivo no existe.");
}
```

### Métodos principales:
* `createNewFile()`: Crea un archivo vacío.
* `mkdir()` / `mkdirs()`: Crea una carpeta o una ruta completa de carpetas.
* `delete()`: Borra el archivo o carpeta.
* `isFile()` / `isDirectory()`: Comprueba qué tipo de elemento es.
* `list()` / `listFiles()`: Devuelve los nombres o archivos dentro de una carpeta.

---

## 3. Rutas Relativas vs Absolutas
* **Absoluta:** La ruta completa desde la raíz (Ej: `C:\Proyectos\Java\datos.txt`). Son peligrosas porque si mueves el proyecto a otro PC, el programa fallará.
* **Relativa:** La ruta respecto a la carpeta del proyecto (Ej: `recursos/datos.txt`). Es la **mejor práctica** para que tu código sea portátil.

---

## 4. Recursos para Profundizar
* [📖 The File Class (Oracle Docs)](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/io/File.html) - Documentación oficial completa.
* [📖 Java File Class (GeeksforGeeks)](https://www.geeksforgeeks.org/file-class-in-java/) - Ejemplos de manipulación de directorios y archivos.

---
[◀ Volver: Introducción a la Persistencia de Datos](./01-introduccion-persistencia.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Flujos de Caracteres ▶](./03-flujos-de-caracteres-texto.md)
