# ASIX_0373_A00_Apuntes2
Parte 2 de los apuntes

# Introducción a CSS 

## 1. Evolución y Función
**¿Qué es CSS?**
En los orígenes de la web, HTML solo estructuraba texto. Con el crecimiento de la web, se necesitó separar el contenido del diseño.
* **HTML:** Define la estructura y función (vínculos, títulos, párrafos).
* **CSS:** Define la presentación visual (color, espacio, posición).

> **Nota:** CSS no es un lenguaje de programación ni de marcado; es un lenguaje de hojas de estilo.

**Historia y Versiones:**
* **1996:** W3C aprueba **CSS Level 1** (basado en las propuestas CHSS y SSP).
* **1998:** Se publica **CSS Level 2** (revisado en 2008 como CSS2.1).
* **Actualidad:** **CSS3**. Se desarrolla por módulos independientes (algunos ya son estándares, otros en desarrollo).

## 2. Ventajas e Inconvenientes
**Ventajas:**
* **Mantenimiento:** Facilita mantener y editar el código.
* **Potencia:** Ofrece más control de diseño que el HTML puro.
* **Simplicidad:** Es un lenguaje sencillo de aprender.
* **Flexibilidad:** Permite diferentes hojas de estilo para un mismo documento (ej. versión web vs. versión para imprimir).
* **Reutilización:** Una hoja de estilo sirve para múltiples documentos HTML.

**Inconveniente Principal:**
* **Inconsistencia en navegadores:** No todos los navegadores interpretan el CSS igual o cumplen los estándares al 100%, obligando a veces a crear ajustes específicos.

---

## 3. Ubicación: ¿Cómo insertar CSS?
Existen tres formas de aplicar estilos a un documento HTML:

### A. Estilo "Inline" (En línea)
Se aplica directamente en la etiqueta HTML usando el atributo `style`. Tiene prioridad alta pero es difícil de mantener.
```html
<p style="text-align:center; color:red">Párrafo centrado rojo</p>


Se define dentro de la etiqueta <style> en el <head> del documento.

HTML
### Estilo interno
<head>
  <style>
    p {
      text-align: center;
      color: red;
    }
  </style>
</head>

### Estilo externo

Se crea un archivo separado con extensión .css y se vincula en el <head>. Es la mejor opción para reutilizar código. En el HTML:

HTML

<head>
  <link rel="stylesheet" href="estils.css" type="text/css" />
</head>

p {
  text-align: center;
  color: red;
}

HTML

<div id="main" class="box">
    <h1 style="color: green;">Hello</h1>
</div>

h1 { color: blue; }              
.box h1 { color: yellow; }       
#main h1 { color: orange; }     
h1 { color: red !important; }    