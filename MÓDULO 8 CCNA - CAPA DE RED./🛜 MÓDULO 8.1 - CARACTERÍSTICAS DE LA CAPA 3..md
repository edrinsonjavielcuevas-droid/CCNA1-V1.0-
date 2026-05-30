
---

La Capa 3 (Capa de Red) sirve para que los dispositivos finales se manden datos entre diferentes redes. Para lograrlo, usa principalmente **IPv4** e **IPv6** para comunicarse, pero también se apoya en **OSPF** para que los routers decidan el mejor camino y en **ICMP** para enviar mensajes de diagnóstico y avisar si algo falla.

**Protocolos de capa de red**: 

![](../IMG/MODULO8IMG/Protocolos%20de%20capa%20de%20red.png)

---

### Las 4 Operaciones de la Capa de Red (Capa 3)

**Direccionamiento:** Para poder comunicarse de extremo a extremo, cada dispositivo final en la red necesita tener configurada una dirección IP única que lo identifique globalmente.

**Encapsulación:** El dispositivo de origen toma los datos de la capa de transporte y los mete dentro de un paquete, agregándole un encabezado IP con los datos clave: la IP de quién envía (emisor) y de quién recibe (receptor).

**Enrutamiento:** Es el servicio que guía los paquetes hacia otras redes a través de los routers. El router elige el mejor camino y cada salto que da el paquete al cruzar un router se le llama formalmente un "salto" (_hop_).

**Desencapsulación:** Cuando el paquete llega por fin al host de destino, este revisa el encabezado IP. Si la IP coincide con la suya, destruye el encabezado y le pasa los datos limpios a la Capa 4 (Transporte).

----

**Encapsulación IP**

Básicamente, el protocolo IP toma el segmento de datos que le entrega la capa de transporte (la capa que está justo arriba) y lo "envuelve" agregándole un **encabezado IP**. Ese encabezado es vital porque es el que se utiliza para lograr entregar el paquete hasta su destino final. Al hacer este proceso de envoltura, los datos se convierten oficialmente en un paquete IP.

![](../IMG/MODULO8IMG/Encapsulación%20IP.png)


**Independencia de las Capas:** El hecho de que la red encapsule los datos capa por capa es genial porque permite mejorar o inventar nuevos protocolos sin dañar al resto del sistema. Esto significa que a la capa de transporte le da exactamente igual si decides usar IPv4, IPv6 o un protocolo inventado en el futuro; el paquete se va a armar sin ningún problema.

**La IP es (casi) inmutable en el viaje:** A medida que tu paquete viaja por el mundo, los routers y switches de Capa 3 van leyendo su encabezado IP para saber a dónde mandarlo. Lo importante aquí es que las direcciones IP originales se mantienen exactamente iguales desde el origen hasta el destino final, con una sola excepción: cuando se topan con un dispositivo haciendo NAT (Traducción de Direcciones de Red) en IPv4.

**Los datos internos son intocables:** Aunque los routers revisen constantemente el encabezado de red para decidir las rutas, ==**nunca tocan ni alteran la carga útil**==. Es decir, los datos que vienen protegidos desde la capa de transporte pasan intactos y sin 
modificaciones durante todo el proceso de enrutamiento.

---

**Características de IP**

El protocolo IP fue diseñado a propósito para ser ligero y tener una sobrecarga baja. Su única misión es llevar un paquete desde el origen hasta el destino a través de las redes, por lo que **no** está diseñado para rastrear ni administrar ese flujo de datos. Si se necesita llevar un control para asegurar que los paquetes llegaron bien, de eso se encargan otros protocolos en otras capas, principalmente TCP en la Capa 4.

Las tres características básicas que definen la forma de operar de IP son:

**Sin conexión:** El protocolo no establece ninguna conexión previa con el dispositivo de destino antes de empezar a enviarle los paquetes de datos.

**Mejor esfuerzo:** Se le considera inherentemente "poco confiable" simplemente porque hace su mejor intento por enviar la información, pero no garantiza la entrega exitosa de los paquetes.

**Medios independientes:** A la IP le da igual por dónde viajen los datos; su operación es totalmente independiente del medio físico que se utilice, ya sea un cable de cobre, fibra óptica o una señal inalámbrica.

---

**Sin conexión**:

Lo que este concepto significa es que el protocolo IP no crea una conexión dedicada de extremo a extremo antes de empezar a mandar los datos.

**Sin conexión - Analogía**

![](../IMG/MODULO8IMG/Sin%20conexión%20-%20Analogía.png)

Las comunicaciones sin conexión funcionan exactamente con ese mismo principio. El protocolo IP no exige que los dispositivos intercambien información de control al principio para establecer una conexión antes de empezar a mandar los paquetes. Simplemente arranca a enviar los datos de una.

**Sin conexión - Red**

![](../IMG/MODULO8IMG/Sin%20conexión%20-%20Red.png)

---

**Mejor esfuerzo**

El protocolo IP es tan ligero que no necesita añadir campos extra en su encabezado para mantener viva una conexión, lo que le quita muchísimo peso y sobrecarga.

Pero esto tiene un costo: como no hay una conexión establecida de antemano, el dispositivo que envía el paquete lo hace a ciegas. Literalmente no sabe si el equipo de destino está encendido, si realmente le llegó el paquete, o si siquiera pudo abrirlo y leerlo. Por eso se le llama de "mejor esfuerzo" o "poco confiable": IP hace el intento de enviar la información, pero no te garantiza bajo ninguna circunstancia que todos los paquetes vayan a llegar a su destino.

![](../IMG/MODULO8IMG/Mejor%20esfuerzo.png)

---

**Independiente de los medios**:

**¿Por qué es "poco confiable"?:** Básicamente, IP no tiene ninguna herramienta para administrar o recuperar los paquetes que se dañan o no llegan a su destino. Aunque el paquete sabe exactamente a dónde va, no tiene cómo avisarle al emisor si la entrega fue exitosa, si llegó en desorden o si se perdió por completo, y tampoco puede retransmitir datos si ocurre un error.

**El trabajo en equipo:** Si se necesita solucionar el problema de paquetes perdidos o desordenados, esa responsabilidad se le delega a las aplicaciones y a los servicios de las capas superiores (específicamente a TCP en la capa de transporte). Al quitarse este peso de encima, IP puede funcionar de una manera muchísimo más eficaz.

**La independencia física:** El concepto central de esta sección es que IP funciona de manera totalmente independiente del medio físico que se use en las capas más bajas. Un mismo paquete IP puede viajar sin problemas convertido en señales electrónicas por cables de cobre, en señales ópticas a través de fibra óptica, o en ondas de radio inalámbricas.

![](../IMG/MODULO8IMG/Independiente%20de%20los%20medios.png)

**El límite de tamaño (MTU):** Aunque a la capa de red le da igual si usas cobre o fibra, sí tiene que respetar el tamaño máximo de datos que ese medio físico puede soportar de un solo golpe. Ese límite se llama **MTU (Unidad de Transmisión Máxima)**. Básicamente, la capa de enlace le avisa a la capa de red cuál es ese límite para que sepa de qué tamaño armar los paquetes.

**Fragmentación de paquetes:** Si un router recibe un paquete IPv4 que es demasiado grande para pasar al siguiente medio (porque tiene un MTU más pequeño), se ve obligado a cortarlo en pedacitos para que quepa. A este proceso se le llama **fragmentación**.

**La desventaja:** Poner al router a cortar paquetes toma tiempo y causa lentitud (latencia) en la red. Y un dato clave de examen al final: los routers **no** pueden fragmentar los paquetes modernos de IPv6.

---

