# Datos del Estudiante:

- Miguel Figuera
- Seccion 8B
- C.I:V-23.558.789
- Telefono: 0424-1727988

# 1 Primera busqueda:

1. World Tabla city:

- Ejercicio 0.- Localice los datos de las ciudades de “Los Angeles” y “San Francisco”:

```sql
SELECT * FROM city WHERE name IN ('Los Angeles', 'San Francisco');
```

- Ejercicio 1.- Localice los datos de las ciudades de “Barcelona” y “Salamanca” solo de España

```sql
SELECT * FROM city
WHERE name IN ('Barcelona', 'Salamanca')
AND countrycode = 'ESP';
```

- Ejercicio 2.- Localice los datos de las ciudades de “Mérida” y de los distritos “Distrito Federal” solo de México

```sql
SELECT * FROM city
WHERE name = 'Mérida'
OR district = 'Distrito Federal'
AND countrycode = 'MEX';
```

- Ejercicio 3.- Localice los datos de las ciudades de “San Miguel” y de los distritos “San Miguel”

```sql
SELECT * FROM city
WHERE name = 'San Miguel'
OR district = 'San Miguel';
```

2. Dell tabla:products

- Ejercicio 4.- Localice los datos de los clientes de “CHRIS RYAN” y “JUDY GRANT”

```sql
SELECT *
FROM customers
WHERE (UPPER(firstname) = 'CHRIS' AND UPPER(lastname) = 'RYAN')
   OR (UPPER(firstname) = 'JUDY' AND UPPER(lastname) = 'GRANT');
```

- Ejercicio 5.- Localice los datos de los clientes de “WILLIAM POITIER” y “SEAN HOPE” que han gastado “16.99”

```sql

SELECT c.*
FROM customers c
JOIN orders o ON c.customerid = o.customerid
WHERE ((UPPER(c.firstname) = 'WILLIAM' AND UPPER(c.lastname) = 'POITIER') OR (UPPER(c.firstname) = 'SEAN' AND UPPER(c.lastname) = 'HOPE'))
  AND o.totalamount = 16.99;

```

- Ejercicio 6.- Localice los datos de los clientes de las academias “ACADEMY ANGELS” y “ACADEMY HALL”

```sql
SELECT *
FROM products
WHERE title = 'ACADEMY ANGELS' OR title = 'ACADEMY HALL';

```

3. Dell tabla customers:

- Ejercicio 7.- Localice el correo y el teléfono de "VKWMNZ” y de “AQVPNI”

```sql
SELECT email, phone
FROM customers c
WHERE  c.firstname = 'VKWMNZ' OR c.firstname = 'AQVPNI';

```

- Ejercicio 8.- Localice el correo y el teléfono de "ALRECW” y de “ZLVTIK”

```sql
SELECT email, phone
FROM customers
WHERE firstname = 'ALRECW' OR firstname = 'ZLVTIK';


```

- Ejercicio 9.- Localice el correo y el teléfono de los usuarios "user16626”, de “user14212” y de “user1689”

```sql

```

# 2 Ordernar SQL por palabra calve

1. BD: pedidos
   Tabla: empleados

- Ejercicio 0.- Localice los datos de los empleados y ordénelos ascendente por Nombre

```sql
SELECT *
FROM EMPLEADOS
ORDER BY NOMBRE ASC;


```

- Ejercicio 1.- Localice los datos de los empleados y ordénelos ascendente por Apellido

```sql
SELECT *
FROM EMPLEADOS
ORDER BY APELLIDO ASC;

```

- Ejercicio 2.- Localice los datos de los empleados y ordénelos descendente por Nombre

```sql
SELECT *
FROM EMPLEADOS
ORDER BY NOMBRE DESC;


```

2. BD: Pedidos
   Tabla: productos

- Ejercicio 3.- Localice los datos de los productos y ordénelos ascendente por Precio Unitario

```sql

SELECT *
FROM PRODUCTOS
ORDER BY PRECIOUNIT ASC;


```

- Ejercicio 4.- Localice los datos de los productos y ordénelos ascendente por Descripción

```sql

SELECT *
FROM PRODUCTOS
ORDER BY DESCRIPCION ASC;

```

- Ejercicio 5.- Localice los datos de los productos y ordénelos descendente por Existencia

```sql

SELECT *
FROM PRODUCTOS
ORDER BY EXISTENCIA DESC;

```

3. BD: Pedidos
   Tabla: proveedores

- Ejercicio 6.- Localice los datos de los proveedores y ordénelos ascendente por Nombre

```sql

SELECT *
FROM PROVEEDORES
ORDER BY NOMBREPROV ASC;

```

- Ejercicio 7.- Localice los datos de los proveedores y ordénelos descendente por Cedula

```sql

SELECT *
FROM PROVEEDORES
ORDER BY PROVEEDORID DESC;

```

- Ejercicio 8.- Localice los datos de los proveedores y ordénelos descendente por Contacto

```sql

SELECT *
FROM PROVEEDORES
ORDER BY CONTACTO DESC;

```

- Ejercicio 9.- Localice los datos de los proveedores y ordénelos ascendente por Contacto

```sql

SELECT *
FROM PROVEEDORES
ORDER BY CONTACTO ASC;

```

# 3 Busqueda Avanzada

Ejercicio 0.- Localice los datos de los productos suministrados por el proveedor Jorge y ordénelos ascendente

```sql
SELECT P.*
FROM PRODUCTOS P
JOIN PROVEEDORES PR ON P.PROVEEDORID = PR.PROVEEDORID
WHERE PR.CONTACTO LIKE 'JORGE%'
ORDER BY P.DESCRIPCION ASC;

```

Ejercicio 1.- Localice los datos de los productos Lácteos y ordénelos ascendente

```sql

SELECT P.*
FROM PRODUCTOS P
JOIN CATEGORIAS C ON P.CATEGORIAID = C.CATEGORIAID
WHERE C.NOMBRECAT = 'LACTEOS'
ORDER BY P.DESCRIPCION ASC;
```

Ejercicio 2.- Localice las fechas de los pedidos del Sr. Paz y ordénelos descendente

```sql

SELECT O.FECHAORDEN
FROM ORDENES O
JOIN CLIENTES CL ON O.CLIENTEID = CL.CLIENTEID
WHERE CL.NOMBRECONTACTO LIKE '%Paz' -- Ejemplo: 'LORENA PAZ'
ORDER BY O.FECHAORDEN DESC;
```

Ejercicio 3.- Localice los datos de los empleados que atendieron los pedidos del Sr. Paz y ordénelos
ascendente

```sql
SELECT DISTINCT E.*
FROM EMPLEADOS E
JOIN ORDENES O ON E.EMPLEADOID = O.EMPLEADOID
JOIN CLIENTES CL ON O.CLIENTEID = CL.CLIENTEID
WHERE CL.NOMBRECONTACTO LIKE '%Paz'
ORDER BY E.APELLIDO ASC, E.NOMBRE ASC;

```

Ejercicio 4.- Localice los datos de los productos cárnicos y especifica su existencia ordénelos ascendente por cantidad

```sql

SELECT P.*
FROM PRODUCTOS P
JOIN CATEGORIAS C ON P.CATEGORIAID = C.CATEGORIAID
WHERE C.NOMBRECAT = 'CARNICOS'
ORDER BY P.EXISTENCIA ASC;
```

Ejercicio 5.- Localice los datos de los productos cosméticos y ordénelos descendente por precio

```sql

SELECT P.*
FROM PRODUCTOS P
JOIN CATEGORIAS C ON P.CATEGORIAID = C.CATEGORIAID
WHERE C.NOMBRECAT = 'COSMETICOS'
ORDER BY P.PRECIOUNIT DESC;
```

Ejercicio 6.- Localice los datos del empleado que atendió la orden número 10

```sql
SELECT E.*
FROM EMPLEADOS E
JOIN ORDENES O ON E.EMPLEADOID = O.EMPLEADOID
WHERE O.ORDENID = 10;

```

Ejercicio 7.- Localice los datos del producto vendido en la orden número 10 y su precio

```sql

SELECT P.*
FROM PRODUCTOS P
JOIN DETALLE_ORDENES DO ON P.PRODUCTOID = DO.PRODUCTOID
WHERE DO.ORDENID = 10;
```

Ejercicio 8.- Localice los datos del producto vendido en la orden número 10 y su cantidad

```sql
SELECT P.*, DO.CANTIDAD
FROM PRODUCTOS P
JOIN DETALLE_ORDENES DO ON P.PRODUCTOID = DO.PRODUCTOID
WHERE DO.ORDENID = 10;

```

Ejercicio 9.- Localice los datos de los productos suministrados por el proveedor Miraflores y ordénelos descendente

```sql
SELECT P.*
FROM PRODUCTOS P
JOIN PROVEEDORES PR ON P.PROVEEDORID = PR.PROVEEDORID
WHERE PR.NOMBREPROV = 'MIRAFLORES'
ORDER BY P.DESCRIPCION DESC;

```

# 4 Funciones SQL COUNT() AVG() y SUM ()

1. BD: Pedidos

   - Ejercicio 0.- Cuente la cantidad de clientes cuyo nombre es “Juan”.

   ```sql
   SELECT COUNT(*)
   FROM CLIENTES
   WHERE NOMBRECONTACTO LIKE 'JUAN %';
   ```

   - Ejercicio 1.- Calcule el promedio de precios de los productos cárnicos

   ```sql
   SELECT AVG(P.PRECIOUNIT)
   FROM PRODUCTOS P
   JOIN CATEGORIAS C ON P.CATEGORIAID = C.CATEGORIAID
   WHERE C.NOMBRECAT = 'CARNICOS';
   ```

   - Ejercicio 2.- Calcule cuanto hay en existencia de los productos de “DON DIEGO”

   ```sql
   SELECT SUM(P.EXISTENCIA)
   FROM PRODUCTOS P
   JOIN PROVEEDORES PR ON P.PROVEEDORID = PR.PROVEEDORID
   WHERE PR.NOMBREPROV = 'DON DIEGO';
   ```

   - Ejercicio 3.- Cuente la cantidad de los productos lácteos

   ```sql
   SELECT COUNT(P.PRODUCTOID)
   FROM PRODUCTOS P
   JOIN CATEGORIAS C ON P.CATEGORIAID = C.CATEGORIAID
   WHERE C.NOMBRECAT = 'LACTEOS';
   ```

2. BD: World

   - Ejercicio 4.- Calcule la superficie conjunta de los países “Angola, Brasil y Gabón”.

   ```sql
   SELECT SUM(surfacearea)
   FROM country
   WHERE name IN ('Angola', 'Brazil', 'Gabon');
   ```

   - Ejercicio 5.- ¿Cuál es el promedio de vida de los países “Angola, Brasil y Gabón”?

   ```sql
   SELECT AVG(lifeexpectancy)
   FROM country
   WHERE name IN ('Angola', 'Brazil', 'Gabon');
   ```

   - Ejercicio 6.- ¿En cuantos países del mundo se habla español?

   ```sql
   SELECT COUNT(DISTINCT countrycode)
   FROM countrylanguage
   WHERE language = 'Spanish';
   ```

   - Ejercicio 7.- Calcule la población conjunta de los distintos Estados cuyos nombres son “Itabuna,
     Newcastle y Rotherham”.

   ```sql
   SELECT SUM(population)
   FROM city
   WHERE name IN ('Itabuna', 'Newcastle', 'Rotherham');
   ```

   - Ejercicio 8.- Calcule cuantos países son de “South America, y North America”

   ```sql
   SELECT COUNT(*)
   FROM country
   WHERE continent IN ('South America', 'North America');
   ```

   - Ejercicio 9.- Calcule cuantos países tiene un nombre que empieza por “C”

   ```sql
   SELECT COUNT(*)
   FROM country
   WHERE name LIKE 'C%';
   ```
