---

copyright:
  years: 2015, 2019
lastupdated: "2019-04-10"

keywords: IoT Platform organization, SIM devices, IBM Watson

subcollection: iot-platform

---

{:new_window: target="\_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:important: .important}

# Externe Services integrieren
{: #ref-index}

<p>Diese {{site.data.keyword.cloud}}-Dokumentationssammlung bezieht sich auf den Lite-Preisstrukturplan von {{site.data.keyword.iot_full}} und enthält grundlegende Informationen zum Einstieg, API-Referenzinformationen und allgemeine Informationen zur Fehlerbehebung.
Die vollständige Dokumentation zum {{site.data.keyword.iot_short_notm}}-Feature finden Sie in der [{{site.data.keyword.iot_short_notm}}-Produktdokumentation![Symbol für externen Link](../../../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html) im IBM Knowledge Center. Weitere Informationen zu den verschiedenen Plänen finden Sie in [{{site.data.keyword.iot_short_notm}}-Servicepläne](/docs/services/IoT?topic=iot-platform-plans_overview#plans_overview).
</p>
{: important}

Die Integration von externen Services ermöglicht Ihnen den Zugriff auf Daten und Operationen von Drittanbietern oder externen Services innerhalb Ihrer {{site.data.keyword.iot_full}}-Organisation.

## Jasper
{: #jasper}

Jasper ist eine Verwaltungs- und Managementplattform für SIM-Geräte. Jasper ist in das Dashboard von {{site.data.keyword.iot_short_notm}} integriert, sodass es nun möglich ist, Jasper-Geräte über Ihr Organisationsdashboard von {{site.data.keyword.iot_short_notm}} zu verwalten.

### Unterstützte Operationen für Jasper

Die von Ihrer Plattform bereitgestellte Integration von Jasper bietet Unterstützung für folgende Jasper-Operationen:

- Gesamte Jasper-Daten anzeigen
  - Status, Tarifplan, Datennutzung für den Monat bisher, SMS-Nutzung für den Monat bisher, Telefonnutzung für den Monat bisher, Überschreitungsgrenzwerte, Hinzufügungsdatum und Änderungsdatum werden angezeigt.
- SIM-Aktivierungsstatus ändern
  - Folgendes kann ausgewählt werden: Bestand, Aktivierungsbereit, Aktiviert, Inaktiviert und Ruhezustand.
- SIM-Nutzung anzeigen
  - Zyklusstartdatum, abrechnungsfähige und gesamte Datennutzung, abrechnungsfähige und gesamte SMS-Nutzung, abrechnungsfähige und gesamte Telefonnutzung werden angezeigt.
  - Das Zyklusstartdatum kann im Datumsformat JJJJ-MM-TT festgelegt werden.
- SMS an SIM senden
- Tarifplan ändern

Sie können auf die unterstützten Operationen im Menü 'Drilldown für Geräte' eines mit Jasper verbundenen Geräts zugreifen, nachdem die nachfolgend beschriebenen Konfigurationsschritte abgeschlossen sind.

### REST-APIs für Jasper
Informationen für den Zugriff auf die REST-API für Jasper finden Sie im Abschnitt 'Jasper-Erweiterung' in der Dokumentation für die [{{site.data.keyword.iot_short_notm}}-HTTP-REST-API ![Symbol für externen Link](../../../../icons/launch-glyph.svg "Symbol für externen Link")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/ext-jasper.html){: new_window}.

### Konfiguration für Jasper

Zum Herstellen einer Verbindung vom Jasper-Service zur {{site.data.keyword.iot_short_notm}}-Organisation müssen zwei Konfigurationsphasen ausgeführt werden. Zunächst muss {{site.data.keyword.iot_short_notm}} mit Ihrem Jasper-Service verbunden werden, anschließend müssen Ihre {{site.data.keyword.iot_short_notm}}-Geräte konfiguriert werden.


1. Jasper-Erweiterung aktivieren. Führen Sie folgende Schritte aus, um die Integration von Jasper in Ihre {{site.data.keyword.iot_short_notm}}-Organisation zu ermöglichen.
  1. Wählen Sie im {{site.data.keyword.iot_short_notm}}-Dashboard die Option **Erweiterungen** aus.
  2. Klicken Sie auf der Seite **Erweiterungen** auf **Erweiterung hinzufügen**.
  3. Klicken Sie neben 'Jasper' auf **Hinzufügen**.
  4. Geben Sie Ihren Benutzernamen, das Kennwort, den Zugriffsschlüssel und die Domänen-ID für Jasper ein.
  5. Klicken Sie auf **Fertig**.

2. Geräte konfigurieren.
Sie können die Geräte, die sowohl mit Ihrer {{site.data.keyword.iot_short_notm}}-Organisation als auch mit Ihrem Jasper-Konto verbunden sind, so konfigurieren, dass Daten von Jasper im Dashboard von {{site.data.keyword.iot_short_notm}} angezeigt werden.  
**Wichtig:** Die Jasper-Konfiguration kann nicht im Rahmen des Prozesses zum Hinzufügen von Geräten angewendet werden. Nur zuvor bereits verbundene Geräte können mit Jasper konfiguriert werden.  
Führen Sie folgende Schritte aus, um Ihre mit Jasper verbundenen Geräte zu konfigurieren:
 1. Suchen Sie auf der Seite 'Geräte' des {{site.data.keyword.iot_short_notm}}-Dashboards nach dem zu konfigurierenden und mit Jasper verbundenen Gerät.
 2. Wählen Sie das Gerät aus, um die Ansicht 'Drilldown für Geräte' zu öffnen.
 3. Blättern Sie abwärts zur Option 'Erweiterungskonfiguration'.
 4. Geben Sie die Erweiterungskonfiguration ein, indem Sie das folgende JSON-Format verwenden, und klicken Sie anschließend auf **Änderungen bestätigen**, um die Konfiguration zu speichern.  

```json  
    {
        "jasper": {
            "iccid": "string"
        }
    }

```

Nach der erfolgreichen Konfiguration der Organisation wird der Abschnitt 'Erweiterungen' unterhalb des Abschnitts 'Erweiterungskonfiguration' in der Ansicht 'Drilldown für Geräte' angezeigt.

## AT&T
{: #att}

### Unterstützte Operationen für AT&T

Die AT&T-Erweiterung ermöglicht folgende AT&T-Operationen:

- Gesamte AT&T-Daten anzeigen
  - Status, Tarifplan, Datennutzung für den Monat bisher, SMS-Nutzung für den Monat bisher, Telefonnutzung für den Monat bisher, Überschreitungsgrenzwerte, Hinzufügungsdatum und Änderungsdatum werden angezeigt.
- SIM-Aktivierungsstatus ändern
  - Folgendes kann ausgewählt werden: Bestand, Aktivierungsbereit, Aktiviert, Inaktiviert und Ruhezustand.
- SIM-Nutzung anzeigen
  - Zyklusstartdatum, abrechnungsfähige und gesamte Datennutzung, abrechnungsfähige und gesamte SMS-Nutzung, abrechnungsfähige und gesamte Telefonnutzung werden angezeigt.
  - Das Zyklusstartdatum kann im Datumsformat JJJJ-MM-TT festgelegt werden.
- SMS an SIM senden
- Tarifplan ändern

### REST-APIs für AT&T
Informationen für den Zugriff auf die REST-API für AT&T finden Sie im Abschnitt 'AT&T-Erweiterung' in der Dokumentation für die [{{site.data.keyword.iot_short_notm}}-HTTP-REST-API ![Symbol für externen Link](../../../../icons/launch-glyph.svg "Symbol für externen Link")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/ext-atnt.html){: new_window}.

### Konfiguration für AT&T

Wenn Sie Ihre {{site.data.keyword.iot_short_notm}}-Organisation mit AT&T verbinden möchten, müssen Sie eine Organisationskonfiguration und eine Gerätekonfiguration ausführen.

Führen Sie die folgenden Schritte aus, um die {{site.data.keyword.iot_short_notm}}-Plattform zu konfigurieren:

1. AT&T-Erweiterung aktivieren. Führen Sie folgende Schritte aus, um die Integration von AT&T und der {{site.data.keyword.iot_short_notm}}-Organisation zu aktivieren:
  1. Wählen Sie im {{site.data.keyword.iot_short_notm}}-Dashboard die Option **Erweiterungen** aus.
  2. Klicken Sie auf der Seite **Erweiterungen** auf **Erweiterung hinzufügen**.
  3. Klicken Sie neben AT&T auf die Option **Hinzufügen**.
  4. Geben Sie Ihren Benutzernamen, das Kennwort, den Zugriffsschlüssel und die Domänen-ID für AT&T ein.
  5. Klicken Sie auf **Fertig**.

Zum Herstellen einer Verbindung von der {{site.data.keyword.iot_short_notm}}-Organisation zum AT&T-Konto müssen zwei Konfigurationsphasen ausgeführt werden. Führen Sie die Konfiguration der Organisation aus und konfigurieren Sie anschließend Ihre Geräte.


2. Geräte konfigurieren
Sie können die Geräte, die sowohl mit Ihrer {{site.data.keyword.iot_short_notm}}-Organisation als auch mit Ihrem AT&T-Konto verbunden sind, so konfigurieren, dass Daten von AT&T im {{site.data.keyword.iot_short_notm}}-Dashboard angezeigt werden.  
**Wichtig:** Die AT&T-Konfiguration kann nicht im Rahmen des Prozesses zum Hinzufügen von Geräten angewendet werden. Nur zuvor bereits verbundene Geräte können mit AT&T konfiguriert werden.  
Führen Sie folgende Schritte aus, um Ihre mit AT&T verbundenen Geräte zu konfigurieren:
 1. Suchen Sie auf der Seite 'Geräte' des {{site.data.keyword.iot_short_notm}}-Dashboards nach dem zu konfigurierenden und mit AT&T verbundenen Gerät.
 2. Wählen Sie das Gerät aus, um die Ansicht 'Drilldown für Geräte' zu öffnen.
 3. Blättern Sie abwärts zur Option 'Erweiterungskonfiguration'.
 4. Geben Sie die Erweiterungskonfiguration ein, indem Sie das folgende JSON-Format verwenden, und klicken Sie anschließend auf **Änderungen bestätigen**, um die Konfiguration zu speichern.  

```json  
    {
        "atnt": {
            "iccid": "string"
        }
    }

```

Nach der erfolgreichen Konfiguration der Organisation wird der Abschnitt 'Erweiterungen' unterhalb des Abschnitts 'Erweiterungskonfiguration' in der Ansicht 'Drilldown für Geräte' angezeigt.

## Arm Mbed-Bridge
{: #arm}

Mit der Bridge können Arm Mbed-Geräte in {{site.data.keyword.iot_short_notm}} integriert und bidirektional Nachrichten ausgetauscht werden. Um diese Integration zu ermöglichen, müssen Sie sich zuerst für ein ARM Mbed-Cloud-Konto registrieren und dann die angeforderten Verbindungsinformationen für Ihre {{site.data.keyword.iot_short_notm}}-Konfiguration angeben.

### Konfiguration für die Einrichtung


1. Aktivieren Sie die Erweiterung für die Arm Mbed-Bridge. Führen Sie dazu die folgenden Schritte aus:
  1. Wählen Sie im {{site.data.keyword.iot_short_notm}}-Dashboard die Option **Erweiterungen** aus.
  2. Klicken Sie auf der Seite 'Erweiterungen' auf **Erweiterung hinzufügen**.
  3. Klicken Sie neben der Erweiterung für die Arm Mbed-Bridge auf **Hinzufügen**.
  4. Geben Sie den Zugriffsschlüssel für Arm Mbed ein. Sie können diesen Schlüssel über das Arm Mbed-Portal unter [https://portal.mbedcloud.com ![Symbol für externen Link](../../../../icons/launch-glyph.svg "Symbol für externen Link")](https://portal.mbedcloud.com){: new_window} erstellen.
  5. Prüfen Sie, ob die Berechtigungsnachweise richtig sind, indem Sie auf die Schaltfläche **Verbindung überprüfen** klicken.
  6. Klicken Sie auf **Fertig**.

### Nutzdatenformat

Die Arm Mbed-Plattform verwendet zwei Typen eingehender Nachrichten: Benachrichtigungen und asynchrone Antworten. {{site.data.keyword.iot_short_notm}} kann Befehle an Geräte senden, die mit der Arm Mbed-Plattform verbunden sind.

#### Benachrichtigungen

Benachrichtigungen werden durch Änderungen in den Geräte- oder Sensordaten generiert. Nachdem {{site.data.keyword.iot_short_notm}} die Nachricht verarbeitet hat, wird sie auf dieselbe Weise an das Ereignistopic des Geräts gesendet wie bei einem Gerät, das direkt mit {{site.data.keyword.iot_short_notm}} verbunden ist. Der Ereignistyp, der für Benachrichtigungen verwendet wird, die von Geräten stammen, die mit der Arm Mbed-Plattform verbunden sind, lautet `notify`.

Das folgende Codebeispiel zeigt das Nutzdatenformat für eine Benachrichtigung, die von der API der Arm Mbed-Plattform gesendet wurde:

```
{
  "ep":<Endpunkt/Geräte-ID>,
  "path":<Ressourcenpfad>,
  "ct":<Inhaltstyp>,
  "payload":<Nutzdaten mit Base64-Codierung>,
  "max-age":<Gültigkeit der Nutzdaten in Sekunden>
}
```

#### Asynchrone Antworten

Wenn {{site.data.keyword.iot_short_notm}} einen Befehl an ein Gerät sendet, das mit der Arm Mbed-Plattform verbunden ist, sendet das Gerät eine Bestätigungsnachricht zurück an {{site.data.keyword.iot_short_notm}}. Diese Bestätigungsnachricht wird als _asynchrone Antwort_ bezeichnet und verwendet den Ereignistyp `asyncResponse`.

Das folgende Codebeispiel zeigt das Nutzdatenformat für eine asynchrone Antwort, die vom Arm Mbed-Cloud-Service gesendet wird:

```
{
  "id":<Transaktions-ID>,
  "status":<200, falls Befehl erfolgreich ausgeführt wurde. Überprüfen Sie weitere HTTP-Antwortcodes>,
  "ct":<Inhaltstyp>,
  "max-age":<Gültigkeit der Nutzdaten in Sekunden>,
  "payload":<Nutzdaten mit Base64-Codierung>,
  "ep":<Endpunkt/Geräte-ID, der/die vom Befehl betroffen ist>,
  "path":<Ressourcenpfad, der vom Befehl betroffen ist>
}
```

#### Befehle an die Arm Mbed-Plattform senden

{{site.data.keyword.iot_short_notm}} kann Befehle an Geräte senden, die mit der Arm Mbed-Plattform verbunden sind. An die Arm Mbed-Plattform gesendete Befehle müssen das folgende JSON-Format aufweisen:

```
{
  "method":<PUT oder POST>,
  "deviceId":<Endpunkt/Geräte-ID>,
  "resourceId":<Ressourcenpfad>,
  "payload": <Nutzdaten mit Base64-Codierung>
}
```
Bei der gewählten Methode muss die Groß-/Kleinschreibung beachtet werden. Die erste Angabe `/` des Ressourcenpfads muss übersprungen werden.


Die Nutzdaten müssen im folgenden Topic publiziert werden:

```
iot-2/type/<Gerätetyp>/id/<Geräte-ID>/cmd/<Befehlstyp>/fmt/<Befehlsformat>
```

<!--
## Orange
{: #orange}

The Orange extension allows you to view SIM card data from devices that are connected to your {{site.data.keyword.iot_short_notm}} and have an Orange SIM card installed.

### Supported operations for Orange

If you have a device that is connected to your {{site.data.keyword.iot_short_notm}} service and has an Orange SIM card, you can use the Orange extension to view the following SIM card data:

- SIM serial number
- Activation status
- Last status change
- Last status refresh
- Location status

### REST APIs for Orange
To access the REST API for Orange, see the Orange Extension section in the [{{site.data.keyword.iot_short_notm}} HTTP REST API ![External link icon](../../../../icons/launch-glyph.svg "External link icon")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/ext-orange.html){: new_window} documentation.

### Configuration for Orange

To enable the Orange extension:

1. From the {{site.data.keyword.iot_short_notm}} dashboard, select **Extensions**.
2. On the **Extensions** page, click **Add Extension**.
3. Click **Add** next to the Orange extension.
4. Enter your Orange user name and password.
6. Click **Done**.

After the Orange extension has been enabled, each device that has an Orange SIM card must be configured to display Orange SIM data.

1. In the devices tab of your {{site.data.keyword.iot_short_notm}} dashboard, find the Orange SIM device to configure.
2. Select the device and scroll down to **Extension Configuration**.
3. Enter the extension configuration by using the following JSON format and then click **Confirm changes** to save your configuration.

```json
    {
        "orange": {
            "serialnumber": "<serial number of Orange SIM>"
        }
    }

```
When the organization is successfully configured, the Extensions section is displayed under the Extensions Configuration section in the Device Drilldown view.
-->

## Speicherung von Langzeitdaten
{: #historical_data}

Die Erweiterung für das Speichern von Langzeitdaten ermöglicht es Ihnen, kompatible Nachrichtenspeicherservices, wie zum Beispiel [{{site.data.keyword.cloudantfull}} ![Symbol für externen Link](../../../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/cloudant_connector.html){: new_window} oder [{{site.data.keyword.messagehub_full}} ![Symbol für externen Link](../../../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/message_hub.html){: new_window}, für Ihre IoT-Daten zu suchen und zu konfigurieren.

## Angepasste Pakete für das Gerätemanagement
{: #device_mgmt}

Das Gerätemanagement ist eine zentrale Funktion von {{site.data.keyword.iot_short_notm}}, die jedoch erweitert werden kann, um zusätzliche Funktionen zu entwickeln. Angepasste Pakete für das Gerätemanagement müssen gültiges JSON-Format enthalten und mindestens eine angepasste Gerätemanagementaktion definieren.

Weitere Informationen zu angepassten Gerätemanagementfunktionen sowie ein Beispiel für das erforderliche JSON-Format finden Sie in [Angepasste Erweiterungen für das Gerätemanagement ![Symbol für externen Link](../../../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/devices/device_mgmt/custom_actions.html){: new_window}.

### Angepasstes Gerätemanagementpaket hinzufügen

Sie können angepasste Pakete für das Gerätemanagement mit dem {{site.data.keyword.iot_short_notm}}-Dashboard hinzufügen oder mithilfe der API.

Gehen Sie wie folgt vor, um ein angepasstes Paket für das Gerätemanagement mithilfe des {{site.data.keyword.iot_short_notm}}-Dashboards hinzuzufügen:

1. Klicken Sie in Ihrem {{site.data.keyword.iot_short_notm}}-Dashboard in der Navigationsleiste auf **Einstellungen**.
2. Klicken Sie auf **Angepasste Gerätemanagementpakete**.
3. Klicken Sie auf die Schaltfläche **Paket hinzufügen**.
4. Wählen Sie Ihre Paketdatei aus und klicken Sie auf **Öffnen**.

Informationen zum Hinzufügen eines angepassten Gerätemanagementpakets mithilfe der API finden Sie in der Dokumentation für die [{{site.data.keyword.iot_short_notm}}-API ![Symbol für externen Link](../../../../icons/launch-glyph.svg "Symbol für externen Link")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/orgAdmin.html){: new_window}.

## E-Mail
{: #email}

Benutzer können mithilfe von E-Mail-Einladungen zu {{site.data.keyword.iot_short_notm}} hinzugefügt werden. Informationen finden Sie in [Benutzerzugriff verwalten](/docs/services/IoT?topic=iot-platform-managing-user-access#managing-user-access).

Damit die Funktion für E-Mail-Einladungen verwendet werden kann, muss eine E-Mail-Erweiterung für die Verwendung des SendGrid-Onlineservice oder eines SMTP-Service (Simple Mail Transfer Protocol) konfiguriert sein. Die Erweiterung kann auch die {{site.data.keyword.cloud_notm}}-Anwendung SendGrid verwenden.

### SendGrid-Onlineservice

Führen Sie die folgenden Schritte aus, um die E-Mail-Erweiterung für die Verwendung mit dem SendGrid-Onlineservice zu konfigurieren:

1. Rufen Sie den berechtigten API-Schlüssel aus Ihrem SendGrid-Onlinekonto ab.
2. Klicken Sie in Ihrem {{site.data.keyword.iot_short_notm}}-Dashboard in der Navigationsleiste auf **Erweiterungen**.
3. Klicken Sie im Abschnitt **E-Mail** auf **Einrichten**.
4. Wählen Sie **SendGrid mit API-Schlüssel** aus.
5. Geben Sie den Namen und die E-Mail-Adresse Ihres Siteadministrators und den berechtigten API-Schlüssel ein.

### SMTP-Service

Führen Sie die folgenden Schritte aus, um die E-Mail-Erweiterung für die Verwendung mit einem SMTP-Service zu konfigurieren:

1. Klicken Sie in Ihrem {{site.data.keyword.iot_short_notm}}-Dashboard in der Navigationsleiste auf **Erweiterungen**.
2. Klicken Sie im Abschnitt **E-Mail** auf **Einrichten**.
3. Wählen Sie **SMTP** aus.
4. Geben Sie die Konfigurationsdetails Ihres SMTP-Service ein.

### {{site.data.keyword.cloud_notm}}-Anwendung SendGrid

Führen Sie die folgenden Schritte aus, um die E-Mail-Erweiterung für die Verwendung der {{site.data.keyword.cloud_notm}}-Anwendung SendGrid zu konfigurieren:

1. Erstellen Sie eine Dummy-Anwendung und binden Sie sie an den SendGrid-Service.  
Fügen Sie den SendGrid-Service zu einer Dummy-Anwendung hinzu und binden Sie ihn an sie, um die Konfigurationsberechtigungsnachweise abzurufen.

 1. Klicken Sie in Ihrem {{site.data.keyword.cloud_notm}}-Dashboard auf **Service erstellen**.
 2. Wählen Sie den SendGrid-Service aus dem Katalog aus und klicken Sie auf **Erstellen**.
 3. Fügen Sie im {{site.data.keyword.cloud_notm}}-Dashboard die Anwendung {{site.data.keyword.runtime_nodejs_full}} hinzu.
 4. Klicken Sie im {{site.data.keyword.cloud_notm}}-Dashboard auf die Anwendung {{site.data.keyword.runtime_nodejs_notm}} und klicken Sie auf **Service oder API binden**. 
 5. Wählen Sie den SendGrid-Service aus und klicken Sie auf **Hinzufügen**.
 6. Führen Sie ein erneutes Staging für die Anwendung {{site.data.keyword.runtime_nodejs_notm}} durch.
2. Bereiten Sie die Konfiguration des {{site.data.keyword.iot_short_notm}}-Service vor.  
{{site.data.keyword.iot_short_notm}} kann mithilfe des {{site.data.keyword.iot_short_notm}}-Dashboards oder mithilfe der {{site.data.keyword.iot_short_notm}}-API konfiguriert werden.  
 1. Klicken Sie im {{site.data.keyword.cloud_notm}}-Dashboard auf die {{site.data.keyword.runtime_nodejs_notm}}-Anwendung. 
 2. Klicken Sie in der Navigationsleiste auf **Umgebungsvariablen**.
 3. Kopieren Sie die angezeigte JSON in eine temporäre Textdatei.  
 Die JSON sollte folgendes Format aufweisen:
```
{
  "name": "SendGridServiceName",
  "label": "user-provided",
  "credentials": {
    "password": "xxx",
    "hostname": "smtp.sendgrid.net",
    "username": "username"
  }
}
```
3. Fügen Sie die Konfigurationsdaten zur {{site.data.keyword.iot_short_notm}}-Organisation hinzu.
 1. Öffnen Sie das {{site.data.keyword.iot_short_notm}}-Dashboard.
 2. Klicken Sie in der Navigationsleiste auf **Erweiterungen**.
 3. Klicken Sie unter dem Symbol **E-Mail** auf **Einrichten**.
 4. Wählen Sie **SendGrid mit Benutzername** aus.
 5. Geben Sie die Konfigurationsdaten aus der temporären Textdatei ein.
 6. Klicken Sie auf **Fertig**.
