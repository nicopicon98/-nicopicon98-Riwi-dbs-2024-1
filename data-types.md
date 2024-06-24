# Tipos de Datos en MySQL Workbench

## Tipos de Datos Numéricos

### Enteros

- `TINYINT`: Entero de 1 byte. Rango: -128 a 127 o 0 a 255 (si es UNSIGNED).
- `SMALLINT`: Entero de 2 bytes. Rango: -32,768 a 32,767 o 0 a 65,535 (si es UNSIGNED).
- `MEDIUMINT`: Entero de 3 bytes. Rango: -8,388,608 a 8,388,607 o 0 a 16,777,215 (si es UNSIGNED).
- `INT` o `INTEGER`: Entero de 4 bytes. Rango: -2,147,483,648 a 2,147,483,647 o 0 a 4,294,967,295 (si es UNSIGNED).
- `BIGINT`: Entero de 8 bytes. Rango: -9,223,372,036,854,775,808 a 9,223,372,036,854,775,807 o 0 a 18,446,744,073,709,551,615 (si es UNSIGNED).

### Decimales

- `FLOAT(M,D)`: Número de coma flotante de precisión simple.
- `DOUBLE(M,D)` o `DOUBLE PRECISION` o `REAL`: Número de coma flotante de doble precisión.
- `DECIMAL(M,D)` o `NUMERIC(M,D)`: Número decimal de precisión fija. 

### Tipos de Datos de Fecha y Hora

- `DATE`: Fecha (AAAA-MM-DD).
- `TIME`: Hora (HH:MM:SS).
- `DATETIME`: Combinación de fecha y hora (AAAA-MM-DD HH:MM:SS).
- `TIMESTAMP`: Combinación de fecha y hora con sello de tiempo (AAAA-MM-DD HH:MM:SS).
- `YEAR(M)`: Año en formato de 2 o 4 dígitos (por defecto 4).

### Tipos de Datos de Cadenas

- `CHAR(M)`: Cadena de longitud fija.
- `VARCHAR(M)`: Cadena de longitud variable.
- `BINARY(M)`: Cadena binaria de longitud fija.
- `VARBINARY(M)`: Cadena binaria de longitud variable.
- `TINYBLOB`, `BLOB`, `MEDIUMBLOB`, `LONGBLOB`: Almacenan datos binarios.
- `TINYTEXT`, `TEXT`, `MEDIUMTEXT`, `LONGTEXT`: Almacenan grandes cadenas de texto.
- `ENUM`: Enumeración de valores posibles.
- `SET`: Conjunto de valores posibles.

## Creación de Tablas con Tipos de Datos

### Ejemplo

```sql
CREATE TABLE examples (
    id INT PRIMARY KEY,
    nombre VARCHAR(100),
    edad INT,
    fecha_nacimiento DATE,
    salario DECIMAL(10, 2),
    creado_en TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

## Claves Primarias y Foráneas

### Claves Primarias

- `PRIMARY KEY`: Identificador único de cada fila en una tabla.
- `AUTO_INCREMENT`: Incrementa automáticamente el valor de la columna.

Entonces, la definición de una clave primaria se puede hacer de la siguiente manera:

```sql
CREATE TABLE examples (
    id INT PRIMARY KEY AUTO_INCREMENT,
    nombre VARCHAR(100),
    edad INT,
    fecha_nacimiento DATE,
    salario DECIMAL(10, 2),
    creado_en TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### Claves Foráneas

- `FOREIGN`: Restricción de integridad referencial.
- `REFERENCES`: Tabla y columna a la que se hace referencia.

Entonces, la definición de una clave foránea se puede hacer de la siguiente manera:

```sql

CREATE TABLE departments (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100)
);

CREATE TABLE employees (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100),
    age INT,
    dob DATE, -- date of birth
    salary DECIMAL(10, 2),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    departments_id INT,
    FOREIGN KEY (departments_id) REFERENCES departments(id)
);

```

En este caso, `id_departamento` es una clave foránea que hace referencia a la columna `id` de la tabla `departamentos`.

Tips a tener en cuenta sobre las claves foráneas:

- La columna referenciada debe tener una clave primaria o una clave única.
- La columna referenciada y la columna que contiene la clave foránea deben tener el mismo tipo de datos. Y aqui seré insistente, **deben tener el mismo tipo de datos**.
- La columna referenciada y la columna que contiene la clave foránea deben tener el mismo tamaño.