# Sistema de Gestión de Bases de Datos Distribuidas en Java

**Descripción:**

En esta tarea, los estudiantes deberán implementar un sistema de gestión de bases de datos distribuidas en el lenguaje de programación Java. El sistema debe ser capaz de administrar bases de datos provenientes de diferentes fuentes, como diferentes gestores de bases de datos (por ejemplo, MySQL, MariaDB, PostgreSQL) y diferentes archivos (por ejemplo, archivos Excel y archivos CSV). El objetivo principal es permitir que el sistema gestione estas bases de datos distribuidas como si fueran una sola base de datos unificada. Los estudiantes deben ser capaces de realizar consultas complejas a través de tablas distribuidas.

**Requisitos del Sistema:**

1. **Conexión a Diferentes Fuentes:** El sistema debe ser capaz de conectarse a diferentes fuentes de datos, incluyendo diferentes gestores de bases de datos (por ejemplo, MySQL, MariaDB, PostgreSQL) y archivos en formato Excel y CSV.

2. **Unificación de Bases de Datos:** El sistema debe ser capaz de unificar estas bases de datos distribuidas y permitir consultas que involucren tablas de múltiples fuentes.

3. **Consultas Complejas:** Los estudiantes deben implementar la capacidad de realizar consultas complejas, incluyendo SELECT con JOIN, WHERE, GROUP BY, ORDER BY, etc., que involucren tablas de bases de datos distribuidas.

**Entregables:**

Los estudiantes deben entregar los siguientes elementos:

1. **Código Fuente:** El código fuente completo del sistema de gestión de bases de datos distribuidas en Java. Debe estar bien organizado y documentado para facilitar la comprensión.

2. **Pruebas Unitarias:** Deben proporcionar pruebas unitarias exhaustivas que demuestren que el sistema funciona correctamente, incluyendo casos de consulta complejos.

3. **Bases de Datos de Prueba:** Deben crear bases de datos de prueba o utilizar bases de datos de ejemplo que permitan probar el sistema de manera efectiva.

4. **Archivo JAR Autoejecutable:** Deben crear un archivo JAR autoejecutable que permita a los evaluadores probar el sistema de manera sencilla.

**Evaluación:**

Los proyectos serán evaluados en función de los siguientes criterios:

1. **Funcionalidad:** El sistema debe ser capaz de conectarse y gestionar bases de datos distribuidas de diferentes fuentes y permitir consultas complejas de manera efectiva.

2. **Calidad del Código:** El código fuente debe estar bien estructurado, ser legible y seguir las mejores prácticas de programación en Java.

3. **Pruebas Unitarias:** Las pruebas unitarias deben cubrir una variedad de casos y demostrar que el sistema funciona de manera robusta y sin errores.

4. **Bases de Datos de Prueba:** Deben proporcionar bases de datos de prueba o datos de ejemplo que permitan probar el sistema de manera efectiva.

---

## Ejemplos de prueba.


1. **MySQL: Base de Datos Distribuida**

```sql
-- Crear la base de datos en MySQL
CREATE DATABASE tienda_distribuida;

-- Utilizar la base de datos
USE tienda_distribuida;

-- Crear tabla de Cajas Registradoras
CREATE TABLE CajasRegistradoras (
    CajaID INT PRIMARY KEY,
    Nombre VARCHAR(50),
    Ubicacion VARCHAR(100)
);

-- Crear tabla de Inventario de Almacén
CREATE TABLE InventarioAlmacen (
    ProductoID INT PRIMARY KEY,
    NombreProducto VARCHAR(100),
    Stock INT,
    Precio DECIMAL(10, 2)
);

-- Crear tabla de Proveedores
CREATE TABLE Proveedores (
    ProveedorID INT PRIMARY KEY,
    NombreProveedor VARCHAR(100),
    Direccion VARCHAR(200),
    Telefono VARCHAR(20)
);

-- Crear tabla de ProductosProveedores (relación muchos a muchos)
CREATE TABLE ProductosProveedores (
    ProductoID INT,
    ProveedorID INT,
    PRIMARY KEY (ProductoID, ProveedorID)
);

-- Inserción de datos para Cajas Registradoras en MySQL
INSERT INTO CajasRegistradoras (Nombre, Ubicacion) VALUES
    ('Caja 1', 'Ubicación A'),
    ('Caja 2', 'Ubicación B'),
    ('Caja 3', 'Ubicación C'),
    ('Caja 4', 'Ubicación D'),
    ('Caja 5', 'Ubicación E'),
    ('Caja 6', 'Ubicación F'),
    ('Caja 7', 'Ubicación G'),
    ('Caja 8', 'Ubicación H'),
    ('Caja 9', 'Ubicación I'),
    ('Caja 10', 'Ubicación J');

-- Inserción de datos para Inventario de Almacén en MySQL
INSERT INTO InventarioAlmacen (NombreProducto, Stock, Precio) VALUES
    ('Producto 1', 100, 19.99),
    ('Producto 2', 75, 29.99),
    ('Producto 3', 50, 49.99),
    ('Producto 4', 30, 9.99),
    ('Producto 5', 20, 39.99),
    ('Producto 6', 10, 89.99),
    ('Producto 7', 45, 15.99),
    ('Producto 8', 60, 7.99),
    ('Producto 9', 80, 24.99),
    ('Producto 10', 55, 14.99);

-- Inserción de datos para Proveedores en MySQL
INSERT INTO Proveedores (NombreProveedor, Direccion, Telefono) VALUES
    ('Proveedor A', 'Calle Principal 123', '+1234567890'),
    ('Proveedor B', 'Avenida Secundaria 456', '+9876543210'),
    ('Proveedor C', 'Calle Terciaria 789', '+1122334455'),
    ('Proveedor D', 'Avenida Cuaternaria 101', '+9988776655'),
    ('Proveedor E', 'Calle Quintaria 202', '+6677889900'),
    ('Proveedor F', 'Avenida Sextaria 303', '+4455667788'),
    ('Proveedor G', 'Calle Séptaria 404', '+1122334455'),
    ('Proveedor H', 'Avenida Octaria 505', '+5544332211'),
    ('Proveedor I', 'Calle Novaria 606', '+1122334455'),
    ('Proveedor J', 'Avenida Decaria 707', '+9988776655');


-- Fin del archivo
```

2. **PostgreSQL: Base de Datos Distribuida**

```sql
-- Crear la base de datos en PostgreSQL
CREATE DATABASE tienda_distribuida;

-- Conectar a la base de datos
\c tienda_distribuida;

-- Crear tabla de Cajas Registradoras
CREATE TABLE CajasRegistradoras (
    CajaID SERIAL PRIMARY KEY,
    Nombre VARCHAR(50),
    Ubicacion VARCHAR(100)
);

-- Crear tabla de Inventario de Almacén
CREATE TABLE InventarioAlmacen (
    ProductoID SERIAL PRIMARY KEY,
    NombreProducto VARCHAR(100),
    Stock INT,
    Precio DECIMAL(10, 2)
);

-- Crear tabla de Proveedores
CREATE TABLE Proveedores (
    ProveedorID SERIAL PRIMARY KEY,
    NombreProveedor VARCHAR(100),
    Direccion VARCHAR(200),
    Telefono VARCHAR(20)
);

-- Crear tabla de ProductosProveedores (relación muchos a muchos)
CREATE TABLE ProductosProveedores (
    ProductoID INT,
    ProveedorID INT,
    PRIMARY KEY (ProductoID, ProveedorID)
);

-- Inserción de datos para Cajas Registradoras en PostgreSQL
INSERT INTO CajasRegistradoras (Nombre, Ubicacion) VALUES
    ('Caja 1', 'Ubicación A'),
    ('Caja 2', 'Ubicación B'),
    ('Caja 3', 'Ubicación C'),
    ('Caja 4', 'Ubicación D'),
    ('Caja 5', 'Ubicación E'),
    ('Caja 6', 'Ubicación F'),
    ('Caja 7', 'Ubicación G'),
    ('Caja 8', 'Ubicación H'),
    ('Caja 9', 'Ubicación I'),
    ('Caja 10', 'Ubicación J');

-- Inserción de datos para Inventario de Almacén en PostgreSQL
INSERT INTO InventarioAlmacen (NombreProducto, Stock, Precio) VALUES
    ('Producto 1', 100, 19.99),
    ('Producto 2', 75, 29.99),
    ('Producto 3', 50, 49.99),
    ('Producto 4', 30, 9.99),
    ('Producto 5', 20, 39.99),
    ('Producto 6', 10, 89.99),
    ('Producto 7', 45, 15.99),
    ('Producto 8', 60, 7.99),
    ('Producto 9', 80, 24.99),
    ('Producto 10', 55, 14.99);

-- Inserción de datos para Proveedores en PostgreSQL
INSERT INTO Proveedores (NombreProveedor, Direccion, Telefono) VALUES
    ('Proveedor A', 'Calle Principal 123', '+1234567890'),
    ('Proveedor B', 'Avenida Secundaria 456', '+9876543210'),
    ('Proveedor C', 'Calle Terciaria 789', '+1122334455'),
    ('Proveedor D', 'Avenida Cuaternaria 101', '+9988776655'),
    ('Proveedor E', 'Calle Quintaria 202', '+6677889900'),
    ('Proveedor F', 'Avenida Sextaria 303', '+4455667788'),
    ('Proveedor G', 'Calle Séptaria 404', '+1122334455'),
    ('Proveedor H', 'Avenida Octaria 505', '+5544332211'),
    ('Proveedor I', 'Calle Novaria 606', '+1122334455'),
    ('Proveedor J', 'Avenida Decaria 707', '+9988776655');


-- Fin del archivo
```

3. **SQLite: Base de Datos Distribuida**

```sql
-- Crear tabla de Cajas Registradoras en SQLite
CREATE TABLE CajasRegistradoras (
    CajaID INTEGER PRIMARY KEY,
    Nombre TEXT,
    Ubicacion TEXT
);

-- Crear tabla de Inventario de Almacén en SQLite
CREATE TABLE InventarioAlmacen (
    ProductoID INTEGER PRIMARY KEY,
    NombreProducto TEXT,
    Stock INTEGER,
    Precio REAL
);

-- Crear tabla de Proveedores en SQLite
CREATE TABLE Proveedores (
    ProveedorID INTEGER PRIMARY KEY,
    NombreProveedor TEXT,
    Direccion TEXT,
    Telefono TEXT
);

-- Crear tabla de ProductosProveedores (relación muchos a muchos) en SQLite
CREATE TABLE ProductosProveedores (
    ProductoID INTEGER,
    ProveedorID INTEGER,
    PRIMARY KEY (ProductoID, ProveedorID)
);

-- Inserción de datos para Cajas Registradoras en SQLite
INSERT INTO CajasRegistradoras (Nombre, Ubicacion) VALUES
    ('Caja 1', 'Ubicación A'),
    ('Caja 2', 'Ubicación B'),
    ('Caja 3', 'Ubicación C'),
    ('Caja 4', 'Ubicación D'),
    ('Caja 5', 'Ubicación E'),
    ('Caja 6', 'Ubicación F'),
    ('Caja 7', 'Ubicación G'),
    ('Caja 8', 'Ubicación H'),
    ('Caja 9', 'Ubicación I'),
    ('Caja 10', 'Ubicación J');



-- Fin del archivo
```

Consulta SQL compleja que hace uso de la base de datos distribuida que hemos creado anteriormente. La consulta buscará obtener el nombre del proveedor, el nombre del producto y la cantidad en stock de cada producto proporcionado por cada proveedor. 

**Comando de Entrada SQL:**

```sql
-- Consulta compleja que obtiene el nombre del proveedor, el nombre del producto y la cantidad en stock de cada producto proporcionado por cada proveedor
SELECT pr.NombreProveedor, p.NombreProducto, ia.Stock
FROM Proveedores pr
INNER JOIN ProductosProveedores pp ON pr.ProveedorID = pp.ProveedorID
INNER JOIN InventarioAlmacen ia ON pp.ProductoID = ia.ProductoID
INNER JOIN CajasRegistradoras cr ON cr.CajaID = ia.ProductoID
ORDER BY pr.NombreProveedor, p.NombreProducto;
```

**Resultado Esperado (Formato Markdown):**

| NombreProveedor | NombreProducto    | Stock |
|-----------------|-------------------|-------|
| Proveedor A     | Producto 1        | 100   |
| Proveedor A     | Producto 2        | 75    |
| Proveedor A     | Producto 3        | 50    |
| Proveedor A     | Producto 4        | 30    |
| Proveedor A     | Producto 5        | 20    |
| Proveedor B     | Producto 1        | 100   |
| Proveedor B     | Producto 2        | 75    |
| Proveedor B     | Producto 3        | 50    |
| Proveedor B     | Producto 4        | 30    |
| Proveedor B     | Producto 5        | 20    |
| ...             | ...               | ...   |

Esta consulta combina información de las tablas `Proveedores`, `ProductosProveedores`, `InventarioAlmacen` y `CajasRegistradoras` utilizando múltiples JOIN para obtener el nombre del proveedor, el nombre del producto y la cantidad en stock de cada producto proporcionado por cada proveedor. La consulta está ordenada por el nombre del proveedor y el nombre del producto para facilitar la visualización.

### Ejemplo 2

Ejemplo de una consulta SQL con subconsultas (SELECTs anidados) utilizando la base de datos distribuida que hemos creado anteriormente. La consulta buscará obtener el nombre de los productos que tienen el menor precio en stock en cada caja registradora. Luego, se muestra el resultado esperado en formato Markdown.

**Comando de Entrada SQL:**

```sql
-- Consulta con subconsultas para obtener los productos con el menor precio en stock en cada caja registradora
SELECT cr.Nombre AS CajaRegistradora, p.NombreProducto AS Producto, ia.Precio AS Precio
FROM CajasRegistradoras cr
INNER JOIN InventarioAlmacen ia ON cr.CajaID = ia.ProductoID
INNER JOIN ProductosProveedores pp ON ia.ProductoID = pp.ProductoID
INNER JOIN Proveedores pr ON pp.ProveedorID = pr.ProveedorID
INNER JOIN (
    SELECT cr.CajaID, MIN(ia.Precio) AS PrecioMinimo
    FROM CajasRegistradoras cr
    INNER JOIN InventarioAlmacen ia ON cr.CajaID = ia.ProductoID
    GROUP BY cr.CajaID
) AS SubConsulta
ON cr.CajaID = SubConsulta.CajaID AND ia.Precio = SubConsulta.PrecioMinimo
ORDER BY cr.Nombre, p.NombreProducto;
```

**Resultado Esperado (Formato Markdown):**

| CajaRegistradora | Producto        | Precio |
|-------------------|------------------|--------|
| Caja 1            | Producto 1       | 19.99  |
| Caja 2            | Producto 4       | 9.99   |
| Caja 3            | Producto 8       | 7.99   |
| Caja 4            | Producto 4       | 9.99   |
| Caja 5            | Producto 4       | 9.99   |
| Caja 6            | Producto 6       | 89.99  |
| Caja 7            | Producto 7       | 15.99  |
| Caja 8            | Producto 8       | 7.99   |
| Caja 9            | Producto 9       | 24.99  |
| Caja 10           | Producto 10      | 14.99  |

En esta consulta, estamos utilizando subconsultas para obtener los productos con el menor precio en stock en cada caja registradora. Primero, creamos una subconsulta que calcula el precio mínimo en stock para cada caja registradora. Luego, combinamos esta subconsulta con las tablas `CajasRegistradoras`, `InventarioAlmacen`, `ProductosProveedores` y `Proveedores` para obtener los nombres de los productos con los precios mínimos en cada caja registradora. La consulta está ordenada por el nombre de la caja registradora y el nombre del producto para facilitar la visualización.