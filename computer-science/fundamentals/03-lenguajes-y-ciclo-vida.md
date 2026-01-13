# Lenguajes de Programación y Ciclo de Vida

## 1. Clasificación de los Lenguajes
Los lenguajes de programación son herramientas que nos permiten comunicarnos con el hardware. Se clasifican según su nivel de abstracción (cercanía al humano o a la máquina).

### Según Nivel de Abstracción
1.  **Lenguaje Máquina (Bajo Nivel):**
    * Cadenas de ceros y unos (binario) que la CPU ejecuta directamente.
    * Es específico de cada arquitectura de procesador.
    * Muy difícil de escribir y entender por humanos.

2.  **Lenguaje Ensamblador (Bajo Nivel):**
    * Utiliza mnemotécnicos (abreviaturas como `ADD`, `MOV`, `JMP`) para representar instrucciones máquina.
    * Requiere un programa "ensamblador" para traducirlo a binario.
    * Sigue dependiendo de la arquitectura del hardware.

3.  **Lenguajes de Alto Nivel:**
    * Usan palabras cercanas al lenguaje humano (generalmente inglés: `if`, `while`, `print`).
    * Son **portables**: el mismo código puede funcionar en diferentes máquinas.
    * Ejemplos: Java, Python, C++, C#.

---

## 2. Traducción: De Código Fuente a Ejecutable
Las computadoras no entienden Java o C++, solo entienden binario. Necesitamos un "traductor".

### A. Compilación (Ej: C, C++)
Traduce **todo** el programa de una sola vez antes de ejecutarlo.
1.  **Código Fuente:** El programador escribe el archivo (`.c`).
2.  **Compilador:** Analiza todo el código y busca errores.
3.  **Código Objeto:** Genera un archivo intermedio binario.
4.  **Linker (Enlazador):** Une el código objeto con librerías del sistema.
5.  **Ejecutable:** Crea un archivo independiente (`.exe`) que puede correr sin el compilador.
    * *Ventaja:* Ejecución muy rápida.
    * *Desventaja:* Hay que recompilar si cambias el S.O.

### B. Interpretación (Ej: Python, JavaScript, PHP)
Traduce y ejecuta instrucción por instrucción, línea a línea.
* No genera un ejecutable final.
* Necesitas tener el intérprete instalado en la máquina que corre el programa.
* *Ventaja:* Muy flexible y multiplataforma.
* *Desventaja:* Ejecución más lenta que un compilado.

### C. Híbrido (Ej: Java)
Combina lo mejor de ambos mundos.
1.  Compila el código fuente (`.java`) a un código intermedio llamado **Bytecode** (`.class`).
2.  Este Bytecode es ejecutado (interpretado) por la **Máquina Virtual de Java (JVM)**.
    * Esto permite la filosofía: *"Write Once, Run Anywhere"* (Escribe una vez, ejecuta donde sea).

---

## 3. Ciclo de Vida del Software (Clásico)
Crear software profesional sigue una serie de fases ordenadas, conocidas como el **Modelo en Cascada** (aunque hoy día se usan metodologías ágiles, esta es la base teórica).

1.  **Análisis:**
    * ¿Qué problema resolvemos?
    * Se definen los **Requisitos** funcionales y no funcionales.
    * Resultado: Documento de Especificación de Requisitos.

2.  **Diseño:**
    * ¿Cómo lo vamos a solucionar?
    * Se definen algoritmos, bases de datos, interfaces y arquitectura.
    * Herramientas: Diagramas UML, diagramas de flujo.

3.  **Codificación (Implementación):**
    * Escritura del código fuente en el lenguaje elegido (Java).
    * Es la fase de "programación" pura.

4.  **Pruebas (Testing):**
    * Detectar y eliminar fallos (bugs).
    * *Pruebas Unitarias:* Probar cada pieza por separado.
    * *Pruebas de Integración:* Probar que las piezas funcionan juntas.

5.  **Explotación y Mantenimiento:**
    * Instalación del software en el entorno del cliente.
    * Corrección de errores post-lanzamiento y mejoras evolutivas.

---

## 4. Entornos de Desarrollo (IDE)
Un **IDE** (Integrated Development Environment) es una aplicación que unifica todas las herramientas necesarias para desarrollar.

**Componentes típicos de un IDE (como Eclipse o IntelliJ):**
* **Editor de Código:** Resaltado de sintaxis y autocompletado.
* **Compilador/Intérprete:** Integrado para ejecutar con un botón.
* **Depurador (Debugger):** Permite pausar la ejecución y ver variables paso a paso.
* **Gestor de Proyectos:** Organiza los archivos y carpetas.

---

## 5. Recursos para Profundizar
* [🎥 Compiled vs Interpreted Languages](https://www.youtube.com/watch?v=_C5AHaS1mOA) - Explicación clara de las diferencias.
* [📖 Historia de Java y la JVM](https://www.java.com/es/download/help/whatis_java.html) - Por qué Java es híbrido.
* [🛠️ Roadmap.sh: Computer Science](https://roadmap.sh/computer-science) - Una ruta visual de todos estos conceptos.

---
[◀ Volver: Programación y Algoritmos](./02-programacion-y-algoritmos.md) | [🏠 Ir al Índice](./README.md)
