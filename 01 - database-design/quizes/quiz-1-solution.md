1. B, C, D
2. C
3. C
4. A, C, D
5. Una clave primaria es un atributo o un conjunto de atributos que identifican de manera única a cada registro en una tabla. Por ejemplo, en una tabla de "Estudiantes", el "ID de Estudiante" podría ser la clave primaria. Una clave foránea es un atributo en una tabla que se utiliza para referenciar la clave primaria de otra tabla, estableciendo así una relación entre las dos tablas. Por ejemplo, si una tabla "Matrículas" tiene un "ID de Estudiante" que se refiere al "ID de Estudiante" en la tabla "Estudiantes", entonces "ID de Estudiante" en "Matrículas" es una clave foránea.
6. B
7. La herencia en un diagrama Entidad-Relación Extendido (EER) permite que una entidad hija herede atributos y relaciones de una entidad padre, similar a la herencia en programación orientada a objetos. Se representa gráficamente mediante un triángulo que conecta la entidad padre con sus entidades hijas. Su propósito es modelar la jerarquía y especialización de entidades, facilitando la organización y reutilización de atributos comunes.
8. C
9. A, B, C
10. Las restricciones de usuario en un diagrama ER afectan el diseño al imponer condiciones específicas que deben cumplirse para mantener la integridad y exactitud de los datos. Un ejemplo de restricción de usuario podría ser "un estudiante solo puede estar inscrito en un máximo de cinco cursos al mismo tiempo". Esta restricción influirá en el diagrama al requerir validaciones adicionales en las relaciones y posiblemente en las reglas de negocio implementadas en el sistema.
11. C
12. A, B, C
13. B
14. Un diagrama Entidad-Relación (ER) es una representación gráfica que muestra la estructura lógica de una base de datos mediante entidades (objetos o conceptos) y las relaciones entre ellas. Es importante en el diseño de bases de datos porque ayuda a visualizar y planificar cómo los datos serán almacenados, organizados y relacionados, facilitando la comunicación entre diseñadores y desarrolladores y asegurando que la base de datos cumpla con los requisitos del sistema.
15. A
16. A, C
17. C
18. B
19. Una relación identificativa es aquella en la que la existencia de una entidad depende de la existencia de otra entidad y se identifica mediante la clave primaria de la entidad relacionada. Por ejemplo, una "Factura" (identificativa) que depende de un "Cliente". Una relación no identificativa es aquella en la que la entidad puede existir independientemente de la otra. Por ejemplo, una relación entre "Estudiantes" y "Cursos" donde un curso puede existir sin que ningún estudiante esté inscrito en él.
20. A, C, D
21. C
22. A, D, E
23. La cardinalidad en un diagrama ER describe el número de instancias de una entidad que pueden estar asociadas con una instancia de otra entidad. Los tipos de cardinalidad incluyen uno a uno (1:1), uno a muchos (1:M), y muchos a muchos (M:N). Por ejemplo, en una relación uno a uno, cada estudiante tiene un único carnet de biblioteca; en una relación uno a muchos, un profesor puede enseñar muchos cursos; en una relación muchos a muchos, muchos estudiantes pueden estar inscritos en muchos cursos.
24. C
25. A, C, E
26. D
27. Una relación recursiva en un diagrama ER es una relación en la que una entidad está relacionada consigo misma. Un ejemplo práctico es una estructura jerárquica de empleados donde cada empleado puede tener un supervisor que también es un empleado. Esto se representa con una relación que conecta la entidad "Empleado" consigo misma.
28. C
29. A, C

### Pregunta 30: Respuesta Abierta

#### Clientes

- ID de cliente (PK)
- Nombre completo
- Dirección
- Número de teléfono
- Correo electrónico
- Fecha de registro
- Tipo de cliente (individual o corporativo)
- Estado
- Relación: 1 opcional a muchos mandatory con **Cuentas Bancarias**.
- Relación: 1 opcional a muchos opcional con **Tarjetas de Crédito**.
- Relación: 1 opcional a muchos opcional con **Préstamos**.
- Relación: 1 opcional a muchos opcional con **Productos Financieros**.
- Relación: 1 opcional a muchos opcional con **Inversiones**.
- Relación: 1 opcional a muchos opcional con **Contactos de Emergencia**.

#### Cuentas Bancarias

- Número de cuenta (PK)
- Tipo de cuenta (ahorros, corriente, depósito a plazo fijo)
- Saldo
- Fecha de apertura
- Estado de la cuenta
- Moneda
- ID de cliente (FK)
- Relación: 1 mandatory a muchos opcional con **Transacciones**.
- Relación: Muchos opcional a 1 opcional con **Empleados**.
- Relación: 1 mandatory a muchos opcional con **Sucursales**.

#### Transacciones

- ID de transacción (PK)
- Tipo de transacción (depósito, retiro, transferencia, pago de préstamo, pago de tarjeta de crédito)
- Monto
- Fecha
- Hora
- Método de pago
- Número de cuenta (FK)
- ID de préstamo (FK, opcional)
- ID de empleado (FK, opcional)
- Relación: Muchos opcional a 1 mandatory con **Cuentas Bancarias**.
- Relación: Muchos opcional a 1 opcional con **Préstamos**.
- Relación: Muchos opcional a 1 opcional con **Empleados**.

#### Préstamos

- ID de préstamo (PK)
- Monto del préstamo
- Tasa de interés
- Fecha de inicio
- Fecha de vencimiento
- Estado del préstamo
- Tipo de préstamo (personal, hipotecario, automotriz)
- ID de cliente (FK)
- Relación: Muchos opcional a 1 opcional con **Transacciones**.

#### Empleados

- ID de empleado (PK)
- Nombre completo
- Puesto
- Salario
- Fecha de contratación
- Estado
- ID de sucursal (FK)
- Relación: Muchos opcional a 1 opcional con **Cuentas Bancarias**.
- Relación: Muchos opcional a 1 opcional con **Empleados** (supervisión).
- Relación: Muchos opcional a muchos opcional con **Departamentos**.
- Relación: Muchos opcional a muchos opcional con **Proyectos**.
- Relación: Muchos opcional a muchos opcional con **Auditorías**.

#### Sucursales

- ID de sucursal (PK)
- Nombre de la sucursal
- Dirección
- Número de teléfono
- País
- Región
- Fecha de apertura
- Relación: 1 mandatory a muchos opcional con **Empleados**.
- Relación: 1 mandatory a muchos opcional con **Cuentas Bancarias**.

#### Productos Financieros

- ID de producto (PK)
- Nombre del producto
- Tipo de producto (tarjeta de crédito, seguro, hipoteca, inversión, préstamo)
- Descripción
- Condiciones
- Fecha de lanzamiento
- Relación: Muchos opcional a muchos opcional con **Clientes**.

#### Departamentos

- ID de departamento (PK)
- Nombre del departamento
- ID de sucursal (FK)
- Relación: 1 mandatory a muchos opcional con **Empleados**.

#### Tarjetas de Crédito

- ID de tarjeta (PK)
- Número de tarjeta
- Límite de crédito
- Saldo actual
- Fecha de expiración
- Tipo de tarjeta (clásica, oro, platino)
- Estado
- ID de cliente (FK)
- Relación: Muchos opcional a 1 mandatory con **Clientes**.

#### Seguros

- ID de seguro (PK)
- Tipo de seguro (vida, salud, auto, hogar)
- Cobertura
- Prima
- Fecha de inicio
- Fecha de fin
- Estado
- ID de cliente (FK)
- Relación: Muchos opcional a 1 mandatory con **Clientes**.
- Relación: Muchos opcional a 1 opcional con **Reclamaciones**.

#### Hipotecas

- ID de hipoteca (PK)
- Monto
- Tasa de interés
- Fecha de inicio
- Fecha de fin
- Estado
- ID de cliente (FK)
- Relación: Muchos opcional a 1 mandatory con **Clientes**.
- Relación: Muchos opcional a 1 opcional con **Transacciones**.

#### Inversiones

- ID de inversión (PK)
- Tipo de inversión (acciones, bonos, fondos mutuos, bienes raíces)
- Monto invertido
- Fecha de inicio
- Valor actual
- Estado
- ID de cliente (FK)
- Relación: Muchos opcional a 1 mandatory con **Clientes**.

#### Agencias

- ID de agencia (PK)
- Nombre
- Dirección
- Número de teléfono
- Tipo de agencia (publicidad, reclutamiento, consultoría)
- Relación: Muchos opcional a muchos opcional con **Sucursales**.
- Relación: Muchos opcional a muchos opcional con **Empleados**.
- Relación: Muchos opcional a muchos opcional con **Proyectos**.

#### Proveedores

- ID de proveedor (PK)
- Nombre
- Dirección
- Número de teléfono
- Tipo de servicios proporcionados
- Fecha de inicio del contrato
- Relación: Muchos opcional a muchos opcional con **Sucursales**.
- Relación: Muchos opcional a muchos opcional con **Auditorías**.

#### Auditorías

- ID de auditoría (PK)
- Fecha
- Auditor responsable
- Resultados
- Recomendaciones
- Estado
- Relación: Muchos opcional a muchos opcional con **Sucursales**.
- Relación: Muchos opcional a muchos opcional con **Departamentos**.
- Relación: Muchos opcional a muchos opcional con **Proveedores**.
- Relación: Muchos opcional a muchos opcional con **Proyectos**.
- Relación: Muchos opcional a muchos opcional con **Empleados**.

#### Reclamaciones

- ID de reclamación (PK)
- Fecha
- Tipo de reclamación (seguro, servicio)
- Monto reclamado
- Estado
- Resolución
- ID de seguro (FK)
- Relación: Muchos opcional a 1 mandatory con **Seguros**.
- Relación: Muchos opcional a 1 opcional con **Transacciones**.

#### Contactos de Emergencia

- ID de contacto (PK)
- Nombre
- Relación con el cliente
- Número de teléfono
- Dirección
- ID de cliente (FK)
- Relación: Muchos opcional a 1 mandatory con **Clientes**.

#### Proyectos

- ID de proyecto (PK)
- Nombre
- Descripción
- Fecha de inicio
- Fecha de fin
- Estado
- Presupuesto
- Relación: Muchos opcional a muchos opcional con **Empleados**.
- Relación: Muchos opcional a muchos opcional con **Departamentos**.
- Relación: Muchos opcional a muchos opcional con **Agencias**.
- Relación: Muchos opcional a muchos opcional con **Contratos**.
- Relación: Muchos opcional a muchos opcional con **Auditorías**.

#### Contratos

- ID de contrato (PK)
- Fecha de inicio
- Fecha de finalización
- Partes involucradas (clientes, proveedores, agencias)
- Términos y condiciones
- Estado
- Relación: Muchos opcional a muchos opcional con **Proyectos**.
- Relación: Muchos opcional a muchos opcional con **Productos Financieros**.
