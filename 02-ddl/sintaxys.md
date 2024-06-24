# Sintaxis de DDL en MySQL

## Comandos Principales de DDL

### CREATE

#### Crear Base de Datos

```sql
CREATE DATABASE nombre_base_de_datos;
```

#### Crear Tabla

```sql
CREATE TABLE nombre_tabla (
    nombre_columna tipo_de_dato [opciones],
    ...
    [PRIMARY KEY (columna1, columna2, ...)],
    [FOREIGN KEY (columna) REFERENCES tabla_remota(columna_remota)]
);
```

#### Alterar Tabla

```sql
-- Agregar columna
ALTER TABLE nombre_tabla
    ADD COLUMN nombre_columna tipo_de_dato [opciones];

-- Eliminar columna
ALTER TABLE nombre_tabla
    DROP COLUMN nombre_columna;

-- Modificar columna
ALTER TABLE nombre_tabla
    MODIFY COLUMN nombre_columna tipo_de_dato [opciones];
```

Me gustaria hacer una aclaración a este punto sobre la sintaxis de `ALTER TABLE` en MySQL. En MySQL, la sintaxis de `ALTER TABLE` es un poco diferente a la de otros motores de bases de datos. En MySQL, la palabra clave `COLUMN` es opcional. Por lo tanto, las siguientes sentencias son equivalentes:

```sql
ALTER TABLE nombre_tabla
    ADD COLUMN nombre_columna tipo_de_dato [opciones];

ALTER TABLE nombre_tabla
    ADD nombre_columna tipo_de_dato [opciones];
```

#### Eliminar Tabla

```sql
DROP TABLE nombre_tabla;
```

Tener muchos cuidado con este comando, ya que eliminar una tabla también elimina todos los datos almacenados en ella.