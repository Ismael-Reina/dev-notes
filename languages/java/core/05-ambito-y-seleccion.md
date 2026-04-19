# Ámbito de Variables y Estructuras de Selección

## 1. Estructura Secuencial y Bloques
Por defecto, Java ejecuta las instrucciones una tras otra, de arriba a abajo.
Sin embargo, el código se organiza en **bloques**.

* **Bloque:** Conjunto de sentencias agrupadas entre llaves `{ ... }`.
* Un bloque puede contener otros bloques dentro (anidamiento).

---

## 2. Ámbito (Scope) de una Variable
El ámbito define **dónde** una variable está "viva" y puede ser utilizada.

> **Regla de Oro:** Una variable solo existe dentro del bloque `{}` donde fue declarada (y en los sub-bloques internos). Cuando el bloque se cierra `}`, la variable desaparece de la memoria.

```java
public class EjemploAmbito {
    public static void main(String[] args) {
        int x = 10; // 'x' vive en todo el main
        
        { // Inicio bloque hijo
            int y = 5;
            System.out.println(x + y); // OK: conoce a 'x' (padre) y 'y' (propia)
        } // Fin bloque hijo -> 'y' MUERE aquí
        
        // System.out.println(y); // ¡ERROR! 'y' ya no existe
        System.out.println(x);    // OK: 'x' sigue viva
    }
}
```

**Variable Local:** Es aquella declarada dentro de un método. Debe ser inicializada antes de usarse, Java no le da valor por defecto (a diferencia de los atributos de clase).

---

## 3. Estructuras Condicionales (Selección)
Permiten que el programa tome decisiones y ejecute un código u otro según una condición (`boolean`).

### A. Condicional Simple (`if`)
Ejecuta el bloque solo si la condición es `true`.

```java
if (nota >= 5) {
    System.out.println("Aprobado");
}
```

### B. Condicional Compuesta (`if - else`)
Ofrece una alternativa si la condición no se cumple.

```java
if (nota >= 5) {
    System.out.println("Aprobado");
} else {
    System.out.println("Suspenso");
}
```

### C. Condicionales Anidados (`else if`)
Para evaluar múltiples condiciones en cascada.

```java
if (nota >= 9) {
    System.out.println("Sobresaliente");
} else if (nota >= 7) {
    System.out.println("Notable");
} else if (nota >= 5) {
    System.out.println("Aprobado");
} else {
    System.out.println("Insuficiente");
}
```

> **Buenas Prácticas:**
> * Usa siempre las llaves `{}` aunque solo haya una instrucción. Evita errores futuros.

---

## 4. Selección Múltiple (`switch`)
Útil cuando queremos comparar una **misma variable** contra **múltiples valores concretos** (casos).
* Tipos permitidos: `byte`, `short`, `int`, `char`, `String` y `Enum`.

```java
int dia = 3;

switch (dia) {
    case 1:
        System.out.println("Lunes");
        break; // ¡IMPORTANTE! Si olvidas el break, ejecuta el siguiente caso también.
    case 2:
        System.out.println("Martes");
        break;
    case 3:
        System.out.println("Miércoles");
        break;
    default: // Opcional: Se ejecuta si no coincide con ninguno
        System.out.println("Día inválido");
}
```

### Switch Expressions (Java 14+) - *El modo moderno*
Es más conciso y evita el error de olvidar el `break`. Usa la flecha `->`.

```java
switch (dia) {
    case 1, 2, 3, 4, 5 -> System.out.println("Día laborable");
    case 6, 7 -> System.out.println("Fin de semana");
    default -> System.out.println("Error");
}
```

---

## 5. Recursos para Profundizar
* [🛠️ Java Control Flow Statements](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/flow.html) - Tutorial oficial de Oracle.
* [⚡ If-Else y Switch en W3Schools](https://www.w3schools.com/java/java_conditions.asp) - Ejemplos rápidos.

---
[◀ Volver: Operadores](./04-operadores-y-expresiones.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Bucles y Saltos ▶](./06-bucles-y-saltos.md)
