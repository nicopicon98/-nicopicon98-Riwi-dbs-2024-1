# Taller: Introducción al Lenguaje de Manipulación de Datos (DML) en Bases de Datos Relacionales

## Objetivos

1. **Memorizar** los conceptos básicos del Lenguaje de Manipulación de Datos (DML) en bases de datos relacionales.
2. **Comprender** y aplicar los conceptos de inserción, actualización y eliminación de datos mediante DML.
3. **Aplicar** consultas básicas y avanzadas de selección de datos.
4. **Analizar** y diseñar consultas para la manipulación eficiente de datos.
5. **Evaluar** la consistencia y eficiencia de las operaciones de manipulación de datos.
6. **Crear** consultas complejas para la gestión de datos en un sistema de información específico.

## Contenidos

1. **Recordar**: Conceptos básicos de bases de datos relacionales y DML.
2. **Comprender**: Operaciones básicas de DML: INSERT, UPDATE, DELETE.
3. **Aplicar**: Consultas SELECT básicas y avanzadas:
   - Selección de columnas específicas.
   - Filtros y condiciones (WHERE).
   - Ordenación de resultados (ORDER BY).
   - Funciones de agregación (SUM, COUNT, AVG, etc.).
   - Agrupación de datos (GROUP BY).
   - Consultas de unión (JOIN).
4. **Analizar**: Optimización de consultas y uso de índices.
5. **Crear**: Consultas complejas para casos de uso específicos.

## Recursos

- [alias.md](../alias.md)

## Instrucciones de entrega

- **Repositorio en GitHub:** Crear un repositorio en GitHub con el nombre `dml-workshop`.
- **Estructura de carpetas:** Crear una carpeta para cada ejercicio con el nombre `exercise-1`, `exercise-2`, `exercise-3`, `exercise-4`.
- **Scripts DML:** Incluir los scripts DML (archivos `.sql`) en cada carpeta de ejercicio.

## Introducción Teórica

### Lenguaje de Manipulación de Datos (DML)

**Definición y Propósito del DML**

El DML es un subconjunto del SQL que se utiliza para manipular los datos almacenados en las bases de datos. Las instrucciones DML se utilizan para insertar, actualizar, eliminar y consultar datos.

- **INSERT:** Inserta nuevos datos en una tabla.
- **UPDATE:** Actualiza datos existentes en una tabla.
- **DELETE:** Elimina datos de una tabla.
- **SELECT:** Recupera datos de una o más tablas.

### Inserción de Datos

```sql
INSERT INTO Usuarios (id, nombre, email) VALUES (1, 'Juan Pérez', 'juan.perez@example.com');
```

### Actualización de Datos

```sql
UPDATE Usuarios SET email = 'juan.perez@nuevoemail.com' WHERE id = 1;
```

### Eliminación de Datos

```sql
DELETE FROM Usuarios WHERE id = 1;
```

### Selección de Datos

```sql
SELECT nombre, email FROM Usuarios WHERE id = 1;
```

### Consultas Avanzadas

- **Selección de Columnas Específicas**
   - Enunciado 1: Obtener el total de usuarios registrados en la tabla `Usuarios`.
   - Enunciado 2: Calcular el promedio de edad de los usuarios registrados en la tabla `Usuarios`.
   - Enunciado 3: Obtener el total de pedidos realizados por cada usuario registrado en la tabla `Usuarios` ordenado por el total de pedidos.

```sql
SELECT COUNT(*) AS total_usuarios FROM Usuarios;
SELECT AVG(edad) AS promedio_edad FROM Usuarios;
SELECT nombre, COUNT(*) AS total_pedidos FROM Usuarios JOIN Pedidos ON Usuarios.id = Pedidos.usuario_id GROUP BY Usuarios.id;
```

- **Filtros y Condiciones (WHERE)**
   - Enunciado 4: Obtener el total de pedidos realizados y el monto total de ventas.
   - Enunciado 5: Obtener el total de productos por categoría.

```sql
SELECT COUNT(*) AS total_pedidos, SUM(total) AS monto_total_ventas FROM Pedidos;
SELECT categoria, COUNT(*) AS total_productos FROM Productos GROUP BY categoria;
```

- **Ordenación de Resultados (ORDER BY)**
   - Enunciado 6: Obtener el nombre y la edad de los usuarios registrados en la tabla `Usuarios` ordenados por edad de forma descendente.

```sql
SELECT nombre, edad FROM Usuarios ORDER BY edad DESC;
```

- **Funciones de Agregación (SUM, COUNT, AVG, etc.)**
   - Enunciado 7: Obtener la edad mínima y máxima de los estudiantes registrados en la tabla `Estudiantes`.

```sql
SELECT MIN(edad) AS edad_minima, MAX(edad) AS edad_maxima FROM Estudiantes;
```

- **Agrupación de Datos (GROUP BY)**
   - Enunciado 8: Obtener el total de pedidos realizados por cada usuario registrado en la tabla `Usuarios` ordenado por el total de pedidos.

```sql
SELECT nombre, COUNT(*) AS total_pedidos FROM Usuarios JOIN Pedidos ON Usuarios.id = Pedidos.usuario_id GROUP BY Usuarios.id;
```

- **Consultas de Unión (JOIN)**
   - Enunciado 9: Obtener el nombre y la categoría de los productos comprados por cada usuario registrado en la tabla `Usuarios`.

```sql
SELECT Usuarios.nombre, Productos.categoria FROM Usuarios JOIN Pedidos ON Usuarios.id = Pedidos.usuario_id JOIN DetallesPedidos ON Pedidos.id = DetallesPedidos.pedido_id JOIN Productos ON DetallesPedidos.producto_id = Productos.id;
```
