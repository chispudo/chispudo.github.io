---
title: Lectura de Permisos
layout: post
post-image: "/assets/images/Post/P3/P3.png"
description: En linux la lectura e interpretación de permisos es una parte fundamental.

tags: 
- Linux

---

En este post se abordarán conceptos importantes como los diferentes tipos de permisos (usuario, grupo y otros) y cómo se combinan para determinar los niveles de acceso.

---

# Lectura de Permisos

![P3i1](/assets/images/Post/P3/P3i1.jpg)

---

# Interpretación de Permisos

![P3i2](/assets/images/Post/P3/P3i2.jpg)

---

## Listar 

Comandos:

**Listar Archivos - Directorios**
Lista los archivos y directorios de un directorio específico. Si no se especifica ningún directorio, entonces se listará el contenido del directorio actual.

```Shell
❯ ls               
Bash
```

**Listar en Formato largo**
Proporciona información detallada sobre los archivos y directorios, como el dueño, los permisos, etc.

```Shell
❯ ls -l 
total 688
drwxr-xr-x 2 gabriel gabriel   4096 may  8 19:19 Cartas
drwxr-xr-x 3 gabriel gabriel   4096 mar  7 09:52 Clasificación de Cuentas
-rw-r--r-- 1 gabriel gabriel  17351 oct 16  2021 Doc.txt
-rw-r--r-- 1 gabriel gabriel 490640 nov 15  2022 DPI.pdf
```

**Listar en formato largo y elementos ocultos**
Mostrar todos los archivos, incluyendo los ocultos para obtener información.

```Shell
> ls -la
total 8
drwxrwxr-x 3 usuario usuario  .
drwxr-xr-x 6 usuario usuario  ..
-rw-rw-r-- 1 usuario usuario  archivo1.txt
drwxrwxr-x 2 usuario usuario  directorio1
.hiddenfile 
```

**Listar en formato humano**
Este comando listará en formato largo todos los archivos y directorios del directorio actual con el tamaño de los archivos en formato humano.

```Shell
❯ ls -lh 
total 688K
drwxr-xr-x 2 gabriel gabriel 4.0K may  8 19:19 Cartas
drwxr-xr-x 3 gabriel gabriel 4.0K mar  7 09:52 Clasificación de Cuentas
-rw-r--r-- 1 gabriel gabriel  17K oct 16  2021 Doc.txt
-rw-r--r-- 1 gabriel gabriel 480K nov 15  2022 DPI.pdf
```

Para saber más de este comando en su shell ingrese lo siguiente:

```Bash
> man ls     
```

---
