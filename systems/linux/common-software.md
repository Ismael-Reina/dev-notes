# Aplicaciones y Juegos Comunes en Linux

Aquí tienes una guía del software más interesante y utilizado, las mejores herramientas para programación y los videojuegos más populares para Linux.

## Índice

1. [Software Esencial y de Uso General](#1-software-esencial-y-de-uso-general)
2. [Las Mejores Aplicaciones para Programadores](#2-las-mejores-aplicaciones-para-programadores)
3. [Videojuegos Populares en Linux](#3-videojuegos-populares-en-linux)

---

## I. 💻 Software Esencial y de Uso General

Estas aplicaciones son ampliamente utilizadas en casi cualquier distribución de Linux.

### 🌐 Navegación y Comunicación

| Categoría | Aplicación | Descripción | Formato Común |
| :--- | :--- | :--- | :--- |
| **Navegador** | **Mozilla Firefox** | El navegador de código abierto por excelencia. Suele venir preinstalado. | Repositorio (APT) |
| **Navegador (Alternativa)** | **Google Chrome** (o **Chromium**)| Chrome es popular por su sincronización; Chromium es la versión 100% de código abierto. | DEB (Chrome) / Repositorio (Chromium) |
| **Ofimática** | **LibreOffice** | La suite ofimática más utilizada. Incluye Writer (Word), Calc (Excel) e Impress (PowerPoint). | Repositorio (APT) |

### 🎨 Multimedia y Diseño

| Categoría | Aplicación | Descripción | Formato Común |
| :--- | :--- | :--- | :--- |
| **Reproductor de Video**| **VLC Media Player** | El reproductor universal que maneja prácticamente cualquier formato de audio y video. | Repositorio / Flatpak |
| **Edición de Imagen** | **GIMP** (GNU Image Manipulation Program) | Un potente editor de gráficos *raster* (mapa de bits), considerado el "Photoshop de código abierto". | Repositorio / Flatpak |
| **Gráficos Vectoriales**| **Inkscape** | Un editor de gráficos vectoriales profesional, ideal para logotipos, ilustraciones y diseño web. | Repositorio / Flatpak |
| **Edición de Audio** | **Audacity** | Editor y grabador de audio muy popular para podcasts y música. | Repositorio / Flatpak |

### ⚙️ Herramientas del Sistema

| Categoría | Aplicación | Descripción | Formato Común |
| :--- | :--- | :--- | :--- |
| **Limpieza** | **BleachBit** | Herramienta para liberar espacio y eliminar archivos temporales y caché del sistema. | Repositorio / Flatpak |
| **Particiones** | **GParted** | Herramienta gráfica imprescindible para crear, redimensionar y formatear particiones de disco. | Repositorio (APT) |
| **Virtualización** | **VirtualBox** o **GNOME Boxes** | Permite ejecutar otros sistemas operativos (como Windows o versiones de Linux) dentro de tu sistema. | Repositorio / DEB |

---

## II. 👨‍💻 Las Mejores Aplicaciones para Programadores

Linux es el sistema operativo preferido por muchos desarrolladores, y estas son las herramientas clave:

### 📝 Editores de Código e IDEs (Entornos de Desarrollo Integrado)

| Aplicación | Tipo | Características Principales |
| :--- | :--- | :--- |
| **Visual Studio Code (VS Code)** | Editor / IDE ligero | El más popular. Multiplataforma, muy extensible mediante *plugins* y ligero. Soporte excelente para casi cualquier lenguaje. |
| **IntelliJ IDEA / PyCharm / WebStorm** | IDEs Completos | Suites profesionales de **JetBrains**. PyCharm para Python, WebStorm para JavaScript/Web, e IDEA para Java/Kotlin. Ofrecen versiones *Community* gratuitas. |
| **Vim / Neovim y Emacs** | Editores de Terminal | Editores legendarios basados en terminal. Requieren una curva de aprendizaje, pero ofrecen una velocidad y eficiencia inigualables para desarrolladores experimentados. |
| **Sublime Text** | Editor de Código Rápido | De pago, pero con una versión de evaluación perpetua. Conocido por su velocidad y potente sistema de selección múltiple. |

### 🗃️ Herramientas de Desarrollo

* **Git:** El sistema de control de versiones estándar. Se usa intensamente desde la terminal.
* **Terminales Avanzadas (Terminators):** Herramientas como **Terminator** o **Tilix** permiten dividir la ventana de la terminal en múltiples paneles para ver *logs* y ejecutar comandos simultáneamente.
* **Docker:** La herramienta estándar de contenedores. Es fundamental para asegurar que las aplicaciones se ejecuten igual en cualquier entorno.
* **Lenguajes Comunes:** La mayoría de las distribuciones ya traen instalados o facilitan la instalación de **Python**, **Node.js** y los compiladores **GCC** (para C/C++).

---

## III. 🎮 Videojuegos Populares en Linux

El *gaming* en Linux ha mejorado drásticamente gracias a herramientas de compatibilidad y el auge de **Steam**.

### 1. Juegos Nativos y de Código Abierto

* **Juegos Nativos:** Muchos títulos importantes de estudios como **Valve** (ej. *Counter-Strike 2, Dota 2, Team Fortress 2, Half-Life 2, Portal 2*) tienen versiones nativas para Linux.
* **0 A.D.:** Un juego de estrategia en tiempo real de código abierto (similar a *Age of Empires*).
* **SuperTuxKart:** Un divertido juego de carreras de karts de código abierto (similar a *Mario Kart*).
* **The Battle for Wesnoth:** Un juego de estrategia por turnos de fantasía de código abierto.

### 2. La Clave de la Compatibilidad: Steam y Proton

La mayoría de los juegos de Windows ahora se pueden jugar en Linux gracias a **Steam** y la herramienta **Proton** (una capa de compatibilidad de Valve):

| Plataforma/Herramienta | Descripción |
| :--- | :--- |
| **Steam** | El cliente de juegos imprescindible. Asegúrate de instalarlo. |
| **Proton** | Herramienta que usa Steam para ejecutar juegos de Windows. Activa la opción **Steam Play** en los ajustes de Steam para acceder a miles de títulos. |
| **Heroic Games Launcher** | Un lanzador de juegos que permite gestionar juegos de **Epic Games Store** y **GOG** en Linux usando Proton. |

### 3. Títulos Populares Jugables con Proton (No nativos de Linux)

La lista es casi infinita, pero estos son algunos ejemplos de juegos populares con excelente rendimiento en Linux:

* **RPG/Aventura:** *Elden Ring, God of War, Cyberpunk 2077, The Witcher 3, Horizon Zero Dawn.*
* **Estrategia:** *Stardew Valley, Cities: Skylines, Factorio, Crusader Kings III.*
* **Multijugador:** *Apex Legends, Rocket League, Destiny 2.*

**Recomendación:** Para verificar si un juego funciona bien en Linux con Proton, visita la web [ProtonDB](https://www.protondb.com/), donde la comunidad califica y ofrece consejos de configuración.
