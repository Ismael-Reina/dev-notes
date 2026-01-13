# Introducción a los Sistemas Informáticos

## 1. Conceptos Fundamentales
La informática es la ciencia que estudia el **tratamiento automático de la información**. Para ello, utilizamos un **Sistema Informático**, compuesto por tres pilares:

* **Hardware (Hw):** Componentes físicos y tangibles (circuitos, cables, dispositivos).
* **Software (Sw):** Componentes lógicos e intangibles (programas, datos, protocolos).
* **Humanware:** El factor humano (usuarios, desarrolladores, técnicos) que interactúa con el sistema.

### Clasificación del Software
1. **Software de Sistema:** Gestiona el hardware y sirve de base (S.O., drivers, utilidades de disco).
2. **Software de Programación:** Herramientas para crear nuevos programas (editores, compiladores, depuradores, IDEs).
3. **Software de Aplicación:** Programas finales para tareas específicas del usuario (navegadores, ofimática, videojuegos).

---

## 2. Arquitectura de Von Neumann
Propuesta en 1945, describe la estructura básica de la mayoría de computadoras modernas. Su característica clave es que **las instrucciones (programas) y los datos se almacenan en la misma memoria**.

### Componentes Principales
1. **CPU (Unidad Central de Proceso):** El "cerebro".
   * **UC (Unidad de Control):** Lee instrucciones de memoria, las decodifica y coordina su ejecución. Es el "director de orquesta".
   * **ALU (Unidad Aritmético-Lógica):** Realiza operaciones matemáticas (+, -, *) y lógicas (AND, OR, NOT).
   * **Registros:** Pequeñas memorias de ultra-alta velocidad dentro de la CPU para almacenar datos temporales inmediatos.

2. **Memoria Principal (RAM):**
   * Almacena tanto el programa en ejecución como los datos que usa.
   * Es **volátil** (se borra al apagar) y de acceso aleatorio.
   * Se organiza en celdas direccionables.

3. **Sistema de E/S (Entrada/Salida):**
   * Permite la comunicación con el exterior a través de **periféricos** (teclado, monitor, disco duro).

4. **Buses:** Canales de comunicación que conectan los componentes:
   * **Bus de Datos:** Transporta la información.
   * **Bus de Direcciones:** Indica *dónde* leer o escribir en la memoria.
   * **Bus de Control:** Transmite órdenes y señales de estado (lectura/escritura, reloj).

---

## 3. Representación de la Información
Las computadoras son máquinas digitales que trabajan con dos estados de tensión (encendido/apagado), representados por el sistema **Binario**.

### Unidades de Medida
* **Bit (b):** La unidad mínima (0 o 1).
* **Byte (B):** Agrupación de **8 bits**. Es la unidad mínima direccionable en memoria.
   * Permite representar $2^8 = 256$ combinaciones distintas.

### Sistemas de Numeración
* **Binario (Base 2):** Usa 0 y 1. Lenguaje nativo de la máquina.
* **Hexadecimal (Base 16):** Usa 0-9 y A-F. Se usa para simplificar la lectura de binario (1 dígito hex = 4 bits).
* **Decimal (Base 10):** Nuestro sistema natural.

### Codificación de Caracteres
Para representar texto, asignamos un valor numérico a cada carácter:
* **ASCII:** Estándar de 7 bits (128 caracteres). Solo inglés (sin ñ ni tildes).
* **ASCII Extendido (ISO-8859-1):** 8 bits (256 caracteres). Incluye caracteres europeos occidentales.
* **Unicode (UTF-8):** Estándar actual. Longitud variable. Permite representar símbolos de casi todos los idiomas del mundo y emojis.

---

## 4. Recursos para Profundizar
* [🎥 Cómo funciona una CPU (En 100 segundos)](https://www.youtube.com/watch?v=FZGugFqdr60) - Explicación visual rápida.
* [📖 The Von Neumann Architecture](https://en.wikipedia.org/wiki/Von_Neumann_architecture) - Artículo detallado en Wikipedia.
* [🛠️ RapidTables - Conversor de Bases](https://www.rapidtables.com/convert/number/binary-to-decimal.html) - Herramienta útil para ejercicios de conversión binario/hex/decimal.

---
[🏠 Ir al Índice](./README.md) | [Siguiente: Programación y Algoritmos ▶](./02-programacion-y-algoritmos.md)
