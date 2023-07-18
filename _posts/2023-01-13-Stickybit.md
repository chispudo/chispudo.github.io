---
title: Permisos Especiales / Sticky Bit
layout: post
post-image: /assets/images/Post/P16/P16.jpg
description: Un vistazo a los permiso Sticky Bit

tags:
- LINUX
- PERMISOS

---

Su objetivo es que solo el usuario creador pueda eliminar o renombrar un archivo en sistemas donde todos los usuarios tienen permisos de lectura y escritura. 

---

El permisos sticky bit consiste en aplicar permisos a directorios cuyos permisos sean estos:

`drwx rxw rwx`

Esos permisos indican que el propietario, el grupo y otros pueden escribir, leer y ejecutar.

Por eso es importante la asignación del permiso sticky bit para que otros usuario no puedan borrar archivos que no sean los suyos.

**Asignar Permiso Sticky bit**

```shell
chmod +t directorio/
```
.                                                                                                                       

**Retirar Permiso Sticky bit**

```shell
chmod -t directorio/
```
---

## Ejemplo Práctico

Tenemos dos directorios públicos que son propiedad del usuario `sauce`:

![P16i0](/assets/images/Post/P16/P16i0.png)

El directorio **Sin_Stickybit** no tiene asignado el permiso.
`drwxrwxrwx`

Y el otro directorio **Stickybit** si lo tiene asignado se puede ver porque tiene una **t** en lugar de una **x**.
`drwxrwxrwt`

---

### Sin Permiso Sticky bit

Que pasaria si otro usuario en este caso **frijol** por un motivo elimina un archivo que es propiedad de **sauce** de la carpeta **Sin_Stickybit**:

![P16i1](/assets/images/Post/P16/P16i1.png)

Entonces si el archivo **Sauce.txt** tenia estos permisos:
`-rw-r--r--`

**¿Por qué motivo otro usuario lo pudo eliminar?**
Esto paso por que el directorio tiene asignado estos permisos: `drwxrwxrwx`

---

### Con Permiso Sticky bit

Ahora si tenemos un directorio con el permiso asignado sticky bit que sucede:

![P16i2](/assets/images/Post/P16/P16i2.png)

Bueno ahora el directorio esta protegido contra estos errores en el que otro usuario que no sea el propietario pueda borrar archivos.


