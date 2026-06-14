
---
### LLA dinámicos:

Todo dispositivo IPv6 debe tener una LLA obligatoria. Tanto las LLA como las GUA pueden configurarse manual o dinámicamente. Es fundamental verificar siempre la configuración de todas las direcciones IPv6 en las interfaces para asegurar que la red funcione correctamente.

La figura muestra que el LLA se crea dinámicamente usando el prefijo fe80 :: / 10 y la ID de interfaz usando el proceso EUI-64, o un número de 64 bits generado aleatoriamente.

![](../IMG/MODULO12IMG/LLA%20dinámicos.png)

---

**LLA dinámicos en Windows**

Los sistemas operativos, como Windows, suelen utilizar el mismo método tanto para una GUA creada por SLAAC como para una LLA asignada dinámicamente. Vea las áreas resaltadas en los siguientes ejemplos que se mostraron anteriormente.

**ID de interfaz generada mediante EUI-64**

![](../IMG/MODULO12IMG/ID%20de%20interfaz%20generada%20mediante%20EUI-64.png)

**ID de interfaz de 64 bits generada aleatoriamente**

![](../IMG/MODULO12IMG/ID%20de%20interfaz%20de%2064%20bits%20generada%20aleatoriamente.png)

---

**LLA dinámicos en enrutadores Cisco**

**Generación automática:** Los routers Cisco crean un LLA automáticamente al asignar una GUA, usando el proceso EUI-64 por defecto.

**Interfaces seriales:** Utilizan la dirección MAC de una interfaz Ethernet para generar su LLA.

**Desventaja:** La LLA dinámica es difícil de recordar debido a su ID de interfaz larga.

**Recomendación:** Es común configurar las LLA de forma estática para facilitar su identificación y administración.

**IPv6 LLA con EUI-64 en el router R1**

![](../IMG/MODULO12IMG/IPv6%20LLA%20con%20EUI-64%20en%20el%20router%20R1.png)

**Verifique la configuración de la dirección IPv6**

La figura muestra el ejemplo de topología.

![](../IMG/MODULO12IMG/Verifique%20la%20configuración%20de%20la%20dirección%20IPv6.png)

---

**Comandos de Verificación IPv6**

| **Comando**                 | **Función principal**                                                                                      |
| --------------------------- | ---------------------------------------------------------------------------------------------------------- |
| `show ipv6 interface brief` | Muestra un resumen del estado de las interfaces (Capa 1 y 2) y las direcciones IPv6 asignadas (GUA y LLA). |
| `show ipv6 route`           | Muestra la tabla de enrutamiento IPv6 para verificar las rutas aprendidas y redes conectadas.              |
| `ping`                      | Prueba la conectividad extremo a extremo con otro dispositivo habilitado para IPv6 en la red.              |

---

