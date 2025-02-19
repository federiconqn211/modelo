# Requisitos



### 2.1 Requisitos funcionales  
- **Registro de usuario:** Los usuarios deben poder registrarse con datos como nombre, correo electrónico, contraseña y rol asignado.  
- **Autenticación de usuario:** El sistema debe permitir el inicio de sesión mediante  username y contraseña, utilizando Keycloak para la autenticación y gestión de identidad.
- **Gestión de roles:** se asignaran roles a los usuarios finales de los diferentes sistemas.  
- **Gestión de permisos:** Los permisos se asignan a roles, no a usuarios directamente. Los usuarios obtienen permisos según su rol y, de esta manera la navegacion por los diferentes sistemas estará condicionada por su rol, segun su área laboral.  
- **Interfaz web:** Los usuarios administradores podrán gestionar usuarios, roles y permisos desde una interfaz web.  
- **Interacción con otros sistemas:** Los permisos otorgados a los usuarios controlan el acceso a otros sistemas conectados.  

- **Usabilidad:** La interfaz debe ser fácil de usar, aprovechando los componentes de Ant Design para una experiencia fluida.  

### 2.3 Requisitos del sistema  
- **Servidor:** Node.js con Express.js.  
- **Base de datos:** MongoDB (requiere instalación de MongoDB o conexión a un servicio de MongoDB en la nube como Atlas).  
- **Frontend:** React con Ant Design. 
