
---

### Modelo cliente - servidor:

El modelo cliente-servidor es la arquitectura fundamental que permite el funcionamiento de la mayoría de los servicios en Internet. En este modelo, la comunicación se divide según los roles de los dispositivos involucrados en la capa de aplicación:

**Cliente:** Es el dispositivo (hardware y software) que inicia la comunicación al realizar una solicitud de datos o servicios. Es la interfaz que utiliza el usuario final para acceder a recursos externos.

**Servidor:** Es el dispositivo que recibe la solicitud, la procesa y responde enviando los flujos de datos requeridos al cliente.

### Conceptos clave del intercambio:

**Formato de mensajes:** Los protocolos de capa de aplicación dictan cómo deben estructurarse las solicitudes y las respuestas para que ambos dispositivos se entiendan.

**Procesos adicionales:** El intercambio no siempre es solo de datos; a menudo requiere autenticación del usuario (para verificar permisos) e identificación específica de los archivos solicitados.

**Direcciones de transferencia:**

**Carga (Upload):** Transferencia de datos desde el cliente hacia el servidor.

**Descarga (Download):** Transferencia de datos desde el servidor hacia el cliente.

Un ejemplo claro es el **correo electrónico**: cuando tu PC solicita correos nuevos, actúa como cliente enviando la petición al servidor de tu ISP. El servidor procesa la solicitud, busca tus mensajes y te los envía (descarga) para que los leas.

![](../IMG/MODULO14IMG/Cliente%20-%20servidor.png)

---

### Redes entre pares:

En el modelo de red entre pares (P2P), los dispositivos acceden a datos y recursos, como archivos o impresoras, sin depender de un servidor dedicado. En esta arquitectura, cualquier terminal conectado puede funcionar simultáneamente tanto como cliente como servidor, estableciendo su función según la solicitud específica de la transacción. Además de compartir recursos físicos o datos, este modelo permite a los usuarios realizar otras actividades como jugar en red o compartir una conexión a Internet, donde cada dispositivo se considera igual en el proceso de comunicación.


![](../IMG/MODULO14IMG/Redes%20entre%20pares.png)

---
### Peer to peer applications:

Las aplicaciones P2P permiten una comunicación descentralizada donde cada dispositivo actúa simultáneamente como cliente y servidor, ejecutando una interfaz de usuario y un servicio en segundo plano para compartir recursos.

Existen principalmente dos formas en las que operan:

**Pura:** El intercambio de recursos y la búsqueda de ubicaciones están totalmente descentralizados entre los nodos.

**Híbrida:** Combina la descentralización del intercambio de archivos con un **directorio centralizado** (servidor de índice). En este modelo, los dispositivos consultan primero a este servidor para localizar dónde está almacenado un recurso específico y luego realizan la transferencia directamente entre sí.

![](../IMG/MODULO14IMG/Peer%20to%20peer%20applications.png)

---

### Aplicaciones P2P comunes:

Las aplicaciones P2P permiten que cualquier equipo en la red actúe como cliente y servidor de forma simultánea. 

**BitTorrent:** Es uno de los protocolos más utilizados para la distribución de archivos de gran tamaño mediante la fragmentación.

**Conexión directa (Direct Connect):** Permite a los usuarios compartir archivos directamente dentro de comunidades o "hubs" específicos.

**eDonkey:** Un protocolo clásico para el intercambio de archivos que utilizaba servidores de indexación.

**Freenet:** Enfocado en la descentralización y el anonimato de la información.

### El Protocolo Gnutella

Muchas de estas herramientas se basan en el protocolo **Gnutella**, que permite a los usuarios buscar y acceder a recursos compartidos por otros nodos en Internet de manera descentralizada.

Varios clientes populares utilizan este protocolo para conectar a los usuarios con la red:

**µTorrent** y **BitComet** (orientados principalmente a torrents).

**DC++** (basado en Direct Connect).

**Deluge** (cliente ligero para BitTorrent).

**eMule** (evolución del protocolo eDonkey).

![](../IMG/MODULO14IMG/Aplicaciones%20P2P%20comunes.png)

----

