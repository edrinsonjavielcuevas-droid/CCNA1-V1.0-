---

---

----

#### Dominios de Difusión y Segmentación

**Concepto de Difusión:** En una red, es como un correo enviado a "todos". Aunque es necesario (ej. para encontrar dispositivos mediante ARP o solicitar una IP mediante DHCP), a menudo genera tráfico innecesario para quienes no necesitan la información.

**Comportamiento de los Switches:** Los switches son "transparentes" a la difusión. Si un switch recibe un paquete de difusión, lo propaga por **todas sus interfaces** (excepto por la que entró), extendiendo el alcance del tráfico a todos los dispositivos y switches conectados.

**Dominio de Difusión:** Es el área de la red donde un mensaje de difusión llega a todos los dispositivos.

**¿Por qué necesitamos segmentar?** 

Sin control, la difusión puede saturar una red grande. Para limitar su alcance y mejorar el rendimiento, se utilizan **routers**, los cuales actúan como barreras naturales que **no reenvían** las tramas de difusión, segmentando así la red en dominios de difusión más pequeños y manejables.

![](../IMG/MODULO11IMG/Dominio%20de%20difusi'on.png)

---
#### Optimización de Redes: División en Subredes

**El Problema:** Un dominio de difusión demasiado grande (muchos hosts en una misma red) provoca un tráfico excesivo de paquetes de difusión. Esto satura el ancho de banda y degrada el rendimiento de los dispositivos, que deben procesar cada una de estas señales constantemente.

**La Solución:** Dividir la red grande en segmentos más pequeños mediante la **división en subredes** (_subnetting_).

Al segmentar, cada subred actúa como su propio dominio de difusión independiente. Por ejemplo, una red `/16` original se puede fragmentar en múltiples redes `/24`, confinando el tráfico de difusión solo a los hosts de su propio segmento y evitando que se propague a otros.

**El Mecanismo:** Esto se logra ajustando la **longitud del prefijo**: se toman bits de la porción de host y se asignan a la porción de red para crear nuevas subredes.

**Nota:** Aunque técnicamente "subred" y "red" tienen definiciones distintas, en la práctica profesional se usan frecuentemente como sinónimos para referirse a cualquier bloque de direccionamiento funcional.

![](../IMG/MODULO11IMG/Un%20dominio%20de%20difusión%20amplio.png)

![](../IMG/MODULO11IMG/Comunicación%20entre%20red.png)

---
#### Razones para segmentar una red:

**Ubicación:**

![](../IMG/MODULO11IMG/DIvisión%20de%20una%20red%20por%20ubicación.png)

---

**Grupo o fusión:**

![](../IMG/MODULO11IMG/Subredes%20por%20grupo%20o%20fusión.png)

---

**Tipo de dispositivo:**

![](../IMG/MODULO11IMG/TIpos%20de%20dispositivos%20para%20subnetting.png)

---

