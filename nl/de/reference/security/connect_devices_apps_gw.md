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

# Verbindungsinformationen für Anwendungen, Geräte und Gateways
{: #connect_devices_apps_gw}

<p>Diese {{site.data.keyword.Bluemix}}-Dokumentationssammlung bezieht sich auf den Lite-Preisstrukturplan von {{site.data.keyword.iot_full}} und enthält grundlegende Informationen zum Einstieg, API-Referenzinformationen und allgemeine Informationen zur Fehlerbehebung.
Die vollständige Dokumentation zum {{site.data.keyword.iot_short_notm}}-Feature finden Sie in der [{{site.data.keyword.iot_short_notm}}-Produktdokumentation![Symbol für externen Link](../../../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html) im IBM Knowledge Center. Weitere Informationen zu den verschiedenen Plänen finden Sie in [{{site.data.keyword.iot_short_notm}}-Servicepläne](/docs/IoT/plans_overview.html#plans_overview).
</p>
{: important}

Anwendungen, Geräte und Gateways können über das MQTT-Protokoll eine Verbindung zu {{site.data.keyword.iot_full}} herstellen. Sie können auch die HTTP-REST-API verwenden, um Geräte mit {{site.data.keyword.iot_short_notm}} zu verbinden.
{: shortdesc}


## URLs für Clientverbindungen
{: #client_connect_url}

Zum Herstellen von Verbindungen zwischen Geräte-, Anwendungs- und Gateway-Clients und Ihrer {{site.data.keyword.iot_short_notm}}-Instanz verwenden Sie folgende Verbindungs-URLs:

### Nachrichtenadresse

<pre class="pre"><var class="keyword varname">Organisations-ID</var>.messaging.internetofthings.ibmcloud.com</pre>
{: codeblock}

### Verbindungs-URL für HTTP-REST-API

<pre class="pre"><code class="hljs">https://<var class="keyword varname">orgId</var>.internetofthings.ibmcloud.com/api/v0002/device/types/<var class="keyword varname">typeId</var>/devices/<var class="keyword varname">deviceId</var>/events/<var class="keyword varname">eventId</var></code></pre>
{: codeblock}

**Hinweise**
- Dabei ist *orgId* die eindeutige Organisations-ID, die beim Registrieren der Serviceinstanz generiert wurde.
- Wenn Sie für ein Gerät oder eine Anwendung eine Verbindung zum Quickstart-Service herstellen, geben Sie 'quickstart' als Wert für *Organisations-ID* an.

## Firewallkonfiguration
{: #firewall_configuration}

Damit Geräte und Anwendungen mit {{site.data.keyword.iot_short_notm}} verbunden werden können, müssen Sie sicherstellen, dass alle Firewalls so konfiguriert sind, dass der Datenverkehr an bestimmten Ports zugelassen wird. Eine Firewall kann sich auf der lokalen Maschine oder auf dem Router befinden oder Teil des Unternehmensnetzes sein. 

### Portsicherheit
{: #client_port_security}

Geräte, Gateways und Anwendungen stellen eine Verbindung zu {{site.data.keyword.iot_short_notm}} entweder über das MQTT- oder über das HTTP-Protokoll her. Verbindungen können nicht sicher oder sicher sein. 

|Verbindungstyp |Protokoll|Portnummer|
|:---|:---|:---|
|Nicht sicher*|MQTT und HTTP|1883 oder 80|
|Sicher (TLS)|MQTT und HTTPS|8883 oder 443|

&ast; Die Ports 1883 und 80 sind standardmäßig für die Nachrichtenübertragung inaktiviert. Informationen zum Ändern der Standardeinstellung finden Sie in [Sicherheitsrichtlinien konfigurieren ![Symbol für externen Link](../../../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/reference/security/set_up_policies.html#set_up_policies.html){: new_window}. 

MQTT wird über TCP und WebSockets unterstützt. MQTT-Clients stellen eine Verbindung unter Verwendung von entsprechenden Berechtigungsnachweisen her, wie beispielsweise Authentifizierungstokens für Geräte bzw. API-Schlüssel und Tokens für Anwendungen. Da diese Berechtigungsnachweise mithilfe der MQTT-Nachrichtenübermittlung in einfachem Text an den nicht sicheren Port 1883 gesendet werden, sollten Sie stattdessen stets die sicheren Alternativen 8883 oder 443 verwenden. Die TLS-Berechtigungsnachweise werden stets verschlüsselt, wenn sie über sichere Ports gesendet werden. Beachten Sie, dass Sie TLS in der Anwendung aktivieren müssen (z. B. mit der Methode `tls_set()` in der Python-MQTT-Bibliothek). Andernfalls werden die Daten möglicherweise auf unsichere Weise gesendet.

Wenn Sie die sichere MQTT-Nachrichtenübertragung an den Ports 8883 oder 443 verwenden, vertrauen neuere Clientbibliotheken automatisch dem Standardzertifikat, das von {{site.data.keyword.iot_short_notm}} angegeben wird. Ist dies für Ihre Clientumgebung nicht der Fall, können Sie die vollständige Zertifikatskette von [messaging.pem ![Symbol für externen Link](../../../../icons/launch-glyph.svg "Symbol für externen Link")](https://github.com/ibm-watson-iot/iot-python/blob/master/src/wiotp/sdk/messaging.pem){: new_window} herunterladen. Wenn Sie ein angepasstes Zertifikat hochgeladen haben, müssen Sie möglicherweise sicherstellen, dass die entsprechende Vertrauenskette zu Ihrer Clientumgebung hinzugefügt wird. 

## Firewallkonfiguration
{: #firewall_configuration .sectiontitle}

Damit Geräte und Anwendungen mit {{site.data.keyword.iot_short_notm}} verbunden werden können, müssen Sie sicherstellen, dass alle Firewalls so konfiguriert sind, dass der Datenverkehr an bestimmten Ports zugelassen wird. Eine Firewall kann sich auf der lokalen Maschine oder auf dem Router befinden oder Teil des Unternehmensnetzes sein. 

Stellen Sie sicher, dass die erforderlichen IP-Adressen geöffnet und für die Kommunikation aktiviert sind. 

|Region | IP-Adresse|Nachrichtenübertragungsports</br> (nicht sicher) | Nachrichtenübertragungsports (sicher)|
|:---|:---|:---| :---|
|us-south|169.45.2.16/28* </br>169.46.7.56/29</br>169.48.234.208/29</br>169.62.202.128/29|1883,80 | 8883,443|
|eu-gb|159.8.169.208/28* </br>158.175.111.152/29</br>158.176.104.24/29</br>141.125.70.152/29|1883,80 | 8883,443|
|eu-de|159.122.121.80/28* </br>149.81.125.176/29</br>158.177.82.208/29</br>161.156.96.80/29|1883,80 | 8883,443|
|Quickstart|169.45.2.16/28* </br>169.46.7.56/29</br>169.48.234.208/29</br>169.62.202.128/29|1883,80 | nicht verfügbar|
|Dediziertes {{site.data.keyword.iot_short_notm}}|Kontaktieren Sie den {{site.data.keyword.IBM}} Ansprechpartner. |-| - |
&ast; Nach dem ersten Quartal 2019 nicht mehr verwendet. 

## TLS-Anforderungen
{: #tls_requirements}

Einige TLS-Clientbibliotheken (TLS - Transport Layer Security) unterstützen keine Domänen, die ein Platzhalterzeichen enthalten. Inaktivieren Sie die Zertifikatsüberprüfung, wenn das Ändern von Bibliotheken nicht erfolgreich ist.

Die jeweiligen TLS-Anforderungen sind davon abhängig, ob die Verbindung zu {{site.data.keyword.iot_short_notm}} über das MQTT- oder das HTTP-Protokoll hergestellt wird. In den folgenden Abschnitten wird angegeben, welche Cipher-Suites bei Verwendung des Standardserverzertifikats unterstützt werden. Wenn Sie ein eigenes Clientzertifikat verwenden, hängt es vom verwendeten Zertifikat ab, welche Cipher-Suites unterstützt werden.

### TLS-Anforderungen für MQTT-Verbindungen

{{site.data.keyword.iot_short_notm}}  erfordert TLS Version 1.2. Stellen Sie sicher, dass mindestens eine der folgenden Cipher-Suites zulässig ist:

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

### TLS-Anforderungen für HTTP-Verbindungen

Wenn Sie das Standardserverzertifikat verwenden, ist für {{site.data.keyword.iot_short_notm}} TLS Version 1.2 erforderlich. Stellen Sie sicher, dass mindestens eine der folgenden Cipher-Suites zulässig ist:


- TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA
- TLS_DHE_RSA_WITH_AES_128_CBC_SHA
- TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA
- TLS_DHE_RSA_WITH_AES_256_CBC_SHA
- TLS_RSA_WITH_AES_256_CBC_SHA
- TLS_RSA_WITH_AES_128_CBC_SHA

Erhöhen Sie die Stärke Ihrer Verschlüsselung, indem Sie die Verschlüsselungen ECDHE oder DHE in Ihrer Verschlüsselungsliste verwenden.

## MQTT-Clientauthentifizierung
{: #mqtt_authentication}

**Wichtig:** Für jeden MQTT-Client ist eine eindeutige Client-ID erforderlich. Wenn Sie versuchen, in Ihrer Organisation eine Verbindung für einen Client mithilfe einer Client-ID herzustellen, für die bereits eine Verbindung besteht, wird die zuerst hergestellte Verbindung getrennt.

Für Geräte und Gateways, die direkt mit {{site.data.keyword.iot_short_notm}} verbunden sind, wird im Dashboard ein Statussymbol angezeigt, mit dem angegeben wird, dass sie verbunden sind. Geräte, die indirekt über ein Gateway verbunden sind, werden als nicht verbunden angezeigt, da das Dashboard über ein Gateway verbundene Geräte nicht erkennt.

### MQTT-Client-ID

Definieren Sie jeden MQTT-Client mithilfe der folgenden Client-IDs und des folgenden Formats, um Geräte, Anwendungen und Gateways erfolgreich zu authentifizieren.

|Clienttyp |ID|MQTT-ID-Format|
|:---|:---|:---|
|Anwendungen|a|<pre class="pre">a:<var class="keyword varname">Organisations-ID</var>:<var class="keyword varname">Anwendungs-ID</var></pre>
|Skalierbare Anwendungen|A|<pre class="pre">A:<var class="keyword varname">Organisations-ID</var>:<var class="keyword varname">Anwendungs-ID</var></pre>
|Geräte|d|<pre class="pre">d:<var class="keyword varname">Organisations-ID</var>:<var class="keyword varname">Gerätetyp</var>:<var class="keyword varname">Geräte-ID</var></pre>|
|Gateways|g|<pre class="pre">g:<var class="keyword varname">Organisations-ID</var>:<var class="keyword varname">Typ-ID</var>:<var class="keyword varname">Geräte-ID</var></pre>|

Dabei gilt:
- *Organisations-ID* ist die aus sechs Zeichen bestehende eindeutige Organisations-ID, die beim Registrieren des Service generiert wurde.
- *appId* ist eine benutzerdefinierte eindeutige Zeichenfolge-ID für den Client.
- *Geräte-ID* gibt ein Gerät oder Gateway unter allen Typen analog zu einer Seriennummer eindeutig an.
- *Gerätetyp* ist die ID für den Typ des Geräts, für das eine Verbindung aufgebaut wird, und sie ist analog zu einer Modellnummer.
- *Type-ID* ist eine ID für den Typ des Gateways, für das eine Verbindung aufgebaut wird, und sie ist analog zu einer Modellnummer.

Die Werte für *Anwendungs-ID*, *Typ-ID*, *Gerätetyp* und *Geräte-ID* dürfen nicht länger als 36 Zeichen sein und sie dürfen nur folgende Zeichen enthalten:
- Alphanumerische Zeichen (a-z, A-Z, 0-9)
- Gedankenstriche (-)
- Unterstreichungszeichen (_)
- Punkte (.)

**Hinweise:**
- Wenn Sie eine Verbindung zum Quickstart-Service herstellen, ist eine Authentifizierung nicht erforderlich.
- Sie müssen eine Anwendung nicht registrieren, bevor Sie eine Verbindung für diese Anwendung herstellen.

Informationen zum Format gemeinsam genutzter Abonnements finden Sie in [MQTT-Konnektivität für Anwendungen ![Symbol für externen Link](../../../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/applications/mqtt.html){: new_window}. 


### Verbindungen für Anwendungen mithilfe von MQTT herstellen

{{site.data.keyword.iot_short_notm}}-Anwendungen erfordern einen API-Schlüssel, um eine Verbindung zu einer Organisation herzustellen. Nach Registrierung eines API-Schlüssels wird ein Token generiert, das zusammen mit diesem API-Schlüssel verwendet werden muss.

Der folgende Code zeigt ein Beispiel eines API-Schlüssels:

<pre class="pre">a-<var class="keyword varname">Organisations-ID</var>-a84ps90Ajs</pre>
{: codeblock}

Das folgende Beispiel zeigt ein typisches Authentifizierungstoken:

```
 MP$08VKz!8rXwnR-Q*
```

Wenn Sie mithilfe eines API-Schlüssels eine MQTT-Verbindung herstellen, müssen Sie sicherstellen, dass folgende Anforderungen erfüllt werden:

- Die MQTT-Client-ID hat das folgende Format: a:*Organisations-ID*:*Anwendungs-ID*
- Der MQTT-Benutzername ist der API-Schlüssel, zum Beispiel: a-*Organisations-ID*-a84ps90Ajs.
- Das MQTT-Kennwort ist das Authentifizierungstoken, zum Beispiel: *MP$08VKz!8rXwnR-Q**

Weitere Informationen finden Sie in [MQTT-Konnektivität für Anwendungen ![Symbol für externen Link](../../../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/applications/mqtt.html){: new_window}. 

### Geräteauthentifizierung

#### Benutzernamen
Der {{site.data.keyword.iot_short_notm}}-Service unterstützt nur die tokenbasierte Authentifizierung für Geräte; daher hat jedes Gerät nur einen einzigen Benutzernamen, der gültig ist.
Der Wert `use-token-auth` gibt für den Service an, dass das Authentifizierungstoken für das Gateway oder das Gerät als Kennwort für die MQTT-Verbindung verwendet wird.

Weitere Informationen finden Sie in [MQTT-Konnektivität für Geräte ![Symbol für externen Link](../../../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/devices/mqtt.html){: new_window}. 

#### Kennwörter
Wenn der Client die tokenbasierte Authentifizierung verwendet, übergeben Sie das Authentifizierungstoken des Geräts als Kennwort für alle MQTT-Verbindungen. 
