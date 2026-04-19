# Variables, Identificadores y Tipos de Datos

## 1. Identificadores
Son los nombres que damos a nuestras variables, clases y métodos.

### Reglas (Obligatorias)
* No pueden empezar por un número.
* No pueden contener espacios.
* No pueden ser palabras reservadas de Java (`class`, `public`, `if`...).
* **Case Sensitive:** `edad` y `Edad` son variables distintas.

### Convenciones (Buenas Prácticas)
En Java somos muy estrictos con el estilo:
* **CamelCase:** Para variables y métodos (empieza minúscula, luego mayúsculas). Ej: `numeroDeVidas`, `calcularPrecioTotal`.
* **PascalCase:** Para **Clases** e Interfaces (empieza mayúscula). Ej: `HolaMundo`, `UsuarioRegistrado`.
* **SNAKE_CASE (Mayúsculas):** Solo para **CONSTANTES**. Ej: `PI`, `MAX_USERS`.

---

## 2. Tipos de Datos Primitivos
Java es un lenguaje **fuertemente tipado**: cada variable debe tener un tipo declarado y no puede cambiar. Los primitivos son los bloques básicos, almacenan el valor directamente en memoria (pila).

| Tipo | Tamaño | Descripción | Rango / Ejemplo |
| :--- | :--- | :--- | :--- |
| **byte** | 8 bits | Entero muy pequeño | -128 a 127 |
| **short** | 16 bits | Entero pequeño | -32,768 a 32,767 |
| **int** | 32 bits | **El estándar para enteros** | -2,147,483,648 a 2,147,483,647 |
| **long** | 64 bits | Entero gigante | $\pm 9 \times 10^{18}$ (Sufijo `L`. Ej: `9000L`) |
| **float** | 32 bits | Decimal simple | Sufijo `f` (Ej: `3.14f`) |
| **double**| 64 bits | **Estándar para decimales** | Mayor precisión (Ej: `3.14159`) |
| **boolean**| 1 bit* | Lógico | `true` o `false` |
| **char** | 16 bits | Un solo carácter (Unicode)| Comilla simple (Ej: `'A'`) |

*(Nota: `String` NO es un tipo primitivo, es una Clase, por eso va con mayúscula).*

---

## 3. Declaración e Inicialización
```java
// 1. Declaración: Reservamos espacio en memoria
int edad;

// 2. Inicialización: Le damos el primer valor
edad = 18;

// 3. Todo en una línea (Recomendado)
int vidaJugador = 100;
double precio = 19.99;
char letraDNI = 'X';
boolean esAdmin = false;
```

### Constantes (`final`)
Si queremos que una variable no pueda cambiar nunca de valor, usamos `final`.
```java
final double IVA = 0.21;
// IVA = 0.50;  <-- ¡ERROR DE COMPILACIÓN! No se puede reasignar.
```

---

## 4. Inferencia de Tipos (`var`)
Desde Java 10, podemos usar `var` si el compilador puede adivinar el tipo por el valor asignado.
```java
var mensaje = "Hola"; // Java sabe que es String
var contador = 0;     // Java sabe que es int
```
*Úsalo con precaución. Es mejor ser explícito cuando estás aprendiendo.*

---

## 5. Recursos para Profundizar
* [🛠️ Java Primitive Data Types](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/datatypes.html) - Tutorial oficial sobre rangos y valores por defecto.
* [⚡ W3Schools Java Variables](https://www.w3schools.com/java/java_variables.asp) - Ejemplos rápidos y sencillos.

---
[◀ Volver: Estructura y Entorno](./02-estructura-y-entorno.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Operadores y Expresiones ▶](./04-operadores-y-expresiones.md)
