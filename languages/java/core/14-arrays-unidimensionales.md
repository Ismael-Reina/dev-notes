# Arrays Unidimensionales (Arreglos o Vectores)

## 1. ¿Qué es un Array?
Un array es una estructura de datos que nos permite almacenar **múltiples valores del mismo tipo** en una sola variable. 

Imagina un array como una estantería con casilleros numerados. Todos los casilleros son del mismo tamaño y guardan el mismo tipo de objeto.

### Características fundamentales en Java:
1.  **Tamaño Fijo:** Una vez creado el array con un tamaño específico (ej. 5 posiciones), **no puede crecer ni encoger**.
2.  **Mismo Tipo:** No puedes mezclar `int` con `String` en el mismo array.
3.  **Basado en índice 0:** El primer elemento siempre está en la posición `0`, y el último en la posición `tamaño - 1`.

---

## 2. Declaración e Instanciación
Como los arrays en Java son **objetos**, debemos usar la palabra clave `new` para reservar su espacio en memoria.

```java
// 1. Declaración (Indicamos que será un array con los corchetes [])
int[] edades; 

// 2. Instanciación (Asignamos memoria para 5 números enteros)
edades = new int[5]; 

// TODO EN UNA LÍNEA (Lo más común)
double[] precios = new double[10]; // Array de 10 decimales (índices del 0 al 9)
```

*Nota: Cuando creas un array numérico con `new`, Java rellena todas las posiciones con `0` por defecto. Si es de booleanos, con `false`. Si es de objetos (como `String`), con `null`.*

---

## 3. Inicialización (Asignar Valores)
Podemos dar valores a los elementos uno por uno usando su índice, o inicializar el array completo directamente.

### A. Manualmente (Posición a posición)
```java
int[] numeros = new int[3];
numeros[0] = 10;
numeros[1] = 25;
numeros[2] = 50;

System.out.println(numeros[1]); // Imprime 25
```

### B. Inicialización rápida (Si ya sabemos los valores)
```java
// Java cuenta cuántos elementos hay dentro de las llaves y le da ese tamaño al array
String[] dias = {"Lunes", "Martes", "Miércoles", "Jueves", "Viernes"};
System.out.println(dias[0]); // Imprime "Lunes"
```

---

## 4. La propiedad `length`
Para saber el tamaño de un array usamos su propiedad `.length` (Ojo: **no lleva paréntesis**, a diferencia del `length()` de los Strings, porque es una propiedad o atributo, no un método).

```java
String[] nombres = {"Ana", "Luis", "Marta"};
System.out.println("El array tiene " + nombres.length + " elementos."); // Imprime 3
```

---

## 5. Recorrer Arrays con Bucles
Esta es la operación más común que harás con un array: pasar por todos sus elementos.

### El Bucle `for` clásico
Útil si necesitas saber en qué posición (índice) te encuentras en cada vuelta.
```java
int[] notas = {5, 7, 9, 4};

for (int i = 0; i < notas.length; i++) {
    System.out.println("En la posición " + i + " la nota es " + notas[i]);
}
```

### El Bucle `for-each` (Mejorado)
Si no te importa el índice y solo quieres ver el valor de cada elemento, este bucle es más limpio y evita el clásico error de "salirse de los límites del array" (`ArrayIndexOutOfBoundsException`).
```java
int[] notas = {5, 7, 9, 4};

// Se lee: "Por cada entero 'nota' dentro del array 'notas'..."
for (int nota : notas) {
    System.out.println("La nota es: " + nota);
}
```

---

## 6. Recursos para Profundizar
* [📖 Java Arrays (W3Schools)](https://www.w3schools.com/java/java_arrays.asp) - Tutorial visual muy sencillo sobre la creación y acceso a arrays.
* [📖 Arrays in Java (GeeksforGeeks)](https://www.geeksforgeeks.org/arrays-in-java/) - Guía detallada con teoría sobre cómo Java maneja los arrays en memoria.

---
[◀ Volver: Cadenas de Caracteres](./13-cadenas-de-caracteres.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Arrays Multidimensionales ▶](./15-arrays-multidimensionales.md)
