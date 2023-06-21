---
title: Creación de usuarios y grupos 
layout: post
post-image: "/assets/images/Post/P5/P5.jpg"
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

![Opciones_useradd](/assets/images/Post/P5/Opciones_useradd.png)

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

![Opciones_grupo](/assets/images/Post/P5/Opciones_grupo.png)

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

