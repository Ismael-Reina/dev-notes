# Métodos y Comparación de Objetos

## 1. Anatomía de un Método
Los métodos definen el **comportamiento** de los objetos. Son bloques de código que realizan una tarea específica y pueden ser llamados varias veces.

Todo método tiene una "firma" (su carné de identidad) que incluye:
1.  **Tipo de retorno:** Qué devuelve el método al terminar (`int`, `String`, o `void` si no devuelve nada).
2.  **Nombre:** Escrito en `camelCase`.
3.  **Parámetros:** Variables que el método necesita recibir para trabajar (van entre paréntesis).

```java
public class Calculadora {
    
    // Método que recibe dos parámetros y DEVUELVE un int
    public int sumar(int a, int b) {
        int resultado = a + b;
        return resultado; // La palabra clave 'return' expulsa el valor
    }

    // Método que no devuelve nada (void)
    public void saludar(String nombre) {
        System.out.println("Hola, " + nombre);
    }
}
```

---

## 2. Métodos Estáticos (`static`) vs De Instancia
Esta es una diferencia crucial en Java.

### Métodos de Instancia (Normales)
Pertenecen al **objeto**. Necesitas crear un objeto con `new` para poder usarlos, porque operan sobre los datos concretos de ese objeto.
* *Ejemplo:* `miCoche.acelerar()` (Acelera ese coche en concreto).

### Métodos Estáticos (`static`)
Pertenecen a la **Clase**. No necesitas crear ningún objeto para usarlos. Se llaman usando el nombre de la clase directamente. Suelen ser utilidades o funciones genéricas.
* *Ejemplo:* `Math.random()` o `Math.max(5, 10)`. No necesitas hacer `new Math()`.

```java
public class Utilidades {
    public static double calcularIVA(double precio) {
        return precio * 0.21;
    }
}

// Uso desde el Main (sin instanciar):
double iva = Utilidades.calcularIVA(100.0);
```

---

## 3. Clases Envoltorio (Wrappers)
Java tiene 8 tipos primitivos (`int`, `double`, `boolean`...). **El problema es que los primitivos NO son objetos**, y a veces Java requiere que todo sea un objeto (por ejemplo, en listas o colecciones).

Para solucionarlo, Java proporciona las **Clases Envoltorio (Wrappers)**. Cogen un primitivo y lo "envuelven" en una clase para darle métodos útiles.

* `int` -> `Integer`
* `double` -> `Double`
* `char` -> `Character`
* `boolean` -> `Boolean`

```java
// Uso de primitivo
int numeroNormal = 5;

// Uso de Wrapper (Autoboxing)
Integer numeroObjeto = 5; 
// Ahora tenemos métodos útiles:
String texto = numeroObjeto.toString(); 
int maximo = Integer.MAX_VALUE; // Constante con el int más grande posible
```

---

## 4. Los Métodos Fundamentales: `equals` y `toString`
Todas las clases en Java heredan (por defecto) de una superclase maestra llamada `Object`. Esto significa que todos tus objetos ya vienen con ciertos métodos de fábrica. Los dos más importantes son:

### A. Comparación de Objetos: `equals()`
Nunca uses `==` para comparar el contenido de dos objetos (como los `String`). El operador `==` solo comprueba si **apuntan al mismo espacio en memoria** (si son el mismo mando a distancia).

Para saber si dos objetos tienen **el mismo contenido**, debes usar (y a veces sobreescribir) el método `.equals()`.

```java
String s1 = new String("Hola");
String s2 = new String("Hola");

System.out.println(s1 == s2);      // FALSE (Están en posiciones de memoria distintas)
System.out.println(s1.equals(s2)); // TRUE (Su contenido es idéntico)
```

### B. Representación Textual: `toString()`
Si intentas imprimir un objeto directamente (`System.out.println(miCoche)`), Java imprimirá algo feo como `Coche@15db9742` (su dirección en memoria). 

Para que imprima algo legible, debes sobreescribir el método `toString()` dentro de tu clase.

```java
public class Coche {
    String marca = "Ford";
    String color = "Rojo";

    // Sobreescribimos el comportamiento por defecto
    @Override
    public String toString() {
        return "Coche de marca " + marca + " y color " + color;
    }
}
```

---

## 5. Recursos para Profundizar
* [📖 Java String equals() Method (W3Schools)](https://www.w3schools.com/java/ref_string_equals.asp) - Ejemplos rápidos de comparación.

---
[◀ Volver: Uso de Objetos](./09-uso-objetos.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Bibliotecas y Consola ▶](./11-bibliotecas-y-consola.md)
