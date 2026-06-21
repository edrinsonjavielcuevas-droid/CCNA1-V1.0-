
---

Un servidor asigna un número de puerto único a cada proceso de aplicación para poder gestionar múltiples servicios simultáneamente; no puede haber dos servicios distintos escuchando en el mismo puerto. Cuando una aplicación está activa en su puerto, el sistema la marca como "abierta", lo que permite a la capa de transporte recibir, procesar y entregar las solicitudes de los clientes dirigidas a ese socket específico.

**Procesos del servidor TCP**

| **Proceso**                         | **Descripción**                                                                                         |
| ----------------------------------- | ------------------------------------------------------------------------------------------------------- |
| **Clientes Envían Solicitudes TCP** | El cliente inicia la comunicación enviando un segmento al servidor para establecer la conexión.         |
| **Solicitar Puertos de Destino**    | El cliente especifica el puerto del servicio que desea acceder en el servidor (ej. puerto 80 para web). |
| **Solicitar Puertos de Origen**     | El cliente genera dinámicamente un puerto local para identificar su propia sesión de respuesta.         |
| **Respuesta de Puertos de Destino** | El servidor responde utilizando como destino el puerto que el cliente generó dinámicamente.             |
| **Respuesta de Puertos de Origen**  | El servidor utiliza su puerto de servicio (ej. 80) como origen para enviar los datos al cliente.        |

---

**Clientes envían solicitudes TCP**

![](Clientes%20envían%20solicitudes%20TCP.png)

---

**Solicitud de puertos de destino**

![](Solicitud%20de%20puertos%20de%20destino.png)

---

**Terminar sección TCP**

![](Terminar%20sección%20TCP.png)


---

### El Enlace de Tres Vías (Three-Way Handshake)

Es el proceso formal para establecer una conexión **full-duplex** entre un cliente y un servidor. Sus tres funciones principales son:

1. **Confirmar presencia:** Asegura que el dispositivo de destino esté activo y conectado.

2. **Validar servicio:** Verifica que el puerto de destino deseado esté escuchando y acepte conexiones.

3. **Iniciar sesión:** Sincroniza los números de secuencia iniciales entre ambos dispositivos para permitir la comunicación bidireccional.

### Los 6 Bits de Control (Marcadores o Flags)

Son indicadores en el encabezado TCP que dictan el estado y el flujo de la conexión:

| **Marcador** | **Nombre**  | **Función Principal**                                                                   |
| ------------ | ----------- | --------------------------------------------------------------------------------------- |
| **SYN**      | Synchronize | Sincroniza números de secuencia al **iniciar** la conexión.                             |
| **ACK**      | Acknowledge | Indica un acuse de recibo; confirma que los datos llegaron.                             |
| **FIN**      | Finish      | Finaliza la sesión; informa que no hay más datos por enviar.                            |
| **RST**      | Reset       | Reinicia bruscamente la conexión (usado ante errores graves).                           |
| **URG**      | Urgent      | Indica que el segmento contiene datos que deben procesarse con prioridad.               |
| **PSH**      | Push        | Solicita que los datos se entreguen a la aplicación inmediatamente (función de empuje). |
**Nota técnica:** Los tres primeros (**SYN, ACK, FIN**) son los que gestionan el ciclo de vida de la conexión (establecer y cerrar), mientras que los otros controlan el comportamiento durante la transmisión.

---

**Campos de bits de control**

![](Campos%20de%20bits%20de%20control.png)


---

