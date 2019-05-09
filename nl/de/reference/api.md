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


# APIs
{: #api_overview}

<p>Diese {{site.data.keyword.cloud}}-Dokumentationssammlung bezieht sich auf den Lite-Preisstrukturplan von {{site.data.keyword.iot_full}} und enthält grundlegende Informationen zum Einstieg, API-Referenzinformationen und allgemeine Informationen zur Fehlerbehebung.
Die vollständige Dokumentation zum {{site.data.keyword.iot_short_notm}}-Feature finden Sie in der [{{site.data.keyword.iot_short_notm}}-Produktdokumentation![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html) im IBM Knowledge Center. Weitere Informationen zu den verschiedenen Plänen finden Sie in [{{site.data.keyword.iot_short_notm}}-Servicepläne](/docs/services/IoT?topic=iot-platform-plans_overview#plans_overview).
</p>
{: important}

Zum Entwickeln von Code für Geräte, Gateways und Anwendungen, die Verbindungen zu {{site.data.keyword.iot_full}} herstellen, stehen mehrere APIs zur Verfügung.

Die HTTP-APIs sind durch HTTP-Basisauthentifizierung geschützt. Wenn Sie im Dashboard einen API-Schlüssel generieren, erhalten Sie einen Schlüssel und ein Authentifizierungstoken. Weitere Informationen zu API-Schlüsseln und Token finden Sie unter [Verbindung über API-Schlüssel![Symbol für externen Link](../../../icons/launch-glyph.svg)](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/platform_authorization.html#api-key){: new_window}.


## Informationen zu HTTP-APIs
{: #api_about}

Jede {{site.data.keyword.iot_short_notm}}-Organisation ist mit einer aus 6 Zeichen bestehenden Organisations-ID angegeben, die im Hostnamen für jeden HTTP-API-Aufruf erforderlich ist.    

### API-Dokumentation
{: #api_docs}

Zur Anzeige der API-Dokumentation rufen Sie die Seite [IBM Watson IoT Platform REST APIs ![Symbol für externen Link](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/index.html){: new_window} auf. Von dieser Landing-Page aus können Sie auf die Dokumentation für die verfügbaren {{site.data.keyword.iot_short_notm}}-APIs zugreifen.

### Interaktive API-Dokumentation

Zur Anzeige und Verwendung der interaktiven API-Dokumentation kann auf die Basis-URL für Ihre Organisation über die folgende Adresse zugegriffen werden:

`https://<orgId>.internetofthings.ibmcloud.com/docs/index.html`

Von dieser Landing-Page aus können Sie auf die Dokumentation für die verfügbaren {{site.data.keyword.iot_short_notm}}-APIs zugreifen. Sie müssen autorisiert sein, um die API-Aufrufe direkt von der Dokumentation aus auszuführen. 

Führen Sie die folgenden Schritte aus, um automatisch berechtigt zu werden: 

1. Melden Sie sich beim {{site.data.keyword.iot_short_notm}}-Dashboard an.
2. Öffnen Sie in demselben Browser eine neue Registerkarte und wechseln Sie zur Landing-Page der interaktiven API-Dokumentation. 

Wenn Sie nicht beim {{site.data.keyword.iot_short_notm}}-Dashboard angemeldet sind, führend Sie die folgenden Schritte aus: 

1. Wechseln Sie zur Landing-Page der interaktiven API-Dokumentation. 
2. Wählen Sie `Berechtigen` aus.
3. Legen Sie in der Anzeige `Verfügbare Berechtigungen` den Benutzernamen für den API-Schlüssel und das Kennwort für das Authentifizierungstoken fest.  Wählen Sie `Berechtigen` aus.
4. Schließen Sie die Anzeige `Verfügbare Berechtigungen`. **Wichtig:** Wählen Sie nicht `Abmelden` (oder Abmeldung) aus.

Nachdem Sie berechtigt wurden, wechseln Sie zu den jeweiligen API-Aufrufen und verwenden die Schaltfläche `Probieren Sie es aus`, um die API-Aufrufe direkt von der Dokumentation aus auszuführen. 

<!-- To authenticate requests to the application API, set the username to the API key and the password to the authentication token. -->
