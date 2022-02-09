# Aprender JavaScript

JavaScript se encuentra entre los lenguajes de programación
más potentes y flexibles de la web. Impulsa el
comportamiento dinámico en la mayoría de los sitios web,
incluido este.

Visita [w3schools](https://www.w3schools.com/) o [losapuntesdemajo](https://losapuntesdemajo.now.sh/) para mas
informacion.
___

## Logica y Algoritmo

Es un conjunto de instrucciones o reglas definidas y no ambiguas,
ordenadas y finitas que permite, típicamente, solucionar un problema,
realizar un cómputo, procesar datos y llevar a cabo otras tareas o
actividades. Dados un estado inicial y una entrada, siguiendo los
pasos sucesivos se llega a un estado final y se obtiene una solución.

> 1. Definir el problema.
>
> 2. Analizar el problema.
    >> * Entradas: Que se necesita para solucionar el problema.
    >> * Salida: Que se obtiene al final del problema.
    >> * Tipo de Dato: Numero, String, Boolea.
> 3. Diseñar el algoritmo.
>
> 4. Probar el algoritmo.



---

## Estructura y Variables.

Para declarar una variable en JavaScript, se puede usar
cualquiera de estas tres palabras clave junto con un
nombre de variable:

* `var` se utiliza en versiones de JavaScript anteriores a
ES6.

* `let` es la forma preferida de declarar una variable
cuando se puede reasignar.

* `const` es la forma preferida de declarar una variable
con un valor constante.

```js
// Esto es un comentario.

var x = 5;
let y = null;
const z = "Hola";

console.log(x);

document.write(x);
```

---

## Operadores Aritméticos.

|              |               |
| :----:       |:----          |
| +            |Suma           |
| -            |Resta          |
| *            |Multiplicacion |
| **           |Exponente      |
| /            |Division       |
| %            |Residuo        |
| ++           |Incremento     |
| --           |Decremento     |
|              |               |

## Operadores de comparación.

|              |                      |
| :----:       |:----                 |
| ==           |Igual                 |
| ===          |Igual valor y tipo    |
| !=           |No igual              |
| !==          |No igual valor y tipo |
| <            |Menor                 |
| >            |Mayor                 |
| <=           |Menor o igual         |
| >=           |Mayor o igual         |
|              |                      |

## Operadores lógicos.

|              |               |
| :----:       |:----          |
| &&           |Y              |
| ```||```     |O              |
| !            |Negacion       |
|              |               |

---

## Condicionales.

Las estructuras de control como los condicionales
(declaraciones`if` y similares) alteran el flujo de control
ejecutando solo bloques de código si se cumplen ciertas
condiciones. Estas estructuras esencialmente permiten que un
programa tome decisiones sobre qué código se ejecuta mientras
se ejecuta el programa.

```js
if (condicion) {
    True;
} else {
    False;
}
```

---

## Funciones.

Las funciones son uno de los bloques de construcción
fundamentales en JavaScript. Una función es un conjunto
reutilizable de declaraciones para realizar una tarea o
calcular un valor. A las funciones se les puede pasar uno
o más valores y pueden devolver un valor al final de su
ejecución. Para usar una función, debe definirla en algún
lugar del alcance donde desea llamarla.

```js
function nombre(parámetro, parámetro) {
    return 0;
}
```

```js
const nombre = (parámetro, parámetro) => {
    return 0;
}
```

---

## Matrices.

Las matrices son listas de datos almacenados y ordenados.
Pueden contener elementos de cualquier tipo de datos. Las
matrices se crean utilizando corchetes, con elementos
individuales separados por comas.

En las matrices la posición empieza desde el 0.

```js
let nombre = ["valor", 21, ...];
var nombre = ["valor", 21, ...];
document.write(nombre [posición]);
```

El metodo `pop()` elimina el ultimo elemento de la matriz.
```js
var nombre = ["valor", 21, ...];
nombre.pop();

// El valor de x sera el elemento eliminado.
var x = nombre.pop();
```

El metodo `push()` agrega un elemento al final de la matriz.
```js
var nombre = ["valor", 21, ...];
nombre.push(valor/valores);

// El valor de x sera la nueva longitud de la matriz.
var x = nombre.push(valor/valores);
```

El metodo `shift()` elimina el primer elemento de la matriz.
```js
var nombre = ["valor", 21, ...];
nombre.shift();

// El valor de x sera el elemento eliminado.
var x = nombre.shift();
```

El metodo `unshift()` agrega un elemento al principio de la
matriz.
```js
var nombre = ["valor", 21, ...];
nombre.unshift(valor/valores);

// El valor de x sera la nueva longitud de la matriz.
var x = nombre.unshift(valor/valores);
```

---

## Bucles.

Un bucle es una herramienta de programación que se utiliza
para repetir un conjunto de instrucciones. Iterar es un
término genérico que significa "repetir" en el contexto de
los bucles. Un bucle continuará iterando hasta que se
cumpla una condición específica, comúnmente conocida como
condición de detención.

La palabra clave `break` puede usarse para salir del ciclo
inmediatamente, continuando la ejecución después del cuerpo
del ciclo.

La palabra clave `continue` puede usarse para saltar de una
condicion del ciclo, continuando con la ejecucion en el
cuerpo del ciclo.

**While**

```js
while(condición) {
    // bloque de codigo.
}
```

**Do While**

```js
do {
    // bloque de codigo.
} while(condición);
```

**For**

```js
for(declaración; condición; iteración) {
    // bloque de codigo.
}
```

**For in**

```js
for(variable in objeto) {
    // bloque de codigo.
}
```

**For of**

```js
for(variable of iterable) {
    // bloque de codigo.
}
```
---

## Clases.

Poo (Programacion orientada a objetos) es un paradigma de
programación que viene a innovar la forma de obtener resultados. Los
objetos se utilizan como metáfora para emular las entidades reales
del negocio a modelar.

Para crear el diagrama de clases UML se necesitan de los siguientes
puntos:

1. identificar el problema.
2. identificar los objetos.
3. definir las clases.
4. hacer diagrama de clases.

JavaScript admite el concepto de clases como sintaxis para
crear objetos. Las clases especifican las propiedades y
métodos compartidos que tendrán los objetos producidos a
partir de la clase.

Cuando se crea un objeto basándose en la clase, el nuevo
objeto se denomina instancia de la clase. Las nuevas
instancias se crean utilizando la palabra clave `new`.

```js
class Nombre {

    constructor(atributo) {
        this.atributo = atributo;
    }

    get atributo() {
        return this.atributo;
    }

    set atributo(x) {
        this.atributo = x;
    }

    static estatico() {
        console.log('Estatico');
    }

    metodo() {
        console.log('Metodo');
    }
}

const nombre = new Nombre(atributo);

nombre.metodo();

Nombre.estatico();
```

```js
class Herencia extends Nombre {

    constructor(atributo, atributo) {
        super(atributo);
        this.atributo = atributo;
    }

    get atributo() {
        return this.atributo;
    }

    set atributo(x) {
        this.atributo = x;
    }
}
```

---

## Objecto.

Un objeto es un tipo de datos integrado para almacenar
pares clave-valor. Los datos dentro de los objetos están
desordenados y los valores pueden ser de cualquier tipo.

```js
const objecto = {

    propiedad: valor,
    propiedad: valor,
    propiedad: valor,

    metodo: function() {
        return 0;
    }

}

document.write(objecto.metodo());
```

```js
const objecto = {

    propiedad: valor,
    propiedad: valor,
    propiedad: valor,

    metodo() {
        return 0;
    }
    
}

document.write(objecto.metodo());
```
