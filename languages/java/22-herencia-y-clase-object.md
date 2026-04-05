# Herencia y Clase Object

## 1. El Concepto de Herencia ("Es un")
La herencia permite crear una clase nueva (hija) basada en una clase existente (padre). La clase hija hereda todos los atributos y métodos no privados del padre y puede añadir los suyos propios.

* **Superclase (Padre):** Clase general.
* **Subclase (Hija):** Clase especializada que usa la palabra reservada `extends`.

```java
public class Vehiculo {
    protected String matricula; // Visible para las hijas
    public void arrancar() { System.out.println("Vehículo arrancado"); }
}

public class Moto extends Vehiculo {
    private boolean tieneSidecar;
    // Moto ya tiene 'matricula' y 'arrancar()' por herencia
}
```

---

## 2. El Modificador `protected`
Como vimos en la Unidad 5, `protected` es el punto medio entre `public` y `private`.
* Permite que los atributos del padre sean visibles para sus hijos (subclases), pero sigan estando ocultos para el resto de clases externas.

---

## 3. Constructores y la palabra `super`
Los constructores **no se heredan**. Cuando creas una `Moto`, primero debe ejecutarse el constructor de `Vehiculo`.
* Usamos `super()` para llamar al constructor del padre. 
* **Regla:** La llamada a `super()` debe ser la **primera línea** del constructor del hijo.

```java
public class Moto extends Vehiculo {
    public Moto(String matricula, boolean tieneSidecar) {
        super(); // Llamada opcional al constructor vacío del padre
        this.matricula = matricula;
        this.tieneSidecar = tieneSidecar;
    }
}
```

---

## 4. La Clase Object y Jerarquía Única
En Java, **todas** las clases heredan automáticamente de la clase `java.lang.Object` si no especificas otra. Esto garantiza que todos los objetos tengan métodos básicos como `equals()`, `toString()` y `hashCode()`.

**Dato clave:** Java **no permite la herencia múltiple** de clases (una hija no puede tener dos padres). Esto evita ambigüedades de código (el problema del diamante).

---

## 5. Recursos para Profundizar
* [📖 Java Inheritance (W3Schools)](https://www.w3schools.com/java/java_inheritance.asp) - Tutorial básico con ejemplos de "Vehicle" y "Car".
* [📖 Object Class (Oracle Docs)](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/Object.html) - Documentación oficial de la clase raíz de Java.
* [📖 The super Keyword (Oracle Docs)](https://docs.oracle.com/javase/tutorial/java/IandI/super.html) - Uso detallado para acceder a miembros de la superclase.

---
[◀ Volver: Relaciones y Composición](./21-relaciones-y-composicion.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Polimorfismo y Sobrescritura ▶](./23-polimorfismo-y-sobrescritura.md)
