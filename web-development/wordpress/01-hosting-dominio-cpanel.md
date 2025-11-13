# 01. Hosting, Dominio y cPanel

Antes de instalar WordPress, necesitas dos cosas fundamentales: un **dominio** y un **hosting**. **cPanel** es la herramienta más común para gestionar ambos.

## ¿Qué es un Dominio?

Es el nombre único de tu sitio web (ej. `ismael-reina.com`). Es la dirección que la gente escribe en el navegador para encontrarte. Los dominios se registran (se "alquilan") anualmente.

## ¿Qué es un Hosting?

Si el dominio es la dirección, el hosting (o alojamiento) es el "terreno" y la "casa" donde viven los archivos y la base de datos de tu web. Es un ordenador (servidor) conectado a Internet 24/7.

**¿Cuándo se necesitan?** Siempre que quieras que tu sitio web sea público y accesible para todo el mundo.

---

## ¿Qué es cPanel?

cPanel es el panel de control estándar de la industria para la administración de alojamientos web (hosting). Su objetivo es simplificar la gestión de tu servidor y sitio web a través de una interfaz visual amigable, sin necesidad de ejecutar comandos complejos.

### Estructura de la Interfaz

La interfaz de cPanel se organiza de manera clara:

* **Sección Central:** El corazón de cPanel. Aquí se agrupan todas las herramientas de gestión por categorías.
* **Columna Derecha:** Un panel con información general y estadísticas vitales de tu hosting (uso de disco, versión de PHP, etc.).

### Herramientas de Gestión Principales

Estas son las secciones más importantes que utilizarás para gestionar tu instalación de WordPress:

#### 🗂️ Archivos

* **Administrador de archivos:** Una herramienta visual para navegar, cargar, editar y eliminar los archivos de tu hosting, similar al explorador de archivos de tu ordenador. Aquí es donde residirán los archivos de WordPress.
* **Cuentas FTP:** Te permite crear usuarios para acceder a tus archivos mediante programas como FileZilla, útil para subir o bajar grandes cantidades de archivos.
* **JetBackup 5 (o similar):** Herramienta crucial para la gestión de **copias de seguridad**. Permite crear y restaurar copias de tus archivos y bases de datos.

#### 💾 Bases de Datos

WordPress almacena todo su contenido en una base de datos.

* **Bases de datos MySQL®:** Un asistente para crear nuevas bases de datos y asignarles usuarios. Es un paso necesario si realizas una instalación manual de WordPress.
* **phpMyAdmin:** Herramienta para interactuar *directamente* con el contenido de tus bases de datos. La usarás muy pocas veces, pero es fundamental saber que existe.

#### 🌐 Dominios

* **Dominios:** Aquí puedes añadir los dominios y subdominios que hayas registrado para asociarlos a tu plan de hosting y que muestren tu sitio web.

#### ⚙️ Software y Aplicaciones

* **Installatron (o Softaculous):** Es un **instalador automático** de aplicaciones. Con unos pocos clics, puedes instalar WordPress sin tener que subir archivos ni crear la base de datos manualmente.
* **Seleccionar Versión de PHP:** Te permite elegir la versión de PHP que ejecutará tu sitio web. Es muy importante para la seguridad y el rendimiento.

#### 📬 Email

* **Cuentas de Email:** Para crear y administrar direcciones de correo con tu propio dominio (ej. `contacto@tuweb.com`).

---

[◀ Volver: Índice](./README.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Instalación ▶](./02-instalacion.md)
