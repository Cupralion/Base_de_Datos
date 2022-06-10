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

![image](https://user-images.githubusercontent.com/104279605/171977951-85d9e465-a00a-4f84-b998-bb45b0ad6ff4.png)


Codigo

https://www.db-fiddle.com/f/mzBz8s8aYEYaZWEZVVUHRa/5



codigo nuevo

CREATE DATABASE editorial;
USE editorial;
--tabla_sucursal
CREATE TABLE sucursal(
  codigo_sucursal VARCHAR(50) PRIMARY KEY,
  domicilio VARCHAR(200) NOT NULL,
  telefono_sucursal BIGINT UNSIGNED UNIQUE,
  ciudad VARCHAR(50),
  provincia VARCHAR(50)
  );  
--insertamos_los_datos_sucursal  
INSERT INTO sucursal VALUES ('suc-01','Tenayuca 15, Colonia Porvenir',5573485948,'CDMX','Miguel Hidalgo');
INSERT INTO sucursal VALUES ('suc-02','Ahuehuetes 24, Colona Reynosa',3395847649,'GUADALAJARA','Zaragoza');
INSERT INTO sucursal VALUES ('suc-03','San Juan 12, Colonia Electricistas',7293840947,'TOLUCA','Toluca');
INSERT INTO sucursal VALUES ('suc-04','Manuel Buendía 948, Colonia Reforma',8293459375,'MONTERREY','Revolucion');
INSERT INTO sucursal VALUES ('suc-05','Petroleos 12, Colonia Alabama',7394850983,'QUERETARO','Juarez');
INSERT INTO sucursal VALUES ('suc-06','Petén 1209, Roma Norte',5587394785,'CDMX','GAM');
INSERT INTO sucursal VALUES ('suc-07','Tlahuac 10, Colonia Reyes',4593849058,'PUEBLA','Oriental');
INSERT INTO sucursal VALUES ('suc-08','Anaxagoras 15, Polanco',3384909859,'CANCUN','cancun');
INSERT INTO sucursal VALUES ('suc-09','Miguel Hidalgo 98, Colonia Angustura',3338930403,'GUADALAJARA','Zapopan');
INSERT INTO sucursal VALUES ('suc-10','Cervantes 56, Colonia Juárez',2288473845,'TIJUANA','Hidalgo');
--tabla_revista
CREATE TABLE revista(
  num_reg VARCHAR(50) PRIMARY KEY,
  titulo_revista VARCHAR(100) NOT NULL UNIQUE,
  tipo VARCHAR(100) NOT NULL UNIQUE,
  periodicidad VARCHAR(100)
  );
--insertamos_los_datos_revista
INSERT INTO revista VALUES ('REV_098','POLITICA HOY','POLITICA','SEMANAL');
INSERT INTO revista VALUES ('REV_099','EMOCION DEPORTIVA','DEPORTIVA','QUINCENAL');
INSERT INTO revista VALUES ('REV_100','MUNDO ROSA','ESPECTACULOS','SEMANAL');
INSERT INTO revista VALUES ('REV_101','VIDEOGAMER','VIDEOJUEGOS','MENSUAL');
INSERT INTO revista VALUES ('REV_102','CINE HOY','CINE','SEMANAL');
INSERT INTO revista VALUES ('REV_103','TODO EN CULTURA','CULTURAL','MENSUAL');
--tabla_periodista
CREATE TABLE periodista(
  nif_periodista VARCHAR(50) PRIMARY KEY,
  nombre_per VARCHAR(100) NOT NULL,
  apellido_pat_per VARCHAR(100) NOT NULL,
  apellido_mat_per VARCHAR(100) NOT NULL,
  telefono_per BIGINT UNIQUE NOT NULL,
  especialidad VARCHAR(100) NOT NULL
  );
--insertamos_los_datos_periodista
INSERT INTO periodista VALUES ('PER_01','KARLA','JUAREZ','PEREZ',5534563748,'DEPORTES');
INSERT INTO periodista VALUES ('PER_02','BEATRIZ','LOPEZ','ANGELES',7289467349,'POLITICA');
INSERT INTO periodista VALUES ('PER_03','TITO','MARQUEZ','GALINDO',8203978465,'ESPECTACULOS');
INSERT INTO periodista VALUES ('PER_04','ISABEL','SUAREZ','JIMENEZ',8263748987,'VIDEOJUEGOS');
INSERT INTO periodista VALUES ('PER_05','PABLO','FERNANDEZ','DUARTE',5523784938,'CINE');
INSERT INTO periodista VALUES ('PER_06','SERGIO','INFANTE','MORALES',7238946574,'CINE');
INSERT INTO periodista VALUES ('PER_07','CARLOS','GUIZAR','CISNEROS',3398475840,'CULTURA');
INSERT INTO periodista VALUES ('PER_08','JUAN','SALAS','MACIAS',5682394848,'DEPORTES');
INSERT INTO periodista VALUES ('PER_09','PEDRO','RICO','GARAY',5548738495,'POLITICA');                             
INSERT INTO periodista VALUES ('PER_10','ANGEL','HERAS','FUENTES',8236475894,'VIDEOJUEGOS');
INSERT INTO periodista VALUES ('PER_11','CESAR','SAN PEDRO','RODRIGUEZ',4585968495,'CINE');
INSERT INTO periodista VALUES ('PER_12','MAGDA','LIRA','SANCHEZ',7683749504,'POLITICA');
--tabla_empleado
CREATE TABLE empleado (
  nif_emp VARCHAR(50) PRIMARY KEY,
  nombre_emp VARCHAR(100) NOT NULL,
  apellido_pat_emp VARCHAR(100) NOT NULL,
  apellido_mat_emp VARCHAR(100) NOT NULL,
  telefono_emp BIGINT UNIQUE NOT NULL,
  codigo_sucursal1 VARCHAR(50),
  FOREIGN KEY (codigo_sucursal1) REFERENCES sucursal(codigo_sucursal) 
  );
--insertamos_los_datos_empleado
INSERT INTO empleado VALUES ('EMP_01','ANGELICA','BLANCAS','MIRANDA',5554363869,codigo_sucursal1);
INSERT INTO empleado VALUES ('EMP_02','DAVID','ASPEITIA','ESCOBEDO',5553949493,codigo_sucursal1);
INSERT INTO empleado VALUES ('EMP_03','ANGEL','GALINDO','HERAS',5582226168,codigo_sucursal1);
INSERT INTO empleado VALUES ('EMP_04','ISMAEL','FERNANDEZ','HERNADEZ',5529145878,codigo_sucursal1);
INSERT INTO empleado VALUES ('EMP_05','MAURICIO','ANDA','JUAREZ',5514795863,codigo_sucursal1);
INSERT INTO empleado VALUES ('EMP_06','ALONSO','BLANCO','ANGELES',5629800966,codigo_sucursal1);
INSERT INTO empleado VALUES ('EMP_07','ALMA','SALAZAR','HUERTA',5553872837,codigo_sucursal1);
INSERT INTO empleado VALUES ('EMP_08','BLANCA','SANTOS','SANTIAGO',5562758700,codigo_sucursal1);
INSERT INTO empleado VALUES ('EMP_09','IGNACIO','HERNANDEZ','HERNNDEZ',5569874632,codigo_sucursal1);
INSERT INTO empleado VALUES ('EMP_10','MAURICIO','MARQUEZ','CHAVEZ',5529145877,codigo_sucursal1);
--tabla_secciones
  CREATE TABLE secciones (
  id_seccion INT UNSIGNED PRIMARY KEY,
  extension VARCHAR(20) NOT NULL,
  titulo_seccion VARCHAR(100) NOT NULL,
  num_reg3 VARCHAR(50) NOT NULL,
  FOREIGN KEY (num_reg3) REFERENCES revista(num_reg) 
  );
--insertamos_los_datos_secciones
INSERT INTO secciones VALUES (1,'esp','espectaculos',num_reg3);
INSERT INTO secciones VALUES (2,'dep','deportes',num_reg3);
INSERT INTO secciones VALUES (3,'pol','politica',num_reg3);
INSERT INTO secciones VALUES (4,'cin','cine',num_reg3);
INSERT INTO secciones VALUES (5,'hog','hogar',num_reg3);
INSERT INTO secciones VALUES (6,'cul','cultura',num_reg3);
INSERT INTO secciones VALUES (7,'vid','videojuegos',num_reg3);
--tabla_ejemplar
CREATE TABLE ejemplar (
  id_ejemplar VARCHAR(50) PRIMARY KEY,
  numero_ejemplares INT UNSIGNED NOT NULL,
  numero_pagias INT UNSIGNED NOT NULL,
  fecha DATE NOT NULL,
  num_reg4 VARCHAR(50) NOT NULL,
  FOREIGN KEY (num_reg4) REFERENCES revista(num_reg) 
  );
--insertamos_los_datos_ejemplar
INSERT INTO ejemplar VALUES ('M01',4855,56,'23/09/2021',num_reg4);
INSERT INTO ejemplar VALUES ('M02',1234,89,'30/09/2021',num_reg4);
INSERT INTO ejemplar VALUES ('M03',5343,78,'09/10/2021',num_reg4);
INSERT INTO ejemplar VALUES ('M04',5654,90,'06/04/2022',num_reg4);
INSERT INTO ejemplar VALUES ('M05',3434,100,'15/03/2022',num_reg4);
INSERT INTO ejemplar VALUES ('M06',6546,100,'01/06/2021',num_reg4);
INSERT INTO ejemplar VALUES ('M07',4534,56,'15/05/2022',num_reg4);
--tabla_sucursal_revista
CREATE TABLE sucursal_revista (
num_reg1 VARCHAR(50) NOT NULL,
codigo_sucursal1 VARCHAR(50) NOT NULL,
FOREIGN KEY (num_reg1) REFERENCES revista(num_reg),
FOREIGN KEY (codigo_sucursal1) REFERENCES sucursal(codigo_sucursal)
);
--insertamos_los_datos_sucursal_revista
INSERT INTO sucursal_revista VALUES (num_reg1,codigo_sucursal1);
--tabla_revista_periodista
CREATE TABLE revista_periodista (
num_reg2 VARCHAR(50) NOT NULL,
nif_periodista1 VARCHAR(50) NOT NULL,
FOREIGN KEY (num_reg2) REFERENCES revista(num_reg),
FOREIGN KEY (nif_periodista1) REFERENCES periodista(nif_periodista)
);
--insertamos_los_datos_revista_periodista
INSERT INTO revista_periodista VALUES (num_reg2,nif_periodista1);

