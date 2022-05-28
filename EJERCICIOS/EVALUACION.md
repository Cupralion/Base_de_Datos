## Práctica 1.

1. Introducción a base de datos

Objetivo: Identificar el nivel de comprensión de los conceptos de base de datos,
mediante preguntas abiertas.
 
Preguntas:

1. ¿Cuáles son las cinco funciones principales del administrador de bases de datos?
(valor 1.5)

2. Indíque cinco responsabilidades del sistema gestor de bases de datos (valor 1.5)

3. En una BD al usuario del sistema se le brindarán recursos para realizar diversas
operaciones sobre estos archivos, tales como: (valor 1.5)

4. ¿Qué es un Sistema de Información? (valor 1.5)

## Práctica 2.

2. Diseño de un modelo relacional

Objetivo: Representar desde un modelo entidad relación un problema


Ejercicio:

Tenemos que diseñar una base de datos sobre proveedores y disponemos de la siguiente
información:

Realiza el modelo entidad relación. (valor 6)

Tenemos esta información sobre una cadena editorial:

● La editorial tiene varias sucursales, con su domicilio, teléfono y un código de
sucursal.

● Cada sucursal tiene varios empleados, de los cuales tendremos su nombre,
apellidos, NIF y teléfono. Un empleado trabaja en una única sucursal.

● En cada sucursal se publican varias revistas, de las que almacenaremos su título,
número de registro, periodicidad y tipo.

● Una revista puede ser publicada por varias sucursales.

● La editorial tiene periodistas (que no trabajan en las sucursales) que pueden
escribir artículos para varias revistas. Almacenaremos los mismos datos que para
los empleados, añadiendo su especialidad.

● También es necesario guardar las secciones fijas que tiene cada revista, que
constan de un título y una extensión.

● Para cada revista, almacenaremos información de cada ejemplar, que incluirá la
fecha, número de páginas y el número de ejemplares vendidos.




#Diagrama

![image](https://user-images.githubusercontent.com/104279605/170846124-11f6f7a6-2694-4765-a6e8-da0b5e56ffea.png)


Codigo

CREATE DATABASE editorial;
USE editorial;
--tabla_sucursal
CREATE TABLE sucursal (
codigo_sucursal INT UNSIGNED PRIMARY KEY,
domicilio VARCHAR(100) NOT NULL,
telefono_sucursal INT UNSIGNED NOT NULL
);
--tabla_revista
CREATE TABLE revista (
numero_de_registro INT UNSIGNED PRIMARY KEY,
periodicidad VARCHAR(100) NOT NULL,
titulo_revista VARCHAR(100) NOT NULL,
Tipo VARCHAR(100) NOT NULL
);
--tabla_periodista
CREATE TABLE periodista (
nif_periodista INT UNSIGNED PRIMARY KEY,
especialidad VARCHAR(100) NOT NULL,
nombre_periodista VARCHAR(100) NOT NULL,
apellido_periodista VARCHAR(100) NOT NULL,
telefono_periodista INT UNSIGNED NOT NULL
);
--tabla_empleado
CREATE TABLE empleado (
nif_empleado INT UNSIGNED PRIMARY KEY,
nombre_empleado VARCHAR(100) NOT NULL,
apellido_empleado VARCHAR(100) NOT NULL,
telefono_empleado INT UNSIGNED NOT NULL,
codigo_sucursal1 INT UNSIGNED NOT NULL,
FOREIGN KEY (codigo_sucursal1) REFERENCES sucursal(codigo_sucursal) 
);
--tabla_secciones
CREATE TABLE secciones (
id_seccion INT UNSIGNED PRIMARY KEY,
extension VARCHAR(100) NOT NULL,
titulo_seccion VARCHAR(100) NOT NULL,
numero_de_registro3 INT UNSIGNED NOT NULL,
FOREIGN KEY (numero_de_registro3) REFERENCES revista(numero_de_registro) 
);
--tabla_ejemplar
CREATE TABLE ejemplar (
id_ejemplar INT UNSIGNED PRIMARY KEY,
fecha DATE NOT NULL,
numero_de_pagias INT UNSIGNED NOT NULL,
numero_de_ejemplares_vendidos INT UNSIGNED NOT NULL,
numero_de_registro4 INT UNSIGNED NOT NULL,
FOREIGN KEY (numero_de_registro4) REFERENCES revista(numero_de_registro) 
);
--tabla_sucursal_revista
CREATE TABLE sucursal_revista (
numero_de_registro1 INT UNSIGNED NOT NULL,
codigo_sucursal1 INT UNSIGNED NOT NULL,
FOREIGN KEY (numero_de_registro1) REFERENCES revista(numero_de_registro),
FOREIGN KEY (codigo_sucursal1) REFERENCES sucursal(codigo_sucursal)
);
--tabla_revista_periodista
CREATE TABLE revista_periodista (
numero_de_registro2 INT UNSIGNED NOT NULL,
nif_periodista1 INT UNSIGNED NOT NULL,
FOREIGN KEY (numero_de_registro2) REFERENCES revista(numero_de_registro),
FOREIGN KEY (nif_periodista1) REFERENCES periodista(nif_periodista)
);

