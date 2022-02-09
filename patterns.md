# Patrones de Diseño

Los patrones de diseño son unas técnicas para resolver problemas
comunes en el desarrollo de software y otros ámbitos referentes al
diseño de interacción o interfaces.

Un patrón de diseño resulta ser una solución a un problema de diseño.
Una de las características mas importantes de los patrones de diseño
es que debe haber comprobado su efectividad resolviendo problemas
similares en ocasiones anteriores. Otra es que debe ser reutilizable,
lo que significa que es aplicable a diferentes problemas de diseño en
distintas circunstancias.
___

## Clasificacion

Los patrones de diseño varían en su complejidad, nivel de detalle y
escala de aplicabilidad. Además, pueden clasificarse por su propósito
y se dividen en tres grupos:

* **Creacionales**: Los patrones creacionales proporcionan mecanismos
de creación de objetos que incrementan la flexibilidad y la
reutilización de código existente. Los patrones creacionales
mas utilizados son `Factory Method`, `Abstract Factory` y `Singleton`.

* **Estructurales**: Los patrones estructurales explican cómo ensamblar
objetos y clases en estructuras más grandes a la vez que se mantiene
la flexibilidad y eficiencia de la estructura. Los patrones
estructurales mas utilizados son `Decorator`.

* **Comportamiento**: Los patrones de comportamiento se encargan de una
comunicación efectiva y la asignación de responsabilidades entre
objetos. Los patrones de comportamiento mas utilizados son `Strategy`.
___

## Factory Method

Es un patrón de diseño creacional que proporciona una interfaz para
crear objetos en una superclase, mientras permite a las subclases
alterar el tipo de objetos que se crearán.

**Problema**: Imagina que estás creando una aplicación para una tienda.
La primera versión de tu aplicación sólo es capaz de hacer envios por
camión, por lo que la mayor parte de tu código se encuentra dentro de
la clase `Camión`.

Al cabo de un tiempo, tu aplicación se vuelve bastante popular. Cada
día recibes decenas de peticiones de empresas de transporte aéreo
para que incorpores la logística por aire de la aplicación.

![Estructura Factory](./src/factory.png)

**Solución**

**transporte/Transporte.java**: Producto.
```java
package transporte;

/*
* Interfaz para todos los transportes.
*/
public interface Transporte {
    void inicio();
    void fin();
}
```

**transporte/Avion.java**: Producto concreto.
```java
package transporte;

/*
* Implementacion del transporte Avion.
*/
public class Avion implements Transporte {
    @Override
    public void inicio() {
        System.out.println("Inicio del recorrido en avion");
    }

    @Override
    public void fin() {
        System.out.println("fin del recorrido en avion");
    }
}
```

**factory/Factory.java**: Factory.
```java
package factory;

/*
* Clase base factory.
*/
public abstract class Factory {
    abstract Transporte crearTransporte();
}
```

**factory/TransporteFactory.java**: Factory concreto.
```java
package factory;

/*
* SeleccionarTransporteFactory producira transporte acorde al tipo de transporte.
*/
public class TransporteFactory extends Factory {
    @Override
    public Transporte crearTransporte(String tipo) {
        if (tipo.equals("Camion")) {
            return new Camion();
        } else if (tipo.equals("Avion")) {
            return new Avion();
        } else {
            return null;
        }
    }
}
```

**app/Demo.java**: Ejecucion.
```java
package app;

/*
* Clase demo.
*/
public class Demo {
    public static void main(String[] args) {
        TransporteFactory factory = new TransporteFactory();
        Transporte transporte = factory.crearTransporte("Avion");
        transporte.inicio();
        transporte.fin();
    }
}
```
---

## Abstract Factory

Es un patrón de diseño creacional que nos permite producir familias
de objetos relacionados sin especificar sus clases concretas.

**Problema**: Imagina que estás creando una tienda de computadores.
Tu código está compuesto por clases que representan lo siguiente:

Una familia de productos relacionados, digamos: Laptop + Desktop.

Algunas variantes de esta familia. Por ejemplo, los productos
Laptop + Desktop están disponibles en estas variantes: Asus, Lenovo.

![Estructura Factory](./src/abstract.png)

**Solución**

**laptops**: Primera jerarquia de productos.

**laptops/Laptop.java**
```java
package laptops;

/*
* Interfaz para toda la familia de laptops.
*/
public interface Laptop {
    void encender();
}
```

**laptops/AsusLaptop.java**
```java
package laptops;

/*
* Variante de laptop para Asus.
*/
public class AsusLaptop implements Laptop {
    @Override
    public void encender() {
        System.out.println("Encendiendo Asus");
    }
}
```

**laptops/LenovoLaptop.java**
```java
package laptops;

/*
* Variante de laptop para Lenovo.
*/
public class LenovoLaptop implements Laptop {
    @Override
    public void encender() {
        System.out.println("Encendiendo Lenovo");
    }
}
```

**desktops**: Segunda jerarquia de productos.

**desktops/Desktop.java**
```java
package desktops;

/*
* Interfaz para toda la familia de desktops.
*/
public interface Desktop {
    void encender();
}
```

**desktops/AsusDesktop.java**
```java
package desktops;

/*
* Variante de desktop para Asus.
*/
public class AsusDesktop implements Desktop {
    @Override
    public void encender() {
        System.out.println("Encendiendo Asus");
    }
}
```

**desktops/LenovoDesktop.java**
```java
package desktops;

/*
* Variante de desktop para Lenovo.
*/
public class LenovoDesktop implements Desktop {
    @Override
    public void encender() {
        System.out.println("Encendiendo Lenovo");
    }
}
```

**factory/Factory.java**: Abstract Factory.
```java
package factory;

/*
* Clase base factory.
*/
public interface Factory {
    Laptop crearLaptop();
    Desktop crearDesktop();
}
```

**factory/AsusFactory.java**: Factory concreto (Asus).
```java
package factory;

/*
* Clase factory para asus.
*/
public class AsusFactory implements Factory{
    @Override
    public Laptop crearLaptop() {
        return new AsusLaptop();
    }

    @Override
    public Desktop crearDesktop() {
        return new AsusDesktop();
    }
}
```

**factory/LenovoFactory.java**: Factory concreto (Lenovo).
```java
package factory;

/*
* Clase factory para lenovo.
*/
public class LenovoFactory implements Factory{
    @Override
    public Laptop crearLaptop() {
        return new LenovoLaptop();
    }

    @Override
    public Desktop crearDesktop() {
        return new LenovoDesktop();
    }
}
```

**cliente/Tienda.java**: Cliente.
```java
package cliente;

/*
* Clase tienda (Cliente).
*/
public class Tienda {
    private Laptop laptop;
    private Desktop desktop;

    public Tienda(Factory factory) {
        laptop = factory.crearLaptop();
        desktop = factory.crearDesktop();
    }
}
```

**app/Demo.java**: Ejecucion.
```java
package app;

/*
* Clase demo.
*/
public class Demo {
    public static void main(String[] args) {
        Factory factory = new LenovoFactory();
        Tienda tienda = new Tienda(factory);
        tienda.crearDesktop();
        tienda.crearLaptop();
    }
}
```
---

## Strategy

Es un patrón de diseño de comportamiento que te permite definir una
familia de algoritmos, colocar cada uno de ellos en una clase
separada y hacer sus objetos intercambiables.

**Problema**: Imagina que estas creando una calculadora. La primera
versión de la aplicación sólamente era capaz de sumar, restar,
multiplicar y dividir. Pero aparentemente, estas opciones se quedan
cortas. De modo que, en la siguiente actualización, añadiste una
opción para sacar el porcentaje. Después, añadiste otra opción para
elevar al cuadrado un numero.

Sin embargo, esto era sólo el principio. Más tarde planeaste añadir
operaciones con seno, y más tarde, otra opción para hacer operaciones
con coseno.

![Estructura Factory](./src/strategy.png)

**Solución**

**strategies/OperacionStrategy.java**: Interfaz común de las operaciones.
```java
package strategies;

/*
* Interfaz común para todas las estrategias.
*/
public interface OperacionStrategy {
    int hacerOperacion(int a, int b);
}
```

**strategies/SumaStrategy.java**: Operacion Suma.
```java
package strategies;

/*
* Estrategia concreta. Implementa la operacion suma.
*/
public class SumaStrategy implements OperacionStrategy {
    @Override
    public int hacerOperacion(int a, int b) {
        return numeroUno + numeroDos;
    }
}
```

**strategies/RestaStrategy.java**: Operacion Resta.
```java
package strategies;

/*
* Estrategia concreta. Implementa la operacion resta.
*/
public class RestaStrategy implements OperacionStrategy {
    @Override
    public int hacerOperacion(int a, int b) {
        return numeroUno - numeroDos;
    }
}
```

**context/CalculadoraContext.java**: Contexto.
```java
package context;

/*
* Clase contexto.
*/
public class CalculadoraContext {
    private OperacionStrategy strategy;

    public CalculadoraContext(OperacionStrategy strategy) {
        this.strategy = strategy;
    }

    public int ejecutar(int a, int b) {
        return strategy.hacerOperacion(a, b);
    }
}
```

**app/Demo.java**: Ejecucion.
```java
package app;

/*
* Clase demo.
*/
public class Demo {
    public static void main(String[] args) {
        CalculadoraContext context = new CalculadoraContext(new SumaStrategy);
        int resultado = context.ejecutar(21, 13);
        System.out.println(resultado);
    }
}
```
---

## Singleton

Es un patrón de diseño creacional que nos permite asegurarnos de que
una clase tenga una única instancia, a la vez que proporciona un
punto de acceso global a dicha instancia. El patron de diseño
singleton funciona de la siguiente manera, si ya has creado un objeto
y al cabo de un tiempo decides crear otro nuevo. En lugar de recibir
un objeto nuevo, obtendrás el que ya habías creado.

**Problema**: Imagina que estas creando una aplicación que tiene un
login. Pero necesitas que un usuario tenga solamente una sesión
abierta.

![Estructura Factory](./src/singleton.png)

**Solución**

**singleton/Singleton.java**: Singleton
```java
package singleton;

/*
* Clase singleton.
*/
public class Singleton {
    private static Singleton instance;

    private Singleton() {
    }

    public static Singleton getInstance() {
        if (instance == null) {
            instance = new Singleton();
        }

        return instance;
    }
}
```

**app/Demo.java**: Ejecucion.
```java
package app;

/*
* Clase demo.
*/
public class Demo {
    public static void main(String[] args) {
        Singleton singleton = Singleton.getInstance();
    }
}
```
---

## Decorator

Es un patrón de diseño estructural que te permite añadir
funcionalidades a objetos colocando estos objetos dentro de objetos
encapsuladores especiales que contienen estas funcionalidades.

**Problema**: Imagina que estás trabajando en un videojuego, uno de
los enemigos tiene diferentes maneras de aparecer en el juego. El
enemigo inicial es sin espada y sin armadura, el siguiente es con
espada y sin armadura y el ultimo es con espada y con armadura.

No puede ser muy complicado ¿verdad?, Extendiste la clase `Enemigo` y
metiste los métodos adicionales dentro de las nuevas subclases. Ahora
simplemente debería instanciar la clase enemigo deseado y utilizarla
para el videojuego.

Pero entonces alguien te hace una pregunta razonable: “¿Por qué no se
pueden utilizar varios tipos de enemigos al mismo tiempo?”. Intentaste
solucionar ese problema creando subclases especiales que combinen
varios enemigos dentro de una clase. Sin embargo, enseguida resultó
evidente que esta solución inflaría el código en gran medida.

![Estructura Factory](./src/decorator.png)

**Solución**

**decorators/Enemigo.java**: Interfaz común del enemigo.
```java
package decorators;

/*
* Interfaz común para todos los enemigos.
*/
public interface Enemigo {
    int recibirDaño();
}
```

**decorators/EnemigoBase.java**: Enemigo Base.
```java
package decorators;

/*
* Decorador concreto. Implementa un enemigo sin espada y armadura.
*/
public class EnemigoBase implements Enemigo {
    @Override
    public int recibirDaño() {
        return 15;
    }
}
```

**decorators/DecoradorEnemigo.java**: Decorador abstracto base.
```java
package decorators;

/*
* Decorador base.
*/
public class DecoradorEnemigo implements Enemigo {
    private Enemigo enemigo;

    public DecoradorEnemigo(Enemigo enemigo) {
        this.enemigo = enemigo;
    }

    @Override
    public int recibirDaño() {
        return this.enemigo.recibirDaño();
    }
}
```

**decorators/EnemigoEspada.java**: Decorador concreto.
```java
package decorators;

/*
* Decorador concreto para enemigos con espada.
*/
public class EnemigoEspada extends DecoradorEnemigo {
    @Override
    public int recibirDaño() {
        return this.enemigo.recibirDaño() - 5;
    }
}
```

**decorators/EnemigoArmadura.java**: Decorador concreto.
```java
package decorators;

/*
* Decorador concreto para enemigos con armadura.
*/
public class EnemigoArmadura extends DecoradorEnemigo {
    @Override
    public int recibirDaño() {
        return this.enemigo.recibirDaño() - 10;
    }
}
```

**app/Demo.java**: Ejecucion.
```java
package app;

/*
* Clase demo.
*/
public class Demo {
    public static void main(String[] args) {
        Enemigo enemigo = new EnemigoBase();
        System.out.println(enemigo.recibirDaño()); // return 15.
        DecoradorEnemigo enemigoConEspada = new EnemigoEspada(enemigo);
        System.out.println(enemigoConEspada.recibirDaño()); // return 10.
        DecoradorEnemigo enemigoConArmadura = new EnemigoArmadura(EnemigoBase);
        System.out.println(enemigoConArmadura.recibirDaño()); // return 5.
        DecoradorEnemigo enemigoConEspadaArmadura = new EnemigoArmadura(enemigoConEspada);
        System.out.println(enemigoConEspadaArmadura.recibirDaño()); // return 0.
    }
}
```
---

## Observer

Es un patrón de diseño de comportamiento que te permite definir un
mecanismo de suscripción para notificar a varios objetos sobre
cualquier evento que le suceda al objeto que están observando.

**Problema**: Imagina que tienes dos tipos de objetos: un objeto
Usuario y un objeto Blog. El usuario está muy interesado en un tema
en especifico (digamos, un nuevo tema de patrones de diseño) que se
publicara en el blog cada semana.

El usuario puede visitar el blog cada día para comprobar si ya hay
una publicacion. Pero, mientras se publica el tema, el usuario ya ha
visitado el blog varias veces y esto serán en vano. Esto ahorraría a
los usuarios visitar el blog cada dia, pero, al mismo tiempo,
molestaría a otros usuarios que no están interesados en el tema.

![Estructura Factory](./src/observer.png)

**Solución**

**subjects/Subject.java**: Notificador básico.
```java
package subjects;

/*
* Notificador básico.
*/
public class Subject {
    void adjuntar(Observer observer);
    void separar(Observer observer);
    void notificar();
}
```

**subjects/Blog.java**: Notificador concreto.
```java
package subjects;

/*
* Notificador concreto.
*/
public class Blog extends Subject {
    private List<Observer> usuarios;

    public Blog() {
        usuarios = new ArrayList<>();
    }

    @Override
    public void adjuntar(Observer observer) {
        // Añadir suscripción.
    }

    @Override
    public void separar(Observer observer) {
        // Eliminar suscripción.
    }

    @Override
    public void notificar() {
        // Notificar con el metodo update del Observer a todos los
        // usuarios.
    }
}
```

**observers/Observer.java**:  Interfaz observadora común.
```java
package decorators;

/*
* Interfaz común para todos los observadores.
*/
public interface Observer {
    void update();
}
```

**observers/Usuario.java**: Observador concreto.
```java
package decorators;

/*
* Observador concreto.
*/
public class Usuario implements Observer {
    @Override
    public void update() {
    }
}
```

**app/Demo.java**: Ejecucion.
```java
package app;

/*
* Clase demo.
*/
public class Demo {
    public static void main(String[] args) {
        Blog blog = new Blog();
        Usuario usuario = new Usuario();

        blog.notificar();
    }
}
```