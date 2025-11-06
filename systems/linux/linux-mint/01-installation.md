# 1. Guía de Instalación de Linux Mint

Este documento cubre los pasos esenciales para instalar Linux Mint en tu ordenador. El proceso es gráfico y muy sencillo de seguir.

## Pasos Previos

Antes de empezar, necesitarás:

1.  **Una unidad USB:** De al menos 8 GB.
2.  **La imagen ISO de Linux Mint:** Descárgala desde la [página oficial de Linux Mint](https://linuxmint.com/download.php). Deberás elegir un entorno de escritorio (Cinnamon es el más popular y recomendado).
3.  **Un programa para crear el USB "booteable":**
    * **Rufus:** Una excelente opción para usuarios en Windows.
    * **Etcher:** Muy sencillo de usar y disponible para Windows, macOS y Linux.

## Creación del USB de Instalación

1.  Abre Rufus o Etcher.
2.  Selecciona el archivo ISO de Linux Mint que has descargado.
3.  Selecciona la unidad USB que vas a usar (¡Cuidado! Se borrará todo su contenido).
4.  Inicia el proceso y espera a que termine.

## Proceso de Instalación

1.  **Arrancar desde el USB:** Inserta el USB en el ordenador donde vas a instalar Mint. Reinicia el equipo y accede a la "Boot Menu" (normalmente pulsando F12, F10, F2 o Supr, varía según el fabricante) para seleccionar arrancar desde la unidad USB.

2.  **Iniciar el Entorno "Live":** Verás un menú de arranque (GRUB). Selecciona la opción "Start Linux Mint". El sistema se cargará en un modo "Live", que te permite probarlo directamente desde el USB sin instalar nada.

3.  **Lanzar el Instalador:** En el escritorio del modo Live, haz doble clic en el icono "Install Linux Mint".

4.  **Asistente de Instalación:**
    * **Idioma:** Selecciona "Español".
    * **Disposición del teclado:** Elige "Español" (o la que corresponda a tu teclado).
    * **Códecs multimedia:** Marca la casilla "Instalar códecs multimedia". Esto es muy recomendable para poder reproducir formatos como MP3, MP4 y otros desde el primer momento.
    * **Tipo de instalación:** Este es el paso más importante.
        * **Instalar junto a Windows (Dual Boot):** Si el instalador detecta Windows, te ofrecerá esta opción. Es la más sencilla si quieres conservar ambos sistemas. Podrás elegir el espacio que dedicas a cada uno deslizando una barra.
        * **Borrar disco e instalar Linux Mint:** Esta opción formateará todo el disco duro y solo instalará Mint. **(¡Se borrarán todos tus datos!)**.
        * **Más opciones (Particionado manual):** Para usuarios avanzados. Permite definir manualmente las particiones (como `/`, `/home` y `swap`). Para empezar, no es necesario complicarse con esto.

5.  **Configuración final:**
    * **Zona horaria:** Selecciona tu ubicación (ej. Madrid).
    * **Crear usuario:** Introduce tu nombre, un nombre para el equipo, tu nombre de usuario (ej. `ismael`) y una contraseña.

6.  **Finalizar:** El instalador comenzará a copiar los archivos. Este proceso tardará unos minutos. Una vez termine, te pedirá reiniciar el equipo. Retira el USB cuando te lo indique y... ¡listo! Ya tendrás Linux Mint instalado.

---
🏠 [Ir al Índice](./README.md) | [Siguiente: Personalización 🠒](./02-customization.md)
