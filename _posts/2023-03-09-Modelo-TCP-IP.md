---
title: Funcionamiento Capa de Aplicación Modelo TCP / IP
layout: post
post-image: /assets/images/Post/P8/P8F.png
description: Modelo utilizado en la enrutación de datos.

tags:
- Redes

---

Es un marco utilizado para visualizar cómo se organizan y transmiten los datos a través de una red.
Su función específica es enviar y recibir datos.

---

# Modelo TCP/IP


| Capa                | Función                                                         | Ejemplos de protocolos                                   |
|---------------------|------------------------------------------------------------------|---------------------------------------------------------|
| Capa de Aplicación  | Interacción entre aplicaciones y usuarios finales.               | HTTP, FTP, DNS, SMTP, SSH, Telnet                       |
| Capa de Transporte  | Entrega confiable y sin errores de datos entre sistemas finales. | TCP, UDP                                                |
| Capa de Internet    | Enrutamiento y direccionamiento de los datos en la red.          | IP, ICMP, ARP                                           |
| Capa de Acceso a la Red | Transmisión física de los datos a través del medio de comunicación. | Ethernet, Wi-Fi, PPP, DSL, ATM, SONET, Frame Relay     |


---

## Capa de Aplicación

Esta capa es donde residen las aplicaciones y servicios que utilizan los usuarios finales, como HTTP, DNS, FTP, SMTP, etc. 


_Ejemplo del funcionamiento de la capa de aplicación_

- Tú, como usuario, escribes la dirección del blog en la barra de direcciones de google y presionas Enter.

- Google, como navegador web, actúa como cliente y envía una solicitud HTTP al servidor que aloja tu blog. Esta solicitud incluye información como la dirección de tu blog y cualquier otra información relevante que google considere importante para obtener los recursos necesarios para cargar la página.

- Cuando envías una solicitud HTTP desde tu navegador web, esta solicitud se envuelve en un paquete de datos que contiene información de la capa de aplicación, como la solicitud HTTP y la dirección IP del servidor al que te estás conectando. Este paquete se transmite hacia abajo a través de las capas del modelo TCP/IP.

- Una vez que el paquete llega al servidor, este sigue el proceso inverso, donde cada capa del modelo TCP/IP va extrayendo la información correspondiente y enviándola a la siguiente capa hasta llegar a la capa de aplicación, donde se procesa la solicitud HTTP.

- El servidor que aloja el blog, al recibir la solicitud a través de la capa de aplicación, analiza la información proporcionada y genera una respuesta correspondiente. En este caso, la respuesta sería el envío de los archivos y carpetas necesarios para que funcione la página (archivos HTML, CSS, imágenes, etc.).

- Este caso, la respuesta sería el envío de los archivos y carpetas necesarios para que funcione tu blog (archivos HTML, CSS, imágenes, etc.).

- El servidor envía la respuesta al navegador google a través del protocolo HTTP. La respuesta contiene los archivos y carpetas necesarios para cargar y mostrar correctamente el blog.

- Google, al recibir la respuesta del servidor, procesa la información recibida. Esto implica leer y analizar los archivos HTML, aplicar los estilos CSS, cargar las imágenes y cualquier otro recurso necesario para mostrar el blog correctamente en la ventana del navegador.


![P8F](/assets/images/Post/P8/P8F.png)

---

**Nota** 
En este post solo tome en cuenta la capa de aplicación no repase a fondo el funcionamiento de cada una de las capas al momento del envío del paquete. 

