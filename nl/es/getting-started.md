---

copyright:
  years: 2016, 2019
lastupdated: "2019-04-16"

keywords: IoT device, Watson IoT Platform, Watson IoT Platform service plans

subcollection: iot-platform

---

{:new_window: target="\_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:important: .important}


# Guía de aprendizaje de iniciación
{: #getting-started}

<p>Esta recopilación de documentación de {{site.data.keyword.cloud}} pertenece al plan de precios Lite de {{site.data.keyword.iot_full}} e incluye información básica de iniciación, referencias de API e información general de resolución de problemas. 
Para obtener la documentación completa de {{site.data.keyword.iot_short_notm}}, consulte la [documentación de producto de {{site.data.keyword.iot_short_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html) en IBM Knowledge Center. Encontrará más información acerca de los distintos planes en [Planes del servicio {{site.data.keyword.iot_short_notm}}](/docs/services/IoT?topic=iot-platform-plans_overview#plans_overview). 
</p>
{: important}

En esta guía de aprendizaje de iniciación de {{site.data.keyword.iot_short_notm}}, se conectará un dispositivo IoT a {{site.data.keyword.iot_short_notm}}.
{:shortdesc}

## Acerca de esta tarea
{: #about .sectiontitle}  

Antes de empezar a recibir datos desde los dispositivos de IoT, debe conectarlos a {{site.data.keyword.iot_short_notm}}. La conexión de un dispositivo a {{site.data.keyword.iot_short_notm}} implica el registro del dispositivo con {{site.data.keyword.iot_short_notm}} y, a continuación, el uso de la información de registro para configurar el dispositivo para conectarlo a {{site.data.keyword.iot_short_notm}}.

## Antes de empezar
{: #byb .sectiontitle}  

Antes de empezar a utilizar {{site.data.keyword.iot_short_notm}}, debe tener los elementos siguientes:  
* Una [cuenta de {{site.data.keyword.cloud}}![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://cloud.ibm.com/registration/){: new_window}.
* Una instancia de {{site.data.keyword.iot_short_notm}}.  
Puede crear una instancia de {{site.data.keyword.iot_short_notm}} directamente desde la [página de {{site.data.keyword.iot_short_notm}} del Catálogo de servicios de {{site.data.keyword.cloud_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/catalog/services/internet-of-things-platform/){:new_window}.  
* Un dispositivo que cumple los requisitos siguientes:  
  *	El dispositivo debe poder comunicarse mediante protocolos HTTP o MQTT.
  * Los mensajes del dispositivo deben ajustarse a los requisitos de carga útil de mensajes de {{site.data.keyword.iot_short_notm}}.  
Para obtener más información, consulte [Desarrollo de dispositivos en {{site.data.keyword.iot_short_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/devices/device_dev_index.html){: new_window}.

Explore las opciones siguientes en función de su situación:

 |  |   El servicio se despliega | El servicio no se despliega
 | -------------| ------------- | -------------
  |**Tengo ningún dispositivo que conectar** | Siga el proceso que se describe en este tema. | Explore la conexión de dispositivos en el apartado sobre [Practicar con {{site.data.keyword.iot_short_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://discover-iot.eu-gb.mybluemix.net/?cm_mc_uid=44491599487314618721024&cm_mc_sid_50200000=1462798151#/play){:new_window}.
  |**No tengo un dispositivo para conectar** | [Simule datos de dispositivo](/docs/services/IoT?topic=iot-platform-sim_device_data#sim_device_data) o [Conecte su teléfono inteligente ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://discover-iot.eu-gb.mybluemix.net/?cm_mc_uid=44491599487314618721024&cm_mc_sid_50200000=1462798151#/play/device/smartphone){:new_window}. | Iníciese en [{{site.data.keyword.iot_short_notm}} Starter](https://cloud.ibm.com/docs/IoT-starter?topic=iot-starter-gettingstartedtemplate#gettingstartedtemplate){:new_window}.



## Paso 1: Registrar su dispositivo
{: #step1 .sectiontitle}  
El registro de un dispositivo implica la clasificación del dispositivo como un tipo de dispositivo, lo que le da un nombre al dispositivo, y proporciona una información de dispositivo. A continuación, proporcione una señal de conexión o acepte una señal generada por {{site.data.keyword.iot_short_notm}}.

**Sugerencia:** Puede registrar los dispositivos uno a uno desde el [panel de control de {{site.data.keyword.iot_short_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://internetofthings.ibmcloud.com){: new_window}, o puede utilizar la [API de {{site.data.keyword.iot_short_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/org-admin.html#!/Device_Bulk_Configuration/post_bulk_devices_add){: new_window} para añadir varios dispositivos.

Para añadir un dispositivo desde el panel de control de {{site.data.keyword.iot_short_notm}}:
1. En la consola de {{site.data.keyword.cloud_notm}}, pulse **Iniciar** en la página de detalles de servicio de {{site.data.keyword.iot_short_notm}}.

    Se abre la consola web de {{site.data.keyword.iot_short_notm}} en un nuevo separador del navegador con el siguiente URL:

    ```
    https://org_id.internetofthings.ibmcloud.com/dashboard/#/overview
    ```

    Donde *org_id* es el ID de la organización de {{site.data.keyword.iot_short_notm}}.

2. En el panel de control Visión general, desde el panel del menú, seleccione **Dispositivos** y, a continuación, pulse **Añadir dispositivo**.

3. Cree un tipo de dispositivo para el dispositivo que está añadiendo.

    Cada dispositivo conectado al {{site.data.keyword.iot_short_notm}} debe estar asociado con un tipo de dispositivo. Los tipos de dispositivos son grupos de dispositivos que comparten características comunes.

    1. Pulse **Crear tipo de dispositivo**.
    2. Especifique un nombre de dispositivo como, por ejemplo, `my_device_type` y una descripción para dicho tipo de dispositivo.

        > **Nota:** El nombre del tipo de dispositivo no debe tener más de 36 caracteres y solo puede contener caracteres alfanuméricos (a-z, A-Z, 0-9) y cualquiera de los siguientes caracteres: `_`, `.` y `-`.

    3. Opcional: Especifique los atributos y metadatos de tipo de dispositivo.

        Puede añadir y editar atributos y metadatos más tarde.
        {: tip}

4. Pulse **Siguiente** para empezar el proceso de adición de su dispositivo con el tipo de dispositivo seleccionado.

5. Especifique un ID de dispositivo como, por ejemplo, `my_first_device`.

    Este ID de dispositivo se utiliza para identificar el dispositivo en el panel de control de {{site.data.keyword.iot_short_notm}} y también un parámetro obligatorio para conectar el dispositivo a {{site.data.keyword.iot_short_notm}}.

    > **Nota:** El nombre del tipo de dispositivo no debe tener más de 36 caracteres y solo puede contener caracteres alfanuméricos (a-z, A-Z, 0-9) y cualquiera de los siguientes caracteres: `_`, `.` y `-`.

    Para los dispositivos conectados a la red, el ID de dispositivo podría ser la dirección MAC del dispositivo sin los dos puntos de separación.

5. Pulse **Siguiente** para completar el proceso.

6. Proporcione una señal de autenticación o acepte un token generado automáticamente. Si elige crear su propia señal, asegúrese de que tiene entre 8 y 36 caracteres de longitud y solo consta de caracteres alfanuméricos y: `_`, `.`, `!`, `&`, `@`, `?`, `\*`, `+`, `(`, `)` y `-`.

    La señal no debe contener secuencias de caracteres repetidos, palabras de diccionario, nombres de usuario ni otras secuencias predefinidas.

7. Verifique que la información de resumen sea correcta y, a continuación, pulse **Añadir** para añadir la conexión.

8. En la página de información de dispositivos, copie y guarde los siguientes detalles:

    * ID de organización
    * Tipo de dispositivo
    * ID de dispositivo
    * Método de autenticación
    * Señal de autenticación

    Necesitará el ID de organización, el tipo de dispositivo, el ID de dispositivo y la señal de autenticación para configurar su dispositivo para conectarse a {{site.data.keyword.iot_short_notm}}.

## Paso 2: Conectar el dispositivo a {{site.data.keyword.iot_short_notm}}
{: #step2 .sectiontitle}  

Después de registrar un dispositivo con {{site.data.keyword.iot_short_notm}}, puede utilizar la información de registro para conectar el dispositivo y empezar a recibir datos de dispositivo.

**Sugerencia:** Hay recetas de conexión disponibles para algunos dispositivos de uso común en [Recetas de conexión de dispositivo ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://developer.ibm.com/recipes/tutorials/category/internet-of-things-iot/){: new_window} en {{site.data.keyword.IBM_notm}}.com.

Para conectar un dispositivo a {{site.data.keyword.iot_short_notm}}:
1. Configure el dispositivo para la mensajería MQTT y la autenticación con la ayuda del ID de organización, el tipo de dispositivo, el ID de dispositivo y la señal de autenticación.

2. Envíe mensajes de dispositivo a la organización de {{site.data.keyword.iot_short_notm}} utilizando el protocolo de MQTT.

    Se necesita la siguiente información al conectar el dispositivo:

    * URL: *org_id*.messaging.internetofthings.ibmcloud.com

      Donde *org_id* es el ID de la organización de {{site.data.keyword.iot_short_notm}}.

    * Puerto:
      * 1883
      * 8883 (cifrado)
      * 443 (websockets)
    * ID de dispositivo: d:_org_id:device_type:device_id_
    * Nombre de usuario: use-token-auth
    * Contraseña: _Señal de autenticación_
    * Formato de tema de suceso: iot-2/evt/_event_id/fmt/format_string_

      Donde _event_id_ especifica el nombre de suceso que se muestra en {{site.data.keyword.iot_short_notm}} y _format_string_ es el formato del suceso, como por ejemplo JSON.

    * Formato del mensaje: JSON

  Para obtener más información, consulte [Conectividad de MQTT para los dispositivos ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/devices/mqtt.html){:new_window}.


## Qué hacer a continuación  
{: #related .sectiontitle}

Amplíe las características de análisis de datos de creando y conectando sus propias apps para consumir datos de dispositivos.
- Para obtener más información sobre cómo conectarse a tipos de dispositivos específicos a {{site.data.keyword.iot_short_notm}}, consulte [Recetas de developerWorks ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://developer.ibm.com/recipes/tutorials/category/internet-of-things-iot/){:new_window}.
- Extraiga herramientas de las [bibliotecas de cliente ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/iot_platform_client_lib.html){:new_window} para crear código para integrar y conectar sus dispositivos y apps.
- Explore la [Documentación de API de {{site.data.keyword.iot_short_notm}}](/docs/services/IoT?topic=iot-platform-api_overview#api_overview).
- [Conecte un servicio de {{site.data.keyword.cloudantfull}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/cloudant_connector.html){:new_window} a {{site.data.keyword.iot_short_notm}} para almacenar datos de dispositivos históricos.
- Para aprovechar todas [las funciones de {{site.data.keyword.iot_short_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html){:new_window}, puede adquirir uno de los planes de servicio de conexión y análisis y, a continuación, migrar el entorno existente.

Para migrar planes, póngase en contacto con el representante de {{site.data.keyword.IBM}} o cree una incidencia de soporte.

También hay disponible en la documentación de producto de {{site.data.keyword.iot_short_notm}} en {{site.data.keyword.IBM_notm}} Knowledge Center un conjunto más detallado de guías de iniciación y aplicaciones de muestra que le guían a través de las bases del desarrollo de un sistema prototipo de IoT completo listo para producción con {{site.data.keyword.iot_short_notm}}. Si es un desarrollador que no ha trabajado antes con {{site.data.keyword.iot_short_notm}}, utilice los procesos paso a paso de la sección [Guías de iniciación ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/getting_started/getting-started-iot-overview.html#getting-started){:new_window}.
