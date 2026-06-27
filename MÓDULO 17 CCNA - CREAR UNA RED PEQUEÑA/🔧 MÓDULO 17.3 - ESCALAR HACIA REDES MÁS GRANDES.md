
---

Para escalar una red de manera inteligente conforme la empresa crece, es necesario realizar una planificación basada en cuatro pilares fundamentales:

**Documentación de la red:** Mantener actualizadas las topologías tanto físicas (cables, ubicación de equipos) como lógicas (esquemas de direccionamiento IP, VLANs).

**Inventario de dispositivos:** Registro detallado de todos los equipos que conforman la red, incluyendo sus especificaciones y estado actual.

**Presupuesto de TI:** Planificación financiera anual que contemple la adquisición necesaria de hardware y software para soportar el crecimiento.

**Análisis de tráfico:** Monitoreo constante de qué protocolos, aplicaciones y servicios se están ejecutando, para determinar los requisitos reales de ancho de banda y rendimiento.

---

El análisis de protocolos, utilizando herramientas como **Wireshark**, es esencial para comprender el comportamiento de una red en crecimiento. Al capturar y examinar el flujo de datos, un administrador puede tomar decisiones informadas sobre cómo optimizar la red.

### Recomendaciones para un análisis efectivo:

**Horarios estratégicos:** Capture tráfico durante las **horas pico** de uso para obtener una muestra representativa de la carga real y de los tipos de tráfico que compiten por el ancho de banda.

**Segmentación:** Realice capturas en **diferentes segmentos y dispositivos** de la red. Esto es crítico porque gran parte del tráfico es local y no atraviesa toda la infraestructura.

### Aplicación de los resultados:

La información recopilada se evalúa basándose en el **origen, destino y tipo de tráfico**. Con estos datos, se pueden ejecutar acciones correctivas:

**Reducción de ruido:** Eliminar flujos de tráfico innecesarios.

**Reubicación de recursos:** Trasladar servidores o servicios a diferentes segmentos de la red para equilibrar la carga.

**Rediseño:** En casos de crecimiento sostenido, los datos pueden justificar una intervención mayor o el rediseño de la infraestructura principal para adaptar el rendimiento a las necesidades crecientes.

Esta metodología convierte la observación pasiva en una estrategia activa para mejorar la eficiencia y escalabilidad de la red.

![](WIreshark.png)

---

|**Herramienta de Windows**|**Función Principal**|
|---|---|
|**Administrador de tareas**|Visualización en tiempo real de la utilización de CPU, RAM, unidades de almacenamiento y consumo de red de aplicaciones activas.|
|**Visor de eventos**|Registro detallado sobre el funcionamiento del sistema y posibles errores.|
|**Uso de datos**|Identificación de las aplicaciones que han consumido ancho de banda en los últimos 30 días.|

**Notas importantes para la administración de red:**

Documentar estas "instantáneas" de información ayuda a identificar requisitos de crecimiento y flujos de tráfico asociados.

Un cambio en la utilización de los recursos puede obligar al administrador a ajustar la asignación de recursos de red.

La herramienta de Uso de datos se accede a través de: **Settings > Network & Internet > Data usage > network interface**.


![](Detalles%20de%20uso.png)

----


