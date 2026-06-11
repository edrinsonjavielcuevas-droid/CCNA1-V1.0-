
---
### Propiedades del Cableado UTP

El cable UTP es el estándar indiscutible de las LAN por su flexibilidad y bajo costo, pero su verdadera magia técnica está en cómo combate el ruido sin usar blindaje metálico. Cisco destaca dos mecanismos de defensa fundamentales:

**Técnica de Anulación (Cancellation):** Los ingenieros diseñan los circuitos en pares. Al colocar dos hilos muy cerca, sus campos magnéticos son exactamente opuestos y se **anulan** entre sí. Esto también neutraliza las interferencias externas (EMI/RFI).

 **Variación del trenzado (Twist rates):** Para potenciar la anulación y evitar que los pares se interfieran entre ellos (_crosstalk_), cada par de color tiene un **número diferente de vueltas por metro**. Si desarmas un cable, verás que el par naranja tiene menos trenzas que el azul; esta asimetría es lo que permite que el cable sea un medio de transmisión confiable a altas velocidades.

El UTP depende exclusivamente del efecto de anulación. Si desenredas demasiado los hilos al ponchar un conector, rompes esta propiedad y generas errores en la red.

![](../IMG/Propiedades%20UTP.png)

---
#### La Capa Física (OSI)

Es el cimiento de la red. Su función es transportar los bits que conforman una trama de la Capa 2 a través de los medios físicos.

**Proceso:** Recibe la trama, la codifica en patrones de señales (eléctricas, ópticas o de radio) y las transmite. El receptor realiza el proceso inverso para reconstruir la trama original.

#### Estándares y Componentes

A diferencia de las capas superiores (software/IETF), la Capa 1 se rige por hardware y estándares de ingeniería (**IEEE, ISO, TIA/EIA, ITU**).

|**Componente**|**Descripción**|
|---|---|
|**Componentes Físicos**|El hardware tangible: NICs, interfaces, conectores y materiales de cables.|
|**Codificación**|El "idioma" o patrón de bits (ej. Manchester) para que el emisor y receptor se entiendan.|
|**Señalización**|Cómo se representan los bits físicamente (voltaje, pulsos de luz o microondas).|

---

## Medios de Transmisión

#### Cable de Cobre

Es el más común por ser económico y flexible, pero sufre de **Atenuación** (pérdida de señal por distancia) e **Interferencias (EMI/RFI)**.

**UTP (Par Trenzado No Blindado):** Usa la técnica de **anulación** y diferentes **ratios de trenzado** por par para cancelar ruidos y _crosstalk_.

 **STP (Par Trenzado Blindado):** Incluye blindaje metálico y requiere conexión a tierra; ideal para entornos con mucho ruido eléctrico.
 
 **Coaxial:** Núcleo de cobre con malla protectora. Vital para Internet por cable y conexiones de antenas inalámbricas.

#### Cable de Fibra Óptica

Transmite bits mediante **pulsos de luz** a través de hilos de vidrio. Es inmune a las interferencias eléctricas y soporta distancias mucho mayores que el cobre.

#### Medios Inalámbricos

Utilizan **ondas de radio** para transportar señales por la atmósfera. Ofrecen movilidad, pero son vulnerables a obstáculos físicos y saturación del espectro.

#### Ancho de Banda y Rendimiento

El **Ancho de Banda** es la capacidad teórica del medio (bits por segundo).

|**Término**|**Definición**|
|---|---|
|**Latencia**|El tiempo/retraso que tardan los datos en viajar de origen a destino.|
|**Rendimiento (Throughput)**|La medida **real** de transferencia en un momento dado.|
|**Capacidad Útil (Goodput)**|Los datos puros transferidos (Rendimiento menos el tráfico de control).|

---

#### Conectividad UTP

Se basa en los estándares **TIA/EIA-568** para el patillaje de los conectores **RJ-45**.

**Directo (Straight-through):** Para conectar dispositivos diferentes (PC a Switch).

 **Cruzado (Crossover):** Para conectar dispositivos iguales (Switch a Switch).
 
 **Rollover:** Cable propietario de Cisco para acceder a la consola de configuración.


![](../IMG/Conectores%20UTP.png)

**Conectores RJ-45 para UTP**

![](../IMG/Conectores%20RJ-45%20para%20UTP.png)

**Socket RJ-45 para UTP**

![](../IMG/Socket%20RJ-45%20para%20UTP.png)

**Cable UTP mal terminado**

![](../IMG/Cable%20UTP%20mal%20terminado.png)

**Cable UTP correctamente terminado**

![](../IMG/Cable%20UTP%20correctamente%20terminado.png)

**Nota:** La terminación incorrecta de los cables puede afectar el rendimiento de la transmisión.

---

### Cables UTP Directos y Cruzados

**Directo (Straight-through):** Ambos extremos iguales (T568A o T568B). Conecta dispositivos **diferentes** (Host a Switch, Switch a Router).

**Cruzado (Crossover):** Extremos diferentes (uno T568A y otro T568B). Conecta dispositivos **similares** (Switch a Switch, Router a Router). _Hoy es heredado gracias al Auto-MDIX._

 **Rollover (Cisco):** Conecta una PC directamente al puerto de **consola** para configuración.

**Regla de oro:** Si no hay conectividad en el lab, lo primero es verificar que el tipo de cable sea el correcto para los dispositivos que estás uniendo.

**T568A and T568B Standards**: La tabla muestra el tipo de cable UTP, los estándares relacionados y la aplicación típica de estos cables.

![](../IMG/T568A%20and%20T568B%20Standards.png)

#### Cable Types and Standards

![](../IMG/Cable%20Types%20and%20Standards.png)

**Actividad - Pinouts de cable**

![](../IMG/Pinout%20T568A.png)

![](../IMG/Pinout%20T569B.png)
