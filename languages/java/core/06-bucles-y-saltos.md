# Estructuras Repetitivas (Bucles) y Saltos

## 1. Conceptos Clave
Antes de ver los bucles, es fundamental entender dos roles que suelen jugar las variables dentro de ellos:

* **Contador:** Variable que se incrementa en una cantidad fija (generalmente 1) en cada iteración. Se usa para saber "cuántas veces" ha pasado algo.
    * *Ejemplo:* `i++`, `vueltas = vueltas + 1`
* **Acumulador:** Variable que suma (o multiplica) valores variables en cada iteración. Se usa para calcular totales.
    * *Ejemplo:* `sumaTotal += precioProducto`

---

## 2. Bucle `while` (Mientras)
Es un bucle **pre-condición**. Evalúa la condición **antes** de ejecutar el bloque.
* Si la condición es falsa al principio, **nunca se ejecuta**.
* Se usa cuando **no sabemos** cuántas veces vamos a repetir algo (ej: "leer hasta que el usuario escriba salir").

```java
int i = 0;
while (i < 5) {
    System.out.println("Vuelta: " + i);
    i++; // ¡IMPORTANTE! Si olvidas esto, tendrás un BUCLE INFINITO
}
```

---

## 3. Bucle `do-while` (Hacer... Mientras)
Es un bucle **post-condición**. Evalúa la condición **después** de ejecutar el bloque.
* Garantiza que el código se ejecuta **al menos una vez**, independientemente de la condición.
* Se usa típicamente para menús ("mostrar menú -> elegir opción -> comprobar si quiere salir").

```java
int numero;
do {
    System.out.println("Introduce un número positivo:");
    numero = leerTeclado();
} while (numero <= 0); // Repetir mientras sea negativo o cero
```

---

## 4. Bucle `for` (Para)
Es la estructura ideal cuando **sabemos de antemano** cuántas repeticiones queremos. Compacta la inicialización, la condición y la actualización en una sola línea.

**Sintaxis:**
`for (inicialización; condición; actualización) { ... }`

```java
// Contar del 0 al 9
for (int i = 0; i < 10; i++) {
    System.out.println("Soy el número " + i);
}

// Recorrer un Array (Versión clásica)
String[] frutas = {"Manzana", "Pera", "Plátano"};
for (int i = 0; i < frutas.length; i++) {
    System.out.println(frutas[i]);
}
```

### Bucle `for-each` (Versión mejorada)
Introducido para recorrer colecciones y arrays de forma más legible y segura (sin manejar índices).
```java
for (String fruta : frutas) {
    System.out.println(fruta);
}
```

---

## 5. Sentencias de Salto (Control de Flujo)
Permiten alterar el flujo normal dentro de un bucle.

### `break` (Romper)
Aborta inmediatamente la ejecución del bucle (o switch) y salta a la primera instrucción después de él.
* *Uso:* "He encontrado lo que buscaba, deja de iterar".

### `continue` (Continuar)
Salta las instrucciones restantes de la vuelta actual y fuerza el inicio de la **siguiente iteración**.
* *Uso:* "Este caso concreto no me interesa, pasa al siguiente".

```java
for (int i = 0; i < 10; i++) {
    if (i == 2) {
        continue; // Se salta el 2 (no imprime nada) y sigue con el 3
    }
    if (i == 5) {
        break;    // Al llegar al 5, el bucle muere por completo
    }
    System.out.println(i);
}
// Salida: 0, 1, 3, 4
```

### Etiquetas (Labels)
Poco usadas, pero existen. Permiten que un `break` o `continue` afecte a un bucle externo anidado, no solo al inmediato.

```java
buclePrincipal: for (int i = 0; i < 5; i++) {
    for (int j = 0; j < 5; j++) {
        if (i == 2 && j == 2) {
            break buclePrincipal; // Rompe AMBOS bucles
        }
    }
}
```

---

## 6. Recursos para Profundizar
* [⚡ Bucle For-Each explicado](https://www.w3schools.com/java/java_foreach_loop.asp) - Cuándo usarlo.

---
[◀ Volver: Ámbito y Selección](./05-ambito-y-seleccion.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Errores y Depuración ▶](./07-errores-y-depuracion.md)
