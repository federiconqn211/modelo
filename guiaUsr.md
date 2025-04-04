# Guía del Usuario
### Login
Para ingresar al sistema, se deberán validar credenciales a través de keyCloack

<img src="./docs/assets/img/img guia usr/login.png" width="1000" >


### Usuarios 
 
>En el menú usuarios, se dan de alta a los mismos en una BD propia del sistema, pero validando su existencia en el sistema **LIMAY**, para el caso de usuarios internos.Para el caso de usuarios externos, se completará la informacion requerida, pero validando existencia del mismo, en el paso final de la carga



<img src="./docs/assets/img/img guia usr/usuarios 1.png" width="1800" >

### Nuevo Usuario
>La carga de un nuevo usuario, es mediante un **wizard** que tendrá una cantidad de pasos, donde se harán diferentes validaciones
### Paso 1 - Buscar Usuario
<img src="./docs/assets/img/img guia usr/wizard usr 1.png" width="1000" >

 El usuario buscado, está em uma Base de Datos, donde se validará si es **TSJ** o **SINE**, para determinarse de manera automática si será **INTERNO** o **EXTERNO**. Al hacer click en el usuario buscado, si éste ya se encuantra cargado, nos llevará a la pantalla de busqueda con el usuario encontrado, y así poder visualizar/ editar su información.


### Paso 2 - Cargar la Información Faltante y Validar con ReNaPer
> Si el usuario buscado **No** está cargado, se habilita el formulario de carga, con algunos datos precargados(de la consulta del paso 1), como ser **username**, **E-mail** y Tipo: **Interno/ Externo**.
los datos de **Apellido** y **Nombre** están completados, **SIN VALIDAR**, por lo que no se consideran suficientes, hasta tanto No sean corroborados con la operación validar, Ingresando Nro. Documento y Género.
>
<img src="./docs/assets/img/img guia usr/wizard usr 2.png" width="1800" >


### Paso 3 - Confirmación
>
 En este paso, tenemos el botón **Finalizar**, que nos pedirá confirmación previa, y en caso de aceptar, se efectuará una validacion en **usuariosV2** verificando existencia de **Nro. Documento**,**Username**, e **email**
>
<img src="./docs/assets/img/img guia usr/wizard usr 4.png" width="1800" >

### Asignación de Roles
>Cada Usuario tendra acceso a los distintos sistemas con un determinado Rol - Perfíl, según las restricciones definidas por las mismas
>

>Un Rol es una restriccion que se define para cada usuario teniendo en cuenta: **Sistema**,**Configuración** y **Preferencia(perfil)**
>
>Cada  Rol se asigna para un determinado **Organismo**,**Area principal** y **Area propia**
>

>Dentro de Cada Rol, existe el **perfil**, que se compone de una serie de funciones que el usuario puede realizar
>


<img src="./docs/assets/img/img guia usr/roles 1.png" width="1800" >

>En la opción de Menú **Editar** se tiene la pestaña **Sistemas y Roles**
>

<img src="./docs/assets/img/img guia usr/roles 2.png" width="1800" >

>Una forma rápida de asignar un Rol, incluido el Perfíl correspondiente, es **Clonándolo** de un usuario existente.
Es muy común que se solicite dar de alta a un usuario **X** y que tenga los permisos para el/los sistema(s) del usuario **Y**
>

### Clonar un Rol
>Para llevar adelante una clonación de Rol, se requieren 3 parametros: **username** ,**sistema** y **organismo**.
>
>Luego, con el botón **Buscar** se valida el Rol, obteniendo una vista previa de lo que se le otorgará al usuario.
>
<img src="./docs/assets/img/img guia usr/roles 3.png" width="1800" >

>**TENER EN CUENTA QUE SE CLONA TODA LA ESTRUCTURA DE PERMISOS. EN CASO DE TENER QUE HACER UN AJUSTE, SE DEBERA LUEGO EDITAR**
>
>**CUANDO SE LE ASIGNA UN ROL AL USUARIO, SE ENVÍA AUTOMÁTICAMENTE UN MAIL AL MISMO, NOTIFICANDOLE DE DICHO EVENTO Y EN PANTALLA SE VISUALIZA UN MENSAJE EMERGENTE:**
>
<img src="./docs/assets/img/img guia usr/notificacion 1.png" width="400" >

>**ADEMÁS LAS NOTIFICACIONES PUEDEN CONSULTARSE EN LA PESTAÑA NOTIFICACIONES E-MAIL**
>

### Sistemas
>El menú sistemas se divide en 2 submenúes, **Administración** y **Roles**

#### Administración
 >Se puede ver el listado de los sistemas a administrar, con un filtro de búsqueda simple y un boton de acciones para poder editar y habilitar/deshabilitar un sistema.

<img src="./docs/assets/img/img guia usr/sistemas 1.png" width="1800" >

Para editar un sistema, mediante el boton de **Acciones > Editar** se despliega un panel lateral con la información separada en 2 pestañas: **Datos Sistema** y **Configuraciones Asociadas**

##### Datos Sistema

se puede editar la información básica
<img src="./docs/assets/img/img guia usr/sistemas editar 1.png" width="1800" >


##### Roles Asociados

se verá en el apartado **Roles**
<img src="./docs/assets/img/img guia usr/sistemas editar 2.png" width="1800" >

>**CUANDO SE HABILITA O DESHABILITA UN SISTEMA, LOS USUARIOS DEL MISMO SON NOTIFICADOS POR MAIL INFORMÁNDOLES ACERCA DE DICHO EVENTO**
>
#### Roles
>Un sistema puede contar con uno o más Roles, en donde se especifica el mapa de navegacion por el mismo, con sus permisos respectivos. estos Roles asociados, se vinculan luego a un usuario, para un determinado Organismo y áreas laborales


<img src="./docs/assets/img/img guia usr/configSistema 1.png" width="1800" >


> Se puede cargar un nuevo rol desde cero, o clonar uno existente y efectuarle los ajustes correspondientes, a los fines de ahorrar tiempo de carga

<img src="./docs/assets/img/img guia usr/configSistema 2.png" width="1800" >

el Rol de un sistema cuenta  con una estructura jerarquica muy flexible, en forma de árbol que se puede modificar mediante **drag & drop**, como asi tambien agregar nuevos nodos, raíz(Páginas navegables)  o bien nodos hoja(Elementos de la pantalla) con sus **check**, los cuales habilitan/ deshabilitan al perfil que tenga asignada la configuraión

### Organismos 

>La información de los organismos visualizados, proviene de una conexión al WS  del sistema **LIMAY**, por lo que solamente accedemos a ella en modo **Solo Lectura**
>
<img src="./docs/assets/img/img guia usr/organismos 1.png" width="1800" >

### Notificaciones 
>Todas las notificaciones enviadas por los distintos sistemas, se pueden consultar.

<img src="./docs/assets/img/img guia usr/notificaciones 1.png" width="1800" >