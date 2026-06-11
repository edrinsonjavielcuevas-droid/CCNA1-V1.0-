
---

### Aspectos Básicos de VLSM (Máscara de Subred de Longitud Variable)

La Máscara de Subred de Longitud Variable (VLSM) es una técnica avanzada de diseño que permite a los administradores dividir un espacio de direcciones IP en subredes de **diferentes tamaños**, superando la limitación del _subnetting_ tradicional donde todos los segmentos debían tener la misma cantidad de hosts. Su propósito principal es maximizar la eficiencia y frenar el desperdicio de direcciones IPv4. 

Por ejemplo, en lugar de asignar una subred con capacidad para 254 equipos a un enlace directo entre dos routers (que solo necesita 2 IPs), VLSM permite ajustarle una máscara pequeña como `/30`, mientras reservas las máscaras más grandes (como `/24` o `/25`) para las redes locales (LAN) que concentran decenas o cientos de usuarios.

Para implementar VLSM con éxito, la regla de oro es ordenar y asignar las redes **de mayor a menor** (empezando por el segmento que requiere más hosts y terminando con el que requiere menos). Además, esta técnica requiere obligatoriamente que la infraestructura utilice protocolos de enrutamiento "sin clase" (_classless_), como OSPF, EIGRP o RIPv2. A diferencia de los protocolos antiguos, estos tienen la capacidad de incluir la longitud del prefijo (la máscara) en sus actualizaciones de enrutamiento, permitiendo que los routers procesen correctamente una topología donde el tamaño de la subred cambia de un enlace a otro.

---

### Ejemplo de Estructura VLSM

Imagina que dispones de la red base **`192.168.1.0/24`** y necesitas segmentarla para cubrir cuatro áreas distintas, organizándolas de mayor a menor necesidad de hosts:

|**Segmento de Red**|**Hosts Requeridos**|**Máscara / Prefijo**|**Dirección de Red**|**Rango de IPs Utilizables**|**Dirección de Broadcast**|
|---|---|---|---|---|---|
|**LAN 1 (Operaciones)**|60|`/26`|`192.168.1.0`|`192.168.1.1` - `192.168.1.62`|`192.168.1.63`|
|**LAN 2 (Ventas)**|28|`/27`|`192.168.1.64`|`192.168.1.65` - `192.168.1.94`|`192.168.1.95`|
|**LAN 3 (Gerencia)**|12|`/28`|`192.168.1.96`|`192.168.1.97` - `192.168.1.110`|`192.168.1.111`|
|**Enlace WAN (Routers)**|2|`/30`|`192.168.1.112`|`192.168.1.113` - `192.168.1.114`|`192.168.1.115`|

Observa cómo VLSM permite que, después de suplir todas estas redes de diferentes tamaños, aún te quede espacio libre desde la IP `192.168.1.116` en adelante para futuros crecimientos.

---
### Conservación IPv4 y Subredes Tradicionales:

El agotamiento de direcciones IPv4 exige optimizar el espacio disponible (un problema que IPv6 elimina gracias a su inmensa capacidad).

**El Problema del Método Tradicional:** Asigna subredes de **tamaño fijo** (todas con la misma cantidad de direcciones). Esto genera un gran desperdicio de IPs a menos que todos los segmentos de tu red requieran exactamente la misma cantidad de hosts.

**Análisis del Escenario:** La siguiente topología necesita **siete subredes** (4 para las LAN y 3 para las conexiones WAN). Si usamos el método tradicional en la red `192.168.20.0/24`, debemos crear 8 subredes fijas de **30 hosts utilizables cada una**. Aunque esto cubre la LAN más grande (Edificio D, con 28 hosts), desperdicia muchísimas direcciones en los enlaces WAN, que solo necesitan 2 hosts.

![](../IMG/MODULO11IMG/Conservación%20IPv4%20y%20Subredes%20Tradicionales.png)

**Esquema de subredes básico**

![](../IMG/MODULO11IMG/Esquema%20de%20subredes%20básico.png)

Estas siete subredes podrían asignarse a las redes LAN y WAN, como se muestra en la figura.

![](../IMG/MODULO11IMG/siete%20subredes.png)

Si bien la división en subredes tradicional satisface las necesidades de la LAN más grande y divide el espacio de direcciones en una cantidad adecuada de subredes, da como resultado un desperdicio significativo de direcciones sin utilizar.

Por ejemplo, solo se necesitan dos direcciones en cada subred para los tres enlaces WAN. Dado que cada subred tiene 30 direcciones utilizables, hay 28 direcciones sin utilizar en cada una de estas subredes. Como se muestra en la figura, esto da como resultado 84 direcciones no utilizadas (28x3).

**Direcciones sin utilizar en subredes WAN**

![](../IMG/MODULO11IMG/Direcciones%20sin%20utilizar%20en%20subredes%20WAN.png)

Además, de esta forma se limita el crecimiento futuro al reducir el número total de subredes disponibles. Este uso ineficiente de las direcciones es característico de la división en subredes tradicional. La aplicación de un esquema de división en subredes tradicional a esta situación no resulta muy eficiente y genera desperdicio.

La máscara de subred de longitud variable (VLSM) se desarrolló para evitar el desperdicio de direcciones al permitirnos subred una subred.

---

### El Concepto de VLSM

**Subnetting Tradicional:** Utiliza una única máscara de subred para todos los segmentos, creando subredes de **tamaño fijo** (todas tienen exactamente la misma capacidad de hosts).

**La Ventaja de VLSM:** Permite dividir el espacio de red en **partes desiguales**. La máscara de subred cambia (varía) según la cantidad específica de bits que se toman prestados para cada subred en particular. De ahí proviene el nombre "longitud variable", ya que te permite ajustar la máscara al tamaño exacto que necesita cada segmento, optimizando el espacio al máximo.

![](../IMG/MODULO11IMG/El%20Concepto%20de%20VLSM.png)

VLSM simplemente subdivide una subred. La misma topología utilizada anteriormente se muestra en la figura. Nuevamente, usaremos la red 192.168.20.0/24 y la subred para siete subredes, una para cada una de las cuatro LAN, y una para cada una de las tres conexiones entre los routeres.

![](../IMG/MODULO11IMG/La%20misma%20topología%20utilizada.png)

La figura muestra cómo la red 192.168.20.0/24 se subredes en ocho subredes de igual tamaño con 30 direcciones de host utilizables por subred. Se usan cuatro subredes para las LAN y tres subredes para las conexiones entre los routers.

**Esquema Básico de Subredes**

![](../IMG/MODULO11IMG/Esquema%20Básico%20de%20Subredes.png)

Sin embargo, las conexiones entre los routeres requieren sólo dos direcciones de host por subred (una dirección de host para cada interfaz del router). Actualmente todas las subredes tienen 30 direcciones de host utilizables por subred. Para evitar desperdiciar 28 direcciones por subred, VLSM puede usarse para crear subredes más pequeñas para las conexiones entre routeres.

Para crear subredes más pequeñas para los enlaces WAN, se dividirá una de las subredes. En este ejemplo, la última subred, 192.168.20.224/27, puede subdividirse aún más. La figura muestra que la última subred se ha subred utilizando la máscara de subred 255.255.255.252 o /30.

**Esquema de división en subredes de VLSM**

![](../IMG/MODULO11IMG/Esquema%20de%20división%20en%20subredes%20de%20VLSM.png)


¿Por qué /30? Recuerde que cuando se conoce el número de direcciones de host necesarias, se puede usar la fórmula 2n -2 (donde n es igual al número de bits de host restantes). Para proporcionar dos direcciones utilizables, se deben dejar dos bits de host en la parte del host. Debido a que hay cinco bits de host en el espacio de direcciones subred 192.168.20.224/27, se pueden pedir prestados tres bits más, dejando dos bits en la porción de host. Los cálculos que se realizan llegado este punto son exactamente los mismos que se utilizan para la división en subredes tradicional: Se toman prestados los bits, y se determinan los rangos de subred. La figura muestra cómo las cuatro subredes /27 se han asignado a las LAN y tres de las subredes /30 se han asignado a los enlaces entre routeres.

![](../IMG/MODULO11IMG/Por%20qué%2030.png)

Este esquema de subredes VLSM reduce el número de direcciones por subred a un tamaño apropiado para las redes que requieren menos subredes. La subred subred 7 para enlaces entre routeres permite que las subredes 4, 5 y 6 estén disponibles para redes futuras, así como cinco subredes adicionales disponibles para conexiones entre routeres.

**Nota:** Cuando use VLSM, siempre comience por satisfacer los requisitos de host de la subred más grande. Siga con la división en subredes hasta que se cumplan los requisitos de host de la subred más pequeña.

---
### Asignación de direcciones de topología VLSM

Usando las subredes VLSM, las redes LAN y entre routeres se pueden abordar sin desperdicio innecesario.

La figura muestra las asignaciones de direcciones de red y las direcciones IPv4 asignadas a cada interfaz de router.

![](../IMG/MODULO11IMG/Asignación%20de%20direcciones%20de%20topología%20VLSM.png)

**Interfaz del Router:** Se le asigna la **primera dirección IPv4** de host de cada subred a su interfaz LAN.

**Configuración de Hosts:** Reciben una dirección IPv4 del intervalo disponible de su subred, acompañada de la máscara adecuada.

**Gateway Predeterminado:** Todos los hosts utilizan la dirección IP asignada a la interfaz LAN del router como su puerta de enlace.

**Tabla de Referencia:** Muestra el desglose de las direcciones de red, los intervalos de hosts y la dirección de gateway predeterminado para cuatro redes LAN.

![](../IMG/MODULO11IMG/Esquema%20de%20Direccionamiento.png)

---



