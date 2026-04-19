# Mapeo Objeto-Relacional (ORM) y Herramientas

En el desarrollo de software moderno, la mayoría de las aplicaciones se construyen usando el paradigma de la **Programación Orientada a Objetos (POO)**. Sin embargo, los sistemas de bases de datos más extendidos, robustos y fiables siguen siendo de tipo **Relacional (RDBMS)**.

Aquí es donde surge un conflicto fundamental.

---

## 1. El Desfase Objeto-Relacional
A este problema se le conoce como **desfase o impedancia objeto-relacional**. Consiste en la diferencia estructural y matemática que existe entre cómo representamos los datos en la memoria del programa y cómo los guardamos en el disco.

* **En el código (POO):** Usamos Clases, Objetos, Herencia, Polimorfismo y Colecciones.
* **En la base de datos (Relacional):** Usamos Tablas, Filas (tuplas), Columnas (tipos primitivos) y Claves Foráneas.

Las bases de datos relacionales no entienden de "objetos" ni de "herencia". Solo permiten guardar datos escalares simples (números, cadenas, fechas). Por lo tanto, para guardar un objeto, un programador tradicionalmente tenía que "despiezarlo", extraer sus atributos simples, y crear largas sentencias SQL de tipo `INSERT` o `UPDATE` (usando JDBC puro).

---

## 2. ¿Qué es el ORM?
**ORM (Object-Relational Mapping)**, o Mapeo Objeto-Relacional, es una técnica y herramienta de programación que soluciona este desfase de forma automática. 

Actúa como un puente o traductor. Te permite manipular la base de datos operando directamente sobre objetos, con todas las características de la POO, simulando que estás trabajando con una base de datos orientada a objetos.

### ¿Cómo funciona la traducción básica?
En el modelo ORM estándar:
* Una **Clase** Java se mapea (se asocia) a una **Tabla**.
* Un **Objeto** (instancia de la clase) se mapea a una **Fila** (registro).
* Un **Atributo** (propiedad de la clase) se mapea a una **Columna**.

---

## 3. Ventajas y Desventajas del ORM

### Ventajas (Por qué se usa en la industria)
1.  **Reducción del tiempo de desarrollo:** Genera automáticamente el SQL en la sombra.
2.  **Abstracción e Independencia:** El código Java no depende de la base de datos. Puedes cambiar de MySQL a Oracle y el código no se toca; el ORM se encarga de traducir al dialecto SQL adecuado.
3.  **Mantenibilidad:** Menos código repetitivo (boilerplate) significa menos errores y código más limpio.
4.  **Soporte de POO pura:** Permite persistir jerarquías de herencia y colecciones.

### Desventajas
1.  **Curva de aprendizaje:** Aprender a configurar y optimizar un ORM lleva tiempo.
2.  **Pérdida de rendimiento (Overhead):** Añade una capa de procesamiento extra. Para consultas hiper-optimizadas o masivas, a veces el SQL puro es más rápido.
3.  **Pérdida de control:** Al delegar la generación del SQL en la herramienta, a veces se generan consultas poco eficientes si el ORM está mal configurado.

---

## 4. Herramientas ORM más utilizadas en Java

El mercado de Java ofrece varias soluciones maduras para aplicar ORM:

### A. Hibernate
Es el *framework* ORM más famoso, extendido y documentado del mundo Java. Es software libre (licencia GNU LGPL). Convierte los datos, genera el SQL automáticamente e incluye su propio y potente lenguaje de consultas orientado a objetos llamado **HQL** (*Hibernate Query Language*).

### B. JPA (Java Persistence API)
Ojo, JPA **no es una herramienta**, es una **especificación** oficial de Java (creada por *Sun Microsystems/Oracle*). Es un manual de reglas que dicta cómo debe funcionar un ORM en Java. 
Herramientas como *Hibernate*, *OpenJPA* o *EclipseLink* son las "implementaciones" que programan el código real siguiendo esas reglas de JPA. Hoy en día, la forma profesional de usar Hibernate es a través de los estándares de JPA.

### C. MyBatis (Anteriormente iBatis)
Es un framework de la *Apache Software Foundation*. Tiene un enfoque diferente: en lugar de ocultarte el SQL, te obliga a escribirlo en archivos XML (o anotaciones), pero automatiza el mapeo de los resultados a objetos Java. Es ideal cuando necesitas un control milimétrico sobre el código SQL.

---
[◀ Volver: Pool de Conexiones](./10-pool-conexiones-datasource.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Configuración y Ficheros de Mapeo (Hibernate) ▶](./12-hibernate-configuracion-y-mapeo.md)
