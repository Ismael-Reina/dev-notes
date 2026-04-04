# Arrays Multidimensionales (Matrices)

## 1. Concepto de Matriz
Un array multidimensional es, en esencia, un **array de arrays**. El caso más común es el de dos dimensiones (2D), conocido como **matriz**, que podemos visualizar como una tabla con filas y columnas.



### Coordenadas
Para acceder a un elemento, necesitamos dos índices:
1.  El primero indica la **fila**.
2.  El segundo indica la **columna**.

---

## 2. Declaración e Instanciación
Usamos un par de corchetes `[]` por cada dimensión que queramos añadir.

```java
// Declaración e instanciación de una matriz de 3 filas y 4 columnas
int[][] matriz = new int[3][4];

// Inicialización directa (rápida)
int[][] tabla = {
    {1, 2, 3}, // Fila 0
    {4, 5, 6}, // Fila 1
    {7, 8, 9}  // Fila 2
};

System.out.println(tabla[1][2]); // Accede a fila 1, columna 2 -> Imprime 6
```

---

## 3. Recorriendo Matrices (Bucles Anidados)
Para procesar todos los elementos de una matriz, necesitamos un bucle dentro de otro: el externo recorre las filas y el interno las columnas de cada fila.

### Uso de `.length` en 2D
* `matriz.length`: Devuelve el número de **filas**.
* `matriz[i].length`: Devuelve el número de **columnas** de esa fila específica.

```java
int[][] datos = new int[3][5];

for (int i = 0; i < datos.length; i++) { // Recorre filas
    for (int j = 0; j < datos[i].length; j++) { // Recorre columnas
        datos[i][j] = i + j;
        System.out.print(datos[i][j] + " ");
    }
    System.out.println(); // Salto de línea al terminar cada fila
}
```

---

## 4. Arrays Irregulares (Jagged Arrays)
En Java, las columnas no tienen por qué medir lo mismo en todas las filas. Podemos crear una matriz donde cada fila tenga un tamaño diferente.

```java
int[][] irregular = new int[3][]; // Definimos 3 filas, pero columnas libres

irregular[0] = new int[2]; // Fila 0 tiene 2 columnas
irregular[1] = new int[5]; // Fila 1 tiene 5 columnas
irregular[2] = new int[1]; // Fila 2 tiene 1 columna
```

---

## 5. Recursos para Profundizar
* [📖 Multidimensional Arrays (Oracle Docs)](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/arrays.html) - Sección oficial que explica los arrays de arrays.
* [📖 Java Multi-Dimensional Arrays (W3Schools)](https://www.w3schools.com/java/java_arrays_multi.asp) - Ejemplos sencillos de matrices y acceso a datos.

---
[◀ Volver: Arrays Unidimensionales](./14-arrays-unidimensionales.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Operaciones con Arrays ▶](./16-operaciones-con-arrays.md)
