# React.

React es una biblioteca Javascript de código abierto diseñada para crear interfaces de usuario con el objetivo de facilitar el desarrollo de aplicaciones en una sola página. Es mantenido por Facebook y la comunidad de software libre.

React intenta ayudar a los desarrolladores a construir aplicaciones que usan datos que cambian todo el tiempo. Su objetivo es ser sencillo, declarativo y fácil de combinar. React sólo maneja la interfaz de usuario en una aplicación. En el modelo MVC (Modelo Vista Controlador) React es la Vista.

Visita [reactjs](https://reactjs.org/) o [losapuntesdemajo](https://losapuntesdemajo.now.sh/) para mas informacion.

---

## JSX.

JSX es una extensión de la sintaxis de JavaScript. Recomendamos usarlo con React para describir cómo debería ser la interfaz de usuario. JSX puede recordarte a un lenguaje de plantillas, pero viene con todo el poder de JavaScript.

JSX produce “elementos” de React.

```js
const nombre = 'Alexander Viafara';
const element = <h1>Hola, {name}</h1>;

ReactDOM.render(
    element,
    document.getElementById('root')
);

/* Hola, Alexander Viafara */
```

Puedes poner cualquier expresión de JavaScript dentro de llaves en JSX.

```js
ReactDOM.render(
    <h1>Hola Alexander, {2020 - 1999} años.</h1>,
    document.getElementById('root');
);

/* Hola Alexander, 21 años.*/
```

No pongas comillas rodeando llaves cuando insertes una expresión JavaScript en un atributo. Debes utilizar comillas (para los valores de los strings) o llaves (para las expresiones), pero no ambas en el mismo atributo.

Si una etiqueta está vacía, puedes cerrarla inmediatamente con `/>`, como en XML.

```js
const element = (
    <div>
        <h1>Imagen.</h1>
        <img src={url} />
    </div>
);
```

Babel compila JSX a llamadas de `React.createElement()`. Estos dos ejemplos son idénticos:

```js
const element = (
  <h1 className="greeting">
    Hola, mundo!
  </h1>
);
```

```js
const element = React.createElement(
  'h1',
  {className: 'greeting'},
  'Hola, mundo!'
);
```

---

## Renderizado Elementos.

En nuestro archivo (HTML) siempre habra un `<div>` con un identificador propio para poder manejar el ReactDOM. En este caso el identificador sera `root`.

```html
<div id="root"></div>
```

Para poder renderizar un elemento de React en un nodo raíz del DOM, tenemos que pasa ambos a `ReactDOM.render()`.

```js
ReactDOM.render(
  <h1>Hola, Mundo!</h1>,
  document.getElementById('root')
);
```

Este muestra un titulo con el texto “Hola, Mundo!” en la página.

React DOM compara el elemento y sus hijos con el elemento anterior, y solo aplica las actualizaciones del DOM que son necesarias para que el DOM esté en el estado deseado.

---

## Componentes y Propiedades.

Los componentes permiten separar la interfaz de usuario en piezas independientes, reutilizables y pensar en cada pieza de forma aislada.

La forma más sencilla de definir un componente es escribir una función de JavaScript.

Esta función es un componente de React válido porque acepta un solo argumento de objeto “props” (que proviene de propiedades) con datos y devuelve un elemento de React. Llamamos a dichos componentes “funcionales” porque literalmente son funciones JavaScript.

```js
function Bienvenida (props) {
  return <h1>Hola, {props.nombre}</h1>;
}
```

```js
import React from 'react';

class Bienvenida extends React.Component {
  render() {
    return <h1>Hola, {this.props.nombre}</h1>;
  }
}

export default Bienvenida;
```

---

## Renderizado Componentes.

Los elementos también pueden representar componentes definidos por el usuario.

Cuando React ve un elemento representando un componente definido por el usuario, pasa atributos JSX e hijos a este componente como un solo objeto. Llamamos a este objeto “props”.

```js
function Bienvenida (props) {
  return <h1>Hola, {props.nombre}</h1>;
}

const element = <Bienvenida nombre="Alexander" />;

ReactDOM.render(
  element,
  document.getElementById('root')
);
```

1. Llamamos a ReactDOM.render() con el elemento `<Bienvenida nombre="Alexander" />`.

2. React llama al componente Bienvenida con {nombre: 'Alexander'} como “props”.

3. Nuestro componente Bienvenida devuelve un elemento `<h1>Hola, Alexander</h1>` como resultado.

4. React DOM actualiza eficientemente el DOM para que coincida con `<h1>Hola, Alexander</h1>`.

---

## Estado y Ciclo De Vida.

El estado es similar a las props, pero es privado y está completamente controlado por el componente.

**constructor:** Se utiliza normalmente para inicializar el estado de un componente react `this.state`, o para enlazar manejadores de eventos a una instancia.

**render:** Es el unico metodo requerido para crear un componente de clase.

**componentDidMount:** Este metodo se ejecuta después de que el componente ha sido renderizada en el DOM. No olvides darle de baja en el metodo `componentWillUnmount`.

**componentWillUnmount:** Este metodo se ejecuta inmediatamente antes de destruir un componente. Realizar las tareas de limpieza.

```js
import React, {Component} from 'react';

class Button extends Component {
  constructor() {
    super();
    this.state = boolean;
  }

  render() {
    return(
      <button>Bienvenida</button>
    );
  }

  componentDidMount() {
    ...
  }

  componentWillUnmount() {
    ...
  }
}
```

---

## Create React App

Create React App es un ambiente cómodo para aprender React, y es la mejor manera de comenzar a construir una nueva aplicación de página única usando React.

Create React App configura tu ambiente de desarrollo de forma que puedas usar las últimas características de Javascript, brindando una buena experiencia de desarrollo, y optimizando tu aplicación para producción. Necesitarás tener [node](https://nodejs.org/en/) y [npm](https://www.npmjs.com/) instalados en tu máquina.

Para crear un proyecto ejecuta:

> npx create-react-app my-app
>
> cd my-app
>
> npm start

---

## Buenas Practicas.

1. Identificar los componentes que tiene el sitio web.

2. Crear una carpeta llamada `component` y en ella colocar
cada componente con el archivo jsx y css.

3. Asegurate de que los eventos empiecen por la palabra `handleNombre`, `onChange = handleChange`.