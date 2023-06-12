---
title: Funcionamiento Capa de Transporte Modelo TCP / IP
layout: post
post-image: /assets/images/Post/P9/P9.jpg	
description: Modelo utilizado en la enrutación de datos.

tags:
- Redes

---

# Definición de la capa de Transporte

La capa de transporte es responsable de entregar datos de manera confiable entre dos sistemas o redes. TCP y UDP son los dos protocolos de transporte que ocurren en esta capa.

![P8F](/assets/images/Post/P9/P9i1.jpg)

## Protocolo TCP

_Garantiza que los datos se transmitan de manera confiable al servicio de destino._

Es un "protocolo de comunicación" de internet que permite a dos dispositivos formar una conexión y transmitir datos de forma fiable y en el orden correcto.

>TCP funciona estableciendo una **conexión** entre dos dispositivos antes de enviar los datos.

![Padd](/assets/images/Post/P9/Padd.jpg)

[Más info](https://chispudo.github.io/blog/TCP-IP)

Entonces el protocolo TCP:

- Proporciona una entrega confiable de datos mediante el establecimiento de una conexión entre dos sistemas.
- Garantiza la entrega secuencial y sin errores de los datos.
- Utilizado en aplicaciones que requieren una entrega confiable de datos, como la transferencia de archivos, el correo electrónico y la navegación web.

---

## Protocolo de Datagramas de Usuario (UDP)

Es utilizado en aplicación que no requieren una entrega confiable de datos, como la transmisión de audio y video en tiempo real, juegos en línea y consultas DNS.
Por eso este protocolo se caracterisa por ser más rápido que TCP debido a su enfoque sin conexión y sin verificación. Pero por ese motivo la entrega de los datos pueden producir errores porque no establece conexión previa, resumiendo no garantiza la entrega secuencial o sin errores de los datos.

![Padd](/assets/images/Post/P9/P9i2.jpg)


