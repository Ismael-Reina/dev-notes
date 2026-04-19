# Ficheros Avanzados: NIO.2 y Acceso Aleatorio

## 1. El problema del Acceso Secuencial
Hasta ahora, hemos utilizado **Flujos (Streams)** para leer o escribir archivos (`FileReader`, `FileInputStream`, etc.). Los flujos tienen una limitación: son **secuenciales**. Si quieres leer la línea 500 de un archivo, tienes que pasar obligatoriamente por las 499 anteriores. Si quieres modificar una palabra a mitad del texto, es casi imposible sin sobrescribir el archivo entero.

---

## 2. Acceso Aleatorio (`RandomAccessFile`)
La clase `RandomAccessFile` (del paquete clásico `java.io`) soluciona este problema. Funciona como un array gigante de bytes almacenado en el disco. 

Posee un **puntero interno** (un cursor) que puedes mover libremente a cualquier posición (byte) del archivo para leer o sobrescribir datos exactamente en ese punto.

### A. Modos de apertura
Al instanciar la clase, debes especificar el modo:
* `"r"`: Solo lectura (Read).
* `"rw"`: Lectura y escritura (Read / Write).

### B. Ejemplo Práctico: Mover el cursor
```java
import java.io.RandomAccessFile;
import java.io.IOException;

public class AccesoAleatorioEjemplo {
    public static void main(String[] args) {
        // Abrimos el archivo en modo Lectura/Escritura
        try (RandomAccessFile raf = new RandomAccessFile("datos.txt", "rw")) {
            
            // 1. Escribimos algo inicial
            raf.writeUTF("Hola Mundo");
            
            // 2. Comprobamos dónde está el cursor (después de escribir)
            System.out.println("Posición actual: " + raf.getFilePointer());
            
            // 3. Movemos el cursor de vuelta al byte 0 (al principio)
            raf.seek(0);
            
            // 4. Sobrescribimos la primera palabra
            raf.writeUTF("Adiós"); 
            
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

> **Nota:** El acceso aleatorio es la base sobre la que se construyen los motores de bases de datos relacionales por debajo para poder actualizar registros concretos sin reescribir tablas enteras.

---

## 3. Introducción a NIO.2 (New I/O)
En Java 7, Oracle se dio cuenta de que la vieja clase `java.io.File` tenía muchas carencias (era lenta, no manejaba bien los enlaces simbólicos y no lanzaba excepciones claras cuando algo fallaba). 

Para solucionarlo, crearon **NIO.2** (`java.nio.file`), una API completamente nueva y mucho más potente para trabajar con el sistema de archivos.

### A. `Path` y `Paths` (El sustituto de `File`)
La interfaz `Path` representa la ruta de un archivo o directorio. Es mucho más versátil que la antigua clase `File`.

```java
import java.nio.file.Path;
import java.nio.file.Paths;

// Crear una ruta (sirve tanto para Windows como para Mac/Linux)
Path ruta = Paths.get("carpeta", "subcarpeta", "archivo.txt");

System.out.println("Nombre del archivo: " + ruta.getFileName());
System.out.println("Ruta absoluta: " + ruta.toAbsolutePath());
System.out.println("Padre: " + ruta.getParent());
```

### B. La clase de utilidad `Files`
La clase `Files` (en plural) contiene métodos estáticos (algoritmos) que nos facilitan la vida enormemente. Tareas que antes requerían 10 líneas de código con `BufferReaders` y bucles `while`, ahora se hacen en **una sola línea**.

```java
import java.nio.file.Files;
import java.nio.file.Path;
import java.nio.file.Paths;
import java.io.IOException;
import java.util.List;

public class NioEjemplo {
    public static void main(String[] args) {
        Path ruta = Paths.get("notas.txt");

        try {
            // 1. Comprobar si existe
            if (Files.notExists(ruta)) {
                Files.createFile(ruta); // Crear archivo vacío
            }

            // 2. Escribir texto (sobrescribe por defecto)
            String contenido = "Aprender NIO.2 es genial.";
            Files.writeString(ruta, contenido);

            // 3. Leer TODO el archivo en una sola línea de código
            String leido = Files.readString(ruta);
            System.out.println("Leído: " + leido);
            
            // Alternativa: Leer todas las líneas como una Lista
            List<String> lineas = Files.readAllLines(ruta);

            // 4. Copiar y Mover archivos fácilmente
            Path destino = Paths.get("copia_notas.txt");
            Files.copy(ruta, destino); // Lanza error si ya existe el destino

        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

---

## 4. Recursos para Profundizar
* [📖 Java NIO.2 File API (Oracle Docs)](https://docs.oracle.com/javase/tutorial/essential/io/fileio.html) - La guía oficial y exhaustiva de Oracle.
* [📖 Clase RandomAccessFile (Oracle Docs)](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/io/RandomAccessFile.html) - La documentación oficial y completa de la clase para acceso aleatorio.
* [📖 Guide to java.nio.file.Path (Baeldung)](https://www.baeldung.com/java-nio-2-path) - Ejemplos prácticos de manipulación de rutas.

---
---
[◀ Volver: Serialización de Objetos](./05-serializacion-de-objetos.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Conectores y Arquitectura JDBC ▶](./07-jdbc-arquitectura-y-conexiones.md)