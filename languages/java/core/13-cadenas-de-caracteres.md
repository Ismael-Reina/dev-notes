# Cadenas de Caracteres (Strings)

## 1. La Naturaleza del String
En Java, `String` no es un tipo de dato primitivo, es una **Clase**. Por tanto, cuando creas un texto, estás instanciando un objeto (aunque Java nos permita omitir la palabra `new` por comodidad).

### La Regla de Oro: Inmutabilidad
Los objetos `String` son **inmutables**. Una vez que se crea un `String` en la memoria, **no se puede modificar**. 

Si intentas alterar un String (por ejemplo, pasarlo a mayúsculas o añadirle texto), Java no modifica el original, sino que **crea un String totalmente nuevo** en la memoria y te lo devuelve.

```java
String saludo = "Hola";
saludo.toUpperCase(); // Esto genera un nuevo String "HOLA", pero 'saludo' sigue siendo "Hola"

// Forma correcta de actualizar la variable:
saludo = saludo.toUpperCase(); // Ahora 'saludo' apunta al nuevo objeto "HOLA"
```

---

## 2. Métodos Principales de la Clase String
Al ser un objeto, `String` viene equipado con decenas de métodos muy útiles para manipular texto. 
*(Nota: En Java, los índices de los caracteres empiezan a contar desde el 0).*

| Método | Descripción | Ejemplo (`texto = "Java"`) |
| :--- | :--- | :--- |
| `length()` | Devuelve la cantidad total de caracteres. | `texto.length()` ➔ `4` |
| `charAt(índice)` | Devuelve el carácter exacto en esa posición. | `texto.charAt(1)` ➔ `'a'` |
| `indexOf(texto)` | Devuelve la posición donde empieza un texto (o -1 si no existe). | `texto.indexOf("v")` ➔ `2` |
| `substring(inicio, fin)` | Extrae un trozo del texto. (El índice 'fin' es exclusivo). | `texto.substring(0, 2)` ➔ `"Ja"` |
| `toUpperCase()` | Convierte todo a mayúsculas. | `texto.toUpperCase()` ➔ `"JAVA"` |
| `toLowerCase()` | Convierte todo a minúsculas. | `texto.toLowerCase()` ➔ `"java"` |
| `trim()` | Elimina los espacios en blanco al principio y al final. | `"  Java  ".trim()` ➔ `"Java"` |
| `replace(viejo, nuevo)`| Sustituye caracteres o palabras enteras. | `texto.replace("a", "o")` ➔ `"Jovo"` |

---

## 3. Comparación de Strings
Como vimos en la unidad anterior, **nunca debes usar `==` para comparar el contenido de dos Strings**.

```java
String a = "DAM";
String b = new String("DAM");

System.out.println(a == b); // FALSE (Memoria distinta)

// 1. Comparación exacta:
System.out.println(a.equals(b)); // TRUE (Contenido idéntico)

// 2. Comparación ignorando mayúsculas/minúsculas:
System.out.println(a.equalsIgnoreCase("dam")); // TRUE
```

---

## 4. Eficiencia: String vs StringBuilder
Dado que los Strings son inmutables, concatenar (unir) textos dentro de un bucle grande usando el operador `+` es un desastre para el rendimiento, ya que crea miles de objetos "basura" en la memoria en cada vuelta.

Para solucionar esto, Java ofrece `StringBuilder`, que es como un String pero **mutable** (se puede modificar internamente sin crear objetos nuevos).

```java
// MAL RENDIMIENTO (Crea 1000 objetos String inútiles)
String textoFinal = "";
for (int i = 0; i < 1000; i++) {
    textoFinal += i; 
}

// BUEN RENDIMIENTO (Modifica el mismo objeto)
StringBuilder sb = new StringBuilder();
for (int i = 0; i < 1000; i++) {
    sb.append(i); 
}
String resultado = sb.toString(); // Al final lo convertimos a String
```

---

## 5. Recursos para Profundizar
* [📖 Documentación Oficial: Clase String (Oracle)](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/String.html) - Lista completa de todos los métodos disponibles.
* [📖 Java Strings (W3Schools)](https://www.w3schools.com/java/java_strings.asp) - Ejemplos rápidos y prácticos.
* [📖 Baeldung: StringBuilder vs StringBuffer](https://www.baeldung.com/java-string-builder-string-buffer) - Artículo técnico sobre las diferencias de rendimiento.

---
[◀ Volver: Excepciones](./12-excepciones.md) | [🏠 Ir al Índice](./README.md) | [Siguiente: Arrays Unidimensionales ▶](./14-arrays-unidimensionales.md)
