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

### Proceso de integración

### Conflictos encontrados
