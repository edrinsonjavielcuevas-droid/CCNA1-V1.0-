
---
### Propiedades del cableado de fibra óptica.

La **fibra óptica** es el medio de red de mayor rendimiento. Consiste en un hilo de vidrio extremadamente delgado que transmite bits como **impulsos de luz**.

**Ventajas:** Ofrece mayor ancho de banda y alcanza distancias mucho más largas que el cobre. Es **totalmente inmune** a las interferencias electromagnéticas (EMI) y de radiofrecuencia (RFI).

 **Funcionamiento:** Actúa como una "tubería de luz" (guía de ondas) donde los láseres o LED envían señales a gran velocidad con una pérdida mínima de señal (baja atenuación).

![](../IMG/Fibra%20ópticas.png)

#### Tipos de fibras ópticas

**Fibra óptica monomodo (SMF)**

![](../IMG/Fibra%20óptica%20monomodo%20(SMF).png)

**Fibra múltimodo (MMF)**

![](../IMG/Fibra%20múltimodo%20(MMF).png)

---

### Dispersión en Fibra Óptica (MMF vs. SMF)

La **dispersión** es la extensión de los pulsos de luz a medida que viajan por el cable. A mayor dispersión, mayor pérdida de intensidad de la señal.

 **MMF (Multimodo):** Tiene una **mayor dispersión**, lo que limita su alcance máximo a unos **500 metros** antes de que la señal se degrade demasiado.

**SMF (Monomodo):** Tiene una dispersión mínima, lo que le permite transmitir datos a distancias mucho mayores sin perder calidad.

----
#### Uso del cableado de fibra óptica

| **Industria / Uso**             | **Aplicación Principal**                                                    |
| ------------------------------- | --------------------------------------------------------------------------- |
| **Redes Empresariales**         | Cableado **backbone** (troncal) e interconexión de infraestructura crítica. |
| **FTTH (Fibra hasta el hogar)** | Servicios de banda ancha residencial y pequeñas empresas.                   |
| **Larga Distancia**             | Conexión de ciudades y países mediante proveedores de servicios.            |
| **Redes Submarinas**            | Conexiones transoceánicas de alta capacidad en entornos hostiles.           |

**Nota:** En este nivel nos enfocaremos principalmente en el uso de fibra dentro de **redes empresariales**.

---

#### Conectores de Fibra Óptica

Los conectores varían según dimensiones y método de acoplamiento. Las empresas los eligen según su equipo y necesidades de densidad de puertos.

**1. Conector ST (Straight Tip):** Conocido como "punta directa", utiliza un mecanismo de bayoneta (girar y bloquear). Fue muy común en redes multimodo.

![](../IMG/Conector%20ST.png)

**2. Conector SC (Subscriber Connector):** A veces llamado conector de suscriptor o "conector cuadrado". Utiliza un mecanismo de tirar y empujar (push-pull) para asegurar un acoplamiento rápido.

![](../IMG/Conector%20SC.png)

**3. Conector LC (Lucent Connector):** Es un conector de factor de forma pequeño (SFP). Es muy popular en redes modernas de alta densidad porque tiene la mitad del tamaño del SC.

![](../IMG/Conector%20LC.png)

**4. Conectores LC Multimodo Dúplex:** Similar al LC, pero utiliza un conector doble para permitir la transmisión y recepción simultánea de datos.

![](../IMG/Conectores%20LC.png)

---

Para lograr una comunicación **dúplex completa** (enviar y recibir al mismo tiempo), la fibra tradicionalmente necesita **dos hilos** de cable. Sin embargo, tecnologías modernas como **100BASE-BX** permiten hacer todo por **una sola fibra** usando distintas longitudes de onda para que las señales no choquen. Por eso verás cables con conectores dobles (dúplex) y otros simples que hacen el trabajo completo.

---
##### Cables de Conexión de Fibra

El color de la chaqueta del cable identifica rápidamente el tipo de fibra:

**Amarillo:** Fibra Monomodo (SMF).

**Naranja (o Aqua):** Fibra Multimodo (MMF).

**1. Cable de conexión multimodo SC-SC:** Utiliza conectores cuadrados en ambos extremos. Común en paneles de conexiones antiguos.

![](../IMG/Cable%20de%20conexión%20multimodo%20SC-SC.png)

**2. Cable de conexión monomodo LC-LC:** Conectores pequeños en ambos extremos. Es el estándar para conectar transceptores SFP en switches modernos.

![](../IMG/Cable%20de%20conexión%20monomodo%20LC-LC.png)

**3. Cable de conexión multimodo ST-LC:** Un cable híbrido que permite conectar equipos viejos (con punta ST) a infraestructura nueva (puertos LC).

![](../IMG/Cable%20de%20conexión%20multimodo%20ST-LC.png)

**4. Cable de conexión monomodo SC-ST:** Otro cable híbrido, esta vez monomodo, para adaptar conexiones de suscriptor (SC) a terminales de punta directa (ST).

![](../IMG/Cable%20de%20conexión%20monomodo%20SC-ST.png)

---
**Fibra vs Cobre**

La **fibra óptica** supera al cobre en distancia, ancho de banda e inmunidad total contra interferencias eléctricas, ya que no conduce electricidad. Por estas ventajas, en entornos empresariales se utiliza principalmente como **cableado troncal (backbone)** para conectar edificios o instalaciones de distribución de datos que manejan un alto tráfico de red.

![](../IMG/Fibra%20vs%20Cobre.png)

---
