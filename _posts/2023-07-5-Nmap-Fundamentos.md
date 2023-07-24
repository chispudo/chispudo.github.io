---
title: Uso básico nmap
layout: post
post-image: /assets/images/Post/P17/P17i0.png
description: Nmap herramienta muy útil al momento de realizar un reconocimiento
tags:
- NMAP

---

Nmap por sus siglas Network Mapper (Mapeador de Red), es una herramienta que permite descubrir dispositivos en una red.

### Indice

- [Conocimientos Previos](#conocimientos-previos)
- [Entendiendo el uso básico de nmap](#uso-de-nmap)
- [Escaneos de host](#descubrimiento-de-host-en-la-red)
- [Información útil que debes conocer](#información-útil)
- [Repaso apretón de manos](#repaso-handshake)
- [Respuesta de puertos](#puertos)
- [Utilizando Wireshark](#utilización-de-wireshark)
- [Tipos de Escaneos](#tipos-de-escaneos)
- [Escaneo Stealth](#escaneo-stealth)
- [Escaneo UDP](#escaneo-udp)
- [Escaneo TCP](#escaneo-tcp-connect)
- [Escaneo ACK](#escaneo-ack)

---

### Conocimientos Previos

Es recomendable conocer algunos temas para entender mejor el post, bueno te dejo unos enlaces para que le des un vistazo:

- [Modelo TCP/IP](https://mechitast.github.io/blog/MTCPIP)
- [Protocolo TCP (Handshake) y Protocolo IP](https://mechitast.github.io/blog/TCP-IP)
- [¿Qué es una dirección IP](https://mechitast.github.io/blog/Direcci%C3%B3nIP)
- [¿Cómo se compone una IPv4?](https://mechitast.github.io/blog/Estructura-IP)

---

## Uso de nmap

Nmap tiene una sintaxis para escaneos básicos y es de la siguiente forma:

```shell
nmap -s<Tipo de escaneo >
```
- La opción `-s` en Nmap es un argumento utilizado para especificar el tipo de escaneo que se realizará. 

Opciones de escaneo con nmap:

![P17i1](/assets/images/Post/P17/P17i1.png)

Existen muchos más es cosa de ver el manual de nmap 

```shell
nmap --help
```
---

### Descubrimiento de host en la red

Para escanear los host de la red local es de la siguiente forma:

```shell
nmap -sP [rango_ip]
```

- Ejemplo escaneo por notación CIDR, utiliza `ifconfig` e identfica tu interfaz de red (eth0, enp0s3, wlan0, etc).

![P17i2](/assets/images/Post/P17/P17i2.png)

En las redes locales, la dirección 192.168.0.1 se reserva a menudo para el router o puerta de enlace de la red. El router es el dispositivo que actúa como punto de acceso entre la red local y otras redes, como Internet. 


```shell
nmap -sP 192.168.0.1/24
```

- Ese comando realizará un ping a los hosts activos dentro del rango de red en la red local.

---

### Información útil

Existen un total de 65,535 puertos en un sistema de comunicaciones de red basado en el modelo TCP/IP. Estos puertos se utilizan para facilitar la comunicación y el intercambio de datos entre diferentes aplicaciones y servicios que se ejecutan en un dispositivo conectado a la red, como computadoras, servidores, enrutadores y otros dispositivos de red.

**UDP/TCP**

Los puertos se dividen en dos categorías principales: puertos TCP (Protocolo de Control de Transmisión) y puertos UDP (Protocolo de Datagramas de Usuario). Ambos protocolos son parte del modelo TCP/IP y se utilizan para transferir datos de manera confiable (TCP) o no confiable (UDP) entre dispositivos de red.

[Más info](https://mechitast.github.io/blog/MTCPIP)

**ENUMERACIÓN**

Los puertos TCP y UDP se numeran del 0 al 65,535. Los primeros 1,024 puertos (del 0 al 1023) se conocen como "puertos bien conocidos" o "puertos reservados" y están asignados a servicios y aplicaciones comunes. Algunos ejemplos de puertos bien conocidos son:

- Puerto 80: HTTP (Protocolo de Transferencia de Hipertexto) para servicios web.
- Puerto 443: HTTPS (HTTP Seguro) para servicios web cifrados con SSL/TLS.
- Puerto 22: SSH (Secure Shell) para acceso remoto seguro a servidores.
- Puerto 21: FTP (Protocolo de Transferencia de Archivos) para transferencia de archivos

>Los puertos del 1024 al 49,151 están registrados para servicios y aplicaciones específicas, mientras que los puertos del 49,152 al 65,535 se consideran puertos dinámicos o privados, que pueden ser utilizados temporalmente por aplicaciones o servicios según sea necesario.

---

### Repaso-Handshake

1. **Paso 1: Envío del SYN (Synchronize):**
El cliente envía un paquete SYN al servidor para iniciar una conexión.

2. **Paso 2: Envío del SYN-ACK (Synchronize-Acknowledge):**
 Si el servidor está dispuesto a aceptar la conexión, responde con un paquete SYN-ACK al cliente.

3. **Paso 3: Envío del ACK (Acknowledge):**
Finalmente, el cliente responde con un paquete ACK al servidor, y la conexión se considera "abierta" y lista para transferir datos.

![P17i2](/assets/images/Post/P17/P17i3.png)

---

### Puertos


- **Abierto (Open)**: Indica que el puerto está aceptando conexiones y hay un servicio o aplicación que está escuchando en ese puerto.

- **Cerrado (Closed)**: Indica que el puerto está cerrado y no hay ningún servicio escuchando en ese puerto. Sin embargo, el host remoto ha enviado una respuesta de tipo "RST" (reset) para indicar que el puerto está cerrado.

- **Filtrado (Filtered)**: Indica que el puerto está protegido por un firewall u otro dispositivo de seguridad y Nmap no pudo determinar si el puerto está abierto o cerrado. Esto puede indicar que el puerto está bloqueado o que el host no respondió a los paquetes de sondeo.

- **Abierto/Filtrado (Open/Filtered)**: Indica que Nmap no pudo determinar si el puerto está abierto o filtrado debido a la falta de respuesta del host escaneado.

- **Cerrado/Filtrado (Closed/Filtered)**: Indica que Nmap no pudo determinar si el puerto está cerrado o filtrado debido a la falta de respuesta del host escaneado. El estado "Cerrado" en Nmap puede implicar el envío de paquetes de tipo "RST" por parte del host remoto, lo que indica que el puerto está cerrado y no hay ningún servicio escuchando en ese puerto.

---

## Utilización de Wireshark

Para ver el funcionamiento a detalle de los distintos escaneos utilizarmos Wireshark.

Wireshark es un **analizador de paquetes de red**, una utilidad que captura todo tipo de información que pasa a través de una conexión.

#### 1 Herramienta tcpdump

Herramienta de línea de comandos que permite capturar y mostrar paquetes de red en tiempo real. Es muy útil para el análisis de tráfico y diagnóstico de problemas de red.

**Uso**

primero necesitamos localizar la interfaz de red:

* Para encontrar la interfaz de red adecuada, puedes usar el comando `ip addr show` o `ifconfig`. La interfaz de red suele tener nombres como eth0, enp0s3, wlan0, entre otros.

#### 2 Realizar la captura con tcpdump

El comando debe ser:

```shell
tcpdump -i <interfaz> -w Captura.cap -v
```
- Donde _interfaz_ es el nombre de la interfaz de red que deseas monitorear y _Captura.cap_ es el archivo en el que se guardarán los paquetes capturados.

#### 3 Realizar escaneo 

En este escaneo especifico el puerto a escanear **-p80** del objetivo:

```shell
sudo nmap -sS -p80 192.168.0.22
```
- A si mismo detenemos la captura al momente de que el escaneo finalice puedes presionar `Ctrl + c` en la ventana del terminal donde se está ejecutando TCPDUMP. 

#### Abrir Wireshark

Correcto, después de finalizar la captura, puedes abrir Wireshark y cargar el archivo `Captura.cap`.

**Filtrar en Wireshark**

El filtro `tcp.port == 80` para filtrar solo los paquetes que utilizan el puerto 80 (HTTP). De esta manera, puedes centrarte en los paquetes relacionados con el escaneo del puerto 80.

---

## Tipos de escaneos

### Escaneo-Stealth

Realiza un escaneo Stealth (sigiloso) utilizando TCP SYN.
Nmap enviará paquetes `SYN` para identificar puertos abiertos en los hosts. 

**Abierto**
Si el puerto está abierto, el host debería responder con un paquete SYN-ACK. 

**Cerrado**
Si el puerto está cerrado, el host responderá con un paquete RST (reset). 

```shell
❯ sudo nmap -sS -p80 192.168.0.22    
Starting Nmap 7.93 ( https://nmap.org ) at 2023-07-23 21:52 CST
Nmap scan report for 192.168.0.22
Host is up (0.00024s latency).

PORT   STATE SERVICE
80/tcp open  http
MAC Address: 08:00:27:CA:7D:13 (Oracle VirtualBox virtual NIC)

Nmap done: 1 IP address (1 host up) scanned in 5.74 seconds
```
. 

**Análizando la Captura con Wireshark**

El puerto esta abierto debido a que envío un (SYN) y luego recibo un reconocimiento (SYN-ACK) e inmediatamente se restablece (RST).



![P17i2](/assets/images/Post/P17/sS.png)

**Interpretación general:**

1. El host objetivo respondió con un paquete SYN, ACK, lo que indica que el puerto está abierto y en escucha.
2. El host objetivo respondió con un paquete RST, lo que indica que el puerto está cerrado porque reinicio la conexión.

![P17i2](/assets/images/Post/P17/Escaneo_sS_wireshark.png)

---

### Escaneo-UDP

El escaneo UDP envía paquetes UDP a los puertos y analiza las respuestas para determinar si los puertos están abiertos o filtrados. 

```shell
❯ sudo nmap -sU -p80 192.168.0.15 -Pn -v
Starting Nmap 7.93 ( https://nmap.org ) at 2023-07-23 21:54 CST
Initiating ARP Ping Scan at 21:54
Scanning 192.168.0.15 [1 port]
Completed ARP Ping Scan at 21:54, 0.04s elapsed (1 total hosts)
Initiating UDP Scan at 21:54
Scanning HackforYou (192.168.0.15) [1 port]
Completed UDP Scan at 21:54, 0.25s elapsed (1 total ports)
Nmap scan report for HackforYou (192.168.0.15)
Host is up (0.00015s latency).

PORT   STATE         SERVICE
80/udp open|filtered http
MAC Address: 08:5B:D6:4F:22:0C (Intel Corporate)

Read data files from: /usr/bin/../share/nmap
Nmap done: 1 IP address (1 host up) scanned in 0.41 seconds
           Raw packets sent: 3 (112B) | Rcvd: 1 (28B)
```
.

**Análizando la Captura con Wireshark**

Un resultado común que podrías esperar es la respuesta ICMP "Destination unreachable" con el mensaje "Port unreachable". Esto se debe a que el protocolo UDP no tiene un procedimiento de apretón de manos (handshake) como TCP, lo que hace que la detección de puertos abiertos en escaneos UDP sea más difícil.

![P17i2](/assets/images/Post/P17/su_wireshark.png)

---

### Escaneo-TCP-Connect

Nmap intentará establecer una conexión completa con los puertos para determinar si están abiertos o cerrados.

**Puerto Abierto**
Si el puerto está abierto y escuchando, se establecerá una conexión y Nmap cerrará la conexión de manera ordenada.

**Puerto Cerrado**
Si el puerto está cerrado, el sistema enviará un paquete de respuesta de "conn-refused" (conexión rechazada) indicando que el puerto está cerrado.

```shell
❯ sudo nmap -sT -p80 192.168.0.22 -Pn -v
Starting Nmap 7.93 ( https://nmap.org ) at 2023-07-23 21:10 CST
Initiating Parallel DNS resolution of 1 host. at 21:10
Completed Parallel DNS resolution of 1 host. at 21:10, 5.61s elapsed
Initiating Connect Scan at 21:10
Scanning 192.168.0.22 [1 port]
Discovered open port 80/tcp on 192.168.0.22
Completed Connect Scan at 21:10, 0.00s elapsed (1 total ports)
Nmap scan report for 192.168.0.22
Host is up (0.00041s latency).

PORT   STATE SERVICE
80/tcp open  http

Read data files from: /usr/bin/../share/nmap
Nmap done: 1 IP address (1 host up) scanned in 5.64 seconds
```
.

**Análizando la Captura con Wireshark**

Esta es una conexión completa un apretón de manos (handshake) y al final enviamos un reincio.

- Pepito - Hola Vera estas ahi?
- Vera   - Si estoy aqui? 
- Pepito - Ok
- Vera   - Bye

![P17i2](/assets/images/Post/P17/sT_Wireshark.png)

---

### Escaneo-ACK

Utilizado para realizar un escaneo de envío de paquete de análisis (ACK Scan) en Nmap. Este tipo de escaneo aprovecha el comportamiento del protocolo TCP para identificar el estado de los puertos en un host objetivo.

**Funcionamiento:**
Cuando Nmap realiza un escaneo ACK (`-sA`), envía paquetes con el indicador ACK activado a los puertos específicos del host objetivo.

**Puerto Filtrado**
Si el puerto está filtrado por un firewall o dispositivo de seguridad, el host responderá con un paquete de tipo "reset" (RST), lo que indica que el puerto está filtrado.

**Puerto Cerrado o Abierto**
Si el puerto está cerrado o abierto, el host simplemente ignorará el paquete ACK y no enviará ninguna respuesta, lo que dificulta la determinación del estado real del puerto mediante este tipo de escaneo.

```shell
❯ sudo nmap -sA -p80 192.168.0.22 -v    
[sudo] password for frijol: 
Starting Nmap 7.93 ( https://nmap.org ) at 2023-07-23 21:44 CST
Initiating ARP Ping Scan at 21:44
Scanning 192.168.0.22 [1 port]
Completed ARP Ping Scan at 21:44, 0.02s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 21:44
Completed Parallel DNS resolution of 1 host. at 21:44, 5.52s elapsed
Initiating ACK Scan at 21:44
Scanning 192.168.0.22 [1 port]
Completed ACK Scan at 21:44, 0.01s elapsed (1 total ports)
Nmap scan report for 192.168.0.22
Host is up (0.00022s latency).

PORT   STATE      SERVICE
80/tcp unfiltered http
MAC Address: 08:00:27:CA:7D:13 (Oracle VirtualBox virtual NIC)

Read data files from: /usr/bin/../share/nmap
Nmap done: 1 IP address (1 host up) scanned in 5.65 seconds
           Raw packets sent: 2 (68B) | Rcvd: 2 (68B)
```
.

**Análizando la Captura con Wireshark**


Si el puerto está filtrado por un firewall o dispositivo de seguridad, el host responderá con un paquete de tipo "reset" (RST), lo que indica que el puerto está filtrado.

![P17i2](/assets/images/Post/P17/sA_Wireshark.png)


---

### Resumen escaneos utilizados

![P17i2](/assets/images/Post/P17/P17i4.png)

