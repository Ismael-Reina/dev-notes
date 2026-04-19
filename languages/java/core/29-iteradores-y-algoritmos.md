# Iteradores y Algoritmos de Colecciones

## 1. El Problema de Modificar mientras se Recorre
Imagina que estás recorriendo una lista de nombres con un `for-each` y, si encuentras el nombre "Ana", lo quieres borrar. 

```java
List<String> lista = new ArrayList<>(List.of("Pepe", "Ana", "Luis"));

for (String nombre : lista) {
    if (nombre.equals("Ana")) {
        lista.remove(nombre); // ¡ERROR! Esto lanzará ConcurrentModificationException
    }
}
```
Java prohíbe modificar estructuralmente una colección (añadir o borrar) mientras la estás recorriendo con un bucle `for-each`, porque los índices internos se rompen.

---

## 2. La Solución: Interfaz `Iterator`
Para borrar elementos de forma segura durante un recorrido, debemos usar un **Iterador**, que es un objeto especializado en recorrer colecciones paso a paso de forma segura.

```java
import java.util.Iterator;

List<String> lista = new ArrayList<>(List.of("Pepe", "Ana", "Luis"));
Iterator<String> it = lista.iterator();

while (it.hasNext()) { // Mientras queden elementos...
    String nombre = it.next(); // Cogemos el siguiente
    if (nombre.equals("Ana")) {
        it.remove(); // Borrado SEGURO a través del iterador
    }
}
```

---

## 3. La Clase de Utilidad `Collections`
Igual que la clase `Arrays` nos ayudaba con los arrays tradicionales, la clase `java.util.Collections` está llena de algoritmos (métodos estáticos) para manipular colecciones.

```java
import java.util.Collections;
import java.util.ArrayList;
import java.util.List;

List<Integer> numeros = new ArrayList<>(List.of(50, 10, 30));

// 1. Ordenar (De menor a mayor)
Collections.sort(numeros); // Queda: [10, 30, 50]

// 2. Invertir el orden
Collections.reverse(numeros); // Queda: [50, 30, 10]

// 3. Desordenar aleatoriamente (Ideal para juegos de cartas)
Collections.shuffle(numeros); 

// 4. Buscar el Máximo o el Mínimo
int maximo = Collections.max(numeros); // Devuelve 50
```

---

## 4. Recursos para Profundizar
* [📖 The Iterator Interface (Oracle Docs)](https://docs.oracle.com/javase/tutorial/collections/interfaces/collection.html#iterator) - Cómo y cuándo usar iteradores.
* [📖 Collections Class in Java (GeeksforGeeks)](https://www.geeksforgeeks.org/collections-class-in-java/) - Lista de todos los algoritmos disponibles.


---
[◀ Volver: Mapas y Diccionarios](./28-mapas-diccionarios.md) | [🏠 Ir al Índice](./README.md)
