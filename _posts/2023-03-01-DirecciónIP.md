---
title: Dirección IP
layout: post
post-image: /assets/images/Post/P1/P1.jpg
description: Conocer muy bien las direcciones IP es fundamental en cualquier área de la informática.
tags: 
- Redes
---

# Dirección de Protocolo de Internet (IP)

_Es un "**protocolo de capa de red**" que se encarga de encaminar los paquetes de datos entre los dispositivos de una red._  

IP proporciona una forma estandarizada para que los dispositivos se comuniquen entre sí a través de Internet, y se utiliza para garantizar que los datos se envían al destino correcto.

---

## Dirección IP Privadas

Son direcciones utilizadas en redes locales y no son accesibles directamente desde Internet.

**EJEMPLO**:

El **enrutador asigna direcciones IP privadas** a cada uno de los dispositivos en tu red local, como una dirección IP privada para tu PC, otra dirección IP privada para tu Impresora, otra para tu TV, y así sucesivamente. 

>Estas direcciones IP privadas son únicas dentro de tu red local, pero no son visibles ni accesibles desde Internet.

![P1i1](/assets/images/Post/P1/P1i1.jpg)

---

## Dirección IP Públicas

_Dirección IP asignada a un dispositivo (enrutador) por un proveedor de servicios de Internet (ISP) y que es visible para el público en Internet._

Este tipo de dirección IP se utiliza para identificar a un dispositivo en Internet y le permite comunicarse con otros dispositivos y servicios en la red.

**EJEMPLO**: 

Muy bien repasando el ejemplo anterior sabemos que el router es el encargado de asignar direcciones IP a cada dispositivo para que se comuniquen entre ellos por ejemplo

* Necesito sacar impreso un documento desde mi computadora a tráves del Wi-fi, bueno la computadora y la impresora se van a comunicar por medio de las direcciones IP privadas de esa red local.


![P1i2](/assets/images/Post/P1/P1i2.jpg)



Pero ahora necesito enviar un documento desde mi computadora a mi profesor ¿ Cómo se hace para comunicarse? si mi dirección IP no la puede ver nadie más que los dispositivos en mi red local. Bueno ahí es donde el router por medio del ISP (Proveedor de servicios de internet), se asigna una dirección IP en nombre de todos los dispositivos en la red, teniendo esa dirección IP pública es como se comunican en internet.
 
* Resumiendo desde mi computadora le envio un documento a mi profesor, el router dice "el dispositivo al que quiero enviarle no esta dentro de mi red", entonces el router con su dirección IP pública actúa como intermediario para que el documento llegue al profesor.

![P1i3](/assets/images/Post/P1/P1i3.jpg)

**Importante** las redes IP Públicas se dividen en:

* **IP estática**: Las direcciones IP estáticas no tienden a cambiar en un largo tiempo estas las ocupan servidores web, ya que necesitan que los dispositivos de la red local se comuniquen entre sí, ejemplo; Netflix, google, servidores DNS, las bases de datos, etc.

* **IP Dinámica**: Son asignadas por un servidor DHCP (Protocolo de configuración dinámica de host) y pueden cambiar con el tiempo. Los dispositivos domésticos y de oficina generalmente tienen direcciones IP dinámicas, ya que se les asigna una dirección IP disponible temporalmente cuando se conectan a la red.

---

### Conclusión

Es importante destacar que si varios dispositivos se conectan a Internet a través de un enrutador o un punto de acceso, comparten la misma dirección IP pública proporcionada por el proveedor de servicios de Internet (ISP).

