---

copyright:

years: 2017, 2019
lastupdated: "2019-04-16"

keywords: own organization, Extension HTTP APIs, API Use, AT&T Extension, Administer AT&T

subcollection: iot-platform

---

{:new_window: target="\_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:tip: .tip}
{:pre: .pre}
{:important: .important}


# API
{: #api_overview}

<p>Esta recopilación de documentación de {{site.data.keyword.cloud}} pertenece al plan de precios Lite de {{site.data.keyword.iot_full}} e incluye información básica de iniciación, referencias de API e información general de resolución de problemas. 
Para obtener la documentación completa de {{site.data.keyword.iot_short_notm}}, consulte la [documentación de producto de {{site.data.keyword.iot_short_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html) en IBM Knowledge Center. Encontrará más información acerca de los distintos planes en [Planes del servicio {{site.data.keyword.iot_short_notm}}](/docs/services/IoT?topic=iot-platform-plans_overview#plans_overview). 
</p>
{: important}

Dispone de varias API para el desarrollo de código para dispositivos, pasarelas y aplicaciones que se conectan a {{site.data.keyword.iot_full}}.

Las API HTTP están protegidas con autenticación básica HTTP. Al generar una clave de API mediante el panel de control, se le presentará una clave y una señal de autenticación. Para obtener más información sobre señales y claves de API, consulte [Conexión de clave de API ![Icono de enlace externo](../../../icons/launch-glyph.svg)](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/platform_authorization.html#api-key){: new_window}.


## Acerca de las API HTTP
{: #api_about}

Cada organización de {{site.data.keyword.iot_short_notm}} se identifica mediante un ID de organización de 6 caracteres necesario en el nombre de host para cualquier llamada de API HTTP.   

### Documentos de API
{: #api_docs}

Para ver los documentos de API, vaya a la página [API REST de IBM Watson IoT Platform ![Icono de enlace externo](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/index.html){: new_window}. Desde esta página, puede acceder a la documentación de las API de {{site.data.keyword.iot_short_notm}}.

### Documentos de API interactivos

Para ver y utilizar los documentos de API interactivos, se puede acceder al URL base de la organización en la dirección siguiente:

`https://<orgId>.internetofthings.ibmcloud.com/docs/index.html`

Desde esta página, puede acceder a la documentación de las API de {{site.data.keyword.iot_short_notm}}. Para tener acceso a la ejecución de las llamadas de API directamente desde la documentación, debe estar autorizado.

Para que se le autorice automáticamente, siga estos pasos:

1. Inicie sesión en el panel de control de {{site.data.keyword.iot_short_notm}}.
2. En el mismo navegador, abra un separador nuevo y vaya a la página de destino de los documentos de API interactivos.

Si no ha iniciado sesión en el panel de control de {{site.data.keyword.iot_short_notm}}, complete los pasos siguientes:

1. Vaya a la página de destino de los documentos de API interactivos.
2. Seleccione `Autorizar`.
3. En el recuadro `Autorizaciones disponibles`, establezca el nombre de usuario en la clave de API y la contraseña en la señal de autenticación. Seleccione `Autorizar`.
4. Cierre el recuadro `Autorizaciones disponibles`. **Importante:** No seleccione `Cerrar sesión`.

Una vez que esté autorizado, vaya a las llamadas de API específicas y utilice el botón `Pruébelo` para ejecutar las llamadas de API directamente desde la documentación.

<!-- To authenticate requests to the application API, set the username to the API key and the password to the authentication token. -->
