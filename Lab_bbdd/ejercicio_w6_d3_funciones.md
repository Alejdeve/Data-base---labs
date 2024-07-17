# 1. Grado y cardinalidad

### Basándote en los ejercicios de ayer, indica el grado y la cardinalidad de las tablas del Lab1.

Primero, vamos a revisar el grado y la cardinalidad de las tablas del Lab1 (el ejemplo de la biblioteca), luego crearemos un modelo conceptual para tres sistemas y, finalmente, trabajaremos en una base de datos de películas con sus respectivas funciones.

## Parte 1: Grado y Cardinalidad de las Tablas del Lab1

### Definición

Grado: Número de atributos (columnas) en una tabla.
Cardinalidad: Número de registros (filas) en una tabla.
Tablas del Lab1 (Biblioteca)

### Tabla Libros

Grado: 4 (id_libro, titulo, anio_publicacion, genero)
Cardinalidad: Número de libros en la tabla, por ejemplo, si hay 5 libros, la cardinalidad es 5.

### Tabla Autores

Grado: 2 (id_autor, nombre)
Cardinalidad: Número de autores en la tabla.

### Tabla Ejemplares

Grado: 4 (id_ejemplar, id_libro, ubicacion, estado)
Cardinalidad: Número de ejemplares en la tabla.

### Tabla Editoriales

Grado: 2 (id_editorial, nombre)
Cardinalidad: Número de editoriales en la tabla.

### Tabla LibroAutor

Grado: 2 (id_libro, id_autor)
Cardinalidad: Número de relaciones entre libros y autores.

# 2. Crear un Modelo Conceptual de Base de Datos

## Objetivo

El objetivo de este ejercicio es diseñar un modelo conceptual de base de datos utilizando el modelo entidad-relación (ERD). Esto implica identificar las entidades, atributos y relaciones necesarias para representar la información de un sistema específico.

Quiero que desarroller 3 sistemas completos para sistemas reales. 

Por ejemplo:
 
 - una biblioteca (que es el ejemplo que te voy a poner a continuación).
 - un supermercado.  
 - una tienda de electrodomésticos.

Elige 3 temas que te motiven, porque podrás reutilizar este trabajo más adelante.

## Descripción del Problema

Puedes crear la base de datos sobre lo que quieras, en el ejemplo lo haremos sobre una biblioteca. La biblioteca necesita gestionar información sobre libros, autores, géneros literarios, miembros y préstamos de libros. Los requisitos del sistema son los siguientes:

Libros: La biblioteca tiene una colección de libros, y cada libro tiene un título, ISBN, fecha de publicación y puede pertenecer a uno o más géneros.
Autores: Cada libro puede tener uno o más autores. Los autores tienen un nombre, una fecha de nacimiento y una nacionalidad.
Géneros: Los libros pertenecen a géneros literarios. Cada género tiene un nombre y una descripción.
Miembros: La biblioteca tiene miembros que pueden tomar prestados libros. Los miembros tienen un número de identificación, nombre, dirección, teléfono y correo electrónico.
Préstamos: Los miembros pueden tomar prestados libros. Cada préstamo tiene una fecha de inicio, una fecha de devolución y puede estar asociado a uno o más libros y un miembro.
Instrucciones
Identificar Entidades y Atributos:

Libros: título, ISBN, fecha de publicación.
Autores: nombre, fecha de nacimiento, nacionalidad.
Géneros: nombre, descripción.
Miembros: número de identificación, nombre, dirección, teléfono, correo electrónico.
Préstamos: fecha de inicio, fecha de devolución.
Identificar Relaciones:

Un libro puede tener uno o más autores.
Un autor puede haber escrito uno o más libros.
Un libro puede pertenecer a uno o más géneros.
Un género puede tener uno o más libros.
Un miembro puede tomar prestado uno o más libros.
Un libro puede ser tomado prestado por uno o más miembros (en diferentes ocasiones).
Un préstamo está asociado a un miembro y uno o más libros.
Dibujar el Diagrama ER:

Usa un software de diagramación o dibuja a mano el diagrama ER que represente las entidades, atributos y relaciones identificadas.
Describir las Cardinalidades:

Define las cardinalidades de cada relación (por ejemplo, uno a muchos, muchos a muchos).
Ejemplo de Modelo Conceptual
A continuación, se muestra un ejemplo simplificado del modelo conceptual en formato texto.

Entidades y Atributos
Libro

Título
ISBN
Fecha de Publicación
Autor

Nombre
Fecha de Nacimiento
Nacionalidad
Género

Nombre
Descripción
Miembro

Número de Identificación
Nombre
Dirección
Teléfono
Correo Electrónico
Préstamo

Fecha de Inicio
Fecha de Devolución

### Relaciones

Libro-Autor: Un libro puede tener uno o más autores, y un autor puede haber escrito uno o más libros.
Libro-Género: Un libro puede pertenecer a uno o más géneros, y un género puede tener uno o más libros.
Miembro-Préstamo: Un miembro puede tener uno o más préstamos, y un préstamo está asociado a un miembro.
Préstamo-Libro: Un préstamo puede incluir uno o más libros, y un libro puede ser incluido en diferentes préstamos a lo largo del tiempo.
Entrega
Entrega tu modelo conceptual en un archivo PDF o una imagen clara del diagrama ER extraído del Dbeaver, junto con una breve descripción de las entidades, atributos y relaciones como se muestra en el ejemplo anterior.

# Mis bases de datos:

## Escuela de surf

La escuela de surf WAVEADDICT necesita gestionar información sobre:

- Tablas de surf y sus alquileres.
- Neoprenos y sus alquileres.
- Datos de Socios (personas que pagan una cuota mensual para tener acceso a descuentos y otros beneficios).
- Estudiantes (personas que toman clases de surf).

### Los requisitos del sistema son los siguientes:

### Tablas de Surf

- Cada tabla de surf tiene un identificador único, un modelo, una longitud y una condición (nueva, usada).

### Neoprenos

- Cada neopreno tiene un identificador único, una talla, un grosor y una condición (Corto, Largo).

### Alquileres de Tablas

- Cada alquiler de tabla tiene un identificador único, una fecha de inicio, una fecha de fin y está asociado a una tabla y un socio.

### Alquileres de Neoprenos

- Cada alquiler de neopreno tiene un identificador único, una fecha de inicio, una fecha de fin y está asociado a un neopreno y un socio.

## Socios

- Cada socio tiene un identificador único, un nombre, una dirección, un teléfono y un correo electrónico.

### Estudiantes

- Cada estudiante tiene un identificador único, un nombre, una dirección, un teléfono, un correo electrónico y un nivel de habilidad (principiante, intermedio, avanzado).

## Instrucciones

### 1. Identificar Entidades y Atributos

### Tablas de Surf
id_tabla
modelo
longitud
condicion

### Neoprenos
id_neopreno
talla
grosor
condicion

### Alquileres de Tablas
id_alquiler_tabla
fecha_inicio
fecha_fin
id_tabla
id_socio

### Alquileres de Neoprenos
id_alquiler_neopreno
fecha_inicio
fecha_fin
id_neopreno
id_socio

### Socios
id_socio
nombre
direccion
telefono
email

### Estudiantes
id_estudiante
nombre
direccion
telefono
email
nivel_habilidad

### 2. Identificar Relaciones

- Un socio puede alquilar una o más tablas.
- Una tabla puede ser alquilada por diferentes socios en distintos momentos.
- Un socio puede alquilar uno o más neoprenos.
- Un neopreno puede ser alquilado por diferentes socios en distintos momentos.
- Un socio puede ser también un estudiante.
- Un estudiante puede tomar clases (una relación más detallada si se desean agregar clases y horarios).

### 3. Dibujar el Diagrama ER

Usando una herramienta de diagramación (como DBeaver, Draw.io o similar), crea el diagrama ER con las entidades, atributos y relaciones identificadas.

<img src="../img/ER_SURF.png" alt="ER surf" width="300">

### 4. Describir las Cardinalidades

### Alquileres de Tablas
Un socio puede tener muchos alquileres de tablas (1 a N).
Una tabla puede estar en muchos alquileres (1 a N).

### Alquileres de Neoprenos
Un socio puede tener muchos alquileres de neoprenos (1 a N).
Un neopreno puede estar en muchos alquileres (1 a N).

### Socios y Estudiantes
Un socio puede ser también un estudiante, y viceversa (1 a 1 si son la misma persona).

## Modelo Conceptual en Formato Texto

## Entidades y Atributos

### Tablas de Surf
id_tabla (Primary Key)
modelo
longitud
condicion

### Neoprenos
id_neopreno (Primary Key)
talla
grosor
condicion

### Alquileres de Tablas
id_alquiler_tabla (Primary Key)
fecha_inicio
fecha_fin
id_tabla (Foreign Key)
id_socio (Foreign Key)

### Alquileres de Neoprenos
id_alquiler_neopreno (Primary Key)
fecha_inicio
fecha_fin
id_neopreno (Foreign Key)
id_socio (Foreign Key)

### Socios
id_socio (Primary Key)
nombre
direccion
telefono
email

### Estudiantes
id_estudiante (Primary Key)
nombre
direccion
telefono
email
nivel_habilidad
Relaciones

### Alquileres de Tablas
Un socio puede tener muchos alquileres de tablas, y una tabla puede estar en muchos alquileres.
Cardinalidad: (1 socio a N alquileres), (1 tabla a N alquileres).

### Alquileres de Neoprenos
Un socio puede tener muchos alquileres de neoprenos, y un neopreno puede estar en muchos alquileres.
Cardinalidad: (1 socio a N alquileres), (1 neopreno a N alquileres).

## Implementación en SQL

A continuación se muestra cómo implementar esto en SQL:

## Restaurante

## Supermercado