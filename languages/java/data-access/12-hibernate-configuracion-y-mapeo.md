# Hibernate: Configuración y Ficheros de Mapeo

Para que Hibernate funcione, necesita dos tipos de información: cómo conectarse a la base de datos (Configuración) y cómo relacionar nuestras clases con las tablas (Mapeo).

---

## 1. El archivo de configuración (`hibernate.cfg.xml`)
Este archivo es el "corazón" de Hibernate. Se coloca habitualmente en la raíz de la carpeta de recursos (`src/main/resources`). En él definimos:
* **Propiedades de conexión:** Driver, URL, usuario y contraseña (similar a JDBC).
* **Dialecto SQL:** Hibernate necesita saber qué "idioma" habla la base de datos (MySQL, Oracle, etc.) para generar el SQL correcto.
* **Pool de conexiones:** Configuración interna o integración con HikariCP.
* **Ficheros de mapeo:** La lista de archivos `.hbm.xml` que debe cargar.

### Ejemplo de `hibernate.cfg.xml`
```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE hibernate-configuration PUBLIC
    "-//Hibernate/Hibernate Configuration DTD 3.0//EN"
    "http://www.hibernate.org/dtd/hibernate-configuration-3.0.dtd">

<hibernate-configuration>
    <session-factory>
        <property name="connection.driver_class">com.mysql.cj.jdbc.Driver</property>
        <property name="connection.url">jdbc:mysql://localhost:3306/mi_db</property>
        <property name="connection.username">root</property>
        <property name="connection.password">1234</property>

        <property name="dialect">org.hibernate.dialect.MySQL8Dialect</property>

        <property name="show_sql">true</property> <property name="format_sql">true</property>

        <mapping resource="com/entidades/Usuario.hbm.xml"/>
    </session-factory>
</hibernate-configuration>
```

---

## 2. El Fichero de Mapeo (`.hbm.xml`)
Es el archivo que explica a Hibernate qué atributo de nuestra clase Java corresponde a qué columna de la tabla SQL. Se suele crear uno por cada clase persistente.

### Estructura básica:
* `<class>`: Define la clase Java y la tabla asociada.
* `<id>`: Define la clave primaria.
* `<property>`: Define el resto de atributos.

### Ejemplo de `Usuario.hbm.xml`
```xml
<hibernate-mapping package="com.entidades">
    <class name="Usuario" table="usuarios">
        <id name="id" column="id_usuario">
            <generator class="native"/> </id>

        <property name="nombre" column="nombre_completo" type="string"/>
        <property name="email" unique="true" not-null="true"/>
    </class>
</hibernate-mapping>
```

---

## 3. Elementos clave del mapeo

### A. Estrategias de generación de IDs (`<generator>`)
* **native:** Elige la mejor opción según la BD (ej. `AUTO_INCREMENT` en MySQL).
* **increment:** Hibernate busca el ID máximo y le suma 1 (útil si la BD no soporta autoincremento).
* **assigned:** El programador debe asignar el ID manualmente antes de guardar.

### B. Tipos de datos
Hibernate tiene sus propios tipos (mapeadores) para asegurar la compatibilidad. Si no se especifica el atributo `type`, Hibernate intenta adivinarlo usando *Reflection*.

---

## 4. Recursos para Profundizar
* [📖 Hibernate Configuration (Official Docs)](https://docs.jboss.org/hibernate/orm/current/userguide/html_single/Hibernate_User_Guide.html#bootstrap) - Guía completa de todas las propiedades configurables.
* [📖 XML Mapping Reference](https://docs.jboss.org/hibernate/orm/3.5/reference/en/html/mapping.html) - Referencia detallada de las etiquetas HBM.
* [📖 Hibernate Dialects List](https://docs.jboss.org/hibernate/orm/current/javadocs/org/hibernate/dialect/package-summary.html) - Lista de dialectos soportados.

---
[◀ Volver: Conceptos de ORM](./11-orm-conceptos-y-herramientas.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Clases Persistentes y Estados del Objeto ▶](./13-hibernate-clases-persistentes-y-estados.md)
