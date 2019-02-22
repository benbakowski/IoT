---

copyright:
  years: 2017, 2019
lastupdated: "2019-02-13"
---

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:important: .important}


# Simulación de datos de dispositivo
{: #sim_device_data}

<p>Esta recopilación de documentación de {{site.data.keyword.Bluemix}} pertenece al plan de precios Lite de {{site.data.keyword.iot_full}} e incluye información básica de iniciación, referencias de API e información general de resolución de problemas. 
Para obtener la documentación completa de {{site.data.keyword.iot_short_notm}}, consulte la [documentación de producto de {{site.data.keyword.iot_short_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html) en IBM Knowledge Center. Encontrará más información acerca de los distintos planes en [planes de servicios de {{site.data.keyword.iot_short_notm}}](/docs/IoT/plans_overview.html#plans_overview). 
</p>
{: important}

Utilizando el simulador de dispositivos de {{site.data.keyword.iot_full}}, puede configurar sucesos simulados para dispositivos. Puede utilizar los datos de suceso de dispositivo para aprender, probar y demostrar la funcionalidad completa de las características de {{site.data.keyword.iot_short_notm}}.
{: shortdesc}

Puede utilizar tipos de dispositivo existentes y dispositivos y el simulador le permite generar nuevos dispositivos de tipos existentes. Puede configurar los detalles de suceso de cada dispositivo o definir una configuración predeterminada que se aplique a todos los dispositivos. Puede exportar una configuración de suceso de simulado para poder volver a utilizarla o compartirla para configurar otras simulaciones.

Para simular datos de dispositivo:

1. Inicie una sesión en {{site.data.keyword.iot_short_notm}}.
2. En el panel de navegación principal, seleccione **Valores**.
3. En la sección **Datos y dispositivos** active el simulador de dispositivo.
4. En el panel de navegación principal, seleccione **Dispositivos**. Un mensaje en la esquina inferior derecha de la pantalla indica que no se están ejecutando simulaciones.
5. Pulse en el mensaje "Se están ejecutando 0 simulaciones".
6. En la ventana emergente **Simulaciones**, pulse **Crear simulación**.
7. Seleccione un tipo de dispositivo existente para el que desee simular datos o cree un nuevo tipo de dispositivo escribiendo el nombre de tipo de dispositivo.
8. Pulse **Importar/Exportar simulación** para utilizar una configuración existente o configurar manualmente los detalles de la simulación para el tipo de dispositivo:
   1. Pulse **+ Tipo de suceso nuevo** para añadir un tipo de suceso al tipo de dispositivo.
   2. Escriba un nombre para el tipo de suceso.
   3. En **Planificación**, establezca la frecuencia del suceso.
   3. Edite los detalles del tipo de suceso en formato JSON y guarde el tipo de suceso actualizado.

   <p> Puede utilizar las variables especiales siguientes al configurar sucesos:  
        - `range`: Esta variable se sustituye con un número aleatorio entre los dos valores proporcionados, por ejemplo: `{"random": range(300, 100)}`  
        - `$counter`: Esta variable se sustituye con el número de dispositivos añadidos en el simulador para el tipo actual, por ejemplo: `{"total": $counter}`  
        - `increment`: Esta variable indica el número de inicio y el número en el que se incrementa, por ejemplo, `{"myNumber": increment(10, 1)}`. En este caso, `myNumber` se inicia en 10 y aumenta en 1 cada vez que se envía una carga útil (10, 11, 12, etc.).</p>
   {: tip}

9. Seleccione un dispositivo registrado para la simulación o cree un nuevo dispositivo escribiendo el nombre del dispositivo.
10. Para crear más simulaciones, pulse **Nueva simulación** y repita los pasos de configuración para cada dispositivo en el que desee aplicar los valores personalizados. El mensaje en la parte inferior derecha de la pantalla muestra el número de simulaciones activas.
11. **Opcional:** Después de configurar simulaciones para dispositivos, exporte los detalles de la simulación para que se puedan reutilizar o compartir:
    1. En la ventana emergente **Simulaciones**, pulse **Importación y exportación**.
    2. Seleccione el separador **Exportar**.
    3. Copie los detalles de la simulación en el portapapeles o descárguelos en un archivo JSON.
12. En la página **Dispositivos**, navegue hasta uno de los dispositivos simulados y seleccione el separador **Sucesos recientes** para verificar que los sucesos simulados están funcionando.
