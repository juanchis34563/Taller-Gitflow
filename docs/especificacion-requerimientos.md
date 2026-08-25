# Especificación de Requerimientos

## 1. Descripción del sistema

## 2. Integrantes

- Nombre:
- Nombre:
- Nombre:
- Nombre:
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
