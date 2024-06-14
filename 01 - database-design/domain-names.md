# Nombres de Dominio

## Introducción

En el contexto de bases de datos relacionales, los nombres de dominio se refieren a las categorías o conjuntos de valores que un atributo puede tener. Los dominios ayudan a definir las reglas y restricciones que se aplican a los datos almacenados en una tabla, asegurando la integridad y consistencia de los datos.

## Tipos de Nombres de Dominio

### Numéricos
- **Enteros** (integer, smallint, bigint): Conjunto de números enteros.
- **Decimales** (decimal, numeric, float, real): Conjunto de números con puntos decimales.
- **Monetarios** (money, smallmoney): Conjunto de valores numéricos usados para representar cantidades de dinero.

### Texto
- **Cadenas de caracteres** (char, varchar, text): Conjunto de secuencias de caracteres.
- **Cadenas fijas** (char): Conjunto de secuencias de caracteres de longitud fija.
- **Cadenas variables** (varchar): Conjunto de secuencias de caracteres de longitud variable.

### Fecha y Hora
- **Fechas** (date): Conjunto de valores que representan fechas.
- **Hora** (time): Conjunto de valores que representan tiempo.
- **Fecha y Hora** (datetime, timestamp): Conjunto de valores que representan una combinación de fecha y hora.

### Booleanos
- **Booleano** (boolean): Conjunto de valores que representan verdadero (true) o falso (false).

### Binarios
- **Datos binarios** (binary, varbinary): Conjunto de secuencias de datos binarios.
- **Imágenes** (image): Conjunto de datos binarios usados para almacenar imágenes.

### Identificadores y Códigos
- **UUID** (uuid): Conjunto de identificadores únicos universales.
- **Códigos** (alphanumeric): Conjunto de valores alfanuméricos usados como códigos.

### Enumerados
- **Valores enumerados** (enum): Conjunto de valores predefinidos y limitados.

### Geográficos
- **Puntos** (point): Conjunto de coordenadas de puntos en un espacio geométrico.
- **Líneas** (line): Conjunto de coordenadas de líneas en un espacio geométrico.
- **Polígonos** (polygon): Conjunto de coordenadas de polígonos en un espacio geométrico.

## Ejemplos de Uso

### Tabla de Atributos con Dominios

| Nombre Entidad | Atributos         | Identificador Único (UID) | Nombre dominio | Tipo de Dato | Tamaño | Obligatoriedad | Restricciones adicionales     |
|----------------|-------------------|---------------------------|----------------|--------------|--------|----------------|-------------------------------|
| Cliente        | ID                | x                         | Numérico       | Número       | 10     | Sí             | Solo números positivos        |
|                | Nombre            |                           | Texto          | Texto        | 100    | Sí             | Solo letras                   |
|                | FechaNacimiento   |                           | Fecha          | Fecha        | -      | Sí             | Fecha válida                  |
|                | Email             |                           | Texto          | Texto        | 255    | Sí             | Formato de email válido       |
|                | EsActivo          |                           | Booleano       | Booleano     | -      | Sí             | Solo true/false               |
|                | ImagenPerfil      |                           | Binario        | Varbinary    | 1024   | No             | Solo datos binarios           |
|                | CodigoDescuento   |                           | Alfanumérico   | Varchar      | 20     | No             | Letras y números sin espacios |
