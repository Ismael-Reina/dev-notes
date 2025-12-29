# 07. Herramientas y Testing

¿Cómo sabemos si nuestra web es realmente accesible? No basta con mirar el código; hay que probarlo. El testing de accesibilidad combina herramientas automáticas con la insustituible revisión manual.

## 1. Herramientas Automáticas

Son programas que escanean tu código en busca de errores comunes (falta de `alt`, contrastes bajos, etiquetas huérfanas).

> ⚠️ **Advertencia:** Las herramientas automáticas solo detectan el **30-40%** de los problemas. Pueden decirte que una imagen tiene `alt`, pero no si el texto describe bien la imagen. **Nunca confíes solo en ellas.**

### Extensiones de Navegador (Imprescindibles)
* **[WAVE (Web Accessibility Evaluation Tool)](https://wave.webaim.org/extension/)**: Muy visual. Inyecta iconos en tu página marcando errores y alertas. Genial para principiantes.
* **[axe DevTools](https://www.deque.com/axe/devtools/)**: Más técnica y robusta. Es el estándar de la industria. Te da explicaciones detalladas de cómo arreglar cada bug.
* **[Lighthouse](https://developers.google.com/web/tools/lighthouse)**: Viene integrada en las DevTools de Chrome. Te da una puntuación del 0 al 100, útil para informes rápidos.

### En el Código (Linters)
Si usas frameworks como React, Vue o Angular, instala plugins de accesibilidad en tu editor (VS Code) para que te avisen mientras programas.
* **`eslint-plugin-jsx-a11y`**: Te grita en rojo si intentas poner un `onclick` en un `div` o si olvidas un `alt`.

## 2. Pruebas Manuales (El verdadero test)

Aquí es donde realmente encuentras las barreras de uso.

### Navegación solo con Teclado
Olvídate del ratón. Intenta usar tu web solo con el teclado.
1.  ¿Puedes llegar a todos los elementos interactivos con `Tab`?
2.  ¿El orden del foco es lógico?
3.  ¿Siempre ves dónde está el foco (outline)?
4.  ¿Puedes activar botones y enlaces con `Enter` o `Espacio`?
5.  ¿Puedes cerrar modales con `Esc`?

### Lectores de Pantalla (Screen Readers)
No necesitas ser experto, pero debes probar tu web con uno para entender la experiencia "lineal" (escuchar el contenido en orden).

* **Windows:** **NVDA** (Gratuito, muy popular) o **JAWS** (De pago).
* **Mac/iOS:** **VoiceOver** (Viene instalado de serie. `Cmd + F5` para activar).
* **Android:** **TalkBack** (Viene instalado de serie).

**Prueba básica:** Activa el lector, cierra los ojos e intenta navegar por tu menú principal o rellenar tu formulario de contacto.

### Zoom y Reflujo
Aumenta el zoom del navegador al **200%** o **400%**.
* ¿Se solapa el texto?
* ¿Desaparece contenido?
* ¿Aparece una barra de scroll horizontal (lo cual es malo)? El contenido debería reajustarse (reflujo) para leerse en una sola columna vertical.

## Recursos para Auditoría

* **[A11Y Project Checklist](https://www.a11yproject.com/checklist/)**: Una lista de comprobación manual excelente y fácil de seguir.
* **[Accessibility Insights](https://accessibilityinsights.io/)**: Herramienta de Microsoft para auditorías guiadas paso a paso.

---

[◀ Volver: Cognitiva e i18n](./06-cognitiva-e-internacionalizacion.md) | [🏠 Ir al Índice](./README.md)
