# Bibliotecas, Consola y Fechas

## 1. Bibliotecas y Paquetes (`import`)
Java viene con miles de clases ya programadas por otros desarrolladores listas para usar (la API de Java). Para mantener todo organizado, estas clases se agrupan en **paquetes** (que no son más que carpetas lógicas).

* **`java.lang`**: Paquete base (String, Math, System). Se importa automáticamente; no tienes que hacer nada.
* **Otros paquetes (`java.util`, `java.time`)**: Tienes que decirle a tu programa que vas a usarlos mediante la sentencia `import`.

```java
// Importar una clase específica (Recomendado)
import java.util.Scanner;

// Importar TODAS las clases de un paquete (Usa más memoria en compilación, evítalo si puedes)
import java.util.*; 

public class Programa { ... }
```

---

## 2. Entrada y Salida por Consola
La clase `System` (del paquete `java.lang`) es nuestra vía de comunicación directa con el sistema operativo para la terminal.

### A. Salida de datos (Output)
* `System.out.print("Hola");`: Imprime en la consola.
* `System.out.println("Hola");`: Imprime y añade un salto de línea al final.
* `System.err.println("Error");`: Imprime un mensaje de error (muchos IDEs lo muestran en color **rojo**).

### B. Entrada de datos (Input)
Para leer lo que el usuario escribe en el teclado, usamos la clase `Scanner` (del paquete `java.util`).

```java
import java.util.Scanner;

public class Entrada {
    public static void main(String[] args) {
        // 1. Instanciamos el Scanner conectándolo al teclado (System.in)
        Scanner teclado = new Scanner(System.in);
        
        System.out.println("Dime tu edad:");
        // 2. Leemos un número entero
        int edad = teclado.nextInt(); 
        
        System.out.println("Dime tu nombre:");
        // Limpiamos el buffer del intro anterior (truco importante)
        teclado.nextLine(); 
        // 3. Leemos un texto
        String nombre = teclado.nextLine(); 
        
        // 4. Cerramos el escáner para liberar recursos
        teclado.close(); 
    }
}
```

---

## 3. Manipulación de Fechas (API `java.time`)
Antes de Java 8 se usaba la clase `Date`, pero era un dolor de cabeza. Ahora usamos el paquete `java.time`, que es moderno, inmutable y mucho más seguro.

### Clases Principales
1.  **`LocalDate`**: Solo fecha (año, mes, día). Ej: Cumpleaños.
2.  **`LocalTime`**: Solo hora (horas, minutos, segundos). Ej: Hora de la alarma.
3.  **`LocalDateTime`**: Fecha y hora combinadas.

```java
import java.time.LocalDate;
import java.time.LocalDateTime;
import java.time.format.DateTimeFormatter;

public class Fechas {
    public static void main(String[] args) {
        // Obtener la fecha actual
        LocalDate hoy = LocalDate.now();
        
        // Crear una fecha específica
        LocalDate finDeAno = LocalDate.of(2026, 12, 31);
        
        // Formatear la fecha para mostrarla como queramos (dd/MM/yyyy)
        LocalDateTime ahora = LocalDateTime.now();
        DateTimeFormatter formato = DateTimeFormatter.ofPattern("dd/MM/yyyy HH:mm");
        String fechaFormateada = ahora.format(formato);
        
        System.out.println(fechaFormateada); // Ej: 04/04/2026 13:50
    }
}
```

---

## 4. Recursos para Profundizar
* **Documentación Oficial de la API (Oracle):**
  * [📖 Clase `System`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/System.html)
  * [📖 Clase `Scanner`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/Scanner.html)
  * [📖 Clase `LocalDate`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/time/LocalDate.html)
  * [📖 Clase `LocalTime`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/time/LocalTime.html)
  * [📖 Clase `DateTimeFormatter`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/time/format/DateTimeFormatter.html) - Tabla completa de formatos ("dd/MM/yyyy").

---
[◀ Volver: Métodos y Comparación](./10-metodos-y-comparacion.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Excepciones ▶](./12-excepciones.md)
