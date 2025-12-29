# 05. Formularios y Componentes Interactivos

Los formularios suelen ser las barreras más grandes en la web. Un formulario inaccesible impide que el usuario se registre, compre o contacte contigo.

## 1. La Regla de Oro: Etiquetas (`<label>`)

Todo `<input>` debe tener una `<label>` asociada programáticamente. No basta con poner texto al lado visualmente.

### Asociación Explícita (Recomendada)
Se usa el atributo `for` en la label y el `id` en el input. Deben coincidir exactamente.

```html
<label for="email">Correo Electrónico:</label>
<input type="email" id="email" name="email">
```

**Beneficios:**
1.  El lector de pantalla lee "Correo Electrónico" cuando el foco llega al input.
2.  Al hacer clic en el texto "Correo Electrónico", el foco se va al input (aumenta el área de clic).

### El problema del `placeholder`
Nunca uses el `placeholder` como sustituto de la etiqueta.
* El `placeholder` desaparece al escribir (problema de memoria a corto plazo).
* Suele tener poco contraste.
* Muchos lectores de pantalla no lo leen.

## 2. Ayuda y Mensajes de Error (`aria-describedby`)

Cuando un input tiene instrucciones extra ("La contraseña debe tener 8 caracteres") o un mensaje de error ("El formato es inválido"), debemos vincular ese texto al input.

Si solo pones un `<div>` debajo, el usuario ciego no sabrá que ese texto existe o que se refiere a ese campo.

```html
<label for="pass">Contraseña</label>
<input type="password" id="pass" aria-describedby="pass-help">
<span id="pass-help">Mínimo 8 caracteres y una mayúscula.</span>
```

Cuando el usuario llegue al input, el lector dirá: *"Contraseña, campo de contraseña. Mínimo 8 caracteres y una mayúscula"*.

## 3. Agrupación de Campos (`<fieldset>`)

Cuando tienes un grupo de opciones relacionadas, como Radio Buttons o Checkboxes, necesitas agruparlas semánticamente.

Si preguntas "¿Color favorito?" y tienes opciones "Rojo" y "Azul", y no las agrupas, el lector solo leerá "Rojo" (sin el contexto de la pregunta).

```html
<fieldset>
  <legend>¿Cuál es tu color favorito?</legend>
  
  <label>
    <input type="radio" name="color" value="rojo"> Rojo
  </label>
  
  <label>
    <input type="radio" name="color" value="azul"> Azul
  </label>
</fieldset>
```

* **`<fieldset>`**: Agrupa los controles.
* **`<legend>`**: Es la "etiqueta" o título del grupo entero.

## 4. Autocompletado (`autocomplete`)

El atributo `autocomplete` ayuda a los navegadores a pre-rellenar datos (nombre, email, tarjeta), lo cual es vital para personas con discapacidades motoras (menos tecleo) y cognitivas (menos esfuerzo de memoria).

```html
<input type="text" autocomplete="given-name">
<input type="email" autocomplete="email">
<input type="tel" autocomplete="tel">
```

## 5. Gestión de Errores

Cuando un formulario falla al enviarse:

1.  **No desactives el botón de envío (Disabled):** Los botones desactivados no son focuseables y confunden al usuario (no sabe por qué no funciona). Es mejor dejar que pulse y mostrarle los errores.
2.  **Foco en el error:** Lleva el foco automáticamente al primer campo con error o al resumen de errores al cargar la página.
3.  **Identificación:** Usa `aria-invalid="true"` en los campos erróneos para que el lector avise de que el dato es incorrecto.

## Recursos

* **[WebAIM: Creating Accessible Forms](https://webaim.org/techniques/forms/)**: Guía detallada sobre formularios.
* **[Inclusive Components](https://inclusive-components.design/)**: Patrones de diseño accesibles para componentes complejos (Tabs, Menús, Toggles).

---

[◀ Volver: Contenido Visual](./04-contenido-visual.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Cognitiva e Internacionalización ▶](./06-cognitiva-e-internacionalizacion.md)
