# Aprender CSS

Sin CSS, cada página web sería un texto simple e imágenes
que fluyeran directamente hacia abajo en la página. Con CSS
,puede agregar color e imágenes de fondo y cambiar el
diseño de su página: ¡sus páginas web pueden sentirse como
obras de arte!

Visita [w3schools](https://www.w3schools.com/) o [losapuntesdemajo](https://losapuntesdemajo.now.sh/) para mas
informacion.

## Estructuras.

```css
/* Variables de css */
:root {
    --nombre: valor;
}
```

```css
/* Ésto es un comentario de css */
selector {
    propiedad: valor;
}
```

---

## Selectores.

**Universal.**

```css
* {
    propiedad: valor;
}
```

**Identificacion.**

```css
#nombre {
    color: var(nombre);
}
```

**Clase.**

```css
.nombre {
    color: var(nombre);
}
```

**Etiqueta.**

```css
body {
    color: var(nombre);
}
```

---

## Propiedades Frecuentes & Ordenamiento.

```css
body {
    weight: valor;
    height: valor;
    margin: valor;
    border: valor tipo color;
    padding: valor;
    background-color: valor;
    font-size: valor;
    font-family: valor;
    font-weight: valor;
    letter-spacing: valor;
    color: valor;
    text-align: valor;
    text-decoration: valor;
    box-sizing: valor;
    background-size: valor;
    background-repeat: valor;
    background-image: url();
    background-position: valor valor;
    background-attachment: valor;
    transform: translate(x, y);
}
```

Las propiedades css se agrupan en diferentes categorías, las cuales
son las siguientes:

1. Posicionamiento
2. Modelo de caja
3. Tipografía y texto
4. Visual
5. Miscelánea

El posicionamiento es lo primero porque puede sacar un elemento del
flujo normal del documento y anular los estilos relacionados con el
modelo de caja. Las propiedades que tienen que ver con animaciones y
transiciones se colocan en la parte final.

```css
.property__order {
    /* Positioning */
    position: absolute;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    z-index: 100;

    /* Display & Box-model */
    display: block;
    float: right;
    width: 100px;
    height: 100px;

    /* Typography */
    font: normal 13px "Helvetica Neue", sans-serif;
    line-height: 1.5;
    color: #333;
    text-align: center;

    /* Visual */
    background-color: #f5f5f5;
    border: 1px solid #e5e5e5;
    border-radius: 3px;

    /* Misc */
    opacity: 1;
    transition: all 1s linear;
    animation: move 10s linear infinite;
}
```

---

## Unidades.

**Absolutas**

```css
.container {
    weight: 1px;
    weight: 1pt;
}
```

**Relativas**

```css
/*
Rem significa root element y es la unidad recomendada
(px/medidaRoot = rem).
Em significa element y es relativa a la medida del padre
directo (px/medidaPadre = em).
*/

.container {
    weight: 1rem;
    weight: 1em;
    height: 1%;
    weight: 1vw;
    height: 1vh;
}
```

---

## Display y Posiciones.

**Display.**

La propiedad `display` determina el tipo de bloque de
renderizado de un elemento. Los valores más comunes para
esta propiedad son: `inline`, `block`, `inline-block`, `none`.

A los elementos en linea no se puede ajustar manualmente su
ancho o alto. El valor `none` sirve para ocultar los elementos.

```css
.container {
    display: valor;
}
```

**Posiciones.**

La propiedad `position` especifica el tipo de método de
posicionamiento utilizado para un elemento y son: `estátic`
, `relative`, `fixed`, `absolute`, `sticky`.

El valor `relative` desplaza el elemento hacia la posicion
dada, concervando el espacio del mismo.

El valor `absolute` desplaza el elemento hacia la posicion
dada, sin concervar el espacio del mismo.

```css
.container {
    position: valor;
    top: valor;
    right: valor;
    bottom: valor;
    left: valor;
}
```

---

## Modelo Caja.

Todos los elementos HTML se pueden considerar como cuadros.
En CSS, el término "modelo de caja" se usa cuando se habla
de diseño y maquetación.

El modelo de caja CSS es esencialmente una caja que
envuelve cada elemento HTML. Consiste en: márgenes, bordes,
relleno y el contenido real. La siguiente imagen ilustra
el modelo de caja.

![Box Model](./src/boxModel.png)

```css
.container {
    /* margin: auto; Centrado horizontal en una caja */
    margin: valor;
    border: valor tipo color;
    padding: valor;
    width: valor;
    height: valor;
}
```

---

## Transiciones y Animaciones.

**Transicion**

```css
transition-property: propiedad;
transition-duration: duración;
transition: propiedad duración;
```

**Animacion**

```css
@keyframes nombre {
    from {
        /* Codigo. */
    } to {
         /* Codigo. */
    }
}
```

```css
@keyframes nombre {
    0% {
        /* Codigo. */
    } 50% {
        /* Codigo. */
    } 100% {
        /* Codigo. */
    }
}
```

```css
animation-name: nombre;
animation-duration: duración;
animation-iteration-count: cantidad;
animation-direction: valor;
```

---

## Flexbox.

Flexbox tiene como objetivo proporcionar una forma más
eficiente de diseñar, alinear y distribuir el espacio entre
los elementos en un contenedor, incluso cuando su tamaño es
desconocido y / o dinámico.

Visita [css-tricks](https://css-tricks.com/snippets/css/a-guide-to-flexbox/) para mas informacion.

**Flex Container**

![Flex Container](./src/containerFlex.svg)

```css
.container {
    display: Flex;
    flex-direction: valor;
    flex-wrap: valor;
    flex-flow: [<'flex-direction'> <'flex-wrap'>];
    justify-content: valor;
    align-items: valor;
    align-content: valor;
}
```

**Flex Items**

![Flex Items](./src/itemFlex.svg)

```css
.items {
    order: valor;
    flex-grow: valor;
    flex-shrink: valor;
    flex-basis: valor;
    flex: [<'flex-grow'> <'flex-shrink'> || <'flex-basis'>]
    align-self: valor;
}
```

---

## Grid.

CSS Grid Layout (también conocido como "Grid"), es un
sistema de diseño bidimensional basado en cuadrículas cuyo
objetivo es nada menos que cambiar completamente la forma
en que diseñamos interfaces de usuario basadas en
cuadrículas.

Vista [css-tricks](https://css-tricks.com/snippets/css/complete-guide-grid/) para mas informacion.

**Grid Container**

![Grid Container](./src/containerGrid.svg)

```css
.items {
    /* repeat (auto-fill | auto-fit, minmax(mínimo, maximo)).
    La funcion minmax() se refiere a el minimo ancho de una
    columna o fila y al maximo de la misma. El valor auto-fill
    permite insertar filas y columnas automaticamente. El
    valor auto-fit es igual que auto-fill, la unica diferencia
    es que auto-fill sigue insertando columnas o filas ya sea
    el caso y auto-fit las estira. */

    display: grid;
    grid-template-rows: [first] 40px [line2] 50% [line3] auto [line4] 1fr;
    grid-template-columns: repeat(cantidad, medida);
    grid-row-gap: medida;
    grid-column-gap: medida;
    gap: <grid-row-gap> <grid-column-gap>;
    grid-template-areas:
        'header header header'
        'main . sidebar'
        'footer footer footer';
}
```

**Grid Items**

![Grid Item](./src/itemGrid.svg)

```css
.items {
    grid-column: <start-line> / <end-line>;
    grid-row: <start-line> / <end-line>;
    grid-area: <start-row> / <start-column> / <end-row> / <end-column>;
    grid-area: nombre;
}
```

---

## Responsive Design: Mobile First.

El `min-width` ejecuta el codigo de `@media` superior o igual
a los pixeles proporcionados, y el `max-width` ejecuta el codigo
de `@media` inferior o igual a los pixeles proporcionados.

```css
@media mediatype and (expresión) {
    /* Codigo css; */
}
```

```css
@media screen and (min-width: 480px) {
    .items {
        color: valor;
        margin: valor;
    }
}
```

**Mediatype:**

* All
* Print
* Screen
* Speech

 **Media Query:**

* Mobile: 640px min.
* Tablet: 768px min.
* Laptop: 1024px min.
* Desktop: 1280px min.
* Large Desktop: 1536px min.

## Buenas Practicas.

1. Planificar antes de codificar, es recomendable dibujar el contorno
de la pagina con los diferentes elementos (HTML).

2. Recomendamos utilizar la extencion (CSS) Css Grid Overlay.

3. Utilizar el inspector de elementos.

4. Crear diseños adaptable (Responsive Design) en archivos diferentes.

5. Crear temas de colores (Light/Dark) en un archivo independiente.

6. Ordenar alfabeticamente las propiedades de css.
