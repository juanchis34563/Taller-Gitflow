# Especificación de Requerimientos

## 1. Descripción del sistema

## 2. Integrantes

- Nombre:
- Nombre:
- Nombre:
- Nombre:
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


### RF-04 - [Nombre del requerimiento]

#### Resumen

#### Entradas

| Entrada | Tipo de dato | Descripción |
|---|---|---|

#### Reglas o condiciones

#### Salidas

| Salida | Tipo de dato | Descripción |
|---|---|---|

#### Resultado esperado


## 4. Gestión de Versiones

### Ramas utilizadas

### Proceso de integración

### Conflictos encontrados
