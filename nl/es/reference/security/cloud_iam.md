---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-13"

---

{:new_window: target="\_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:important: .important}


# Autenticación y autorización de {{site.data.keyword.iamshort}} para {{site.data.keyword.iot_short_notm}} (Beta)
{: #cloud_iam}

<p>Esta recopilación de documentación de {{site.data.keyword.Bluemix}} pertenece al plan de precios Lite de {{site.data.keyword.iot_full}} e incluye información básica de iniciación, referencias de API e información general de resolución de problemas. 
Para obtener la documentación completa de {{site.data.keyword.iot_short_notm}}, consulte la [documentación de producto de {{site.data.keyword.iot_short_notm}} ![Icono de enlace externo](../../../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html) en {{site.data.keyword.IBM_notm}} Knowledge Center. Encontrará más información acerca de los distintos planes en [planes de servicios de {{site.data.keyword.iot_short_notm}}](/docs/IoT/plans_overview.html#plans_overview). 
</p>
{: important}

Las API de {{site.data.keyword.iot_full}} soportan la autenticación y la autorización de los usuarios mediante {{site.data.keyword.iamshort}} (IAM).

La autenticación y la autorización de {{site.data.keyword.iamlong}} para {{site.data.keyword.iot_short_notm}} solo están disponibles como parte de un programa beta limitado. Las actualizaciones futuras pueden incluir cambios que no son compatibles con la versión actual de esta característica. Pruébela y [denos su opinión ![Icono de enlace externo](../../../../icons/launch-glyph.svg)](https://developer.ibm.com/answers/smart-spaces/17/internet-of-things.html){: new_window}.
{: important}

{{site.data.keyword.iamshort}} se crea en {{site.data.keyword.Bluemix_notm}} y se utiliza para autenticar y autorizar a los usuarios administrativos y de desarrollador que necesitan configurar y gestionar sus servicios de {{site.data.keyword.IBM_notm}}. Los usuarios que necesitan acceso al panel de control de {{site.data.keyword.iot_short_notm}} se autentican utilizando {{site.data.keyword.iamshort}}. El origen de identidad para {{site.data.keyword.iamshort}} pueden ser usuarios de IBMid registrados o puede ser el servicio de directorio de un cliente que da soporte a SAML.  

{{site.data.keyword.iot_short_notm}} también da soporte a la autenticación de usuarios a través de {{site.data.keyword.appid_short_notm}}. {{site.data.keyword.appid_short_notm}} se utiliza para autenticar a los usuarios que necesitan acceso a las aplicaciones alojadas en {{site.data.keyword.Bluemix_notm}}. Los usuarios de {{site.data.keyword.appid_short_notm}} normalmente no realizan actividades administrativas o de desarrollo en un servicio de nube. Para obtener más información, consulte [Autenticación de {{site.data.keyword.appid_short_notm}} para la plataforma IoT de Watson ![Icono de enlace externo](../../../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/app_id.html#app_id){: new_window}.

IAM permite a los usuarios obtener una señal de OAuth de IAM y utilizarla para autenticar las llamadas de API. Por ejemplo, un usuario con la CLI de {{site.data.keyword.containershort_notm}} instalada puede utilizar el mandato siguiente:

`bx iam oauth-tokens`

El mandato devuelve la señal IAM del usuario que ha iniciado la sesión en el formato siguiente:

`IAM Token: Bearer <some token>`

Un usuario también puede utilizar el punto final de señal IAM para iniciar la sesión y recuperar su señal IAM, tal como se muestra en el ejemplo siguiente:
`curl -s 'https://iam.bluemix.net/oidc/token?grant_type=urn:ibm:params:oauth:grant-type:apikey&response_type=cloud_iam&apikey=<apikey>' -H'Content-Type:x-www-form-urlencoded' -XPOST`

Este ejemplo de API utiliza una clave de API IAM para solicitar la señal IAM y devuelve el `Bearer <token>`.

A continuación, cuando un usuario llama a una API de {{site.data.keyword.iot_short_notm}}, puede proporcionar la cabecera de autorización `Authorization: Bearer <token>` en sus llamadas de API.

## Generación de una señal de IAM
{: #iam_generate}

Puede elegir cómo automatizar la creación de la señal IAM, en función de cómo se autentique con {{site.data.keyword.Bluemix_notm}} y el tipo de ID de {{site.data.keyword.Bluemix_notm}} que utilice.

Si utiliza un ID no federado, puede elegir una de las opciones siguientes para crear una señal IAM:
 - **Nombre de usuario y contraseña de {{site.data.keyword.Bluemix_notm}}:** Puede crear una señal para automatizar completamente la creación de la señal de acceso de IAM.
 - **Generar una clave de API de {{site.data.keyword.Bluemix_notm}}:** Utilice claves de API de {{site.data.keyword.Bluemix_notm}}, que dependen de la cuenta de {{site.data.keyword.Bluemix_notm}} para la que se generan. No puede combinar su clave de API de {{site.data.keyword.Bluemix_notm}} con otro ID de cuenta en la misma señal de IAM. Para acceder a los clústeres que se han creado con una cuenta distinta de aquella en la que se basa la clave de API de {{site.data.keyword.Bluemix_notm}}, debe iniciar una sesión en la cuenta para generar una nueva clave de API.

Si utiliza un ID federado, puede elegir una de las opciones siguientes para crear una señal IAM:
 - **Generar una clave de API de {{site.data.keyword.Bluemix_notm}}:** Las claves de API de {{site.data.keyword.Bluemix_notm}} dependen de la cuenta de {{site.data.keyword.Bluemix_notm}} para la que se generan. No puede combinar su clave de API de {{site.data.keyword.Bluemix_notm}} con otro ID de cuenta en la misma señal de IAM. Para acceder a los clústeres que se han creado con una cuenta distinta de aquella en la que se basa la clave de API de {{site.data.keyword.Bluemix_notm}}, debe iniciar una sesión en la cuenta para generar una nueva clave de API.
 - **Utilizar un código de acceso puntual:** Si se autentica con {{site.data.keyword.Bluemix_notm}} utilizando un código de acceso puntual, no puede automatizar completamente la creación de la señal IAM porque la recuperación de un código de acceso puntual requiere una interacción manual con el navegador web. Para automatizar por completo la creación de la señal de IAM, debe crear en su lugar una clave de API de {{site.data.keyword.Bluemix_notm}}.

Cuando se crea la señal de acceso, la información del cuerpo que se incluye en la solicitud varía en función del método de autenticación de {{site.data.keyword.Bluemix_notm}} que utiliza. Sustituya los valores siguientes:
- `<my_username>` = Su nombre de usuario de {{site.data.keyword.Bluemix_notm}}.
- `<my_password>` = Su contraseña de {{site.data.keyword.Bluemix_notm}}.
- `<my_api_key>` = Su clave de API de {{site.data.keyword.Bluemix_notm}}.
- `<my_passcode>` = Su código de acceso único de {{site.data.keyword.Bluemix_notm}}. Ejecute `bx login --sso` y siga las instrucciones de la salida de la CLI para recuperar el código de acceso puntual mediante su navegador web.

Ejemplo:
`POST https://iam.<region>.bluemix.net/oidc/token`

Para especificar una región de {{site.data.keyword.Bluemix_notm}}, revise las abreviaturas de la región que se utilizan en los puntos finales de la API. Consulte [Puntos finales de API de la región de {{site.data.keyword.Bluemix_notm}} ![Icono de enlace externo](../../../../icons/launch-glyph.svg)](https://console.bluemix.net/docs/containers/cs_regions.html#bluemix_regions){: new_window} para obtener más información.

Parámetro de entrada	 | Valores
---------------- | -----------
Cabecera	| Content-Type:application/x-www-form-urlencoded<br>Authorization: Basic Xng7Png=<br>Nota: Se le proporciona `Xng7Png=`, la autorización codificada con URL para el nombre de usuario bx y la contraseña bx.
Cuerpo correspondiente al nombre de usuario y contraseña de {{site.data.keyword.Bluemix_notm}}	|	grant_type: password<br>response_type: cloud_iam, uaa<br>nombre de usuario: `<my_username>`<br>contraseña: `<my_password>`<br>uaa_client_id: cf<br>uaa_client_secret:<br>Nota: Añada la clave uaa_client_secret sin ningún valor especificado.
Cuerpo correspondiente a las claves de API de {{site.data.keyword.Bluemix_notm}}	|	grant_type: urn:ibm:params:oauth:grant-type:apikey<br>response_type: cloud_iam<br>uaa<br>apikey: `<my_api_key>`<br>uaa_client_id: cf<br>uaa_client_secret:<br>Nota: Añada la clave uaa_client_secret sin ningún valor especificado.
Cuerpo correspondiente al código de acceso puntual de {{site.data.keyword.Bluemix_notm}}	|	grant_type: urn:ibm:params:oauth:grant-type:passcode<br>response_type: cloud_iam, uaa<br>passcode: `<my_passcode>`<br>uaa_client_id: cf<br>uaa_client_secret:<br>Nota: Añada la clave uaa_client_secret sin ningún valor especificado.

Ejemplo de salida de API:

```
{
"access_token": "<iam_token>",
"refresh_token": "<iam_refresh_token>",
"uaa_token": "<uaa_token>",
"uaa_refresh_token": "<uaa_refresh_token>",
"token_type": "Bearer",
"expires_in": 3600,
"expiration": 1493747503
}
```
Encontrará la señal de IAM en el campo **access_token** de la salida de API.

En el ejemplo siguiente se muestra cómo utilizar la señal IAM al llamar a las API.

```
GET https://org.domain/api/v0002/bulk/devices
```

Parámetro de entrada   |	Valores
----------------- | -----------
Cabeceras	|	Content-Type: application/json<br>Authorization: bearer `<iam_token>`
