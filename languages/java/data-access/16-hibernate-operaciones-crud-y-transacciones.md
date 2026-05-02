# Hibernate: Operaciones CRUD y Transacciones

Una vez que entendemos los estados por los que pasa un objeto y cómo se relacionan entre sí, interactuar con la base de datos en Hibernate es mucho más sencillo y limpio que escribir sentencias SQL a mano con JDBC.

Todas las operaciones se realizan a través de un objeto `Session`.

---

## 1. Create (Insertar Datos)
Para guardar un objeto nuevo en la base de datos (pasar de *Transient* a *Persistent*).

* `session.save(objeto)`: Guarda el objeto y devuelve el ID generado por la BD de forma inmediata.
* `session.persist(objeto)`: Guarda el objeto, pero no garantiza devolver el ID al instante (es el estándar oficial de JPA).

```java
Usuario nuevo = new Usuario("Ana", "ana@email.com");
session.persist(nuevo);
```

---

## 2. Read (Consultar Datos por ID)
Hay dos formas principales de recuperar un objeto por su Clave Primaria. Entender la diferencia te salvará de graves problemas de rendimiento.

### A. `session.get(Clase.class, id)`
Va directamente a la base de datos, ejecuta un `SELECT` y te devuelve el objeto lleno con los datos. Si el registro no existe, devuelve `null`. Úsalo cuando **no estás seguro** de si el registro existe.

### B. `session.load(Clase.class, id)` (Proxy / Lazy)
Devuelve un objeto "falso" (un *Proxy*) vacío. **No hace ninguna consulta a la BD de inmediato**. Solo ejecutará el `SELECT` en el instante exacto en que intentes leer algún dato (ej. `user.getNombre()`). Si el registro no existe, lanza una excepción. Úsalo cuando solo necesitas la referencia del objeto para enlazarlo con otro.

---

## 3. Update (Actualizar Datos)

### A. Actualización Automática (Dirty Checking)
Si el objeto ya está en estado **Persistente** (lo acabas de sacar con `get()`), no necesitas llamar a ningún método. Simplemente cambia sus valores con un *setter*. Hibernate detectará que está "sucio" y ejecutará el `UPDATE` automáticamente al confirmar la transacción.

### B. Actualización Manual (`merge`)
Si tienes un objeto **Detached** (ej. datos que vienen de un formulario web con su ID), tienes que volver a ligarlo a una sesión.
* `session.merge(objeto)`: Copia los datos del objeto separado a un objeto persistente de la sesión actual. Es el estándar seguro.

---

## 4. Delete (Borrar Datos)
Para borrar un registro, necesitas tener su referencia y pasarlo al método `delete()`.

```java
// Usamos load() porque es más eficiente: no necesitamos cargar 
// los datos reales de la BD, solo la referencia (ID) para borrarlo.
Usuario user = session.load(Usuario.class, 1); 
session.delete(user);
```

---

## 5. Gestión de Transacciones (ACID)
Una vez modeladas las entidades y conociendo las operaciones CRUD, debemos asegurar que nuestras modificaciones en la base de datos cumplan con el principio **ACID** (Atomicidad, Consistencia, Aislamiento y Durabilidad).

En Hibernate, cualquier operación de escritura (Create, Update, Delete) **debe ir obligatoriamente envuelta en una transacción**.

```java
Transaction tx = null;
try {
    tx = session.beginTransaction();
    
    // Operaciones CRUD
    session.persist(empleado); // Create
    departamento.setNombre("IT"); // Update (Dirty Checking)
    
    tx.commit(); // Si todo va bien, confirmamos los cambios en SQL
} catch (Exception e) {
    if (tx != null) tx.rollback(); // Si algo falla, deshacemos todo para evitar datos corruptos
    e.printStackTrace();
}
```

---

## 5. Recursos para Profundizar
* [📖 Get vs Load in Hibernate (Baeldung)](https://www.baeldung.com/hibernate-save-persist-update-merge-saveorupdate) - Diferencias clave en profundidad.
* [📖 Hibernate Update vs Merge (Vlad Mihalcea)](https://vladmihalcea.com/jpa-persist-and-merge/) - Guía experta sobre cómo reconectar objetos *Detached*.

---
[◀ Volver: Relaciones y Colecciones](./15-hibernate-relaciones-y-colecciones.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Lenguaje de Consultas (HQL) ▶](./17-hibernate-hql-y-consultas.md)