
---

**Encabezado de paquetes IPv4**:

El protocolo IPv4 es uno de los principales en la capa de red, y la función central de su encabezado es garantizar que el paquete logre llegar a su siguiente parada en el camino hacia el destino final. Para hacer esto posible, este encabezado está compuesto por varios campos con información clave en forma de números binarios, los cuales son leídos y examinados durante todo el proceso de la Capa 3.

---

**Campos del encabezado de paquetes IPv4:**

El encabezado de un paquete IPv4 es fundamental para la gestión de las comunicaciones en la Capa 3, ya que sus diversos campos contienen parámetros de configuración específicos representados mediante valores binarios. Para su análisis y consulta, estos campos se organizan en diagramas visuales que se interpretan de izquierda a derecha y de arriba hacia abajo. Estos diagramas permiten identificar la estructura detallada de los campos que componen un paquete IPv4.

![](../IMG/MODULO8IMG/Campos%20del%20encabezado%20de%20paquetes%20IPv4.png)

---

|**Campo**|**Descripción**|
|---|---|
|**Versión**|Indica que es un paquete IPv4 (valor 0100).|
|**DiffServ (ToS)**|Determina la prioridad del paquete (calidad de servicio).|
|**Suma de comprobación**|Detecta errores o daños en el encabezado.|
|**Tiempo de vida (TTL)**|Limita la vida útil del paquete; se reduce en cada router (si llega a 0, se descarta).|
|**Protocolo**|Identifica el protocolo de la capa superior (ej. TCP, UDP, ICMP).|
|**IP de origen**|Dirección IPv4 unicast del emisor.|
|**IP de destino**|Dirección IPv4 del receptor (unicast, multicast o difusión).|

---

