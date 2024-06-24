# Llaves Foráneas en MySQL

## Definición

Una llave foránea (`FOREIGN KEY`) es una restricción utilizada para asegurar la integridad referencial entre dos tablas. Esta restricción garantiza que el valor en una columna o conjunto de columnas de una tabla coincida con el valor en una columna o conjunto de columnas de otra tabla.

## Sintaxis para Crear Llaves Foráneas

### Al Crear una Tabla

```sql
CREATE TABLE nombre_tabla (
    nombre_columna tipo_de_dato [opciones],
    ...
    [PRIMARY KEY (columna1, columna2, ...)],
    FOREIGN KEY (columna) REFERENCES tabla_remota(columna_remota)
);
```

### Ejemplo

```sql
CREATE TABLE Pagos (
    id INT PRIMARY KEY,
    monto DECIMAL(10, 2),
    factura_id INT,
    FOREIGN KEY (factura_id) REFERENCES Facturas(id)
);
```

### Al Modificar una Tabla

```sql
ALTER TABLE nombre_tabla
    ADD CONSTRAINT nombre_llave_foranea
    FOREIGN KEY (columna) REFERENCES tabla_remota(columna_remota);
```

### Ejemplo

```sql
ALTER TABLE Pagos
ADD CONSTRAINT fk_factura
FOREIGN KEY (factura_id) REFERENCES Facturas(id);
```

## Sintaxis para Eliminar Llaves Foráneas

```sql
ALTER TABLE nombre_tabla
DROP FOREIGN KEY nombre_llave_foranea;
```

### Ejemplo

```sql
ALTER TABLE Pagos
DROP FOREIGN KEY fk_factura;
```