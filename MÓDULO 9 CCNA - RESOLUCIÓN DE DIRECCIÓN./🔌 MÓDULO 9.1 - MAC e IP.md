
---

#### Resolución y Tipos de Direcciones en una LAN Ethernet

Para que la comunicación sea efectiva en una red, a menudo se presenta una situación donde un host origen conoce la dirección IP de destino, pero desconoce su dirección física. En este punto, la **resolución de direcciones** (como ARP en IPv4 o _Neighbor Discovery_ en IPv6) se vuelve un proceso crítico para poder armar y enviar la trama de datos.

En una red LAN Ethernet, todo dispositivo operativo cuenta con dos identificadores primarios:

**Dirección física (Dirección MAC):** Pertenece a la Capa 2 (Enlace de datos). Su función exclusiva es permitir la comunicación directa de tarjeta de red a tarjeta de red (NIC a NIC) dentro del **mismo segmento de red local**.

**Dirección lógica (Dirección IP):** Pertenece a la Capa 3 (Red). Es responsable del enrutamiento de extremo a extremo, guiando el paquete desde el origen original hasta el destino final, independientemente de si el receptor está en la red local o en una red remota.

**Mecanismo de entrega local:** Las direcciones MAC se utilizan para entregar la trama (que contiene el paquete IP encapsulado) en el medio físico. Si el host emisor determina que la dirección IP de destino se encuentra en su propia red local, utilizará directamente la dirección MAC de ese dispositivo de destino para realizar la entrega final de la trama.

Ejemplo de representaciones MAC simplificadas.

![](../IMG/MODULO9IMG/Ejemplo%20de%20representaciones%20MAC%20simplificadas.png)

---

**Destino de una red remota**

Cuando la dirección IP de destino (IPv4 ó IPv6) está en una red remota, la dirección MAC será la dirección gateway predeterminada del host (es decir, la interfaz del router).

==Representación de dirección MAC simplificada.==

![](../IMG/MODULO9IMG/Representación%20de%20dirección%20MAC%20simplificada.png)

**El problema:** PC1 se da cuenta de que PC2 está en una red diferente. Por lo tanto, no puede enviarle la información directamente de tarjeta de red a tarjeta de red. Debe enviarla a su puerta de enlace o _gateway_ (el Router R1).

**Armado de la trama (El cuadro de la izquierda):**

**Capa 3 (Direcciones IP):** PC1 pone su propia IP como origen y la IP de PC2 como destino. Estas direcciones lógicas de extremo a extremo **no cambian**.

**Capa 2 (Direcciones MAC):** Como el paquete debe ir primero al router para salir de la red local, PC1 pone su propia MAC como origen (`aa-aa-aa`) y **la MAC del Router R1** como destino (`bb-bb-bb`).

**El trabajo del Router (R1):** Cuando R1 recibe esa trama, rompe la "envoltura" de las direcciones MAC para poder leer la IP de destino. Al ver que va hacia la red `10.1.1.0/24`, el router crea una _nueva_ envoltura MAC (ahora usando `cc-cc-cc` como origen y `dd-dd-dd` como destino) para pasarle el paquete al siguiente router (R2), acercándolo a su destino final.

==Básicamente: Las IP te dicen el destino final del viaje, mientras que las MAC solo te llevan de una "parada" a la siguiente.==

---

En nuestro ejemplo, R1 encapsularía  el paquete con una nueva información de dirección de Capa 2 como se muestra en la imagen.

![](../IMG/MODULO9IMG/R1%20encapsularía.png)

La nueva dirección MAC de destino sería la de la interfaz R2 G0/0/1 y la nueva dirección MAC de origen sería la de la interfaz R1 G0/0/1.

![](../IMG/MODULO9IMG/Saltos%20de%20la%20MAC.png)

----

