# Flujos de Caracteres (Archivos de Texto)

## 1. Streams o Flujos
Java ve los datos como un "chorro" de información llamado **Stream**. 
* Si los datos son texto legible (letras, números), usamos **Character Streams** (`Reader` y `Writer`).
* Trabajan con el estándar Unicode (2 bytes por carácter).



---

## 2. Escritura de Texto: `FileWriter` y `BufferedWriter`
Para escribir de forma eficiente, no escribimos carácter por carácter en el disco (es muy lento). Usamos un **Buffer** (una zona de memoria temporal) que acumula texto y lo suelta de golpe.

### El patrón decorador
"Envolvemos" un escritor simple dentro de uno con buffer:
```java
import java.io.BufferedWriter;
import java.io.FileWriter;
import java.io.IOException;

try (BufferedWriter bw = new BufferedWriter(new FileWriter("notas.txt"))) {
    bw.write("Línea 1: Aprendiendo Ficheros.");
    bw.newLine(); // Salto de línea automático
    bw.write("Línea 2: Java es potente.");
} catch (IOException e) {
    System.err.println("Error al escribir: " + e.getMessage());
}
```

---

## 3. Lectura de Texto: `FileReader` y `BufferedReader`
Para leer, el proceso es idéntico. `BufferedReader` nos permite usar el método estrella: `readLine()`, que lee una línea completa hasta encontrar un salto de línea.

```java
import java.io.BufferedReader;
import java.io.FileReader;
import java.io.IOException;

try (BufferedReader br = new BufferedReader(new FileReader("notas.txt"))) {
    String linea;
    while ((linea = br.readLine()) != null) {
        System.out.println("Leído: " + linea);
    }
} catch (IOException e) {
    System.err.println("Error al leer: " + e.getMessage());
}
```

---

## 4. Try-with-resources
Habrás notado el `try (...)`. En ficheros es **obligatorio** cerrar el flujo para liberar el archivo. 
Antiguamente se hacía en un bloque `finally` con `.close()`, pero con **Try-with-resources** (Java 7+), Java cierra el archivo automáticamente al terminar el bloque, incluso si ocurre un error.

---

## 5. Recursos para Profundizar
* [📖 Character Streams (Oracle Docs)](https://docs.oracle.com/javase/tutorial/essential/io/charstreams.html) - Guía oficial sobre Readers y Writers.
* [📖 BufferedReader in Java (W3Schools)](https://www.w3schools.com/java/java_bufferedreader.asp) - Referencia rápida de métodos de lectura.

---
[◀ Volver: Introducción a Ficheros](./02-introduccion-ficheros-clase-file.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Flujos de Bytes ▶](./04-flujos-de-bytes-binarios.md)
