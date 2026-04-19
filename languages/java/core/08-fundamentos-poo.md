# Fundamentos de la Programación Orientada a Objetos (POO)

## 1. Cambio de Paradigma
Hasta ahora programábamos de forma **procedural** (instrucciones paso a paso, variables sueltas y funciones).
La **POO (Programación Orientada a Objetos)** propone una forma distinta de pensar: intentar modelar el software basándonos en las cosas del mundo real.

* **Antes (Procedural):** Teníamos datos (`nombre`, `edad`) y funciones (`imprimirDatos()`) separados.
* **Ahora (POO):** Unimos datos y funciones en una sola entidad llamada **Objeto**.

### Beneficios Principales
1.  **Reutilización:** Una vez creada una clase (ej: `Coche`), puedes crear infinitos objetos de ella sin reescribir código.
2.  **Mantenibilidad:** Si falla algo en el "Motor", vas directo a la clase `Motor` a arreglarlo, sin tocar el resto.
3.  **Modularidad:** Divide un problema grande en problemas pequeños (objetos) que interactúan entre sí.

---

## 2. Los 4 Pilares de la POO
Aunque los profundizaremos más adelante, estos son los conceptos teóricos que sustentan Java:

1.  **Encapsulamiento:** Proteger los datos del objeto para que nadie los modifique incorrectamente desde fuera (usando `private`).
2.  **Herencia:** Crear nuevas clases a partir de otras ya existentes (ej: `Moto` hereda de `Vehiculo`), aprovechando su código.
3.  **Polimorfismo:** La capacidad de un objeto de comportarse de diferentes formas según el contexto (ej: el método `mover()` funciona distinto en un `Coche` que en un `Avion`, pero ambos se "mueven").
4.  **Abstracción:** Centrarnos en *qué* hace un objeto y no en *cómo* lo hace por dentro.

---

## 3. Clases y Objetos: La Diferencia Vital
Es la pregunta de examen número 1. Entender esto es entender la POO.

### La Clase (El Molde)
Una **Clase** es una plantilla, un plano o un esquema. Define cómo serán los objetos, pero **no contiene datos concretos** (salvo constantes) ni ocupa memoria por sí misma (conceptualmente).
* *Analogía:* El molde metálico para cortar galletas con forma de estrella.

### El Objeto (La Instancia)
Un **Objeto** es una entidad concreta creada a partir de una clase. Tiene sus propios valores y ocupa espacio en memoria.
* *Analogía:* La galleta de harina y mantequilla que sale del horno. Puedes hacer 100 galletas (objetos) con un solo molde (clase).

| Concepto | Descripción | Ejemplo |
| :--- | :--- | :--- |
| **Clase** | Definición abstracta (Plano) | `Coche` (concepto general) |
| **Objeto** | Instancia concreta (Realidad) | El Ferrari rojo de mi vecino |

---

## 4. Anatomía de una Clase
Una clase se compone de dos tipos de miembros:

### A. Atributos (Propiedades / Campos)
Son las variables dentro de la clase. Representan el **ESTADO** del objeto.
* *Ejemplos para un Coche:* `color`, `marca`, `velocidadActual`, `encendido`.

### B. Métodos (Comportamiento)
Son las funciones dentro de la clase. Representan lo que el objeto **SABE HACER**.
* *Ejemplos para un Coche:* `arrancar()`, `acelerar()`, `frenar()`.

```java
// Definición de la Clase (El molde)
public class Coche {
    // Atributos (Estado)
    String marca;
    String color;
    int velocidad;

    // Métodos (Comportamiento)
    void acelerar() {
        velocidad = velocidad + 10;
    }
}
```

---

## 5. Recursos para Profundizar
* [🎥 Curso Programación Orientada a Objetos (TodoCode)](https://www.youtube.com/playlist?list=PLQxX2eiEaqbwNP20GMMCjRslRq2lOLWlg) - Lista de reproducción completa y muy amena sobre POO en Java (2025).
* [📖 Conceptos POO - Tutorial Oficial Oracle](https://docs.oracle.com/javase/tutorial/java/concepts/index.html) - La "biblia" de Java con definiciones exactas.
* [⚡ Clases y Objetos - W3Schools](https://www.w3schools.com/java/java_classes.asp) - Ejemplos muy visuales.

---
[◀ Volver: Errores y Depuración](./07-errores-y-depuracion.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Uso de Objetos ▶](./09-uso-objetos.md)
