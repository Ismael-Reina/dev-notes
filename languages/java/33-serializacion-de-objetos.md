# Serialización de Objetos

## 1. ¿Qué es la Serialización?
Imagina que estás programando un videojuego y el jugador quiere guardar la partida. Tienes un objeto `Jugador` que contiene nivel, salud, inventario, etc. Guardar cada uno de estos datos línea a línea en un archivo de texto sería muy tedioso de programar.

La **Serialización** es el proceso de convertir un objeto Java completo en una secuencia de bytes para poder guardarlo en un archivo o enviarlo por la red. El proceso inverso, recuperar los bytes para reconstruir el objeto original en memoria, se llama **Deserialización**.

---

## 2. La interfaz `Serializable`
Para que Java te permita serializar una clase, esta debe implementar la interfaz `java.io.Serializable`. 
Es una interfaz "marcadora", lo que significa que no tiene métodos. Solo sirve para decirle a la máquina virtual: *"Doy permiso explícito para que este objeto se convierta en bytes"*.

```java
import java.io.Serializable;

// Al implementar Serializable, autorizamos la serialización
public class Jugador implements Serializable {
    private String nombre;
    private int nivel;
    
    // 'transient' indica que este dato se omitirá al guardar en el fichero
    private transient String contraseña; 

    public Jugador(String nombre, int nivel, String contraseña) {
        this.nombre = nombre;
        this.nivel = nivel;
        this.contraseña = contraseña;
    }
    
    @Override
    public String toString() {
        return "Jugador{" + "nombre='" + nombre + "', nivel=" + nivel + "}";
    }
}
```

---

## 3. `ObjectOutputStream` y `ObjectInputStream`
Estas son las clases encargadas de escribir (guardar) y leer (recuperar) objetos enteros.

### A. Guardar un Objeto (Serializar)
```java
import java.io.FileOutputStream;
import java.io.ObjectOutputStream;
import java.io.IOException;

public class GuardarPartida {
    public static void main(String[] args) {
        Jugador j1 = new Jugador("Heroe99", 50, "secreta123");
        
        try (ObjectOutputStream oos = new ObjectOutputStream(new FileOutputStream("partida.dat"))) {
            // Guardamos el objeto completo de una sola vez
            oos.writeObject(j1);
            System.out.println("Partida guardada correctamente.");
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

### B. Cargar un Objeto (Deserializar)
```java
import java.io.FileInputStream;
import java.io.ObjectInputStream;

public class CargarPartida {
    public static void main(String[] args) {
        try (ObjectInputStream ois = new ObjectInputStream(new FileInputStream("partida.dat"))) {
            // Leemos el objeto y hacemos un "casting" al tipo Jugador
            Jugador jugadorCargado = (Jugador) ois.readObject();
            System.out.println("Partida cargada: " + jugadorCargado);
            // Si imprimes el objeto, verás que la 'contraseña' se lee como 'null' (por ser transient)
        } catch (Exception e) {
            System.err.println("Error al cargar la partida: " + e.getMessage());
        }
    }
}
```

---

## 4. Recursos para Profundizar
* [📖 Object Streams (Oracle Docs)](https://docs.oracle.com/javase/tutorial/essential/io/objectstreams.html) - Documentación oficial sobre la lectura y escritura de objetos.
* [📖 Java Serialization (GeeksforGeeks)](https://www.geeksforgeeks.org/serialization-in-java/) - Guía profunda sobre la serialización y el uso de `transient`.
* [📖 The transient keyword (Baeldung)](https://www.baeldung.com/java-transient-keyword) - Por qué y cuándo evitar que ciertas variables se serialicen.

---
[◀ Volver: Flujos de Bytes](./32-flujos-de-bytes-binarios.md) | [🏠 Ir al Índice](./README.md)
