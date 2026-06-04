
---

El **gateway predeterminado** (puerta de enlace) es la dirección IP de la interfaz del router conectada a la red local del host. Para que funcione, tanto el host como la interfaz del router deben pertenecer a la misma red. El dispositivo **solo utiliza** este gateway cuando necesita enviar paquetes a un equipo que se encuentra en una red distinta.

**Ejemplo de la topología:** Si un router interconecta dos redes LAN, su interfaz **G0/0** se conecta a la red **192.168.10.0** y su interfaz **G0/1** a la red **192.168.11.0**. Los hosts de cada segmento usarán la IP de su respectiva interfaz como gateway. Sin embargo, si PC1 y PC2 están en la misma red y desean comunicarse entre sí, el paquete viaja directamente a través del switch local y **no** se utiliza el gateway predeterminado.

![](../IMG/MODULO10IMG/Ejemplo%20de%20la%20topología.png)

---
**Comunicación hacia una Red Remota**

Cuando un dispositivo necesita enviar información a una red distinta (por ejemplo, de **PC1** a **PC3**), el flujo de comunicación ocurre así:

1 - **Envío al Gateway:** PC1 arma el paquete con la IP final de PC3, pero como no están en la misma red local, envía físicamente la trama a su puerta de enlace predeterminada (la interfaz **G0/0/0** del router **R1**).

2 - **Decisión de Enrutamiento:** El router **R1** recibe el paquete, lee la IP de destino y consulta su **tabla de enrutamiento** para descubrir por qué camino debe enviarlo.

3 - **Reenvío:** Una vez identificada la ruta, R1 saca el paquete por la interfaz de salida correspondiente (G0/0/1 en este caso) para que llegue con éxito a PC3.

---

> **Nota:** Esta misma lógica y proceso de usar el router local como "puerta de salida" se aplica exactamente igual para las redes que operan con IPv6.

---

![](../IMG/MODULO10IMG/Comunicación%20hacia%20una%20Red%20Remota.png)

El mismo proceso ocurriría en una red IPv6, aunque esto no se muestra en la topología. Los dispositivos usarían la dirección IPv6 del enrutador local como puerta de enlace predeterminada.

---
**Gateway Predeterminado para un Switch**

Por naturaleza, un switch de Capa 2 no necesita una dirección IP para realizar su trabajo básico de reenviar tramas. Sin embargo, configurar una IP es obligatorio si necesitas **administrar el equipo de forma remota** (por ejemplo, vía SSH).

Para que la administración remota funcione correctamente, debes configurar dos elementos:

1 - **SVI (Interfaz Virtual de Switch):** Debes asignarle una dirección IPv4 y una máscara de subred para poder acceder al switch desde la misma red local.

2 - **Gateway Predeterminado:** Si vas a administrar el switch desde una **red distinta** (remota), el switch necesita saber por dónde enviar las respuestas de vuelta. Para eso requiere la IP de su puerta de enlace (la interfaz del router local).

**Comando de Configuración:** Para establecer el gateway predeterminado en un switch, ingresa al modo de configuración global y utiliza el siguiente comando, indicando la IP del router conectado a la LAN:

`ip default-gateway <dirección_IP_del_router>`

![](../IMG/MODULO10IMG/Gateway%20Predeterminado%20para%20un%20Switch.png)

**Administración remota en IPv4:** Para conectarte a un switch desde otra red (ej. por SSH), es **obligatorio** configurarle el gateway predeterminado a mano. Sin él, el switch recibe tu mensaje pero no sabe por dónde enviar la respuesta.

**La ventaja de IPv6:** **No requiere configuración manual** del gateway. El switch lo aprende de forma 100% automática escuchando los mensajes RA (_Router Advertisement_) de ICMPv6 que envía el router.

**Nota:** Los paquetes que se originan en servidores conectados al switch ya deben crearse con la dirección de gateway predeterminado configurada en el sistema operativo de su servidor.

---

