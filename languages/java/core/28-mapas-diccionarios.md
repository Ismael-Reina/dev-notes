# Mapas y Diccionarios

## 1. La Interfaz `Map`
Un `Map` es una colección muy especial porque **no hereda de `Collection`**. Almacena los datos en pares de **Clave-Valor** (Key-Value), como si fuera un diccionario tradicional o un archivo JSON.



* **Clave (Key):** Actúa como el identificador único (ej: el DNI, el código de producto). **No puede haber claves duplicadas**.
* **Valor (Value):** Es el dato asociado a esa clave. Puede haber valores repetidos.

---

## 2. HashMap y TreeMap
Igual que con los Sets, tenemos dos implementaciones principales:

1.  **`HashMap`**: Muy rápido. No garantiza orden de las claves.
2.  **`TreeMap`**: Las claves se ordenan automáticamente (ej: orden alfabético).

### Operaciones Básicas
```java
import java.util.HashMap;
import java.util.Map;

// <Tipo de Clave, Tipo de Valor>
Map<String, Integer> inventario = new HashMap<>();

// 1. Añadir (put)
inventario.put("Manzanas", 50);
inventario.put("Peras", 30);
inventario.put("Manzanas", 60); // Si la clave ya existe, SOBREESCRIBE el valor

// 2. Leer (get)
int cantidad = inventario.get("Peras"); // Devuelve 30

// 3. Comprobar existencia
boolean hayNaranjas = inventario.containsKey("Naranjas"); // Devuelve false

// 4. Borrar (remove)
inventario.remove("Peras");
```

---

## 3. Recorrer un Mapa
Como un mapa tiene dos partes (clave y valor), no podemos recorrerlo con un simple `for-each` directamente. Tenemos tres opciones:

### A. Recorrer solo las claves (`keySet()`)
```java
for (String fruta : inventario.keySet()) {
    System.out.println("Fruta: " + fruta);
}
```

### B. Recorrer solo los valores (`values()`)
```java
for (Integer cant : inventario.values()) {
    System.out.println("Cantidad: " + cant);
}
```

### C. Recorrer Clave y Valor a la vez (`entrySet()`) -> Lo más recomendado
```java
for (Map.Entry<String, Integer> entrada : inventario.entrySet()) {
    System.out.println("Producto: " + entrada.getKey() + " | Stock: " + entrada.getValue());
}
```

---

## 4. Recursos para Profundizar
* [📖 The Map Interface (Oracle Docs)](https://docs.oracle.com/javase/tutorial/collections/interfaces/map.html) - Documentación oficial.
* [📖 HashMap in Java (W3Schools)](https://www.w3schools.com/java/java_hashmap.asp) - Ejemplos rápidos y visuales de mapas.

---
[◀ Volver: Conjuntos y Sets](./27-conjuntos-y-sets.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Iteradores y Algoritmos ▶](./29-iteradores-y-algoritmos.md)
