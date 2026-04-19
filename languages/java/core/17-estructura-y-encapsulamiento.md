# Estructura de Clases y Encapsulamiento

## 1. Diseñando nuestras propias Clases
Hasta ahora hemos utilizado clases creadas por otros (como `String` o `Scanner`). Ahora vamos a crear las nuestras. Una clase es un archivo `.java` que define los **atributos** (datos) y **métodos** (comportamientos) de una entidad.

### Estructura Básica
```java
// Definición de la clase
public class CuentaBancaria {
    
    // 1. Atributos (El estado)
    String titular;
    double saldo;

    // 2. Métodos (El comportamiento)
    public void ingresar(double cantidad) {
        saldo += cantidad;
    }
}
```

---

## 2. Modificadores de Acceso (Visibilidad)
En el ejemplo anterior, cualquier otra clase podría hacer `miCuenta.saldo = -5000;`. Esto es un fallo de seguridad gravísimo. 

Para evitarlo, Java utiliza los **Modificadores de Acceso**, que dictan quién puede ver o modificar un atributo o método:

* **`public`**: Accesible desde cualquier parte de la aplicación (cualquier paquete).
* **`private`**: **Solo** accesible desde dentro de la propia clase. Es el más estricto.
* **`protected`**: Accesible dentro del mismo paquete y en clases hijas (lo veremos en Herencia).
* **`default` (sin palabra clave)**: Accesible solo para clases que estén dentro del mismo paquete.

> **Regla de Oro de la POO:** Los **atributos** deben ser **SIEMPRE `private`** para proteger los datos. Los **métodos** que queramos que otros usen serán `public`.

---

## 3. Encapsulamiento (Getters y Setters)
Si los atributos son privados, ¿cómo leemos o modificamos su valor desde fuera? Usando métodos públicos controlados, conocidos como **Getters** (para leer) y **Setters** (para escribir).

Esta técnica se llama **Encapsulamiento** y nos permite validar los datos antes de guardarlos.

```java
public class CuentaBancaria {
    // 1. Atributos PRIVADOS
    private String titular;
    private double saldo;

    // 2. Getter (Método para LEER el saldo)
    public double getSaldo() {
        return saldo;
    }

    // 3. Setter (Método para MODIFICAR el saldo con validación)
    public void setSaldo(double nuevoSaldo) {
        if (nuevoSaldo >= 0) {
            saldo = nuevoSaldo; // Solo cambia si es un valor positivo
        } else {
            System.out.println("Error: El saldo no puede ser negativo.");
        }
    }
}
```

---

## 4. Recursos para Profundizar
* [📖 Access Control (Oracle Docs)](https://docs.oracle.com/javase/tutorial/java/javaOO/accesscontrol.html) - Tabla oficial con los permisos de cada modificador.
* [📖 Java Encapsulation (W3Schools)](https://www.w3schools.com/java/java_encapsulation.asp) - Ejemplos rápidos sobre por qué usar Getters y Setters.

---
[◀ Volver: Operaciones con Arrays](./16-operaciones-con-arrays.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Constructores y 'this' ▶](./18-constructores-y-this.md)
