# Flujos de Bytes (Archivos Binarios)

## 1. Archivos de Texto vs Archivos Binarios
En el capítulo anterior vimos los flujos de caracteres (`Reader` y `Writer`), diseñados exclusivamente para texto. Sin embargo, no todos los archivos son texto. Las imágenes, audios, vídeos o ejecutables están compilados en formato binario puro.

Para manipular estos archivos sin corromperlos, debemos leerlos byte a byte utilizando **Flujos de Bytes** (Byte Streams), cuyas clases principales son `InputStream` y `OutputStream`.

---

## 2. Lectura y Escritura: `FileInputStream` y `FileOutputStream`
Estas clases nos permiten conectarnos a un archivo binario para extraer o inyectar bytes.

Al igual que con los archivos de texto, escribir byte a byte directamente en el disco es lento. Por ello, la mejor práctica es "envolver" estos flujos en sus versiones con búfer: `BufferedInputStream` y `BufferedOutputStream`.

### Ejemplo Práctico: Copiar una imagen
Este ejemplo lee una imagen de origen y crea una copia exacta byte a byte en otra ubicación.

```java
import java.io.BufferedInputStream;
import java.io.BufferedOutputStream;
import java.io.FileInputStream;
import java.io.FileOutputStream;
import java.io.IOException;

public class CopiadorArchivos {
    public static void main(String[] args) {
        String origen = "recursos/foto.jpg";
        String destino = "recursos/foto_copia.jpg";

        // Usamos try-with-resources para asegurar el cierre automático
        try (
            BufferedInputStream bis = new BufferedInputStream(new FileInputStream(origen));
            BufferedOutputStream bos = new BufferedOutputStream(new FileOutputStream(destino))
        ) {
            int byteLeido;
            // El método read() devuelve un byte (entre 0 y 255), o -1 si llegó al final
            while ((byteLeido = bis.read()) != -1) {
                bos.write(byteLeido);
            }
            System.out.println("¡Imagen copiada con éxito!");
            
        } catch (IOException e) {
            System.err.println("Error al procesar el archivo: " + e.getMessage());
        }
    }
}
```

---

## 3. Clases Especializadas: `DataInputStream` y `DataOutputStream`
A veces necesitamos guardar datos primitivos puros de Java (un `int`, un `double`, un `boolean`) sin convertirlos a texto. Estas clases nos permiten escribir y leer esos datos primitivos directamente en binario.

```java
import java.io.DataOutputStream;
import java.io.FileOutputStream;
import java.io.IOException;

public class EscribirDatos {
    public static void main(String[] args) {
        try (DataOutputStream dos = new DataOutputStream(new FileOutputStream("datos.bin"))) {
            dos.writeInt(100);       // Escribe 4 bytes
            dos.writeDouble(3.14);   // Escribe 8 bytes
            dos.writeBoolean(true);  // Escribe 1 byte
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

---

## 4. Recursos para Profundizar
* [📖 Byte Streams (Oracle Docs)](https://docs.oracle.com/javase/tutorial/essential/io/bytestreams.html) - Guía oficial sobre la manipulación de flujos de bytes.
* [📖 Data Streams (Oracle Docs)](https://docs.oracle.com/javase/tutorial/essential/io/datastreams.html) - Cómo guardar tipos primitivos en ficheros binarios.
* [📖 FileInputStream in Java (GeeksforGeeks)](https://www.geeksforgeeks.org/fileinputstream-in-java-with-examples/) - Ejemplos prácticos y métodos clave.

---
[◀ Volver: Flujos de Caracteres](./31-flujos-de-caracteres-texto.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Serialización de Objetos ▶](./33-serializacion-de-objetos.md)
