---

copyright:

years: 2017, 2019
lastupdated: "2019-02-13"

---

{:new_window: target="\_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:important: .important}


# API
{: #api_overview}

<p>Esta recopilación de documentación de {{site.data.keyword.Bluemix}} pertenece al plan de precios Lite de {{site.data.keyword.iot_full}} e incluye información básica de iniciación, referencias de API e información general de resolución de problemas. 
Para obtener la documentación completa de {{site.data.keyword.iot_short_notm}}, consulte la [documentación de producto de {{site.data.keyword.iot_short_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html) en IBM Knowledge Center. Encontrará más información acerca de los distintos planes en [planes de servicios de {{site.data.keyword.iot_short_notm}}](/docs/IoT/plans_overview.html#plans_overview). 
</p>
{: important}

Dispone de varias API para el desarrollo de código para dispositivos, pasarelas y aplicaciones que se conectan a {{site.data.keyword.iot_full}}.

Las API HTTP están protegidas con autenticación básica HTTP. Al generar una clave de API mediante el panel de control, se le presentará una clave y una señal de autenticación. Para obtener más información sobre claves de API y señales, consulte [Conexión de la clave de API ![Icono de enlace externo](../../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/platform_authorization.html#api-key).


## Acerca de las API HTTP
{: #api_about}

Después de registrar su propia organización, se le proporcionará un ID de organización de 6 caracteres, que es necesario en el nombre de host para cualquier llamada de API HTTP. Puede acceder al URL base de su organización en la siguiente dirección:

https://<**orgId**>.internetofthings.ibmcloud.com/api/v0002

Para autenticar solicitudes a la API de aplicación, establezca el nombre de usuario en la clave de API y la contraseña en la señal de autenticación.

Para las API de mensajería, utilice la siguiente dirección:

https://<**orgId**>.messaging.internetofthings.ibmcloud.com/api/v0002

## API HTTP
{: #api_http}

API                     | Utilícela para...       
------------- | -------------
[Administración de la organización ![Icono de enlace externo](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/orgAdmin.html){: new_window} | Configurar una organización (incluyendo crear y suprimir dispositivos), comprobar el uso, ver el estado del servicio y diagnosticar problemas de conexión del dispositivo.
[Seguridad ![Icono de enlace externo](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/security.html){: new_window} | Gestionar la autenticación y la autorización de usuarios, claves de API y dispositivos.
[Gestión de la información ![Icono de enlace externo](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/info-mgmt.html){: new_window} |  Acceder a los datos de sucesos del dispositivo y obtener y actualizar la ubicación del dispositivo y la información meteorológica para dicha ubicación.
[Gestión de datos ![Icono de enlace externo](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/state-mgmt.html){: new_window}   |   Organizar e integrar datos entrantes y salientes de {{site.data.keyword.iot_short_notm}}.
[Gestión de dispositivos ![Icono de enlace externo](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/deviceMgmt.html){: new_window} | Interactuar con dispositivos gestionados utilizando el protocolo de gestión de dispositivos.
[Mensajería ![Icono de enlace externo](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/http-messaging.html){: new_window}   | Publicar sucesos y enviar mandatos utilizando HTTP.
[Gestión de riesgos ![Icono de enlace externo](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/riskmgmt.html){: new_window}   | Gestión de los informes y las políticas de gestión de riesgos.

## API HTTP de extensión
{: #api_extension}

API                     | Utilícela para...       
------------- | -------------
[Extensión de AT&T ![Icono de enlace externo](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/ext-atnt.html){: new_window} | Administrar dispositivos AT&T.
[Extensión de Jasper ![Icono de enlace externo](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/ext-jasper.html){: new_window} | Administrar dispositivos Jasper.
[Extensión de Orange ![Icono de enlace externo](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/ext-orange.html){: new_window} | Visualizar los datos de la tarjeta SIM desde dispositivos que están conectados a su organización de {{site.data.keyword.iot_short_notm}} y tienen una tarjeta SIM de Orange instalada.

## API HTTP beta
{: #api_beta}

API                     | Utilícela para...       
------------- | -------------
[Restaurar dispositivos suprimidos ![Icono de enlace externo](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002-beta/restore-device-beta.html){: new_window}   | Si se suprime un dispositivo por equivocación, puede restaurarlo dentro de un plazo de 14 días.
