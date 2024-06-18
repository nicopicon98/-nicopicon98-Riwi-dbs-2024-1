# Segundo Escenario (Segunda Ronda)

## Caso de Estudio 1: Universidad Internacional "EducaGlobal"

La Universidad Internacional "EducaGlobal" necesita una base de datos para gestionar sus operaciones académicas y administrativas. La base de datos debe capturar información detallada sobre estudiantes, cursos, profesores, departamentos, horarios, calificaciones, matrículas, y becas. A continuación se describen los requisitos detallados:

### Estudiantes
- Cada estudiante tiene un identificador único (ID de estudiante), nombre completo, dirección, número de teléfono, correo electrónico, fecha de nacimiento, fecha de ingreso, y estado.
- Un estudiante puede estar matriculado en múltiples cursos, pero cada matrícula es única para cada estudiante y curso.
- Un estudiante puede tener múltiples becas, y una beca puede ser otorgada a múltiples estudiantes.

### Cursos
- Cada curso tiene un identificador único (ID de curso), nombre del curso, descripción, créditos, y el departamento que lo ofrece.
- Un curso puede tener múltiples estudiantes matriculados, y un estudiante puede estar matriculado en múltiples cursos.
- Un curso es impartido por un profesor, y un profesor puede impartir múltiples cursos.
- Un curso tiene un horario específico.

### Profesores
- Cada profesor tiene un identificador único (ID de profesor), nombre completo, dirección, número de teléfono, correo electrónico, y el departamento al que pertenece.
- Un profesor puede impartir múltiples cursos, y un curso es impartido por un profesor.

### Departamentos
- Cada departamento tiene un identificador único (ID de departamento), nombre del departamento, y la facultad a la que pertenece.
- Un departamento puede ofrecer múltiples cursos, y un curso es ofrecido por un departamento.
- Un departamento tiene múltiples profesores, y un profesor pertenece a un departamento.

### Horarios
- Cada horario tiene un identificador único (ID de horario), día de la semana, hora de inicio, hora de fin, y el aula en la que se imparte el curso.
- Un horario está asociado con un curso específico.

### Calificaciones
- Cada calificación tiene un identificador único (ID de calificación), nota, fecha de registro, y el estudiante y curso a los que pertenece.
- Un estudiante puede tener múltiples calificaciones, y una calificación está asociada con un único estudiante y curso.

### Matrículas
- Cada matrícula tiene un identificador único (ID de matrícula), fecha de matrícula, y el estudiante y curso correspondientes.
- Un estudiante puede tener múltiples matrículas, y una matrícula está asociada con un único estudiante y curso.

### Becas
- Cada beca tiene un identificador único (ID de beca), nombre de la beca, descripción, y monto.
- Una beca puede ser otorgada a múltiples estudiantes, y un estudiante puede recibir múltiples becas.

## Caso de Estudio 2: Biblioteca Pública "Leer es Vivir"

La Biblioteca Pública "Leer es Vivir" necesita una base de datos para gestionar sus operaciones diarias. La base de datos debe capturar información detallada sobre libros, miembros, préstamos, reservas, autores, categorías, empleados y eventos. A continuación se describen los requisitos detallados:

### Libros
- Cada libro tiene un identificador único (ID de libro), título, género, fecha de publicación, y el autor.
- Un libro puede tener múltiples reservas y préstamos, y una reserva o préstamo está asociado con un solo libro.

### Miembros
- Cada miembro tiene un identificador único (ID de miembro), nombre completo, dirección, número de teléfono, correo electrónico, fecha de registro, y estado.
- Un miembro puede hacer múltiples reservas y préstamos, y una reserva o préstamo está asociado con un único miembro.

### Préstamos
- Cada préstamo tiene un identificador único (ID de préstamo), fecha de préstamo, fecha de devolución, y el libro y miembro asociados.
- Un libro puede tener múltiples préstamos, y un miembro puede tener múltiples préstamos.

### Reservas
- Cada reserva tiene un identificador único (ID de reserva), fecha de reserva, y el libro y miembro asociados.
- Un libro puede tener múltiples reservas, y un miembro puede hacer múltiples reservas.

### Autores
- Cada autor tiene un identificador único (ID de autor), nombre completo, nacionalidad, y fecha de nacimiento.
- Un autor puede escribir múltiples libros, y un libro es escrito por un autor.

### Categorías
- Cada categoría tiene un identificador único (ID de categoría), nombre de la categoría, y descripción.
- Un libro puede pertenecer a múltiples categorías, y una categoría puede tener múltiples libros.

### Empleados
- Cada empleado tiene un identificador único (ID de empleado), nombre completo, dirección, número de teléfono, correo electrónico, y fecha de contratación.
- Un empleado puede gestionar múltiples eventos y prestar asistencia a los miembros.

### Eventos
- Cada evento tiene un identificador único (ID de evento), nombre del evento, descripción, fecha y hora, y el empleado responsable.
- Un evento puede estar asociado con múltiples miembros, y un miembro puede asistir a múltiples eventos.

# Tercer Escenario (Tercera Ronda)

## Caso de Estudio 1: Clínica de Salud "Salud Total"

La clínica de salud "Salud Total" necesita una base de datos para gestionar sus operaciones diarias. La base de datos debe capturar información detallada sobre pacientes, médicos, citas, tratamientos, medicamentos, historiales médicos, facturación y departamentos. A continuación se describen los requisitos detallados:

### Pacientes
- Cada paciente tiene un identificador único (ID de paciente), nombre completo, dirección, número de teléfono, correo electrónico, fecha de nacimiento, y estado.
- Un paciente puede tener múltiples citas, y cada cita es única para cada paciente y médico.
- Un paciente puede recibir múltiples tratamientos, y un tratamiento puede ser administrado a múltiples pacientes.

### Médicos
- Cada médico tiene un identificador único (ID de médico), nombre completo, especialidad, número de teléfono, correo electrónico, y el departamento al que pertenece.
- Un médico puede tener múltiples citas con diferentes pacientes.
- Un médico puede prescribir múltiples medicamentos, y un medicamento puede ser prescrito por múltiples médicos.

### Citas
- Cada cita tiene un identificador único (ID de cita), fecha y hora, motivo de la cita, y el paciente y médico correspondientes.
- Un paciente puede tener múltiples citas, y un médico puede atender múltiples citas.

### Tratamientos
- Cada tratamiento tiene un identificador único (ID de tratamiento), nombre del tratamiento, descripción, y el médico que lo administra.
- Un tratamiento puede ser administrado a múltiples pacientes, y un paciente puede recibir múltiples tratamientos.

### Medicamentos
- Cada medicamento tiene un identificador único (ID de medicamento), nombre del medicamento, descripción, dosis, y posibles efectos secundarios.
- Un medicamento puede ser prescrito a múltiples pacientes, y un paciente puede recibir múltiples medicamentos.

### Historiales Médicos
- Cada historial médico tiene un identificador único (ID de historial), resumen del historial, fecha de creación, y el paciente correspondiente.
- Un paciente tiene un único historial médico, que puede ser actualizado con el tiempo.

### Facturación
- Cada factura tiene un identificador único (ID de factura), fecha de emisión, monto, y el paciente correspondiente.
- Un paciente puede tener múltiples facturas, y cada factura es única para cada paciente.

### Departamentos
- Cada departamento tiene un identificador único (ID de departamento), nombre del departamento, y el médico encargado.
- Un departamento puede tener múltiples médicos, y un médico pertenece a un departamento.

## Caso de Estudio 2: Compañía de Software "TechSolutions"

La compañía de software "TechSolutions" necesita una base de datos para gestionar sus proyectos y empleados. La base de datos debe capturar información detallada sobre empleados, proyectos, tareas, departamentos, clientes, contratos, facturación y reuniones. A continuación se describen los requisitos detallados:

### Empleados
- Cada empleado tiene un identificador único (ID de empleado), nombre completo, dirección, número de teléfono, correo electrónico, fecha de contratación, y el departamento al que pertenece.
- Un empleado puede estar asignado a múltiples proyectos, y un proyecto puede tener múltiples empleados asignados.

### Proyectos
- Cada proyecto tiene un identificador único (ID de proyecto), nombre del proyecto, descripción, fecha de inicio, fecha de fin, y el cliente para el que se desarrolla.
- Un proyecto puede tener múltiples tareas, y una tarea está asociada con un solo proyecto.

### Tareas
- Cada tarea tiene un identificador único (ID de tarea), descripción de la tarea, fecha de inicio, fecha de fin, y el empleado asignado.
- Un empleado puede estar asignado a múltiples tareas, y una tarea puede estar asignada a múltiples empleados.

### Departamentos
- Cada departamento tiene un identificador único (ID de departamento), nombre del departamento, y el empleado encargado.
- Un departamento puede tener múltiples empleados, y un empleado pertenece a un departamento.

### Clientes
- Cada cliente tiene un identificador único (ID de cliente), nombre del cliente, dirección, número de teléfono, correo electrónico, y el contacto principal.
- Un cliente puede tener múltiples proyectos, y un proyecto está asociado con un solo cliente.

### Contratos
- Cada contrato tiene un identificador único (ID de contrato), descripción del contrato, fecha de inicio, fecha de fin, y el proyecto asociado.
- Un proyecto puede tener múltiples contratos, y un contrato está asociado con un solo proyecto.

### Facturación
- Cada factura tiene un identificador único (ID de factura), fecha de emisión, monto, y el cliente correspondiente.
- Un cliente puede tener múltiples facturas, y cada factura es única para cada cliente.

### Reuniones
- Cada reunión tiene un identificador único (ID de reunión), fecha y hora, motivo de la reunión, y los empleados participantes.
- Una reunión puede tener múltiples empleados, y un empleado puede asistir a múltiples reuniones.
