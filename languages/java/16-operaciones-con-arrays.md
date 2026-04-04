# Operaciones con Arrays y la Clase Arrays

## 1. La Clase de Utilidad `java.util.Arrays`
Manipular arrays a mano (usando bucles `for` para buscar, ordenarlos o imprimirlos) puede ser muy tedioso. Afortunadamente, Java nos proporciona la clase `java.util.Arrays`, que contiene un conjunto de **métodos estáticos** (listos para usar sin hacer `new`) para facilitarnos la vida.

Para usarla, primero debemos importarla en la parte superior de nuestro archivo:
```java
import java.util.Arrays;
```

---

## 2. Operaciones Comunes

### A. Imprimir un Array: `toString()`
Si intentas imprimir un array directamente (`System.out.println(numeros)`), verás algo incomprensible (su dirección de memoria). Para ver su contenido en formato texto, usamos `toString()` para arrays 1D, o `deepToString()` para matrices 2D.

```java
int[] numeros = {10, 20, 30};
System.out.println(Arrays.toString(numeros)); // Imprime: [10, 20, 30]

int[][] matriz = {{1, 2}, {3, 4}};
System.out.println(Arrays.deepToString(matriz)); // Imprime: [[1, 2], [3, 4]]
```

### B. Ordenar un Array: `sort()`
Ordena los elementos en orden ascendente (alfabético para textos, de menor a mayor para números). **Modifica el array original**.

```java
String[] nombres = {"Zack", "Ana", "Luis"};
Arrays.sort(nombres);
System.out.println(Arrays.toString(nombres)); // Imprime: [Ana, Luis, Zack]
```

### C. Rellenar un Array: `fill()`
Asigna un mismo valor a todas las posiciones de un array. Es súper útil para inicializar tableros de juegos o resetear valores.

```java
int[] puntos = new int[5];
Arrays.fill(puntos, 100); 
// El array ahora es: {100, 100, 100, 100, 100}
```

### D. Buscar un elemento: `binarySearch()`
Busca un valor de forma ultra-rápida. 
> **¡Importante!** Para que la búsqueda binaria funcione, **el array debe estar ordenado previamente** con `sort()`. 

Devuelve el índice donde se encuentra el elemento, o un número negativo si no existe.

```java
int[] codigos = {50, 10, 30};
Arrays.sort(codigos); // Ahora es: {10, 30, 50}

int indice = Arrays.binarySearch(codigos, 30); 
System.out.println("Encontrado en la posición: " + indice); // Imprime 1
```

---

## 3. Copia de Arrays: El Problema de la Referencia
Como vimos en la unidad de POO, un array es un objeto. Si haces la asignación `arrayA = arrayB`, **NO** estás copiando los datos; simplemente tienes dos variables apuntando a la misma posición de memoria (el mismo "mando a distancia").

Para hacer un "clon" real e independiente, usamos `copyOf()`:

```java
int[] original = {1, 2, 3};

// Crea un array NUEVO, copia los elementos, y permite cambiar el tamaño final
// Si pides más tamaño (ej. 5), rellena los huecos sobrantes con ceros.
int[] copia = Arrays.copyOf(original, 5); 
System.out.println(Arrays.toString(copia)); // Imprime: [1, 2, 3, 0, 0]
```

---

## 4. Limitaciones de los Arrays
Los arrays clásicos (`[]`) son rapidísimos y consumen muy poca memoria, pero tienen un problema de diseño enorme: **su tamaño es fijo e inmutable**. 

Si creas un array de 10 posiciones y necesitas guardar el elemento 11, la única solución es crear un nuevo array de 11 posiciones y copiar todos los datos del viejo al nuevo.

> **El Futuro:** En unidades posteriores solucionaremos esto utilizando el **API de Colecciones (Collections)**, donde aprenderemos a usar estructuras como `ArrayList`, que son listas dinámicas que crecen y menguan automáticamente según necesitemos.

---

## 5. Recursos para Profundizar
* [📖 Clase Arrays (Documentación Oficial de Oracle)](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/Arrays.html) - La referencia absoluta con todos los métodos de utilidad disponibles.
* [📖 Java Arrays class (GeeksforGeeks)](https://www.geeksforgeeks.org/java/array-class-in-java/) - Ejemplos prácticos y teoría sobre cómo funcionan `sort()`, `binarySearch()` y la copia de arrays.

---
[◀ Volver: Arrays Multidimensionales](./15-arrays-multidimensionales.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Diseño de Clases ▶](./17-diseno-clases.md)
