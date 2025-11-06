# 3. Configuración Esencial del Sistema

Estos pasos son cruciales para asegurar la estabilidad, seguridad y funcionalidad de tu instalación de Linux Mint.

## I. 🛡️ Fase de Preparación y Estabilidad

El primer paso para cualquier instalación nueva de Linux.

Paso | Acción Recomendada | Por qué es importante
--- | --- | ---
**1. Instalar Actualizaciones** | Abrir el `Gestor de Actualizaciones` y aplicar todas las disponibles (o usar `sudo apt update && sudo apt upgrade`). | Mantiene el sistema seguro y estable. ¡Es lo primero que debes hacer!
**2. Configurar Timeshift** | Abrir la aplicación `Timeshift` y configurarla para crear instantáneas (copias de seguridad) del sistema. | Te permite restaurar el sistema a un estado anterior si algo sale mal.
**3. Controladores (Drivers)** | Abrir el `Gestor de Controladores` para buscar e instalar drivers propietarios (NVIDIA/AMD, Wi-Fi). | Garantiza el rendimiento óptimo del hardware.
**4. Códecs Multimedia** | Si no se marcaron durante la instalación, instalarlos (`sudo apt install mint-meta-codecs`). | Para reproducir MP3, MP4, etc.

## II. 💻 Fase de Funcionalidad y Software

Define cómo vas a instalar y gestionar tus aplicaciones.

Elemento | Acción Recomendada | Notas Importantes
--- | --- | ---
**Flatpak** | Utilizar Flathub como fuente principal para aplicaciones de terceros. | Mint tiene soporte completo. Las aplicaciones están aisladas (más seguras). Usa `flatpak install` y visita Flathub.
**Snap (Opcional)** | Habilitar el soporte Snap si necesitas una aplicación específica que solo esté allí. | **Precaución:** Mint lo deshabilita por defecto. Comando para habilitarlo: <br> `sudo rm /etc/apt/preferences.d/nosnap.pref` <br> `sudo apt update && sudo apt install snapd`
**Gestor de Software** | Usar la interfaz gráfica para buscar e instalar aplicaciones comunes. | Es el método más sencillo, ya que combina los repositorios APT y Flathub en una sola interfaz.

## III. Comandos Esenciales de Terminal

Un resumen de los comandos básicos para la gestión del sistema.

Tarea | Comando
--- | ---
Actualizar Sistema | `sudo apt update && sudo apt upgrade`
Limpiar Sistema | `sudo apt autoreme`
Instalar un programa (APT) | `sudo apt install [nombre_paquete]`
Limpiar Flatpak | `flatpak uninstall --unused`
