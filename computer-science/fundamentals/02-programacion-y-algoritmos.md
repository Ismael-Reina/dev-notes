# Programación y Algoritmia

## 1. Conceptos Básicos
Antes de escribir código, debemos entender la lógica que lo gobierna.

* **Algoritmo:** Conjunto ordenado y finito de operaciones que permite hallar la solución a un problema. No depende de un lenguaje de programación específico (es universal).
* **Programa:** Es la implementación de un algoritmo en un lenguaje de programación concreto que una computadora puede entender y ejecutar.

### Características de un Buen Algoritmo
1.  **Preciso:** Cada paso debe estar claramente definido sin ambigüedades.
2.  **Finito:** Debe tener un inicio y un fin. No puede ejecutarse eternamente (bucle infinito no deseado).
3.  **Determinista:** Para las mismas entradas, siempre debe producir la misma salida.
4.  **Eficiente:** Debe consumir la menor cantidad de recursos (tiempo y memoria) posible.

---

## 2. Fases de Creación de un Programa
El proceso de programación no es solo "picar código". Sigue un ciclo lógico:

1.  **Análisis del Problema:** Entender qué se nos pide. Definir claramente las **Entradas** (datos necesarios) y las **Salidas** (resultados esperados).
2.  **Diseño del Algoritmo:** Diseñar la solución usando herramientas como Pseudocódigo u Ordinogramas.
3.  **Codificación:** Traducir el diseño a un lenguaje de programación (Java, Python, C).
4.  **Pruebas y Depuración:** Comprobar que funciona y corregir errores.
5.  **Documentación y Mantenimiento:** Explicar cómo funciona para el futuro.

---

## 3. Herramientas de Representación
Para diseñar algoritmos sin atarnos a la sintaxis compleja de un lenguaje real, usamos dos herramientas principales:

### A. Pseudocódigo
Es un lenguaje falso, mezcla de lenguaje humano y convenciones de programación. Permite centrarse en la lógica sin preocuparse por puntos y comas.

**Ejemplo: Algoritmo para saber si eres mayor de edad**

[BLOCK]pseudocodigo
INICIO
    Leer edad
    SI edad >= 18 ENTONCES
        Escribir "Eres mayor de edad"
    SINO
        Escribir "Eres menor de edad"
    FIN_SI
FIN
[BLOCK]

### B. Ordinogramas (Diagramas de Flujo)
Representación gráfica del algoritmo usando símbolos estandarizados unidos por flechas (líneas de flujo).

| Símbolo | Nombre | Función |
| :--- | :--- | :--- |
| **Óvalo** | Inicio/Fin | Marca el comienzo y el final del algoritmo. |
| **Paralelogramo** | Entrada/Salida | Lectura de datos (teclado) o impresión de resultados (pantalla). |
| **Rectángulo** | Proceso | Operaciones matemáticas, asignaciones de valor. |
| **Rombo** | Decisión | Una pregunta con dos salidas posibles (Sí/No). Representa el `if`. |

---

## 4. Programación Estructurada
Es el paradigma fundamental que dice que todo programa puede escribirse utilizando únicamente tres estructuras de control. Esto evita el "código espagueti" (uso caótico de saltos `GOTO`).

### 1. Estructura Secuencial
Las instrucciones se ejecutan una tras otra, en orden descendente.
* *Ejemplo:* Leer A -> Leer B -> Sumar A+B -> Mostrar Resultado.

### 2. Estructura Condicional (Selectiva)
Permite elegir entre diferentes caminos según si una condición es Verdadera o Falsa.
* **Simple:** `SI (condición) ENTONCES (acción)`.
* **Doble:** `SI (condición) ... SINO ...` (If-Else).
* **Múltiple:** Elegir entre varias opciones según el valor de una variable (Switch/Case).

### 3. Estructura Iterativa (Repetitiva o Bucles)
Permite repetir un bloque de instrucciones mientras se cumpla una condición.
* **Mientras (While):** La condición se evalúa al principio. Si es falsa, no entra nunca.
* **Repetir (Do-While):** La condición se evalúa al final. Se ejecuta al menos una vez.
* **Para (For):** Se usa cuando sabemos de antemano cuántas veces queremos repetir el ciclo (tiene un contador).

---

## 5. Recursos para Profundizar
* [🛠️ PSeInt](https://pseint.sourceforge.net/) - La mejor herramienta educativa para escribir pseudocódigo y generar diagramas de flujo automáticamente. **Muy recomendada para practicar la lógica**.
* [🧩 Blockly Games](https://blockly.games/maze?lang=es) - Juegos de lógica para entender bucles y condicionales visualmente.
* [📖 Introduction to Algorithms (Khan Academy)](https://www.khanacademy.org/computing/computer-science/algorithms) - Curso gratuito sobre eficiencia y lógica.

---
[◀ Volver: Sistemas Informáticos](./01-sistemas-informaticos.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Lenguajes y Ciclo de Vida ▶](./03-lenguajes-y-ciclo-vida.md)
