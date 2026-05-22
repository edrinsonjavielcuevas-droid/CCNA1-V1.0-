
---

**Fundamentos de switches**

Si un switch acaba de reenviar cada trama que recibió todos los puertos, su red estaría tan congestionada que probablemente se detendría por completo. Por eso debemos saber como estos distribuyen su carga.

Un switch Ethernet de capa 2 usa direcciones MAC de capa 2 para tomar decisiones de reenvío. No tiene conocimiento de los datos (protocolo) que se transportan en la porción de datos de la trama, como un paquete IPv4, un mensaje ARP o un paquete IPv6 ND. El switch toma sus decisiones de reenvío basándose únicamente en las direcciones MAC Ethernet de capa 2.

Un switch Ethernet examina su tabla de direcciones MAC para tomar una decisión de reenvío para cada trama, a diferencia de los hubs Ethernet heredados que repiten bits en todos los puertos excepto el puerto entrante.

**Nota:** Las direcciones MAC se acortan a lo largo de este tema con fines de demostración.

![](Fundamentos%20de%20switches.png)

**Nota:** En ocasiones, la tabla de direcciones MAC se denomina tabla de memoria de contenido direccionable (CAM). Aunque el término “tabla CAM” es bastante común, en este curso nos referiremos a ella como “tabla de direcciones MAC”.

---

**Switch, Aprendiendo**

El switch arma la tabla de direcciones MAC de manera dinámica después de examinar la dirección MAC de origen de las tramas recibidas en un puerto.El switch reenvía las tramas después de buscar una coincidencia entre la dirección MAC de destino de la trama y una entrada de la tabla de direcciones MAC.

**Examinar la dirección MAC de Origen ( APRENDER )**

El switch examina la **dirección MAC de origen** de cada trama que ingresa para construir y mantener su tabla de direcciones MAC de forma dinámica. El proceso sigue estas reglas de hardware:

**Si la MAC no existe:** El switch la registra inmediatamente en la tabla vinculándola al número de puerto físico por el que entró.

**Si la MAC ya existe:** El switch refresca su temporizador de envejecimiento (_aging time_). Por defecto, la mayoría de los switches retienen una entrada inactiva durante **5 minutos** antes de borrarla.

**Si la MAC cambió de puerto:** Si la dirección ya existía pero aparece en un puerto diferente, el switch la trata como una actualización inmediata: borra el registro viejo y guarda la MAC asociada al puerto más reciente.

![](Examinar%20la%20dirección%20MAC%20de%20Origen%20(%20APRENDER%20).png)

----

**Reenviando**

Cuando una trama entra al switch, este lee la **dirección MAC de destino** para decidir cómo y por dónde transmitirla, aplicando tres reglas de hardware según el estado de su tabla:

**MAC de destino encontrada (Unicast conocida):** Si la dirección ya está registrada en la tabla, el switch conmuta la trama **únicamente por el puerto físico específico** asociado a esa MAC, evitando saturar el resto de la red.

**MAC de destino NO encontrada (Unicast desconocida):** Si la dirección es individual pero no aparece en la tabla, el switch se ve obligado a realizar una inundación (**Flooding**), reenviando la trama por **todos los puertos activos**, excepto por el puerto por donde ingresó originalmente.

**Tramas Broadcast o Multicast:** Si el destino es una dirección de difusión (`FFFF.FFFF.FFFF`) o de grupo, el switch ejecuta la misma inundación automática, enviándola por todos los puertos menos el de origen.

![](Reenviando.png)

---

**Filtrado de tramas** 

A medida que un switch recibe tramas de diferentes dispositivos, puede completar la tabla de direcciones MAC examinando la dirección MAC de cada trama. Cuando la tabla de direcciones MAC del switch contiene la dirección MAC de destino, puede filtrar la trama y reenviar un solo puerto.

**PC-D a Switch:**

En la figura, PC-D responde a PC-A. El switch ve la dirección MAC de PC-D en la trama entrante en el puerto 4. A continuación, el switch coloca la dirección MAC de PC-D en la tabla de direcciones MAC asociada con el puerto 4.

![](PC-D%20a%20Switch.png)

---

**Switch a PC-A**

A continuación, dado que el switch tiene la dirección MAC de destino para la PC-A en la Tabla de direcciones MAC, enviará la trama solo al puerto 1, como se muestra en la figura.

![](Switch%20a%20PC-A.png)

---

**PC-A a Switch PC-D**

A continuación, PC-A envía otro trama a PC-D como se muestra en la figura. La tabla de direcciones MAC ya contiene la dirección MAC para PC-A; por lo tanto, el temporizador de actualización de cinco minutos para esa entrada se restablece. Luego, debido a que la tabla de switch contiene la dirección MAC de destino para PC-D, envía la trama solo por el puerto 4.

![](PC-A%20a%20Switch%20PC-D.png)

---
