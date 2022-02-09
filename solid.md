# SOLID

Es un acrónimo introducido por Robert C. Martin ​que representa cinco
principios básicos de la programación orientada a objetos y el
diseño. Cuando estos principios se aplican en conjunto es más
probable que un desarrollador cree un sistema que sea fácil de
mantener y ampliar con el tiempo. Los principios **SOLID** son guías
que pueden ser aplicadas en el desarrollo de software para eliminar
malos diseños provocando que el programador tenga que refactorizar el
código fuente hasta que sea legible y extensible.

* **S**: Single Responsability Principle (SRP)
* **O**: Open/Closed Principle (OCP)
* **L**: Liskov Substitution Principle (LSP)
* **I**: Interface Segretation Principle (ISP)
* **D**: Dependency Inversion Principle (DIP)
---

## Principio de responsabilidad única (SRP)

Como lo indica su propio nombre, establece que una clase o componente
debe ser responsable de una sola cosa.

**Ejemplo**: Como podemos observar la clase `Estudiante` tiene mas de una
responsabilidad, la primera es obtener acceso a las prodiedades de la
clase y la segunda es guardar el objeto en una base de datos.

```java
public class Estudiante {
    private int codigo;

    public Estudiante(int codigo) {
        this.codigo = codigo;
    }

    public int getCodigo() {
        return codigo;
    }

    public void guardarEstudianteDB() {
        //...
    }
}
```
Para evitar esto, debemos separar las responsabilidades de la clase,
por lo que podemos crear otra clase que se encargue de las
operaciones de la base de datos.

```java
public class Estudiante {
    private int codigo;

    public Estudiante(int codigo) {
        this.codigo = codigo;
    }

    public int getCodigo() {
        return codigo;
    }
}

public class EstudianteDB {
    public void guardarEstudianteDB() {
        //...
    }
}
```
---

## Principio de abierto/cerrado (OCP)

Establece que las entidades software (clases) deberían estar abiertos
para su extensión, pero cerrados para su modificación.

**Ejemplo**: Si quisiéramos iterar a través de una lista de carreras
universitarias e imprimir sus notas promedio por pantalla, esto no
cumpliría el principio abierto/cerrado, ya que si decidimos añadir
una nueva carrera también tendríamos que modificar el condicional del
metodo main que hemos creado.

```java
public class Carrera {
    private int codigo;

    public Carrera(int codigo) {
        this.codigo = codigo;
    }

    public int getCarrera() {
        return codigo;
    }

    public static void main() {
        List<Carrera> carreras = new ArrayList<>();

        carreras.add(new Carrera(1234));
        carreras.add(new Carrera(9012));

        for (Carrera c : carreras) {
            if (c.getCodigo() == 1234) {
                System.out.println(4.5);
            }
            if (c.getCodigo() == 9012) {
                System.out.println(3.7);
            }
        }
    }
}
```
Para evitar esto, cada carrera nueva tendria un método nota. Esto es
un ejemplo sencillo, pero imagina que tu aplicación crece y crece,
¿cuántas modificaciones tendríamos que hacer?. Para cumplir con el
principio podriamos hacer lo siguiente.

```java
interface Carrera {
    float nota();
}

public class Sistema implements Carrera {
    @Override
    public float nota() {
        return 4.5;
    }
}

public class Medicina implements Carrera {
    @Override
    public float nota() {
        return 3.7;
    }
}

public class Demo {
    public static void main() {
        List<Carrera> carreras = new ArrayList<>();

        carreras.add(new Sistema());
        carreras.add(new Medicina());

        for (Carrera c : carreras) {
            System.out.println(c.nota());
        }
    }
}
```
---

## Principio de sustitución de Liskov (LSP)

El objetivo de este principio es asegurar que una clase hija pueda
asumir el lugar de su clase padre sin errores.

**Ejemplo**: Como podemos observar la interfaz `Personaje` tiene tres
metodo que debemos implementar, pero la clase `Medico` solamente
implementa los metodos correr y curar. Esto viola el principio de
substitución de Liskov ya que la clase `Medico` no puede hacerse
pasar por la interfaz `Personaje` debido a que no implementa los
mismos metodos.

```java
interface Personaje {
    void correr();
    void disparar();
    void curar();
}

public class Medico implements Personaje {
    @Override
    public void correr() {
        //...
    }

    @Override
    public void disparar() {
        //Error
    }

    @Override
    public void curar() {
        //...
    }
}
```
Para evitar esto, podemos dividir los metodos de la interfaz
Personaje y hacer una interfaz independiente con el metodo e
implementarlo en las clases necesarias.

```java
interface ICorrer {
    void correr();
}

interface IDisparar {
    void disparar();
}

interface ICurar() {
    void curar();
}

public class Medico implements ICorrer, ICurar {
    @Override
    public void correr() {
        //...
    }

    @Override
    public void curar() {
        //...
    }
}

public class Soldado implements ICorrer, IDisparar {
    @Override
    public void correr() {
        //...
    }

    @Override
    public void disparar() {
        //...
    }
}
```
---

## Principio de segregación de la interfaz (ISP)

El objetivo de este principio es que un cliente no debería estar
forzado a depender de métodos que no usa.

**Ejemplo**: Imaginemos que queremos definir las clases necesarias para
los medios de transporte. Por ejemplo, carro, barco y avion. El
problema es que el carro no vuela, y el avion no anda, por lo que
tendríamos que añadir una excepción o aviso si se intenta llamar a
estos métodos.

```java
interface Transporte {
    void volar();
    void andar();
}

public class Carro implements Transporte {
    @Override
    public void volar() {
        //Error
    }

    @Override
    public void andar() {
        //...
    }
}

public class Avion implements Transporte {
    @Override
    public void volar() {
        //...
    }

    @Override
    public void andar() {
        //Error
    }
}
```
Lo correcto sería segregar las interfaces, tanto como sea necesario.
Así, cada clase implementa las interfaces de la que realmente
necesita implementar sus métodos.

```java
interface IVolar {
    void volar();
}

interface IAndar {
    void andar();
}

public class Carro implements IAndar {
    @Override
    public void andar() {
        //...
    }
}

public class Avion implements IVolar {
    @Override
    public void volar() {
        //...
    }
}
```
---

## Principio de inversión de la dependencia (DIP)

Las dependencias deberían de estar sobre abstracciones, no sobre
clases concretas. Es decir los módulos de alto nivel no deberían
depender de módulos de bajo nivel.

**Ejemplo**: Imaginemos que tenemos una clase para realizar el acceso
a un videojuego, y eso lo hacemos a través de la base de datos MySQL.
Ahora Imaginemos que en el futuro queremos cambiar la base de datos
por MongoDB, ¿Ves el problema?, tendríamos que modificar las
instancias de la clase Acceso, una por una.

```java
public class SQL {
    public void datos() {
        //...
    }
}

public class Acceso {
    private SQL sql;

    public Acceso(SQL sql) {
        this.sql = sql;
    }
    
    public void acceder() {
        //...
    }
}
```
Lo correcto sería hacer que el módulo Acceso dependa de una
abstracción más genérica de base de datos. Así, sin importar el tipo
de base de datos que se le pase al módulo Acceso, ni este ni sus
instancias tendrán que cambiar. Cada servicio que queramos pasar a
Acceso deberá implementar la interfaz DataBase.

```java
interface DataBase {
    void datos();
}

public class SQL implements DataBase {
    @Override
    public void datos() {
        //...
    }
}

public class MongoDB implements DataBase {
    @Override
    public void datos() {
        //...
    }
}

public class Acceso {
    private DataBase dataBase;

    public Acceso(DataBase dataBase) {
        this.dataBase = dataBase;
    }
    
    public void acceder() {
        //...
    }
}
```