# Aprender HTML

HTML es la base de todas las páginas web. Sin HTML, no
podría organizar texto o agregar imágenes o videos a sus
páginas web. HTML es el comienzo de todo lo que necesita
saber para crear páginas web atractivas.

Visita [w3schools](https://www.w3schools.com/) para mas
informacion.

## Estructuras.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <h1>Title</h1>
    <p>Paragraph</p>
</body>
</html>
```

```html
<!-- Ésto es un comentario de html -->
<etiqueta atributo="valor">texto</etiqueta>
```

```html
<!-- Ésto es un comentario de html -->
<etiqueta atributo="valor">
```

---

## BEM

La metodología **BEM** que significa (Bloque, Elemento,
Modificador). Es una metodología ágil de desarrollo basada
en componentes. Fue creada por la empresa Yandex para
desarrollar sitios web en poco tiempo y con un soporte de
largo plazo.

Bloque: `header`, `div`, `menu`, `checkbox`, `imput`.

```html
<main>
    <section class="seccion">
        <!-- Bloque contenedor -->
    </section>
</main>
```

Elemento: `manu item`, `list item`, `header title`,
`checkbox caption`.

```html
<main>
    <section class="seccion">
        <h1 class="seccion__titulo">Title</h1>
    </section>
</main>
```

Modificador: `fixed`, `disable`, `size big`, `danger`,
`checked`.

```html
<main>
    <section class="seccion">
        <p class="seccion__parrafo seccion__parrafo--pequeño"></p>
        <p class="seccion__parrafo seccion__parrafo--grande"></p>
    </section>
</main>
```

---

## Atributos & Ordenamiento.

**Clase.**

```html
<div `class="bloque"`>
    <h1>Title 1</h1>
    <p>Paragraph</p>
</div>
```

**Identificacion.**

```html
<div `id="bloque"`>
    <h1>Title 1</h1>
    <p>Paragraph</p>
</div>
```

Los atributos html tienen un orden especifico para facilitar la
lectura del codigo y son las siguientes:

1. `class`
2. `id` , `name`
3. `data-*`
4. `src`, `for`, `type`, `href`, `value`
5. `title`, `alt`
6. `role`, `aria-*`

```html
<a class="..." id="..." data-toggle="modal" href="#">Example link</a>
<input class="form-control" type="text">
<img src="..." alt="...">
```

---

## Etiquetas.

**Title.**

```html
<h1>Title 1</h1>
<h2>Title 2</h2>
<h3>Title 3</h3>
```

**Parrafo.**

```html
<p>Paragraph</p>
```

**Negrilla.**

```html
<b>Bold</b>
```

**Italica.**

```html
<i>Italic</i>
```

**Salto de linea.**

```html
<p>Corresponding label for the `<br>`
line break</p>
```

**Boton.**

```html
<button>Button</button>
```

**Contenedor.**

```html
`<div>`
    <h1>Title 1</h1>
    <p>Paragraph</p>
`</div>`
```

**Enlace.**

```html
<a href="#" target="valor"></a>
```

**Metadato.**

```html
<meta name="valor" content="">
```

**Css.**

```html
<link rel="stylesheet" href="#">
```

**JavaScript.**

```html
<script src="#"></script>
```

---

## Semántica.

**Cabezera.**

```html
<!-- Informacion introductoria o enlaces de navegacion -->

`<header>`
    <h1>Title 1</h1>
    <p>Paragraph</p>
`</header>`
```

**Navegacion.**

```html
`<nav>`
    <ul>
        <li>List item</li>
        <li>List item</li>
        <li>List item</li>
    </ul>
`</nav>`
```

**Principal.**

```html
<!-- Solo debe haber uno por pagina -->

`<main>`
    <h1>Title 1</h1>
    <p>Paragraph</p>
`</main>`
```

**Seccion.**

```html
<!-- Agrupar contenido relacionado tematicamente -->

`<section>`
    <h1>Title 1</h1>
    <p>Paragraph</p>
`</section>`
```

**Articulo.**

```html
<!-- Contenido independiente -->

`<article>`
    <h1>Title 1</h1>
    <p>Paragraph</p>
`</article>`
```

**Lateral.**

```html
`<aside>`
    <h1>Title 1</h1>
    <p>Paragraph</p>
`</aside>`
```

**Pie.**

```html
`<footer>`
    <ul>
        <li>List item</li>
        <li>List item</li>
        <li>List item</li>
    </ul>
`</footer>`
```

---

## Listas.

**Lista desordenada.**

```html
<ul>
    <li>List item</li>
    <li>List item</li>
    <li>List item</li>
</ul>
```

**Lista ordenada.**

```html
<ol>
    <li>List item</li>
    <li>List item</li>
    <li>List item</li>
</ol>
```

---

## Multimedia.

**Imagen.**

```html
<img src="#" alt="descripción obligatoria">
```

**Video.**

```html
<video src="#" controls></video>
```

**Audio.**

```html
<audio src="#" controls></audio>
```

```html
<figure>
  <img src="#" alt="descripción obligatoria">
  <br>
  <figcaption>Tendencia o conclusion</figcaption>
</figure>
```

---

## Formulario.

Se considera buena práctica establecer un atributo `for` en el
elemento `label`, con un valor que coincida con el valor del atributo
`id` del elemento `input`. Esto permite a las tecnologías asistivas
crear una relación vinculada entre la etiqueta y el elemento hijo
`input`.

El atributo `action` en el elemento `form` sirve para enviar datos a
un servidor usando HTML puro.

Cuando se envía un formulario, los datos se envían al servidor e
incluyen entradas para las opciones seleccionadas. Los `inputs` de
tipo `radio` y `checkbox` reportan sus valores desde el atributo
`value`.

Puedes hacer que una casilla de verificación o botón de radio se
marque por defecto usando el atributo `checked`.

El atributo `placeholder` muestra texto provisional en el `input`,
antes de que el usuario haya ingresado nada.

```html
<form action="url/enviodeformulario.php">
  <label for="fName">First name:</label><br>
  <input type="text" name="fName"><br>

  <label for="lName">Last name:</label><br>
  <input type="text" name="lName"><br>

  <input type="text" placeholder="Ingrese su edad"><br>

  <!-- El boton de tipo radio solo permite selecionar una opcion,
  el atributo `name` debe ser igual -->
  <input type="radio" id="estudiante" name="ocupacion" value="estudiante" checked>
  <label for="estudiante">Estudiante</label>
  <input type="radio" id="profesor" name="ocupacion" value="profesor">
  <label for="profesor">Profesor</label>

  <!-- El boton de tipo checkbox permite selecionar varias opcion,
  el atributo `name` debe ser diferente -->
  <input type="checkbox" id="trabajo" name="trabajo" value="trabajo">
  <label for="trabajo">Trabajo</label>
  <input type="checkbox" id="estudio" name="estudio" value="estudio">
  <label for="estudio">Estudio</label>
</form>
```