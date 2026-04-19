# Miembros Estáticos y Recursividad

## 1. Atributos Estáticos (Variables de Clase)
En capítulos anteriores vimos los **métodos estáticos** (aquellos que se pueden llamar sin hacer `new`, como `Math.random()`). Ahora veremos los **atributos estáticos**.

Cuando declaramos un atributo normal, cada objeto tiene su propia copia. 
Cuando declaramos un atributo como `static`, **pasa a pertenecer a la Clase**. Todos los objetos creados a partir de esa clase **comparten la misma variable**.

### Caso de uso típico: Un contador global
```java
public class Coche {
    private String marca; // Atributo de instancia (uno por cada coche)
    
    // Atributo ESTÁTICO (compartido por todos los coches)
    public static int contadorCoches = 0; 

    public Coche(String marca) {
        this.marca = marca;
        contadorCoches++; // Cada vez que nace un coche, subimos el contador global
    }
}

// En el main:
Coche c1 = new Coche("Ford");
Coche c2 = new Coche("Audi");

// Se accede a través del nombre de la clase
System.out.println(Coche.contadorCoches); // Imprime 2
```

---

## 2. Constantes Globales (`static final`)
Si combinamos `static` (compartido por todos) con `final` (no se puede modificar), obtenemos una **constante global**. Por convención, se escriben en mayúsculas y separadas por guiones bajos.

```java
public class Matematicas {
    public static final double NUMERO_PI = 3.14159;
}
// Uso: System.out.println(Matematicas.NUMERO_PI);
```

---

## 3. Recursividad
La recursividad es una técnica de programación donde **un método se llama a sí mismo** para resolver un problema dividiéndolo en problemas más pequeños.

### Reglas de la Recursividad
Todo método recursivo DEBE tener:
1.  **Caso Base:** Una condición que detenga la recursión. Si no lo pones, el método se llamará infinitamente hasta colapsar la memoria (el temido error `StackOverflowError`).
2.  **Caso Recursivo:** La parte donde el método se llama a sí mismo modificando los parámetros para acercarse al caso base.

### Ejemplo Clásico: El Factorial
El factorial de 5 (5!) es 5 * 4 * 3 * 2 * 1.
```java
public class Calculadora {
    
    public int factorial(int n) {
        // 1. Caso Base: El factorial de 1 es 1. ¡Aquí paramos!
        if (n == 1) {
            return 1;
        } 
        // 2. Caso Recursivo: n * factorial(n - 1)
        else {
            return n * factorial(n - 1);
        }
    }
}
```

---

## 4. Recursos para Profundizar
* [📖 Understanding Class Members (Oracle Docs)](https://docs.oracle.com/javase/tutorial/java/javaOO/classvars.html) - Explicación oficial de variables y métodos de clase (`static`).
* [📖 Java Recursion (W3Schools)](https://www.w3schools.com/java/java_recursion.asp) - Tutorial rápido con ejemplos como la suma recursiva.
* [📖 Recursion in Java (GeeksforGeeks)](https://www.geeksforgeeks.org/recursion-in-java/) - Análisis detallado y cómo se apilan las llamadas en memoria.

---
[◀ Volver: Métodos Avanzados](./19-metodos-avanzados.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Relaciones y Composición ▶](./21-relaciones-y-composicion.md)
