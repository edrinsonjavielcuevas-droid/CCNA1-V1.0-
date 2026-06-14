
---

### Configuración de GUA estática en un router:

Configurar una **GUA IPv6** es sumamente intuitivo si ya conoces el proceso en IPv4; la lógica es idéntica, con la principal diferencia de que el prefijo `ip` es sustituido por `ipv6` en los comandos.

**Sintaxis de configuración**

Mientras que en IPv4 usas `ip address [dirección] [máscara]`, en IPv6 el comando es: `ipv6 address [ipv6-address]/[prefix-length]`

**Regla fundamental:** A diferencia de IPv4, **no debe haber espacio** entre la dirección IPv6 y la longitud del prefijo (la barra `/`).

**Ejemplo práctico:** Si vas a configurar la subred `2001:db8:acad:1::/64` en una interfaz, el comando sería: `ipv6 address 2001:db8:acad:1::1/64`

**Nota de estudio:** Recuerda que al configurar una GUA, es una excelente práctica configurar también la LLA de forma estática en la misma interfaz, para tener control total sobre la puerta de enlace que usarán tus dispositivos.


**Topología de ejemplo**

![](../IMG/MODULO12IMG/Topología%20de%20ejemplo.png)

El ejemplo muestra los comandos necesarios para configurar la GUA IPv6 en GigabitEthernet 0/0/0, GigabitEthernet 0/0/1 y la interfaz Serial 0/1/0 de R1.

### Configuración de IPv6 GUA en el router R1

![](../IMG/MODULO12IMG/Configuración%20de%20IPv6%20GUA%20en%20el%20router%20R1.png)

----

**Configuración de GUA estática en un host de Windows**

Configurar la dirección IPv6 en un host de forma manual es similar a configurar una dirección IPv4.

Como se muestra en la figura, la dirección de puerta de enlace predeterminada configurada para PC1 es 2001: db8: acad: 1 :: 1. Esta es la GUA de la interfaz R1 GigabitEthernet en la misma red. Alternativamente, la dirección de puerta de enlace predeterminada se puede configurar para que coincida con el LLA de la interfaz GigabitEthernet. El uso de la LLA del enrutador como dirección de puerta de enlace predeterminada se considera una práctica recomendada. Cualquiera de las dos configuraciones funciona.

![](../IMG/MODULO12IMG/Configuración%20de%20GUA%20estática%20en%20un%20host%20de%20Windows.png)

En redes grandes, la asignación dinámica es indispensable. Los clientes obtienen su **GUA** mediante dos métodos:

**SLAAC:** El dispositivo obtiene el prefijo del router y genera su propio ID de interfaz automáticamente.

**DHCPv6 (con estado):** Un servidor asigna las direcciones y gestiona el registro de clientes.

**Dato clave:** En ambos métodos, la **LLA** del router se configura automáticamente como la **puerta de enlace predeterminada** del dispositivo.

---

**Configuración estática de una dirección de unidifusión local de enlace**

Aquí tienes el resumen al grano:

Configurar una **LLA (Link-Local Address)** manualmente permite crear direcciones simples y fáciles de recordar (útil principalmente en routers), lo que facilita su gestión como puerta de enlace predeterminada.

**Comando:** `ipv6 address [dirección] link-local`

**Regla:** Si la dirección está en el rango `fe80` a `febf`, es obligatorio añadir el parámetro `link-local` al final del comando.

**Ejemplo:** `ipv6 address fe80::1 link-local`

**Ejemplo de topología con LLAS**

![](../IMG/MODULO12IMG/Ejemplo%20de%20topología%20con%20LLAS.png)

El ejemplo muestra la configuración de un LLA en el router R1.

![](../IMG/MODULO12IMG/El%20ejemplo%20muestra%20la%20configuración%20de%20un%20LLA%20en%20el%20router%20R1.png)

Las LAs configuradas estáticamente se utilizan para hacerlas más fácilmente reconocibles como pertenecientes al router R1. En este ejemplo, todas las interfaces del router R1 se han configurado con un LLA que comienza con **fe80::1:**_n_ y un dígito único «n» a la derecha. El «**1**» representa el router R1.

Siguiendo la misma sintaxis que el router R1, si la topología incluía el router R2, tendría sus tres interfaces configuradas con las LAs fe80:: 2:1, fe80:2:2 y fe80:: 2:3.

**Nota:** Se podría configurar exactamente la misma LLA en cada enlace siempre que sea único en ese enlace. Esto se debe a que los LLA solo tienen que ser únicos en ese enlace. Sin embargo, la práctica común es crear un LLA diferente en cada interfaz del router para facilitar la identificación del router y la interfaz específica.

---

