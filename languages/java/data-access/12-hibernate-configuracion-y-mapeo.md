# Hibernate: Configuración y Mapeo Clásico (XML)

Para que Hibernate funcione, necesita saber dos cosas fundamentales: **dónde está la base de datos** (Configuración) y **cómo se relacionan nuestras clases con las tablas** (Mapeo). 

En este capítulo veremos la configuración esencial y daremos un repaso rápido a la forma clásica de mapeo (basada en XML), que hoy en día se considera *Legacy* (obsoleta) pero que aún se enseña en entornos académicos.

---

## 1. El archivo de configuración (`hibernate.cfg.xml`)
Este archivo es el "corazón" de Hibernate en aplicaciones Java SE. Suele colocarse en la raíz de la carpeta de recursos (`src/main/resources`). Aquí definimos las credenciales, el dialecto y registramos las entidades.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE hibernate-configuration PUBLIC
    "-//Hibernate/Hibernate Configuration DTD 3.0//EN"
    "http://www.hibernate.org/dtd/hibernate-configuration-3.0.dtd">

<hibernate-configuration>
    <session-factory>
        <!-- 1. Propiedades de conexión (JDBC) -->
        <property name="connection.driver_class">com.mysql.cj.jdbc.Driver</property>
        <property name="connection.url">jdbc:mysql://localhost:3306/mi_db</property>
        <property name="connection.username">root</property>
        <property name="connection.password">1234</property>

        <!-- 2. Dialecto SQL (Crucial para que Hibernate traduzca correctamente) -->
        <property name="dialect">org.hibernate.dialect.MySQL8Dialect</property>

        <!-- 3. Propiedades de desarrollo -->
        <property name="show_sql">true</property> <!-- Muestra el SQL generado en consola -->
        <property name="format_sql">true</property> <!-- Formatea el SQL para leerlo mejor -->

        <!-- 4. Registro de Clases / Mapeos -->
        <mapping class="com.quizmael.model.User"/> <!-- Forma moderna -->
        <!-- <mapping resource="com/entidades/Usuario.hbm.xml"/> Forma clásica -->
    </session-factory>
</hibernate-configuration>
```

---

## 2. El Mapeo Clásico (`.hbm.xml`) - *LEGACY*
⚠️ **Aviso:** *Esta es la forma antigua de trabajar. Ya no se utiliza en la industria moderna, pero es probable que te la exijan en temarios oficiales antiguos.*

Antiguamente, para mantener las clases Java completamente "limpias" (sin dependencias de Hibernate), se creaba un archivo XML paralelo por cada clase. Este archivo actuaba como un diccionario.

### Estructura básica de un `.hbm.xml`:
* `<class>`: Asocia la clase Java con el nombre de la tabla SQL.
* `<id>`: Define qué atributo es la Clave Primaria (PK) y cómo se genera (`<generator>`).
* `<property>`: Asocia un atributo normal con una columna de la base de datos.

```xml
<hibernate-mapping package="com.entidades">
    <class name="Usuario" table="usuarios">
        <!-- Clave Primaria -->
        <id name="id" column="user_id">
            <generator class="native"/> <!-- Delega el autoincremento a la BD -->
        </id>

        <!-- Atributos normales -->
        <property name="nombre" column="nombre_completo" type="string"/>
        <property name="email" unique="true" not-null="true"/>
    </class>
</hibernate-mapping>
```

---

## 3. La Transición al Mapeo Moderno
Mantener decenas de archivos `.hbm.xml` sincronizados con el código Java era un infierno de mantenimiento. Por ello, la comunidad Java adoptó el uso de **Anotaciones JPA** directamente en el código Java. En el siguiente capítulo veremos este estándar, que es el que utilizarás en la vida real.

---

## 4. Recursos Adicionales
* [📖 Hibernate Configuration (Official Docs)](https://docs.jboss.org/hibernate/orm/current/userguide/html_single/Hibernate_User_Guide.html#bootstrap) - Guía completa de propiedades del `hibernate.cfg.xml`.
* [📖 Legacy XML Mapping](https://docs.jboss.org/hibernate/orm/3.5/reference/en/html/mapping.html) - Documentación antigua sobre las etiquetas HBM.
* [📖 Hibernate Dialects List](https://docs.jboss.org/hibernate/orm/current/javadocs/org/hibernate/dialect/package-summary.html) - Lista de dialectos soportados.

---
[◀ Volver: Conceptos de ORM](./11-orm-conceptos-y-herramientas.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Anotaciones JPA ▶](./13-hibernate-anotaciones-jpa.md)

