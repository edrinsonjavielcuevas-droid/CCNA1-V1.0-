
---

**Porciones de Red y de Host (Direccionamiento IPv4)**

Una dirección IPv4 es una secuencia de **32 bits** dividida en dos partes jerárquicas:

**Porción de Red:** Identifica la red específica a la que pertenece el dispositivo. Todos los dispositivos que están en la misma red local **deben tener exactamente los mismos bits** en esta porción.

**Porción de Host:** Identifica al dispositivo específico (el host) dentro de esa red. Cada host dentro de la misma red debe tener una porción de host **única** para ser diferenciado de los demás.

![](../IMG/MODULO11IMG/Direccion%20IPv4.png)

----

**¿Cómo saben los dispositivos dónde termina la red y empieza el host?**

La dirección IP por sí sola no te dice dónde está el corte. Para eso existe la **Máscara de Subred**.

La máscara de subred actúa como una "plantilla" o "filtro" que le indica al dispositivo cuáles bits de los 32 corresponden a la red y cuáles al host.

**En la práctica:** Si comparas la IP de un dispositivo con la de otro usando sus respectivas máscaras, puedes determinar instantáneamente si el otro equipo está "cerca" (en la misma red) o "lejos" (en otra red y por tanto necesitas un _gateway_).


----

**Requisitos de Configuración y Dirección de Red**

**Puerta de enlace predeterminada (Gateway):** Es obligatoria para poder comunicarte con **redes remotas**.

**Servidor DNS:** Es necesario para traducir los nombres de dominio a direcciones IPv4.

**Dirección de red:** El dispositivo utiliza la máscara de subred para calcularla. Esta dirección es clave porque representa a **todos los dispositivos** que pertenecen a esa misma red.

**Máscara de subred:**

![](Máscara%20de%20subred.png)

Una máscara de subred es una secuencia continua de unos (1) seguida de ceros (0). Para separar la porción de red de la del host, el dispositivo compara esta máscara con la dirección IPv4 bit a bit, de izquierda a derecha.

En la siguiente imagen podemos ver una IPv4 vs su Máscara de subred.

![](IPv4%20vs%20su%20Máscara%20de%20subred.png)

**Nota:** La máscara de subred no contiene datos de la dirección; solo funciona como una guía que le indica al equipo dónde buscar las porciones de red y host. Para extraer exactamente la porción de red, la computadora utiliza la operación lógica binaria llamada **AND**.

----

#### Longitud del prefijo (Notación de Barra): 

Es un método abreviado y más sencillo para expresar la máscara de subred. En lugar de usar el formato decimal largo, simplemente se cuenta la cantidad total de bits configurados en `1` en la máscara y se escribe una barra diagonal (`/`) seguida de ese número (por ejemplo, **/24**).

**Comparación de máscara de subred y longitud de sufijo**

![](Comparación%20de%20máscara%20de%20subred%20y%20longitud%20de%20sufijo.png)

**Sinónimo:** La _dirección de red_ también se llama comúnmente **prefijo** o **prefijo de red**. Por eso, a la cantidad de unos (1) en la máscara se le llama _longitud del prefijo_.

**Sintaxis de escritura:** Al escribir una IP con esta notación, se coloca la dirección seguida inmediatamente de la barra y el número, **sin espacios**.

`Ejemplo tradicional: 192.168.10.10 255.255.255.0`

`Notación de prefijo: 192.168.10.10/24`

_(Nota: En esta etapa, el enfoque principal suele ser el prefijo /24, que equivale a la máscara 255.255.255.0)._

---

### Determinación de la red - Lógica AND:

Es la operación booleana fundamental que utilizan los dispositivos de red para calcular su dirección de red. Su funcionamiento se basa en una única regla estricta:

**1 AND 1 = 1** (Solo se obtiene un `1` si ambos bits comparados son `1`).

**Cualquier otra combinación** (0 y 1, 1 y 0, 0 y 0) da como resultado siempre **0**.

---

**Cálculo de la Dirección de Red (Operación AND)**

**Regla Booleana:** En lógica digital, `1` es Verdadero (True) y `0` es Falso (False). La operación AND requiere que **ambos** valores de entrada sean `1` para dar como resultado un `1`.

**Aplicación:** Para identificar a qué red pertenece un host, el equipo toma la Dirección IP y la Máscara de Subred, y les aplica la operación AND lógico **bit por bit**.

**Ejemplo Práctico:**

**Dirección del Host:** `192.168.10.10`

**Máscara de Subred:** `255.255.255.0`

**Dirección de Red (Resultado del AND):** `192.168.10.0`

![](Cálculo%20de%20la%20Dirección%20de%20Red%20(Operación%20AND).png)

**Propósito de la Operación AND**

El cálculo AND se ejecuta **bit a bit** entre la IP y la máscara para producir la dirección de red (ej. `192.168.10.0/24`). Esta operación matemática es fundamental porque es el mecanismo exacto que permite a un host **descubrir a qué red local pertenece**.

---

**Direcciones de red, de host y de difusión:**

Dentro de cada red, las direcciones IP se clasifican en tres tipos fundamentales:

**Dirección de Red:** Representa al segmento de red en su totalidad.

**Direcciones de Host:** Son las IP utilizables que se asignan individualmente a los dispositivos.

**Dirección de Broadcast (Difusión):** Se utiliza para enviar un mensaje a _todos_ los dispositivos de esa red simultáneamente.

![](Direcciones%20de%20red,%20de%20host%20y%20de%20difusión.png)

---

**Características de la Dirección de Red**

Representa a un segmento de red específico. Para que un dispositivo se considere parte de una red, debe cumplir 3 criterios estrictos:

Compartir la misma **máscara de subred**.

Poseer exactamente los mismos **bits en la porción de red**.

Estar físicamente (o lógicamente a través de VLANs) en el mismo **dominio de difusión** (_broadcast domain_) que los demás equipos.

**OJO:** Esta dirección **nunca se le puede asignar a un dispositivo** (ni a una PC, ni a la interfaz de un router).

![](Características%20de%20la%20Dirección%20de%20Red.png)

---

**Direcciones de Host**

Son las IP utilizables que se pueden asignar a los dispositivos de una red (computadoras, impresoras, interfaces de routers, etc.).

**Regla de asignación:** En la porción de host (la que corresponde a los `0` en la máscara de subred), se permite cualquier combinación de bits **excepto dos**:

Todos los bits en `0` (reservada para la Dirección de Red).

Todos los bits en `1` (reservada para la Dirección de Broadcast).

**Unicidad:** Todo equipo en la misma red debe compartir la misma porción de red y máscara, pero su porción de host debe ser **estrictamente única**.

**Rango de Direcciones Utilizables** Para saber qué IPs puedes asignar a tus equipos, identificas los límites:

**Primera dirección de host:** Tiene todos los bits de la porción de host en `0`, excepto el último bit a la extrema derecha que es `1` (Ej: `192.168.10.1/24`).

**Última dirección de host:** Tiene todos los bits de la porción de host en `1`, excepto el último bit a la extrema derecha que es `0` (Ej: `192.168.10.254/24`).

---

**Dirección de Broadcast (Difusión)**

**Propósito:** Se utiliza exclusivamente cuando se necesita enviar un mensaje o paquete a **todos los dispositivos** de una red IPv4 de forma simultánea.

**Regla de Oro (Nivel de bits):** Para identificarla, **todos los bits correspondientes a la porción de host deben ser `1`**.

**Ejemplo:** En una red `/24`, el último octeto de la dirección de broadcast siempre será `255` (ej. `192.168.10.255/24`).

**Restricción de uso:** Al igual que ocurre con la dirección de red, la dirección de broadcast está reservada y **nunca se le puede asignar a un dispositivo**.

---

