
## Conjuntos de protocolos de red:

![](../IMG/Suit%20de%20protocolos.jpg)

Un conjunto de protocolos es un grupo de protocolos interrelacionados que trabajan juntos para permitir la comunicación. Se visualizan como una pila de protocolos (stack), donde las capas superiores dependen de los servicios de las capas inferiores.

#### Los 4 Conjuntos Principales:

TCP/IP: El conjunto de protocolos estándar de la industria actual y el utilizado en Internet.

ISO (Modelo OSI): Aunque se usa principalmente como modelo de referencia, tiene su propio conjunto de protocolos desarrollado por la ISO.

AppleTalk: Un conjunto de protocolos patentado por Apple (obsoleto).

Novell NetWare: Un conjunto de protocolos patentado desarrollado por Novell (obsoleto). 

---

![](../IMG/Capas%20y%20Protocolos%20del%20Conjunto%20TCP-IP.jpg)

### Capas TCP/IP

![](../IMG/Conjunto%20de%20TCPIP.jpg)

Para que un mensaje viaje, cada capa tiene sus propios "especialistas".

#### La capa de Aplicación (El origen) , basicamente es donde se genera el dato que el usuario quiere enviar.

**HTTP / HTTPS**: El protocolo para navegar por la web.

**DNS:** Traduce nombres (google.com) a direcciones IP.

**DHCP:** Asigna direcciones IP automáticamente a los dispositivos.

**FTP:** Protocolo de transferencia de archvos, le permite a los usuarios tranferir archivos de un host a otro a travéz de la red.

**SLAAC:** Autoconfiguración sin estado, basicamente es un metodo que le permite a los  dispositivos obtener su información de direccionamiento IPv6 sin utilizar un servidor  DHCPv6.

**Protocolos de Correo**

**SMTP (Simple Mail Transfer Protocol) :** Se encarga del envío de correo (cliente a servidor o entre servidores).

**POP3 (Post Office Protocol v3) :** Descarga de correos del servidor al dispositivo local, funciona con si fuera un buzón.

**IMAP (Internet Message Access Protocol) :** Acceso y gestión de correos almacenados en el servidor.

**Transferencia de Archivos y Acceso Remoto**

**SFTP (SSH FTP):** Es básicamente el protocolo FTP pero "metido" dentro de un túnel seguro de SSH. Combina la gestión de archivos con el cifrado fuerte.

**SSH ( Secure shell ):** Inicio de sesión remoto seguro a la línea de comandos de un dispositivo.

**TFTP (Trivial FTP) :** Transferencia de archivos simple, sin conexión y con baja sobrecarga (mejor esfuerzo).

**Servicios Web**

 **HTTP:** Reglas para intercambiar archivos multimedia en la web.

**HTTPS:** Versión segura de HTTP que cifra el intercambio de datos.

**REST:** Uso de APIs y solicitudes HTTP para crear aplicaciones web.


#### Capa de Transporte (El cartero) Se encarga de que los datos lleguen de forma ordenada y completa.

**TCP (Transmission Control Protocol):** Es el protocolo "seguro". Este  divide los datos en segmentos y confirma que el receptor los recibió. Si algo se pierde, lo reenvía.

**UDP (User Datagram Protocol): Es el protocolo "rápido"**. Envía los datos sin confirmar la recepción. Ideal para streaming o juegos online donde la velocidad importa más que un error mínimo.

#### Capa de Internet (La brújula) Aquí es donde se decide la ruta que tomarán los datos.

**IP (IPv4 e IPv6)**: Se encarga del direccionamiento. Le pone la "etiqueta" de origen y destino al paquete.

**NAT** Traduce las direcciones IPv4 de una red privada en direcciones IPv4 públicas globalmente únicas.

**ICMP**: Se usa para pruebas y mensajes de error (como el famoso comando ping).

**ICMPv4:** Protocolo de mensajes de control para IPv4 que informa sobre el éxito o fracaso en el envío de paquetes (ej. "Destino inalcanzable").

**ICMPv6:** Versión actualizada para IPv6 que incluye todas las funciones de ICMPv4, pero añade capacidades de detección de errores y mensajería mucho más robustas.
    
**ICMPv6 ND (Neighbor Discovery):** Es el mecanismo que permite a los dispositivos en una misma red IPv6 comunicarse entre sí. Sustituye funciones que antes hacían otros protocolos en IPv4 (como ARP).

#### Capa de Acceso a la Red (El camino físico) Es la que pone los datos sobre el medio físico (cable o aire).

Ethernet: El estándar para conexiones por cable.

WLAN (Wi-Fi): El estándar para conexiones inalámbricas.

ARP (Address Resolution Protocol): Traduce una dirección IP a una dirección física (MAC).



---
#### Ejemplo de protocolo TCP/IP

- **Alcance de TCP/IP:** Los protocolos TCP/IP operan específicamente en las capas de **Aplicación**, **Transporte** e **Internet**.
    
- **Capa de Acceso a la Red:**
    
    - No contiene protocolos de la suite TCP/IP.
        
    - Utiliza protocolos LAN como **Ethernet** y **WLAN** (inalámbrica).
        
    - **Responsabilidad:** Se encarga de la entrega física de los paquetes IP a través de los medios.
        
- **Ejemplo de Comunicación (Web):**
    
    - **Aplicación:** HTTP.
        
    - **Transporte:** TCP.
        
    - **Internet:** IP.
        
    - **Acceso a la Red:** Ethernet (o estándares inalámbricos como WLAN/celular).

---

