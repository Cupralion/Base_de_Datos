En la BD utilizada en clase realiza las siguientes consultas:

* La tabla empleado
* 
*

![image](https://user-images.githubusercontent.com/104279605/172028115-fd669be9-4d75-4cc4-9a31-aa9df281210c.png)

* Los titulos de las revistas

*

**![image](https://user-images.githubusercontent.com/104279605/172028159-98a57ef2-b1eb-492c-aa28-eaa62b063418.png)

* Los nombres, apellidos y especialidad de los periodostas

*

![image](https://user-images.githubusercontent.com/104279605/172028198-9484f511-876d-40a2-a152-bc964f8fd24c.png)

*

* Muestra los empleados que estan en x sucursal

![image](https://user-images.githubusercontent.com/104279605/172028629-6abfa598-4170-4b47-a551-ba4562ecf24b.png)

*

* Muestra que periodistas colaboraron en x revista y en que sucursal se publico la revista

![image](https://user-images.githubusercontent.com/104279605/172029434-d724986c-b41d-4473-bdf5-1916765f44c6.png)

*

* Mustra que seccion esta en x revista, en que sucursal se imprimio y que empleados estan en esa sucursal.

![image](https://user-images.githubusercontent.com/104279605/172490833-840b7caf-26e2-4829-8ebc-81572ad7d4c5.png)


*


* En la tabla peridistas muestra solo los que escriban sobre cine

![image](https://user-images.githubusercontent.com/104279605/172491455-1b5e5d8d-00cc-4307-b976-628fd70d6822.png)

*


* De la tabla revistas muestra las que sean de publicacion quincenal

![image](https://user-images.githubusercontent.com/104279605/172492085-d02a942e-ebc5-4b59-927e-2954270525fb.png)

*

* Muestra el nombre de ka revista que se hayan impreso despues del 30 de septiembre del 2021

*
![image](https://user-images.githubusercontent.com/104279605/172492670-3f84e2ca-273e-4120-9ccf-858f94334eed.png)

*

* Muestra el nombre de la revista que se haya publicado en la sucursal 1 cuyos ejemplares tengan más de 80 páginas.

https://www.db-fiddle.com/f/iAUjGLoFoHtam2pK68Xh1B/1




link mi codigo https://www.db-fiddle.com/f/mzBz8s8aYEYaZWEZVVUHRa/4

codigo
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
INSERT INTO empleado VALUES ('EMP_01','ANGELICA','BLANCAS','MIRANDA',5554363869,'suc-01');
INSERT INTO empleado VALUES ('EMP_02','DAVID','ASPEITIA','ESCOBEDO',5553949493,'suc-02');
INSERT INTO empleado VALUES ('EMP_03','ANGEL','GALINDO','HERAS',5582226168,'suc-03');
INSERT INTO empleado VALUES ('EMP_04','ISMAEL','FERNANDEZ','HERNADEZ',5529145878,'suc-04');
INSERT INTO empleado VALUES ('EMP_05','MAURICIO','ANDA','JUAREZ',5514795863,'suc-05');
INSERT INTO empleado VALUES ('EMP_06','ALONSO','BLANCO','ANGELES',5629800966,'suc-06');
INSERT INTO empleado VALUES ('EMP_07','ALMA','SALAZAR','HUERTA',5553872837,'suc-07');
INSERT INTO empleado VALUES ('EMP_08','BLANCA','SANTOS','SANTIAGO',5562758700,'suc-08');
INSERT INTO empleado VALUES ('EMP_09','IGNACIO','HERNANDEZ','HERNNDEZ',5569874632,'suc-09');
INSERT INTO empleado VALUES ('EMP_10','MAURICIO','MARQUEZ','CHAVEZ',5529145877,'suc-10');
--tabla_secciones
  CREATE TABLE secciones (
  id_seccion INT UNSIGNED PRIMARY KEY,
  extension VARCHAR(20) NOT NULL,
  titulo_seccion VARCHAR(100) NOT NULL,
  num_reg3 VARCHAR(50) NOT NULL,
  FOREIGN KEY (num_reg3) REFERENCES revista(num_reg) 
  );
--insertamos_los_datos_secciones
INSERT INTO secciones VALUES (1,'esp','espectaculos','REV_098');
INSERT INTO secciones VALUES (2,'dep','deportes','REV_099');
INSERT INTO secciones VALUES (3,'pol','politica','REV_100');
INSERT INTO secciones VALUES (4,'cin','cine','REV_101');
INSERT INTO secciones VALUES (5,'hog','hogar','REV_102');
INSERT INTO secciones VALUES (6,'cul','cultura','REV_103');
INSERT INTO secciones VALUES (7,'vid','videojuegos','REV_098');
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
INSERT INTO ejemplar VALUES ('M01',4855,56,'2021/09/23','REV_098');
INSERT INTO ejemplar VALUES ('M02',1234,89,'2021/09/30','REV_099');
INSERT INTO ejemplar VALUES ('M03',5343,78,'2021/10/09','REV_100');
INSERT INTO ejemplar VALUES ('M04',5654,90,'2022/04/06','REV_101');
INSERT INTO ejemplar VALUES ('M05',3434,100,'2022/03/15','REV_102');
INSERT INTO ejemplar VALUES ('M06',6546,100,'2021/06/01','REV_103');
INSERT INTO ejemplar VALUES ('M07',4534,56,'2022/05/15','REV_098');
--tabla_sucursal_revista
CREATE TABLE sucursal_revista (
num_reg1 VARCHAR(50) NOT NULL,
codigo_sucursal2 VARCHAR(50) NOT NULL,
FOREIGN KEY (num_reg1) REFERENCES revista(num_reg),
FOREIGN KEY (codigo_sucursal2) REFERENCES sucursal(codigo_sucursal)
);
--insertamos_los_datos_sucursal_revista
INSERT INTO sucursal_revista VALUES ('REV_098','suc-01');
INSERT INTO sucursal_revista VALUES ('REV_099','suc-02');
INSERT INTO sucursal_revista VALUES ('REV_100','suc-03');
INSERT INTO sucursal_revista VALUES ('REV_101','suc-04');
INSERT INTO sucursal_revista VALUES ('REV_102','suc-05');
INSERT INTO sucursal_revista VALUES ('REV_103','suc-06');
INSERT INTO sucursal_revista VALUES ('REV_098','suc-07');
INSERT INTO sucursal_revista VALUES ('REV_099','suc-08');
INSERT INTO sucursal_revista VALUES ('REV_100','suc-09');
INSERT INTO sucursal_revista VALUES ('REV_101','suc-10');
--tabla_revista_periodista
CREATE TABLE revista_periodista (
num_reg2 VARCHAR(50) NOT NULL,
nif_periodista1 VARCHAR(50) NOT NULL,
FOREIGN KEY (num_reg2) REFERENCES revista(num_reg),
FOREIGN KEY (nif_periodista1) REFERENCES periodista(nif_periodista)
);
--insertamos_los_datos_revista_periodista
INSERT INTO revista_periodista VALUES ('REV_098','PER_01');
INSERT INTO revista_periodista VALUES ('REV_099','PER_02');
INSERT INTO revista_periodista VALUES ('REV_100','PER_03');
INSERT INTO revista_periodista VALUES ('REV_101','PER_04');
INSERT INTO revista_periodista VALUES ('REV_102','PER_05');
INSERT INTO revista_periodista VALUES ('REV_103','PER_06');
INSERT INTO revista_periodista VALUES ('REV_098','PER_07');
INSERT INTO revista_periodista VALUES ('REV_099','PER_08');
INSERT INTO revista_periodista VALUES ('REV_100','PER_09');
INSERT INTO revista_periodista VALUES ('REV_101','PER_10');
INSERT INTO revista_periodista VALUES ('REV_102','PER_11');
INSERT INTO revista_periodista VALUES ('REV_103','PER_12');
