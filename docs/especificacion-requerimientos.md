# Especificación de Requerimientos

## 1. Descripción del sistema

Sistema de manejo de tutorías

## 2. Integrantes

- Nombre: Juan Felipe Uribe
- Nombre: Santiago Mesias
- Nombre: Juan Esteban Victoria
- Nombre: Samuel Ocampo Coral
- Nombre:

## 3. Requerimientos Funcionales

### RF-01 - Registro de Tutoría Académica

#### Resumen

Permite a un profesor programar y registrar una nueva tutoría académica en el sistema centralizado, especificando los datos requeridos para que posteriormente los estudiantes puedan consultarla e inscribirse.

#### Entradas

| Entrada | Tipo de dato | Descripción |
|---|---|---|
| codigoProfesor | String | Identificador único del profesor que ofrece la tutoría. |
| tema | String | Asignatura, tema o contenido específico que se tratará en la tutoría. |
| fecha | Date | Fecha programada para la realización de la tutoría (YYYY-MM-DD). |
| horaInicio | Time | Hora de inicio de la sesión de tutoría (HH:MM). |
| cantidadMaximaEstudiantes | Integer | Número máximo de estudiantes que pueden ser atendidos en la tutoría. |

#### Reglas o condiciones

- La fecha programada no puede ser anterior a la fecha actual del sistema.
- La cantidad máxima de participantes debe ser un número entero dentro del rango de 1 a 10 estudiantes.
- Todos los campos de entrada son obligatorios.

#### Salidas

| Salida | Tipo de dato | Descripción |
|---|---|---|
| idTutoria | String | Identificador único asignado automáticamente por el sistema a la tutoría creada. |
| mensajeConfirmacion | String | Notificación enviada al profesor confirmando la creación exitosa de la tutoría. |

#### Resultado esperado
La tutoría queda registrada correctamente en el sistema con un identificador único asignado, sus cupos iniciales disponibles son iguales a la cantidad máxima configurada, y se encuentra disponible para consulta por parte de los estudiantes.

# RF-02 - Consultar tutorías disponibles

#### Resumen

Permitir a los estudiantes consultar las tutorías disponibles para una fecha específica, con la posibilidad de filtrar opcionalmente los resultados por asignatura o tema de interés.

#### Entradas

| Entrada         | Tipo de dato | Descripción                                                                                 |
| --------------- | ------------ | ------------------------------------------------------------------------------------------- |
| fechaConsulta   | LocalDate    | Fecha para la cual el estudiante desea consultar las tutorías disponibles.                  |
| asignaturaOTema | String       | Asignatura o tema de interés utilizado para filtrar las tutorías. Esta entrada es opcional. |

#### Reglas o condiciones

* La `fechaConsulta` debe corresponder a la fecha que el estudiante desea consultar.
* La asignatura o tema de interés puede ser omitida para consultar todas las tutorías disponibles en la fecha indicada.
* Si se proporciona una asignatura o tema, solamente se deben mostrar las tutorías que correspondan con dicho criterio.
* La consulta debe mostrar únicamente las tutorías que se encuentren disponibles.
* Si no existen tutorías que coincidan con los criterios de búsqueda, el sistema debe informar al estudiante que no se encontraron tutorías.

#### Salidas

| Salida              | Tipo de dato | Descripción                                                                                     |
| ------------------- | ------------ | ----------------------------------------------------------------------------------------------- |
| identificador       | String       | Identificador único de la tutoría encontrada.                                                   |
| tema                | String       | Tema de la tutoría.                                                                             |
| profesorResponsable | String       | Identificación o código del profesor responsable de la tutoría.                                 |
| fecha               | LocalDate    | Fecha en la que se realizará la tutoría.                                                        |
| horaInicio          | LocalTime    | Hora de inicio de la tutoría.                                                                   |
| cuposDisponibles    | Integer      | Cantidad de cupos que todavía están disponibles para la tutoría.                                |
| mensaje             | String       | Mensaje informado al estudiante cuando no se encuentran tutorías que coincidan con la búsqueda. |

#### Resultado esperado

El sistema muestra al estudiante las tutorías disponibles que coinciden con la fecha indicada y, si se proporcionó, con la asignatura o tema de interés. Para cada tutoría encontrada se presenta su identificador, tema, profesor responsable, fecha, hora de inicio y cantidad de cupos disponibles. Si no existen tutorías que coincidan con los criterios de búsqueda, el sistema informa al estudiante que no se encontraron tutorías.



### RF-03 - Inscripción a Tutoría Académica

#### Resumen

Permite a un estudiante autenticado consultar el detalle de una tutoría disponible y registrar su inscripción en ella, siempre y cuando existan cupos suficientes y no presente cruce de horarios con otras tutorías previamente inscritas.

#### Entradas

| Entrada | Tipo de dato | Descripción |
|---|---|---|
| codigoEstudiante | String | Identificador único del estudiante que solicita la inscripción. |
| idTutoria | String | Identificador único de la tutoría académica a la cual desea inscribirse. |

#### Reglas o condiciones

- El estudiante no puede inscribirse a una tutoría que ya no tenga cupos disponibles (cuposDisponibles > 0).
- Un estudiante no puede inscribirse más de una vez a la misma tutoría.
- El estudiante no debe tener inscrita otra tutoría en la misma fecha y rango de hora.
- Todos los campos de entrada son obligatorios.

#### Salidas

| Salida | Tipo de dato | Descripción |
|---|---|---|
| idInscripcion | String | Identificador único generado por el sistema para la inscripción realizada. |
| estadoInscripcion | String | Estado del registro (ej. "CONFIRMADA"). |
| mensajeConfirmacion | String | Mensaje de notificación informando al estudiante la confirmación del cupo. |

#### Resultado esperado

La inscripción queda registrada exitosamente en el sistema, la cantidad de cupos disponibles de la tutoría se reduce en 1 y la tutoría aparece en el historial o agenda de tutorías del estudiante.


### RF-04 - Cancelación de Inscripcion a una Tutoría.

#### Resumen
Permitir que un estudiante cancele una inscripcion previamente realizada a una tutoria especifica. El sistema validará la existencia ed la incripción y el horario de inicioo de la tutoria; de cumplir los criterios, procederá a revocar el registro de incripción, liberar un cupo en la tutoria y confirmar el éxito de la operación. En caso contrario, notificará la causa de rechazo.

#### Entradas

| Entrada | Tipo de dato | Descripción |
|Codigo estudiantil|String|Id unico de cada estudiante|
|Identificador de tutoria|String| Codigo unico generado previamente por el sistema|

#### Reglas o condiciones
-Inscripción previa es existente
-La tutoria no debe haber empezado
-Si se ejecuta correctamente, debe dar 1 cupo el cual el estudiante ya no ocupa
-Manejar excepciones

#### Salidas

| Salida | Tipo de dato | Descripción |
|Mensaje de estado|String|Mensaje que indica si la cancelación se realizo correctamente o el motivo por el cual no fue posible procesarla|
|Cupos actualizados|Int|Nuevo conteo de cupos disponibles|

#### Resultado esperado
Caso exitoso:
- El sistema elimina la relacion de inscripcion entre el estudiante y la tutoria
- El contador de cupos disponibles se actualiza +1
Caso fallido:
- No se realiza ningun cambio
- Se muestra la razon por la que no se pudo cancelar la inscripcion



## 4. Gestión de Versiones

### Ramas utilizadas

feat/names-description, feature/rf01-registro-tutoria, feature/rf02, feature/rf03-inscripcion-tutoria, feat/gestion-versiones

### Proceso de integración

Primero se hizo la base de todo en main, despues se hizo un pull desde develop, y se trabajó en develop desde ramas aparte (feature), las cuales fueron unidas a develop cuando fueron terminadas.

### Conflictos encontrados

Al trabajar en ramas diferentes al mismo tiempo, no se actualiza automaticamente, entonces toca hacer el pull de develop antes de hacer cualquier merge, también se hizo el commit de el requerimiento 4 directamente a main de manera accidental.
