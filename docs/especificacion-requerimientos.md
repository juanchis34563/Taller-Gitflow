# Especificación de Requerimientos

## 1. Descripción del sistema

Sistema de manejo de tutorías.

## 2. Integrantes

* Nombre: Juan Felipe Uribe
* Nombre: Santiago Mesias
* Nombre: Juan Esteban Victoria
* Nombre: Samuel Ocampo Coral
* Nombre:

## 3. Requerimientos Funcionales

### RF-01 - Registrar tutoría

#### Resumen

Permite registrar una nueva tutoría académica en el sistema, almacenando la información necesaria para que posteriormente pueda ser consultada por los estudiantes.

#### Entradas

| Entrada    | Tipo de dato | Descripción                                     |
| ---------- | ------------ | ----------------------------------------------- |
| idTutoria  | String       | Identificador único de la tutoría.              |
| nombre     | String       | Nombre o tema de la tutoría.                    |
| fecha      | LocalDate    | Fecha en la que se realizará la tutoría.        |
| horaInicio | LocalTime    | Hora de inicio de la tutoría.                   |
| horaFin    | LocalTime    | Hora de finalización de la tutoría.             |
| cupos      | int          | Cantidad de estudiantes que pueden inscribirse. |

#### Reglas o condiciones

* Todos los campos obligatorios deben estar diligenciados.
* El identificador de la tutoría debe ser único.
* La fecha y hora de la tutoría deben ser válidas.
* La cantidad de cupos debe ser mayor que cero.
* La hora de inicio debe ser anterior a la hora de finalización.

#### Salidas

| Salida        | Tipo de dato | Descripción                                                |
| ------------- | ------------ | ---------------------------------------------------------- |
| idTutoria     | String       | Identificador de la tutoría registrada.                    |
| mensajeEstado | String       | Mensaje que indica si el registro fue exitoso o rechazado. |

#### Resultado esperado

La tutoría queda registrada exitosamente en el sistema y puede ser consultada posteriormente por los estudiantes.

### RF-02 - Consultar tutorías disponibles

#### Resumen

Permite a un estudiante consultar las tutorías académicas que se encuentran disponibles para inscripción, mostrando la información necesaria para seleccionar una tutoría.

#### Entradas

| Entrada | Tipo de dato | Descripción                                                     |
| ------- | ------------ | --------------------------------------------------------------- |
| fecha   | LocalDate    | Fecha opcional utilizada para filtrar las tutorías disponibles. |
| tema    | String       | Tema opcional utilizado para filtrar las tutorías.              |

#### Reglas o condiciones

* Solo deben mostrarse tutorías registradas en el sistema.
* Las tutorías deben tener al menos un cupo disponible.
* Las tutorías que ya hayan finalizado no deben aparecer como disponibles.
* Los filtros de fecha y tema son opcionales.
* Si no existen tutorías que cumplan las condiciones, se debe informar al estudiante.

#### Salidas

| Salida        | Tipo de dato  | Descripción                                                      |
| ------------- | ------------- | ---------------------------------------------------------------- |
| listaTutorias | List<Tutoria> | Lista de tutorías que cumplen las condiciones de disponibilidad. |
| mensajeEstado | String        | Mensaje que informa el resultado de la consulta.                 |

#### Resultado esperado

El sistema muestra al estudiante una lista de las tutorías disponibles para inscripción junto con su información relevante, como fecha, horario, tema y cantidad de cupos disponibles.

### RF-03 - Inscripción a Tutoría Académica

#### Resumen

Permite a un estudiante autenticado consultar el detalle de una tutoría disponible y registrar su inscripción en ella, siempre y cuando existan cupos suficientes y no presente cruce de horarios con otras tutorías previamente inscritas.

#### Entradas

| Entrada          | Tipo de dato | Descripción                                                              |
| ---------------- | ------------ | ------------------------------------------------------------------------ |
| codigoEstudiante | String       | Identificador único del estudiante que solicita la inscripción.          |
| idTutoria        | String       | Identificador único de la tutoría académica a la cual desea inscribirse. |

#### Reglas o condiciones

* El estudiante no puede inscribirse a una tutoría que ya no tenga cupos disponibles (`cuposDisponibles > 0`).
* Un estudiante no puede inscribirse más de una vez a la misma tutoría.
* El estudiante no debe tener inscrita otra tutoría en la misma fecha y rango de hora.
* Todos los campos de entrada son obligatorios.

#### Salidas

| Salida              | Tipo de dato | Descripción                                                                |
| ------------------- | ------------ | -------------------------------------------------------------------------- |
| idInscripcion       | String       | Identificador único generado por el sistema para la inscripción realizada. |
| estadoInscripcion   | String       | Estado del registro, por ejemplo, "CONFIRMADA".                            |
| mensajeConfirmacion | String       | Mensaje de notificación informando al estudiante la confirmación del cupo. |

#### Resultado esperado

La inscripción queda registrada exitosamente en el sistema, la cantidad de cupos disponibles de la tutoría se reduce en 1 y la tutoría aparece en el historial o agenda de tutorías del estudiante.

### RF-04 - Cancelación de Inscripción a una Tutoría

#### Resumen

Permite que un estudiante cancele una inscripción previamente realizada a una tutoría específica. El sistema validará la existencia de la inscripción y el horario de inicio de la tutoría. Si se cumplen los criterios, procederá a cancelar el registro de inscripción, liberar un cupo en la tutoría y confirmar el éxito de la operación. En caso contrario, notificará la causa del rechazo.

#### Entradas

| Entrada          | Tipo de dato | Descripción                                                              |
| ---------------- | ------------ | ------------------------------------------------------------------------ |
| codigoEstudiante | String       | Identificador único del estudiante.                                      |
| idTutoria        | String       | Identificador único de la tutoría a la cual está inscrito el estudiante. |

#### Reglas o condiciones

* Debe existir una inscripción previa del estudiante en la tutoría.
* La tutoría no debe haber comenzado.
* Al cancelar correctamente, se debe liberar un cupo en la tutoría.
* Si la inscripción no existe, la operación debe ser rechazada.
* Se deben manejar las excepciones que puedan ocurrir durante la cancelación.

#### Salidas

| Salida            | Tipo de dato | Descripción                                                                                                      |
| ----------------- | ------------ | ---------------------------------------------------------------------------------------------------------------- |
| mensajeEstado     | String       | Mensaje que indica si la cancelación se realizó correctamente o el motivo por el cual no fue posible procesarla. |
| cuposActualizados | int          | Nuevo conteo de cupos disponibles después de la cancelación.                                                     |

#### Resultado esperado

**Caso exitoso:**

* El sistema elimina la relación de inscripción entre el estudiante y la tutoría.
* El contador de cupos disponibles se actualiza aumentando en 1.
* El sistema informa al estudiante que la cancelación fue exitosa.

**Caso fallido:**

* No se realiza ningún cambio en la inscripción.
* Se muestra la razón por la que no se pudo cancelar.

## 4. Gestión de Versiones

### Ramas utilizadas

`feat/names-description`, `feature/rf01-registro-tutoria`, `feature/rf02`, `feature/rf03-inscripcion-tutoria`, `feat/gestion-versiones`.

### Proceso de integración

Primero se creó la base del proyecto en `main`. Posteriormente, se realizó un `pull` desde `develop` y se trabajó en `develop` mediante ramas independientes (`feature`). Una vez terminados los requerimientos correspondientes, las ramas fueron integradas a `develop` mediante Pull Requests.

### Conflictos encontrados

Al trabajar en ramas diferentes de manera simultánea, los cambios realizados en una rama no se actualizan automáticamente en las demás. Por esta razón, es necesario actualizar la rama con los cambios de `develop` antes de realizar una integración, con el fin de reducir y resolver posibles conflictos.

También se realizó accidentalmente el commit correspondiente al requerimiento 4 directamente sobre `main`. Esto generó una situación de integración que debió ser revisada para mantener la organización establecida mediante GitFlow.
