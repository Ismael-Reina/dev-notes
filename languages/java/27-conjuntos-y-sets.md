# Conjuntos (Sets)

## 1. La Interfaz `Set`
Un `Set` (conjunto) es una colección que **NO permite elementos duplicados**. Es el equivalente matemático a un conjunto. Si intentas añadir un elemento que ya existe, la colección simplemente lo ignora y devuelve `false`.



A diferencia de las Listas, la mayoría de los Sets **no tienen índice** (no puedes hacer `get(0)`).

---

## 2. Implementaciones Principales

### A. HashSet (El más rápido)
Usa una tabla Hash internamente. 
* **Ventaja:** Es extremadamente rápido para buscar, añadir o borrar elementos.
* **Desventaja:** **No garantiza ningún orden**. Los elementos se guardan como caen, y al imprimirlos pueden salir en un orden diferente cada vez.

```java
import java.util.HashSet;
import java.util.Set;

Set<String> dnis = new HashSet<>();
dnis.add("12345678A");
dnis.add("87654321B");
dnis.add("12345678A"); // Intentamos añadir un duplicado

System.out.println(dnis.size()); // Imprime 2. El duplicado fue ignorado.
```

### B. TreeSet (El ordenado)
Usa una estructura de árbol internamente.
* **Ventaja:** Mantiene los elementos **ordenados automáticamente** (alfabéticamente o de menor a mayor).
* **Desventaja:** Es más lento que el `HashSet` porque tiene que reordenar el árbol con cada inserción.

---

## 3. La importancia de `equals()` y `hashCode()`
¿Cómo sabe un `HashSet` que dos objetos son "el mismo" para no duplicarlos? 
No usa el operador `==`. Java utiliza el método `hashCode()` para ubicar el objeto en memoria, y luego `equals()` para confirmar que son idénticos. 

> **Regla de oro:** Si creas tu propia clase (ej: `Persona`) y vas a guardarla en un `Set`, **debes sobrescribir** los métodos `equals()` y `hashCode()`, o Java considerará que dos personas con el mismo DNI son distintas por ocupar distinta memoria.

---

## 4. Recursos para Profundizar
* [📖 The Set Interface (Oracle Docs)](https://docs.oracle.com/javase/tutorial/collections/interfaces/set.html) - Guía oficial sobre conjuntos.
* [📖 HashSet in Java (GeeksforGeeks)](https://www.geeksforgeeks.org/hashset-in-java/) - Ejemplos prácticos y teoría de tablas hash.

---
[◀ Volver: Listas (ArrayList y LinkedList)](./26-listas-arraylist-y-linkedlist.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Mapas y Diccionarios ▶](./28-mapas-diccionarios.md)
