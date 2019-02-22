---

copyright:
  years: 2016, 2019
lastupdated: "2019-02-13"

---

{:new_window: target="\_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:important: .important}

# Migración de {{site.data.keyword.iot_short_notm}} Lite a {{site.data.keyword.iot_short_notm}} de producción o de no producción
{: #org_migration}

<p>Esta recopilación de documentación de {{site.data.keyword.Bluemix}} pertenece al plan de precios Lite de {{site.data.keyword.iot_full}} e incluye información básica de iniciación, referencias de API e información general de resolución de problemas. 
Para obtener la documentación completa de {{site.data.keyword.iot_short_notm}}, consulte la [documentación de producto de {{site.data.keyword.iot_short_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html) en {{site.data.keyword.IBM}} Knowledge Center. Encontrará más información acerca de los distintos planes en [planes de servicios de {{site.data.keyword.iot_short_notm}}](/docs/IoT/plans_overview.html#plans_overview). 
</p>
{: important}

Una vez que haya "echado a andar" con Watson IoT Platform Lite y tenga claro cómo se adapta a su entorno de IoT, puede actualizar a [Watson IoT Platform de no producción o a uno de los planes de producción ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html){: new_window}.
{:shortdesc}

**Nota:** Este documento sólo está destinado a los usuarios que tienen una instancia de Lite. Si ha creado instancias de IoT Platform con los planes estándar o de seguridad avanzada, {{site.data.keyword.IBM}} le ayudará a migrar la instancia existente de {{site.data.keyword.iot_short_notm}} a los nuevos planes de producción o de no producción.

## Visión general del proceso de migración
{: #org_migration_overview}

Mediante la migración a {{site.data.keyword.iot_short_notm}}, se eliminan los límites del plan Lite de 500 dispositivos y el consumo de datos mensual.

Los planes de {{site.data.keyword.iot_short_notm}} incluyen los siguientes componentes adicionales para dar soporte a la arquitectura de aplicaciones IoT de extremo a extremo:

- {{site.data.keyword.messagehub}}: una versión alojada de {{site.data.keyword.IBM_notm}} de la plataforma de streaming Kafka que las aplicaciones pueden utilizar para recibir datos de IoT.
- {{site.data.keyword.dashdbshort}} para el almacenamiento de datos de análisis.
- {{site.data.keyword.cloudantfull}} DB para datos de series temporales.
- {{site.data.keyword.cos_full}} para la retención de datos a largo plazo.

En este documento se describen los tipos de datos que puede que desee migrar de una instancia de Lite existente a una versión completa.

**Nota:** en general, es más fácil configurar el entorno de producción o de no producción de {{site.data.keyword.iot_short_notm}} desde cero, ya que incluye componentes y características más allá del servicio {{site.data.keyword.iot_short_notm}} Lite. Además, los dispositivos y los usuarios creados para las pruebas en la versión Lite probablemente no serán los mismos que se utilizarán para la producción.

No obstante, si desea transferir algunos de los valores existentes de Lite, las secciones siguientes le indican los pasos a seguir.

La documentación de las [API de {{site.data.keyword.iot_short_notm}}](/docs/IoT/reference/api.html#api_overview) proporciona instrucciones sobre cómo invocar las API y su conjunto completo de parámetros.


## Antes de empezar
{: #org_migration_byb}

Para iniciar el proceso de migración, debe adquirir {{site.data.keyword.iot_short_notm}} (ya sea de producción o de no producción). Tras la compra, el equipo de operaciones de {{site.data.keyword.IBM_notm}} le suministrará una nueva instancia de {{site.data.keyword.iot_short_notm}}. Esto incluirá un nuevo ID de organización alfanumérico de seis caracteres.


## Migración de usuarios
{: #user_migration}

[Las API de gestión de usuarios ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/security.html#!/Authorization_-_User_Management){: new_window} proporcionan la exportación e importación masivas de usuarios de {{site.data.keyword.iot_short_notm}} y se pueden utilizar para exportar e importar los usuarios que desea conservar en la nueva organización.

1. Exporte los usuarios de la organización Lite.  
Utilice el mandato `GET /authorization/users` para exportar todos los usuarios de la organización de la cuenta Lite como un objeto JSON.
2. Limpie la lista de usuarios.  
Si es necesario, edite la estructura JSON para eliminar los usuarios que no desee migrar a la nueva organización.
3. Importe los usuarios a la nueva organización.  
Utilice el mandato `POST /authorization/users/multiple` para importar a la lista de usuarios JSON editada a la nueva organización.

Ahora los usuarios tienen acceso a la nueva organización, que se mostrará en el selector de organización en el panel de control de {{site.data.keyword.iot_short_notm}}.

##  Migración de dispositivos  
{: #device_migration}

La migración de los dispositivos se puede llevar a cabo siguiendo estos pasos:  
1. Migre los tipos de dispositivo que desea conservar en la nueva organización.  
2. Migre los dispositivos en sí a la nueva organización.  
3. Actualice el nombre de host que utilizan los dispositivos para conectarse a {{site.data.keyword.Bluemix_short}} para empezar a trabajar con el nuevo ID de organización.
4. Migre la información de gestión de datos que haya creado en la plataforma Lite.   
Esto puede incluir interfaces lógicas y físicas de dispositivo, cosas y reglas.

<p>Los tipos de dispositivo y los dispositivos se pueden migrar de forma masiva con las API siguientes:
<table>
<tr>
<th> Documentación de API </th>
<th> API de exportación </th>
<th> API de importación </th>
</tr>
<tr>
<td> [API de tipos de dispositivo ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/org-admin.html) </td>
<td> `GET /device/types` </td>
<td> `POST /device/types` </td>
</tr>
<tr>
<td>  [API de dispositivos ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/org-admin.html#!/Device_Bulk_Configuration) </td>
<td> `GET /bulk/devices` </td>
<td>  `POST /bulk/devices/add`</td>
</tr>
</table>
</p>
{: tip}


**Importante:** {{site.data.keyword.iot_short_notm}} no almacena las señales de autenticación de dispositivo, solo la versión salada de ellas. Por lo tanto, la llamada de `GET /bulk/devices` no puede devolver las señales de autenticación de los dispositivos almacenados. Si tiene un registro de las señales de autenticación de dispositivo, puede añadirlas al objeto JSON antes de hacer la carga masiva. De lo contrario, debe generar nuevas señales de autenticación de dispositivo para cada dispositivo y copiarlas en los dispositivos.  

Si utiliza certificados del lado del dispositivo para autenticar dispositivos, en lugar de señales de autenticación, no es necesario que realice esta acción. Sin embargo, si utiliza certificados de lado del dispositivo, debe cargar los certificados que se han utilizado para firmarlos en la nueva organización.


## Actualización de dispositivos
{: #update_devices}

Cuando los dispositivos estén registrados en la nueva organización, debe actualizar la configuración o el código presentes en cada uno de los dispositivos existentes para utilizar el nombre de host de la nueva organización.

Para los clientes de mensajería MQTT y HTTP, utilice el nombre de host siguiente:  
`<orgId>.messaging.internetofthings.ibmcloud.com`

Apunte los clientes de API REST al siguiente nombre de host:  
`<orgId>.internetofthings.ibmcloud.com`

**Importante:** si ha generado nuevas señales de autenticación para los dispositivos, debe copiarlas en cada dispositivo.


## Migración de gestión de dispositivos
{: #device_management}

Las [API de gestión de datos ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/state-mgmt.html){: new_window} incluyen API para exportar e importar interfaces físicas y lógicas de dispositivo, definiciones de cosas y reglas.

**Importante:** {{site.data.keyword.iot_short_notm}} no da soporte actualmente al concepto de duplicados de activos para la ingestión de datos.

## Paneles y tarjetas
{: #boards_cards}

{{site.data.keyword.iot_short_notm}} no incluye API para importar y exportar definiciones y personalizaciones de paneles y tarjetas. Debe volver a crear manualmente estos elementos en la nueva organización.

## Habilitar las extensiones necesarias
{: #extensions}

Debe volver a crear las extensiones que haya habilitado en la plataforma Lite, como por ejemplo enlaces a {{site.data.keyword.messagehub}}, {{site.data.keyword.cloudant_short_notm}} y Jasper en la nueva organización.

## Migración de aplicaciones
{: #application_migration}

Si ha desarrollado aplicaciones que llaman a API que se ofrecen con el servicio Lite de {{site.data.keyword.iot_short_notm}} para, por ejemplo, enviar o recibir datos, o para administrar el servicio, debe actualizarlos para utilizar la nueva instancia de producción o de no producción de {{site.data.keyword.iot_short_notm}}. Esto también se aplica a cualquier flujo de Node-RED que pueda estar utilizando.
La migración implica:
- Actualización de las aplicaciones para que utilicen un nuevo ID de organización de seis caracteres.
- Actualización de las aplicaciones para que utilicen las credenciales de señal y clave de API que cree para su nueva instancia de servicio.

**Importante:** si ha estado utilizando un enlace de Cloud Foundry para pasar el ID de organización y las credenciales a la aplicación, debe utilizar un mecanismo distinto, ya que la nueva instancia de {{site.data.keyword.iot_short_notm}} no se suministra para ejecutarse en el espacio de Cloud Foundry.

### Generación de credenciales de conexión de API

El proceso de migración a seguir depende de la naturaleza de la aplicación. En general, para todos los casos, el primer paso es adquirir una clave de API y una señal de autenticación para que las utilice la aplicación.

1. Inicie la sesión en el panel de control de nivel superior del nuevo servicio de {{site.data.keyword.iot_short_notm}}.
2. Seleccione el separador **Uso**.
3. Pulse el enlace **Ver detalles** para obtener la información de servicio de {{site.data.keyword.iot_short_notm}}.  
Se visualiza la información siguiente:
   - El ID de organización de seis caracteres
   - La señal y la clave de API.  
   Debe generar nuevas claves de API para cada una de las aplicaciones, en lugar de utilizar la clave de API que se muestra aquí. Esto le permite establecer los permisos adecuados para cada aplicación.
   - URL de host.
4. Cree una combinación de clave de API y señal de autenticación para su aplicación.  
La necesitará cuando configure la aplicación para conectarla con su organización.   
   1.  Pulse `Iniciar`.  
   Esto le llevará a través del panel de control de servicio subyacente que ha utilizado para administrar el servicio Lite de {{site.data.keyword.iot_short_notm}}.
   2. Seleccione **Apps**.
   3. Pulse **Generar clave de API**
   4. Copie los valores de la clave de API y la señal de autenticación que se listan.
   5. Seleccione un rol adecuado para la aplicación.   
   6. Añada un comentario para que pueda identificar fácilmente esta combinación de clave de API y señal de autenticación.
   7. Pulse **Generar**.
   8. **Importante:** Realice una copia local de la señal de autenticación. No se puede volver a crear después de cerrar la ventana.


### Actualización de aplicaciones Node-RED
Necesitará configurar los nodos Node-RED para conectarse a la nueva instancia de {{site.data.keyword.iot_short_notm}}. Los nodos `ibmiot` ya no podrán utilizar la opción de autenticación `BluemixService`, por lo que es necesario seleccionar la opción `Clave de API` en su lugar.
1. Abra el nodo `ibmiot` para editarlo.
2. En las propiedades del nodo, seleccione **Clave de API**.
3. Para el campo Clave de API, pulse el icono de edición y, a continuación, especifique la clave de API y la señal de autenticación que ha guardado en el paso anterior.
4. Guarde los cambios y vuelva a desplegar el flujo de Node-RED.

### Actualización de una aplicación que no utiliza un enlace de Cloud Foundry
Identifique la ubicación en la que la aplicación almacena el ID de org, la clave de API y la señal de autorización, y sustitúyalos por los valores que ha guardado anteriormente.

Si la aplicación utiliza uno de los SDK de {{site.data.keyword.iot_short_notm}}, es probable que estos valores se retengan en un archivo de propiedades.
{: tip}

### Actualización de una aplicación que utiliza un enlace de Cloud Foundry

{{site.data.keyword.Bluemix_short}} proporciona un mecanismo para enlazar las aplicaciones de Cloud Foundry con uno o varios servicios de Cloud Foundry. Los enlaces se pueden establecer utilizando la CLI de {{site.data.keyword.Bluemix_short}} o creando una `Conexión` entre la aplicación y el servicio en el panel de control de {{site.data.keyword.Bluemix_short}}.

Cuando una aplicación está enlazada con un servicio, las credenciales de clave de API y señal de autenticación del servicio se copian en la variable de entorno `VCAP_SERVICES`, desde donde puede recuperarlas la aplicación.

**Importante:** este mecanismo de enlace no se puede utilizar con el nuevo servicio de {{site.data.keyword.iot_short_notm}}. Debe encontrar el código en la aplicación que está leyendo en `VCAP_SERVICES` y sustituirlo por código que lea los valores en una ubicación en la que ahora almacena la señal de autorización y la clave de API. Para completar la actualización, debe volver a crear y a desplegar la aplicación.
