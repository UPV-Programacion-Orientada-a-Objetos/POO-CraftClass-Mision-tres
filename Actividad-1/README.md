## Actividad-3: Desarrollo de un Sistema de Interpretación SQL en Java

**Descripción:**

En esta tarea, se les solicita a los estudiantes desarrollar un sistema de interpretación de sentencias SQL en el lenguaje de programación Java. El sistema debe ser capaz de interpretar sentencias SQL como SELECT, UPDATE, DELETE e INSERT. Además, se deben cumplir las siguientes restricciones:

### Requisitos del Sistema:

1. **Select Anidados:** El sistema debe ser capaz de interpretar sentencias SELECT anidadas. Esto significa que debe ser capaz de procesar consultas SQL que contengan subconsultas SELECT dentro de ellas. Por ejemplo:

   ```sql
   SELECT columna1, (SELECT columna2 FROM tabla2 WHERE condicion) AS resultado FROM tabla1 WHERE condicion;
   ```

   En este ejemplo, se muestra una sentencia SELECT anidada dentro de otra sentencia SELECT.

2. **Sentencias JOIN:** El sistema debe ser capaz de manejar sentencias JOIN, incluyendo INNER JOIN, LEFT JOIN, RIGHT JOIN y OUTER JOIN. Debe ser capaz de combinar datos de múltiples tablas según las condiciones especificadas en las sentencias JOIN. Por ejemplo:

   ```sql
   SELECT columna1, columna2 FROM tabla1
   INNER JOIN tabla2 ON tabla1.id = tabla2.id;
   ```

   En este ejemplo, se utiliza una sentencia INNER JOIN para combinar datos de dos tablas.

3. **Programación con Hilos (Threads):** El sistema debe ser implementado utilizando hilos (Threads) de Java. Deben utilizarse hilos para gestionar las solicitudes de consultas SQL concurrentes de manera eficiente.

### Entregables:

Los estudiantes deben entregar los siguientes elementos:

1. **Código Fuente:** El código fuente completo del sistema de interpretación SQL en Java. Debe estar organizado y comentado de manera adecuada para facilitar la comprensión.

2. **Pruebas Unitarias:** Se deben proporcionar pruebas unitarias exhaustivas para demostrar que el sistema funciona correctamente. Las pruebas deben cubrir una variedad de casos, incluyendo consultas SQL simples y complejas con JOIN y subconsultas.

3. **Archivo Autoejecutable JAR:** Deben crear un archivo JAR autoejecutable que permita a los evaluadores probar el sistema de manera sencilla.

**Evaluación:**

Los proyectos serán evaluados en función de los siguientes criterios:

1. **Funcionalidad:** El sistema debe ser capaz de interpretar y ejecutar correctamente las sentencias SQL especificadas, incluyendo select anidados y sentencias JOIN.

2. **Calidad del Código:** El código fuente debe estar bien estructurado, ser legible y seguir las mejores prácticas de programación en Java.

3. **Pruebas Unitarias:** Las pruebas unitarias deben cubrir una variedad de casos y demostrar que el sistema funciona de manera robusta y sin errores.

4. **Entregables Completos:** Todos los elementos requeridos (código fuente, pruebas unitarias y archivo JAR) deben ser entregados de manera adecuada y a tiempo.

Esta tarea brinda a los estudiantes la oportunidad de aplicar sus conocimientos en programación orientada a objetos y concurrencia en un proyecto práctico. ¡Buena suerte con la tarea!

--

## Datos de prueba

Esquema de base de datos para un almacén que incluye tablas para productos y gestión de inventarios. 

```sql
-- Crear la tabla 'Productos' para almacenar información sobre los productos en el almacén
CREATE TABLE Productos (
    ProductoID INTEGER PRIMARY KEY,
    Nombre TEXT NOT NULL,
    Descripcion TEXT,
    Precio DECIMAL(10, 2) NOT NULL,
    StockInicial INTEGER NOT NULL,
    UnidadMedida TEXT NOT NULL
);

-- Crear la tabla 'Inventario' para realizar un seguimiento de los niveles de inventario de cada producto
CREATE TABLE Inventario (
    InventarioID INTEGER PRIMARY KEY,
    ProductoID INTEGER,
    FechaRegistro DATE NOT NULL,
    CantidadEntrada INTEGER NOT NULL,
    CantidadSalida INTEGER NOT NULL,
    FOREIGN KEY (ProductoID) REFERENCES Productos(ProductoID)
);

-- Crear la tabla 'Proveedores' para almacenar información sobre los proveedores de los productos (opcional)
CREATE TABLE Proveedores (
    ProveedorID INTEGER PRIMARY KEY,
    NombreProveedor TEXT NOT NULL,
    Direccion TEXT,
    Telefono TEXT
);

-- Crear una tabla de relación 'ProductosProveedores' para asociar productos con sus proveedores (opcional)
CREATE TABLE ProductosProveedores (
    ProductoID INTEGER,
    ProveedorID INTEGER,
    PRIMARY KEY (ProductoID, ProveedorID),
    FOREIGN KEY (ProductoID) REFERENCES Productos(ProductoID),
    FOREIGN KEY (ProveedorID) REFERENCES Proveedores(ProveedorID)
);

-- Ejemplo de inserción de datos de prueba
INSERT INTO Productos (Nombre, Descripcion, Precio, StockInicial, UnidadMedida)
VALUES ('Producto 1', 'Descripción del Producto 1', 10.99, 100, 'Unidades');
INSERT INTO Productos (Nombre, Descripcion, Precio, StockInicial, UnidadMedida)
VALUES ('Producto 2', 'Descripción del Producto 2', 15.49, 75, 'Unidades');
INSERT INTO Inventario (ProductoID, FechaRegistro, CantidadEntrada, CantidadSalida)
VALUES (1, '2023-10-10', 50, 0);
INSERT INTO Inventario (ProductoID, FechaRegistro, CantidadEntrada, CantidadSalida)
VALUES (2, '2023-10-11', 0, 25);
-- Pruebas para la tabla 'Productos'
INSERT INTO Productos (Nombre, Descripcion, Precio, StockInicial, UnidadMedida)
VALUES ('Camisa', 'Camisa de algodón', 25.99, 50, 'Unidades');
INSERT INTO Productos (Nombre, Descripcion, Precio, StockInicial, UnidadMedida)
VALUES ('Zapatos deportivos', 'Zapatos para correr', 49.99, 30, 'Pares');
INSERT INTO Productos (Nombre, Descripcion, Precio, StockInicial, UnidadMedida)
VALUES ('Laptop', 'Laptop de 15 pulgadas', 899.99, 10, 'Unidades');
INSERT INTO Productos (Nombre, Descripcion, Precio, StockInicial, UnidadMedida)
VALUES ('Teclado mecánico', 'Teclado para gaming', 79.99, 20, 'Unidades');
INSERT INTO Productos (Nombre, Descripcion, Precio, StockInicial, UnidadMedida)
VALUES ('Monitor 4K', 'Monitor de alta resolución', 349.99, 15, 'Unidades');
INSERT INTO Productos (Nombre, Descripcion, Precio, StockInicial, UnidadMedida)
VALUES ('Cámara DSLR', 'Cámara réflex digital', 699.99, 5, 'Unidades');
INSERT INTO Productos (Nombre, Descripcion, Precio, StockInicial, UnidadMedida)
VALUES ('Impresora láser', 'Impresora en blanco y negro', 149.99, 8, 'Unidades');
INSERT INTO Productos (Nombre, Descripcion, Precio, StockInicial, UnidadMedida)
VALUES ('Mochila', 'Mochila resistente al agua', 39.99, 40, 'Unidades');
INSERT INTO Productos (Nombre, Descripcion, Precio, StockInicial, UnidadMedida)
VALUES ('Tablet', 'Tablet Android', 199.99, 12, 'Unidades');
INSERT INTO Productos (Nombre, Descripcion, Precio, StockInicial, UnidadMedida)
VALUES ('Altavoces Bluetooth', 'Altavoces portátiles', 59.99, 18, 'Pares');
-- Pruebas para la tabla 'Inventario'
INSERT INTO Inventario (ProductoID, FechaRegistro, CantidadEntrada, CantidadSalida)
VALUES (1, '2023-10-10', 10, 5);
INSERT INTO Inventario (ProductoID, FechaRegistro, CantidadEntrada, CantidadSalida)
VALUES (2, '2023-10-11', 8, 4);
INSERT INTO Inventario (ProductoID, FechaRegistro, CantidadEntrada, CantidadSalida)
VALUES (3, '2023-10-12', 5, 2);
INSERT INTO Inventario (ProductoID, FechaRegistro, CantidadEntrada, CantidadSalida)
VALUES (4, '2023-10-13', 7, 3);
INSERT INTO Inventario (ProductoID, FechaRegistro, CantidadEntrada, CantidadSalida)
VALUES (5, '2023-10-14', 9, 1);
INSERT INTO Inventario (ProductoID, FechaRegistro, CantidadEntrada, CantidadSalida)
VALUES (6, '2023-10-15', 4, 2);
INSERT INTO Inventario (ProductoID, FechaRegistro, CantidadEntrada, CantidadSalida)
VALUES (7, '2023-10-16', 6, 3);
INSERT INTO Inventario (ProductoID, FechaRegistro, CantidadEntrada, CantidadSalida)
VALUES (8, '2023-10-17', 3, 1);
INSERT INTO Inventario (ProductoID, FechaRegistro, CantidadEntrada, CantidadSalida)
VALUES (9, '2023-10-18', 5, 2);
INSERT INTO Inventario (ProductoID, FechaRegistro, CantidadEntrada, CantidadSalida)
VALUES (10, '2023-10-19', 8, 4);
-- Pruebas para la tabla 'Proveedores' (opcional)
INSERT INTO Proveedores (NombreProveedor, Direccion, Telefono)
VALUES ('Proveedor A', 'Calle Principal 123', '+1234567890');
INSERT INTO Proveedores (NombreProveedor, Direccion, Telefono)
VALUES ('Proveedor B', 'Avenida Secundaria 456', '+9876543210');
-- Pruebas para la tabla 'ProductosProveedores' (opcional)
INSERT INTO ProductosProveedores (ProductoID, ProveedorID)
VALUES (1, 1);
INSERT INTO ProductosProveedores (ProductoID, ProveedorID)
VALUES (2, 1);
INSERT INTO ProductosProveedores (ProductoID, ProveedorID)
VALUES (3, 2);
INSERT INTO ProductosProveedores (ProductoID, ProveedorID)
VALUES (4, 2);
INSERT INTO ProductosProveedores (ProductoID, ProveedorID)
VALUES (5, 1);
INSERT INTO ProductosProveedores (ProductoID, ProveedorID)
VALUES (6, 2);
INSERT INTO ProductosProveedores (ProductoID, ProveedorID)
VALUES (7, 2);
INSERT INTO ProductosProveedores (ProductoID, ProveedorID)
VALUES (8, 1);
INSERT INTO ProductosProveedores (ProductoID, ProveedorID)
VALUES (9, 2);
INSERT INTO ProductosProveedores (ProductoID, ProveedorID)
VALUES (10, 1);
```

## Ejemplo de sub-consultas (Selects anidados)

Ejemplo de una consulta SELECT anidada utilizando los datos de prueba proporcionados anteriormente. La consulta buscará el nombre de los productos y la cantidad total de entrada y salida de inventario para cada uno de ellos. 

**Comando de Entrada SQL:**

```sql
SELECT p.Nombre, 
       (SELECT SUM(CantidadEntrada - CantidadSalida) 
        FROM Inventario i 
        WHERE i.ProductoID = p.ProductoID) AS StockTotal
FROM Productos p;
```

**Resultado Esperado:**

| Nombre            | StockTotal |
|-------------------|------------|
| Camisa            | 5          |
| Zapatos deportivos| 4          |
| Laptop            | 3          |
| Teclado mecánico  | 3          |
| Monitor 4K        | 8          |
| Cámara DSLR       | 2          |
| Impresora láser   | 4          |
| Mochila           | 38         |
| Tablet            | 10         |
| Altavoces Bluetooth | 12      |

En esta consulta SELECT anidada, se obtiene el nombre de los productos de la tabla `Productos` y calculando el stock total para cada uno de ellos sumando las cantidades de entrada y restando las cantidades de salida de la tabla `Inventario`.

## Ejemplo de INNER JOIN

Ejemplo de una consulta SQL utilizando INNER JOIN para combinar las tablas `Productos` e `Inventario`. La consulta buscará el nombre de los productos y la cantidad total de entrada de inventario para cada uno de ellos.

**Comando de Entrada SQL:**

```sql
SELECT p.Nombre, SUM(i.CantidadEntrada) AS TotalEntrada
FROM Productos p
INNER JOIN Inventario i ON p.ProductoID = i.ProductoID
GROUP BY p.Nombre;
```

**Resultado Esperado**

| Nombre            | TotalEntrada |
|-------------------|-------------|
| Camisa            | 10          |
| Zapatos deportivos| 8           |
| Laptop            | 5           |
| Teclado mecánico  | 7           |
| Monitor 4K        | 9           |
| Cámara DSLR       | 4           |
| Impresora láser   | 6           |
| Mochila           | 12          |
| Tablet            | 16          |
| Altavoces Bluetooth | 20       |

En esta consulta, estamos utilizando INNER JOIN para combinar la información de las tablas `Productos` e `Inventario` en función del campo `ProductoID`. Luego, agrupamos los resultados por el nombre del producto y calculamos la suma de la cantidad de entrada de inventario para cada producto. Esto nos da el total de entrada de inventario para cada producto en el almacén.

## OUTER JOIN (LEFT JOIN)

Ejemplo de una consulta SQL utilizando OUTER JOIN para combinar las tablas `Productos` e `Inventario`. La consulta buscará el nombre de los productos y la cantidad total de entrada de inventario para cada uno de ellos, incluyendo los productos que no tienen registros en la tabla `Inventario`.

**Comando de Entrada SQL (OUTER JOIN):**

```sql
SELECT p.Nombre, COALESCE(SUM(i.CantidadEntrada), 0) AS TotalEntrada
FROM Productos p
LEFT JOIN Inventario i ON p.ProductoID = i.ProductoID
GROUP BY p.Nombre;
```

**Resultado Esperado**

| Nombre            | TotalEntrada |
|-------------------|-------------|
| Camisa            | 10          |
| Zapatos deportivos| 8           |
| Laptop            | 5           |
| Teclado mecánico  | 7           |
| Monitor 4K        | 9           |
| Cámara DSLR       | 4           |
| Impresora láser   | 6           |
| Mochila           | 12          |
| Tablet            | 16          |
| Altavoces Bluetooth | 20       |
| Producto 1        | 0           |
| Producto 2        | 0           |
| Producto 3        | 0           |
| Producto 4        | 0           |
| Producto 5        | 0           |
| Producto 6        | 0           |
| Producto 7        | 0           |
| Producto 8        | 0           |
| Producto 9        | 0           |
| Producto 10       | 0           |

En esta consulta, estamos utilizando LEFT JOIN (OUTER JOIN) para combinar la información de las tablas `Productos` e `Inventario`. Esto nos permite obtener la cantidad total de entrada de inventario para cada producto, incluyendo los productos que no tienen registros en la tabla `Inventario`. Utilizamos la función `COALESCE` para asegurarnos de que los productos sin registros en `Inventario` tengan un valor de total de entrada de 0 en la salida.

## RIGHT JOIN

Ejemplo de una consulta SQL utilizando RIGHT JOIN para combinar las tablas `Productos` e `Inventario`. La consulta buscará el nombre de los productos y la cantidad total de entrada de inventario para cada uno de ellos, incluyendo los registros de la tabla `Inventario` y los productos que no tienen registros en la tabla `Productos`. .

**Comando de Entrada SQL (RIGHT JOIN):**

```sql
SELECT p.Nombre, COALESCE(SUM(i.CantidadEntrada), 0) AS TotalEntrada
FROM Productos p
RIGHT JOIN Inventario i ON p.ProductoID = i.ProductoID
GROUP BY p.Nombre;
```

**Resultado Esperado**

| Nombre            | TotalEntrada |
|-------------------|-------------|
| Camisa            | 10          |
| Zapatos deportivos| 8           |
| Laptop            | 5           |
| Teclado mecánico  | 7           |
| Monitor 4K        | 9           |
| Cámara DSLR       | 4           |
| Impresora láser   | 6           |
| Mochila           | 12          |
| Tablet            | 16          |

En esta consulta, estamos utilizando RIGHT JOIN para combinar la información de las tablas `Productos` e `Inventario`. Esto nos permite obtener la cantidad total de entrada de inventario para cada producto, incluyendo los registros de la tabla `Inventario` y excluyendo los productos que no tienen registros en `Productos`. Utilizamos la función `COALESCE` para asegurarnos de que los productos sin registros en `Productos` tengan un valor de total de entrada de 0 en la salida.