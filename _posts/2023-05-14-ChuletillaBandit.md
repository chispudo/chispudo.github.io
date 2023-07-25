---
title: Bandit Overthewiregames "Chivito/Chuletilla"
layout: post
post-image: /assets/images/Post/P8/P8.png
description: Comó enfrentar los retos bandit y no morir en el intento.
tags:
- LINUX

---

Este post tendrá información acerca de los juegos de guerra o mejor conocido como [OverTheWireGames](https://overthewire.org/wargames/bandit/) en especifíco de los juegos bandit (bandido).
Esa página proporciona una base muy buena sobre conceptos de linux, en los que tendrás que enfrentarte a ciertos desafíos. Puedes visitar el enlace anterior para más información.

Con respecto al post tendrá información que te puede ayudar a resolver o a conocer algunos coneptos básicos a la hora de enfrentarte a sus desafíos. 

> No resolvere los desafíos más bien te enseñare algunas técnicas que necesitas de saber antes de empezar a jugar.

### Indice

- [¿Qué es ssh?](#ssh)
- [Conexiones por ssh](#conectarse-por-ssh)
- [Comandos de ayuda en linux](#conceptos-básicos)
- [Búsquedas rápidas con find](#búsquedas-con-find)
 - [Ejemplos búsquedas simples con find](#práctica-búsquedas-simples)
 - [Opción -exec en find](#opción-exec)
- [Buscar dentro de archivos](#uso-básico-del-comando-grep)
- [Método de codificación base64](#base64)
- [Cifrado César ROT13](#rot13)
- [Openssl](#openssl)
- [Conclusión](#conclusión-final)


# ssh

SSH (Secure Shell) es un protocolo de red seguro utilizado para la administración remota de sistemas y el intercambio seguro de datos.

En el contexto de la ciberseguridad SSH se suele utilizar para realizar pruebas de penetración y evaluaciones de seguridad en sistemas remotos. Permite identificar vulnerabilidades y realizar ataques controlados.

### Conectarse-por-ssh

Hay varias formas dependiendo del la situación, te mostraré todas las que conozco hasta el momento:

- Conexión por dirección IP.

```shell
# Sintaxis
ssh usuario@direcciónIP:[puerto]
# Ejemplo
ssh user@192.168.0.1:8080
# Otro ejemplo
ssh frijol@192.168.1.6:22
```
- Conexión por servidor remoto y dominio.

```shell
# Sintaxis
ssh servidor@dominio.com -p [puerto]
# Ejemplo
ssh bandit0@bandit.labs.overthewire.org -p 2220
```
- Por claves privadas **clave.sshkey**.

```shell
# Sintaxis
ssh -i clave_privada usuario@direccion_servidor
```

- Por conexión automática. En este caso es necesario especificar la contraseña correspondiente al usuario y que se utilizará para la autenticación.

```shell
# Sintaxis
sshpas -p 'contraseña' shh servidor@dominio.com -p [puerto]
# Ejemplo
sshpass -p 'cat bandit2' ssh bandit2@bandit.labs.overthewire.org -p 2220
```
--- 

# Conceptos-básicos 

A continuación una lista de comandos que te pueden servir al momento de resolver los desafíos de bandido.

**man**

Utilizar el manual, se accede con el comando y la palabra man:

```shell
> man man
# Para buscar dentro del manual una opción específica utiliza '/' 
> /Opciones
# 'q' para salir
```
.

**--help**

También puedes utilizar la opción --help:

```shell
man --help
```
.

**apropos**

Buscar nombres y descripciones de páginas de manual con `apropos` sin duda este comando es ideal para buscar información acerca de lo que quieres hacer pero no sabes el nombre del comando:

```shell
❯ apropos --and repeated lines 
uniq (1)             - report or omit repeated lines
```

- También es útil para saber la información básica de lo que hace un comando

```shell
> apropos --exact uniq
uniq (1)             - report or omit repeated lines
```
.

![P8i1](/assets/images/Post/P8/P8i1.png)

**whatis**

Puedes ejecutar `whatis <comando>` para obtener una descripción breve de un comando específico. Mostrar descripciones de una línea de las páginas del manual.

```shell
> whatis man
man (1)              - interfaz de los manuales de referencia del sistema
man (7)              - macros to format man page
```
.

Son casi lo mismo que apropos jeje.

**ls**

El comando _ls_ te listará todos los archivos o directorios de tu ruta actual (_pwd_ para saber mi ruta actual)
Tienes más información en el siguiente [post](https://mechitast.github.io/blog/Lectura-Permisos).

**cat**

El comando _cat_ te permite mostrar el contenido de un fichero o archivo su sintaxis es la siguiente:

```shell
cat ficheto.txt
```

- Mostrar el contenido de todos los archivos en el directorio actual. El carácter `*` es un comodín que representa cualquier archivo en el directorio actual, y la opción `./` indica que se busquen los archivos en el directorio actual.

```shell
> cat ./*
rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi
```

- Acceder a un archivo con un espacio en su nombre, para hacerlo puedes poner **cat** y con el tabulador se autocompleta:

```shell
> cat spaces\ in\ this\ filename
# Otra forma
> cat "spaces in this filename"
```

- Mostrar archivos ocultos:

```shell
> cat .hidden 
```
. 

**cd**

Utilizamos el comando cd para acceder a directorios pero y si estos son ocultos como accedemos bueno puedes utilizar comodines como el asterisco:
Recuerda el punto `.` significa el sitio actual y la barra en un directorio (en este caso). 

```shell
> cd ./*
# Otra forma de acceder

```
.

**file**

Utilidad para determinar el tipo y formato de un archivo

```shell
> file Documentos 
Documentos: directory
> file ./*
./-file04: data
./-file05: Non-ISO extended-ASCII text, with NEL line terminators
./-file06: Non-ISO extended-ASCII text, with no line terminators, with escape sequences
./-file07: ASCII text
```
.

**strings**

```shell
> whatis strings
imprimir las secuencias de caracteres imprimibles en ficheros
``` 

Básicamente encuentra e imprime cadenas de texto incrustadas en archivos binarios. Puede ser útil para visualizar ficheros que no se sepa que son de texto plano.
[Más info](https://es.wikipedia.org/wiki/Strings_(Unix)#:~:text=strings%20es%20un%20programa%20de,objeto%20y%20volcados%20de%20memoria.)

```shell
> strings ./*
;#8q
BXot
.Y>*
a\6n
lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR
```
.

**sort**

El comando sort sirve para ordenar líneas de texto en orden alfabético o númerico.

-   `-r`: Ordenar en orden inverso.
-   `-n`: Ordenar según el valor numérico de las líneas.
-   `-u`: Solo imprimir líneas únicas.

```shell
sort -r file.txt
```
. 

Recuerda si necesitar hacer algo sobre un archivo o directorio y no sabes como hacerlo puedes utilizar **apropos**

```shell
❯ apropos --and sort file               
apt-sortpkgs (1)     - Utility to sort package index files
bunzip2 (1)          - a block-sorting file compressor, v1.0.8
bzip2 (1)            - a block-sorting file compressor, v1.0.8
comm (1)             - compare two sorted files line by line
sort (1)             - sort lines of text files
sort-dctrl (1)       - sort Debian control files
```
.

**Tuberías**

Permiten conectar o dirigir la salida de un comando a otro comando o archivo.

```shell
> sort data.txt | uniq -u
EN632PlfYiZbn3PhVK3XOGSlNInNE00t
```
---

## Búsquedas con Find

El comando find (buscar) como su nombre lo indica buscará archivos basandose en las diferentes opciones que especifiques.

**Sintaxis**:

```shell
find [ruta] [opciones]
```

**Ruta**
- `/` Buscar en el directorio raíz, en todo el sistema.
- `.` Buscar en la carpeta en la que estas ubicado (pwd para saber tú ubicación).
- `~` Para buscar desde el directorio home.

![P18i0](/assets/images/Post/P18/P18i0.png)

### Práctica búsquedas simples

Buscando un directorio por nombre poemas desde el directorio raíz (2❯ /dev/null) se utiliza para evitar que te salgan mensajes de error.

```shell
❯ find / -name poemas 2> /dev/null
/home/gabriel/Documentos/Bash/Udemy/Scripts-Bash/Tareas/Regedex/poemas
/mnt/HDD1/Contenido/Practico/poemas
```

* Búsqueda por dos parámetros:

```shell
❯ find / -type f -name 'IP*.sh' 2> /dev/null
/home/gabriel/Scripts/Bash/IPv4.sh
/mnt/HDD1/BackupME/Archivos/Scripts/Bash/IPv4.sh
```

* Buscando por tres parámetros:

```shell
❯ find ~ -maxdepth 4 -type d -iname '*ath' 2> /dev/null
/home/gabriel/.oh-my-zsh/plugins/shrink-path
/home/gabriel/.oh-my-zsh/plugins/copypath
/home/gabriel/Documentos/Office/Math
```
* Buscar archivos ocultos en un directorio:

```shell
$ find . -name ".*" -maxdepth 1 ./.hidden_file
```

### Opción exec

Se basa en la ejecución de cualquier comando en todos los elementos que encontro previamente el find.

**Sintaxis**

```shell
find [ruta] [opciones] -exec <comando> '{}' ';'
```
-

**EJEMPLO**:

- Buscamos en el directorio home **~** ficheros con un peso mayor a un gigabyte **+1G** y con **-exec** le pasamos el comando que queremos ejecutar al resultado de la búsqueda anterior _(el resultado de la búsqueda ante>
Y por último terminanos el comando con **';'**.

```shell
❯ find ~ -size +1G -exec ls '{}' ';'

/home/gabriel/Descargas/Loc-OS-22-LXDE-i386.iso

```

- Las posibilidades son muchas por eso es importante practicar este comando.

---

### Uso básico del comando **grep**

A diferencia de find el comando grep se puede utilizar para buscar dentro de archivos, un ejemplo podría ser buscar la palabra linux dentro del archivo.txt:

```shell
grep -i "linux" archivo.txt
```
Esto buscará en el archivo "archivo.txt" todas las líneas que contengan la palabra "Linux" sin importar si está en mayúsculas o minúsculas.

También se puede utilizar el uso de tuberías estas permiten **conectar o dirigir la salida de un comando a otro comando o archivo**.

```shell
> cat data.txt | grep "millionth"
millionth	TESKZC0XvTetK0S9xNwm25STk5iWrBvP
```
---

## Base64

Base 64 no es un método de encriptación de datos más bien es una codificación. Una codificación consiste en transformar un carácter del alfabeto a otro lenguaje.

### Propósito de base64

Base64 utiliza la codifiación de datos binarios (como imágenes o archivos) a texto con el propósito de que la transferencia de los mismos se puedan realizar en canales que solo admiten texto, esto se hacen en medios que no puedan manejar datos binarios.

> Para que estos datos se puedan almacenar en el ordenador y que puedan interpretarlos se deben convertir a formato binario “bytes.

#### Codificar y decodificar base64 en la terminal

Para codificar se utiliza **base64**.

```shell
echo gmichet | base64
Z21pY2hldAo=
```
- Para decodificar se agrega un **-d** al final:

```shell
echo Z21pY2hldAo= | base64 -d
gmichet
```
- Otro ejemplo pero con un archivo:

```shell
bandit?@bandit:~$ cat data.txt 
VGhlIHBhc3N3b3JkIGlzIDZ6UGV6aUxkUjJSS05kTllGTmI2blZDS3pwaGxYSEJNCg==
bandit?@bandit:~$ cat data.txt | base64 -d
The password is 6zPeziLdR2RKNdNYFNb6nVCKzphlXHBM
```
.

La mayoría de la codificación base64 se puede reconocer por agregar al final el signo = esto se debe a que el signo elimina el relleno.

---

## ROT13

El primer cifrado conocido (un cifrado por sustitución) fue usado por Julio César alrededor del año 58 AC. Ahora se conoce como el cifrado César.

Para aplicar ROT13 en Bash, se puede utilizar el comando **tr** (translate), que se utiliza para traducir o reemplazar caracteres. En el caso de ROT13, se puede traducir cada letra en el alfabeto a su equivalente ROT13.

### Cifrar y Descifrar el ROT13 en Bash

```shell
tr 'A-Za-z' 'N-ZA-Mn-za-m'
```
- Ejemplos:

```shell
❯ echo "Hola mundo" | tr 'A-Za-z' 'N-ZA-Mn-za-m'
Ubyn zhaqb
❯ echo "Ubyn zhaqb" | tr 'A-Za-z' 'N-ZA-Mn-za-m'
Hola mundo
```
---

## Openssl

El comando **openssl** es una herramienta muy versátil para trabajar con encriptación, autenticación y certificados digitales. La opción **connect** se utiliza para conectarse a un servidor remoto y establecer una conexión segura SSL/TLS.
[Más info SSL/TLS](https://djangocas.dev/blog/test-tls-connectivity-with-openssl/#:~:text=openssl%20s_client%20is%20an%20SSL,diagnostic%20tool%20for%20SSL%20servers.)

```shell
openssl s_client -connect <host>:<port>
```
. 

_Opción Interesante:_

La opción **-ign_eof** indica que OpenSSL no debe cerrar la conexión cuando se reciba una señal de fin de archivo (EOF).

```shell
openssl s_client -connect localhost:30001 -ign_eof
```
---

# Conclusión Final

En este post cubri algo básico acerca de los juegos bandit, si eres nuevo para poder pasarlos con éxito es necesario que investigues cada cosa y que intentes de diferentes formas en alcanzar la flag, no pienses que te saldrá en un día es importante que lleves notas o documentes cada solución que encuentres en los niveles. 

También trata de ir a los enlaces que recomienda la propia página además puedes usar el manual de los comandos eso te dará mucha soltura y si no conoces un comando puedes utilizar **apropos**.



