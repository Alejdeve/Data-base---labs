# Ejercicio Completo de Creación de Base de Datos

## 1. Elegir una Temática
Elige una temática para tu base de datos. Te propongo una biblioteca, pero si hay algo que te motiva más, puedes usarlo mientras cumplas con los requisitos del ejercicio.

Al inicio de tu código, dropea (elimina) la base de datos si ya existe. Tras ello crea la base de datos de nuevo y acuérdate de usar la palabra reservada "use" para indicar que base de datos vas a usar.

## 2. Crear una Tabla Principal
Crea una tabla principal que almacenará la información central de tu base de datos.

Tabla Libros
id_libro: Identificador único para cada libro.
titulo: Título del libro.
anio_publicacion: Año de publicación del libro.
genero: Género del libro.

## 3. Crear Dos Tablas que Referencien a la Principal
Crea dos tablas adicionales que referencien a la tabla principal utilizando claves foráneas. En este caso podemos crear una tabla de Autores y otra de Ejemplares

Tabla Autores
id_autor: Identificador único para cada autor.
nombre: Nombre del autor.
Tabla Ejemplares
id_ejemplar: Identificador único para cada ejemplar de un libro.
id_libro: Referencia al libro correspondiente.
ubicacion: Ubicación del ejemplar en la biblioteca.
estado: Estado del ejemplar (e.g., disponible, prestado, dañado).

## 4. Relacionar la Tabla Principal con una Cuarta Tabla

Relaciona la tabla principal con una cuarta tabla que almacene información adicional relevante. En este ejemplo, una tabla de editoriales.

Tabla Editoriales
id_editorial: Identificador único para cada editorial.
nombre: Nombre de la editorial.

## 5. Insertar una Tabla Intermedia

Para manejar una relación Many-to-Many entre la tabla principal y una de las tablas adicionales, inserta una tabla intermedia.

Tabla LibroAutor
id_libro: Referencia a la tabla Libros.
id_autor: Referencia a la tabla Autores.
Resumen de Relaciones
La tabla principal debe tener una relación Many-to-One con la cuarta tabla.
La tabla principal debe tener una relación One-to-Many con una de las tablas adicionales.
La tabla principal y otra tabla adicional deben tener una relación Many-to-Many a través de la tabla intermedia.

## Solucion:

drop database if exists Biblioteca;

create database Biblioteca;

use Biblioteca;

create table libros (
	id_libro INT auto_increment primary key,
	titulo VARCHAR(255) not null,
	anio_publicacion year not null,
	genero VARCHAR(100) not NULL
);

create table autores (
	id_autor INT auto_increment primary key,
	nombre VARCHAR(255) not NULL
);

create table ejemplares (
	id_ejemplar INT auto_increment primary key,
	id_libro INT not null,
	ubicacion VARCHAR(255) not null,
	estado VARCHAR(50) not null,
	foreign key (id_libro) references libros(id_libro)
);

create table editoriales (
	id_editorial INT auto_increment primary key,
	nombre VARCHAR(255) not NULL
);

alter table libros add column id_editorial INT not null;
alter table libros add foreign key (id_editorial) references editoriales (id_editorial);

create table LibroAutor (
	id_libro INT not null,
	id_autor INT not null,
	primary key (id_libro, id_autor),
	foreign key (id_libro) references libros(id_libro),
	foreign key (id_autor) references autores(id_autor)
);