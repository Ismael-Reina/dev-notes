# Relaciones entre Clases y Composición

## 1. ¿Cómo se relacionan los objetos?
En una aplicación real, las clases no están aisladas. Interactúan entre sí de diferentes formas:

1.  **Relación de Uso (Clientela):** Una clase utiliza a otra de forma puntual (ej: una clase `Tienda` usa un objeto `Ticket` dentro de un método).
2.  **Relación de Composición ("Tiene un"):** Una clase contiene a otra como parte de sus atributos (ej: un `Coche` tiene un `Motor`).
3.  **Relación de Herencia ("Es un"):** Una clase es una versión especializada de otra (ej: un `Turismo` es un `Vehiculo`).



---

## 2. Composición en Profundidad
La composición es la base de la reutilización de código sin usar herencia. Permite crear objetos complejos combinando objetos más simples.

### Implementación y Seguridad
Al usar composición, debemos tener cuidado con la **ocultación**. Si un atributo es un objeto privado, no deberíamos devolver la referencia directa en un Getter, ya que desde fuera podrían modificar el objeto interno sin pasar por nuestra clase.

```java
public class Motor {
    private int caballos;
    public Motor(int caballos) { this.caballos = caballos; }
}

public class Coche {
    private String marca;
    private Motor motor; // Composición: El coche "tiene un" motor

    public Coche(String marca, int caballos) {
        this.marca = marca;
        // El coche crea su propio motor al nacer
        this.motor = new Motor(caballos); 
    }
}
```

---

## 3. Clases Anidadas e Internas
Java permite definir una clase dentro de otra. Esto se hace cuando una clase solo tiene sentido si existe dentro de la clase "padre".
* **Clase interna:** Tiene acceso a todos los miembros (incluso privados) de la clase externa.
* Ayuda a agrupar clases que solo se usan en un lugar, mejorando el encapsulamiento.

---

## 4. Recursos para Profundizar
* [📖 Java Composition (GeeksforGeeks)](https://www.geeksforgeeks.org/composition-in-java/) - Conceptos y ejemplos claros sobre la relación "Has-A".
* [📖 Nested Classes (Oracle Docs)](https://docs.oracle.com/javase/tutorial/java/javaOO/nested.html) - Guía oficial sobre clases internas y anidadas.
* [📖 Baeldung: Composition vs Inheritance](https://www.baeldung.com/java-inheritance-composition) - Análisis sobre cuándo es mejor usar una u otra.

---
[◀ Volver: Miembros Estáticos](./20-miembros-estaticos-y-recursividad.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Herencia y Clase Object ▶](./22-herencia-y-clase-object.md)
