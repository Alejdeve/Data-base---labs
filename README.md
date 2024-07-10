# Data-base---labs

## Ejercicio 1: Normalización de una Base de Datos de Películas

### Descripción: La tabla Peliculas contiene información sobre películas, incluyendo detalles de actores, director, año de estreno, género y país de origen. Esta tabla no está normalizada.

### Instrucciones:
### 1. Identifica las posibles redundancias y dependencias.
### 2. Descompón la tabla Peliculas en varias tablas siguiendo las reglas de normalización hasta alcanzar la 3FN.

1. redundancias:

 - Columna de directores, James Cameron de repite.
 - Columna años, tambien hay años repetidos.
 - Columna genero
 - Columna Actor principal

Dependencias:

Encontre en internet que existen 3 tipos de depndencias (Funcional, parcial y transitiva).

### Dependencias funcionales:
 - id_pelicula --> Titulo
 - id_pelicula --> Director
 - id_pelicula --> año_estreno
 - id_pelicula --> genero
 - id_pelicula --> actor principal
 - id_pelicula --> actor secundario
 - id_pelicula --> pais de origen

 no tenemos informacion para identificar otras dependencias.      
 
2. Descompón la tabla Peliculas en varias tablas siguiendo las reglas de normalización hasta alcanzar la 3FN.

Descomponemos la tabla peliculas asi:

 - Cramos una tabla directores  e insertamos los datos de lso directores 
 - Creamos una tabla de generos e insertamos los valores de generos
 - creamos una tabla de actores e insertamos los valores de actores principales
 - como hacemos todo en un mismo codigo ahora debemos ejecutar un omando que elimine la tabla que existe llamda peliculas el comando es: 
    DROP TABLE IF EXISTS peliculas;
 - Creamos la tabla Peliculas normalizada (es decir con sus claves foraneas correspondientes).

 el codigo de la normalizacion de la tabla de peliculas seria el siguiente:

 CREATE DATABASE IF NOT EXISTS lab1;
	
	use lab1;
	
	DROP DATABASE IF EXISTS lab1;
	
	CREATE DATABASE lab1;
	
	USE lab1;
	
	-- Ejercicio 1: Base de Datos de Películas
	CREATE TABLE Peliculas (
	    id_pelicula INT PRIMARY KEY,
	    titulo VARCHAR(255),
	    director VARCHAR(255),
	    año_estreno INT,
	    genero VARCHAR(255),
	    actor_principal VARCHAR(255),
	    actor_secundario VARCHAR(255),
	    pais_origen VARCHAR(255)
	);	
	
	INSERT INTO Peliculas (id_pelicula, titulo, director, año_estreno, genero, actor_principal, actor_secundario, pais_origen) VALUES
	(1, 'The Shawshank Redemption', 'Frank Darabont', 1994, 'Drama', 'Tim Robbins', 'Morgan Freeman', 'USA'),
	(2, 'The Godfather', 'Francis Ford Coppola', 1972, 'Crime', 'Marlon Brando', 'Al Pacino', 'USA'),
	(3, 'The Dark Knight', 'Christopher Nolan', 2008, 'Action', 'Christian Bale', 'Heath Ledger', 'USA'),
	(4, 'Forrest Gump', 'Robert Zemeckis', 1994, 'Drama', 'Tom Hanks', 'Robin Wright', 'USA'),
	(5, 'Pulp Fiction', 'Quentin Tarantino', 1994, 'Crime', 'John Travolta', 'Samuel L. Jackson', 'USA'),
	(6, 'Inception', 'Christopher Nolan', 2010, 'Sci-Fi', 'Leonardo DiCaprio', 'Joseph Gordon-Levitt', 'USA'),
	(7, 'Titanic', 'James Cameron', 1997, 'Romance', 'Leonardo DiCaprio', 'Kate Winslet', 'USA'),
	(8, 'The Matrix', 'The Wachowskis', 1999, 'Sci-Fi', 'Keanu Reeves', 'Laurence Fishburne', 'USA'),
	(9, 'Avatar', 'James Cameron', 2009, 'Sci-Fi', 'Sam Worthington', 'Zoe Saldana', 'USA'),
	(10, 'Gladiator', 'Ridley Scott', 2000, 'Action', 'Russell Crowe', 'Joaquin Phoenix', 'USA');
	
	-- Normalizacion tabla peliculas

	-- Creamos tabla directores
	CREATE TABLE Directores (
    id_director INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(255) NOT NULL,
    pais_origen VARCHAR(255) -- Si un director está asociado con un solo país
	);

	-- Insertamos datos en la tabla Directores
	INSERT INTO Directores (nombre, pais_origen) VALUES
	('Frank Darabont', 'USA'),
	('Francis Ford Coppola', 'USA'),
	('Christopher Nolan', 'USA'),
	('Robert Zemeckis', 'USA'),
	('Quentin Tarantino', 'USA'),
	('James Cameron', 'USA'),
	('The Wachowskis', 'USA'),
	('Ridley Scott', 'USA');

	-- Creamos tabla generos
	CREATE TABLE Generos (
    id_genero INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL
	);

	-- Insertamos datos en la tabla Generos
	INSERT INTO Generos (nombre) VALUES
	('Drama'),
	('Crime'),
	('Action'),
	('Sci-Fi'),
	('Romance');

	-- Creamos tabla Actores
	CREATE TABLE Actores (
    id_actor INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(255) NOT NULL
	);

	-- Insertar datos en la tabla Actores
	INSERT INTO Actores (nombre) VALUES
	('Tim Robbins'),
	('Morgan Freeman'),
	('Marlon Brando'),
	('Al Pacino'),
	('Christian Bale'),
	('Heath Ledger'),
	('Tom Hanks'),
	('Robin Wright'),
	('John Travolta'),
	('Samuel L. Jackson'),
	('Leonardo DiCaprio'),
	('Joseph Gordon-Levitt'),
	('Kate Winslet'),
	('Keanu Reeves'),
	('Laurence Fishburne'),
	('Sam Worthington'),
	('Zoe Saldana'),
	('Russell Crowe'),
	('Joaquin Phoenix');

	DROP TABLE IF EXISTS peliculas;

	CREATE TABLE Peliculas (
    id_pelicula INT AUTO_INCREMENT PRIMARY KEY,
    titulo VARCHAR(255) NOT NULL,
    id_director INT,
    año_estreno INT,
    id_genero INT,
    id_actor_principal INT,
    id_actor_secundario INT,
    FOREIGN KEY (id_director) REFERENCES Directores(id_director),
    FOREIGN KEY (id_genero) REFERENCES Generos(id_genero),
    FOREIGN KEY (id_actor_principal) REFERENCES Actores(id_actor),
    FOREIGN KEY (id_actor_secundario) REFERENCES Actores(id_actor)
	);


<img src="./img/Peliculas ER.png" alt="ER Tabla peliculas" width="300">



## Ejercicio 2: Normalización de una Base de Datos de Coches
### Descripción: 
### La tabla Coches contiene información sobre coches, incluyendo detalles del propietario y el taller de servicio. Esta tabla no está normalizada.

### Instrucciones:
Identifica las posibles redundancias y dependencias.
Descompón la tabla Coches en varias tablas siguiendo las reglas de normalización hasta alcanzar la 3FN.

### Dependencias funcionales:

- id_coche -> marca
- id_coche -> modelo
- id_coche -> año
- id_coche -> propietario_nombre
- id_coche -> propietario_direccion
- id_coche -> propietario_telefono
- id_coche -> taller_nombre
- id_coche -> taller_direccion

### Dependencias Transitivas

Podemos observar que:

- propietario_direccion y propietario_telefono dependen de propietario_nombre. Similarmente, taller_direccion depende de taller_nombre.

## Normalización a 3FN
Para normalizar la tabla Coches hasta la Tercera Forma Normal (3FN), seguiremos estos pasos:

1. 1FN (Primera Forma Normal): Esta en valores atomicos desde la creacion de la tabla.
2. 2FN (Segunda Forma Normal): Eliminar dependencias parciales.

### Paso 1: Crear Tablas para separar la informacion:

- Tabla Propietarios
- Tabla Talleres
- Tabla Coches (Con claves foraneas correspondientes)

CREATE DATABASE IF NOT EXISTS lab1;
	
	use lab1;
	
	DROP DATABASE IF EXISTS lab1;
	
	CREATE DATABASE lab1;
	
	USE lab1;
	
	-- Ejercicio 2: Base de Datos de Coches
	CREATE TABLE Coches (
	    id_coche INT PRIMARY KEY,
	    marca VARCHAR(255),
	    modelo VARCHAR(255),
	    año INT,
	    propietario_nombre VARCHAR(255),
	    propietario_direccion VARCHAR(255),
	    propietario_telefono VARCHAR(255),
	    taller_nombre VARCHAR(255),
	    taller_direccion VARCHAR(255)
	);
	
	-- Insertar datos en la tabla Coches
	INSERT INTO Coches (id_coche, marca, modelo, año, propietario_nombre, propietario_direccion, propietario_telefono, taller_nombre, taller_direccion) VALUES
	(1, 'Toyota', 'Corolla', 2018, 'Juan Pérez', 'Calle Principal 123', '123-456-7890', 'Taller Juan', 'Avenida Central 456'),
	(2, 'Honda', 'Civic', 2017, 'María López', 'Avenida Libertad 456', '987-654-3210', 'Taller Martínez', 'Calle Independencia 789'),
	(3, 'Ford', 'Mustang', 2020, 'Pedro García', 'Calle Sur 789', '456-789-0123', 'Taller Rodríguez', 'Avenida Norte 123'),
	(4, 'Chevrolet', 'Camaro', 2019, 'Ana Martínez', 'Calle Este 567', '321-654-0987', 'Taller Sánchez', 'Avenida Oeste 567'),
	(5, 'Nissan', 'Altima', 2016, 'Luisa Torres', 'Avenida Central 789', '789-012-3456', 'Taller Gómez', 'Calle Principal 234'),
	(6, 'BMW', 'X5', 2021, 'Carlos Ruiz', 'Calle Norte 345', '210-987-6543', 'Taller López', 'Avenida Sur 890'),
	(7, 'Mercedes-Benz', 'C-Class', 2019, 'Sofía Rodríguez', 'Avenida Oeste 890', '543-210-9876', 'Taller Martín', 'Calle Este 678'),
	(8, 'Audi', 'A4', 2018, 'Javier Gómez', 'Calle Este 789', '012-345-6789', 'Taller Pérez', 'Avenida Norte 345'),
	(9, 'Hyundai', 'Elantra', 2017, 'Laura Sánchez', 'Avenida Libertad 678', '876-543-2109', 'Taller Hernández', 'Calle Sur 456'),
	(10, 'Kia', 'Optima', 2019, 'Diego Martín', 'Calle Principal 567', '234-567-8901', 'Taller Ruiz', 'Avenida Central 678');
	
	-- Normalizacion Coches

	-- Separamos la informacion de propietarios
	CREATE TABLE Propietarios (
    id_propietario INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(255) NOT NULL,
    direccion VARCHAR(255),
    telefono VARCHAR(255)
	);
	
	-- Insertar datos en la tabla Propietarios
	INSERT INTO Propietarios (nombre, direccion, telefono) VALUES
	('Juan Pérez', 'Calle Principal 123', '123-456-7890'),
	('María López', 'Avenida Libertad 456', '987-654-3210'),
	('Pedro García', 'Calle Sur 789', '456-789-0123'),
	('Ana Martínez', 'Calle Este 567', '321-654-0987'),
	('Luisa Torres', 'Avenida Central 789', '789-012-3456'),
	('Carlos Ruiz', 'Calle Norte 345', '210-987-6543'),
	('Sofía Rodríguez', 'Avenida Oeste 890', '543-210-9876'),
	('Javier Gómez', 'Calle Este 789', '012-345-6789'),
	('Laura Sánchez', 'Avenida Libertad 678', '876-543-2109'),
	('Diego Martín', 'Calle Principal 567', '234-567-8901');
	
	CREATE TABLE Talleres (
    id_taller INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(255) NOT NULL,
    direccion VARCHAR(255)
	);

	-- Insertar datos en la tabla Talleres
	INSERT INTO Talleres (nombre, direccion) VALUES
	('Taller Juan', 'Avenida Central 456'),
	('Taller Martínez', 'Calle Independencia 789'),
	('Taller Rodríguez', 'Avenida Norte 123'),
	('Taller Sánchez', 'Avenida Oeste 567'),
	('Taller Gómez', 'Calle Principal 234'),
	('Taller López', 'Avenida Sur 890'),
	('Taller Martín', 'Calle Este 678'),
	('Taller Pérez', 'Avenida Norte 345'),
	('Taller Hernández', 'Calle Sur 456'),
	('Taller Ruiz', 'Avenida Central 678');

	DROP TABLE IF EXISTS Coches;

	CREATE TABLE Coches (
    id_coche INT AUTO_INCREMENT PRIMARY KEY,
    marca VARCHAR(255),
    modelo VARCHAR(255),
    año INT,
    id_propietario INT,
    id_taller INT,
    FOREIGN KEY (id_propietario) REFERENCES Propietarios(id_propietario),
    FOREIGN KEY (id_taller) REFERENCES Talleres(id_taller)
	);	

	-- Insertar datos en la tabla Coches
	INSERT INTO Coches (marca, modelo, año, id_propietario, id_taller) VALUES
	('Toyota', 'Corolla', 2018, 1, 1),
	('Honda', 'Civic', 2017, 2, 2),
	('Ford', 'Mustang', 2020, 3, 3),
	('Chevrolet', 'Camaro', 2019, 4, 4),
	('Nissan', 'Altima', 2016, 5, 5),
	('BMW', 'X5', 2021, 6, 6),
	('Mercedes-Benz', 'C-Class', 2019, 7, 7),
	('Audi', 'A4', 2018, 8, 8),
	('Hyundai', 'Elantra', 2017, 9, 9),
	('Kia', 'Optima', 2019, 10, 10);

3FN (Tercera Forma Normal): Eliminar dependencias transitivas.

### Resultado

La tabla Coches original ha sido descompuesta en tres tablas normalizadas (Coches, Propietarios, Talleres) siguiendo las reglas de normalización hasta alcanzar la 3FN. Esto elimina redundancias y mejora la integridad de los datos, haciendo que la base de datos sea más eficiente y fácil de mantener

<img src="./img/ER_Coches.png" alt="ER Coches" width="300">


 
