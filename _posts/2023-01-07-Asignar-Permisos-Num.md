---
title: Asignar Permisos Método Numérico
layout: post
post-image: /assets/images/Post/P6/LINUX.jpg
description: Comando chmod, utilizado para cambiar permisos

tags:
- linux

---

Cuando interpretas los permisos en formato numérico en Linux, cada posición representa un bit que puede tener el valor de 1 o 0. La posición más a la derecha representa el bit menos significativo, y cada posición a la izquierda representa un bit más significativo.

---

# Permisos numéricos

Estos permisos se asginan con el comando [chmod](https://chispudo.github.io/blog/Chmod), los puedes asignar en formato simbólico, o como en este caso formato numérico. 
A continuación un ejemplo:

![P6i1](/assets/images/Post/P6/P6i1.png)

Bueno para entender mejor la asignación de permisos por este método prepare la siguiente imagen:

![P6i1](/assets/images/Post/P6/P6i2.png)

**EJEMPLO**:

Bueno ahora quiero asignar estos permisos:

`rwx rw- r-x`

**Caracteres**: 
- Si tiene el carácter = 1
- Si no tiene caracter = 0

**Entonces** queda así:

```Shell
rwx rw- r-x
111 110 101
```
**Ahora** les asignamos la posición de derecha a izquierda 0, 1, 2: 

```Shell
Permisos: rwx rw- r-x
Caracter: 111 110 101
Posición: 210 210 210
```

**Fórmula**: `2^Posición`
- Si tiene un 1 la sección de carácter usamos la fórmula.
- Si tiene un 0 la sección de carácter no usamos la fórmula.

**Resolviendo** permisos de usuario `rwx`:

2⁰ + 2¹ + 2² = 1+2+4 =7

**Resolviendo** permisos de grupos `rx-`:

2¹ + 2² = 2+4 = 6

**Resolviendo** permisos de otros `r-x`:

2⁰ + 2² = 1+4 = 5

**ORDENANDO LOS RESULTADOS**:

765 = rwx rw- r-x

**Práctica** ahora que tenemos los permisos en formato numérico probemos en la terminal de linux:

![P6i3](/assets/images/Post/P6/P6i3.png)

Como podemos observar el resultado:

```Shell
Antes:   rwxr-xrw-
Después: rwxrw-r-x
``` 

De esta forma podemos asignar permisos a directorios o archivos pero también se puede en el formato simbólico como en este post [Cambiar Permisos de Archivos y Directorios](https://chispudo.github.io/blog/Chmod)


