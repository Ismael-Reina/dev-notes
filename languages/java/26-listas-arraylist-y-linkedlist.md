# Listas (ArrayList y LinkedList)

## 1. La Interfaz `List`
Una lista es una colección ordenada donde cada elemento tiene un índice (empezando en 0) y se permiten elementos duplicados.

---

## 2. ArrayList: El Estándar
Es la implementación más utilizada. Por dentro funciona como un array que se clona y crece solo cuando se llena.

* **Ventaja:** Muy rápido para acceder a elementos por su índice (`get(5)`).
* **Desventaja:** Lento si tienes que insertar o borrar elementos en medio de una lista muy grande (porque tiene que desplazar todos los demás).

```java
import java.util.ArrayList;
import java.util.List;

List<String> tareas = new ArrayList<>();
tareas.add("Aprender Java"); // Añadir
tareas.add("Comprar pan");
tareas.remove(1);             // Borrar por índice
String primera = tareas.get(0); // Leer
```

---

## 3. LinkedList: Lista Enlazada
Funciona como una cadena de vagones donde cada elemento conoce al anterior y al siguiente.



* **Ventaja:** Ultra rápido para insertar o borrar elementos en cualquier posición (solo hay que cambiar los "enganches").
* **Desventaja:** Lento para buscar un elemento por índice, porque tiene que recorrer la cadena desde el principio.

---

## 4. Métodos Comunes en Listas
| Método | Acción |
| :--- | :--- |
| `add(E e)` | Añade al final. |
| `add(int i, E e)` | Inserta en una posición específica. |
| `get(int i)` | Devuelve el elemento en esa posición. |
| `set(int i, E e)` | Reemplaza el elemento en esa posición. |
| `remove(int i)` | Elimina el elemento por índice. |
| `size()` | Devuelve el número de elementos (como el `.length`). |
| `contains(Object o)` | Devuelve true si el elemento está en la lista. |
| `clear()` | Vacía la lista por completo. |

---

## 5. Recursos para Profundizar
* [📖 Clase ArrayList (Oracle Docs)](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/ArrayList.html) - Documentación oficial completa.
* [📖 ArrayList vs LinkedList (GeeksforGeeks)](https://www.geeksforgeeks.org/arraylist-vs-linkedlist-java/) - Comparativa de rendimiento y cuándo elegir cada una.
* [📖 Java List Interface (W3Schools)](https://www.w3schools.com/java/java_arraylist.asp) - Guía práctica de uso.

---
[◀ Volver: Introducción a Colecciones](./25-introduccion-colecciones-y-genericos.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Conjuntos y Sets ▶](./27-conjuntos-y-sets.md)
