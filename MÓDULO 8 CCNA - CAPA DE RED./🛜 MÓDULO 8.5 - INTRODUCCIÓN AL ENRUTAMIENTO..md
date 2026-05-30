
---

### Decisión de Envío de Paquetes del Router

Cuando un paquete originado en un host llega a la interfaz de un router (habitualmente funcionando como la puerta de enlace predeterminada para tráfico remoto), el dispositivo intermedio ejecuta un proceso lógico en la Capa de Red para determinar el reenvío:

**Examen de destino:** El router inspecciona el encabezado del paquete entrante para extraer la dirección IP de destino.

**Consulta de la tabla de enrutamiento:** El dispositivo compara esta dirección IP con las entradas almacenadas en su propia tabla de enrutamiento. Esta tabla contiene una base de datos de direcciones de red conocidas (prefijos) y las instrucciones sobre dónde y por qué interfaz reenviar el tráfico.

**Criterio de la coincidencia más larga (_Longest Match_):** Para tomar la decisión final de reenvío, el router evalúa todas las rutas posibles y selecciona estrictamente la entrada que tenga la mayor coincidencia de bits con la dirección IP de destino. Esto garantiza que el paquete se envíe por la ruta más específica y exacta disponible en la topología.

![](../IMG/MODULO8IMG/Decisión%20de%20Envío%20de%20Paquetes%20del%20Router.png)

**Tabla de ruteo R1**

![](../IMG/MODULO8IMG/Tabla%20de%20ruteo%20R1.png)

---

**Tabla de enrutamiento IP del router**

La tabla de enrutamiento de un router actúa como una base de datos que almacena todos los destinos de red conocidos, clasificando las rutas en tres categorías principales:

**Redes conectadas directamente:** Corresponden a las interfaces físicas o lógicas operativas del propio router. Estas rutas se registran automáticamente en la tabla de enrutamiento en el momento en que a una interfaz se le asigna una dirección IP y cambia a estado activo (_up_).

**Redes remotas:** Son segmentos de red que no están conectados físicamente al router local, sino que se alcanzan a través de otros dispositivos intermediarios. El router aprende sobre estas rutas mediante configuración estática manual por parte del administrador de red, o mediante el intercambio automatizado de información usando protocolos de enrutamiento dinámico.

**Ruta predeterminada (_Default Route_):** Funciona como la ==puerta de enlace de último recurso==. El router utiliza esta entrada exclusivamente para encaminar paquetes cuyo destino no tiene una coincidencia específica (o coincidencia más larga) dentro de las otras entradas de la tabla de enrutamiento.

La siguiente figura muestra redes directamente conectadas y remotas del router R1.

![](../IMG/MODULO8IMG/Tabla%20de%20enrutamiento%20IP%20del%20router.png)

**OJO:** Un router puede descrubrir redes remotas de dos maneras.

**Manualmente:** Las redes remotas se inglesan manualmente en la tabla de rutas mediante rutas estáticas.

**Dinámicamente:** Las rutas remotas se aprenden automáticamente mediante un protocolo de enrrutamiento dinámica.

----

#### Enrutamiento estático

Son entradas de rutas que se configuran manualmente. Esta misma misma incluye la dirección de red remota y la dirección IP del router del salto siguiente.

![](../IMG/MODULO8IMG/Enrutamiento%20estático.png)

La principal limitación del enrutamiento estático es su incapacidad para adaptarse a las fallas o cambios en la topología de la red. Si un enlace principal se cae, la ruta no se actualiza automáticamente, lo que interrumpe la comunicación. Para restablecer el flujo de datos, un administrador de red debe intervenir y reconfigurar manualmente los dispositivos para indicarles el nuevo camino alternativo hacia el destino.

![](../IMG/MODULO8IMG/Enrutamiento%20estático2.png)

**Características del Enrutamiento Estático**

**Gestión manual:** Se configura a mano y no se adapta automáticamente a fallas; exige reconfiguración si la topología cambia.

**Escalabilidad:** Diseñado para redes pequeñas o topologías simples sin enlaces redundantes.

**Uso común:** Se utiliza frecuentemente en conjunto con protocolos dinámicos para definir la ruta predeterminada (_default route_).

---

**Enrutamiento dinámico:**  

**Descubrimiento autónomo:** Permite a los routers aprender automáticamente sobre redes remotas y rutas predeterminadas mediante el intercambio continuo de información entre dispositivos.

**Adaptabilidad a fallos:** Actualiza dinámicamente las tablas de enrutamiento en respuesta a cualquier cambio o caída en la topología de la red, eliminando la necesidad de reconfiguración manual por parte del administrador.

**Protocolos estándar:** Las implementaciones de enrutamiento dinámico más comunes en la industria incluyen OSPF y EIGRP.

La siguiente imagen muestra como R1 y R2 comparten información de manera automatica mediante el protocolo de enrutamiento OSPF.

![](../IMG/MODULO8IMG/Enrutamiento%20dinámico.png)

**Operación y Configuración del Enrutamiento Dinámico**

La configuración base de un protocolo dinámico requiere únicamente que el administrador habilite las redes conectadas directamente al router. Una vez configurado, el protocolo ejecuta de manera autónoma las siguientes funciones:

**Descubrimiento:** Detecta automáticamente las redes remotas disponibles en la topología.

**Mantenimiento:** Mantiene la información de enrutamiento sincronizada y actualizada entre los dispositivos.

**Selección de ruta:** Calcula y elige el camino más eficiente (_best path_) hacia las redes de destino.

**Convergencia:** Encuentra y establece dinámicamente una nueva ruta óptima si el enlace principal sufre una caída.

---

**Registro en la Tabla de Enrutamiento:** Independientemente de si una ruta se aprende dinámicamente o se configura de forma estática, el router registra en su tabla de enrutamiento IP tanto la dirección de la red remota como la dirección del siguiente salto (_next hop_). La principal ventaja del método dinámico es su capacidad de reajustar automáticamente estos registros ante cualquier alteración en la infraestructura.

---

![](../IMG/MODULO8IMG/Operación%20y%20Configuración%20del%20Enrutamiento%20Dinámico.png)

**NOTA:** Actualmente es muy común que algunos routers usen ambos protocolos de enrutamiento.

----

**Introducción a una tabla de enrutamiento IPv4:**

En la configuración de tablas de enrutamiento IPv4, es una práctica estándar implementar arquitecturas híbridas que combinan métodos estáticos y dinámicos para optimizar el tráfico. En una topología típica, un router interno (R1) puede utilizar una ruta estática predeterminada (_default route_) para derivar todo el tráfico cuyo destino no tenga una coincidencia específica en su tabla hacia el router de borde (R2) con acceso a Internet; mientras que, de manera simultánea, ambos dispositivos emplean un protocolo de enrutamiento dinámico como OSPF para anunciar y sincronizar automáticamente la información de sus redes locales conectadas directamente.

![](../IMG/MODULO8IMG/Introducción%20a%20una%20tabla%20de%20enrutamiento%20IPv4.png)

![](../IMG/MODULO8IMG/Introducción%20a%20una%20tabla.png)

---

**Análisis de la Tabla de Enrutamiento IPv4 (`show ip route`)**

En los dispositivos Cisco IOS, la tabla de enrutamiento IPv4 se visualiza ejecutando el comando **`show ip route`** desde el modo EXEC privilegiado. Esta tabla almacena todas las rutas de destino conocidas por el router.

Cada entrada en la tabla inicia con un código identificador que indica el origen de la ruta (cómo fue aprendida). Los códigos más comunes son:

|**Código**|**Significado**|**Tipo de Enrutamiento**|
|---|---|---|
|**L**|**Local:** Dirección IP específica de la interfaz local del router.|Conectado directamente|
|**C**|**Conectada:** Red que está conectada directamente a una interfaz.|Conectado directamente|
|**S**|**Estática:** Ruta configurada manualmente por un administrador.|Estático|
|**O**|**OSPF:** Ruta aprendida dinámicamente mediante el protocolo OSPF.|Dinámico|
|**D**|**EIGRP:** Ruta aprendida dinámicamente mediante el protocolo EIGRP.|Dinámico|

#### **Clasificación de las Rutas en la Tabla**

**Rutas conectadas directamente (Códigos C y L):** Se generan de forma automática en el momento en que una interfaz del router se configura con una dirección IP y se activa. El sistema añade automáticamente la entrada **C** (que representa la dirección de red) y la entrada **L** (que representa la dirección IP exacta de la interfaz local). Estas entradas siempre especifican cuál es la interfaz de salida.

**Rutas dinámicas (Códigos O, D, etc.):** Son aquellas que el router aprende de manera automática al intercambiar información con otros routers vecinos utilizando protocolos como OSPF o EIGRP.

**Ruta predeterminada o _Default Route_ (Código S):** Se utiliza para enviar paquetes cuyos destinos no coinciden con ninguna otra entrada específica en la tabla. Su dirección de red consta de todos ceros (ej. `0.0.0.0` en IPv4). Cuando esta ruta se configura de forma estática, aparece en la tabla marcada con el código **`S*`** (el asterisco indica que es candidata a ruta predeterminada).

----

