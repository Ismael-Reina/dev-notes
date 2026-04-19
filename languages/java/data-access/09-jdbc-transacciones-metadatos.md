# JDBC: Transacciones y Metadatos

En este capítulo exploraremos cómo asegurar que un conjunto de operaciones se realice de forma atómica y cómo obtener información sobre la estructura de la base de datos sin conocerla de antemano.

---

## 1. Gestión de Transacciones
Una **transacción** es una unidad de trabajo que debe cumplir con las propiedades **ACID** (Atomicidad, Consistencia, Aislamiento y Durabilidad). En JDBC, por defecto, cada sentencia SQL se ejecuta y se guarda automáticamente (*Auto-commit*).

Para gestionar transacciones manualmente y asegurar que varias operaciones "triunfen o fallen juntas" (como una transferencia bancaria), seguimos estos pasos:

1.  **Desactivar Auto-commit:** `conexion.setAutoCommit(false);`
2.  **Ejecutar operaciones:** Lanzar los `executeUpdate()`.
3.  **Confirmar cambios:** `conexion.commit();` si todo fue bien.
4.  **Deshacer cambios:** `conexion.rollback();` dentro del bloque `catch`.

### Ejemplo de Transacción
```java
try {
    conexion.setAutoCommit(false); // Iniciamos transacción

    // Operación 1: Restar dinero
    pstmt1.executeUpdate();
    
    // Operación 2: Sumar dinero
    pstmt2.executeUpdate();

    conexion.commit(); // Si llegamos aquí, guardamos todo
    System.out.println("Transacción completada con éxito.");

} catch (SQLException e) {
    conexion.rollback(); // Si algo falla, volvemos al estado inicial
    System.err.println("Error en la transacción. Se ha hecho rollback.");
} finally {
    conexion.setAutoCommit(true); // Restauramos el comportamiento por defecto
}
```

---

## 2. Metadatos (Metadata)
Los metadatos son "datos sobre los datos". JDBC nos permite obtener información técnica sobre la base de datos o sobre los resultados de una consulta.

### A. DatabaseMetaData
Proporciona información general sobre el motor de la base de datos, las tablas existentes, columnas, versiones, etc.

```java
DatabaseMetaData dbmd = conexion.getMetaData();

System.out.println("Motor: " + dbmd.getDatabaseProductName());
System.out.println("Versión: " + dbmd.getDatabaseProductVersion());

// Listar todas las tablas de la base de datos
ResultSet rs = dbmd.getTables(null, null, null, new String[]{"TABLE"});
while (rs.next()) {
    System.out.println("Tabla encontrada: " + rs.getString("TABLE_NAME"));
}
```

### B. ResultSetMetaData
Es extremadamente útil para aplicaciones dinámicas. Permite saber cuántas columnas tiene un `ResultSet` y cómo se llaman, sin ver el código SQL.

```java
ResultSet rs = pstmt.executeQuery("SELECT * FROM usuarios");
ResultSetMetaData rsmd = rs.getMetaData();

int numColumnas = rsmd.getColumnCount();
for (int i = 1; i <= numColumnas; i++) {
    System.out.println("Columna " + i + ": " + rsmd.getColumnName(i) + 
                       " (Tipo: " + rsmd.getColumnTypeName(i) + ")");
}
```

---

## 3. Recursos para Profundizar
* [📖 JDBC Transactions (Oracle Docs)](https://docs.oracle.com/javase/tutorial/jdbc/basics/transactions.html) - Guía detallada sobre niveles de aislamiento y commit.
* [📖 Using Metadata in JDBC (Baeldung)](https://www.baeldung.com/jdbc-database-metadata) - Cómo inspeccionar bases de datos de forma dinámica.
* [📖 JDBC Metadata Interface](https://docs.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html) - Referencia oficial de métodos de metadatos.

---
[◀ Volver: Operaciones CRUD y SQL](./08-jdbc-operaciones-crud.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Mapeo Objeto Relacional (ORM) y JPA ▶](./10-orm-conceptos-y-configuracion.md)
