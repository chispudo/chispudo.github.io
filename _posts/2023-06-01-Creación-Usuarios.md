---
title: Creación de usuarios y grupos 
layout: post
post-image: "/assets/images/Post/P5/P5.png"
description: Creación de usuarios y grupos en linux

tags:
- Linux

---

En Linux, los usuarios son cuentas que se utilizan para identificar y autenticar a las personas que acceden al sistema. Cada usuario tiene su propio nombre de usuario y contraseña, y puede tener diferentes permisos y configuraciones.

---

# Identificadores de Usuario

La información proporcionada por los identificadores de usuario (UID), identificadores de grupo (GID) y la lista de grupos a los que pertenece un usuario es importante.

```Shel
id user
```
Salida:

```Shell
uid=1001(user) gid=1004(user) grupos=1004(user)
```

**uid**: El UID (**Identificador de Usuario**) es un número único asignado a cada usuario en el sistema. Sirve para identificar de manera exclusiva a un usuario en el sistema.

**gid**: El GID (**Identificador de Grupo**) es un número que identifica al grupo principal al que pertenece el usuario. Un grupo es un conjunto de usuarios que tienen ciertos permisos y configuraciones compartidas.

**grupos**: Esta parte muestra una lista de los GIDs de los grupos adicionales a los que pertenece el usuario. Los grupos adicionales son aquellos en los que el usuario ha sido incluido aparte del grupo principal.

---

# Creación de Usuarios 

Para crear un nuevo usuario en Linux, se utilizan comandos específicos como `useradd`, `adduser` o `usermod`.

### Creando un usuario con `useradd`

Es el comando básico para crear usuarios. 

![P5i1](/assets/images/Post/P5/P5i1.png)

Utilizamos el comando `id nombre_usuario` para que nos muestre información sobre el usuario:

![P5i2](/assets/images/Post/P5/P5i2.png)

* **uid=1001(user1)**: El valor `uid` representa el identificador único del usuario en el sistema. En este caso, el valor es 1001. "user1" es el nombre del usuario asociado a ese identificador.

* **gid=1004(user1)**: El valor `gid` representa el identificador único del grupo principal al que pertenece el usuario. En este caso, el valor es 1004. "user1" es el nombre del grupo asociado a ese identificador.

* **grupos=1004(user1)**: Esta parte muestra una lista separada por comas de los identificadores y nombres de los grupos adicionales a los que pertenece el usuario. En este caso, el usuario "user1" solo pertenece al grupo con el identificador 1004 y nombre "user1".

### Explorando diferentes opciones sobre el comando `useradd`

**Sintaxis**

```Shell
useradd [opciones] <nombre_de_usuario>
```

| Opción | Descripción |
|--------|-------------|
| `<nombre_de_usuario>` | Especifica el nombre del usuario que deseas crear. |
| `-d <directorio_de_inicio>` | Especifica un directorio de inicio personalizado para el usuario. |
| `-s <ruta_al_shell>` | Establece el shell predeterminado para el usuario. |
| `-g <nombre_del_grupo>` | Asigna un grupo principal al usuario. |
| `-p <contraseña_cifrada>` | Establece una contraseña cifrada para el usuario (se recomienda utilizar `passwd` para establecer la contraseña de forma segura). |
| `-m` | Crea el directorio de inicio del usuario si no existe. |
| `-c <comentario>` | Agrega un comentario o descripción al usuario (información de GECOS). |
| `-e <fecha>` | Establece una fecha de vencimiento para la cuenta del usuario. |
| `-r` | Crea un sistema de usuario o una cuenta de usuario del sistema (generalmente utilizado para cuentas del sistema). |
| `-U` | Crea el usuario con un UID único. |
| `-l` | Crea el usuario con un nombre de inicio de sesión (login) en minúsculas. |
| `-k <directorio>` | Copia los archivos y directorios del esqueleto especificado al directorio de inicio del usuario. |


---

# Creando un usuario con `adduser`

Comando más amigable y interactivo para crear usuarios. Proporciona un asistente paso a paso para configurar el usuario. 

![P5i3](/assets/images/Post/P5/P5i3.png)

Información del usuario:

![P5i4](/assets/images/Post/P5/P5i4.png)

---

# Creación de grupos

Los grupos se utilizan para organizar y administrar los usuarios y sus permisos. Para crear nuevos grupos a nuestro sistema utilizamos `groupadd` 

**Sintaxis**:

```Shell
groupadd <nombre_del_grupo>
```

#### Opciones en la creación de grupos

Creación de grupos en Linux, junto con las diferentes opciones.

| Comando | Descripción |
|---------|-------------|
| `groupadd -g <GID> <namegrupo>` | Crea un grupo con un GID (identificador de grupo) específico. El GID debe ser un número no utilizado actualmente por otro grupo. Por ejemplo, `groupadd -g 1001 grupo1` creará un grupo llamado "grupo1" con un GID de 1001. |
| `groupadd -r <namegrupo>` | Crea un grupo de sistema. Los grupos de sistema son utilizados para propósitos específicos del sistema y suelen tener GIDs bajos. |
| `groupadd -f <namegrupo>` | Crea un grupo forzando la creación, incluso si ya existe un grupo con el mismo nombre. Esto puede ser útil si deseas sobrescribir un grupo existente. |
| `groupmod -n <nuevo_nombre> <namegrupo>` | Cambia el nombre de un grupo existente. Por ejemplo, `groupmod -n nuevo_grupo grupo1` cambiará el nombre del grupo "grupo1" a "nuevo_grupo". |
| `groupmod -g <nuevo_GID> <namegrupo>` | Cambia el GID de un grupo existente. Por ejemplo, `groupmod -g 1002 grupo1` cambiará el GID del grupo "grupo1" a 1002. |
| `groupdel <namegrupo>` | Elimina un grupo existente. Por ejemplo, `groupdel grupo1` eliminará el grupo llamado "grupo1". |

**EJEMPLO**:

![P5i5](/assets/images/Post/P5/P5i5.png)

Para mostrar un grupo en especifico utilizo este comando `less /etc/group | grep "Grupo2"`, less para mostrar el contenido del archivo /etc/group y luego grep para filtrar las líneas que contienen el texto "Grupo2".

![P5i6](/assets/images/Post/P5/P5i6.png)


---

# Modificando un usuario con `usermod`

Permite modificar las propiedades de un usuario existente. 

**Sintaxis básica**:

```Shell
usermod [opciones] <nombre_de_usuario>
```

| Opción | Descripción |
|--------|-------------|
| `-l, --login <nuevo_nombre>` | Cambia el nombre de inicio de sesión (login) del usuario. |
| `-d, --home <nuevo_directorio>` | Cambia el directorio de inicio del usuario. |
| `-s, --shell <ruta_al_shell>` | Cambia el shell predeterminado del usuario. |
| `-aG, --append <nombre_del_grupo>` | Agrega al usuario a un grupo adicional. |
| `-G, --groups <lista_de_grupos>` | Reemplaza la lista de grupos a la que pertenece el usuario con la lista proporcionada. |
| `-e, --expiredate <fecha>` | Establece una fecha de caducidad para la cuenta de usuario. |
| `-L, --lock` | Bloquea la cuenta de usuario, lo que impide que el usuario inicie sesión. |
| `-U, --unlock` | Desbloquea una cuenta de usuario bloqueada previamente. |

**EJEMPLOS**:

Quiero que el usuario1 pertenezca al Grupo2:

![P5i7](/assets/images/Post/P5/P5i7.png)

---

## Eliminando usuarios y grupos

Verifica que estás seleccionando el usuario correcto antes de eliminarlo. con `id user`.

Eliminando user1:

![P5i8](/assets/images/Post/P5/P5i8.png)

Eliminando el Grupo2:

![P5i9](/assets/images/Post/P5/P5i9.png)

