# Hibernate: Operaciones CRUD con Sesiones

Una vez que entendemos los estados por los que pasa un objeto (Transitorio, Persistente, Separado), realizar operaciones CRUD en Hibernate es mucho más sencillo y limpio que escribir sentencias SQL a mano con JDBC.

Para todas estas operaciones, necesitamos obtener un objeto `Session` a partir de nuestra `SessionFactory` y envolver nuestras acciones en una **Transacción**.

---

## 1. Create (Insertar Datos)
Para guardar un objeto nuevo en la base de datos (pasar de *Transient* a *Persistent*).

* `session.save(objeto)`: Guarda el objeto y devuelve el ID generado por la base de datos de forma inmediata.
* `session.persist(objeto)`: Guarda el objeto, pero no garantiza devolver el ID al instante (es el estándar oficial de JPA y suele ser preferido hoy en día).

```java
Usuario nuevo = new Usuario("Ana", "ana@email.com");

session.beginTransaction();
Integer idGenerado = (Integer) session.save(nuevo);
session.getTransaction().commit();

System.out.println("Usuario guardado con ID: " + idGenerado);
```

---

## 2. Read (Consultar Datos por ID)
En Hibernate hay dos formas principales de recuperar un objeto si conocemos su Clave Primaria. Entender la diferencia te salvará de graves problemas de rendimiento.

### A. `session.get(Clase.class, id)`
Va directamente a la base de datos, ejecuta un `SELECT` y te devuelve el objeto lleno con los datos. Si el registro no existe, devuelve `null`. 
* **Cuándo usarlo:** Cuando no estás seguro de si el registro existe en la base de datos.

### B. `session.load(Clase.class, id)` (Lazy Loading)
Devuelve un objeto "falso" (un *Proxy*). **No hace ninguna consulta a la base de datos de inmediato**. Solo ejecutará el `SELECT` en el instante exacto en que intentes leer algún dato (ej. al llamar a `user.getNombre()`). Si el registro no existe y tratas de acceder a él, lanzará una excepción `ObjectNotFoundException`. 
* **Cuándo usarlo:** Cuando estés 100% seguro de que el objeto existe y solo necesitas su referencia (por ejemplo, para asignarlo como clave foránea de otro objeto sin gastar memoria cargando todos sus datos).

```java
session.beginTransaction();

// Uso clásico con get()
Usuario user = session.get(Usuario.class, 1);
if (user != null) {
    System.out.println("Usuario encontrado: " + user.getNombre());
}

session.getTransaction().commit();
```

---

## 3. Update (Actualizar Datos)
Aquí es donde brilla el motor de Hibernate frente a JDBC clásico.

### A. Actualización Automática (Dirty Checking)
Si el objeto ya está en estado **Persistente** (por ejemplo, lo acabas de sacar con `get()`), no necesitas llamar a ningún método de actualización. Simplemente cambia sus valores con un *setter* y haz el *commit*. Hibernate detecta los cambios automáticamente.

```java
session.beginTransaction();

Usuario user = session.get(Usuario.class, 1);
user.setEmail("nuevo_email@email.com"); // Hibernate detecta que el objeto está "sucio"

session.getTransaction().commit(); // Aquí se ejecuta un UPDATE SQL automáticamente
```

### B. Actualización Manual (`update` y `merge`)
Si tienes un objeto **Detached** (Separado) que viene de otra sesión (por ejemplo, los datos te llegan desde un formulario de una página web y tú creas un objeto con ese ID), tienes que volver a ligarlo a una sesión abierta.

* `session.update(objeto)`: Fuerza la actualización. Falla si ya hay otro objeto persistente con ese mismo ID en la sesión actual.
* `session.merge(objeto)`: Copia los datos del objeto separado a un objeto persistente seguro de la sesión actual. Es más seguro y es el estándar moderno.

```java
session.beginTransaction();
// usuarioDetached es un objeto que teníamos guardado en memoria de antes
session.merge(usuarioDetached); 
session.getTransaction().commit();
```

---

## 4. Delete (Borrar Datos)
Para borrar un registro, necesitas tener una referencia al objeto en memoria (con su ID) y pasarlo al método `delete()`.

```java
session.beginTransaction();

// Aquí usamos load() porque es más eficiente: no necesitamos 
// cargar los datos de la BD, solo decirle a Hibernate qué ID queremos borrar.
Usuario user = session.load(Usuario.class, 1); 
session.delete(user);

session.getTransaction().commit(); // Se ejecuta el DELETE SQL
```

---

## 5. Recursos para Profundizar
* [📖 Get vs Load in Hibernate (Baeldung)](https://www.baeldung.com/hibernate-save-persist-update-merge-saveorupdate) - Diferencias clave en profundidad.
* [📖 Hibernate Update vs Merge (Vlad Mihalcea)](https://vladmihalcea.com/jpa-persist-and-merge/) - Guía experta sobre cómo reconectar objetos *Detached*.

---
[◀ Volver: Operaciones CRUD con Sesiones](./14-hibernate-operaciones-crud.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Relaciones, Colecciones y Transacciones ▶](./16-hibernate-relaciones-y-transacciones.md)
