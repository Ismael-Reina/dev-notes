# Hibernate: Lenguaje de Consultas (HQL) y SQL Nativo

Los métodos `get()` y `load()` son perfectos si conoces la Clave Primaria. Pero, ¿qué pasa si quieres buscar a un usuario por su email o sacar una lista de todos los usuarios de una ciudad? Para búsquedas complejas, necesitamos un lenguaje de consultas.

---

## 1. ¿Qué es HQL?
**HQL (Hibernate Query Language)** es un lenguaje de consultas orientado a objetos. Su sintaxis es casi idéntica a SQL, pero con una diferencia radical: **HQL no entiende de tablas ni de columnas, solo entiende de Clases y Atributos de Java.**

* **SQL:** `SELECT * FROM usuarios WHERE correo = 'a@a.com'`
* **HQL:** `FROM Usuario u WHERE u.email = 'a@a.com'`

La inmensa ventaja de HQL es que es **independiente de la base de datos**. Tú escribes HQL, y el Dialecto de Hibernate lo traduce automáticamente al SQL específico de MySQL, Oracle o la base de datos que estés usando en ese momento.

---

## 2. Ejecutar consultas HQL
Para ejecutar una consulta, creamos un objeto `Query` a partir de la sesión.

### A. Consultar una lista de objetos (`list()`)
Para obtener múltiples resultados usamos el método `list()`.

```java
session.beginTransaction();

// Fíjate que "Usuario" es el nombre de la CLASE (con mayúscula), no de la tabla.
String hql = "FROM Usuario"; 
Query<Usuario> query = session.createQuery(hql, Usuario.class);

List<Usuario> listaUsuarios = query.list();

for (Usuario u : listaUsuarios) {
    System.out.println(u.getNombre());
}

session.getTransaction().commit();
```

### B. Consultar un único resultado (`uniqueResult()`)
Si tu consulta busca por un campo único (ej. un email), usamos `uniqueResult()`. Lanza excepción si hay más de un resultado.

```java
String hql = "FROM Usuario u WHERE u.email = 'admin@empresa.com'";
Query<Usuario> query = session.createQuery(hql, Usuario.class);

Usuario admin = query.uniqueResult();
```

### C. Funciones de Agregación
HQL soporta perfectamente las operaciones matemáticas clásicas (`count()`, `sum()`, `avg()`, `max()`, `min()`). El resultado suele ser un tipo numérico primitivo o su *Wrapper* (`Long`, `Double`), no un objeto de tu clase.

```java
// Contar cuántos usuarios hay en total
String hql = "SELECT count(u) FROM Usuario u";
Query<Long> query = session.createQuery(hql, Long.class);

Long totalUsuarios = query.uniqueResult();
System.out.println("Total de usuarios: " + totalUsuarios);
```

---

## 3. Uso de Parámetros (Evitar Inyección SQL)
Al igual que en JDBC usábamos `PreparedStatement` con `?`, en HQL usamos **parámetros nombrados**. Esto hace el código muchísimo más legible y seguro.

```java
// Los parámetros empiezan por dos puntos (:)
String hql = "FROM Usuario u WHERE u.ciudad = :ciudadBuscada AND u.edad > :edadMinima";
Query<Usuario> query = session.createQuery(hql, Usuario.class);

// Asignamos los valores a los parámetros
query.setParameter("ciudadBuscada", "Madrid");
query.setParameter("edadMinima", 18);

List<Usuario> adultosMadrid = query.list();
```

---

## 4. Paginación de Resultados
Si tienes 1 millón de usuarios, hacer `FROM Usuario` colapsará la memoria RAM de tu servidor. En SQL puro, paginar es un infierno porque cada base de datos lo hace distinto (`LIMIT` en MySQL, `ROWNUM` en Oracle). **En HQL, son dos líneas de código universales:**

```java
String hql = "FROM Usuario u ORDER BY u.nombre ASC";
Query<Usuario> query = session.createQuery(hql, Usuario.class);

// Empezar a leer desde el registro 0 (el primero)
query.setFirstResult(0); 

// Leer como máximo 10 registros
query.setMaxResults(10); 

List<Usuario> primeraPagina = query.list();
```

---

## 5. SQL Nativo (El último recurso)
A veces, necesitas hacer una consulta súper compleja usando funciones matemáticas muy específicas de tu motor que HQL no soporta. Para esos casos, Hibernate te permite saltarte las reglas y ejecutar SQL puro usando `createNativeQuery()`.

```java
// Aquí SÍ usamos el nombre de la tabla y las columnas
String sqlPuro = "SELECT * FROM usuarios WHERE DATEDIFF(NOW(), fecha_registro) > 30";
Query<Usuario> query = session.createNativeQuery(sqlPuro, Usuario.class);

List<Usuario> usuariosAntiguos = query.list();
```
> **Aviso:** Abusar del SQL Nativo rompe la independencia de la base de datos. Solo úsalo cuando HQL se quede corto.

---

## 6. Recursos para Profundizar
* [📖 Hibernate Query Language Reference](https://docs.jboss.org/hibernate/orm/current/userguide/html_single/Hibernate_User_Guide.html#hql) - La biblia de HQL oficial de JBoss/Hibernate.
* [📖 Baeldung: Hibernate Aggregate Functions](https://www.baeldung.com/hibernate-aggregate-functions) - Guía práctica sobre cómo usar `count()`, `sum()`, `avg()`, etc., en HQL.

---
[◀ Volver: HQL y Consultas](./15-hibernate-hql-y-consultas.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Introducción a BDOR (Unidad 4) ▶](./17-introduccion-a-las-bdor-y-bdoo.md)
