# Clases Abstractas e Interfaces

## 1. Clases y Métodos Abstractos (`abstract`)
Una **clase abstracta** es un concepto incompleto. Se utiliza como un molde base para otras clases, pero **no se puede instanciar** directamente (no puedes hacer un `new`).

Un **método abstracto** es un método que está declarado pero no implementado (no tiene llaves `{}`). Obliga a las clases hijas a escribir el código de ese método.

```java
public abstract class Figura {
    protected String color;
    
    // Método normal (Heredado por todos)
    public String getColor() { return color; }
    
    // Método abstracto (Obligatorio de implementar en las hijas)
    public abstract double calcularArea(); 
}

public class Cuadrado extends Figura {
    private double lado;
    
    @Override
    public double calcularArea() {
        return lado * lado; // Si no escribimos esto, Java da error de compilación.
    }
}
```

---

## 2. El Modificador `final` (El fin de la herencia)
Es exactamente lo opuesto a `abstract`.
* **Clase `final`:** Nadie puede heredar de ella (ej: `String` es una clase final en Java).
* **Método `final`:** Nadie puede sobrescribirlo con `@Override`.

---

## 3. Interfaces (Contratos Estrictos)
Una Interfaz es una especie de "contrato" 100% abstracto. Define **qué** se debe hacer, pero no **cómo**. En lugar de heredar (`extends`), las interfaces se **implementan** (`implements`).

* Todos sus métodos son `public abstract` por defecto.
* Todos sus atributos son `public static final` (constantes) por defecto.
* **Una clase puede implementar múltiples interfaces** (la forma que tiene Java de simular la herencia múltiple).

```java
public interface Volador {
    void volar(); // Implícitamente public abstract
}

public class Avion implements Volador {
    @Override
    public void volar() {
        System.out.println("Encendiendo motores y despegando...");
    }
}
```

---

## 4. ¿Clase Abstracta o Interfaz?
La pregunta del millón en diseño de software:

| Característica | Clase Abstracta | Interfaz |
| :--- | :--- | :--- |
| **Relación** | "Es un" (Identidad). Ej: Perro es un Animal. | "Sabe hacer / Puede ser" (Habilidad). Ej: Pájaro es Volador. |
| **Herencia** | Simple (Solo 1 padre `extends`). | Múltiple (Varias `implements`). |
| **Atributos** | Puede tener atributos normales (`private`, `protected`). | Solo constantes (`public static final`). |
| **Métodos** | Puede tener métodos con código real. | Por lo general, solo firmas vacías (salvo métodos `default` en Java 8+). |

---

## 5. Recursos para Profundizar
* [📖 Abstract Methods and Classes (Oracle Docs)](https://docs.oracle.com/javase/tutorial/java/IandI/abstract.html) - Guía oficial sobre cuándo usarlas.
* [📖 Interfaces in Java (Oracle Docs)](https://docs.oracle.com/javase/tutorial/java/IandI/createinterface.html) - Implementación de interfaces como APIs.
* [📖 Abstract Class vs Interface (GeeksforGeeks)](https://www.geeksforgeeks.org/difference-between-abstract-class-and-interface-in-java/) - Tabla comparativa exhaustiva.

---
[◀ Volver: Polimorfismo y Sobrescritura](./23-polimorfismo-y-sobrescritura.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Introducción a Colecciones ▶](./25-introduccion-colecciones-y-genericos.md)
