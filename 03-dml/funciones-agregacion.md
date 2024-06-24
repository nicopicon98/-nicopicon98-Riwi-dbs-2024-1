# Funciones de Agregación en SQL

Las funciones de agregación en SQL permiten realizar cálculos sobre un conjunto de valores y devolver un único resultado. Algunas de las funciones de agregación más comunes son:

- `COUNT()`: Devuelve el número de filas en un conjunto de resultados.
- `SUM()`: Calcula la suma de los valores en un conjunto de resultados.
- `AVG()`: Calcula el promedio de los valores en un conjunto de resultados.
- `MIN()`: Devuelve el valor mínimo en un conjunto de resultados.
- `MAX()`: Devuelve el valor máximo en un conjunto de resultados.
- `GROUP_CONCAT()`: Concatena los valores de una columna en un solo string.
- `STDEV()`: Calcula la desviación estándar de los valores en un conjunto de resultados.
- `VAR()`: Calcula la varianza de los valores en un conjunto de resultados.

En este taller, vamos a explorar cómo utilizar estas funciones de agregación en consultas SQL.

## Ejercicio 1

### Enunciado

Dada la siguiente tabla `Ventas`:

```sql
CREATE TABLE Ventas (
    id INT PRIMARY KEY,
    producto VARCHAR(50),
    cantidad INT,
    precio DECIMAL(10, 2)
);
```

Escribir una consulta SQL que devuelva el total de ventas realizadas y el monto total vendido.

### Solución

```sql
SELECT COUNT(*) AS total_ventas, SUM(precio * cantidad) AS monto_total
FROM Ventas;
```

## Ejercicio 2

### Enunciado

Dada la siguiente tabla `Productos`:

```sql
CREATE TABLE Productos (
    id INT PRIMARY KEY,
    nombre VARCHAR(50),
    precio DECIMAL(10, 2)
);
```

Escribir una consulta SQL que devuelva el precio promedio de los productos.

### Solución

```sql
SELECT AVG(precio) AS precio_promedio
FROM Productos;
```

## Ejercicio 3

### Enunciado

Dada la siguiente tabla `Estudiantes`:

```sql
CREATE TABLE Estudiantes (
    id INT PRIMARY KEY,
    nombre VARCHAR(50),
    edad INT
);
```

Escribir una consulta SQL que devuelva la edad mínima y máxima de los estudiantes.

### Solución

```sql
SELECT MIN(edad) AS edad_minima, MAX(edad) AS edad_maxima
FROM Estudiantes;
```

## Ejercicio 4

### Enunciado

Dada la siguiente tabla `Pedidos`:

```sql
CREATE TABLE Pedidos (
    id INT PRIMARY KEY,
    usuario_id INT,
    total DECIMAL(10, 2)
);
```

Escribir una consulta SQL que devuelva el total de pedidos realizados y el monto total de ventas.

### Solución

```sql
SELECT COUNT(*) AS total_pedidos, SUM(total) AS monto_total_ventas
FROM Pedidos;
```

## Ejercicio 5

### Enunciado

Dada la siguiente tabla `Productos`:

```sql
CREATE TABLE Productos (
    id INT PRIMARY KEY,
    nombre VARCHAR(50),
    categoria VARCHAR(50),
    precio DECIMAL(10, 2)
);
```

Escribir una consulta SQL que devuelva el total de productos por categoría.

### Solución

```sql
SELECT categoria, COUNT(*) AS total_productos
FROM Productos
GROUP BY categoria;
```

Acotación: En este caso, la función de agregación `COUNT(*)` se utiliza para contar el número de productos en cada categoría, y la cláusula `GROUP BY` se utiliza para agrupar los resultados por categoría.