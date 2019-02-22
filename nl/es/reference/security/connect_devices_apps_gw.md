---

copyright:
  years: 2015, 2019
lastupdated: "2019-02-13"

---

{:new_window: target="\_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}
{:pre: .pre}
{:important: .important}

# Información de conexión para aplicaciones, dispositivos y pasarelas
{: #connect_devices_apps_gw}

<p>Esta recopilación de documentación de {{site.data.keyword.Bluemix}} pertenece al plan de precios Lite de {{site.data.keyword.iot_full}} e incluye información básica de iniciación, referencias de API e información general de resolución de problemas. 
Para obtener la documentación completa de {{site.data.keyword.iot_short_notm}}, consulte la [documentación de producto de {{site.data.keyword.iot_short_notm}} ![Icono de enlace externo](../../../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html) en IBM Knowledge Center. Encontrará más información acerca de los distintos planes en [planes de servicios de {{site.data.keyword.iot_short_notm}}](/docs/IoT/plans_overview.html#plans_overview). 
</p>
{: important}

Puede conectar aplicaciones, dispositivos y pasarelas a {{site.data.keyword.iot_full}} mediante el protocolo de MQTT. También puede utilizar la API REST HTTP para conectar dispositivos a {{site.data.keyword.iot_short_notm}}.
{: shortdesc}


## URL de conexiones de clientes
{: #client_connect_url}

Para conectar clientes de dispositivos, aplicaciones y pasarelas a la instancia de {{site.data.keyword.iot_short_notm}}, utilice los siguientes URL de conexión:

### Dirección de mensajería

<pre class="pre"><var class="keyword varname">orgId</var>.messaging.internetofthings.ibmcloud.com</pre>
{: codeblock}

### URL de conexión de la API REST de HTTP

<pre class="pre"><code class="hljs">https://<var class="keyword varname">orgId</var>.internetofthings.ibmcloud.com/api/v0002/device/types/<var class="keyword varname">typeId</var>/devices/<var class="keyword varname">deviceId</var>/events/<var class="keyword varname">eventId</var></code></pre>
{: codeblock}

**Notas**
- Donde *orgId* es el único ID de organización generado al registrar la instancia de servicio.
- Si está conectando un dispositivo o aplicación al servicio de Inicio rápido, especifique 'quickstart' como valor de *orgId*.

## Configuración del cortafuegos
{: #firewall_configuration}

Para conectar dispositivos y aplicaciones a {{site.data.keyword.iot_short_notm}}, debe asegurarse de que los cortafuegos estén configurados para permitir el tráfico en puertos específicos. Los cortafuegos pueden estar ubicados en la máquina local, en el direccionador o en la red corporativa.

### Seguridad de puerto
{: #client_port_security}

Los dispositivos, las pasarelas y las aplicaciones se conectan a {{site.data.keyword.iot_short_notm}} utilizando el protocolo MQTT o HTTP. Las conexiones pueden ser seguras o no seguras.

|Tipo de conexión |Protocolo|Número de puerto|
|:---|:---|:---|
|No segura*|MQTT y HTTP|1883 u 80|
|Secura (TLS)|MQTT y HTTPS|8883 o 443|

&ast;De forma predeterminada, los puertos 1883 y 80 están inhabilitados para la mensajería. Para obtener información sobre cómo cambiar el valor predeterminado, consulte [Configuración de políticas de seguridad ![Icono de enlace externo](../../../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/reference/security/set_up_policies.html#set_up_policies.html){: new_window}.

MQTT recibe soporte sobre TCP y WebSockets. Los clientes de MQTT se conectan utilizando las credenciales adecuadas, como por ejemplo las señales de autenticación de dispositivo para dispositivos y claves y señales de API para aplicaciones. Dado que la mensajería de MQTT al puerto no seguro 1883 envía estas credenciales en texto sin formato, utilice siempre las alternativas seguras 8883 o 443 en su lugar. Las credenciales TLS siempre están cifradas cuando se envían a través de puertos seguros. Tenga en cuenta que debe habilitar TLS en la aplicación (ej.: mediante el método `tls_set()` en la biblioteca de MQTT de Python). De lo contrario, los datos se pueden enviar de forma no segura.

Cuando se utiliza la mensajería de MQTT segura en los puertos 8883 o 443, las bibliotecas de clientes más recientes confían automáticamente en el certificado predeterminado presentado por {{site.data.keyword.iot_short_notm}}. Si este no es el caso para el entorno del cliente, puede descargar y utilizar la cadena de certificados completa desde [messaging.pem ![Icono de enlace externo](../../../../icons/launch-glyph.svg "Icono de enlace externo")](https://github.com/ibm-watson-iot/iot-python/blob/master/src/wiotp/sdk/messaging.pem){: new_window}. Si ha subido un certificado personalizado, es posible que tenga que comprobar que se añade la cadena de confianza adecuada a su entorno de cliente.

## Configuración del cortafuegos
{: #firewall_configuration .sectiontitle}

Para conectar dispositivos y aplicaciones a {{site.data.keyword.iot_short_notm}}, debe asegurarse de que los cortafuegos estén configurados para permitir el tráfico en puertos específicos. Los cortafuegos pueden estar ubicados en la máquina local, en el direccionador o en la red corporativa.

Asegúrese de que las direcciones IP requeridas estén abiertas y habilitadas para la comunicación.

|Región | Dirección IP|Puertos de mensajería</br> (no seguros) | Puertos de mensajería (seguros)|
|:---|:---|:---| :---|
|us-south|169.45.2.16/28* </br>169.46.7.56/29</br>169.48.234.208/29</br>169.62.202.128/29|1883,80 | 8883,443|
|eu-gb|159.8.169.208/28* </br>158.175.111.152/29</br>158.176.104.24/29</br>141.125.70.152/29|1883,80 | 8883,443|
|eu-de|159.122.121.80/28* </br>149.81.125.176/29</br>158.177.82.208/29</br>161.156.96.80/29|1883,80 | 8883,443|
|Inicio rápido|169.45.2.16/28* </br>169.46.7.56/29</br>169.48.234.208/29</br>169.62.202.128/29|1883,80 | no disponible|
|{{site.data.keyword.iot_short_notm}} dedicado|Póngase en contacto con el representante de {{site.data.keyword.IBM}}.|-| - |
&ast;Se dejará de utilizar pasado el primer trimestre de 2019.

## Requisitos de TLS
{: #tls_requirements}

Algunas bibliotecas de cliente de Transport Layer Security (TLS) no dan soporte a dominios que incluyan un comodín. Si no puede cambiar satisfactoriamente las bibliotecas, inhabilite la comprobación de certificados.

Los requisitos de TLS dependen de si está conectando a {{site.data.keyword.iot_short_notm}} con el protocolo MQTT o HTTP. En las secciones siguientes se muestran las suites de cifrado que reciben soporte si se utiliza el certificado de servidor predeterminado. Si utiliza su propio certificado de cliente, las suites de cifrado que reciben soporte dependen del certificado utilizado.

### Requisitos de TLS para conexiones MQTT

{{site.data.keyword.iot_short_notm}} requiere TLS v1.2. Asegúrese de que se permita al menos una de las suites de cifrado siguientes:

- TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256
- TLS_DHE_RSA_WITH_AES_128_GCM_SHA256
- TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA
- TLS_DHE_RSA_WITH_AES_128_CBC_SHA
- TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384
- TLS_DHE_RSA_WITH_AES_256_GCM_SHA384
- TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA
- TLS_DHE_RSA_WITH_AES_256_CBC_SHA
- TLS_RSA_WITH_AES_128_GCM_SHA256
- TLS_RSA_WITH_AES_256_GCM_SHA384

### Requisitos de TLS para conexiones HTTP

Si está utilizando el certificado de servidor predeterminado, {{site.data.keyword.iot_short_notm}} requiere TLS v1.2. Asegúrese de que se permita al menos una de las suites de cifrado siguientes:


- TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA
- TLS_DHE_RSA_WITH_AES_128_CBC_SHA
- TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA
- TLS_DHE_RSA_WITH_AES_256_CBC_SHA
- TLS_RSA_WITH_AES_256_CBC_SHA
- TLS_RSA_WITH_AES_128_CBC_SHA

Aumente la fuerza de su cifrado usando los cifrados de secreto de reenvío ECDHE o DHE en su lista de cifrado.

## Autenticación de cliente de MQTT
{: #mqtt_authentication}

**Importante:** Cada cliente de MQTT requiere un ID de cliente exclusivo. Si intenta conectar un cliente a la organización utilizando un ID de cliente que ya esté conectado, se desconectará la primera conexión.

Los dispositivos y pasarelas que están conectados directamente al {{site.data.keyword.iot_short_notm}} muestran un icono de estado en el panel de control para indicar que están conectados. Los dispositivos que están conectados de forma indirecta a través de una pasarela se muestran como desconectados porque el panel de control no sabe qué dispositivos están conectados a través de una pasarela.

### Identificadores de cliente de MQTT

Para que se autentiquen correctamente los dispositivos, aplicaciones y pasarelas, defina cada cliente de MQTT utilizando los siguientes identificadores de clientes y formato:

|Tipo de cliente |ID|Formato de ID de MQTT|
|:---|:---|:---|
|Aplicaciones|a|<pre class="pre">a:<var class="keyword varname">orgId</var>:<var class="keyword varname">appId</var></pre>
|Aplicaciones escalables|A|<pre class="pre">A:<var class="keyword varname">orgId</var>:<var class="keyword varname">appId</var></pre>
|Dispositivos|d|<pre class="pre">d:<var class="keyword varname">orgId</var>:<var class="keyword varname">deviceType</var>:<var class="keyword varname">deviceId</var></pre>|
|Pasarelas|g|<pre class="pre">g:<var class="keyword varname">orgId</var>:<var class="keyword varname">typeId</var>:<var class="keyword varname">deviceId</var></pre>|

Donde
- *orgId* es el ID de organización de seis caracteres exclusivo que se ha generado cuando se ha registrado el servicio.
- *appId* es un identificador de serie exclusivo definido por el usuario para el cliente.
- *deviceId* identifica de forma exclusiva un dispositivo o pasarela en todos los tipos y es similar a un número de serie.
- *device_type* es el identificador para el tipo de dispositivo que se está conectando y es similar a un número de modelo.
- *typeId* es un identificador del tipo de pasarela que se está conectando y es similar a un número de modelo.

Los valores *appId*, *type_id*, *device_type* y *device_id* no deben tener más de 36 caracteres y sólo pueden contener:
- Caracteres alfanuméricos (a-z, A-Z, 0-9)
- Guiones ( - )
- Guiones bajos ( _ )
- Puntos ( . )

**Notas:**
- Cuando se conecta al servicio de Inicio rápido, no se necesita autenticación.
- No es necesario registrar una aplicación antes de establecer la conexión.

Para obtener información sobre el formato de las suscripciones compartidas, consulte [Conectividad de MQTT para aplicaciones ![Icono de enlace externo](../../../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/applications/mqtt.html){: new_window}.


### Conexión de aplicaciones utilizando MQTT

Las aplicaciones de {{site.data.keyword.iot_short_notm}} requieren una clave de API para conectarse a una organización. Cuando se registra una clave de API, se genera una señal, que se debe utilizar con dicha clave de API.

El código siguiente proporciona un ejemplo de una clave de API:

<pre class="pre">a-<var class="keyword varname">orgId</var>-a84ps90Ajs</pre>
{: codeblock}

El ejemplo siguiente muestra una señal de autenticación típica:

```
 MP$08VKz!8rXwnR-Q*
```

Cuando se realiza una conexión de MQTT utilizando una clave de API, asegúrese de que cumple los siguientes requisitos:

- El ID de cliente de MQTT está en el siguiente formato: a:*orgId*:*appId*
- El nombre de usuario de MQTT es la clave de la API, por ejemplo, a-*orgId*-a84ps90Ajs
- La contraseña de MQTT es la señal de autenticación, por ejemplo, *MP$08VKz!8rXwnR-Q**

Para obtener más información, consulte [Conectividad de MQTT para las aplicaciones ![Icono de enlace externo](../../../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/applications/mqtt.html){: new_window}.

### Autenticación de dispositivo

#### Nombres de usuario
El servicio de {{site.data.keyword.iot_short_notm}} sólo da soporte a la autenticación basada en señales para dispositivos; por lo tanto, cada dispositivo sólo tiene un nombre de usuario válido.
Un valor de `use-token-auth` indica al servicio que la señal de autenticación para la pasarela o el dispositivo se utiliza como la contraseña para la conexión de MQTT.

Para obtener más información, consulte [Conectividad de MQTT para los dispositivos ![Icono de enlace externo](../../../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/devices/mqtt.html){: new_window}.

#### Contraseñas
Si el cliente está utilizando la autenticación basada en señales, envíe la señal de autenticación de dispositivo como la contraseña para todas las conexiones de MQTT.
