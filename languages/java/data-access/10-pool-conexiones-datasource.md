# Pool de Conexiones y DataSource

En aplicaciones profesionales, abrir y cerrar una conexión con la base de datos es una operación **costosa y lenta**. El Pool de Conexiones es la solución técnica para optimizar este rendimiento.

---

## 1. El concepto de Connection Pool
Un **Pool de Conexiones** es un depósito o "piscina" de conexiones a la base de datos que ya están abiertas y listas para ser usadas.

* **Sin Pool:** Tu aplicación pide conexión -> La BD negocia el acceso -> Se usa -> Se cierra. (Repetir esto 1000 veces por segundo tumba el servidor).
* **Con Pool:** La aplicación pide conexión -> El Pool le presta una que ya está abierta -> Se usa -> Se devuelve al Pool (no se cierra).

---

## 2. La interfaz DataSource
Aunque podemos configurar el pool a mano, Java ofrece la interfaz `javax.sql.DataSource` como un estándar para obtener conexiones. Es preferible a `DriverManager` porque permite configurar el pool de forma transparente al código.

---

## 3. Implementaciones Populares
Java no trae un pool nativo avanzado, por lo que usamos librerías de terceros:
* **HikariCP:** El más rápido y el estándar actual (usado por Spring Boot).
* **Apache DBCP:** Muy maduro y configurable.
* **C3P0:** Un clásico con muchas opciones de recuperación de errores.

---

## 4. Ejemplo con HikariCP
Para usarlo, necesitamos la dependencia en nuestro proyecto y configurar el objeto `HikariDataSource`.

```java
import com.zaxxer.hikari.HikariConfig;
import com.zaxxer.hikari.HikariDataSource;
import java.sql.Connection;
import java.sql.SQLException;

public class PoolConexiones {
    private static HikariDataSource dataSource;

    static {
        HikariConfig config = new HikariConfig();
        config.setJdbcUrl("jdbc:mysql://localhost:3306/mi_db");
        config.setUsername("user");
        config.setPassword("pass");
        
        // Configuración del Pool
        config.setMaximumPoolSize(10); // Máximo 10 conexiones simultáneas
        config.setIdleTimeout(30000);   // Tiempo para cerrar conexiones inactivas
        
        dataSource = new HikariDataSource(config);
    }

    public static Connection getConnection() throws SQLException {
        return dataSource.getConnection(); // Obtiene una conexión libre del pool
    }
}
```

---

## 5. Recursos para Profundizar
* [📖 HikariCP GitHub](https://github.com/brettwooldridge/HikariCP) - Documentación oficial del pool más rápido.
* [📖 Guide to HikariCP (Baeldung)](https://www.baeldung.com/hikaricp) - Configuración paso a paso.

---
[◀ Volver: Transacciones y Metadatos](./09-jdbc-transacciones-metadatos.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Mapeo Objeto Relacional (ORM) y JPA ▶](./11-orm-conceptos-y-configuracion.md)
