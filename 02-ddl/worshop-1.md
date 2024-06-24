# Taller: Introducción al Lenguaje de Definición de Datos (DDL) en Bases de Datos Relacionales

## Objetivos

1. **Memorizar** los conceptos básicos del Lenguaje de Definición de Datos (DDL) en bases de datos relacionales.
2. **Comprender** y aplicar los conceptos de entidades, atributos y relaciones mediante DDL.
3. **Aplicar** los diferentes tipos de cardinalidad en la creación de tablas y relaciones mediante DDL.
4. **Analizar** y diseñar esquemas de bases de datos relacionales utilizando DDL.
5. **Evaluar** la estructura de un esquema de base de datos y sugerir mejoras.
6. **Crear** un esquema completo de base de datos para un sistema de información específico utilizando DDL.

## Contenidos

1. **Recordar**: Conceptos básicos de bases de datos relacionales y DDL.
2. **Comprender**: Identificación de entidades, atributos, claves primarias (PK), claves foráneas (FK) y relaciones mediante DDL.
3. **Aplicar**: Tipos de cardinalidad y su implementación en DDL:
   - Uno a Uno (1:1).
   - Uno a Muchos (1:N).
   - Muchos a Muchos (M:N).
4. **Analizar**: Diferencias entre el modelo relacional y el modelo entidad-relación.
5. **Crear**: Esquemas de bases de datos relacionales utilizando DDL.

## Recursos

- [data-types](../data-types.md)
- [foreign-Keys](../foreign-keys.md)
- [update-delete-options](../foreign-keys/update-delete-options.md)
- [ddl-sintaxys](./sintaxys.md)

## Instrucciones de entrega

- **Repositorio en github:** Crear un repositorio en github con el nombre `ddl-workshop`.
- **Estructura de carpetas:** Crear una carpeta para cada ejercicio con el nombre `exercise-1`, `exercise-2`, `exercise-3`, `exercise-4`.
- **Scripts DDL:** Incluir los scripts DDL (archivos `.sql`) en cada carpeta de ejercicio.

## Introducción Teórica

### Lenguaje de Definición de Datos (DDL)

**Definición y Propósito del DDL**

El DDL es un subconjunto del SQL que se utiliza para definir y modificar la estructura de las bases de datos. Las instrucciones DDL se utilizan para crear, alterar y eliminar objetos de la base de datos como tablas, índices y vistas.

- **CREATE:** Crea objetos de base de datos nuevos.
- **ALTER:** Modifica la estructura de objetos de base de datos existentes.
- **DROP:** Elimina objetos de base de datos.

### Creación de Tablas

```sql
CREATE TABLE Usuarios (
    id INT PRIMARY KEY,
    nombre VARCHAR(100),
    email VARCHAR(100)
);
```

### Modificación de Tablas

```sql
ALTER TABLE Usuarios ADD COLUMN fecha_registro DATE;
```

### Eliminación de Tablas

```sql
DROP TABLE Usuarios;
```

## Ejericios Prácticos

### Ejercicio 1

Vamos a empezar con algo sencillo. Sé que a este punto te estarás preguntando "Bueno profe, y `CREATE DATABASE`, `DROP DATABASE`, ¿dónde quedan?". Tranquilos, creación de bases de datos, eliminación de bases de datos y esquemas también son parte del DDL.

No te preocupes, también cubriremos estos comandos fundamentales para la gestión de bases de datos. Aquí tienes algunos ejercicios prácticos para familiarizarte con ellos:

- Para crear una base de datos, utiliza el comando `CREATE DATABASE` seguido del nombre de la base de datos. Por ejemplo, `CREATE DATABASE MiBaseDeDatos;`.
- Para eliminar una base de datos, utiliza el comando `DROP DATABASE` seguido del nombre de la base de datos. Por ejemplo, `DROP DATABASE MiBaseDeDatos;`.

- Ahora si, hablemos del ejercicio: Has sido contratado para crear una base de datos para una empresa de plomería. La base de datos debe contener información sobre los clientes, los servicios que han solicitado y los plomeros que han realizado los servicios.

- Crea una base de datos llamada `plumbing`.
- Crea las siguientes tablas:

  - `clientes` con los campos
    - `id` (clave primaria) autoincremental,
    - `nombre` (cadena de texto de máximo 50 caracteres) no nulo,
    - `email` (cadena de texto de máximo 50 caracteres) no nulo,
    - `telefono` (cadena de texto de máximo 15 caracteres) no nulo.
  - `servicios` con los campos:
    - `id` (clave primaria) autoincremental,
    - `nombre` (cadena de texto de máximo 50 caracteres) no nulo,
    - `descripcion` (cadena de texto de máximo 255 caracteres) no nulo,
    - `precio` (número decimal) no nulo.
  - `plomeros` con los campos:
    - `id` (clave primaria) autoincremental,
    - `nombre` (cadena de texto de máximo 50 caracteres) no nulo,
    - `email` (cadena de texto de máximo 50 caracteres) no nulo,
    - `telefono` (cadena de texto de máximo 15 caracteres) no nulo.
  - `facturas` con los campos:
    - `id` (clave primaria) autoincremental,
    - `cliente_id` (clave foránea) no nulo,
    - `servicio_id` (clave foránea) no nulo,
    - `plomero_id` (clave foránea) no nulo,
    - `fecha` (fecha) no nulo,
    - `total` (número decimal) no nulo.
  - `descuentos` con los campos:
    - `id` (clave primaria) autoincremental,
    - `factura_id` (clave foránea) no nulo,
    - `monto` (número decimal) no nulo.
  - `pagos` con los campos:
    - `id` (clave primaria) autoincremental,
    - `factura_id` (clave foránea) nulo,
    - `monto` (número decimal) no nulo,
    - `fecha` (fecha) no nulo.
  - `auditoria` con los campos:
    - `id` (clave primaria) autoincremental,
    - `tabla` (cadena de texto de máximo 50 caracteres) no nulo,
    - `accion` (cadena de texto de máximo 50 caracteres) no nulo,
    - `fecha` (fecha) no nulo.

- Con base en el archivo [data-types](../data-types.md), crea las siguientes relaciones:

  - Un cliente puede solicitar uno o varios servicios. Un servicio esta asociado a un solo cliente.
  - Un plomero puede realizar uno o varios servicios. Un servicio puede ser realizado por uno o varios plomeros.
  - Una factura puede tener uno o varios descuentos. Un descuento esta asociado a una sola factura.
  - Todas las tablas tienen una relación con la tabla `auditoria` de 1:N.

- El DBA se equivocó y olvidó agregar un campo a la tabla `clientes`. Agrega un campo llamado `direccion` (cadena de texto de máximo 255 caracteres) a la tabla `clientes`.
- El DBA también olvidó agregar un campo a la tabla `servicios`. Agrega un campo llamado `fecha` (fecha) a la tabla `servicios`.
- El DBA cometió otro error y olvidó agregar un campo a la tabla `plomeros`. Agrega un campo llamado `direccion` (cadena de texto de máximo 255 caracteres) a la tabla `plomeros`.
- El DBA cometió otro error y olvidó agregar un campo a la tabla `facturas`. Agrega un campo llamado `direccion` (cadena de texto de máximo 255 caracteres) a la tabla `facturas`.

- El DBA cometió otro error y es que olvido definir como no nulo el campo `factura_id` en la tabla `pagos`. Modifica la tabla `pagos` para que el campo `factura_id` sea no nulo. A este punto recuerda que tienes el archivo [data-types](../data-types.md) y [foreign-keys](../foreign-keys.md) como referencia.

- El DBA se percató que cometió otro error y es que olvido que la tabla `descuentos` no tiene relación con la tabla `auditoria`. Has esto leyendo el archivo [foreign-keys](../foreign-keys.md) como referencia.