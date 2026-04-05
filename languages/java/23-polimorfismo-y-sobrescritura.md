# Polimorfismo y Sobrescritura

## 1. Sobrescritura de Métodos (`@Override`)
Cuando una clase hereda de otra, a veces el comportamiento del padre no le sirve exactamente al hijo. La **sobrescritura** (Overriding) permite a la clase hija redefinir un método del padre.

Se utiliza la anotación `@Override` (es opcional, pero muy recomendada para que el compilador verifique que no te has equivocado al escribir el nombre del método).

```java
public class Animal {
    public void hacerSonido() {
        System.out.println("Hace un sonido genérico.");
    }
}

public class Perro extends Animal {
    @Override
    public void hacerSonido() {
        System.out.println("Guau, guau!");
    }
    
    public void ladrarFuerte() {
        super.hacerSonido(); // Llama al método original del padre
        System.out.println("¡GUAU!");
    }
}
```

---

## 2. Polimorfismo (Múltiples Formas)
El polimorfismo es la capacidad de un objeto para ser referenciado por una variable de su clase **padre**, pero comportándose como su clase **hija** real en tiempo de ejecución (ligadura dinámica).

```java
// El "mando a distancia" es de tipo Animal, pero la "televisión" es un Perro
Animal miMascota = new Perro();

// Al ejecutar, Java mira el OBJETO REAL en memoria (Perro), no la referencia.
miMascota.hacerSonido(); // Imprimirá "Guau, guau!", no el sonido genérico.
```

Esto es increíblemente útil para procesar colecciones de objetos distintos de forma genérica:
```java
Animal[] zoo = new Animal[2];
zoo[0] = new Perro();
zoo[1] = new Gato();

for (Animal a : zoo) {
    a.hacerSonido(); // Cada animal hará su propio sonido automáticamente
}
```

---

## 3. El operador `instanceof` y Casting
A veces, teniendo una referencia genérica (como `Animal`), necesitamos usar un método específico del hijo (ej: `Perro.olfatear()`). Para ello, debemos hacer un **Casting explícito** (transformar la referencia).

Para evitar que el programa crashee con un `ClassCastException` si nos equivocamos de tipo, primero comprobamos con `instanceof`:

```java
Animal desconocido = new Perro();

if (desconocido instanceof Perro) {
    // Casting seguro (downcasting)
    Perro miPerro = (Perro) desconocido; 
    miPerro.olfatear();
} else {
    System.out.println("No es un perro.");
}
```

---

## 4. Recursos para Profundizar
* [📖 Polymorphism in Java (Oracle Docs)](https://docs.oracle.com/javase/tutorial/java/IandI/polymorphism.html) - La explicación oficial de Oracle sobre el polimorfismo.
* [📖 Method Overriding (GeeksforGeeks)](https://www.geeksforgeeks.org/overriding-in-java/) - Reglas técnicas sobre qué se puede y no se puede sobrescribir.
* [📖 The instanceof Keyword (Baeldung)](https://www.baeldung.com/java-instanceof) - Ejemplos prácticos de cómo comprobar tipos en tiempo de ejecución.

---
[◀ Volver: Herencia y Clase Object](./22-herencia-y-clase-object.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Clases Abstractas e Interfaces ▶](./24-clases-abstractas-e-interfaces.md)
