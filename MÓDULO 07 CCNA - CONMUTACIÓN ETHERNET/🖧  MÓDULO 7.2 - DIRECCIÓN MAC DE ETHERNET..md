
---

### Dirección MAC y hexadecimal.

**Representación:** Mientras que IPv4 usa decimal y binario, las direcciones **IPv6 y MAC Ethernet** utilizan el sistema **hexadecimal (Base 16)**, el cual abarca los números del `0` al `9` y las letras de la `A` a la `F`.

Un solo dígito hexadecimal representa exactamente **4 bits binarios** (un _nibble_).

**Estructura MAC:** Una dirección MAC consta de **48 bits binarios**, pero gracias al sistema hexadecimal, se puede compactar y expresar de forma sencilla usando únicamente **12 dígitos hexadecimales**.

**Equivalentes decimales y binarios a los valores hexadecimales del 0 al F.**

![](../IMG/MÓDULO7IMG/Equivalentes%20decimales%20y%20binarios%20a%20los%20valores%20hexadecimales%20del%200%20al%20F..png)

Dado que 8 bits (un byte) es un método de agrupación binaria común, los números binarios del 00000000 al 11111111 se pueden representar en hexadecimal como el rango del 00 al FF.

---

**Equivalentes decimales, binarios y hexadecimales seleccionados**

![](../IMG/MÓDULO7IMG/Equivalentes%20decimales,%20binarios%20y%20hexadecimales%20seleccionados.png)

Cuando se usa hexadecimal, los ceros iniciales siempre se muestran para completar la representación de 8 bits.

Los números hexadecimales suelen ser representados por el valor precedido por **0x** (por ejemplo, 0x73) para distinguir entre valores decimales y hexadecimales en la documentación.

El hexadecimal también puede estar representado por un subíndice 16, o el número hexadecimal seguido de una H (por ejemplo, 73H).

----

En una LAN Ethernet, las direcciones MAC identifican de forma única a los dispositivos físicos (NIC) de origen y destino dentro del mismo segmento local de la Capa 2. Esta dirección consta de **48 bits**, lo que equivale exactamente a **6 bytes** de longitud, y se representa de forma sencilla mediante **12 dígitos hexadecimales**.

![](../IMG/MÓDULO7IMG/Identificador%20MAC.png)

==Todas las direcciones MAC deben ser únicas para el dispositivo Ethernet o la interfaz Ethernet.== Para garantizar esto, todos los proveedores que venden dispositivos Ethernet deben registrarse con el IEEE para obtener un código hexadecimal único de 6 (es decir, 24 bits o 3 bytes) denominado identificador único de organización (OUI).

Cuando un proveedor asigna una dirección MAC a un dispositivo o interfaz Ethernet, el proveedor debe hacer lo siguiente:

- Utilice su OUI asignado como los primeros 6 dígitos hexadecimales.
- Asigne un valor único en los últimos 6 dígitos hexadecimales.

Por lo tanto, una dirección MAC Ethernet consiste en un código OUI de proveedor hexadecimal 6 seguido de un valor asignado por el proveedor hexadecimal 6, como se muestra en la figura.

![](../IMG/MÓDULO7IMG/Proveedor%20MAC%20único.png)

Por ejemplo, suponga que Cisco necesita asignar una dirección MAC única a un nuevo dispositivo. El IEEE ha asignado a Cisco un OUI de **00-60-2F**. Cisco configuraría entonces el dispositivo con un código de proveedor único como **3A-07-BC**. Por lo tanto, la dirección MAC Ethernet de ese dispositivo sería **00-60-2F-3A-07-BC.**

Es responsabilidad del proveedor asegurarse de que ninguno de sus dispositivos tenga asignada la misma dirección MAC. Sin embargo, es posible que existan direcciones MAC duplicadas debido a errores cometidos durante la fabricación, errores cometidos en algunos métodos de implementación de máquinas virtuales o modificaciones realizadas con una de varias herramientas de software. En cualquier caso, será necesario modificar la dirección MAC con una nueva NIC o realizar modificaciones a través del software.

---

**Procesamiento de tramas**

A veces, la dirección MAC se conoce como una dirección grabada (BIA) porque la dirección está codificada en la memoria de solo lectura (ROM) en la NIC. Es decir que la dirección está codificada en el chip de la ROM de manera permanente.

**Nota:** ==En los sistemas operativos de PC y NIC modernos, es posible cambiar la dirección MAC en el software. Esto es útil cuando se intenta acceder a una red filtrada por BIA. En consecuencia, el filtrado o el control de tráfico basado en la dirección MAC ya no son tan seguros.==

Cuando la computadora se inicia, la NIC copia su dirección MAC de la ROM a la RAM. Cuando un dispositivo reenvía un mensaje a una red Ethernet, el encabezado Ethernet incluye estos:

**Dirección MAC de origen** - Esta es la dirección MAC de la NIC del dispositivo origen.

**Dirección MAC de destino** - Esta es la dirección MAC de la NIC del dispositivo de destino.

**Nota:** Las NIC de Ethernet también aceptarán tramas si la dirección MAC de destino es una transmisión o un grupo multicast del que es miembro el host.

Cualquier dispositivo que sea la origen o destino de una trama Ethernet, tendrá una NIC Ethernet y, por lo tanto, una dirección MAC. Esto incluye estaciones de trabajo, servidores, impresoras, dispositivos móviles y routers.

---

**Dirección MAC de unicast**

Una dirección MAC de unicast es la dirección única que se utiliza cuando se envía una trama desde un único dispositivo de transmisión a un único dispositivo de destino.

![](../IMG/MÓDULO7IMG/Dirección%20MAC%20de%20unicast.png)

==El proceso que utiliza un host de origen para determinar la dirección MAC de destino asociada con una dirección IPv4 se conoce como Protocolo de resolución de direcciones (ARP). El proceso que utiliza un host de origen para determinar la dirección MAC de destino asociada con una dirección IPv6 se conoce como Neighbor Discovery (ND).==

**Nota:** La dirección MAC de origen siempre debe unicast.

---

**Dirección MAC broadcast**

Cada dispositivo de la LAN Ethernet recibe y procesa una trama de broadcast Ethernet. Las características de una transmisión Ethernet son las siguientes:

**Tiene una dirección MAC de destino de FF-FF-FF-FF-FF-FF en hexadecimal (48 unidades en binario).**

**Está inundado todos los puertos del switch Ethernet excepto el puerto entrante.**

**No es reenviado por un router.**

Si los datos encapsulados son un paquete broadcast IPv4, esto significa que el paquete contiene una dirección IPv4 de destino que tiene todos los (1s) en la parte del host. Esta numeración en la dirección significa que todos los hosts de esa red local (dominio de broadcast) recibirán y procesarán el paquete.

![](../IMG/MÓDULO7IMG/Dirección%20MAC%20broadcast.png)

Sin embargo, no todas las transmisiones Ethernet llevan un paquete de broadcast IPv4. Por ejemplo, las solicitudes ARP no utilizan IPv4, pero el mensaje ARP se envía como un broadcast Ethernet.

---

**Dirección MAC de multicast**

==Una trama de multicast de Ethernet es recibida y procesada por un grupo de dispositivos en la LAN de Ethernet que pertenecen al mismo grupo de multicast.==

**Caracteristicas**

Hay una dirección MAC de destino 01-00-5E cuando los datos encapsulados son un paquete de multicast IPv4 y una dirección MAC de destino de 33-33 cuando los datos encapsulados son un paquete de multicast IPv6.

Existen otras direcciones MAC de destino de multicast reservadas para cuando los datos encapsulados no son IP, como Spanning Tree Protocol (STP) y Link Layer Discovery Protocol (LLDP).

Se inundan todos los puertos del switch Ethernet excepto el puerto entrante, a menos que el switch esté configurado para la indagación de multicast.

No es reenviado por un router, a menos que el router esté configurado para enrutar paquetes de multicast.

Las direcciones de multicast representan a un grupo específico de hosts receptores. Por esta naturaleza, **solo pueden utilizarse como destino** de un paquete; la dirección de origen siempre tiene que ser una dirección de unicast individual.

**Rangos IP de Multicast:**

**IPv4:** `224.0.0.0` a `239.255.255.255`

**IPv6:** Comienza estrictamente con el prefijo `ff00::/8`

**Mapeo de Capa 2:** Para poder entregar las tramas dentro de la red local, cada dirección IP de multicast requiere una **dirección MAC de multicast correspondiente**, la cual se genera de forma automática asociando y heredando parte de la información de direccionamiento de la propia dirección IP (v4 o v6).

![](../IMG/MÓDULO7IMG/Dirección%20MAC%20de%20multicast.png)

Los protocolos de enrutamiento y otros protocolos de red utilizan direccionamiento multicast. Las aplicaciones como el software de vídeo e imágenes también pueden utilizar direccionamiento multicast, aunque las aplicaciones multicast no son tan comunes.

---

