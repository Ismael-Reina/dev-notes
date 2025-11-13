# 02. Instalación de WordPress

Existen dos métodos principales para instalar WordPress: la **automática**, que es rápida y recomendada para principiantes, y la **manual**, que te da un control total sobre el proceso.

## A) Instalación Automática (Recomendada)

Este método simplifica todo el proceso a rellenar un formulario usando una herramienta como **Installatron** (incluida en la mayoría de hostings).

### 1. Acceso al Instalador ⚙️

1.  Inicia sesión en tu **cPanel**.
2.  Busca la sección "Software" > "**Installatron Applications Installer**".
3.  Dentro de Installatron, busca **WordPress** y pulsa el botón "Instalar esta aplicación".

### 2. Configuración de la Instalación 📝

Aparecerá un formulario. Rellena las secciones clave:

**Dominio:**
* **Protocolo:** Elige la opción `https://` (sin `www.`).
* **Dominio:** Selecciona tu dominio principal.
* **Ruta:** **Déjala en blanco** para instalar WordPress en tu dominio principal (ej: `https://tudominio.com`).

**Configuración (Settings):**
* **Nombre de usuario administrador:** Elige uno que **no sea "admin"** por seguridad.
* **Contraseña de administrador:** Crea una contraseña fuerte y segura.
* **Email de administrador:** Introduce un correo electrónico válido para notificaciones.
* **Título del sitio web:** Escribe el nombre de tu web (ej: "Mi Primera Página Web").
* **Lema del sitio web:** Bórralo y déjalo en blanco por ahora.

### 3. Verificación y Acceso al Dashboard ✅

1.  Haz clic en el botón "Instalar" y espera uno o dos minutos.
2.  **Comprobar:** Visita tu dominio (`https://tudominio.com`) para ver la página de bienvenida.
3.  **Acceder:** Para entrar a tu panel de administrador, ve a `https://tudominio.com/wp-admin` e introduce el usuario y contraseña que creaste.

---

## B) Instalación Manual (Control Total)

Este método te da un control absoluto y es la mejor forma de entender cómo funciona WordPress por dentro.

### Fase 1: Preparar los Archivos en el Hosting 📁

1.  **Descargar:** Ve a la web oficial `es.wordpress.org` y descarga el último `.zip` de WordPress.
2.  **Subir archivos:** Tienes dos métodos:

    * **Método A: Administrador de Archivos (cPanel)**
        1.  **Preparar:** Descomprime el `.zip` en tu ordenador. Entra en la carpeta `wordpress` que se ha creado, selecciona **todos los archivos de dentro** y vuelve a comprimirlos en un nuevo `.zip`. (Esto evita que tu web se instale en `tudominio.com/wordpress/`).
        2.  **Subir:** En cPanel > "Administrador de Archivos", ve a la carpeta raíz de tu dominio (normalmente `public_html`).
        3.  **Extraer:** Sube el nuevo `.zip` que creaste, haz clic derecho sobre él y selecciona "Extract".
        4.  **Limpiar:** Borra el `.zip` que subiste.

    * **Método B: Cliente FTP (FileZilla)**
        1.  **Conectar:** Usa tu cliente FTP con los datos de tu hosting (Servidor, Usuario, Contraseña).
        2.  **Subir:** Descomprime el `.zip` de WordPress en tu ordenador. Arrastra **todo el contenido** de la carpeta `wordpress` (no la carpeta en sí) al directorio `public_html` en el servidor.

### Fase 2: Crear la Base de Datos 💾

WordPress necesita una base de datos para almacenar todo (posts, páginas, usuarios, etc.).

1.  **Ir a cPanel:** Busca la sección "Bases de datos" y entra en "**Bases de datos MySQL®**".
2.  **Crear BBDD:** En "Nueva base de datos", pon un nombre (ej: `miweb_wp`) y pulsa "Crear".
3.  **Crear Usuario:** En "Añadir nuevo usuario", crea un nombre de usuario (ej: `miweb_user`) y genera una contraseña fuerte.
4.  **¡Apunta estos 3 datos!**: Nombre de BBDD, Usuario y Contraseña.
5.  **Asignar Usuario:** En "Añadir usuario a la base de datos", selecciona el usuario y la BBDD que acabas de crear y pulsa "Añadir".
6.  **Dar Privilegios:** Marca la casilla "**TODOS LOS PRIVILEGIOS**" y haz clic en "Hacer cambios".

### Fase 3: Ejecutar el Instalador de WordPress 🚀

1.  **Iniciar asistente:** Abre tu navegador y accede a tu dominio (ej: `https://tudominio.com`). Se iniciará el asistente de instalación.
2.  **Configurar BBDD:** Introduce los datos que apuntaste:
    * **Nombre de la base de datos:** `miweb_wp`
    * **Nombre de usuario:** `miweb_user`
    * **Contraseña:** La contraseña que generaste.
    * **Servidor de la base de datos:** Déjalo en `localhost` (suele ser el correcto).
    * **Prefijo de tabla:** Puedes cambiar `wp_` a algo aleatorio (ej: `xyz_`) por seguridad.
3.  **Rellenar Información del Sitio:** Si la conexión a la BBDD es correcta, pasarás a la última pantalla:
    * **Título del sitio:** El nombre de tu web.
    * **Nombre de usuario:** Tu usuario para **acceder a WordPress** (¡No uses "admin"!).
    * **Contraseña:** Tu contraseña para acceder a WordPress.
    * **Tu correo electrónico:** Un email válido para la administración.
4.  **Finalizar:** Haz clic en "Instalar WordPress". ¡Listo!

---

[◀ Volver: Hosting y cPanel](./01-hosting-dominio-cpanel.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Recorrido Dashboard ▶](./03-recorrido-dashboard.md)
