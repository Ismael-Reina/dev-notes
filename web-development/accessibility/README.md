# Accesibilidad Web (a11y)

La **Accesibilidad Web** (conocida como **a11y**) es la práctica de crear sitios y aplicaciones que puedan ser utilizados por el mayor número de personas posible, independientemente de sus capacidades físicas, cognitivas o tecnológicas.

No se trata de "hacer un favor" a una minoría, sino de construir una web universal y robusta. Una web accesible es, por definición, una web de mayor calidad técnica.

## ¿Por qué es fundamental?

Más allá de la empatía, hay tres razones pragmáticas para implementar accesibilidad:

1.  **Legalidad:** En muchos países (incluyendo la UE), la accesibilidad es obligatoria por ley para sitios públicos y empresas de cierto tamaño. El incumplimiento puede derivar en multas.
2.  **Negocio (SEO y Alcance):** Google es, en esencia, un usuario ciego que navega con teclado. Si tu web es accesible, posicionará mejor. Además, ignorar la accesibilidad es ignorar a casi el 20% de la población mundial.
3.  **Experiencia de Usuario (UX):** Las mejoras de accesibilidad benefician a todos.
    * *Ejemplo:* Los subtítulos (pensados para sordos) ayudan a quien ve vídeos en el metro sin cascos.
    * *Ejemplo:* El contraste alto ayuda a quien mira el móvil bajo el sol.

## Dimensiones de la Discapacidad

Debemos diseñar pensando en tres contextos, no solo en discapacidades crónicas:

| Tipo | Permanente | Temporal | Situacional |
| :--- | :--- | :--- | :--- |
| **Visual** | Ceguera / Daltonismo | Cataratas / Infección | Reflejo del sol en la pantalla |
| **Motora** | Falta de un brazo / Parálisis | Brazo escayolado | Tener un bebé en brazos |
| **Auditiva** | Sordera total | Otitis / Dolor | Entorno muy ruidoso (bar) |
| **Cognitiva** | Dislexia / Autismo | Fatiga / Estrés | Distracciones / Multitarea |

## El Estándar: WCAG

Las **Web Content Accessibility Guidelines (WCAG)** son la "biblia" técnica que debemos seguir. Se basan en 4 principios (POUR):

1.  **Perceptible:** La información no puede ser invisible a los sentidos del usuario (ej: si no puede ver, debe poder escucharla).
2.  **Operable:** La interfaz debe poder manejarse (ej: si no puede usar ratón, debe funcionar con teclado).
3.  **Comprensible:** El lenguaje y el funcionamiento deben ser claros y predecibles.
4.  **Robusto:** El código debe ser estándar para funcionar en navegadores actuales, futuros y tecnologías de asistencia (lectores de pantalla).

### Niveles de Conformidad

* **Nivel A (Básico):** Lo mínimo para que la web no sea inutilizable. Insuficiente para un producto profesional.
* **Nivel AA (Estándar de Industria):** El objetivo al que debemos apuntar. Es el requerido legalmente en la mayoría de normativas.
* **Nivel AAA (Excelencia):** Requisitos muy estrictos (ej: interpretación en lengua de signos en vídeos). Difícil de implementar en la totalidad de un sitio.

---

[Siguiente: Semántica y Estructura ▶](./01-semantica-y-estructura.md)
