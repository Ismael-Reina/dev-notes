# JDBC: Operaciones CRUD y Sentencias SQL

Una vez establecida la conexión, el siguiente paso es interactuar con la base de datos. En JDBC, esto se hace mediante objetos que representan sentencias SQL.

---

## 1. Statement vs. PreparedStatement
Existen dos formas principales de enviar comandos SQL a la base de datos:

### A. Statement (No recomendado para datos variables)
Se usa para sentencias SQL estáticas y sencillas. 
* **Riesgo:** Es vulnerable a **Inyección SQL** si concatenas variables directamente en la cadena de texto.

### B. PreparedStatement (El estándar profesional)
La sentencia se pre-compila en la base de datos. Los valores se pasan mediante parámetros (`?`).
* **Seguridad:** Evita la inyección SQL automáticamente.
* **Rendimiento:** Es más eficiente si se ejecuta la misma sentencia varias veces con distintos datos.

---

## 2. Ejecución de actualizaciones (INSERT, UPDATE, DELETE)
Para cualquier operación que modifique datos (DML) o estructura (DDL), utilizamos el método `executeUpdate()`. Este devuelve un `int` con el número de filas afectadas.

```java
String sql = "INSERT INTO usuarios (nombre, email) VALUES (?, ?)";

try (PreparedStatement pstmt = conexion.prepareStatement(sql)) {
    pstmt.setString(1, "Ismael");
    pstmt.setString(2, "ismael@ejemplo.com");
    
    int filasAfectadas = pstmt.executeUpdate();
    System.out.println("Filas insertadas: " + filasAfectadas);
} catch (SQLException e) {
    e.printStackTrace();
}
```

---

## 3. Consulta de datos (SELECT) y el ResultSet
Para leer datos, utilizamos `executeQuery()`, que devuelve un objeto **ResultSet**. El ResultSet es un cursor que apunta a las filas de la tabla resultante.

* `rs.next()`: Mueve el cursor a la siguiente fila. Devuelve `false` cuando no hay más.
* `rs.getTipo(columna)`: Recupera el valor de una columna de la fila actual.

```java
String sql = "SELECT id, nombre, email FROM usuarios";

try (PreparedStatement pstmt = conexion.prepareStatement(sql);
     ResultSet rs = pstmt.executeQuery()) {
    
    while (rs.next()) {
        int id = rs.getInt("id");
        String nombre = rs.getString("nombre");
        String email = rs.getString("email");
        
        System.out.println(id + " | " + nombre + " | " + email);
    }
} catch (SQLException e) {
    e.printStackTrace();
}
```

---

## 4. Ejemplo Completo: Operación CRUD
```java
public void actualizarEmail(int id, String nuevoEmail) {
    String sql = "UPDATE usuarios SET email = ? WHERE id = ?";
    
    try (PreparedStatement pstmt = conexion.prepareStatement(sql)) {
        pstmt.setString(1, nuevoEmail);
        pstmt.setInt(2, id);
        
        if (pstmt.executeUpdate() > 0) {
            System.out.println("Usuario actualizado correctamente.");
        }
    } catch (SQLException e) {
        e.printStackTrace();
    }
}
```

---

## 5. Recursos para Profundizar
* [📖 Java Database Queries (Baeldung)](https://www.baeldung.com/java-jdbc-queries) - Diferencias profundas entre Statement y PreparedStatement.
* [📖 JDBC ResultSet Tutorial (Oracle Docs)](https://docs.oracle.com/javase/tutorial/jdbc/basics/retrieving.html) - Cómo navegar por resultados complejos.
* [📖 SQL Injection Prevention (OWASP)](https://cheatsheetseries.owasp.org/cheatsheets/SQL_Injection_Prevention_Cheat_Sheet.html) - Por qué PreparedStatement es vital para la seguridad.

---
[◀ Volver: Arquitectura y Conexiones](./07-jdbc-arquitectura-y-conexiones.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Gestión de Transacciones y Metadatos ▶](./09-jdbc-transacciones-metadatos.md)
