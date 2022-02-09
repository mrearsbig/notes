# Aprender Base de Datos

Una base de datos es una colección organizada de información
estructurada, o datos, típicamente almacenados electrónicamente
en un sistema de computadora. Actualmente existen dos base de
datos SQL y NoSQL.
___

## SQL

**SQL** (Structured Query Language) es un lenguaje estándar para
almacenar, manipular y recuperar datos en bases de datos. Los
software mas importantes en cuanto a SQL se refieran son `MySQL`,
`MariaDB`, `PostgreSQL` y `SQLite`. SQL se puede ejecutar para
hacer consultas, recuperar datos, insertar registros, actualizar
registros y eliminar registros. Tambien se puede crear nuevas bases
de datos y tablas.

Visita [w3schools](https://www.w3schools.com/sql/default.asp) para mas informacion.

Una base de datos suele contener una o más tablas. Cada tabla se
identifica con un nombre (por ejemplo, "Clientes" o "Productos").
Las tablas contienen registros (filas) con datos.

Tabla: "clientes"

| id | name      | city      | user      |
| -- | --------- | --------- | --------- |
| 1  | Camilo    | Florida   | camilito  |
| 2  | Andres    | Cali      | andresito |
| 3  | Alexander | Bogota    | alexito   |
| 4  | Angelica  | Santander | angelica  |

`CREATE DATABASE`: Se utiliza para crear una base de datos.

```sql
CREATE DATABASE nombreBaseDatos;
CREATE DATABASE tienda;
```

`CREATE TABLE`: Se utiliza para crear una tabla en la base de datos.

```sql
CREATE TABLE nombretabla(
    nombrecolumna tipoDato,
    nombrecolumna tipoDato,
    nombrecolumna tipoDato
);

CREATE TABLE clientes(
    id INT PRIMARY KEY,
    name VARCHAR(255),
    city VARCHAR(40),
    user VARCHAR(70)
);
```

`DROP DATABASE`: Se utiliza para eliminar una base de datos.

```sql
DROP DATABASE nombreBaseDatos;

DROP DATABASE tienda;
```

`DROP TABLE`: Se utiliza para eliminar una tabla de la base de datos.

```sql
DROP TABLE nombreTabla;

DROP TABLE clientes;
```

`SELECT`: Se utiliza para seleccionar datos de una tabla de la
base de datos. Con el * seleccionamos todas las columnas de la
tabla, tambien podemos seleccionar cada columna individual.

```sql
SELECT * FROM nombreTabla

SELECT * FROM clientes;
SELECT name, city FROM clientes;
```

`INSERT INTO`: Se utiliza para insertar nuevos datos en una tabla
de la base de datos.

```sql
INSERT INTO nombreTabla VALUES(valor, valor);

INSERT INTO clientes VALUES(5, 'Josefa', 'Cali', 'josefita');
INSERT INTO clientes(name, user) VALUES('Fernando', 'fernandito');
```

`UPDATE`: Se utiliza para modificar los datos de un tabla en la
base de datos.

```sql
UPDATE nombreTabla
SET columna = valor
WHERE condicion;

UPDATE clientes
SET city = 'Bogota'
WHERE id = 1;
```

`DELETE`: Se utiliza para eliminar un dato de la tabla en la base
de datos.

```sql
DELETE FROM nombreTabla WHERE columna = valor;

DELETE FROM clientes WHERE name = 'josefa';
```
---

## NoSQL

**NoSQL** es un sistema de gestion de base de datos que difiere del
modelo clásico de **SQL**, en aspectos importantes, siendo el más
destacado que no usan SQL como lenguaje principal de consultas. Los
datos almacenados no requieren estructuras fijas como tablas, y
habitualmente escalan bien horizontalmente. Los sistemas NoSQL se
denominan a veces "no solo SQL" para subrayar el hecho de que también
pueden soportar lenguajes de consulta de tipo SQL. Los software mas
importantes en cuanto a NoSQL se refiere son `Cassandra`, `MongoDB`
y `Redis`.

En este caso trabajaremos con unos de los software mas importantes de
**NoSQL** llamado `MongoDB`.

# MongoDB

`MongoDB` es una base de datos NoSQL orientada a documentos que se
utiliza para el almacenamiento de datos. En lugar de usar tablas y
filas como en las bases de datos relacionales tradicionales, MongoDB
hace uso de colecciones y documentos. Los **documentos** constan de
pares `{clave: valor}` que son la unidad básica de datos en MongoDB.
Las **colecciones** contienen conjuntos de documentos y funciones que son
equivalentes a las tablas de bases de datos relacionales. MongoDB
utiliza el formato **BSON**, que es muy parecido al formato **JSON**
para la creacion de datos.

```json
{
    "nombre": "Nombre",
    "apellido": "Apellido",
    "codigo": "11223344",
    "edad": 21
}
```
---

## Comandos MongoDB

`mongod`: Inicia la base de datos.

`mongo`: Conecta la base de datos.

`show dbs`: Muestra la lista de todas las bases de datos.

`use nombreBaseDatos`: Cambia la base de datos actual a
`nombreBaseDatos` y sino existe la crea.

`db`: Muestra la base de datos actual.

`db.dropDatabase()`: Elimina la base de datos actual.

`db.createCollection("nombreBaseDatos")`: Crea una coleccion.

`db.nombreBaseDatos.drop()`: Elimina una coleccion.

`show collections`: Muestra la lista de colecciones de la base de
datos.

`db.nombreBaseDatos.insert({JSON})`: Inserta un dato a la coleccion.

`db.nombreBaseDatos.find()`: Muestra los datos de una coleccion,
tambien podemos filtrar los datos de una coleccion con
`db.nombreBaseDatos.find({clave: valor})`.

`db.nombreBaseDatos.find().pretty()`: Muestra los datos de una
coleccion en formato BSON.

`db.nombreBaseDatos.update({clave: valor}, {$set: {clave: valor}})`:
Actualiza un dato de la coleccion.

`db.nombreBaseDatos.remove()`: Elimina un dato en especifico de la
coleccion.