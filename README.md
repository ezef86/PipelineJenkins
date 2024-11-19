# **Dos Pipelines Declarativos de Jenkins para la Gestión de Usuarios en Linux**

## **Propósito**

Estos pipelines declarativos de Jenkins automatizan la creación y eliminación de usuarios del sistema Linux. Permite agregar usuarios con parámetros personalizados como el inicio de sesión, nombre completo y departamento, además de eliminar usuarios según su UID. También genera una contraseña temporal para el nuevo usuario y fuerza a cambiarla en el próximo inicio de sesión.

### **Requisitos Previos**

- Jenkins debe estar instalado y configurado.
- El usuario de Jenkins debe tener privilegios de `sudo` sin contraseña.

### **Descripción General del Pipeline de Nuevos Usuarios**

### **Parámetros de Entrada**

- **LOGIN**: Nombre de inicio de sesión para el nuevo usuario (por ejemplo, `jperez`).
- **NOMBRE**: Nombre del usuario (por ejemplo, `Juan`).
- **APELLIDO**: Apellido del usuario (por ejemplo, `Perez`).
- **DEPARTAMENTO**: Departamento (opciones: `Contabilidad`, `Tecnología`, `Finanzas`).
- **ADD_TO_SUDO**: Booleano para asignar privilegios de sudo.

### **Descripción General del Pipeline de Eliminar Usuarios**

### **Parámetros de Entrada**

- **USER_UID**: Número de identificador del usuario a remover.

### **Manejo de Errores**

- **Permiso denegado**: Verifique que el usuario de Jenkins tenga los privilegios correctos de `sudo`.
- **El usuario ya existe**: Asegúrese de que el parámetro `LOGIN` sea único.

### **Referencias**

- [Documentación sobre Sintaxis de Pipeline Declarativo de Jenkins](https://www.jenkins.io/doc/book/pipeline/syntax/)
