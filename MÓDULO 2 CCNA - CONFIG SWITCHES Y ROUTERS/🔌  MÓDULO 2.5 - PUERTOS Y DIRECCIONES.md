
---
Las direcciones IP son fundamentales para identificar y permitir la comunicación entre dispositivos finales (PCs, impresoras, servidores, etc.) en una red. Una dirección **IPv4** se representa mediante cuatro números (0-255) y trabaja en conjunto con una **máscara de subred**, la cual permite diferenciar qué parte de la dirección identifica a la red y qué parte al dispositivo específico. Finalmente, el **gateway predeterminado** actúa como la "puerta de salida", siendo la dirección del router que el host utiliza para enviar información hacia redes remotas o Internet.

---

|**Elemento**|**Función Principal**|
|---|---|
|**Dirección IP**|Identificador único de cada terminal en la red.|
|**Máscara de Subred**|Determina a qué subred pertenece el dispositivo (separa red de host).|
|**Gateway Predeterminado**|Dirección del router para acceder a otras redes o a la nube.|
|**IPv6**|Versión más moderna que está reemplazando gradualmente a IPv4.|

---

Las comunicaciones de red se realizan a través de interfaces físicas que conectan dispositivos mediante diversos medios, como cables de cobre, fibra óptica o señales inalámbricas, cuya elección depende de la distancia, velocidad y costo requeridos. En el caso de los switches de capa 2, aunque sus puertos físicos no procesan direcciones IP, se utilizan las **Interfaces Virtuales de Switch (SVI)**, como la **VLAN1** predeterminada, para asignar una dirección IP al equipo; esto permite administrar el switch de forma remota sin afectar su funcionamiento básico de envío de datos.

![](../IMG/Interfaz%20y%20pueto.png)

**Medios de Red y sus Diferencias**

| **Medio de Red**                 | **Características Principales**                                             |
| -------------------------------- | --------------------------------------------------------------------------- |
| **Cobre (Par trenzado/Coaxial)** | Económico y común en LANs, pero limitado por la distancia e interferencias. |
| **Fibra Óptica**                 | Alta velocidad y grandes distancias; inmune a interferencias eléctricas.    |
| **Inalámbrico (Wireless)**       | Máxima movilidad, pero sensible al entorno y obstáculos físicos.            |
### Concepto Clave: SVI (Interfaz Virtual de Switch)

**¿Qué es?**: Una interfaz lógica creada en el software del switch, no un puerto físico.

**VLAN1**: Es la interfaz virtual que viene por defecto en los switches Cisco.

**Propósito**: Se le asigna una dirección IP únicamente para poder **entrar al switch remotamente** (vía SSH o Telnet) y gestionarlo a través de la red.

---

**Configuración de Dispositivos Finales** La asignación de direcciones IP en PCs o impresoras puede ser **manual (estática)**, donde el administrador introduce los datos uno a uno, o **automática**, utilizando el protocolo DHCP para que el dispositivo reciba su configuración de red sin intervención humana.

**Verificación en el Host** Es fundamental comprobar que la configuración es correcta mediante herramientas del sistema operativo. En Windows, se utiliza el comando `ipconfig` en el símbolo del sistema para verificar la dirección IPv4, la máscara de subred y el gateway predeterminado asignados al equipo.

**Interfaz Virtual de Switch (SVI)** Para gestionar un switch de forma remota, se debe configurar una **SVI (Switch Virtual Interface)**. Al asignar una dirección IP a la interfaz lógica (comúnmente la VLAN 1) y activarla con el comando `no shutdown`, el switch se vuelve accesible a través de la red.

**Conectividad Básica** El paso final es la implementación y validación de la conectividad. Esto implica asegurar que todos los elementos (direcciones IP, máscaras y cables) permitan que los dispositivos finales y los de red se "vean" entre sí, completando así la estructura funcional de la red local.

**Configuración de interfaz virtual de switch.**

![](../IMG/interfaz%20virtual%20de%20switch.png)

