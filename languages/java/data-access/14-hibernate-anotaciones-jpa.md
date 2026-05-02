# Hibernate: Anotaciones JPA (El Mapeo Moderno)

El estándar actual de la industria para el mapeo objeto-relacional es abandonar los archivos XML e incrustar la metainformación directamente en nuestras clases mediante **Anotaciones JPA**. 

A estas clases de datos simples, sin lógica de negocio pesada ni herencias extrañas, se les conoce universalmente como **POJOs** (*Plain Old Java Objects*).

---

## 1. ¿Qué es JPA?
**JPA (Jakarta Persistence API / Java Persistence API)** no es un programa, es una **especificación**. Es un manual de reglas de Java que define cómo deben usarse las anotaciones. Hibernate es el "motor" que lee esas reglas y ejecuta el SQL.

Al usar importaciones de `jakarta.persistence.*`, logramos que nuestro código no dependa en exclusiva de Hibernate; el día de mañana podríamos cambiar el motor ORM sin reescribir nuestras clases.

---

## 2. Anotaciones de Clase
Se colocan en la cabecera del POJO.

* `@Entity` **(Obligatoria):** Marca la clase como una entidad que será gestionada por el ORM.
* `@Table`: Permite especificar el nombre real de la tabla en SQL. Si no se pone, se asume el nombre de la clase.
  * *Ejemplo:* `@Table(name = "users")`

---

## 3. Anotaciones de Identificador (Clave Primaria)
* `@Id` **(Obligatoria):** Indica el atributo que actuará como Primary Key.
* `@GeneratedValue`: Delega la generación del ID a la base de datos.
  * `GenerationType.IDENTITY`: Usa el autoincremental nativo (ideal para MySQL/MariaDB).
  * `GenerationType.SEQUENCE`: Usa secuencias (ideal para Oracle/PostgreSQL).

---

## 4. Anotaciones de Atributos (Columnas)
Por defecto, todo atributo de la clase se mapea a una columna con su mismo nombre. Usamos anotaciones para refinar esto:

* `@Column`: Personaliza la columna física. Soporta parámetros como `name`, `nullable`, `unique`, y `length`.
* `@Transient`: Le dice al ORM que **ignore** este atributo. Solo existirá en la memoria RAM, no en la base de datos.
* `@Enumerated(EnumType.STRING)`: Obliga a guardar un `Enum` de Java usando su nombre en texto en lugar de su índice numérico (que es propenso a errores si el Enum cambia en el futuro).
* `@Lob`: (*Large Object*) Se usa para almacenar datos inmensos, como archivos binarios (ej. `byte[]` para imágenes) o textos enormes.

---

## 5. Ejemplo Práctico
Aquí tienes un POJO real, limpio y totalmente configurado con JPA.

```java
package com.quizmael.model;

import jakarta.persistence.*;
import java.time.LocalDate;

@Entity
@Table(name = "users")
public class User {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    @Column(name = "user_id", nullable = false)
    private Integer id;

    @Column(name = "name", nullable = false, unique = true, length = 20)
    private String name;

    @Column(name = "email", length = 40)
    private String email;

    @Column(name = "birth_date")
    private LocalDate birthDate;

    // Guarda el Enum como cadena de texto ("ADMIN", "USER"...)
    @Enumerated(EnumType.STRING)
    @Column(name = "role", nullable = false)
    private Role role; 

    @Lob
    @Column(name = "profile_picture")
    private byte[] profilePicture;

    // Constructor vacío obligatorio para JPA
    public User() {}

    // Getters y Setters...
    public Integer getId() { return id; }
    public void setId(Integer id) { this.id = id; }
}
```

---

## 6. Recursos Adicionales
* [📖 Baeldung: Introduction to JPA Annotations](https://www.baeldung.com/jpa-entities) - Excelente guía rápida de uso.
* [📖 Hibernate User Guide: Annotations](https://docs.jboss.org/hibernate/orm/current/userguide/html_single/Hibernate_User_Guide.html#entity) - El manual oficial sobre mapeo moderno.

---
[◀ Volver: Clases Persistentes y Estados](./13-hibernate-clases-persistentes-y-estados.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Relaciones y Colecciones ▶](./15-hibernate-relaciones-y-colecciones.md)