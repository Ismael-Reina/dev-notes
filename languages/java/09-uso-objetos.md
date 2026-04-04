# Uso de Objetos y Ciclo de Vida

## 1. El Ciclo de Vida de un Objeto
Igual que un ser vivo, un objeto en Java pasa por fases:
1.  **Creación:** Se reserva memoria y se inicializan sus datos.
2.  **Uso:** Lo manipulamos a través de sus métodos.
3.  **Destrucción:** Cuando ya no sirve, se libera la memoria automáticamente.

---

## 2. Declaración vs Instanciación
Es el error número 1 al empezar: confundir la variable con el objeto.

### Paso 1: Declaración
Creamos una variable del tipo de la Clase.
```java
Coche miFerrari; 
// Ahora mismo 'miFerrari' no es un coche, es una referencia vacía (null).
// Si intentas usarla -> NullPointerException.
```

### Paso 2: Instanciación (El operador `new`)
Aquí es donde ocurre la magia. `new` pide al sistema operativo memoria para crear el objeto real.
```java
miFerrari = new Coche(); 
// Ahora SÍ existe el objeto en memoria RAM.
```

### Paso 3: Todo junto (Lo habitual)
```java
Coche miFerrari = new Coche();
```

---

## 3. Constructores
¿Qué pasa cuando haces `new Coche()`? Estás llamando a un método especial: el **Constructor**.
Su misión es preparar el objeto (darle valores iniciales) antes de que nadie pueda usarlo.

### Reglas de los Constructores
1.  Se llaman **exactamente igual** que la clase.
2.  **No devuelven nada** (ni siquiera `void`).
3.  Si tú no escribes ninguno, Java crea uno vacío invisible por defecto.

```java
public class Coche {
    String marca;

    // Constructor personalizado
    public Coche(String marcaInicial) {
        this.marca = marcaInicial; // 'this' se refiere al objeto actual
    }
}

// Uso:
Coche c1 = new Coche("Ford"); // Obligatorio pasar la marca al nacer
```

---

## 4. Referencias y Memoria (El Mando a Distancia)
Java no guarda el objeto dentro de la variable.
* La variable `c1` es un **mando a distancia** (referencia).
* El objeto `new Coche()` es la **televisión** (entidad en memoria).

Si haces esto:
```java
Coche c1 = new Coche();
Coche c2 = c1;
```
**NO** has clonado el coche. Tienes **dos mandos a distancia** apuntando a la **misma televisión**. Si cambias el canal con `c2`, cambia para `c1`.

---

## 5. Destrucción: Garbage Collector (El Basurero)
En lenguajes antiguos (C++), tú tenías que crear memoria y **borrarla** manualmente. Si se te olvidaba, el PC se quedaba sin RAM.

En Java, existe el **Garbage Collector (Recolector de Basura)**:
1.  Cuando un objeto se queda sin referencias (nadie apunta a él).
2.  El Garbage Collector pasa, detecta que está "huérfano" y libera la memoria automáticamente.
3.  Tú no tienes que preocuparte de destruir objetos.

---

## 6. Objetos String (Un caso especial)
Aunque `String` es una clase, es tan importante que Java le da "superpoderes".

1.  **Creación rápida:** No necesitas `new`.
    `String nombre = "Pepe";` (Válido y recomendado).
2.  **Inmutabilidad:** Una vez creado un String, **no se puede modificar**.
    * Si haces `texto.toUpperCase()`, el original no cambia; Java crea un String *nuevo* en memoria con las mayúsculas.

---
[◀ Volver: Fundamentos POO](./08-fundamentos-poo.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Métodos y Comparación ▶](./10-metodos-y-comparacion.md)
