# Buenas Practica (Programacion)

Es un conjunto de técnicas, principios, metodologías que debemos
implementar en nuestro software para que se vuelva fácil, rápido y
seguro de desarrollar, mantener y desplegar.

---

**Nombre descriptivos**: Las variables, funciones, etc; deben tener
nombres descriptivos y para mayor conveniencia en inglés.

```js
let item = 'item'; // Buena práctica

let i = 'item'; // Mala práctica
```
```js
// Buena práctica
function deleteItem() {
       //...
}

// Mala práctica
function dI() {
       //...
}
```

**Funciones de un solo propósito**: Las funciones no pueden ser
multipropósito y tampoco pueden contener tantos parámetros, tienen
que tener una sola responsabilidad o acción.

```js
// Buena práctica
function sumarNumeros(a, b) {
       return a + b;
}

// Mala práctica
function sumarNumeros(a, b) {
       return a + b;
      if( a > b) {
          return true;
      }
}
```

**Comentarios**: Las funciones que no sean legibles debe contener
comentarios para especificar de que se trata cierta funcion.

```js
// Esta función suma dos números dados (Buena practica).
function sumarNumeros(a, b) {
       //...
}

// Mala práctica
function sumarNumeros(a, b) {
       //...
}
```

**If anidados**: Evitar tener tantos if anidados.

```js
// Buena práctica
if(a > b && a % 2 === 0 && b % 2 !== 0) {
      //...
}

// Mala práctica
if(a > b) {
      if(a % 2 === 0) {
          if(b % 2 !== 0) {
              //...
          }
      }
}
```

**Resultados de operaciones**: El resultado de una operación
(función) se puede almacenar en una variable, si el lenguaje de
programacion es de tipado fuerte tine que ser en una variable del
mismo tipo de dato.

```java
public class Verificacion {
       public static boolean verificarEstado(int estado) {
              if (estado == 1) {
                     return true;
              } else {
                     return false;
              }
       }
}

// Buena práctica
public class Main {
       public static void main(String[] args) {
              boolean estado = Verificacion.verificarEstado(1);

              if (estado == true) {
                     System.out.println("Correcto");
              } else {
                     System.out.println("Incorrecto");
              }
       }
}

// Mala práctica
public class Main {
       public static void main(String[] args) {
              if (Verificacion.verificarEstado(1) == true) {
                     System.out.println("Correcto");
              } else {
                     System.out.println("Incorrecto");
              }
       }
}
```

**Patrones de arquitectura de software**: Utilizar algunos de los
patrones de arquitectura de software para la buena implementación y
separación del código.

**Refactorizar**: Tratar de que el código sea lo más simple, legible
y limpio posible.