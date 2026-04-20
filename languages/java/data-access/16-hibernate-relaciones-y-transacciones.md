# Hibernate: Relaciones, Colecciones y Transacciones

En el mundo real, los objetos no están aislados. Un "Pedido" pertenece a un "Cliente", y una "Categoría" tiene muchos "Productos". Hibernate gestiona estas asociaciones mediante el mapeo de relaciones y colecciones.

---

## 1. Tipos de Relaciones (Asociaciones)
Las relaciones en Hibernate se definen en los archivos `.hbm.xml` (o anotaciones) reflejando la lógica de la base de datos:

### A. Muchos a Uno (`<many-to-one>`)
Es la más común. Varios objetos de una clase apuntan a uno solo de otra (ej. muchos Empleados en un Departamento).
* En Java: Un atributo del tipo de la clase destino.
* En SQL: Una columna con una Clave Foránea (FK).

### B. Uno a Muchos (`<set>`, `<list>`)
Es la inversa de la anterior. Un objeto tiene una colección de otros (ej. un Departamento tiene una lista de Empleados).
* En Java: Se usan interfaces de colecciones como `Set` o `List`.

---

## 2. El concepto de Cascada (`cascade`)
La cascada define qué debe pasar con los objetos hijos cuando realizamos una acción sobre el objeto padre. Si borras un `Cliente`, ¿quieres que se borren automáticamente todos sus `Pedidos`?

Tipos de cascada más comunes:
* **all:** Todas las operaciones (guardar, borrar, actualizar) se replican en los hijos.
* **save-update:** Solo se replican los guardados y actualizaciones.
* **delete:** Si borras al padre, se borran los hijos.
* **none:** (Por defecto) No se hace nada automáticamente.

```xml
<set name="empleados" cascade="all" inverse="true">
    <key column="id_departamento"/>
    <one-to-many class="com.entidades.Empleado"/>
</set>
```

---

## 3. Carga Perezosa (Lazy) vs Inmediata (Eager)
Al mapear colecciones, Hibernate permite decidir cuándo cargar los datos de la base de datos:
* **lazy="true" (Por defecto):** Hibernate no carga la lista de hijos hasta que realmente la pides en el código (ej. `depto.getEmpleados().size()`). Esto ahorra mucha memoria.
* **lazy="false":** Carga todo el árbol de objetos de golpe con un `JOIN`. Úsalo con cuidado, puede ser muy lento.

---

## 4. Gestión de Transacciones Avanzada
Como vimos en JDBC, las transacciones aseguran que los datos sean consistentes. En Hibernate, siempre debemos envolver las operaciones de escritura en una transacción.

```java
Transaction tx = null;
try {
    tx = session.beginTransaction();
    
    // Operaciones complejas con múltiples objetos
    session.save(objeto1);
    session.update(objeto2);
    
    tx.commit(); // Éxito total
} catch (Exception e) {
    if (tx != null) tx.rollback(); // Error: Volvemos atrás
    e.printStackTrace();
}
```

---

## 5. Recursos para Profundizar
* [📖 Hibernate Association Mappings (Baeldung)](https://www.baeldung.com/hibernate-one-to-many) - Guía completa sobre One-to-Many y Many-to-One.
* [📖 Understanding Cascade Types](https://vladmihalcea.com/a-beginners-guide-to-jpa-and-hibernate-cascade-types/) - Explicación experta sobre cuándo usar cada tipo de cascada.
* [📖 Lazy Loading in Hibernate](https://www.baeldung.com/hibernate-lazy-eager-loading) - Comparativa de rendimiento entre carga perezosa e inmediata.

---
[◀ Volver: HQL y Consultas](./15-hibernate-hql-y-consultas.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Introducción a BDOR (Unidad 4) ▶](./17-introduccion-bdor.md)
