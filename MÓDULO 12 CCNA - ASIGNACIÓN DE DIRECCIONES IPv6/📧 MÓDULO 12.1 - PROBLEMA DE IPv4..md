
---

Existen varios protocolos para migrar de IPv4 a IPv6, aunque realmente una no reemplazará a la otra, sino que tienen que coexistir juntas. Por eso existen 3 cotegorías:

**1. Dual-stack (Doble pila)** Esta técnica permite que los protocolos IPv4 e IPv6 coexistan en el mismo segmento de red. Los dispositivos ejecutan ambas pilas de protocolos de manera simultánea, lo que facilita una conectividad nativa donde la red del cliente tiene acceso directo a Internet a través de IPv6.

![](../IMG/MODULO12IMG/Dual%20stack.png)

---

**2. Tunelización** La tunelización es un método que permite transportar paquetes IPv6 a través de una infraestructura de red que solo soporta IPv4. Básicamente, se encapsula el paquete IPv6 dentro de un paquete IPv4 para que pueda atravesar redes antiguas sin necesidad de actualizar todos los equipos intermedios.

![](Tunelización.png)

---

**3. Traducción** La traducción permite que los dispositivos que solo utilizan IPv6 se comuniquen con servidores o dispositivos que solo utilizan IPv4. Se utiliza un dispositivo (como un gateway o NAT64) para convertir los paquetes de un protocolo al otro, permitiendo la comunicación entre ambos mundos aunque sean técnicamente incompatibles.

![](Traducción.png)

La tunelización y la traducción son exclusivamente mecanismos de transición para facilitar el despliegue hacia un entorno de IPv6 nativo, por lo que su implementación debe limitarse a casos donde sea estrictamente necesario, ya que el objetivo fundamental debe ser siempre establecer comunicaciones IPv6 nativas de extremo a extremo entre el origen y el destino.

---
## Direccionamiento Dinámico para las GUAs de IPv6

**Fundamento de IPv6:** El primer paso para dominar IPv6 es entender su formato y escritura.

**Capacidad:** Son direcciones mucho más extensas que las IPv4, lo que hace casi imposible agotar las direcciones disponibles.

**Estructura Técnica:**

Tienen una longitud total de 128 bits.

Se escriben como una cadena de valores hexadecimales.

Cada cuatro bits equivalen a un dígito hexadecimal, sumando un total de 32 valores hexadecimales.

**Formato de escritura:** No distinguen entre mayúsculas y minúsculas; pueden escribirse indistintamente.

---

**Segmentos o hextetos de 16 bits**

![](Segmentos%20o%20hextetos%20de%2016%20bits.png)


---

**Formato preferido**

El formato preferido es escribir la dirección completa en grupos de cuatro valores hexadecimales, separados por dos puntos (`x:x:x:x:x:x:x:x`).

**Concepto de "Hexteto":**

En IPv4 usamos el término **octeto** (8 bits).

En IPv6 usamos el término no oficial **hexteto** para referirnos a cada segmento de **16 bits** (que contiene 4 dígitos hexadecimales).

**Composición:** Una dirección en formato preferido contiene 8 hextetos, sumando un total de 32 dígitos hexadecimales (128 bits).

**Nota clave:** Aunque se llama "preferido", escribir los 32 dígitos completos es largo y tedioso. Existen dos reglas específicas para abreviar estas direcciones y hacerlas más manejables.

Estos son ejemplos de direcciones IPv6 en el formato preferido.

![](Formato%20preferido.png)

---

**Regla 1 - Omitir los ceros iniciales**

La primera regla para abreviar una dirección IPv6 consiste en **omitir los ceros iniciales** de cualquier hexteto, permitiendo eliminar hasta tres ceros a la izquierda dentro de cada segmento de 16 bits. Es fundamental recordar que esta regla aplica estrictamente a los ceros colocados al inicio; los ceros situados al final o en medio deben conservarse intactos para evitar ambigüedades en el valor del hexteto y asegurar la correcta interpretación de la dirección.

**Ejemplos de aplicación de la Regla 1**

|**Hexteto Original**|**Hexteto Abreviado**|
|---|---|
|`01ab`|`1ab`|
|`09f0`|`9f0`|
|`0a00`|`a00`|
|`00ab`|`ab`|
|`0000`|`0`|

**Nota importante:** El hexteto `0000` se puede reducir simplemente a un único `0`. Recuerda que si el valor es `abc`, no puedes escribirlo como `abc0` porque cambiarías su valor, ya que la regla solo permite eliminar ceros a la **izquierda**.

---

**Regla 2 - Dos puntos dobles**

La segunda regla para comprimir direcciones IPv6 establece que se puede usar un **doble colon (`::`)** para reemplazar una o más cadenas contiguas de hextetos compuestos exclusivamente por ceros. Esta notación, conocida como "formato comprimido", permite una reducción significativa en la escritura de la dirección, pero tiene una restricción crítica: **solo se puede utilizar una vez** por dirección para evitar ambigüedades en su expansión. Si una dirección contiene múltiples cadenas de ceros, se recomienda aplicar el doble colon en la cadena más larga; en caso de empate en longitud, se debe aplicar en la primera cadena que aparezca.

Reglas clave para el uso de `::`

| **Escenario**          | **Regla / Práctica**                                        |
| ---------------------- | ----------------------------------------------------------- |
| **Uso permitido**      | Solo una vez por dirección IPv6.                            |
| **Función**            | Reemplaza una cadena continua de uno o más hextetos `0000`. |
| **Múltiples cadenas**  | Elegir la cadena más larga.                                 |
| **Empate en longitud** | Elegir la primera cadena que aparezca.                      |

**Nota crítica:** El uso incorrecto del doble colon (como en `2001:db8::abcd::1234`) es inválido porque el sistema no podría determinar cuántos ceros deben restaurarse en cada sección, resultando en múltiples direcciones posibles.

---


