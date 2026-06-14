
---

**Unidifusión (_Unicast_):** Identifica de manera única una interfaz específica en un dispositivo habilitado para IPv6; es una comunicación uno a uno.

**Multidifusión (_Multicast_):** Se utiliza para enviar un único paquete IPv6 a un grupo de múltiples destinos simultáneamente.

**Difusión por proximidad (_Anycast_):** Es una dirección de unidifusión asignada a varios dispositivos. Los paquetes enviados a esta dirección son enrutados automáticamente al dispositivo más cercano (en términos de topología de red) que posea dicha dirección.


> **Nota clave:** A diferencia de IPv4, **IPv6 no utiliza direcciones de difusión (_broadcast_)**. Para lograr un resultado similar de comunicación masiva, IPv6 emplea una dirección de multidifusión especial de "todos los nodos".

**Longitud del prefijo IPv6**

Tanto en IPv4 como en IPv6, la porción de red se define mediante la **longitud de prefijo** (notación de barra `/`).

**IPv4 vs. IPv6:**

**IPv4:** Utiliza máscara decimal punteada (ej. `255.255.255.0`) o notación `/24`.

**IPv6:** **No utiliza** máscara decimal punteada; emplea exclusivamente la notación de barra `/`.

**Rango y Estándar:**

La longitud de prefijo en IPv6 puede variar de **0 a 128**.

El estándar recomendado para redes LAN y la mayoría de los despliegues es **`/64`**.

**Longitud del prefijo IPv6**

![](Longitud%20del%20prefijo%20IPv6.png)

Se recomienda utilizar un ID de interfaz de 64 bits en la mayoría de las redes porque la autoconfiguración de direcciones sin estado (SLAAC) emplea esta longitud específica. Además, esta medida simplifica significativamente tanto la creación como la administración de las subredes.

---

**Tipos de direcciones de unidifusión IPv6**

Las direcciones IPv6 de unidifusión identifican de manera exclusiva una interfaz en un dispositivo habilitado para IPv6, siendo necesarias como direcciones de origen para el envío de paquetes. Existen diversas categorías de estas direcciones, incluyendo la unidifusión global, link-local, loopback, sin especificar, local única e IPv4 integrada.

**Direcciones IPv6 de unidifusión**

![](Direcciones%20IPv6%20de%20unidifusión.png)

**Dirección de Unidifusión Global (GUA):** Es el equivalente a una dirección IPv4 pública. Estas direcciones son exclusivas a nivel mundial y son totalmente enrutables a través de Internet, permitiendo que el dispositivo sea accesible desde cualquier parte de la red global. Pueden configurarse de forma manual (estática) o automática (dinámica).

**Dirección Local de Enlace (LLA):** Es obligatoria para todo dispositivo con IPv6 y se utiliza exclusivamente para la comunicación con otros dispositivos dentro del mismo segmento de red (enlace local). Dado que los routers no reenvían paquetes que utilicen una LLA como origen o destino, su ámbito está estrictamente limitado al enlace local, lo que significa que no son enrutables fuera de esa subred específica.

Las **Direcciones Locales Únicas (ULA)**, identificadas en el rango `fc00::/7` a `fdff::/7`, funcionan como una alternativa privada para el direccionamiento interno dentro de una organización o entre sitios específicos. A diferencia de las GUA, estas direcciones **no son enrutables globalmente** ni se traducen para acceder a Internet, lo que las hace ideales para dispositivos que requieren comunicación aislada, como impresoras, servidores locales o equipos de gestión interna que no deben estar expuestos a redes externas.

---

**IPv6 GUA:**

Las **GUA** son direcciones globalmente únicas y enrutables en Internet, siendo el equivalente en IPv6 a las direcciones públicas de IPv4. Su asignación jerárquica comienza en la **ICANN/IANA**, que distribuye los bloques a los cinco Registros Regionales de Internet (RIR).

**Rango actual:** Actualmente solo se asignan GUA que comienzan con los bits `001`, lo cual se representa como `2000::/3`.

**Identificación rápida:** Dado que el rango empieza con `001` en binario, todas las GUA actuales comienzan con el dígito hexadecimal **2** o **3** en su primer hexteto.

**Reserva especial:** El bloque `2001:db8::/32` está reservado exclusivamente para propósitos de **documentación y ejemplos**, por lo que no debe usarse en redes reales.

![](IPv6%20GUA.png)

La siguiente imagen muestra la estructura y el rango de una GUA.

**Direcciones IPv6 con un prefijo de enrutamiento global /48  y un prefijo /64.

![](Direcciones%20IPv6%20con%20un%20prefijo%20de%20enrutamiento%20global.png)


---

Una Dirección de Unidifusión Global (GUA) de IPv6 tiene una estructura jerárquica diseñada para facilitar el enrutamiento y la creación de subredes sin las complicaciones de IPv4. Típicamente, una GUA se divide en tres partes principales para alcanzar la longitud recomendada de `/64`.

**Prefijo Global de Enrutamiento** Es la porción de red que tu proveedor de servicios de Internet (ISP) te asigna. Por lo general, los ISP entregan un prefijo `/48` a las empresas, lo que significa que los primeros 48 bits (los primeros 3 hextetos, como `2001:db8:acad::/48`) identifican tu red principal en Internet. El tamaño de este prefijo determina cuántos bits te quedarán disponibles para crear subredes.

**ID de Subred** Es el campo que se encuentra entre el prefijo global y el ID de interfaz. A diferencia de IPv4, donde tienes que "pedir prestados" bits de la porción de host para crear subredes, IPv6 ya viene con este espacio dedicado. Si tu ISP te da un `/48` y usas el estándar `/64`, te quedan 16 bits (exactamente el cuarto hexteto) exclusivos para crear hasta 65,536 subredes internas.

**ID de Interfaz** Esta parte equivale a la porción de "host" en IPv4 y se utiliza para identificar de manera única la tarjeta de red de un dispositivo. Se recomienda encarecidamente que siempre tenga **64 bits** de longitud. Esto no solo permite alojar 18 trillones de dispositivos por subred, sino que es un requisito técnico indispensable para que la autoconfiguración dinámica (SLAAC) funcione correctamente. Un dato curioso es que, al no existir el _broadcast_ en IPv6, puedes usar direcciones de host con puros `1`s o puros `0`s (aunque la de todos ceros se reserva para los routers de la subred).

**Resumen de la estructura típica (/64)**

|**Componente**|**Tamaño típico**|**¿Quién lo define?**|**Función principal**|**Equivalente IPv4**|
|---|---|---|---|---|
|**Prefijo Global de Enrutamiento**|48 bits (3 hextetos)|El ISP|Identificar tu red principal en el Internet global.|Porción de Red (Pública)|
|**ID de Subred**|16 bits (1 hexteto)|El administrador local|Organizar y segmentar la red interna (ej. Ventas, TI).|Bits prestados de la máscara|
|**ID de Interfaz**|64 bits (4 hextetos)|SLAAC o asignación manual|Identificar de forma única el dispositivo final.|Porción de Host|

---

Las **Direcciones Locales de Enlace (LLA)** son un componente vital en IPv6, diseñadas exclusivamente para la comunicación entre dispositivos que se encuentran en el mismo segmento de red (enlace o subred). Su característica principal es que **no son enrutables**; un router jamás reenviará un paquete que tenga una LLA como origen o destino hacia otra red.

### Puntos clave de las LLA:

**Son estrictamente obligatorias:** A diferencia de las direcciones globales (GUA), que son opcionales según la necesidad de Internet, **toda interfaz** habilitada para IPv6 debe tener al menos una LLA para funcionar.

**Se autoconfiguran:** Si no le asignas una LLA de forma manual, el dispositivo genera la suya automáticamente sin necesidad de comunicarse con un servidor DHCP. Esto garantiza que dispositivos en la misma red (como una PC y una impresora, o una PC y su router) puedan "hablar" entre sí inmediatamente.

**Identificación rápida (Rango):** Las LLA operan en el bloque **`fe80::/10`**. En la práctica, esto significa que el primer hexteto de la dirección siempre comenzará con un valor que va desde **`fe80`** hasta **`febf`**.

---

**Comunicaciones de enlace local de IPv6**

![](Comunicaciones%20de%20enlace%20local%20de%20IPv6.png)

La siguiente imagen muestra algunos de los usos de la LLA en IPv6:

![](usos%20de%20la%20LLA%20en%20IPv6.png)


Existen dos métodos para que un dispositivo obtenga su LLA:

**Configuración Estática:** El administrador de red asigna la dirección manualmente en la interfaz del dispositivo.

**Configuración Dinámica:** El dispositivo genera su propia dirección de forma automática. Existen dos enfoques comunes:

**Generación Aleatoria:** El dispositivo crea el ID de interfaz con valores aleatorios.

**Método EUI-64 (Identificador Único Extendido):** El dispositivo utiliza su propia dirección MAC de 48 bits, inserta bits adicionales en el centro para convertirla en una estructura de 64 bits, y la combina con el prefijo `fe80::`.

> **Dato importante:** El uso de EUI-64 es un estándar muy común porque garantiza que, al derivar el ID de interfaz de la dirección física (MAC), cada dispositivo tenga un identificador único a nivel mundial, evitando conflictos en la red.

----

