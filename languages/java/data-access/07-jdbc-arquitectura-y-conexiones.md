# JDBC: Arquitectura, Conectores y Conexiones

## 1. ¿Qué es JDBC?
**JDBC (Java Database Connectivity)** es una API estándar de Java que permite a las aplicaciones conectarse a bases de datos relacionales, ejecutar sentencias SQL y procesar los resultados. 

Su gran ventaja es la **abstracción**: gracias a JDBC, el código Java que escribes para consultar una base de datos MySQL es prácticamente idéntico al que usarías para una base de datos Oracle o PostgreSQL.

---

## 2. La Arquitectura de JDBC
JDBC funciona como una "capa intermedia" entre tu código y el servidor de base de datos. Se compone de dos partes principales:
1.  **JDBC API:** Un conjunto de interfaces estándar (`Connection`, `Statement`, `ResultSet`) que vienen integradas en el JDK (paquetes `java.sql` y `javax.sql`).
2.  **JDBC Driver:** Es el "traductor" específico para cada base de datos. No viene con Java; debes descargarlo (normalmente como una dependencia Maven/JAR) del fabricante de la base de datos.

---

## 3. El Driver (Conector)
Para que Java pueda hablar con una base de datos, necesita el archivo `.jar` del conector.
* **MySQL:** `mysql-connector-j`
* **PostgreSQL:** `postgresql`
* **Oracle:** `ojdbc`

Antiguamente era necesario registrar el driver manualmente con `Class.forName()`, pero desde JDBC 4.0 (Java 6), los drivers se cargan automáticamente si están en el *classpath*.

---

## 4. Estableciendo la Conexión
Para conectarnos, necesitamos tres elementos fundamentales:
1.  **URL de conexión:** Sigue el formato `jdbc:subprotocolo:nombre_base_datos`.
2.  **Usuario.**
3.  **Contraseña.**

### Ejemplo de Conexión (Patrón Try-with-resources)
```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;

public class ConexionJDBC {
    // Ejemplo de URL para MySQL: jdbc:mysql://host:puerto/nombre_bd
    private static final String URL = "jdbc:mysql://localhost:3306/mi_empresa";
    private static final String USER = "root";
    private static final String PASS = "1234";

    public static void main(String[] args) {
        // Usamos try-with-resources para asegurar que la conexión se cierre sola
        try (Connection con = DriverManager.getConnection(URL, USER, PASS)) {
            
            if (con != null) {
                System.out.println("¡Conexión establecida con éxito!");
            }

        } catch (SQLException e) {
            System.err.println("Error al conectar: " + e.getMessage());
            System.err.println("Código de error SQL: " + e.getErrorCode());
        }
    }
}
```

---

## 5. Anatomía de la URL de Conexión
La URL de conexión es la "dirección postal" que usa el `DriverManager` para saber a qué servidor llamar y qué driver utilizar.

| Base de Datos | Formato de URL |
| :--- | :--- |
| **MySQL** | `jdbc:mysql://[host][:puerto]/[base_datos]` |
| **PostgreSQL** | `jdbc:postgresql://[host][:puerto]/[base_datos]` |
| **SQLite (Fichero)** | `jdbc:sqlite:[ruta_al_archivo.db]` |
| **Oracle** | `jdbc:oracle:thin:@[host]:[puerto]:[SID]` |

---

## 6. Recursos para Profundizar
* [📖 JDBC Overview (Oracle Docs)](https://docs.oracle.com/javase/8/docs/technotes/guides/jdbc/) - Introducción técnica a la arquitectura JDBC.
* [📖 Introduction to JDBC (Baeldung)](https://www.baeldung.com/java-jdbc) - Guía práctica para configurar conexiones y drivers.
* [📖 MySQL Connector/J Documentation](https://dev.mysql.com/doc/connector-j/en/) - Documentación oficial para conectar Java con MySQL.

---
[◀ Volver: Ficheros Avanzados (NIO.2)](./06-ficheros-avanzados-nio2-y-acceso-aleatorio.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Operaciones CRUD y Sentencias SQL ▶](./08-jdbc-operaciones-crud.md)
