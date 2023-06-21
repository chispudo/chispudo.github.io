---
title: Estructura de una dirección IPv4
layout: post
post-image: /assets/images/Post/P11/P11i1.jpg
description: Conocer como se compone una dirección IP es importante

tags:
- Redes

---

# Dirección IP 

Recordando una dirección IP es un identificador único que identifica a un dispositivo, ya sea en su red local LAN o en Internet, etc.
Estas direcciones IP estan compuestas por el lenguaje binario de unos y ceros, que es el lenguaje que entienden las computadoras.

---

## Clases de Direcciones IPv4

Existen diferentes clases para cada dirección IP: 

![P11i1](/assets/images/Post/P11/P11i1.png)

Ejemplos de diferentes clases de direcciones IP:

* Una empresa puede tener asignado este rango de dirección IP privada:

`10.10.0.2`

* Y en tu casa la dirección IP privada de tú telefóno puede ser:

`192.168.0.15`

* Y la IP pública de tu enrutador (router) puede ser:

`190.166.103.108`

Ahora teniendo esos ejemplos te muestro una tabla de los diferentes rangos de direcciones IP que hay:

![P11i2](/assets/images/Post/P11/P11i2.png)

- Clase A: Esta clase se utiliza principalmente para redes grandes con muchos host.
- Clase B: Esta clase se utiliza para redes de tamaño mediano.
- Clase C: Esta clase se utiliza para redes pequeñas.
- Clase D: Se utilizan para multicast, lo que significa que se utilizan para enviar datos a múltiples hosts en una sola transmisión.
- Clase E: Se reservan para uso futuro o experimentación y no se utilizan para redes públicas.

---

#### Como podemos identificar la dirección asignada en nuestro dispositivo

Esto puede variar de acuerdo a tu sistema operativo pero el proceso es similar ya que la forma más eficiente es desde la consola de comandos:

**DIRECCIÓN IP PRIVADA WINDOWS**

![P11i2](/assets/images/Post/P11/P11i4.jpg)


En windows abre el **CMD** o el **Powershell** y ejecuta el siguiente comando:

`ipconfig`

>Puedes identificar tú IP por el apartado `Link-local` o `IPv4 address`.

La dirección IP privada suele tener el formato "192.168.X.X" o "10.X.X.X" dependiendo de la configuración de tu red. 

**DIRECCIÓN IP PRIVADA EN LINUX**

![P11i2](/assets/images/Post/P11/P11i5.png)

Para ver tu dirección IP privada desde la terminal de Linux, puedes utilizar el comando:

`ifconfig`

>Generalmente la dirección IP en linux esta denominada como `inet` para IPv4 e `inet6` para IPv6.

Otras formas de ver la dirección IP privada es:
* Este comando mostrará la información de todas las interfaces de red en tu sistema, incluyendo las direcciones IP asignadas. 

`ip addr show`

* Pero si lo que quieres es ver únicamente tu IP privada y nada más puedes utilizar:

`hostname -I | awk '{print $1}` o simplemente `hostname -I`

**DIRECCIÓN IP pública**

![P11i2](/assets/images/Post/P11/P11i6.png)

La IP pública del router de tú casa suele cambiar (IP Dinámica) es raro que tu IP no cambie (IP estática). Cambiando de tema el que conozcan tu dirección IP pública es un problema porque esa IP es la principal que utiliza tu router para comunicarse en nombre de todos los dispositivos en la red LAN a internet, generalmente apagando el router automáticamente cambia la IP (debido a la memoria volátil) como es dinámica en mayoría de redes locales, a no ser que tengas un servidor, siempre ten cuidado en no compartir la IP pública.

Para visualizar mi IP pública lo puedes hacer por este medio:

[Whatismyip.com](https://www.whatismyip.com/es/)

>La dirección IP que te muestra el sitio web WhatIsMyIP será la dirección IP pública de tu conexión a internet. La dirección IP pública es la que identifica tu conexión en internet y te permite comunicarte con otros dispositivos y servicios en la red.

---

# Entendiendo la estructura de las direcciones IPv4

Las direcciones IP estan representadas en decimales para interpretarlas facilmente, pero las computadoras las entienden en binario (01010101), a continuación una imagen para entender mejor:

![P11i3](/assets/images/Post/P11/P11i3.jpg)

- **32 bits**: Una dirección IPv4 consta de un total de 32 bits ni más ni menos.
- **Byte**: Un byte es un conjunto de 8 bits y a esto se le llama _octeto_.
- **Bits**: Corresponde a un solo dígito binario pueden ser _unos o ceros_.
- **Octeto**: Un octeto corresponde a 1 byte o 8 bits. (0 es un octeto, 192 es un octeto, 15 es un octeto).

---

Ahora ya conoces lo básico de las direcciones IP espero que esto sirva de ayuda.
