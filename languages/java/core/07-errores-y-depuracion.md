# Errores y Depuración de Código

## 1. Tipos de Errores
No todos los fallos son iguales. Identificar el tipo de error es el primer paso para solucionarlo.

### A. Errores de Sintaxis (Tiempo de Compilación)
Son los más fáciles de detectar. El código no cumple las reglas del lenguaje (falta un punto y coma, llaves desparejadas, escribir `wile` en vez de `while`).
* **Consecuencia:** El programa **no compila**. El IDE lo marca en rojo inmediatamente.
* **Solución:** Leer el mensaje del IDE y corregir la escritura.

### B. Errores de Ejecución (Runtime Errors / Excepciones)
El código está bien escrito, pero intenta hacer algo imposible durante la ejecución.
* *Ejemplos:* Dividir por cero, acceder a la posición 10 de un array de 5 elementos, leer un archivo que no existe.
* **Consecuencia:** El programa se cierra abruptamente (crash) y lanza una **Excepción** en la consola.

### C. Errores Lógicos (Semánticos)
Son los más peligrosos y difíciles de detectar. El programa compila y se ejecuta sin fallos, pero **no hace lo que queremos**.
* *Ejemplo:* Un bucle que nunca termina (bucle infinito) o una fórmula matemática mal planteada.
* **Solución:** Aquí es donde entra la **Depuración**.

---

## 2. ¿Qué es Depurar (Debugging)?
Es el proceso de ejecutar el programa paso a paso para observar qué está ocurriendo internamente en la memoria y encontrar errores lógicos.

> **Mito:** "Yo depuro poniendo `System.out.println('Entra aquí')` por todas partes".
> **Realidad:** Eso es lento y sucio. Usa las herramientas del IDE.

---

## 3. Herramientas del Depurador (Debugger)
Todos los IDEs modernos (NetBeans, IntelliJ, Eclipse) comparten los mismos conceptos básicos.

### 1. Breakpoint (Punto de Ruptura) 🔴
Es una señal que ponemos en una línea de código (generalmente haciendo clic en el margen izquierdo).
* **Función:** Cuando ejecutamos en "Modo Debug", el programa se **pausará** automáticamente al llegar a esa línea, permitiéndonos inspeccionar el estado.

### 2. Controles de Ejecución
Una vez el programa está pausado, usamos estos botones para movernos:

* **Step Over (Paso a paso / F8):** Ejecuta la línea actual y pasa a la siguiente. Si la línea es una llamada a un método, lo ejecuta entero sin entrar en él.
* **Step Into (Entrar / F7):** Si la línea es una llamada a un método, **entra** dentro de ese método para depurarlo línea a línea.
* **Step Out (Salir):** Ejecuta lo que queda del método actual y vuelve al lugar desde donde fue llamado.
* **Resume/Continue (F5/F9):** Reanuda la ejecución normal hasta encontrar el siguiente Breakpoint.

### 3. Inspección de Variables (Watches)
Mientras estamos en pausa, podemos ver el panel de "Variables".
* Nos muestra el valor actual de todas las variables en ese instante exacto.
* Podemos ver cómo cambian los contadores de un bucle en tiempo real.
* Podemos "vigilar" (Watch) expresiones específicas (ej: ver cuánto vale `i * 2` en cada vuelta).

---

## 4. Guía Rápida de Depuración en NetBeans/IntelliJ
1.  **Pon un Breakpoint:** Haz clic en el número de línea donde crees que empieza el problema.
2.  **Lanza el Debugger:** En lugar de darle al botón "Play" (Run) ▶️, dale al botón del "Bicho" (Debug) 🐞.
3.  **Observa:** El programa se detendrá. Mira el panel de variables.
4.  **Avanza:** Usa "Step Over" para ver cómo avanza el flujo lógico. ¿Entra en el `if` que esperabas? ¿El contador del `for` sube correctamente?

---

## 5. Recursos para Profundizar
* [📖 Common Java Exceptions](https://programming.guide/java/list-of-java-exceptions.html) - Lista de errores de ejecución comunes.

---
[◀ Volver: Bucles y Saltos](./06-bucles-y-saltos.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Fundamentos POO ▶](./08-fundamentos-poo.md)
