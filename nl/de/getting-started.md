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


# Lernprogramm zur Einführung
{: #gettingstartedtemplate .task}

<p>Diese {{site.data.keyword.Bluemix}}-Dokumentationssammlung bezieht sich auf den Lite-Preisstrukturplan von {{site.data.keyword.iot_full}} und enthält grundlegende Informationen zum Einstieg, API-Referenzinformationen und allgemeine Informationen zur Fehlerbehebung.
Die vollständige Dokumentation zum {{site.data.keyword.iot_short_notm}}-Feature finden Sie in der [{{site.data.keyword.iot_short_notm}}-Produktdokumentation![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html) im IBM Knowledge Center. Weitere Informationen zu den verschiedenen Plänen finden Sie in [{{site.data.keyword.iot_short_notm}}-Servicepläne](/docs/IoT/plans_overview.html#plans_overview).
</p>
{: important}

In diesem {{site.data.keyword.iot_short_notm}}-Lernprogramm zur Einführung wird eine Verbindung von einem IoT-Gerät zu {{site.data.keyword.iot_short_notm}} hergestellt.
{:shortdesc}

## Informationen zu diesem Vorgang
{: #about .sectiontitle}  

Bevor Sie mit dem Empfang von Daten von Ihren IoT-Geräten beginnen können, müssen Sie sie mit {{site.data.keyword.iot_short_notm}} verbinden. Um ein Gerät mit {{site.data.keyword.iot_short_notm}} zu verbinden, muss das Gerät für {{site.data.keyword.iot_short_notm}} registriert werden; die Registrierungsinformationen werden anschließend verwendet, um das Gerät für die Verbindung zu {{site.data.keyword.iot_short_notm}} zu konfigurieren.

## Vorbereitende Schritte
{: #byb .sectiontitle}  

Bevor Sie mit der Verwendung von {{site.data.keyword.iot_short_notm}} beginnen können, benötigen Sie Folgendes:   
* Ein [{{site.data.keyword.Bluemix}}-Konto ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net/registration/){: new_window}. 
* Eine {{site.data.keyword.iot_short_notm}}-Instanz.   
Sie können eine {{site.data.keyword.iot_short_notm}}-Instanz direkt über die [{{site.data.keyword.iot_short_notm}}-Seite im {{site.data.keyword.Bluemix_short}}-Servicekatalog ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/catalog/services/internet-of-things-platform/){:new_window} erstellen.   
* Ein Gerät, das die folgenden Anforderungen erfüllt:   
  *	Ihr Gerät muss in der Lage sein, unter Verwendung der HTTP- oder MQTT-Protokolle zu kommunizieren.
  * Die Gerätenachrichten müssen den Anforderungen an die {{site.data.keyword.iot_short_notm}}-Nachrichtennutzdaten entsprechen.  
Weitere Informationen finden Sie in [Entwickeln von Geräten in {{site.data.keyword.iot_short_notm}} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/devices/device_dev_index.html){: new_window}. 

Abhängig von der jeweiligen Situation stehen die folgenden Optionen zur Verfügung: 

 |  |   Service ist bereitgestellt | Service ist nicht bereitgestellt
 | -------------| ------------- | -------------
  |**Ich verfüge über ein Gerät, das ich verbinden kann** | Den im vorliegenden Abschnitt beschriebenen Prozess durchführen. | Erkunden Sie das Herstellen von Verbindungen für Geräte in [{{site.data.keyword.iot_short_notm}} ausprobieren ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://discover-iot.eu-gb.mybluemix.net/?cm_mc_uid=44491599487314618721024&cm_mc_sid_50200000=1462798151#/play){:new_window}.
  |**Ich verfüge nicht über ein Gerät, das ich verbinden kann** | [Gerätedaten simulieren ](/docs/IoT/devices/device_sim.html) oder [Verbindung zum Smartphone herstellen ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://discover-iot.eu-gb.mybluemix.net/?cm_mc_uid=44491599487314618721024&cm_mc_sid_50200000=1462798151#/play/device/smartphone){:new_window}. | Beginnen Sie mit [{{site.data.keyword.iot_short_notm}} Starter](https://console.bluemix.net/docs/IoT-starter/iot500.html#gettingstartedtemplate){:new_window}.



## Schritt 1: Gerät registrieren
{: #step1 .sectiontitle}  
Zum Registrieren eines Geräts gehört die Klassifizierung des Geräts als bestimmten Gerätetyp, das Benennen des Geräts und das Bereitstellen von Geräteinformationen. Anschließend stellen Sie ein Verbindungstoken bereit oder Sie akzeptieren ein Token, das von {{site.data.keyword.iot_short_notm}} generiert wird.

**Tipp:** Sie können Geräte einzeln über das [{{site.data.keyword.iot_short_notm}}-Dashboard ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://internetofthings.ibmcloud.com){: new_window} registrieren oder Sie können die [{{site.data.keyword.iot_short_notm}}-API ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/org-admin.html#!/Device_Bulk_Configuration/post_bulk_devices_add){: new_window} verwenden, um mehrere Geräte hinzuzufügen. 

Gehen Sie wie folgt vor, um ein Gerät über das {{site.data.keyword.iot_short_notm}}-Dashboard hinzuzufügen:
1. Klicken Sie in der {{site.data.keyword.Bluemix_notm}}-Konsole auf der Detailseite für den {{site.data.keyword.iot_short_notm}}-Service auf **Starten**.

    Die {{site.data.keyword.iot_short_notm}}-Webkonsole wird in einer neuen Browserregisterkarte unter der folgenden URL geöffnet:

    ```
    https://org_id.internetofthings.ibmcloud.com/dashboard/#/overview
    ```

    Dabei ist *Organisations-ID* die ID Ihrer {{site.data.keyword.iot_short_notm}}-Organisation.

2. Wählen Sie im Dashboard 'Überblick' im Menüteilfenster die Option **Geräte** aus und klicken Sie anschließend auf **Gerät hinzufügen**.

3. Erstellen Sie einen Gerätetyp für das Gerät, das Sie hinzufügen.

    Jedem Gerät, das mit {{site.data.keyword.iot_short_notm}} verbunden ist, muss ein Gerätetyp zugeordnet sein. Gerätetypen sind Gruppen von Geräten, denen allgemeine Merkmale gemeinsam sind.

    1. Klicken Sie auf **Gerätetyp erstellen**.
    2. Geben Sie einen Gerätenamen ein, z. B. `my_device_type`, sowie eine Beschreibung für den Gerätetyp.

        > **Hinweis:** Der Name des Gerätetyps darf maximal 36 Zeichen umfassen und nur alphanumerische Zeichen (a-z, A-Z, 0-9) sowie folgende Zeichen enthalten: `_`, `.` und `-`. 

    3. Optional: Geben Sie Attribute und Metadaten zu dem Gerätetyp ein.

        Sie können Attribute und Metadaten später hinzufügen und bearbeiten.
        {: tip}

4. Klicken Sie auf **Weiter**, um mit dem Hinzufügen Ihres Geräts mit dem ausgewählten Gerätetyp zu beginnen.

5. Geben Sie eine Geräte-ID ein, z. B. `my_first_device`.

    Die Geräte-ID wird zum Ermitteln des Geräts im {{site.data.keyword.iot_short_notm}}-Dashboard verwendet und ist auch ein erforderlicher Parameter für das Herstellen einer Verbindung zwischen Ihrem Gerät und {{site.data.keyword.iot_short_notm}}.

    > **Hinweis:** Der Name des Gerätetyps darf maximal 36 Zeichen umfassen und nur alphanumerische Zeichen (a-z, A-Z, 0-9) sowie folgende Zeichen enthalten: `_`, `.` und `-`. 

    Bei netzverbundenen Geräten kann die Geräte-ID beispielsweise die MAC-Adresse des Geräts ohne trennende Doppelpunkte sein.

5. Klicken Sie auf **Weiter**, um den Prozess abzuschließen.

6. Stellen Sie ein Authentifizierungstoken bereit oder akzeptieren Sie ein automatisch generiertes Token. Wenn Sie ein eigenes Token erstellen möchten, achten Sie darauf, dass es zwischen 8 und 36 Zeichen lang ist und nur aus alphanumerischen Zeichen und den folgenden Zeichen besteht: `_`, `.`, `!`, `&`, `@`, `?`, `\*`, `+`, `(`, `)` und `-`. 

    Das Token darf keine Folgen aus wiederholten Zeichen, Wörterbuchwörter, Benutzernamen oder andere vordefinierte Folgen enthalten.

7. Überprüfen Sie die Übersichtsinformationen auf ihre Richtigkeit und klicken Sie anschließend auf **Hinzufügen**, um die Verbindung hinzuzufügen.

8. Kopieren Sie auf der Seite mit den Geräteinformationen die folgenden Einzelangaben und speichern Sie sie:

    * Organisations-ID
    * Gerätetyp
    * Geräte-ID
    * Authentifizierungsmethode
    * Authentifizierungstoken

    Sie benötigen die Organisations-ID, den Gerätetyp, die Geräte-ID und das Authentifizierungstoken, um das Gerät für die Verbindung zu {{site.data.keyword.iot_short_notm}} zu konfigurieren. 

## Schritt 2: Gerät mit {{site.data.keyword.iot_short_notm}} verbinden
{: #step2 .sectiontitle}  

Nach dem Registrieren eines Geräts in {{site.data.keyword.iot_short_notm}}, können Sie die Registrierungsinformationen verwenden, um das Gerät zu verbinden und mit dem Empfang von Gerätedaten zu beginnen.

**Tipp:** Verbindungsanleitungen für einige gängige Geräte sind in [Verbindungsanleitungen für Geräte ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://developer.ibm.com/recipes/tutorials/category/internet-of-things-iot/){: new_window} in {{site.data.keyword.IBM_notm}}.com verfügbar. 

Gehen Sie wie folgt vor, um ein Gerät mit {{site.data.keyword.iot_short_notm}} zu verbinden: 
1. Richten Sie das Gerät für die MQTT-Nachrichtenübertragung ein und verwenden Sie zur Authentifizierung die Organisations-ID, den Gerätetyp, die Geräte-ID und das Authentifizierungstoken. 

2. Senden Sie mithilfe des MQTT-Protokolls Gerätenachrichten an Ihre {{site.data.keyword.iot_short_notm}}-Organisation.

    Folgende Informationen sind zum Verbinden Ihrer Geräte erforderlich:

    * URL: *Organisations-ID*.messaging.internetofthings.ibmcloud.com

      Dabei ist *Organisations-ID* die ID Ihrer {{site.data.keyword.iot_short_notm}}-Organisation.

    * Port:
      * 1883
      * 8883 (verschlüsselt)
      * 443 (Websockets)
    * Geräte-ID: d:_org_id:device_type:device_id_
    * Benutzername: use-token-auth
    * Kennwort: _Authentication token_
    * Format des Ereignistopics: iot-2/evt/_event_id/fmt/format_string_

      Hierbei gibt _event_id_ den Ereignisnamen an, der in {{site.data.keyword.iot_short_notm}} angezeigt wird, und _format_string_ das Format des Ereignisses, z. B. JSON.

    * Nachrichtenformat: JSON

  Weitere Informationen finden Sie in [MQTT-Konnektivität für Geräte ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/devices/mqtt.html){:new_window}. 


## Weitere Schritte  
{: #related .sectiontitle}

Erweitern Sie die Datenanalysefeatures, indem Sie eigene Apps erstellen und verbinden, um Gerätedaten zu verarbeiten. 
- Weitere Informationen zur Vorgehensweise beim Verbinden bestimmter Gerätetypen mit {{site.data.keyword.iot_short_notm}} finden Sie in [developerWorks-Anleitungen ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://developer.ibm.com/recipes/tutorials/category/internet-of-things-iot/){:new_window}.
- In den [Clientbibliotheken ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/iot_platform_client_lib.html){:new_window} stehen Tools zur Verfügung, mit denen Sie Code für das Integrieren und Verbinden Ihrer Geräte und Apps erstellen können. 
- Lesen Sie die [{{site.data.keyword.iot_short_notm}}-API-Dokumentation](/docs/IoT/reference/api.html). 
- [Stellen Sie eine Verbindung von einem {{site.data.keyword.cloudantfull}}-Service ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/cloudant_connector.html){:new_window} zu Ihrer {{site.data.keyword.iot_short_notm}}-Instanz her, um Langzeitdaten für Geräte zu speichern. 
- Wenn Sie das vollständige [{{site.data.keyword.iot_short_notm}}-Feature-Set ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html){:new_window} nutzen möchten, können Sie einen der Verbindungs- und Analyseservicepläne kaufen und dann die vorhandene Umgebung migrieren. 

Wenn Sie Pläne migrieren möchten, wenden Sie sich an den {{site.data.keyword.IBM}} Ansprechpartner oder öffnen Sie ein Support-Ticket. 

Eine Reihe detaillierterer Einführungen und Beispielanwendungen, die Sie durch die Grundlagen der Entwicklung eines produktionsbereiten End-to-End-IoT-Prototypsystems mit {{site.data.keyword.iot_short_notm}} führt, ist ebenfalls in der {{site.data.keyword.iot_short_notm}}-Produktdokumentation im {{site.data.keyword.IBM_notm}} Knowledge Center verfügbar. Wenn Sie ein Entwickler sind, der zum ersten Mal mit {{site.data.keyword.iot_short_notm}} arbeitet, verwenden Sie die in einzelne Arbeitsschritte aufgegliederten Prozesse im Abschnitt mit den [einführenden Anleitungen ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/getting_started/getting-started-iot-overview.html#getting-started){:new_window}. 
