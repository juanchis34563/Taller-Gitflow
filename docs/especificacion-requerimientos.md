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



### RF-03 - [Nombre del requerimiento]

#### Resumen

#### Entradas

| Entrada | Tipo de dato | Descripción |
|---|---|---|

#### Reglas o condiciones

#### Salidas

| Salida | Tipo de dato | Descripción |
|---|---|---|

#### Resultado esperado


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
