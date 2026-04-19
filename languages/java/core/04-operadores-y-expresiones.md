# Operadores, Expresiones y Comentarios

## 1. Operadores Aritméticos
Se usan para realizar cálculos matemáticos básicos.

| Operador | Descripción | Ejemplo | Resultado (si a=10, b=3) |
| :---: | :--- | :--- | :--- |
| `+` | Suma | `a + b` | `13` |
| `-` | Resta | `a - b` | `7` |
| `*` | Multiplicación | `a * b` | `30` |
| `/` | División | `a / b` | `3` (Ojo: división entera) |
| `%` | Módulo (Resto) | `a % b` | `1` (Lo que sobra de 10/3) |

> **Nota sobre la división:** Si divides dos números enteros (`10 / 3`), Java devuelve un entero (`3`), truncando los decimales. Si quieres decimales, al menos uno debe ser double (`10.0 / 3` -> `3.333`).

---

## 2. Operadores Relacionales y Lógicos
Se utilizan para tomar decisiones (condicionales). Siempre devuelven un `boolean` (`true` o `false`).

### Relacionales (Comparación)
* `>` Mayor que
* `<` Menor que
* `>=` Mayor o igual
* `<=` Menor o igual
* `==` **Igualdad** (Cuidado: no confundir con `=` de asignación)
* `!=` Distinto de

### Lógicos (Para unir condiciones)
| Operador | Nombre | Descripción | Ejemplo |
| :---: | :--- | :--- | :--- |
| `&&` | **AND** (Y) | Devuelve `true` si **ambas** son verdaderas. | `(5>0) && (5<10)` -> `true` |
| `\|\|` | **OR** (O) | Devuelve `true` si **al menos una** es verdadera. | `(5>0) \|\| (5>100)` -> `true` |
| `!` | **NOT** (No) | Invierte el valor (`true` -> `false`). | `!(5>0)` -> `false` |

---

## 3. Operadores Unarios (Incremento/Decremento)
Muy usados en bucles `for` para sumar o restar 1 a una variable.

```java
int x = 5;
x++;    // Equivale a: x = x + 1; (Ahora x vale 6)
x--;    // Equivale a: x = x - 1; (Ahora x vale 5)

// Asignación compuesta (Atajo)
x += 5; // Equivale a: x = x + 5;
x *= 2; // Equivale a: x = x * 2;
```

---

## 4. Conversión de Tipos (Casting)
A veces necesitamos guardar un valor de un tipo en una variable de otro tipo.

### Casting Implícito (Automático)
De un tipo pequeño a uno grande. No hay pérdida de datos, Java lo hace solo.
```java
int numero = 100;
double decimal = numero; // Se convierte a 100.0 automáticamente
```

### Casting Explícito (Manual)
De un tipo grande a uno pequeño. **Puede haber pérdida de datos**, por eso debemos forzarlo poniendo el tipo entre paréntesis.
```java
double precio = 9.99;
int precioEntero = (int) precio; // ¡OJO! Se trunca a 9 (pierdes el .99)
```

---

## 5. Comentarios
El código se lee más veces de las que se escribe. Documentar es vital.

```java
// 1. Comentario de una línea (para explicaciones breves)
int x = 10; 

/* 2. Comentario multilínea 
   (para anular bloques de código grandes
   o explicaciones largas)
*/

/**
 * 3. JavaDoc (Documentación oficial)
 * Se usa antes de clases y métodos. 
 * Permite generar páginas web de ayuda automáticamente.
 * @author Ismael
 * @version 1.0
 */
public class Ejemplo { ... }
```

---

## 6. Recursos para Profundizar
* [⚡ Java Operators (W3Schools)](https://www.w3schools.com/java/java_operators.asp) - Lista completa y ejercicios.
* [📖 Javadoc Guide](https://www.oracle.com/technical-resources/articles/java/javadoc-tool.html) - Cómo escribir documentación profesional.

---
[◀ Volver: Variables y Tipos](./03-variables-y-tipos.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Ámbito y Selección ▶](./05-ambito-y-seleccion.md)

---
[◀ Volver: Variables y Tipos](./03-variables-y-tipos.md) | [🏠 Ir al Índice](./README.md)
