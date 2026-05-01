# Hibernate: Clases Persistentes y Estados del Objeto

En Hibernate no guardamos filas, guardamos objetos. Pero para que Hibernate pueda coger un objeto de Java y meterlo en una base de datos, ese objeto tiene que cumplir unas normas y pasa por un "ciclo de vida" muy estricto.

---

## 1. Clases Persistentes (POJOs)
Una clase persistente es simplemente una clase normal de Java (un POJO: *Plain Old Java Object*) que ha sido mapeada a una tabla en la base de datos. 

Sin embargo, Hibernate exige **cuatro reglas de oro** para que una clase pueda ser gestionada correctamente:

1.  **Constructor por defecto (obligatorio):** La clase debe tener un constructor sin argumentos (puede ser `protected` o `public`). Hibernate lo usa para instanciar objetos automáticamente mediante *Reflection*.
2.  **Propiedad Identificadora (obligatorio):** Debe tener un atributo mapeado como clave primaria (`<id>`).
3.  **Métodos Getter y Setter (recomendado):** Hibernate necesita acceder a los atributos. Aunque puede acceder directamente a las variables de instancia, usar *getters* y *setters* es el estándar.
4.  **No ser `final` (recomendado):** Si haces la clase `final`, Hibernate no podrá usar un mecanismo llamado *Lazy Loading* (carga perezosa) porque no podrá crear clases "Proxy" que hereden de ella.

### Ejemplo de POJO válido:
```java
package com.entidades;

public class Usuario {
    private int id; // Identificador
    private String nombre;

    // 1. Constructor vacío (Obligatorio)
    public Usuario() {}

    // Constructor útil para el programador
    public Usuario(String nombre) {
        this.nombre = nombre;
    }

    // 2. Getters y Setters
    public int getId() { return id; }
    public void setId(int id) { this.id = id; }
    
    public String getNombre() { return nombre; }
    public void setNombre(String nombre) { this.nombre = nombre; }
}
```

---

## 2. SessionFactory y Session
Para interactuar con la base de datos, Hibernate utiliza dos objetos principales:

* **`SessionFactory` (La Fábrica):** Es un objeto muy pesado que se crea **una sola vez** al arrancar la aplicación. Lee el `hibernate.cfg.xml`, crea el pool de conexiones y se guarda en memoria. Es *Thread-Safe* (seguro para múltiples hilos).
* **`Session` (La Sesión):** Es un objeto muy ligero que representa **una unidad de trabajo** con la base de datos (como una conexión JDBC). Se abre, se usa para guardar/leer cosas, y se cierra inmediatamente. **No** es *Thread-Safe*.

---

## 3. El Ciclo de Vida del Objeto (Los 4 Estados)
Esto es el núcleo de Hibernate. Un objeto mapeado puede estar en uno de estos 4 estados dependiendo de su relación con una `Session` abierta.

### 1. Transient (Transitorio)
El objeto acaba de ser creado con el operador `new`. 
* **Características:** No tiene asignado un `id` (suele valer 0 o nulo) y Hibernate no sabe que existe. Si apagas el programa, el objeto se borra de la RAM y se pierde.

### 2. Persistent (Persistente)
El objeto ha sido asociado a una `Session` abierta (usando `save()`, `persist()` o recuperándolo con `get()`).
* **Características:** Tiene un `id` asignado. **Hibernate está vigilando este objeto**. Cualquier cambio que hagas en sus atributos mediante un *setter*, Hibernate lo detectará y lanzará un `UPDATE` automático en la base de datos sin que tú se lo pidas.

### 3. Detached (Separado / Desligado)
El objeto era persistente, pero **la `Session` se ha cerrado** (o se ha vaciado con `clear()`).
* **Características:** El objeto sigue teniendo su `id` y sigue existiendo en la RAM, pero **Hibernate ya no lo vigila**. Si haces un *setter*, la base de datos no se enterará. Se puede volver a ligar a una nueva sesión usando el método `update()` o `merge()`.

### 4. Removed (Eliminado)
Se ha llamado al método `delete()` pasando el objeto.
* **Características:** Sigue existiendo en la RAM de Java, pero está marcado para ser borrado físicamente de la tabla cuando se confirme la transacción (*commit*).

---

## 4. Ejemplo del Ciclo de Vida en Código

```java
// 1. Estado TRANSIENT (Transitorio)
Usuario user = new Usuario("Ismael"); 
// 'user' no está en la BD, no tiene ID válido.

Session session = sessionFactory.openSession();
session.beginTransaction();

// 2. Pasa a estado PERSISTENT (Persistente)
session.save(user); 
// Ahora 'user' tiene ID. Hibernate lo está vigilando.
user.setNombre("Ismael Actualizado"); // ¡Hibernate hará un UPDATE automático aquí!

session.getTransaction().commit();
session.close();

// 3. Pasa a estado DETACHED (Separado)
// La sesión se ha cerrado. Hibernate ya no mira al objeto.
user.setNombre("Ismael Olvidado"); // Este cambio NO se guarda en la base de datos.
```

---

## 5. Recursos para Profundizar
* [📖 Hibernate Entity State Transitions (Vlad Mihalcea)](https://vladmihalcea.com/a-beginners-guide-to-jpa-hibernate-entity-state-transitions/) - El mejor artículo en internet sobre los estados de Hibernate, escrito por un desarrollador core de Hibernate.
* [📖 Baeldung: Hibernate Lifecycle](https://www.baeldung.com/hibernate-entity-lifecycle) - Ejemplos prácticos de cada estado y los métodos que provocan las transiciones.

---
[◀ Volver: Configuración y Mapeo Clásico](./12-hibernate-configuracion-y-mapeo-clasico.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Anotaciones JPA ▶](./14-hibernate-anotaciones-jpa.md)
