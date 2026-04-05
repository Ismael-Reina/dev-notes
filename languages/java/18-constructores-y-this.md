# Constructores y la palabra clave 'this'

## 1. Recordando los Constructores
El constructor es el método especial que se ejecuta automáticamente cuando hacemos un `new`. Su objetivo principal es inicializar los atributos del objeto con valores válidos desde el momento en que "nace".

* Debe llamarse **exactamente igual** que la clase.
* **No tiene tipo de retorno** (ni siquiera `void`).

---

## 2. El problema del "Shadowing" y la palabra `this`
Es muy común que los parámetros que recibe el constructor se llamen igual que los atributos de la clase (por claridad). Esto genera un conflicto de nombres.

Para que Java sepa diferenciar cuál es cuál, usamos la palabra clave **`this`**.
* `this` significa **"este objeto en concreto"**. 
* `this.nombre` hace referencia al atributo de la clase, mientras que `nombre` (a secas) hace referencia al parámetro del método.

```java
public class Persona {
    private String nombre;
    private int edad;

    // Constructor
    public Persona(String nombre, int edad) {
        // this.nombre (Atributo) = nombre (Parámetro)
        this.nombre = nombre; 
        this.edad = edad;
    }
}
```

---

## 3. Sobrecarga de Constructores (Overloading)
Una clase no tiene por qué tener un solo constructor. Puede tener **varios**, siempre y cuando reciban **diferente número o tipo de parámetros**. 

A esto se le llama **Sobrecarga**, y permite dar flexibilidad a la hora de crear objetos.

```java
public class Persona {
    private String nombre;
    private int edad;
    private String pais;

    // Constructor 1: Recibe todos los datos
    public Persona(String nombre, int edad, String pais) {
        this.nombre = nombre;
        this.edad = edad;
        this.pais = pais;
    }

    // Constructor 2: Solo recibe el nombre (Por defecto es de España y tiene 0 años)
    public Persona(String nombre) {
        this.nombre = nombre;
        this.edad = 0;
        this.pais = "España";
    }

    // Constructor 3: Vacío (Nosotros decidiremos los datos después con los Setters)
    public Persona() {
        this.nombre = "Desconocido";
        this.pais = "Sin especificar";
    }
}

// Uso en el Main:
// Podemos crear personas de 3 formas distintas
Persona p1 = new Persona("Ana", 25, "México");
Persona p2 = new Persona("Luis"); 
Persona p3 = new Persona(); 
```

---

## 4. Recursos para Profundizar
* [📖 Providing Constructors for Your Classes (Oracle Docs)](https://docs.oracle.com/javase/tutorial/java/javaOO/constructors.html) - La guía oficial de Oracle sobre constructores y sobrecarga.
* [📖 Using the this Keyword (Oracle Docs)](https://docs.oracle.com/javase/tutorial/java/javaOO/thiskey.html) - Explicación detallada de cómo y por qué utilizar `this`.
* [📖 Java Constructors (W3Schools)](https://www.w3schools.com/java/java_constructors.asp) - Ejemplos simples de inicialización de atributos.

---
[◀ Volver: Estructura y Encapsulamiento](./17-estructura-y-encapsulamiento.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Métodos Avanzados ▶](./19-metodos-avanzados.md)
