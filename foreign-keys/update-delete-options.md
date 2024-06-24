# Opciones de actualización y eliminación de llaves foráneas en MySQL

## Definición

Las llaves foráneas (`FOREIGN KEY`) en MySQL pueden tener opciones de actualización y eliminación que definen el comportamiento de la base de datos cuando se actualiza o elimina un registro en la tabla padre.

## Opciones de actualización y eliminación

### Opción `ON DELETE`

- `CASCADE`: Borra automáticamente los registros de la tabla hija cuando se elimina un registro de la tabla padre.
- `SET NULL`: Establece los valores de la columna de la llave foránea en `NULL` cuando se elimina un registro de la tabla padre.
- `RESTRICT`: No permite eliminar un registro de la tabla padre si hay registros asociados en la tabla hija.
- `NO ACTION`: Es equivalente a `RESTRICT`.

### Opción `ON UPDATE`

- `CASCADE`: Actualiza automáticamente los registros de la tabla hija cuando se actualiza un registro de la tabla padre.
- `SET NULL`: Establece los valores de la columna de la llave foránea en `NULL` cuando se actualiza un registro de la tabla padre.
- `RESTRICT`: No permite actualizar un registro de la tabla padre si hay registros asociados en la tabla hija.
- `NO ACTION`: Es equivalente a `RESTRICT`.

## Ejemplo

```sql
CREATE TABLE clientes (
  id INT PRIMARY KEY AUTO_INCREMENT,
  nombre VARCHAR(50) NOT NULL,
  email VARCHAR(50) NOT NULL,
  telefono VARCHAR(15) NOT NULL,
  direccion VARCHAR(255) NOT NULL
);

CREATE TABLE servicios (
  id INT PRIMARY KEY AUTO_INCREMENT,
  nombre VARCHAR(50) NOT NULL,
  descripcion VARCHAR(255) NOT NULL,
  precio DECIMAL(10, 2) NOT NULL,
  fecha DATE NOT NULL
);

CREATE TABLE plomeros (
  id INT PRIMARY KEY AUTO_INCREMENT,
  nombre VARCHAR(50) NOT NULL,
  email VARCHAR(50) NOT NULL,
  telefono VARCHAR(15) NOT NULL,
  direccion VARCHAR(255) NOT NULL
);

CREATE TABLE facturas (
  id INT PRIMARY KEY AUTO_INCREMENT,
  cliente_id INT NOT NULL,
  servicio_id INT NOT NULL,
  plomero_id INT NOT NULL,
  fecha DATE NOT NULL,
  total DECIMAL(10, 2) NOT NULL,
  direccion VARCHAR(255) NOT NULL,
  FOREIGN KEY (cliente_id) REFERENCES clientes(id) ON DELETE CASCADE ON UPDATE CASCADE,
  FOREIGN KEY (servicio_id) REFERENCES servicios(id) ON DELETE CASCADE ON UPDATE CASCADE,
  FOREIGN KEY (plomero_id) REFERENCES plomeros(id) ON DELETE CASCADE ON UPDATE CASCADE
);

CREATE TABLE descuentos (
  id INT PRIMARY KEY AUTO_INCREMENT,
  factura_id INT NOT NULL,
  monto DECIMAL(10, 2) NOT NULL,
  FOREIGN KEY (factura_id) REFERENCES facturas(id) ON DELETE CASCADE ON UPDATE CASCADE
);

CREATE TABLE pagos (
  id INT PRIMARY KEY AUTO_INCREMENT,
  factura_id INT NOT NULL,
  monto DECIMAL(10, 2) NOT NULL,
  fecha DATE NOT NULL,
  FOREIGN KEY (factura_id) REFERENCES facturas(id) ON DELETE CASCADE ON UPDATE CASCADE
);