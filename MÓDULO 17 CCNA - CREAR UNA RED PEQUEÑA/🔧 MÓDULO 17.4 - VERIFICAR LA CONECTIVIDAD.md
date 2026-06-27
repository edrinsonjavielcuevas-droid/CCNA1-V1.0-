
---

El comando `ping` es la herramienta fundamental para verificar la conectividad de **Capa 3** (Capa de Red):

### Funcionamiento Técnico

**Protocolo:** Utiliza **ICMP** (Internet Control Message Protocol).

**Tipos de mensaje:**

**ICMP Tipo 8:** Mensaje de solicitud de eco (_Echo Request_).

**ICMP Tipo 0:** Mensaje de respuesta de eco (_Echo Reply_).

**Comportamiento en Windows:** Por defecto, envía **cuatro** mensajes consecutivos y espera sus correspondientes cuatro respuestas para confirmar la conectividad.

### Utilidad

Permite comprobar rápidamente si existe un camino válido entre una IP de origen y una de destino, midiendo además estadísticas de **RTT** (_Round Trip Time_ o tiempo de ida y vuelta). Está disponible universalmente en sistemas operativos como Windows, Linux, macOS y Cisco IOS.

![](01_CCNA/IMG/MODULO17IMG/Ping.png)

![](PPing1.png)

Como se muestra en el resultado del comando, PC A ha recibido respuestas de echo de PC-B verificando la conexión de red de Capa 3.

![](PC%20'A.png)

La salida confirma la conectividad de Capa 3 entre el PC A y el PC B.

La salida de un comando **ping** del IOS de Cisco varía de un host de Windows. Por ejemplo, el ping de IOS envía cinco mensajes de eco ICMP, como se muestra en la salida.

![](PING%201.png)

Observe los **!!!!!** caracteres en el resultado. El comando IOS **ping** muestra un indicador para cada respuesta de echo ICMP recibida. En la siguiente tabla se enumeran los posibles caracteres del comando **ping:**

### Indicadores de ping IOS

![](Indicador%20de%20ping%20IOS.png)

**Nota:** Otras posibles respuestas de ping incluyen Q, M,?, o &. Sin embargo, el significado de estos están fuera de alcance para este módulo.

----

### Ping extendido

Un estándar **ping** utiliza la dirección IP de la interfaz más cercana a la red de destino como origen de **ping**. La dirección IP de origen del comando**ping 10.1.1.10** en R1 sería la de la interfaz G0/0/0 (209.165.200.225), como se ilustra en el ejemplo.

![](PIng%20extendido.png)

Cisco IOS ofrece un modo "extendido" del comando ping, el cual permite ajustar parámetros para crear pings personalizados. Este modo se accede en modo EXEC privilegiado escribiendo "ping" sin una dirección IP de destino, tras lo cual se presentarán indicaciones para personalizar el comando. Al presionar Enter, se aceptan los valores predeterminados.

Un ping extendido es útil, por ejemplo, para probar la conectividad entre redes específicas (como la LAN R1 192.168.10.0/24 y la LAN 10.1.1.0) permitiendo especificar una dirección IP de origen distinta, como la de una interfaz específica (ejemplo: G0/0/1 con IP 192.168.10.1).

![](Ping%20ex.png)

El siguiente resultado del comando configura un **ping** extendido en R1 y especifica que la dirección IP de origen sea la de la interfaz G0/0/1 (es decir, 192.168.10.1).

![](ping%20en%20consola.png)

**Nota:** El comando **ping ipv6** se utiliza para pings IPv6 extendidos.

---

### Verificar la conectividad con Traceroute

**Propósito:** Mientras que `ping` verifica la conectividad de Capa 3, `traceroute` (o `tracert` en Windows) ayuda a localizar en qué punto de la ruta ocurre un fallo, proporcionando una lista de saltos hasta el destino.

**Diferencias de sintaxis:**

En **Windows**, el comando es `tracert` y utiliza solicitudes de eco ICMP.

En **Cisco IOS** (y Linux), el comando es `traceroute` y utiliza paquetes UDP con un número de puerto no válido, esperando un mensaje de "puerto ICMP inalcanzable" desde el destino.

**Interpretación de resultados:** La aparición de asteriscos (*) indica que un salto no respondió, lo que sugiere una falla de interconexión o que los routers están configurados para no responder a estas solicitudes.

**Comandos de interrupción:**

En **Windows**, se utiliza `Ctrl-C`.

En **Cisco IOS**, se utiliza `Ctrl-Shift-6`.

---

Al igual que el comando ping, `traceroute` cuenta con un modo extendido que permite ajustar parámetros para diagnosticar problemas complejos, como bucles de enrutamiento, routers que descartan paquetes o bloqueos de firewall.

### Diferencias clave según el sistema:

**Windows (tracert):** Permite configurar parámetros mediante **opciones o "flags"** directamente en la línea de comandos (ejemplos: `-d` para no resolver nombres, `-h` para limitar saltos, `-w` para ajustar el tiempo de espera).

**Cisco IOS (traceroute extendido):** Se activa escribiendo `traceroute` sin IP de destino. El sistema guía al usuario paso a paso mediante una serie de indicadores para configurar parámetros detallados. Al presionar **Enter** en cada paso, se aceptan los valores predeterminados.

### Caso de uso práctico

El `traceroute` extendido en Cisco IOS es particularmente útil cuando necesitas especificar una **dirección IP de origen específica** (por ejemplo, la IP de una interfaz LAN como `192.168.10.1`) para probar cómo se comporta el tráfico cuando sale desde un segmento concreto de la red, en lugar de usar la IP de la interfaz de salida predeterminada.

---

