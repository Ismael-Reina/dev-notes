# Manejo de Excepciones

## 1. ¿Qué es una Excepción?
Una **excepción** es un evento anómalo que ocurre durante la *ejecución* del programa (Runtime) y rompe el flujo normal de las instrucciones.

Si tu programa espera que el usuario introduzca su edad (un número) y el usuario escribe "veinte" (texto), Java no sabe qué hacer, "lanza una excepción" (`InputMismatchException`) y **el programa se cierra de golpe (crashea)**.

El manejo de excepciones nos permite "capturar" ese error, evitar que el programa se cierre, y mostrar un mensaje amigable o tomar una acción alternativa.

---

## 2. La Estructura `try - catch`
Para manejar este problema, envolvemos el código "peligroso" en un bloque de control de errores.

### A. El bloque `try` (Intentar)
Aquí ponemos el código que creemos que puede fallar. Java lo ejecutará con precaución. Si todo va bien, el bloque `catch` se ignora por completo. Si algo falla, el `try` se detiene inmediatamente y le pasa el control al `catch`.

### B. El bloque `catch` (Capturar)
Es la "red de seguridad". Solo se ejecuta si ocurre un error dentro del `try`. Debemos especificar qué tipo de error estamos esperando capturar.

```java
import java.util.Scanner;
import java.util.InputMismatchException;

public class DivisionSegura {
    public static void main(String[] args) {
        Scanner teclado = new Scanner(System.in);
        
        System.out.println("Introduce un número para dividir 100:");
        
        try {
            // Código peligroso: El usuario podría escribir un 0 o una letra
            int numero = teclado.nextInt();
            int resultado = 100 / numero;
            System.out.println("El resultado es: " + resultado);
            
        } catch (ArithmeticException e) {
            // Se ejecuta si el usuario introdujo un 0 (No se puede dividir por cero)
            System.err.println("¡Error! No se puede dividir por cero.");
            
        } catch (InputMismatchException e) {
            // Se ejecuta si el usuario introdujo texto en lugar de un número
            System.err.println("¡Error! Debes introducir un número entero.");
            
        } catch (Exception e) {
            // Captura CUALQUIER otro error imprevisto (Exception es la clase padre)
            System.err.println("Ha ocurrido un error inesperado: " + e.getMessage());
        }
        
        // Gracias al try-catch, el programa no "muere" y llega hasta aquí
        System.out.println("Fin del programa.");
        teclado.close();
    }
}
```

---

## 3. Reglas y Buenas Prácticas
1.  **Orden de los `catch`:** Si vas a poner varios `catch`, siempre debes poner las excepciones más específicas arriba y las más genéricas (`Exception`) al final. Si pones `Exception` primero, capturará todo y los demás `catch` nunca se ejecutarán.
2.  **No silencies errores:** Nunca dejes un bloque `catch` vacío. Al menos imprime el error o un aviso. Si lo dejas vacío, el programa fallará en silencio y será imposible de depurar.
3.  **El objeto Exception (`e`):** La variable `e` que recibe el `catch` contiene información útil. Puedes usar `e.getMessage()` para ver qué falló exactamente, o `e.printStackTrace()` para ver la línea exacta de código que causó el fallo.

---

## 4. Recursos para Profundizar
* [⚡ Java Exceptions (W3Schools)](https://www.w3schools.com/java/java_try_catch.asp) - Ejemplos rápidos y lista de excepciones comunes.

---
[◀ Volver: Bibliotecas y Consola](./11-bibliotecas-y-consola.md) | [🏠 Ir al Índice](./README.md)
