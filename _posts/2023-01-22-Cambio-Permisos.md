---
title: Cambio de Permisos
layout: post
post-image: "assets/images/Post/P4/P4."
description: Cambio permisos u,g,o.

tags:
- Linux

---

Aprenderas a cambiar permisos a usuarios, grupos, otros. Tanto de archivos, direcotorios, etc.

---

# Creación de usuarios

Recuerda que el comando `adduser` generalmente requiere privilegios de superusuario, por lo tanto, se utiliza sudo al principio del comando para ejecutarlo con los permisos adecuados.

```Shell
sudo adduser nombre_usuario
```

A continuación, se te solicitará establecer una contraseña para el nuevo usuario. Ingresa una contraseña segura y sigue las instrucciones adicionales que se te indiquen.
**Pulsando ENTER puedes saltar lo que creas innecesario**

![P4i1](/assets/images/Post/P4/P4i1.png)


### Cambiar contraseñas a usuarios

Utilizamos el comando `passwd` y el nombre del usuario que se cambiará la contraseña. Si no colocas el usuario la contraseña se cambiara al usuario que este ejecutandoel comando.

```Shell
passwd ana
```

### Crear grupos

Para crear un grupo utilizamos el comando `addgroup` con su respectivo nombre de grupo `Estudiantes`

```Shell
addgroup Estudiantes
```

---

# Cambios de propietario y grupo sobre archivos o directorios `chown`

El comando chown en Linux se utiliza para cambiar el propietario y/o el grupo de un archivo o directorio. Es una herramienta poderosa que te permite ajustar los permisos de acceso y controlar quién puede realizar acciones en los archivos.

**Sintaxis**

```Shell
chown usuario:grupo archivo/directorio
```

### Cambiar propietario y grupo simultáneamente

Para cambiar tanto el propietario como el grupo de un archivo o directorio al mismo tiempo, se utiliza el siguiente formato:

```Shell
chown usuario:grupo archivo
```

### Cambiar propietario o grupo de forma independiente

Si deseas cambiar solo el propietario o solo el grupo de un archivo o directorio, puedes hacerlo utilizando el siguiente formato:

* Cambiar solo el propietario:

`chown nuevo_propietario archivo`

* Cambiar solo el grupo:

`chown :nuevo_grupo archivo`

---

# Cambio de Permisos

El comando `chmod` (change mode):

**Sintaxis**:

```Shell
chmod modificador[+][-]permisos file
```

* **Modificador** usuario, grupo, otros.
* **[+]** Indica el agregar permisos.
* **[-]** Indica quitar permisos.
* **Permisos**: Permisos agregar o quitar, r,w,x.

**ejemplo:**

* En este ejemplo le indico que el usuario no debe tener permisos de lectura(r) sobre el documento.txt

```Bash
chmod u-r documento.txt
```

_otro ejemplo_

![Pi3](/assets/images/Post/P4/P4i3.png)


### Combinación de Permisos

Si quiero indicar múltiples permisos sobre un directorio o archivo:

```Shell
chmod u+r,g+x carpeta
```

### Establecer permisos específicos

Si necesitas establecer permisos específicos para usuarios, grupos y otros en un archivo o directorio en Linux, puedes utilizar el comando `chmod`. En este caso, utilizaremos el signo `=` para indicar únicamente los permisos que deseamos asignar.

```Shell
chmod u=w,o=wx carta.txt
```

En el ejemplo anterior, se han establecido los siguientes permisos:

Para el **usuario (u)**: se ha asignado únicamente el permiso de escritura (w).
Para **otros (o)**: se han asignado los permisos de escritura (w) y ejecución (x).
Estos permisos se han aplicado al archivo llamado "carta.txt".



