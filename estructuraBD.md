
## 📂 Colección: `usuarios`

### Descripción
Esta colección almacena información detallada sobre los usuarios, incluyendo su nombre, preferencias, sistemas asociados, y datos personales.


### Estructura de la colección

| Campo            | Tipo de dato      | Descripción                                                                 |
|------------------|-------------------|-----------------------------------------------------------------------------|
| `_id`            | ObjectId          | Identificador único del usuario.                                             |
| `username`       | String            | Nombre de usuario.                                                           |
| `estado`         | Boolean           | Estado del usuario (activo/inactivo).                                        |
| `datosPersonales`| Object            | Subdocumento con los datos personales del usuario.                           |
| `sistemas`       | Array de objetos  | Lista de sistemas asociados al usuario, cada uno con áreas laborales y preferencias. |
| `createdBy`      | String            | Indica quién creó el usuario.                                                |
| `deletedAt`      | Date/Null         | Fecha de eliminación (si el usuario ha sido eliminado).                      |
| `createdAt`      | Date              | Fecha de creación del usuario.                                               |
| `updatedAt`      | Date              | Fecha de última actualización del usuario.                                   |
| `__v`            | Integer           | Versión del documento (campo interno de Mongoose).                           |
| `tipousuario`    | String            | Tipo de usuario (ej. "interno").                                             |

### Subdocumento: `datosPersonales`

| Campo       | Tipo de dato | Descripción                                      |
|-------------|--------------|--------------------------------------------------|
| `nombre`    | String       | Nombre del usuario.                              |
| `apellido`  | String       | Apellido del usuario.                            |
| `_id`       | ObjectId     | Identificador único del subdocumento `datosPersonales`. |

### Subdocumento: `sistemas` (Array de objetos)

Cada objeto en el array `sistemas` tiene los siguientes campos:

| Campo           | Tipo de dato     | Descripción                                                        |
|-----------------|------------------|--------------------------------------------------------------------|
| `nombre`        | String           | Nombre del sistema asociado al usuario.                            |
| `preferencias`  | Boolean          | Preferencias del usuario en ese sistema.                           |
| `areaLaboral`   | Array de objetos | Lista de áreas laborales asociadas al sistema.                     |

#### Subdocumento: `areaLaboral` (Array dentro de `sistemas`)

| Campo            | Tipo de dato      | Descripción                                                        |
|------------------|-------------------|--------------------------------------------------------------------|
| `codigoOrganismo`| String            | Código del organismo asociado.                                     |
| `areaPrincipal`  | String            | Área principal dentro del sistema.                                 |
| `areaPropia`     | String            | Área propia del usuario dentro del sistema.                        |
| `ubicaciones`    | Array de enteros   | Lista de ubicaciones relacionadas con el área laboral.             |
| `_id`            | ObjectId          | Identificador único del área laboral.                              |



## 📂 Colección: `sistemas`
### Descripción
Esta colección almacena los sistemas disponibles en la plataforma.

### Estructura de la colección

| Campo         | Tipo de dato | Descripción                                      |
|--------------|-------------|--------------------------------------------------|
| `_id`        | ObjectId    | Identificador único del sistema.                 |
| `nombre`     | String      | Nombre del sistema.                              |
| `descripcion`| String      | Descripción breve del sistema.                   |
| `paginaInicio` | String    | Ruta de inicio dentro del sistema.               |
| `estado`     | Boolean     | Estado del sistema (activo/inactivo).            |
| `createdBy`  | String      | Usuario que creó el sistema.                     |
| `deletedAt`  | Date/Null   | Fecha de eliminación (si el sistema fue eliminado). |
| `createdAt`  | Date        | Fecha de creación del sistema.                   |
| `updatedAt`  | Date        | Fecha de última actualización del sistema.       |
| `__v`        | Integer     | Versión del documento (campo interno de Mongoose). |


## 📂 Colección: `usuarios_preferencias`

### Descripción
Esta colección almacena las preferencias personalizadas de los usuarios para los sistemas y áreas laborales asociadas. Incluye configuraciones específicas de perfil y filtros de búsqueda para los usuarios.

### Estructura de la colección

| Campo           | Tipo de dato  | Descripción                                                      |
|-----------------|---------------|------------------------------------------------------------------|
| `_id`           | ObjectId      | Identificador único de la preferencia.                           |
| `username`      | String        | Nombre de usuario al que pertenecen las preferencias.            |
| `areaLaboral`   | String        | Código del área laboral asociada (referencia a `areaLaboral`).   |
| `perfil`        | Object        | Configuración personalizada del perfil del usuario.              |
| `configPerfil`  | Object        | Configuración de perfil asociada con las operaciones del usuario.|
| `configSistema` | ObjectId      | Identificador del sistema asociado (referencia a `sistemas`).    |
| `createdBy`     | String        | Usuario que creó la preferencia.                                 |
| `deletedAt`     | Date/Null     | Fecha de eliminación (si la preferencia fue eliminada).          |
| `createdAt`     | Date          | Fecha de creación de la preferencia.                             |
| `updatedAt`     | Date          | Fecha de última actualización de la preferencia.                 |
| `sistema`       | String        | Nombre del sistema al que pertenecen las preferencias.           |
| `updatedBy`     | String        | Usuario que realizó la última actualización.                     |
| `__v`           | Integer       | Versión del documento (campo interno de Mongoose).               |

### Subdocumento: `perfil`

| Campo           | Tipo de dato  | Descripción                                                      |
|-----------------|---------------|------------------------------------------------------------------|
| `filtros`       | Object        | Filtros de búsqueda y criterios aplicados al perfil del usuario. |

#### Subdocumento: `filtros`

| Campo            | Tipo de dato     | Descripción                                                         |
|------------------|------------------|---------------------------------------------------------------------|
| `buscar`         | Array de objetos | Filtros de búsqueda personalizados del usuario.                    |

##### Subdocumento: `buscar` (Array dentro de `filtros`)

| Campo             | Tipo de dato  | Descripción                                                             |
|-------------------|---------------|-------------------------------------------------------------------------|
| `id`              | Integer       | Identificador del filtro de búsqueda.                                  |
| `nombre`          | String        | Nombre del filtro de búsqueda.                                         |
| `campos`          | Object        | Campos asociados con el filtro de búsqueda.                            |

###### Subdocumento: `campos`

| Campo             | Tipo de dato  | Descripción                                                             |
|-------------------|---------------|-------------------------------------------------------------------------|
| `filtrosComunes`  | Object        | Filtros comunes aplicados al perfil.                                   |
| `filtrosActuacion`| Object        | Filtros específicos para la actuación.                                  |
| `tipoBusqueda`    | String        | Tipo de búsqueda realizada (ACTUACION, EXPEDIENTE, etc.).               |



## 📂 Colección: `config_sistemas`

### Descripción
Esta colección almacena configuraciones de los sistemas, incluyendo acciones permitidas, filtros de búsqueda, configuraciones del dashboard, y otros parámetros relacionados con el funcionamiento de las funcionalidades del sistema.

### Estructura de la colección

| Campo                | Tipo de dato  | Descripción                                                      |
|----------------------|---------------|------------------------------------------------------------------|
| `_id`                | ObjectId      | Identificador único de la configuración del sistema.             |
| `nombreConfigSistema`| String        | Nombre de la configuración del sistema.                          |
| `ingresadas`         | Object        | Configuración de acciones ingresadas en el sistema.              |
| `buscar`             | Object        | Configuración de búsqueda y acciones asociadas.                  |
| `solicitudesME`      | Object        | Configuración relacionada con las solicitudes en Mesa de Entrada.|
| `listar`             | Object        | Configuración de acciones para listar elementos.                 |
| `verExpediente`      | Object        | Configuración de acciones relacionadas con el expediente.        |
| `configuracion`      | Object        | Configuración de modelos y tipos de registros en el sistema.     |
| `editorActuacion`    | Object        | Configuración de acciones del editor de actuación.               |
| `dashboard`          | Object        | Configuración de acciones en el dashboard del sistema.           |
| `buscarFeria`        | Object        | Configuración de acciones relacionadas con la búsqueda en Feria.|
| `idSistema`          | ObjectId      | Identificador del sistema asociado.                              |
| `nombreAnterior`     | String        | Nombre anterior de la configuración del sistema.                 |
| `sistema`            | ObjectId      | Identificador del sistema relacionado.                           |
| `estado`             | Boolean       | Estado de la configuración del sistema (activo o no).            |

### Subdocumento: `ingresadas`

| Campo                | Tipo de dato  | Descripción                                                      |
|----------------------|---------------|------------------------------------------------------------------|
| `acciones`           | Object        | Acciones disponibles para ingresar datos.                        |

#### Subdocumento: `acciones`

| Campo                | Tipo de dato  | Descripción                                                      |
|----------------------|---------------|------------------------------------------------------------------|
| `cambiarUbicacion`   | Boolean       | Indica si es posible cambiar la ubicación.                       |

### Subdocumento: `buscar`

| Campo                | Tipo de dato  | Descripción                                                      |
|----------------------|---------------|------------------------------------------------------------------|
| `expediente`         | Object        | Filtros y acciones relacionadas con la búsqueda de expedientes.  |
| `actuacion`          | Object        | Filtros y acciones relacionadas con la búsqueda de actuaciones.  |
| `mesa_entrada`       | Object        | Acciones disponibles en la Mesa de Entrada.                      |

#### Subdocumento: `expediente`, `actuacion` y `mesa_entrada`

| Campo                | Tipo de dato  | Descripción                                                      |
|----------------------|---------------|------------------------------------------------------------------|
| `filtros`            | Boolean       | Indica si los filtros están habilitados.                         |
| `acciones`           | Object        | Acciones permitidas relacionadas con los expedientes, actuaciones o mesas de entrada. |



##### a excepción de los campos: _id, nombreConfigSistema, idSistema,createdAt,createdBy,updatedBy,updatedAt,deletedBy,deletedAt
##### el resto de la estructura es dinámica, por lo que puede haber nuevos campos, con diferentes nombres

## 📂 Colección: `organismos`

### Descripción
Esta colección almacena información sobre los organismos, incluyendo el nombre del organismo, su código, estado, domicilios, y las áreas principales asociadas, cada una con sus respectivas subáreas.

### Estructura de la colección

| Campo              | Tipo de dato  | Descripción                                                      |
|--------------------|---------------|------------------------------------------------------------------|
| `_id`              | ObjectId      | Identificador único del organismo.                               |
| `organismo`        | String        | Nombre del organismo.                                            |
| `codigo`           | String        | Código del organismo.                                            |
| `estado`           | Boolean       | Estado del organismo (activo o no).                              |
| `domicilio`        | Object        | Dirección del organismo.                                         |
| `areasPrincipales` | Array         | Áreas principales asociadas al organismo.                        |
| `createdAt`        | Date          | Fecha de creación del organismo.                                 |
| `createdBy`        | String        | Usuario que creó el organismo.                                   |
| `updatedAt`        | Date          | Fecha de última actualización del organismo.                     |
| `updatedBy`        | String        | Usuario que realizó la última actualización del organismo.       |
| `_class`           | String        | Clase del modelo que representa al organismo.                    |

### Subdocumento: `domicilio`

| Campo             | Tipo de dato  | Descripción                                                      |
|-------------------|---------------|------------------------------------------------------------------|
| `localidad`       | String        | Localidad del domicilio.                                         |
| `calle`           | String        | Calle del domicilio.                                             |
| `nro`             | String        | Número del domicilio.                                            |
| `dpto`            | String        | Departamento del domicilio (opcional).                           |

### Subdocumento: `areasPrincipales`

| Campo             | Tipo de dato  | Descripción                                                      |
|-------------------|---------------|------------------------------------------------------------------|
| `_id`             | ObjectId      | Identificador único del área principal.                          |
| `areaPrincipal`   | String        | Nombre del área principal.                                       |
| `domicilio`       | Object        | Dirección del área principal.                                    |
| `subArea`         | Array         | Subáreas asociadas al área principal.                             |
| `updatedAt`       | Date          | Fecha de última actualización del área principal.                |
| `updatedBy`       | String        | Usuario que realizó la última actualización del área principal.  |

#### Subdocumento: `subArea`

| Campo             | Tipo de dato  | Descripción                                                      |
|-------------------|---------------|------------------------------------------------------------------|
| `_id`             | ObjectId      | Identificador único de la subárea.                               |
| `area`            | String        | Nombre de la subárea.                                            |
| `domicilio`       | Object        | Dirección de la subárea.                                         |
| `updatedAt`       | Date          | Fecha de última actualización de la subárea.                     |
| `updatedBy`       | String        | Usuario que realizó la última actualización de la subárea.       |

