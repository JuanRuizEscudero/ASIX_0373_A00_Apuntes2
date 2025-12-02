
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

27/11/2025

## 1 Estructura y Sintaxis de una Regla CSS

CSS (Cascading Style Sheets) es un conjunto de reglas que definen la estética final de los documentos (X)HTML.

### Anatomía de una Regla

Cada regla CSS se compone de dos partes fundamentales:

1.  **Selector:** Define a qué elemento o elementos HTML queremos aplicar los estilos.
2.  **Bloque de Declaraciones:** Contiene las instrucciones de estilo.

Una **declaración** individual siempre sigue la estructura: `propiedad: valor;`.

#### Desglose Explicativo

Tomando como ejemplo la siguiente regla:

```css
p {
    font-size: 10pt;
    background-color: gray;
}
```

  * **`p` (Selector):** Indica que esta regla afectará a todos los párrafos (`<p>`) del documento.
  * **Declaración 1:**
      * `font-size` (Propiedad): Qué característica vamos a cambiar (tamaño de fuente).
      * `10pt` (Valor): Cómo vamos a cambiarla.
  * **Declaración 2:**
      * `background-color` (Propiedad): Color de fondo.
      * `gray` (Valor): El color específico.

-----

## 2 Tipos de Selectores Básicos

### Selector de Elementos (o de Tipo)

Selecciona todos los elementos que coincidan con el nombre de la etiqueta HTML en la página.

  * **Ejemplo:**
    ```css
    /* Afecta a TODOS los enlaces <a> del documento HTML */
    a {
        color: red;
    }
    ```

### Selector de ID

Selecciona un elemento único que tenga un atributo `id` específico. El atributo `id` debe ser único en toda la página para distinguir un elemento de forma inequívoca.

  * **Sintaxis:** Se usa el símbolo almohadilla (`#`).
  * **Ejemplo:**
    ```css
    #example {
        property: value;
    }
    ```
    Esto afectaría únicamente al elemento: `<p id="example">`.

-----

## 3 Selectores Avanzados

### Selector Universal

Sirve para seleccionar **todos** los elementos de la página sin excepción. Es útil para "resetear" estilos globales.

  * **Sintaxis:** Se usa el asterisco (`*`).
  * **Ejemplo:**
    ```css
    * {
        border: 1px solid #000000;
    }
    ```
    *Resultado:* Todos los elementos del HTML tendrán un borde sólido negro de 1 píxel.

### Selectores de Atributos

Permiten seleccionar elementos basándose en si tienen un atributo o en el valor exacto de ese atributo.

1.  **Por presencia de atributo:**

    ```css
    img[alt] { ... }
    ```

    Selecciona todas las imágenes `<img>` que tengan definido el atributo `alt`, sin importar su contenido.

2.  **Por valor exacto:**

    ```css
    img[src="alert.gif"] { ... }
    ```

    Es más específico. Solo selecciona la imagen cuyo origen (`src`) sea exactamente "alert.gif".

*Nota:* CSS3 permite selecciones aún más avanzadas (cadenas de texto al principio, final o en cualquier punto del valor).

### Selectores de Relación (Jerarquía)

Es crucial entender la diferencia entre **hijos** y **descendientes**.

#### A. Selectores de Hijos (`>`)

Seleccionan elementos que son **hijos DIRECTOS** de otro elemento. No afecta a nietos ni niveles inferiores.

  * **Ejemplo:** `div > em` seleccionará un `<em>` solo si está inmediatamente dentro de un `<div>`.
  * **Uso avanzado (`:nth-child`):** Podemos seleccionar un hijo específico por su orden numérico.
    ```css
    .parent :nth-child(4) { color: red; }
    ```
    Esto aplicaría estilo al **cuarto hijo directo** del elemento con clase `.parent`, sin importar qué tipo de etiqueta sea ese cuarto hijo.

#### B. Selectores de Descendientes (espacio)

Seleccionan elementos indicados en **CUALQUIER PUNTO** de la jerarquía dentro del elemento padre (hijos, nietos, bisnietos...).

  * **Sintaxis:** Se separan los selectores con un espacio.
  * **Ejemplo:** `div em` selecciona cualquier `<em>` que esté dentro de un `<div>`, aunque esté metido dentro de otro párrafo o etiqueta intermedia.

#### Comparativa Visual: Hijos vs Descendientes

  * `div > em`: Solo afecta al `<em>` si el HTML es `<div><em>Hola</em></div>`.
  * `div em`: Afecta al `<em>` en `<div><p><em>Hola</em></p></div>` (aquí el `>` fallaría porque el `em` es hijo de `p`, no de `div` directamente).

#### C. Selectores de Hermanos Adyacentes (`+`)

Seleccionan un elemento que aparece **DIRECTAMENTE DESPUÉS** de otro, compartiendo el mismo padre.

  * **Ejemplo:**
    ```css
    h1 + h2 { margin-top: -5mm; }
    ```
    Esto busca un `<h2>` que esté inmediatamente después de un `<h1>`. Es muy útil para ajustar espacios entre títulos consecutivos.

-----

## 4 Pseudoclases y Pseudoelementos

### Pseudoclases (Estados)

No definen estilos para el elemento en sí, sino para sus diversos **estados**. Son muy comunes en enlaces.

  * `:link`: Estado normal por defecto (no visitado).
  * `:visited`: Enlace que ya ha sido visitado por el navegador.
  * `:focus`: Cuando el elemento tiene el "foco" (ej: un input donde se está escribiendo o un enlace seleccionado con teclado).
  * `:hover`: Cuando el puntero del ratón pasa por encima del elemento.

### Pseudoelementos (Partes concretas)

Permiten estilizar una **parte específica** del elemento, no el elemento entero.

  * **Ejemplo:** `::first-line`

    ```css
    p::first-line { color: red; }
    ```

    Solo la **primera línea** del párrafo será roja.

  * **Sintaxis (`:` vs `::`):**

      * Navegadores antiguos usaban dos puntos simples (`:`).
      * CSS3 introduce los dos puntos dobles (`::`) para distinguir visualmente los *pseudoelementos* de las *pseudoclases*. Los navegadores modernos soportan ambos, pero se recomienda `::` para pseudoelementos.

-----

## 5 Tutorial: Cómo implementar Google Fonts

Las tipografías web permiten usar fuentes que el usuario no tiene instaladas en su ordenador. Google Fonts es el servicio más popular para esto.

### Paso 1: Entender el funcionamiento

No puedes simplemente poner el nombre de una fuente cualquiera en tu CSS si el usuario no la tiene instalada. Debes "llamarla" desde un servidor externo (en este caso, Google).

### Paso 2: Seleccionar la fuente

1.  Ve a [fonts.google.com](https://fonts.google.com/).
2.  Busca la tipografía que te guste.
3.  Haz clic en ella para ver los detalles.

### Paso 3: El "Carrito" de estilos

Dentro de la página de la fuente, verás diferentes grosores (Light, Regular, Bold, etc.).

1.  Haz clic en **"Select this style"** (o el icono de `+`) al lado de cada variante que necesites.
2.  Esto las añadirá a una barra lateral o icono de "bolsa de la compra".

### Paso 4: Obtener el código (Embed)

Una vez seleccionadas tus fuentes, busca la opción **"Get embed code"** o "Use on the web" en el panel lateral. Google te dará dos opciones de código:

  * **Opción A (HTML - `<link>`):** Se pone en el `<head>` de tu HTML. Es lo más común.
    ```html
    <link href="https://fonts.googleapis.com/css2?family=Roboto&display=swap" rel="stylesheet">
    ```
  * **Opción B (CSS - `@import`):** Se pone al inicio de tu archivo CSS.

### Paso 5: Aplicar en CSS

En el mismo panel de Google Fonts donde obtuviste el código, verás las **"CSS rules to specify families"**. Copia esa línea y úsala en tu selector.

**Ejemplo final de implementación:**

```css
/* En tu archivo CSS */
body {
    /* Aquí aplicas la fuente que acabas de importar */
    font-family: 'Roboto', sans-serif;
}
```