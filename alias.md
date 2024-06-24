# Alias en SQL

En SQL, los alias son nombres alternativos que se pueden asignar a columnas o tablas en una consulta. Los alias se utilizan para hacer que los resultados de la consulta sean más legibles y fáciles de entender.

### Alias de Columnas

En una consulta SQL, se pueden asignar alias a las columnas utilizando la palabra clave `AS`. Por ejemplo:

```sql
SELECT nombre AS nombre_completo, edad AS edad_actual
FROM Estudiantes;
```

En este caso, la columna `nombre` se renombra como `nombre_completo` y la columna `edad` se renombra como `edad_actual`.

### Alias de Tablas

En una consulta SQL, se pueden asignar alias a las tablas utilizando la palabra clave `AS`. Por ejemplo:

```sql
SELECT e.nombre, e.edad
FROM Estudiantes AS e;
```

En este caso, la tabla `Estudiantes` se renombra como `e`, y se pueden hacer referencia a las columnas de la tabla utilizando este alias.

Los alias son útiles para abreviar nombres largos, mejorar la legibilidad de las consultas y evitar conflictos de nombres en consultas complejas que involucran múltiples tablas.