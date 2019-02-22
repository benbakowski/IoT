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


# APIs
{: #api_overview}

<p>Diese {{site.data.keyword.Bluemix}}-Dokumentationssammlung bezieht sich auf den Lite-Preisstrukturplan von {{site.data.keyword.iot_full}} und enthält grundlegende Informationen zum Einstieg, API-Referenzinformationen und allgemeine Informationen zur Fehlerbehebung.
Die vollständige Dokumentation zum {{site.data.keyword.iot_short_notm}}-Feature finden Sie in der [{{site.data.keyword.iot_short_notm}}-Produktdokumentation![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html) im IBM Knowledge Center. Weitere Informationen zu den verschiedenen Plänen finden Sie in [{{site.data.keyword.iot_short_notm}}-Servicepläne](/docs/IoT/plans_overview.html#plans_overview).
</p>
{: important}

Zum Entwickeln von Code für Geräte, Gateways und Anwendungen, die Verbindungen zu {{site.data.keyword.iot_full}} herstellen, stehen mehrere APIs zur Verfügung.

Die HTTP-APIs sind durch HTTP-Basisauthentifizierung geschützt. Wenn Sie im Dashboard einen API-Schlüssel generieren, erhalten Sie einen Schlüssel und ein Authentifizierungstoken. Weitere Informationen zu API-Schlüsseln und Tokens finden Sie in [Verbindung über API-Schlüssel ![Symbol für externen Link](../../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/platform_authorization.html#api-key). 


## Informationen zu HTTP-APIs
{: #api_about}

Nachdem Sie sich für Ihre eigene Organisation registriert haben, erhalten Sie eine aus sechs Zeichen bestehende Organisations-ID, die im Hostnamen für alle HTTP-API-Aufrufe angegeben sein muss. Auf die Basis-URL für Ihre Organisation kann über die folgende Adresse zugegriffen werden:

https://<**orgId**>.internetofthings.ibmcloud.com/api/v0002

Zum Authentifizieren von Anforderungen bei der Anwendungs-API legen Sie den API-Schlüssel als Benutzernamen und das Authentifizierungstoken als Kennwort fest.

Verwenden Sie für Messaging-APIs die folgende Adresse:

https://<**orgId**>.messaging.internetofthings.ibmcloud.com/api/v0002

## HTTP-APIs
{: #api_http}

API                     | Verwendungszweck       
------------- | -------------
[Organisationsadministration ![Symbol für externen Link](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/orgAdmin.html){: new_window} | Konfigurieren einer Organisation (einschließlich Erstellen und Löschen von Geräten), Überprüfen der Nutzung, Anzeigen des Servicestatus und Diagnostizieren von Geräteverbindungsproblemen.
[Sicherheit ![Symbol für externen Link](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/security.html){: new_window} | Verwalten der Authentifizierung und Berechtigung von Benutzern, API-Schlüsseln und Geräten.
[Information Management ![Symbol für externen Link](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/info-mgmt.html){: new_window} |  Zugriff auf Geräteereignisdaten, Abrufen und Aktualisieren der Geräteposition sowie Abrufen von Wetterdaten für diese Position. 
[Datenmanagement  ![Symbol für externen Link](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/state-mgmt.html){: new_window}   |   Organisieren und Integrieren von ein- und ausgehenden Daten für {{site.data.keyword.iot_short_notm}}.
[Gerätemanagement ![Symbol für externen Link](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/deviceMgmt.html){: new_window} | Interagieren mit verwalteten Geräten mithilfe des Gerätemanagementprotokolls.
[Messaging ![Symbol für externen Link](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/http-messaging.html){: new_window}   | Publizieren von Ereignissen und Senden von Befehlen mithilfe von HTTP.
[Risikomanagement ![Symbol für externen Link](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/riskmgmt.html){: new_window}   | Verwalten von Richtlinien und Berichten für das Risikomanagement.

## Erweiterungs-HTTP-APIs
{: #api_extension}

API                     | Verwendungszweck       
------------- | -------------
[AT&T-Erweiterung ![Symbol für externen Link](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/ext-atnt.html){: new_window} | Verwalten von AT&T-Geräten.
[Jasper-Erweiterung ![Symbol für externen Link](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/ext-jasper.html){: new_window} | Verwalten von Jasper-Geräten.
[Orange-Erweiterung ![Symbol für externen Link](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/ext-orange.html){: new_window} | Anzeigen von Daten der SIM-Karte von Geräten, die mit Ihrer {{site.data.keyword.iot_short_notm}}-Organisation verbunden sind und in die eine Orange-SIM-Karte installiert ist.

## Beta-HTTP-APIs
{: #api_beta}

API                     | Verwendungszweck       
------------- | -------------
[Gelöschte Geräte wiederherstellen ![Symbol für externen Link](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002-beta/restore-device-beta.html){: new_window}   | Wenn ein Gerät versehentlich gelöscht wird, kann es innerhalb von 14 Tagen wiederhergestellt werden.
