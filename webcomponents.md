# Web Components.

Los elementos personalizados o en ingles (Custom Elements) proporcionan a los autores una forma de crear sus propios elementos DOM con todas las funciones. Aunque los autores siempre pueden usar elementos no estándar en sus documentos, con el comportamiento específico de la aplicación agregado después del hecho mediante secuencias de comandos o similar, históricamente dichos elementos han sido no conformes y no muy funcionales. Al definir un elemento personalizado, los autores pueden informar al analizador cómo construir correctamente un elemento y cómo los elementos de esa clase deben reaccionar a los cambios.

Los elementos personalizados son parte de un esfuerzo mayor para "racionalizar la plataforma", al explicar las características de la plataforma existente (como los elementos de HTML) en términos de puntos de extensibilidad de nivel inferior expuestos por el autor (como la definición de elementos personalizados). Aunque hoy en día existen muchas limitaciones en las capacidades de los elementos personalizados, tanto funcional como semánticamente, que les impiden explicar completamente el comportamiento de los elementos existentes de HTML, esperamos reducir esta brecha con el tiempo.

## Custom Elements.

Los elementos personalizados brindan a los desarrolladores la capacidad de extender HTML y crear sus propias etiquetas. Dado que los elementos personalizados se basan en estándares, se benefician del modelo de componentes integrado de la Web. El resultado es un código más modular que se puede reutilizar en muchos contextos diferentes.

El `customElements` se usa para definir un elemento personalizado y notificar al navegador sobre una nueva etiqueta. Llama a `customElements.define()` con el nombre de etiqueta que desees crear y una class JavaScript que extienda el HTMLElement básico. El `customElements` debe incluir un nombre con guión o el navegador se quejará de que tiene un nombre de elemento no válido.

### LifeCycle

**constructor:** Es útil para inicializar el estado, configurar receptores de eventos o crear un DOM Shadow.

**connectedCallback:** Se llama cada vez que se inserta el elemento en el DOM. Es útil para ejecutar código de configuración, como la obtención de recursos o la representación. En general, debes intentar demorar el trabajo hasta este momento.

**disconnectedCallback:** Se llama cada vez que se quita el elemento del DOM. Es útil para ejecutar código de limpieza (eliminación de receptores de eventos, etc.).

**attributeChangedCallback:** Agrega, quita, actualiza o reemplaza un atributo. También se llama para obtener valores iniciales cuando el analizador crea un elemento o lo actualiza.

```js
class Button extends HTMLElement {
  constructor() {
    super();

    this.innerHTML = `
      <button>Element</button>
    `;
  }
}

window.customElements.define('components-button', Button);
```

```js
window.customElements.define('components-button', class extends HTMLElement {
  constructor() {
    super();
  }

  connectedCallback() {
    ...
  }

  disconnectedCallback() {
    ...
  }
  attributeChangedCallback(attrName, oldVal, newVal) {
    ...
  }
});
```

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
  </head>
  <body>
    <components-boton></components-boton>
  </body>
</html>
```

## Shadow DOM.

Shadow DOM es un estándar web que ofrece encapsulación del marcado (HTML) y estilo de componente (CSS). Es una pieza de importancia crítica en la historia de los componentes web, ya que asegura que un componente funcionará en cualquier entorno, incluso si hay otro CSS o JavaScript en juego en la página. En pocas palabras el Shadow DOM aisla los componentes del exterior.

```js
class Navegation extends HTMLElement {

  constructor() {
    super();

    const shadow = this.attachShadow({mode: 'open'});
    shadow.innerHTML = `
      <style>
        :host {
          --color: #050;
        }

        header {
          display: Flex;
        }

        h1 {
          color: var(--color);
        }

        ul {
          list-style: none;
        }
      </style>

      <header>
        <div>
          <h1>Logo</h1>
        </div>
        <nav>
          <ul>
            <li>Home</li>
            <li>Project</li>
            <li>Contact</li>
          </ul>
        </nav>
      </header>
    `;
  }
}

window.customElements.define('components-nav', Navegation);
```

## HTML Template.

El HTML Template es comun cuando se tienes que reutilizar las mismas estructuras de lenguaje de marcado repetidas veces en una página web, tiene sentido utilizar algún tipo de plantilla en lugar de repetir la misma estructura una y otra vez. Esto ya era posible hacerlo antes, pero ahora es mucho mas fácil con el elemento de HTML `template`. Este elemento y su contenido no son renderizados en el DOM, pero pueden ser referenciados vía JavaScript.

```js
window.customElements.define('components-template', class extends HTMLElement {
  constructor() {
    super();
    
    const shadow = this.attachShadow({mode: 'open'});
    const template = document.createElement('template');

    template.innerHTML = `
      <style>
        h1 {
          color: gold;
        }

        p {
          color: blue;
        }
      </style>
  
      <div>
        <h1>Template</h1>
        <p>This is a template example</p>
      </div>
    `;

    /* With Shadow DOM */
    shadow.appendChild(template.content);
  }
});
```