# Métodos Avanzados y Paso de Parámetros

## 1. Sobrecarga de Métodos (Method Overloading)
Igual que podemos tener varios constructores, Java nos permite tener **varios métodos con el mismo nombre** dentro de una misma clase. 

Para que Java no se confunda, la "firma" del método debe ser diferente. Esto significa que **deben recibir diferente número o tipo de parámetros**. El tipo de retorno (`void`, `int`, etc.) NO sirve para diferenciar métodos sobrecargados.

```java
public class Impresora {
    
    // Método 1: Recibe un texto
    public void imprimir(String texto) {
        System.out.println("Imprimiendo texto: " + texto);
    }
    
    // Método 2: Recibe un número (Sobrecarga válida)
    public void imprimir(int numero) {
        System.out.println("Imprimiendo número: " + numero);
    }
    
    // Método 3: Recibe dos números (Sobrecarga válida)
    public void imprimir(int a, int b) {
        System.out.println("Imprimiendo suma: " + (a + b));
    }
}
```

---

## 2. Paso de Parámetros: ¿Valor o Referencia?
Esta es una pregunta clásica de examen y de entrevista técnica. ¿Qué pasa cuando enviamos una variable a un método y ese método la modifica por dentro?

> **Regla fundamental en Java:** En Java, **TODO se pasa por valor** (se pasa una copia). Sin embargo, se comporta de forma distinta si es un tipo primitivo o un objeto.

### A. Tipos Primitivos (Paso por valor puro)
Si pasas un `int`, `double` o `boolean`, se envía una **copia exacta** del valor. Si el método modifica esa copia, la variable original del `main` **NO cambia**.

```java
public void cambiarNumero(int x) {
    x = 99; // Solo modifica la copia local
}

// En el main:
int miNumero = 10;
cambiarNumero(miNumero);
System.out.println(miNumero); // Imprime 10 (El original está intacto)
```

### B. Objetos y Arrays (Paso del valor de la referencia)
Si pasas un objeto (como un Array o un `Coche`), lo que se copia y se envía es el **valor de la referencia** (el "mando a distancia"). 
Como la copia del mando y el mando original apuntan a la **misma televisión** (mismo espacio en memoria), si el método modifica el objeto por dentro, **el original SÍ se ve afectado**.

```java
public void cambiarArray(int[] numeros) {
    numeros[0] = 99; // Modifica el objeto real en la memoria
}

// En el main:
int[] misNumeros = {1, 2, 3};
cambiarArray(misNumeros);
System.out.println(misNumeros[0]); // ¡Imprime 99! (El original fue alterado)
```

---

## 3. Recursos para Profundizar
* [📖 Passing Information to a Method (Oracle Docs)](https://docs.oracle.com/javase/tutorial/java/javaOO/arguments.html) - Explicación oficial sobre el paso de argumentos primitivos y de referencia.
* [📖 Method Overloading in Java (W3Schools)](https://www.w3schools.com/java/java_methods_overloading.asp) - Ejemplos básicos de sobrecarga.
* [📖 Pass by Value vs Pass by Reference (GeeksforGeeks)](https://www.geeksforgeeks.org/g-fact-31-java-is-strictly-pass-by-value/) - Análisis técnico de por qué Java es estrictamente "paso por valor".

---
[◀ Volver: Constructores y 'this'](./18-constructores-y-this.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Miembros Estáticos y Recursividad ▶](./20-miembros-estaticos-y-recursividad.md)
