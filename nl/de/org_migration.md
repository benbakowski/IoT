---

copyright:
  years: 2016, 2019
lastupdated: "2019-04-05"

keywords: Lite plan, migrate, Watson IoT Platform

subcollection: iot-platform

---

{:new_window: target="\_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:important: .important}

# Migration von {{site.data.keyword.iot_short_notm}}-Lite-Plänen auf {{site.data.keyword.iot_short_notm}}-Pläne für Produktionsumgebungen oder nicht für die Produktion verwendete Umgebungen
{: #org_migration}

<p>Diese {{site.data.keyword.cloud}}-Dokumentationssammlung bezieht sich auf den Lite-Preisstrukturplan von {{site.data.keyword.iot_full}} und enthält grundlegende Informationen zum Einstieg, API-Referenzinformationen und allgemeine Informationen zur Fehlerbehebung.
Die vollständige Dokumentation zum {{site.data.keyword.iot_short_notm}}-Feature finden Sie in der [{{site.data.keyword.iot_short_notm}}-Produktdokumentation![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html) im {{site.data.keyword.IBM}} Knowledge Center. Weitere Informationen zu den verschiedenen Plänen finden Sie in [{{site.data.keyword.iot_short_notm}}-Servicepläne](/docs/services/IoT?topic=iot-platform-plans_overview#plans_overview).
</p>
{: important}

Nachdem Sie die ersten Erfahrungen mit dem Lite-Plan von Watson IoT Platform gesammelt und sich einen Überblick über die Integrationsmöglichkeiten in Ihre IoT-Umgebung verschafft haben, können Sie ein Upgrade auf [einen der Watson IoT Platform-Pläne für Produktionsumgebungen oder für nicht für die Produktion verwendete Umgebungen ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html){: new_window} durchführen.
{:shortdesc}

**Hinweis:** Dieses Dokument ist nur für Benutzer mit eine Lite-Instanz vorgesehen. Wenn Sie zuvor IoT Platform-Instanzen im Rahmen der Standard- oder Advanced Security-Pläne erstellt haben, unterstützt Sie {{site.data.keyword.IBM}} dabei, die vorhandene {{site.data.keyword.iot_short_notm}}-Instanz auf die neuen Pläne für Produktionsumgebungen oder für nicht für die Produktion verwendete Umgebungen zu migrieren.

## Übersicht über den Migrationsprozess
{: #org_migration_overview}

Durch eine Migration auf {{site.data.keyword.iot_short_notm}} werden die für Lite-Pläne gültigen Grenzwerte von 500 Geräten und einer monatlichen Datennutzung entfernt.

Die {{site.data.keyword.iot_short_notm}}-Pläne enthalten die folgenden zusätzlichen Komponenten zur Unterstützung der End-to-End-Anwendungsarchitektur von IoT:

- {{site.data.keyword.messagehub}} - von {{site.data.keyword.IBM_notm}} gehostete Version der Kafka-Streamingplattform, die Ihre Anwendungen für den Empfang von IoT-Daten nutzen können.
- {{site.data.keyword.dashdbshort}} - für die Analysedatenspeicherung.
- {{site.data.keyword.cloudantfull}} - Datenbank für Zeitreihendaten.
- {{site.data.keyword.cos_full}} - für die langfristige Datenspeicherung.

In diesem Dokument werden die Datentypen beschrieben, die Sie von einer vorhandenen Lite-Instanz auf eine vollständige Version migrieren können.

**Hinweis:** Im Allgemeinen ist es am einfachsten, die {{site.data.keyword.iot_short_notm}}-Produktionsumgebung bzw. die nicht für die Produktion verwendete Umgebung völlig neu einzurichten, da sie Komponenten und Features enthält, die über den {{site.data.keyword.iot_short_notm}}-Lite-Service hinaus gehen. Darüber hinaus werden die für Tests in der Lite-Version erstellten Geräte und Benutzer voraussichtlich nicht identisch mit denen sein, die für die Produktion verwendet werden.

Wenn Sie jedoch einige der vorhandenen Lite-Einstellungen übernehmen möchten, werden Sie anhand der folgenden Abschnitte durch den Prozess geführt.

Die Dokumentation zu den [{{site.data.keyword.iot_short_notm}}-APIs]/docs/services/IoT?topic=iot-platform-api_overview#api_overview) enthält Anweisungen zum Aufrufen der APIs und eine Beschreibung sämtlicher Parameter. 


## Vorbereitende Schritte
{: #org_migration_byb}

Bevor Sie den Migrationsprozess starten können, müssen Sie {{site.data.keyword.iot_short_notm}} (für die Produktion oder nicht für die Produktion) kaufen. Beim Kauf stellt Ihnen das operative Team von {{site.data.keyword.IBM_notm}} eine neue {{site.data.keyword.iot_short_notm}}-Instanz zur Verfügung. Hierzu gehört eine neue sechsstellige alphanumerische Organisations-ID.


## Benutzer migrieren
{: #user_migration}

Mithilfe von [Benutzerverwaltungs-APIs ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/security.html#!/Authorization_-_User_Management){: new_window} können Massenexporte und -importe von {{site.data.keyword.iot_short_notm}}-Benutzern durchgeführt werden. Auf diese Weise können Sie die Benutzer, die in der neuen Organisation beibehalten werden sollen, exportiert und importiert werden.

1. Benutzer aus der Lite-Organisation exportieren.  
Mit dem Befehl `GET /authorization/users` können Sie alle Benutzer als JSON-Objekt aus der Organisation Ihres Lite-Kontos exportieren.
2. Benutzerliste bereinigen.  
Bearbeiten Sie bei Bedarf die JSON-Struktur, um Benutzer zu entfernen, die nicht in die neue Organisation migriert werden sollen.
3. Benutzer in die neue Organisation importieren.  
Mit dem Befehl `POST /authorization/users/multiple` können Sie die bearbeitete JSON-Liste der Benutzer in die neue Organisation importieren. 

Die Benutzer verfügen nun über Zugriff auf die neue Organisation, die in der Organisationsauswahl im {{site.data.keyword.iot_short_notm}}-Dashboard angezeigt wird.

##  Geräte migrieren  
{: #device_migration}

Für die Migration von Geräten können diese Schritte ausgeführt werden werden:  
1. Die Gerätetypen migrieren, die in der neuen Organisation beibehalten werden sollen.  
2. Die Geräte selbst in die neue Organisation migrieren.  
3. Den Hostnamen, den die Geräte zum Herstellen einer Verbindung zu {{site.data.keyword.cloud_notm}} verwenden, so aktualisieren, dass er mit der neuen Organisations-ID beginnt.
4. Auf der Lite-Plattform erstellte Datenverwaltungsinformationen migrieren.   
Hierzu können physische und logische Geräteschnittstellen, Dinge und Regeln gehören.

<p>Mit den folgenden APIs können Gerätetypen und Geräte in einer Massenoperation migriert werden:
<table>
<tr>
<th> API-Dokumentation </th>
<th> Export-API </th>
<th> Import-API </th>
</tr>
<tr>
<td> [Gerätetyp-API ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/org-admin.html) </td>
<td> `GET /device/types` </td>
<td> `POST /device/types` </td>
</tr>
<tr>
<td>  [Geräte-API ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/org-admin.html#!/Device_Bulk_Configuration) </td>
<td> `GET /bulk/devices` </td>
<td>  `POST /bulk/devices/add`</td>
</tr>
</table>
</p>
{: tip}


**Wichtig:** {{site.data.keyword.iot_short_notm}} speichert keine Geräteauthentifizierungstokens, nur Salt-Versionen davon. Der Aufruf `GET /bulk/devices` kann daher die Authentifizierungstoken für gespeicherte Geräte nicht zurückgeben. Falls Sie die Geräteauthentifizierungstokens dokumentiert haben, können Sie diese vor der Massenladeoperation zum JSON-Objekt hinzufügen. Andernfalls müssen Sie für jedes Gerät neue Geräteauthentifizierungstokens generieren und diese zu den Geräten kopieren.  

Wenn Sie anstelle von Authentifizierungstoken geräteseitige Zertifikate für die Authentifizierung von Geräten verwenden, müssen Sie diese Schritte nicht ausführen. Bei der Verwendung geräteseitiger Zertifikate müssen Sie jedoch die für die Signierung verwendeten Zertifikate in die neue Organisation hochladen.


## Geräte aktualisieren
{: #update_devices}

Wenn die Geräte in der neuen Organisation registriert sind, müssen Sie die Konfiguration bzw. den Code auf den vorhandenen Geräten so aktualisieren, dass sie den Hostnamen der neue Organisation verwenden.

Verwenden Sie für MQTT- und HTTP-Nachrichtenübertragungsclients den folgenden Hostnamen:  
`<orgId>.messaging.internetofthings.ibmcloud.com`

Verweisen Sie REST-API-Clients auf den folgenden Hostnamen:  
`<orgId>.internetofthings.ibmcloud.com`

**Wichtig:** Falls Sie neue Authentifizierungstokens für die Geräte generiert haben, müssen Sie diese zum jeweiligen Gerät kopieren.


## Migration des Gerätemanagements
{: #device_management}

Die [Datenverwaltungs-APIs ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/state-mgmt.html){: new_window} umfassen APIs für das Exportieren und Importieren von physischen und logischen Geräteschnittstellen, Definitionen für Dinge und Regeln.

**Wichtig:** {{site.data.keyword.iot_short_notm}} unterstützt zum gegenwärtigen Zeitpunkt das Konzept der Assetzwillinge für die Datenaufnahme nicht.

## Boards und Karten
{: #boards_cards}

{{site.data.keyword.iot_short_notm}} enthält keine APIs für das Importieren und Exportieren von Definitionen und Anpassungen für Boards und Karten. Sie müssen diese in der neuen Organisation manuell erneut erstellen.

## Gegebenenfalls erforderliche Erweiterungen aktivieren
{: #extensions}

Sie müssen alle Erweiterungen, die Sie auf der Lite-Plattform aktiviert haben, in der neuen Organisation erneut erstellen. Hierzu gehören z. B. Links zu {{site.data.keyword.messagehub}}, {{site.data.keyword.cloudant_short_notm}} und Jasper.

## Anwendungen migrieren
{: #application_migration}

Wenn Sie Anwendungen entwickelt haben, die APIs aufrufen, die mit dem Lite-Service von {{site.data.keyword.iot_short_notm}} angeboten werden, um beispielsweise Daten zu senden oder zu empfangen oder den Service zu verwalten, müssen Sie diese für die Verwendung der neuen, für die Produktion oder nicht für die Produktion genutzten {{site.data.keyword.iot_short_notm}}-Instanz aktualisieren. Dies gilt auch für alle Node-RED-Abläufe, die Sie möglicherweise verwenden.
Die Migration umfasst Folgendes:
- Aktualisieren der Anwendungen für die Verwendung einer neuen sechsstelligen Organisations-ID.
- Aktualisieren der Anwendungen für die Verwendung des API-Schlüssels und der Tokenberechtigungsnachweise, die Sie für die neue Serviceinstanz erstellt haben.

**Wichtig:** Wenn Sie eine Cloud Foundry-Bindung verwendet haben, um die Organisations-ID und die Berechtigungsnachweise an die Anwendung zu übergeben, müssen Sie einen anderen Mechanismus verwenden, da die neue {{site.data.keyword.iot_short_notm}}-Instanz nicht für die Ausführung in Ihrem Cloud Foundry-Bereich bereitgestellt wird.

### API-Verbindungsberechtigungsnachweise generieren

Welchen Migrationsprozess Sie verwenden, ist von der Art der Anwendung abhängig. Grundsätzlich besteht in allen Fällen der erste Schritt darin, einen API-Schlüssel und ein Authentifizierungstoken anzufordern, die die Anwendung verwenden kann.

1. Melden Sie sich beim übergeordneten Dashboard des neuen {{site.data.keyword.iot_short_notm}}-Service an.
2. Wählen Sie die Registerkarte **Nutzung** aus.
3. Klicken Sie auf den Link **Details anzeigen**, um die {{site.data.keyword.iot_short_notm}}-Serviceinformationen anzuzeigen.  
Die folgenden Informationen werden angezeigt:
   - Sechsstellige Organisations-ID
   - API-Schlüssel und Token  
   Verwenden Sie nicht den hier angezeigten API-Schlüssel, sondern generieren Sie neue API-Schlüssel für jede Anwendung. Auf diese Weise können Sie die entsprechenden Berechtigungen für jede Anwendung festlegen.
   - Host-URL.
4. Erstellen Sie eine Kombination aus API-Schlüssel und Authentifizierungstoken für Ihre Anwendung.  
Sie benötigen diese beim Konfigurieren der Anwendung für die Verbindung zu Ihrer Organisation.   
   1.  Klicken Sie auf `Starten`.  
   Hierdurch wird das zugrunde liegende Service-Dashboard aufgerufen, das Sie zur Verwaltung des Lite-Service von {{site.data.keyword.iot_short_notm}} verwendet haben.
   2. Wählen Sie **Apps** aus.
   3. Klicken Sie auf **API-Schlüssel generieren**.
   4. Kopieren Sie die Werte für den API-Schlüssel und das Authentifizierungstoken, die aufgelistet werden.
   5. Wählen Sie eine für Ihre Anwendung geeignete Rolle aus.   
   6. Fügen Sie einen Kommentar hinzu, sodass Sie die Kombination aus API-Schlüssel und Authentifizierungstoken einfach identifizieren können.
   7. Klicken Sie auf **Generieren**.
   8. **Wichtig:** Erstellen Sie eine lokale Kopie des Authentifizierungstokens. Es kann nach dem Schließen des Fensters nicht erneut erstellt werden.


### Node-RED-Anwendungen aktualisieren
Sie müssen die Node-RED-Knoten für die Verbindung zur neuen {{site.data.keyword.iot_short_notm}}-Instanz konfigurieren. Die `ibmiot`-Knoten werden die `BluemixService`-Authentifizierungsoption nicht mehr verwenden können, daher müssen Sie stattdessen die Option `API-Schlüssel` auswählen.
1. Öffnen Sie den Knoten `ibmiot` zur Bearbeitung.
2. Wählen Sie unter den Knoteneigenschaften **API-Schlüssel** aus.
3. Klicken Sie für das Feld 'API-Schlüssel' auf das Bearbeitungssymbol und geben Sie dann den API-Schlüssel und das Authentifizierungstoken ein, die Sie im vorherigen Schritt gespeichert haben.
4. Speichern Sie die Änderungen und stellen Sie den Node-RED-Ablauf erneut bereit.

### Anwendung aktualisieren, die keine Cloud Foundry-Bindung verwendet
Ermitteln Sie die Position, an der die Anwendung die Organisations-ID, den API-Schlüssel und das Authentifizierungstoken speichert, und ersetzen Sie diese durch die Werte, die Sie zuvor gespeichert haben. 

Wenn die Anwendung eines der {{site.data.keyword.iot_short_notm}}-SDKs verwendet, werden diese Werte wahrscheinlich in einer Eigenschaftendatei gespeichert.
{: tip}

### Anwendung aktualisieren, die eine Cloud Foundry-Bindung verwendet

{{site.data.keyword.cloud_notm}} stellt einen Mechanismus bereit, mit dem Cloud Foundry-Anwendungen an einen oder mehrere Cloud Foundry-Services gebunden werden können. Bindungen können über die {{site.data.keyword.cloud_notm}}-Befehlszeilenschnittstelle oder mithilfe einer `Verbindung` zwischen der Anwendung und dem Service im {{site.data.keyword.cloud_notm}}-Dashboard erstellt werden.

Wenn eine Anwendung an einen Service gebunden wird, werden die Berechtigungsnachweise des API-Schlüssels und des Authentifizierungstokens für den Service in die Umgebungsvariable `VCAP_SERVICES` kopiert, wo sie von der Anwendung abgerufen werden können.

**Wichtig:** Dieser Bindungsmechanismus kann im neuen {{site.data.keyword.iot_short_notm}}-Service nicht verwendet werden. Suchen Sie den Code in der Anwendung, der die Werte der Umgebungsvariablen `VCAP_SERVICES` abruft, und ersetzen Sie ihn durch Code, der diese Werte an der Position abruft, an der Sie den API-Schlüssel und das Authentifizierungstoken nun speichern. Um die Aktualisierung abzuschließen, müssen Sie die Anwendung erneut erstellen und erneut bereitstellen.
