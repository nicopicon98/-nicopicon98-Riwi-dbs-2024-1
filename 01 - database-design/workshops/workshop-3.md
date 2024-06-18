# Taller de Normalización de Bases de Datos

## Descripción del Taller
Este taller está diseñado para ayudarte a entender y aplicar la normalización de bases de datos, comenzando desde cero hasta alcanzar un nivel avanzado. Aprenderás paso a paso cómo organizar y optimizar tus datos, reduciendo la redundancia y asegurando que cada dato sea preciso y útil. A través de actividades prácticas y ejemplos claros, irás mejorando tus habilidades y conocimientos de manera progresiva.

## Instrucciones de entrega

- Crea un nuevo repositorio en tu cuenta de GitHub llamado `database-design-normalization-workshop`.
- Sigue las instrucciones de cada módulo y realiza los ejercicios prácticos propuestos en herramientas como draw.io, Lucidchart, o cualquier otra herramienta de diagramación que prefieras.
- Sube tus respuestas a tu repositorio y comparte el enlace en moodle semana 2.

---

## Módulo 1: Introducción a la Normalización

### Objetivo
Entender los conceptos básicos de normalización y su importancia en bases de datos.

### Contenidos
- **Conceptos Básicos de Normalización:**
  - Definición de normalización: Proceso de organizar datos en tablas para reducir la redundancia y mejorar la integridad. Miralo de esta manera: si tienes una lista de amigos, no querrás repetir sus nombres cada vez que los menciones, ¿verdad? En lugar de eso, los guardas una vez y los referencias por un atributo que sea único y de esta manera garantizar que estemos hablando de la misma persona.
  - Importancia de la normalización en bases de datos:
    - Reducción de la redundancia: Evita la repetición innecesaria de datos. Esto es, si tienes un dato que se repite muchas veces, es mejor guardarlo una vez y referenciarlo. O por ejemplo, si tienes un dato que depende de otro, es mejor guardarlo en una tabla separada.
    - Mejora de la integridad y consistencia de los datos: Al tener los datos organizados de manera lógica, es más fácil mantenerlos actualizados y evitar errores.
    - Facilita la actualización y mantenimiento de la base de datos: Al tener una estructura clara y bien definida, es más sencillo agregar, modificar o eliminar datos sin afectar la integridad de la base de datos.
  - Ejemplo de una base de datos no normalizada:

    ```plaintext
    Estudiantes:
    | ID | Nombre       | Curso        | Profesor    |
    |----|--------------|--------------|-------------|
    | 1  | Juan Pérez   | Matemáticas  | Sr. López   |
    | 2  | Ana Gómez    | Ciencias     | Sra. García |
    | 3  | Juan Pérez   | Ciencias     | Sra. García |
    ```
  
  - ¿Qué está mal con esta tabla?
    - Repetición de datos: El nombre de Juan Pérez se repite dos veces.
    - Dependencias parciales: El profesor depende del curso, no del estudiante directamente.
    - Dependencias transitivas: El profesor depende indirectamente del estudiante.
  
  - ¿Cómo podemos mejorar esta tabla?
    - Normalizarla: Dividir la tabla en tablas más pequeñas y relacionadas.
    - ¿Cómo se vería después de la normalización?
  
    ```plaintext
    Estudiantes:
    | ID | Nombre       |
    |----|--------------|
    | 1  | Juan Pérez   |
    | 2  | Ana Gómez    |
    | 3  | Juan Pérez   |

    Cursos:
    | ID_Curso | Nombre_Curso |
    |----------|--------------|
    | 101      | Matemáticas  |
    | 102      | Ciencias     |

    Profesores:
    | ID_Profesor | Nombre_Profesor |
    |-------------|-----------------|
    | 1           | Sr. López       |
    | 2           | Sra. García     |

    Inscripciones:
    | ID_Estudiante | ID_Curso | ID_Profesor |
    |---------------|----------|-------------|
    | 1             | 101      | 1           |
    | 2             | 102      | 2           |
    | 3             | 102      | 2           |
    ```
---

## Módulo 2: Primera Forma Normal (1NF)

### Objetivo
Normalizar una base de datos a la Primera Forma Normal (1NF).

### Contenidos
- **Definición y Criterios de 1NF:**
  - Cada columna debe contener valores atómicos.
  - No debe haber conjuntos de valores repetidos.

- **Caso de Uso:**
  - Tabla inicial con valores repetidos:
  
    ```plaintext
    Estudiantes:
    | ID | Nombre       | Curso1      | Curso2      |
    |----|--------------|-------------|-------------|
    | 1  | Juan Pérez   | Matemáticas | Ciencias    |
    | 2  | Ana Gómez    | Ciencias    | Historia    |
    ```

  - Normalización a 1NF:

    ```plaintext
    Estudiantes:
    | ID | Nombre       | Curso       |
    |----|--------------|-------------|
    | 1  | Juan Pérez   | Matemáticas |
    | 1  | Juan Pérez   | Ciencias    |
    | 2  | Ana Gómez    | Ciencias    |
    | 2  | Ana Gómez    | Historia    |
    ```

  - ¿Qué cambió?
    - Ahora cada fila tiene un solo valor por columna.
    - Los valores repetidos se han separado en filas distintas. Si ahora no hay 2 cursos por estudiante, sino 30, no tendríamos que agregar 30 columnas, sino 30 filas.

  - ¿Por qué es importante?
    - Facilita la consulta y actualización de datos.
    - Evita la redundancia y mejora la integridad de los datos.

### Ejercicio Práctico

**Caso: Base de datos de una biblioteca**

El antiguo DBA de la biblioteca diseñó la base de datos de la siguiente manera:

```plaintext
Libros:
| ID_Libro | Titulo                | Autor1                | Autor2                | Autor3                | Genero1        | Genero2       |
|----------|-----------------------|-----------------------|-----------------------|-----------------------|----------------|---------------|
| 1        | Don Quijote           | Miguel de Cervantes   | NULL                  | NULL                  | Novela         | Clásico       |
| 2        | Cien Años de Soledad  | Gabriel García Márquez| NULL                  | NULL                  | Realismo Mágico| Novela        |
| 3        | La Odisea             | Homero                | NULL                  | NULL                  | Épica          | Clásico       |
| 4        | Good Omens            | Neil Gaiman           | Terry Pratchett       | NULL                  | Fantasía       | Comedia       |
```

#### Problemas identificados:

1. Las columnas Autor2 y Autor3 tienen valores NULL cuando el libro tiene un solo autor.
2. Las columnas Genero2 tienen valores NULL cuando el libro pertenece a un solo género.
3. No se puede añadir más de tres autores ni más de dos géneros sin modificar la estructura de la tabla.

#### Tareas a realizar: 

- Normaliza la tabla Libros a la Primera Forma Normal (1NF)

#### Instrucciones:

1. Reorganiza los datos de manera que cada columna contenga valores atómicos.
2. No debe haber conjuntos de valores repetidos. Como por ejemplo, si un libro tiene más de un autor, cada autor debe estar en una fila distinta.

---

## Módulo 3: Segunda Forma Normal (2NF)

### Objetivo
Normalizar una base de datos a la Segunda Forma Normal (2NF).

### Contenidos
- **Explicación de Claves Primarias y Dependencias Parciales:**
  - Clave primaria: Identificador único para cada registro.
  - Dependencias parciales: Cuando una columna depende solo de una parte de la clave primaria. Por ejemplo, si el nombre del curso depende del ID del curso, pero no del ID del estudiante, entonces hay una dependencia parcial.

- **Caso de Uso:**
  - Tabla en 1NF con dependencias parciales:

    ```plaintext
    Inscripciones:
    | ID_Estudiante | ID_Curso | Nombre_Estudiante | Nombre_Curso | Profesor    |
    |---------------|----------|-------------------|--------------|-------------|
    | 1             | 101      | Juan Pérez        | Matemáticas  | Sr. López   |
    | 1             | 102      | Juan Pérez        | Ciencias     | Sra. García |
    | 2             | 102      | Ana Gómez         | Ciencias     | Sra. García |
    ```

  - Normalización a 2NF:

    ```plaintext
    Estudiantes:
    | ID_Estudiante | Nombre_Estudiante |
    |---------------|-------------------|
    | 1             | Juan Pérez        |
    | 2             | Ana Gómez         |

    Cursos:
    | ID_Curso | Nombre_Curso |
    |----------|--------------|
    | 101      | Matemáticas  |
    | 102      | Ciencias     |

    Inscripciones:
    | ID_Estudiante | ID_Curso | Profesor    |
    |---------------|----------|-------------|
    | 1             | 101      | Sr. López   |
    | 1             | 102      | Sra. García |
    | 2             | 102      | Sra. García |
    ```

  - ¿Qué cambió?
    - Ahora cada tabla tiene una clave primaria única.
    - Las dependencias parciales se han eliminado al separar las tablas. Miralo de esta manera: si tienes un dato que depende de otro, pero también de un tercero, es mejor guardarlo en una tabla separada.

  - ¿Por qué es importante?
    - Evita la redundancia y mejora la integridad de los datos.
    - Facilita la actualización y mantenimiento de la base de datos.

### Ejercicio Práctico

**Caso: Base de datos de una tienda en línea**

El antiguo DBA de la tienda diseñó la base de datos de la siguiente manera:

```plaintext
Pedidos:
| ID_Pedido | ID_Producto | Cliente          | Dirección             | Producto      | Precio |
|-----------|-------------|------------------|-----------------------|---------------|--------|
| 1         | 101         | Juan Pérez       | Calle 123, Ciudad A   | Camiseta      | 20.00  |
| 1         | 102         | Juan Pérez       | Calle 123, Ciudad A   | Pantalones    | 25.00  |
| 2         | 103         | Ana Gómez        | Avenida 456, Ciudad B | Zapatos       | 50.00  |
| 2         | 101         | Ana Gómez        | Avenida 456, Ciudad B | Camiseta      | 20.00  |
```

#### Problemas identificados:

1. La información del cliente se repite para cada producto en el mismo pedido.
2. La información del producto se repite para cada pedido en el que aparece.

#### Tareas a realizar: 

- Normaliza la tabla Pedidos a la Segunda Forma Normal (2NF).

#### Instrucciones:

1. Crea tablas separadas para Clientes, Productos y Detalles de Pedidos.
2. Asegúrate de eliminar las dependencias parciales. Recordemos que una dependencia parcial es cuando una columna depende solo de una parte de la clave primaria, o sea, de un solo atributo y no de todos los atributos que conforman la clave primaria.

---

## Módulo 4: Tercera Forma Normal (3NF)

### Objetivo
Normalizar una base de datos a la Tercera Forma Normal (3NF).

### Contenidos
- **Definición y Eliminación de Dependencias Transitivas:**
  - Dependencias transitivas: Cuando una columna depende indirectamente de la clave primaria. Por ejemplo, si el profesor depende del curso, pero el curso depende del estudiante, entonces el profesor depende indirectamente del estudiante.

- **Caso de Uso:**
  - Tabla en 2NF con dependencias transitivas:

    ```plaintext
    Inscripciones:
    | ID_Estudiante | ID_Curso | Profesor    | Departamento |
    |---------------|----------|-------------|--------------|
    | 1             | 101      | Sr. López   | Matemáticas  |
    | 1             | 102      | Sra. García | Ciencias     |
    | 2             | 102      | Sra. García | Ciencias     |
    ```

  - Normalización a 3NF:

    ```plaintext
    Profesores:
    | ID_Profesor | Nombre_Profesor | Departamento |
    |-------------|------------------|--------------|
    | 1           | Sr. López        | Matemáticas  |
    | 2           | Sra. García      | Ciencias     |

    Inscripciones:
    | ID_Estudiante | ID_Curso | ID_Profesor |
    |---------------|----------|-------------|
    | 1             | 101      | 1           |
    | 1             | 102      | 2           |
    | 2             | 102      | 2           |
    ```

  - ¿Qué cambió?
    - Recordemos que la dependencia transitiva es cuando una columna depende indirectamente de la clave primaria. En este caso, el departamento depende del profesor, pero el profesor depende del curso, por lo que el departamento depende indirectamente del curso. Por ende, al separar las tablas, eliminamos esta dependencia transitiva.

### Ejercicio Práctico

**Caso: Base de datos de un hospital**

El antiguo DBA del hospital diseñó la base de datos de la siguiente manera:

```plaintext
Consultas:
| ID_Consulta | ID_Paciente | Paciente         | Doctor       | Especialidad |
|-------------|-------------|------------------|--------------|--------------|
| 1           | 100         | Juan Pérez       | Dr. Smith    | Cardiología  |
| 2           | 101         | Ana Gómez        | Dr. Johnson  | Neurología   |
| 3           | 100         | Juan Pérez       | Dr. Smith    | Cardiología  |
| 4           | 102         | Maria López      | Dr. Lee      | Pediatría    |
```

#### Problemas identificados:

1. La información del paciente se repite en varias consultas.
2. La especialidad del doctor se repite en cada consulta.

#### Tareas a realizar:

- Normaliza la tabla Consultas a la Tercera Forma Normal (3NF).

#### Instrucciones:

1. Crea tablas separadas para Pacientes, Doctores y Consultas.
2. Asegúrate de eliminar las dependencias transitivas. Una dependencia transitiva ocurre cuando una columna depende indirectamente de la clave primaria, es decir, depende de otro atributo que no es la clave primaria. Por ejemplo, en la tabla Inscripciones, el departamento dependía del profesor, y el profesor dependía del curso, por lo que el departamento dependía indirectamente del curso. Al separar las tablas, se eliminó esta dependencia transitiva (departamento -> profesor -> curso).

---

## Módulo 5: Forma Normal de Boyce-Codd (BCNF)

### Objetivo
Normalizar una base de datos a la Forma Normal de Boyce-Codd (BCNF).

### Contenidos
- **Explicación de la BCNF:**
  - Cada determinante debe ser una clave candidata.
    - Determinante: Atributo que determina el valor de otro atributo. Por ejemplo, en una tabla de empleados, el ID del empleado determina su nombre.
    - Clave candidata: Conjunto de atributos que identifica de manera única a cada fila de una tabla.
  - Se usa cuando la 3NF no es suficiente para eliminar todas las dependencias.

- **Caso de Uso:**
  - Situación donde 3NF no es suficiente:

    ```plaintext
    Cursos:
    | ID_Curso | Nombre_Curso | ID_Profesor |
    |----------|--------------|-------------|
    | 101      | Matemáticas  | 1           |
    | 102      | Ciencias     | 2           |
    | 103      | Historia     | 1           |
    ```

  - Normalización a BCNF:

    ```plaintext
    Cursos:
    | ID_Curso | Nombre_Curso |
    |----------|--------------|
    | 101      | Matemáticas  |
    | 102      | Ciencias     |
    | 103      | Historia     |

    Curso_Profesor:
    | ID_Curso | ID_Profesor |
    |----------|-------------|
    | 101      | 1           |
    | 102      | 2           |
    | 103      | 1           |
    ```

  - ¿Qué cambió?
    - Ahora cada determinante es una clave candidata.
    - Se eliminan las dependencias no deseadas y se garantiza la integridad de los datos.

### Ejercicio Práctico

**Caso: Base de datos de proyectos de investigación**

El antiguo DBA de la universidad diseñó la base de datos de la siguiente manera:

```plaintext
Proyectos:
| ID_Proyecto | Nombre_Proyecto    | ID_Profesor | Nombre_Profesor |
|-------------|--------------------|-------------|------------------|
| 1           | IA Avanzada        | 101         | Dr. Smith        |
| 2           | Robótica           | 102         | Dr. Johnson      |
| 3           | IA Aplicada        | 101         | Dr. Smith        |
| 4           | Redes de Computo   | 103         | Dr. Lee          |
```

#### Problemas identificados:

1. El nombre del profesor se repite en varias filas.
2. Existe una dependencia funcional parcial entre ID_Profesor y Nombre_Profesor.

#### Tareas a realizar:

Normaliza la tabla Proyectos a la Forma Normal de Boyce-Codd (BCNF).

#### Instrucciones:

1. Crea tablas separadas para Proyectos y Profesores.
2. Asegúrate de que cada determinante sea una clave candidata. Una clave candidata es un conjunto de atributos que identifica de manera única a cada fila de una tabla. Por ejemplo, en la tabla Empleados, el ID del empleado es una clave candidata porque identifica de manera única a cada empleado.

---

## Módulo 6: Cuarta y Quinta Forma Normal (4NF y 5NF)

### Objetivo
Normalizar una base de datos a la Cuarta y Quinta Forma Normal (4NF y 5NF).

### Contenidos
- **Definición y Criterios:**
  - **4NF:** Eliminación de dependencias multi-valuadas.
  - **5NF:** Eliminación de juntas de dependencia.
  - Se utilizan cuando la BCNF no es suficiente para eliminar todas las dependencias.

- **Caso de Uso para 4NF:**
  - Tabla con dependencias multi-valuadas:

    ```plaintext
    Proyectos:
    | ID_Proyecto | Nombre_Proyecto | ID_Empleado | ID_Habilidad |
    |-------------|------------------|-------------|--------------|
    | 1           | Proyecto A       | 1           | 101          |
    | 1           | Proyecto A       | 1           | 102          |
    | 1           | Proyecto A       | 2           | 101          |
    ```

  - Normalización a 4NF:

    ```plaintext
    Proyectos:
    | ID_Proyecto | Nombre_Proyecto |
    |-------------|------------------|
    | 1           | Proyecto A       |

    Proyecto_Empleado:
    | ID_Proyecto | ID_Empleado |
    |-------------|-------------|
    | 1           | 1           |
    | 1           | 2           |

    Empleado_Habilidad:
    | ID_Empleado | ID_Habilidad |
    |-------------|--------------|
    | 1           | 101          |
    | 1           | 102          |
    | 2           | 101          |
    ```

  - ¿Qué cambió?
    - Se eliminan las dependencias multi-valuadas.
    - Cada tabla tiene una sola dependencia y se garantiza la integridad de los datos.

- **Caso de Uso para 5NF:**
  - Tabla con juntas de dependencia:

    ```plaintext
    Contratos:
    | ID_Proyecto | ID_Empleado | ID_Proveedor |
    |-------------|-------------|--------------|
    | 1           | 1           | 1001         |
    | 1           | 2           | 1002         |
    | 2           | 1           | 1001         |
    ```

  - Normalización a 5NF:

    ```plaintext
    Proyectos:
    | ID_Proyecto | Nombre_Proyecto |
    |-------------|------------------|
    | 1           | Proyecto A       |
    | 2           | Proyecto B       |

    Proyecto_Empleado:
    | ID_Proyecto | ID_Empleado |
    |-------------|-------------|
    | 1           | 1           |
    | 1           | 2           |
    | 2           | 1           |

    Proyecto_Proveedor:
    | ID_Proyecto | ID_Proveedor |
    |-------------|--------------|
    | 1           | 1001         |
    | 2           | 1001         |
    | 1           | 1002         |
    ```

  - ¿Qué cambió?
    - Se eliminan las juntas de dependencia.
    - Cada tabla tiene una sola dependencia y se garantiza la integridad de los datos.


### Ejercicio Práctico para 4NF

**Caso: Base de datos de empleados y habilidades**

El antiguo DBA de la empresa diseñó la base de datos de la siguiente manera:

```plaintext
Empleado_Habilidades:
| ID_Empleado | Nombre_Empleado | Habilidad           |
|-------------|-----------------|---------------------|
| 1           | Juan Pérez      | Programación        |
| 1           | Juan Pérez      | Diseño de Bases de Datos |
| 2           | Ana Gómez       | Programación        |
| 2           | Ana Gómez       | Análisis de Datos   |
```

#### Problemas identificados:

1. La información de habilidades multi-valuadas.
2. La información de empleados se repite en varias filas

#### Tareas a realizar:

Normaliza la tabla Empleado_Habilidades a la Cuarta Forma Normal (4NF).

#### Instrucciones:

1. Crea tablas separadas para Empleados y Habilidades.
2. Asegúrate de eliminar las dependencias multi-valuadas. Recordemos por dependencia multi-valuada a cuando un atributo depende de un conjunto de otros atributos, en lugar de depender de un solo atributo. Esto, lo podemos lograr separando los atributos en tablas distintas.

### Ejercicio Práctico para 5NF

Caso: Base de datos de contratos

El antiguo DBA de la empresa diseñó la base de datos de la siguiente manera:

```plaintext
Contratos:
| ID_Proyecto | ID_Empleado | ID_Proveedor |
|-------------|-------------|--------------|
| 1           | 1           | 1001         |
| 1           | 2           | 1002         |
| 2           | 1           | 1001         |
```

#### Problemas identificados:

1. Existencia de juntas de dependencia entre proyectos, empleados y proveedores. Recordemos que una junta de dependencia ocurre cuando un atributo depende de otro atributo que no es la clave primaria. Aqui, esto esta ocurriendo entre los atributos ID_Empleado e ID_Proveedor, puesto que ambos dependen del ID_Proyecto.

#### Tareas a realizar:

Normaliza la tabla Contratos a la Quinta Forma Normal (5NF).

#### Instrucciones:

1. Crea tablas separadas para Proyectos, Empleados y Proveedores.
2. Asegúrate de eliminar las juntas de dependencia. Una junta de dependencia ocurre cuando un atributo depende de otro atributo que no es la clave primaria. Por ejemplo, en la tabla Contratos, el ID_Empleado y el ID_Proveedor dependen del ID_Proyecto, en lugar de depender de la clave primaria de su propia tabla.

---

## Módulo 7: Redundancia de Datos en la vida real

### Objetivo
Entender cómo la normalización ayuda a reducir la redundancia de datos en casos reales.

### Contenidos
- **Explicación de la Reducción de Redundancia:**
  - Beneficios de eliminar datos duplicados.
  - Mejora en la integridad y consistencia de los datos.

- **Caso de Uso:**
  - Tabla inicial con datos duplicados:

    ```plaintext
    Estudiantes:
    | ID | Nombre       | Curso        |
    |----|--------------|--------------|
    | 1  | Juan Pérez   | Matemáticas  |
    | 2  | Ana Gómez    | Ciencias     |
    | 1  | Juan Pérez   | Matemáticas  |
    ```

  - Normalización para eliminar duplicados:

    ```plaintext
    Estudiantes:
    | ID | Nombre       |
    |----|--------------|
    | 1  | Juan Pérez   |
    | 2  | Ana Gómez    |

    Cursos:
    | ID_Curso | Nombre_Curso |
    |----------|--------------|
    | 101      | Matemáticas  |
    | 102      | Ciencias     |

    Inscripciones:
    | ID_Estudiante | ID_Curso |
    |---------------|----------|
    | 1             | 101      |
    | 2             | 102      |
    ```
### Ejercicio Práctico

**Caso: Base de datos de ventas en una tienda**

El antiguo DBA de la tienda diseñó la base de datos de la siguiente manera:

```plaintext
Ventas:
| ID_Venta | Cliente        | Producto     | Precio | Fecha       |
|----------|----------------|--------------|--------|-------------|
| 1        | Juan Pérez     | Camiseta     | 20.00  | 2023-01-01  |
| 2        | Ana Gómez      | Pantalones   | 25.00  | 2023-01-02  |
| 3        | Juan Pérez     | Camiseta     | 20.00  | 2023-01-03  |
```

#### Problemas identificados:

1. La información del cliente se repite en varias ventas.
2. La información del producto y su precio se repiten en varias ventas.

#### Tareas a realizar:

Normaliza la tabla Ventas para eliminar la redundancia de datos.

#### Instrucciones:

1. Crea tablas separadas para Clientes, Productos y Ventas.
2. Asegúrate de eliminar los datos duplicados.

---

## Módulo 8: Atomicidad de Datos en Bases de Datos en la vida real

### Objetivo
Comprender la importancia de la atomicidad en bases de datos en casos reales.

### Contenidos
- **Importancia de la Atomicidad:**
  - Garantiza que las transacciones se completen de manera total o no se realicen en absoluto.
  - Evita inconsistencias en los datos.

- **Caso de Uso:**
  - Ejemplo de registros no atómicos:

    ```plaintext
    Pedidos:
    | ID_Pedido | Cliente       | Producto_Cantidad        |
    |-----------|---------------|--------------------------|
    | 1         | Juan Pérez    | TV:1, Radio:2            |
    | 2         | Ana Gómez     | Laptop:1, Mouse:1        |
    ```

  - Normalización para lograr atomicidad:

    ```plaintext
    Pedidos:
    | ID_Pedido | Cliente       |
    |-----------|---------------|
    | 1         | Juan Pérez    |
    | 2         | Ana Gómez     |

    Detalle_Pedidos:
    | ID_Pedido | Producto | Cantidad |
    |-----------|----------|----------|
    | 1         | TV       | 1        |
    | 1         | Radio    | 2        |
    | 2         | Laptop   | 1        |
    | 2         | Mouse    | 1        |
    ```

### Ejercicio Práctico

**Caso: Base de datos de inventarios en un almacén**

El antiguo DBA del almacén diseñó la base de datos de la siguiente manera:

```plaintext
Inventarios:
| ID_Inventario | Producto         | Cantidad_Ubicaciones           |
|---------------|------------------|--------------------------------|
| 1             | Tornillos        | A1:100, B2:200                 |
| 2             | Clavos           | A3:150, B4:100                 |
```

#### Problemas identificados:

1. La información de las ubicaciones y cantidades no es atómica.
2. La información de los productos se repite en varias filas.

#### Tareas a realizar:

Normaliza la tabla Inventarios para lograr atomicidad en los datos.

#### Instrucciones:

1. Crea tablas separadas para Inventarios y Detalle_Ubicaciones.
2. Asegúrate de que cada registro en las tablas contenga valores atómicos.

---

## Modulo 9: Conclusiones de un ex DBA

En el mundo real, es común encontrarse con bases de datos que no están completamente normalizadas, y eso está bien. La normalización es un proceso destinado a mejorar la estructura y eficiencia de una base de datos, pero no siempre es necesario o posible en todos los casos. Más que una regla estricta, debemos ver la normalización como una guía para mejorar la calidad de nuestros datos, facilitando su consulta, actualización y mantenimiento. No obstante, es crucial comprender los principios de la normalización y saber cuándo y cómo aplicarlos en situaciones prácticas.

A lo largo de nuestra experiencia, también descubrimos que la desnormalización es una práctica común, especialmente en sistemas que demandan alto rendimiento y escalabilidad. La desnormalización implica añadir redundancia de datos para mejorar el rendimiento de las consultas, sacrificando en cierta medida la integridad y consistencia de los datos. Es un equilibrio que se ajusta según las necesidades del sistema y los recursos disponibles.

Desde nuestros primeros pasos con Python, HTML, CSS y JavaScript hasta el manejo de bases de datos, hemos aprendido que en programación no hay una única respuesta correcta para todas las situaciones. Lo esencial es comprender a fondo el problema que enfrentamos, sumergirnos en él con preguntas, pruebas y errores, hasta encontrar la solución que mejor se adapte a nuestras necesidades.

En última instancia, una lección crucial de la arquitectura de bases de datos y del software en general es que los requisitos no funcionales, como la escalabilidad, rendimiento y seguridad, son tan importantes, o incluso más, que los requisitos funcionales. Estos factores determinan el diseño de la base de datos, la elección de la arquitectura y las tecnologías a utilizar, y en general, la calidad del sistema que estamos construyendo. Al diseñar, normalizar o desnormalizar una base de datos, siempre pregúntate: ¿Qué impacto tendrá en la escalabilidad, rendimiento y seguridad de mi sistema? Con esta mentalidad, estarás un paso más cerca de convertirte en un experto en bases de datos.

Saludos de su Team Lead Nico,

---