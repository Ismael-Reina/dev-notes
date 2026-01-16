# Estructura de un Programa y Entorno de Desarrollo

## 1. Anatomía de un Programa Java
Todo programa en Java debe estar contenido dentro de una **Clase**. No existe código "suelto" como en Python o JS.

### Estructura Mínima
```java
public class HolaMundo {                            // 1. Definición de la Clase
    public static void main(String[] args) {        // 2. Método Main
        System.out.println("¡Hola, Java!");         // 3. Sentencia
    }
}
```

1.  **Clase (`class`):** Es el contenedor principal. Por convención, debe llamarse igual que el archivo (archivo `HolaMundo.java` -> `class HolaMundo`).
2.  **Método Main (`main`):** Es el punto de entrada. La JVM busca este método específico para empezar a ejecutar el programa.
    * `public`: Accesible desde fuera.
    * `static`: No necesita instanciar la clase para ejecutarse.
    * `void`: No devuelve ningún valor.
3.  **Sentencias:** Las instrucciones que terminan **siempre** en punto y coma (`;`).

---

## 2. La API de Java
Java no viene vacío; trae una biblioteca gigantesca de código prefabricado llamada **API (Application Programming Interface)**.
Está organizada en **Paquetes** (carpetas):

* `java.lang`: Fundamental (String, Math, System). Se importa automáticamente.
* `java.util`: Utilidades (Scanner, Date, ArrayList).
* `java.io`: Entrada y salida de datos (ficheros).

Para usar una clase que no esté en `java.lang`, debemos importarla al inicio:
```java
import java.util.Scanner; // Importamos la clase Scanner para leer teclado
```

---

## 3. El Entorno de Desarrollo (IDE)
Aunque se puede programar con el Bloc de notas y compilar por consola, profesionalmente usamos un **IDE**.

### Funciones Clave de un IDE
1.  **Editor Inteligente:** Colorea sintaxis, autocompleta código (IntelliSense) y avisa de errores en tiempo real.
2.  **Gestión de Proyectos:** Organiza cientos de archivos y librerías.
3.  **Depurador (Debugger):** Permite ejecutar el código línea a línea para encontrar fallos.
4.  **Refactorización:** Permite cambiar el nombre de una variable en todo el proyecto con un clic.

**Los Grandes IDEs:**
* **IntelliJ IDEA:** El estándar actual de la industria. Potente y moderno.
* **Eclipse:** El veterano. Muy usado en empresas tradicionales y administración.
* **NetBeans:** Muy didáctico y ligero, a menudo usado en educación (seguramente lo veas en clase).
* **VS Code:** Editor de texto vitaminado. Con extensiones funciona genial para Java, pero requiere más configuración manual.

---

## 4. Recursos para Profundizar
* [📖 Java API Documentation](https://docs.oracle.com/en/java/javase/17/docs/api/index.html) - El manual de referencia oficial. Acostúmbrate a leerlo.

---
[◀ Volver: Introducción a la Plataforma](./01-introduccion-plataforma.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Variables y Tipos de Datos ▶](./03-variables-y-tipos.md)
