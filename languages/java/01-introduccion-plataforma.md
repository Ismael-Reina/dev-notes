# Introducción a la Plataforma Java

## 1. Breve Historia y Filosofía
Java nació en 1991 dentro de **Sun Microsystems** (hoy Oracle), diseñado por **James Gosling**. Su nombre original era *Oak*. Aunque se pensó para electrónica de consumo, su auge llegó con Internet.

Su filosofía central se resume en el lema:
> **"Write Once, Run Anywhere" (WORA)**
> *(Escribe una vez, ejecuta en cualquier lugar)*

---

## 2. Características Clave
Java se define como un lenguaje:

1.  **Orientado a Objetos (POO):** Todo el diseño se basa en objetos y clases. Facilita la reutilización y el mantenimiento.
2.  **Independiente de la Arquitectura:** No compila a código máquina nativo de una CPU específica, sino a un código intermedio neutro.
3.  **Simple:** Elimina la complejidad de C++ (sin punteros aritméticos directos, gestión automática de memoria).
4.  **Seguro:** Se ejecuta en un entorno controlado (sandbox) que previene accesos no autorizados a la memoria del sistema.
5.  **Multihilo:** Soporte nativo para ejecutar tareas concurrentes.

---

## 3. Arquitectura: El Secreto del Bytecode
La magia de la portabilidad de Java reside en su proceso de traducción híbrido.

### El Proceso
1.  **Código Fuente (`.java`):** Archivo de texto legible por humanos.
2.  **Compilador (`javac`):** Traduce el fuente a **Bytecode**.
3.  **Bytecode (`.class`):** Código binario intermedio, independiente del hardware.
4.  **Máquina Virtual de Java (JVM):** Un intérprete específico para cada sistema operativo (Windows, Linux, Mac) que traduce el Bytecode a código máquina real en tiempo de ejecución.

**Diagrama conceptual:**

```text
Código Fuente (.java)  --->  Compilador (javac)  --->  Bytecode (.class)
                                                            |
                                                            v
                                                   [ Máquina Virtual (JVM) ]
                                                            |
                                             -------------------------------
                                             |              |              |
                                        Windows CPU     Linux CPU       Mac CPU
```

---

## 4. El Ecosistema: JDK, JRE y JVM
Conceptos que suelen confundirse pero son distintos:

* **JVM (Java Virtual Machine):** El motor de ejecución. Simula un ordenador virtual.
* **JRE (Java Runtime Environment):** JVM + Bibliotecas estándar de clases. Es lo mínimo necesario para **ejecutar** un programa Java.
* **JDK (Java Development Kit):** JRE + Herramientas de desarrollo (`javac`, depurador, generador de documentación). Es lo necesario para **programar**.

> **Regla:** JDK > JRE > JVM

---

## 5. Tipos de Ediciones (Distribuciones)
* **Java SE (Standard Edition):** La API base. Incluye las bibliotecas fundamentales (`java.lang`, `java.util`). Es lo que estudiarás en el ciclo.
* **Jakarta EE (antes Java EE):** Versión empresarial. Añade librerías para desarrollo web, servidores y grandes sistemas distribuidos.
* **Java ME (Micro Edition):** Versión reducida para dispositivos con recursos limitados (en desuso frente a Android).

---
[◀ Volver: Índice](./README.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Estructura y Entorno ▶](./02-estructura-y-entorno.md)
