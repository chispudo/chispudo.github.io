---
title: Funcionamiento Capa de Internet Modelo TCP / IP
layout: post
post-image: /assets/images/Post/P10/P10i1.jpg
description: También llamada capa de red.

tags:
- Redes

---

# Información de la Capa de Internet o Capa de Red

 Es responsable de garantizar la entrega al host de destino, que potencialmente reside en una red diferente. 
 La capa de internet determina que protocolo es responsable de entregar los paquetes de datos.

- Proporciona direccionamiento lógico en forma de direcciones IP.
- La capa de Red o Internet proporciona conectividad entre host finales en diferentes redes, por ejemplo, fuera de la red de área local (LAN).

![P10i1](/assets/images/Post/P10/Capas.png)


---

## Lista de Protocolos que operan en la capa de Red

|Protocolo|Definición | 
|-----|---|
|IPv4|IPv4 (Internet Protocol version 4) es el protocolo de Internet más ampliamente utilizado. Permite la comunicación y el enrutamiento de paquetes de datos en redes IP.|
|IPv6|IPv6 (Internet Protocol version 6) es la versión más reciente del protocolo de Internet. Ofrece un espacio de direcciones IP más amplio y características adicionales para soportar el crecimiento de Internet.|
|ICMP|ICMP (Internet Control Message Protocol) se utiliza para enviar mensajes y controlar el estado de la red. Proporciona información sobre problemas de entrega de paquetes y errores en la red.|
|ARP|ARP (Address Resolution Protocol) se utiliza para asociar direcciones IP con direcciones MAC en una red local.|
|DHCP|DHCP (Dynamic Host Configuration Protocol) se utiliza para asignar dinámicamente direcciones IP a dispositivos en una red.|
|DNS|DNS (Domain Name System) se utiliza para traducir nombres de dominio legibles para los humanos en direcciones IP numéricas utilizadas por las computadoras.|
|GP|BGP (Border Gateway Protocol) es un protocolo de enrutamiento utilizado en Internet para intercambiar información de enrutamiento entre sistemas autónomos (AS). | 

---

### Protocolo de Internet (IP)

El protocolo de Internet (IP) se encarga de enviar los paquetes de datos al destino correcto en una red. Este protocolo se basa en:

* Protocolo de Control de Transmisión (TCP) 
* Protocolo de Datagramas de Usuario (UDP) 

para entregar los paquetes al servicio correspondiente en el dispositivo de destino.

El protocolo IP **utiliza los paquetes IP** para permitir la comunicación entre dos redes. 

1. Estos paquetes son enviados desde la red de origen y son enrutados a través de diferentes dispositivos de red hasta llegar a la red de destino. 
2. Durante el proceso de enrutamiento, el protocolo IP se encarga de retransmitir cualquier dato que se haya perdido o dañado en el camino.


#### Formato de un paquete IPv4

![P10i2](/assets/images/Post/P10/P10i2.jpg)

    +-------------------------------------------------------------------+
    |                      Encabezado IPv4 (Header)                     |
    +-------------------------------------------------------------------+
    | Versión | Longitud de la cabecera | Tipo de servicio |  Longitud  |
    |         |       (Tamaño fijo)    |                  |  total del  |
    |         |                        |                  |   paquete   |
    +-------------------------------------------------------------------+
    |               Identificación del paquete (ID)                     |
    +-------------------------------------------------------------------+
    |  Bandera  |  Desplazamiento de fragmento  |   Tiempo de vida (TTL)|
    +-------------------------------------------------------------------+
    |        Protocolo         |               Suma de comprobación     |
    +-------------------------------------------------------------------+
    |                         Dirección IP de origen                    |
    +-------------------------------------------------------------------+
    |                        Dirección IP de destino                    |
    +-------------------------------------------------------------------+
    |                      Opciones (si se utilizan)                    |
    +-------------------------------------------------------------------+
    |                            Datos del paquete                      |
    |                             (Carga útil)                          |
    +-------------------------------------------------------------------+

En este ejemplo, el paquete IPv4 consta de varios campos que contienen información importante para el enrutamiento y la entrega de los datos. Estos campos son los siguientes:

- **Versión**: Indica la versión del protocolo IP utilizado (por ejemplo, IPv4).
- **Longitud de la cabecera**: Especifica la longitud de la cabecera del paquete en palabras de 32 bits.
- **Tipo de servicio**: Proporciona información sobre cómo debe ser tratado el paquete por los routers y otros dispositivos de red.
- **Longitud total del paquete**: Indica la longitud total del paquete, incluyendo la cabecera y los datos.
- **Identificación del paquete**: Un valor único asignado al paquete para ayudar en la reensamblaje de fragmentos en caso de que el paquete se divida en fragmentos más pequeños durante la transmisión.
- **Bandera y desplazamiento de fragmento**: Utilizados para indicar si el paquete se divide en fragmentos y cómo se deben ensamblar.
- **Tiempo de vida (TTL)**: Especifica el número máximo de saltos o routers que puede atravesar el paquete antes de que se descarte.
- **Protocolo**: Indica el protocolo de la capa superior que utiliza la carga útil del paquete (por ejemplo, TCP, UDP).
- **Suma de comprobación**: Un valor calculado que se utiliza para verificar la integridad de los datos en el paquete.
- **Dirección IP de origen**: La dirección IP del dispositivo que envía el paquete.
- **Dirección IP de destino**: La dirección IP del dispositivo al que se envía el paquete.
- **Opciones**: Opcionalmente, se pueden incluir opciones adicionales en el paquete, como la marca de tiempo.
- **Carga útil del paquete**: Contiene los datos reales que se están transmitiendo, como el contenido de un mensaje, una solicitud HTTP o cualquier otro tipo de información que se esté enviando a través de la red.



#### Resumen

La capa de Red o capa de Internet del modelo TCP/IP se encarga de enrutar los paquetes de datos a través de la red desde el origen hasta el destino. 


