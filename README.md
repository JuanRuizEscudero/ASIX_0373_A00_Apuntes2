
#  Apuntes de CSS (Cascading Style Sheets)

## 1 Introducción y Evolución
**¿Qué es?**
Es un lenguaje de hojas de estilo (no de programación) utilizado para definir la presentación visual de un documento escrito en HTML.

* **HTML:** Define la **estructura** y función (qué es cada cosa: título, enlace, párrafo).
* **CSS:** Define la **presentación** (cómo se ve: colores, fuentes, espacios).

**Historia:** CSS nació para separar el diseño del contenido.
* **CSS1 (1996):** Primera recomendación oficial del W3C.
**CSS2 (1998) / CSS2.1:** Mejoras y revisiones.
* **CSS3 (Actualidad):** Dividido en módulos independientes.

---

## 2 Sintaxis Básica
Una hoja de estilos es un conjunto de **reglas**. Cada regla indica al navegador cómo mostrar un elemento.

### Estructura de una Regla
```css
/* Esto es un comentario en CSS */
selector {
    propiedad: valor;
}
```

  * **Selector:** Indica a qué elemento HTML afecta la regla (ej. `p`, `h1`).
  * **Declaración:** El bloque dentro de las llaves `{...}`.
      * **Propiedad:** Característica a cambiar (ej. `color`, `font-size`).
      * **Valor:** Ajuste específico (ej. `red`, `12px`).

**Ejemplo:**

```css
p {
    font-size: 10pt;       /* Propiedad: font-size, Valor: 10pt */
    background-color: gray;
}
```

-----

## 3 Ubicación: Formas de aplicar CSS

Existen tres maneras de vincular estilos al HTML.

### A. Estilo Externo (Recomendado)

Se crea un archivo `.css` independiente y se enlaza en el `<head>` del HTML. Permite reutilizar estilos en varias páginas.

```html
<head>
    <link rel="stylesheet" href="estilos.css" type="text/css">
</head>
```

### B. Estilo Interno

Se definen dentro de la etiqueta `<style>` en la cabecera del documento HTML.

```html
<head>
    <style>
        p { color: red; }
    </style>
</head>
```

### C. Estilo Inline (En línea)

Se aplica directamente en la etiqueta HTML. Es difícil de mantener.

```html
<p style="text-align:center; color:red">Texto rojo</p>
```

-----

## 4 Prioridad y Cascada (Especificidad)

Cuando varias reglas afectan al mismo elemento, ¿cuál gana? El navegador decide basándose en un sistema de puntuación (**Especificidad**) y ciertas reglas.

### Tabla de Puntuación

| Tipo de Selector | Puntos | Ejemplo |
| :--- | :--- | :--- |
| **Inline** (en etiqueta) | 1000 | `<div style="...">` |
| **ID** (\#) | 100 | `#header` |
| **Clase** (.), Atributo, Pseudo-clase | 10 | `.menu`, `:hover` |
| **Elemento** (etiqueta), Pseudo-elemento | 1 | `h1`, `div`, `::after` |
| **Universal** (\*) | 0 | `*` |

### Reglas de Conflicto

1.  **Mayor Especificidad:** Gana la regla con más puntos.
2.  **Orden (Cascada):** A igual puntuación, gana la **última** regla escrita en el archivo.
3.  **`!important`:** Esta declaración rompe todas las reglas anteriores. Tiene prioridad absoluta (aunque se recomienda usar poco).

### Ejemplo Resuelto (Priority Check)

```html
<div id="main" class="box">
    <h1 style="color: green;">Hola</h1>
</div>
```

```css
/* CSS */
h1 { color: blue; }
.box h1 { color: yellow; }
#main h1 { color: orange; }
h1 { color: red !important; }
```

  * **Resultado:** El color será **ROJO** debido al `!important`. Sin esa etiqueta, sería Naranja (por el ID), y si no hubiera ID, Verde (por el estilo Inline).

-----

## 5 Ventajas e Inconvenientes

### Ventajas

  * Código más limpio y fácil de mantener.
  * Mayor control visual que el HTML antiguo.
  * **Reutilización:** Una hoja de estilos sirve para muchas páginas.
  * **Flexibilidad:** Se pueden definir estilos distintos para pantalla e impresión.

### Inconvenientes

  * **Compatibilidad:** No todos los navegadores interpretan CSS exactamente igual (aunque ha mejorado, a veces requiere ajustes específicos).
