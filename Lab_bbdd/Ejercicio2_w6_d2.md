# Base de datos supermercado

## Parte 1:

Crea una base de datos para un supermercado donde habrá tres tablas: clientes, productos y proveedores.

### Tabla Clientes
id_cliente: Identificador único para cada cliente.
nombre: Nombre del cliente.
direccion: Dirección del cliente.
telefono: Teléfono de contacto del cliente.
email: Correo electrónico del cliente.

### Tabla Productos
id_producto: Identificador único para cada producto.
nombre_producto: Nombre del producto.
precio: Precio del producto.
id_proveedor: Identificador del proveedor del producto (Clave foránea).

### Tabla Proveedores
id_proveedor: Identificador único para cada proveedor.
nombre_proveedor: Nombre del proveedor.
direccion: Dirección del proveedor.
telefono: Teléfono de contacto del proveedor.
email: Correo electrónico del proveedor.

### Elige el tipo de dato para cada atributo y justifica por qué usas ese dato.

## Tabla Clientes

- id_cliente: INT - Identificador único para cada cliente. Usamos INT porque es un tipo de dato adecuado para un identificador único y puede autoincrementarse.
- nombre: VARCHAR(255) - Nombre del cliente. VARCHAR se utiliza porque permite almacenar cadenas de texto de longitud variable.
- direccion: VARCHAR(255) - Dirección del cliente. VARCHAR es adecuado para almacenar direcciones de longitud variable.
- telefono: VARCHAR(15) - Teléfono de contacto del cliente. VARCHAR se utiliza porque los números de teléfono pueden contener caracteres como guiones y paréntesis.
- email: VARCHAR(255) - Correo electrónico del cliente. VARCHAR es adecuado para almacenar correos electrónicos de longitud variable.

## Tabla Productos

- id_producto: INT - Identificador único para cada producto. INT se utiliza por las mismas razones que id_cliente.
- nombre_producto: VARCHAR(255) - Nombre del producto. VARCHAR es adecuado para almacenar nombres de productos de longitud variable.
- precio: DECIMAL(10, 2) - Precio del producto. DECIMAL se utiliza para almacenar valores numéricos con decimales, ideal para precios.
- id_proveedor: INT - Identificador del proveedor del producto (Clave foránea). INT se utiliza para hacer referencia a la tabla Proveedores.

## Tabla Proveedores

- id_proveedor: INT - Identificador único para cada proveedor. INT se utiliza por las mismas razones que id_cliente y id_producto.
- nombre_proveedor: VARCHAR(255) - Nombre del proveedor. VARCHAR es adecuado para almacenar nombres de proveedores de longitud variable.
- direccion: VARCHAR(255) - Dirección del proveedor. VARCHAR es adecuado para almacenar direcciones de longitud variable.
- telefono: VARCHAR(15) - Teléfono de contacto del proveedor. VARCHAR se utiliza porque los números de teléfono pueden contener caracteres como guiones y       paréntesis.
- email: VARCHAR(255) - Correo electrónico del proveedor. VARCHAR es adecuado para almacenar correos electrónicos de longitud variable.

### Crea las tablas en SQL usando Dbeaver.

USE supermercado;

CREATE TABLE Clientes (
	id_cliente INT PRIMARY KEY AUTO_INCREMENT,
	nombre VARCHAR(255) not NULL,
	direccion VARCHAR(255) not NULL,
	telefono VARCHAR(15),
	email VARCHAR(255) not NULL
);

CREATE TABLE Proveedores(
	id_proveedor INT PRIMARY KEY AUTO_INCREMENT,
	nombre_proveedor VARCHAR(255) not NULL,
	direccion VARCHAR(255) not NULL,
	teLefono VARCHAR(15),
	email VARCHAR(255)
);

CREATE TABLE Productos(
	id_producto INT PRIMARY KEY AUTO_INCREMENT,
	nombre_producto VARCHAR(255),
	precio DECIMAL(10,2),
	id_proveedor INT,
	FOREIGN KEY (id_proveedor) REFERENCES proveedores(id_proveedor)
);

### Inserta al menos 10 datos para rellenar tu base de datos.

INSERT INTO Clientes (nombre, direccion, telefono, email) values
('Manuel Garcia', 'Rambla Sant Jordi 1', '635-988-512', 'manuel.garcia@hotmail.com'),
('Alejandro Garcia', 'Rambla Sant Jordi 2', '635-988-513', 'manuel.garcia2@hotmail.com'),
('Manuel Rojas', 'Rambla Sant Jordi 3', '635-988-513', 'Alejandro.garcia3@hotmail.com'),
('Alejandro Rojas', 'Rambla Sant Jordi 4', '635-988-514', 'alejandro.rojas4@hotmail.com'),
('Ana Molina', 'Rambla Sant Jordi 5', '635-988-515', 'anamolina@hotmail.com'),
('James Rodriguez', 'Rambla Sant Jordi 6', '635-988-516', 'jamesrodriguez@hotmail.com'),
('Joan Ferrer', 'Carrer Aigua', '635-988-517', 'robot16@hotmail.com'),
('Jordi Capdevila', 'Carrer principal 12', '635-988-518', 'hacker20@hotmail.com'),
('Manel Pique', 'Carrer els Molins 47', '635-988-519', 'manel.pique@hotmail.com'),
('Jaume Torrat', 'San Diego 182', '635-988-520', 'toymachine@hotmail.com');

INSERT INTO Proveedores (nombre_proveedor, direccion, telefono, email) VALUES
('Proveedor A', 'Calle Proveedor 1', '111-222-3333', 'proveedora@example.com'),
('Proveedor B', 'Calle Proveedor 2', '444-555-6666', 'proveedorb@example.com'),
('Proveedor C', 'Calle Proveedor 3', '777-888-9999', 'proveedorc@example.com'),
('Proveedor D', 'Calle Proveedor 4', '000-111-2222', 'proveedord@example.com'),
('Proveedor E', 'Calle Proveedor 5', '111-232-3333', 'proveedore@example.com'),
('Proveedor F', 'Calle Proveedor 6', '444-535-6666', 'proveedorf@example.com'),
('Proveedor G', 'Calle Proveedor 7', '777-838-9999', 'proveedorg@example.com'),
('Proveedor H', 'Calle Proveedor 8', '000-191-2222', 'proveedorh@example.com'),
('Pepsi co', 'Calle falsa 123', '999-000-232-789', 'administrador@pepsico.com'),
('Proveedor I', 'Calle Proveedor 9', '333-474-5555', 'proveedori@example.com');

INSERT INTO Productos (nombre_producto, precio, id_proveedor) VALUES
('Doritos', 10.99, 9),
('Producto 2', 15.49, 2),
('Producto 3', 7.99, 3),
('Producto 4', 12.49, 1),
('Producto 5', 8.99, 2),
('Producto 6', 14.99, 3),
('Producto 7', 11.99, 4),
('Producto 8', 9.49, 5),
('Producto 9', 13.99, 4),
('Producto 10', 16.99, 5);

## Parte 2: Base de Datos Propia

### Crea tu propia base de datos para cualquier finalidad que imagines (por ejemplo, una base de datos de películas de ciencia ficción).

### Tabla Películas de ejemplo

id_pelicula: Identificador único para cada película.
titulo: Título de la película.
director: Nombre del director de la película.
anyo: Año de lanzamiento de la película.
genero: Género de la película.
duracion: Duración de la película en minutos.

## Elige el tipo de dato para cada atributo y justifica por qué usas ese dato.

## Base de datos MyMusic

## Tabla Canciones:

### id_cancion: INT AUTO_INCREMENT PRIMARY KEY

- Utilizamos INT para el identificador único de cada canción porque es un valor numérico que se incrementa automáticamente con cada nueva entrada, asegurando que cada canción tenga un ID único y secuencial.

### nombre_cancion: VARCHAR(255)

- Utilizamos VARCHAR(255) porque los títulos pueden variar en longitud y 255 caracteres son más que suficientes para la mayoría de los títulos de canciones.

### banda: VARCHAR(255)

- Utilizamos VARCHAR(255) porque los nombres de las bandas pueden ser de diferentes longitudes, y 255 caracteres son suficientes para almacenar la mayoría de   los nombres completos.

### nombre_album: VARCHAR(255)

- Utilizamos VARCHAR(255) por la misma razon que la utilizamos en banda.

### genero: VARCHAR(100)

- Utilizamos VARCHAR(100) por la misma razon que la utilizamos en banda.

### duracion: INT

- Utilizamos INT porque la duración de una cancion en minutos es un valor numérico entero, y este tipo de dato es el más adecuado para representarlo.
Con esta estructura, no utilizamos TIME porque la mayoria por no decir todas las canciones duran menos de una hora y con TIME seria mejor utilizar las horas minutos y seg.

## tabla Album

### id_album INT auto_increment primary key:

- utilizamos INT para el identificador único de cada album porque es un valor numérico que se incrementa automáticamente con cada nueva entrada, asegurando que cada album tenga un ID único y secuencial.
	
### nombre_album VARCHAR(255) not null:

- Utilizamos VARCHAR(255) por la misma razon que la utilizamos en banda.
	
### banda VARCHAR(255) not null:

- Utilizamos VARCHAR(255) porque los nombres de las bandas pueden ser de diferentes longitudes, y 255 caracteres son suficientes para almacenar la mayoría de   los nombres completos.

### anio year not null:

- Utilizamos YEAR porque es exactamente un año el valor que requerimos.

## tabla Genero:

### id_genero INT auto_increment primary key.

- utilizamos INT para el identificador único de cada genero porque es un valor numérico que se incrementa automáticamente con cada nueva entrada, asegurando que cada genero tenga un ID único y secuencial.

### nombre_genero VARCHAR(255) not null.

- Utilizamos VARCHAR(255) porque los nombres de los generos pueden ser de diferentes longitudes, y 255 caracteres son suficientes para almacenar la mayoría de   los nombres completos.


## Crea la tabla en SQL usando Dbeaver.

### Codigo SQL

create database if not exists MyMusic;

use MyMusic;

create table Canciones (
	id_cancion INT auto_increment primary key,
	nombre_cancion VARCHAR(255) not null,
	banda VARCHAR(255) not null,
	album VARCHAR(255) not NULL,	
	genero VARCHAR(100) not null,
	duracion INT not null 
);

create table Album (
	id_album INT auto_increment primary key,
	nombre_album VARCHAR(255) not null,
	banda VARCHAR(255) not null,
	anio year not null
);

create table Genero (
	id_genero INT auto_increment primary key,
	nombre_genero VARCHAR(255) not null,
	id_album INT,
	foreign key (id_album) references album(id_album)
);

### Todos los ejercicios deben estar normalizados al menos hasta la tercera forma normal.

## Inserta al menos 10 datos para rellenar tu base de datos.

### Tabla canciones

insert into canciones (nombre_cancion, banda, genero, duracion) values
('the kid are not alright', 'the offspring', 'rock', '3.22'),
('basket case', 'green day', 'rock', '2.46'),
('fat lip', 'sum 41', 'rock', '2.26'),
('fuel', 'metallica', 'heavy metal', '4.11'),
('the trooper', 'iron maiden', 'metal', '6.36'),
('superman', 'gold finger', 'rock', '3.36'),
('let it be', 'the beatles', 'pop', '3.25'),
('paranoid', 'Ozzy ousburne', 'rock', '2.36'),
('the world is mine', 'David Guetta', 'techno', '3.39');

### tabla Albums

insert into album (nombre_album , banda, anio) values
('americana', 'the offspring', '1996'),
('dookie', 'green day', '1992'),
('all killer no filler', 'sum 41', '2000'),
('load', 'metallica', '1989'),
('fear of the dark', 'iron maiden', '1989'),
('enema of state', 'blink 182', '1999'),
('the best of gold finger', 'gold finger', '1996'),
('let it be', 'let it be', '1961'),
('paranoid', 'Ozzy ousburn', '1985'),
('guetta blaster', 'David guetta', '2004');

## Normalización y corrección de MyMusic en nueva base de datos llamada MymusicLab

create database if not exists MyMusiclab;

use MyMusiclab;

create table Bandas(
	id_banda INT auto_increment primary key,
	nombre_banda VARCHAR(255) not NULL
);

create table Generos (
	id_genero INT auto_increment primary key,
	nombre_genero VARCHAR(255) not null	
);

create table Album (
	id_album INT auto_increment primary key,
	nombre_album VARCHAR(255) not null,
	id_banda INT not null,
	anio year not null,
	foreign key (id_banda) references Bandas (id_banda)
);

create table Canciones (
	id_cancion INT auto_increment primary key,
	nombre_cancion VARCHAR(255) not null,
	id_banda INT not null,	
	id_genero INT not null,
	id_album INT not null,
	duracion decimal(10, 2) not null,
	foreign key (id_banda) references bandas(id_banda),
	foreign key (id_genero) references Generos(id_genero),
	foreign key (id_album) references Album(id_album)
);

## Codigo para insertar datos:

INSERT INTO Bandas (nombre_banda) VALUES
('Queen'),
('The Beatles'),
('Pink Floyd'),
('Led Zeppelin'),
('The Rolling Stones'),
('AC/DC'),
('Nirvana'),
('The Doors'),
('Metallica'),
('U2');

INSERT INTO Generos (nombre_genero) VALUES
('Rock'),
('Pop'),
('Metal'),
('Punk'),
('Alternative'),
('Blues'),
('Jazz'),
('Country'),
('Classical'),
('Hip-Hop');

INSERT INTO Album (nombre_album, id_banda, anio) VALUES
('A Night at the Opera', 1, 1975),
('Abbey Road', 2, 1969),
('The Dark Side of the Moon', 3, 1973),
('Led Zeppelin IV', 4, 1971),
('Let It Bleed', 5, 1969),
('Back in Black', 6, 1980),
('Nevermind', 7, 1991),
('The Doors', 8, 1967),
('Master of Puppets', 9, 1986),
('The Joshua Tree', 10, 1987);

INSERT INTO Canciones (nombre_cancion, id_banda, id_genero, id_album, duracion) VALUES
('Bohemian Rhapsody', 1, 1, 1, 5.55),
('Come Together', 2, 1, 2, 4.20),
('Money', 3, 1, 3, 6.30),
('Stairway to Heaven', 4, 1, 4, 8.02),
('Gimme Shelter', 5, 1, 5, 4.37),
('Hells Bells', 6, 1, 6, 5.12),
('Smells Like Teen Spirit', 7, 5, 7, 5.01),
('Light My Fire', 8, 1, 8, 7.06),
('Battery', 9, 3, 9, 5.12),
('With or Without You', 10, 1, 10, 4.56);