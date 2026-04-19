# Introducción a la Persistencia de Datos

## 1. El Concepto de Persistencia
En la programación básica, los datos viven en la memoria RAM (variables, objetos, arrays). Esta memoria es **volátil**, lo que significa que al cerrar la aplicación o apagar el ordenador, toda la información se pierde.

La **persistencia** es la acción de guardar el estado de esos datos en un medio de almacenamiento secundario (como un disco duro o un servidor en la nube) para que sobrevivan a la ejecución del programa y puedan ser recuperados en el futuro.

---

## 2. Evolución del Almacenamiento de Datos

### A. Ficheros Planos (Archivos de Texto/Binarios)
Es la forma más básica de persistencia.
* **Ventajas:** Muy fáciles de implementar para datos simples (ej: guardar configuraciones o logs).
* **Desventajas:** Pésimos para buscar información concreta. Si tienes un archivo con 10.000 clientes y quieres buscar uno, tienes que leer el archivo entero secuencialmente. Además, no manejan bien la concurrencia (dos usuarios intentando escribir a la vez).

### B. Bases de Datos Relacionales (SQL)
Sistemas como MySQL, PostgreSQL u Oracle. Organizan la información en **tablas** con filas y columnas, estableciendo relaciones matemáticas entre ellas.
* **Ventajas:** Búsquedas ultra rápidas (índices), evitan datos duplicados y garantizan la integridad de las transacciones (ACID).
* **Desventajas:** Estructura rígida. Si quieres cambiar el formato de un dato, tienes que alterar la estructura de la tabla entera.

### C. Bases de Datos NoSQL y Orientadas a Objetos
Sistemas como MongoDB o Firebase. No usan tablas, sino "documentos" (parecidos a JSON).
* **Ventajas:** Flexibilidad total. Cada registro puede tener campos diferentes. Ideales para Big Data y aplicaciones muy cambiantes.

---

## 3. El Desfase Objeto-Relacional (Impedance Mismatch)
En Java, programamos usando el **Paradigma Orientado a Objetos** (Clases, Herencia, Polimorfismo, Listas). Sin embargo, el 90% de las bases de datos del mundo son **Relacionales** (Tablas, Filas, Columnas, Claves Foráneas).

Estos dos mundos **no hablan el mismo idioma**. Guardar un objeto `Cliente` (que tiene una lista de objetos `Factura` por dentro) en una base de datos de tablas requiere desmontar el objeto en piezas y repartirlo en varias tablas. 

### ¿Cómo soluciona esto Java?
En este bloque estudiaremos las dos grandes formas de comunicar Java con una base de datos:
1.  **JDBC (Java Database Connectivity):** La forma tradicional. Escribimos sentencias SQL a mano dentro de Java. Es rápido, pero genera mucho código repetitivo.
2.  **ORM (Object-Relational Mapping):** Tecnologías como **JPA e Hibernate**. Hacen magia: tú le das un objeto Java y el framework se encarga automáticamente de traducirlo a SQL y guardarlo en las tablas correctas sin que tú escribas ni una sola sentencia SQL.

---

## 4. Recursos para Profundizar
* [📖 Object-Relational Impedance Mismatch (Wikipedia)](https://en.wikipedia.org/wiki/Object-relational_impedance_mismatch) - Explicación detallada del problema de incompatibilidad entre objetos y tablas.

---
[🏠 Ir al Índice](./README.md) | [Siguiente: Formatos de Intercambio (XML/JSON) ▶](./02-formatos-intercambio-xml-json.md)
