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

### RF-01 - [Nombre del requerimiento]

#### Resumen

#### Entradas

| Entrada | Tipo de dato | Descripción |
|---|---|---|

#### Reglas o condiciones

#### Salidas

| Salida | Tipo de dato | Descripción |
|---|---|---|

#### Resultado esperado


### RF-02 - [Nombre del requerimiento]

#### Resumen

#### Entradas

| Entrada | Tipo de dato | Descripción |
|---|---|---|

#### Reglas o condiciones

#### Salidas

| Salida | Tipo de dato | Descripción |
|---|---|---|

#### Resultado esperado


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
