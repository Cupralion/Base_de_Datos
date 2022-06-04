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

![image](https://user-images.githubusercontent.com/104279605/171970037-6413e176-cf78-419f-9cfe-b5a8cc70dde6.png)


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





CREATE DATABASE editorial;
USE editorial;
--tabla_sucursal
CREATE TABLE sucursal(
  codigo_sucursal VARCHAR(50) PRIMARY KEY,
  domicilio VARCHAR(200) NOT NULL,
  telefono_sucursal BIGINT UNSIGNED UNIQUE
  );
  
INSERT INTO sucursal VALUES('suc-01','Tenayuca 15, Colonia Porvenir',5573485948);
INSERT INTO sucursal VALUES('suc-02','Ahuehuetes 24, Colona Reynosa',3395847649);
INSERT INTO sucursal VALUES('suc-03','San Juan 12, Colonia Electricistas',7293840947);
INSERT INTO sucursal VALUES('suc-04','Manuel Buendía 948, Colonia Reforma',8293459375):
INSERT INTO sucursal VALUES('suc-05','Petroleos 12, Cpolonia Alabama',7394850983);
INSERT INTO sucursal VALUES('suc-06','Petén 1209, Roma Norte',5587394785);
INSERT INTO sucursal VALUES('suc-07','Tlahuac 10, Colonia Reyes',4593849058);
INSERT INTO sucursal VALUES('suc-08','Anaxagoras 15, Polanco',3384909859);
INSERT INTO sucursal VALUES('suc-09','Miguel Hidalgo 98, Colonia Angustura',3338930403);
INSERT INTO sucursal VALUES('suc-10','Cervantes 56, Colonia Juárez',2288473845)




--tabla_revista
CREATE TABLE revista(
  numero_de_registro VARCHAR(50) PRIMARY KEY,
  periodicidad VARCHAR(100),
  titulo_revista VARCHAR(100) NOT NULL UNIQUE,
  tipo VARCHAR(100) NOT NULL UNIQUE
  );
--tabla_periodista
CREATE TABLE periodista(
  nif_periodista VARCHAR(50) PRIMARY KEY,
  especialidad VARCHAR(100) NOT NULL,
  nombre_periodista VARCHAR(100) NOT NULL,
  apellido_periodista VARCHAR(100) NOT NULL,
  telefono_periodista BIGINT UNIQUE NOT NULL
  );
--tabla_empleado
CREATE TABLE empleado (
  nif_empleado VARCHAR(50) PRIMARY KEY,
  nombre_empleado VARCHAR(100) NOT NULL,
  apellido_empleado VARCHAR(100) NOT NULL,
  telefono_empleado BIGINT UNIQUE NOT NULL,
  codigo_sucursal1 VARCHAR(50),
  FOREIGN KEY (codigo_sucursal1) REFERENCES sucursal(codigo_sucursal) 
  );
--tabla_secciones
  CREATE TABLE secciones (
  id_seccion INT UNSIGNED PRIMARY KEY,
  extension VARCHAR(20) NOT NULL,
  titulo_seccion VARCHAR(100) NOT NULL,
  numero_de_registro3 VARCHAR(50) NOT NULL,
  FOREIGN KEY (numero_de_registro3) REFERENCES revista(numero_de_registro) 
  );
--tabla_ejemplar
CREATE TABLE ejemplar (
  id_ejemplar VARCHAR(50) PRIMARY KEY,
  fecha DATE NOT NULL,
  numero_de_pagias INT UNSIGNED NOT NULL,
  numero_de_ejemplares_vendidos INT UNSIGNED NOT NULL,
  numero_de_registro4 VARCHAR(50) NOT NULL,
  FOREIGN KEY (numero_de_registro4) REFERENCES revista(numero_de_registro) 
  );
--tabla_sucursal_revista
CREATE TABLE sucursal_revista (
numero_de_registro1 VARCHAR(50) NOT NULL,
codigo_sucursal1 VARCHAR(50) NOT NULL,
FOREIGN KEY (numero_de_registro1) REFERENCES revista(numero_de_registro),
FOREIGN KEY (codigo_sucursal1) REFERENCES sucursal(codigo_sucursal)
);
--tabla_revista_periodista
CREATE TABLE revista_periodista (
numero_de_registro2 VARCHAR(50) NOT NULL,
nif_periodista1 VARCHAR(50) NOT NULL,
FOREIGN KEY (numero_de_registro2) REFERENCES revista(numero_de_registro),
FOREIGN KEY (nif_periodista1) REFERENCES periodista(nif_periodista)
);


