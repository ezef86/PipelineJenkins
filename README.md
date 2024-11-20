# **Pipeline Declarativo de Jenkins para la Gestión de Usuarios en Linux**

## **Propósito**

Estos pipelines declarativos de Jenkins automatizan la creación y eliminación de usuarios del sistema Linux. Permite agregar usuarios con parámetros personalizados como el inicio de sesión, nombre completo y departamento, además de eliminar usuarios según su UID. También genera una contraseña temporal para el nuevo usuario y fuerza a cambiarla en el próximo inicio de sesión.

---

### **<u>Requisitos Previos</u>**

- Jenkins debe estar instalado y configurado.
- En caso que la ubicación del Jenkinsfile esté en un repositorio de GitHub, agregar la URL del repo al crear el job en Jenkins.
- Si es un repo privado generar un token de seguridad en GitHub y almacenarlo en las credenciales de Jenkins.
- El usuario Jenkins en Linux debe tener privilegios de `sudo` sin contraseña. Para ello ejecutar el siguiente comando:

```bash
    sudo usermod -aG sudo jenkins
```

- O bien, editar el archivo sudoers para que no solicite contraseña al realizar comandos sudo en consola:

```bash
    sudo visudo
```

- Agregar la siguiente línea debajo del usuario root y guardar: <br><br>

<img src="img\sudo-visudo-edit.png" alt="sudo-visudo-edit-cli" width="40%"/>

## **Descripción General del Pipeline de Nuevos Usuarios**

### **<u>Parámetros de Entrada</u>**

- **LOGIN**: Nombre de inicio de sesión para el nuevo usuario (por ejemplo, `jperez`).
- **NOMBRE**: Nombre del usuario (por ejemplo, `Juan`).
- **APELLIDO**: Apellido del usuario (por ejemplo, `Perez`).
- **DEPARTAMENTO**: Departamento (opciones: `Contabilidad`, `Tecnología`, `Finanzas`).
- **ADD_TO_SUDO**: Booleano para asignar privilegios de sudo. <br><br>

  <img src="img\build-with-params-1.png" alt="jenkins-snapshot-1" width="75%"/> <br><br>

  ### [Ver mensajes de consola de salida ](console_outputs\build26_newuser.txt)

  ### En la consola de Linux se puede verificar el usuario creado: <br><br>

  <img src="img\new-user-cli-login.png" alt="cli-login" width="75%"/>

## **Descripción General del Pipeline de Eliminar Usuarios**

### **<u>Parámetros de Entrada</u>**

- **USER_UID**: Número de identificador del usuario a remover. <br><br>

<img src="img\build-with-params-2.png" alt="jenkins-snapshot-2" width="75%"/> <br><br>

### [Ver mensajes de consola de salida ](console_outputs\build18_delete-user.txt)

### En la consola de Linux se puede verificar que el usuario ha sido removido del sistema: <br><br>

  <img src="img\deleted-user-cli.png" alt="cli-deleted-user-cli" width="75%"/>

### **<u>Manejo de Errores</u>**

- **Permiso denegado**: Verifique que el usuario de Jenkins tenga los privilegios correctos de `sudo`.
- **El usuario ya existe**: Asegúrese de que el parámetro `LOGIN` sea único.

### **<u>Referencias</u>**

- [Documentación sobre Sintaxis de Pipeline Declarativo de Jenkins](https://www.jenkins.io/doc/book/pipeline/syntax/)
