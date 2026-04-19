# Introducción a Colecciones y Genéricos

## 1. ¿Por qué colecciones dinámicas?
Hasta ahora, para guardar varios datos usábamos arrays (`int[]`). Sin embargo, los arrays tienen dos grandes problemas:
1. **Tamaño fijo:** No puedes añadir el elemento 11 a un array de 10.
2. **Falta de métodos:** No tienen funciones integradas para buscar, borrar o insertar fácilmente.

Las **Colecciones** en Java son estructuras de datos que crecen y decrecen automáticamente según necesites.

---

## 2. Los tipos Genéricos (`<T>`)
Para que las colecciones sean seguras, Java utiliza **Genéricos**. Esto permite especificar qué tipo de objetos vamos a guardar dentro de los "picos" o diamantes `< >`.

```java
// Sin genéricos (Peligroso: acepta cualquier objeto)
ArrayList lista = new ArrayList();

// Con genéricos (Seguro: solo acepta Cadenas)
ArrayList<String> nombres = new ArrayList<>();
```

Si intentas meter un `Integer` en una lista de `<String>`, el compilador te avisará antes de que el programa falle.

---

## 3. Jerarquía de la API de Colecciones
Casi todas las colecciones en Java heredan de una interfaz común llamada `Collection`.



Las tres grandes familias que estudiaremos son:
* **List**: Listas ordenadas que permiten duplicados.
* **Set**: Conjuntos que NO permiten duplicados.
* **Map**: Diccionarios de clave-valor.

---

## 4. Recursos para Profundizar
* [📖 The Collections Framework (Oracle Docs)](https://docs.oracle.com/javase/tutorial/collections/intro/index.html) - Introducción oficial de Oracle.
* [📖 Java Generics (W3Schools)](https://www.w3schools.com/java/java_generics.asp) - Conceptos básicos de los diamantes `<T>`.
* [📖 Baeldung: Guide to Java Collections](https://www.baeldung.com/java-collections) - Un repaso técnico por toda la jerarquía.

---
[◀ Volver: Clases Abstractas e Interfaces](./24-clases-abstractas-e-interfaces.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Listas (ArrayList y LinkedList) ▶](./26-listas-arraylist-y-linkedlist.md)
