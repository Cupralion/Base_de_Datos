
## Práctica 4
### Data warehouse

Objetivo: Demostrar la identificación de los elementos que componen data warehouse y
su esquema

Ejercicio:

1. ¿Qué es un DataWarehouse?(valor 2)

R= Un data warehouse es un tipo de sistema de gestión de datos diseñado para habilitar y dar soporte a las tareas de inteligencia empresarial (BI), especialmente las analíticas. Los data warehouses solo se han diseñado para realizar consultas y tareas de análisis, y suelen contener grandes cantidades de datos históricos.

2. Realiza un diseño del modelo en estrella (valor 2)




3. Realiza un diseño del modelo copo de nieve (valor 2)


## Práctica 7
### Funciones en SQL
Objetivo: Demostrar el uso y aplicación en una base de datos para mejorar la gestión

Ejercicio:

1. Calcula el número total de productos que hay en la tabla productos. (valor 4.5)

R= ![image](https://user-images.githubusercontent.com/104279605/173197373-144ea431-a05b-43f0-810d-179351ab3f22.png)
USE tienda;

SELECT COUNT(nom_producto)

FROM  producto 

;


2. Muestra el número total de productos que tiene cada uno de los fabricantes. El listado
también debe incluir los fabricantes que no tienen ningún producto. El resultado
mostrará dos columnas, una con el nombre del fabricante y otra con el número de
productos que tiene. Ordene el resultado descendentemente por el número de
productos. (valor 4.5)

R= ![image](https://user-images.githubusercontent.com/104279605/173197049-755881e9-edf0-4d2a-a335-3563d8b0b1ab.png)

USE tienda;

SELECT marca_fabricante, COUNT(nom_producto)

FROM fabricante INNER JOIN producto ON producto.id_fabricante1=fabricante.id_fabricante

GROUP BY marca_fabricante

ORDER BY COUNT(nom_producto) DESC;


3. Muestra el precio máximo, precio mínimo y precio medio de los productos de cada
uno de los fabricantes. El resultado mostrará el nombre del fabricante junto con los
datos que se solicitan. (valor 4.5)

R= ![image](https://user-images.githubusercontent.com/104279605/173197143-285c0e45-48cd-44ba-9c2f-b93616937827.png)

USE tienda;

SELECT marca_fabricante, MAX(precio), MIN(precio), AVG(precio)

FROM fabricante INNER JOIN producto ON producto.id_fabricante1=fabricante.id_fabricante

GROUP BY marca_fabricante

;


4. Muestra el nombre de cada fabricante, junto con el precio máximo, precio mínimo,
precio medio y el número total de productos de los fabricantes que tienen un precio
medio superior a 200€. Es necesario mostrar el nombre del fabricante. (valor 4.5)

R= ![image](https://user-images.githubusercontent.com/104279605/173197228-d33c3508-bba7-4079-aa8e-7239b276e12a.png)

USE tienda;

SELECT marca_fabricante, MAX(precio), MIN(precio), AVG(precio), COUNT(nom_producto)

FROM fabricante INNER JOIN producto ON producto.id_fabricante1=fabricante.id_fabricante

WHERE precio>200

GROUP BY marca_fabricante

;




