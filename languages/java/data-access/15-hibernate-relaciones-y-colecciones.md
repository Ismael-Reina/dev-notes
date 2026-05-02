# Hibernate: Relaciones y Colecciones

En el mundo real, los objetos no están aislados. Un `Departamento` tiene muchos `Empleados`, y un `Estudiante` se matricula en muchos `Cursos`. Hibernate gestiona estas asociaciones automáticamente, traduciendo la navegación entre objetos Java a Claves Foráneas (Foreign Keys) en SQL.

Al igual que con las entidades básicas, podemos mapear estas relaciones de la forma clásica (XML) o de la forma moderna (Anotaciones JPA).

---

## 1. Mapeo de Relaciones (Cardinalidad)

Es crucial entender qué lado de la relación es el "propietario". El lado propietario es el que **contiene físicamente la columna con la Clave Foránea** en la base de datos.

### A. Uno a Muchos / Muchos a Uno (1:N)
Es la relación más común. Por ejemplo, muchos empleados pertenecen a un mismo departamento.

**Forma Clásica (XML - Legacy):**
El lado "Muchos" usa `<many-to-one>`, y el lado "Uno" usa una colección `<set>` con la etiqueta `<one-to-many>`.
```xml
<!-- En Departamento.hbm.xml (Lado Uno) -->
<set name="empleados" inverse="true"> <!-- inverse="true" marca que él NO manda sobre la FK -->
    <key column="departamento_id"/>
    <one-to-many class="com.ejemplo.Empleado"/>
</set>

<!-- En Empleado.hbm.xml (Lado Muchos - Propietario de la FK) -->
<many-to-one name="departamento" class="com.ejemplo.Departamento" column="departamento_id"/>
```

**Forma Moderna (Anotaciones JPA):**
Se usan `@OneToMany` y `@ManyToOne`. La clave foránea se define con `@JoinColumn` y la inversa con `mappedBy`.
```java
// 1. Lado Uno (No propietario) - Departamento.java
@OneToMany(mappedBy = "departamento") 
private List<Empleado> empleados = new ArrayList<>();

// 2. Lado Muchos (Propietario de la FK) - Empleado.java
@ManyToOne
@JoinColumn(name = "departamento_id") // Esta es la columna física en la tabla 'empleado'
private Departamento departamento;
```

### B. Muchos a Muchos (N:M)
Un `Estudiante` tiene muchos `Cursos`, y un `Curso` tiene muchos `Estudiantes`. En bases de datos relacionales, esto **siempre requiere una tabla intermedia**.

**Forma Clásica (XML - Legacy):**
```xml
<set name="cursos" table="estudiante_curso">
    <key column="estudiante_id"/>
    <many-to-many class="com.ejemplo.Curso" column="curso_id"/>
</set>
```

**Forma Moderna (Anotaciones JPA):**
Se usa `@ManyToMany` y se define la tabla puente explícitamente con `@JoinTable` en el lado propietario.
```java
@ManyToMany
@JoinTable(
    name = "estudiante_curso", // Nombre de la tabla intermedia en SQL
    joinColumns = @JoinColumn(name = "estudiante_id"), // FK hacia esta entidad
    inverseJoinColumns = @JoinColumn(name = "curso_id") // FK hacia la otra entidad
)
private List<Curso> cursos = new ArrayList<>();
```

---

## 2. Optimizando el Rendimiento: Carga Perezosa
Al mapear colecciones, Hibernate debe decidir cuándo ir a la base de datos a buscar los datos hijos.

* **EAGER (Ansiosa):** Carga todos los datos de golpe con un enorme `JOIN`. Puede saturar la memoria RAM.
* **LAZY (Perezosa):** Es la **buena práctica**. Le indica a Hibernate que no cargue la lista de hijos hasta que realmente la pidas en el código (ej. al hacer `departamento.getEmpleados()`).

```java
@ManyToOne(fetch = FetchType.LAZY)
@JoinColumn(name = "departamento_id")
private Departamento departamento;
```

---

## 3. Propagación de Operaciones: Cascada
El parámetro `cascade` define qué ocurre con los objetos hijos si modificamos al padre. ¿Si borras un Departamento, quieres que se borren automáticamente todos sus Empleados?

* **XML:** `cascade="all"`, `cascade="save-update"`, `cascade="delete"`, `cascade="none"`.
* **JPA:** `CascadeType.ALL`, `CascadeType.PERSIST`, `CascadeType.REMOVE`.

*Ejemplo JPA:* `@OneToMany(mappedBy = "departamento", cascade = CascadeType.ALL)`

---

## 4. Gestión de Transacciones
Una vez modeladas las entidades, debemos asegurar que nuestras operaciones en la base de datos cumplan con el principio **ACID** (Atomicidad, Consistencia, Aislamiento y Durabilidad). 

En Hibernate, cualquier operación de escritura (INSERT, UPDATE, DELETE) **debe** ir envuelta en una transacción.

```java
Transaction tx = null;
try {
    tx = session.beginTransaction();
    
    // Operaciones (ej. asociar un empleado a un departamento y guardarlo)
    session.persist(empleado);
    
    tx.commit(); // Si todo va bien, confirmamos los cambios en SQL
} catch (Exception e) {
    if (tx != null) tx.rollback(); // Si algo falla, deshacemos todo para evitar datos corruptos
    e.printStackTrace();
}
```

---

## 5. Recursos para Profundizar
* [📖 Hibernate Association Mappings (Baeldung)](https://www.baeldung.com/hibernate-one-to-many) - Guía excepcional para entender el uso de `@OneToMany` y `@ManyToOne`.
* [📖 Lazy Loading vs Eager Fetching](https://www.baeldung.com/hibernate-lazy-eager-loading) - Análisis de rendimiento entre tipos de carga.
* [📖 Understanding Cascade Types (Vlad Mihalcea)](https://vladmihalcea.com/hibernate-cascade-types/) - Explicación avanzada sobre cómo la cascada afecta a la integridad de datos.

---
[◀ Volver: Anotaciones JPA](./14-hibernate-anotaciones-jpa.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Operaciones CRUD y Transacciones ▶](./16-hibernate-operaciones-crud-y-transacciones.md)