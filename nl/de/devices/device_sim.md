---

copyright:
  years: 2017, 2019
lastupdated: "2019-04-05"

keywords: device simulator, devices

subcollection: iot-platform

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:important: .important}


# Simulieren von Gerätedaten
{: #sim_device_data}

<p>Diese {{site.data.keyword.cloud}}-Dokumentationssammlung bezieht sich auf den Lite-Preisstrukturplan von {{site.data.keyword.iot_full}} und enthält grundlegende Informationen zum Einstieg, API-Referenzinformationen und allgemeine Informationen zur Fehlerbehebung.
Die vollständige Dokumentation zum {{site.data.keyword.iot_short_notm}}-Feature finden Sie in der [{{site.data.keyword.iot_short_notm}}-Produktdokumentation![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html) im IBM Knowledge Center. Weitere Informationen zu den verschiedenen Plänen finden Sie in [{{site.data.keyword.iot_short_notm}}-Servicepläne](/docs/services/IoT?topic=iot-platform-plans_overview#plans_overview).
</p>
{: important}

Verwenden Sie den {{site.data.keyword.iot_full}}-Gerätesimulator verwenden, um simulierte Ereignisse für Geräte zu konfigurieren, um mit allen Funktionen versehene {{site.data.keyword.iot_short_notm}}-Komponenten kennenzulernen, zu testen und vorzuführen, ohne dass Sie sich registrieren oder eine Verbindung zu realen Geräten herstellen müssen.
{: shortdesc}

Durch die Verwendung des Gerätesimulators können Sie simulierte Geräte für vorhandene Gerätetypen erstellen oder auch neue Gerätetypen und Geräte erstellen. Jedes simulierte Gerät kann eindeutige Ereignisdetails verwenden, aber Sie können auch eine Standardkonfiguration erstellen, die auf alle Geräte angewendet wird.

## Vorbereitende Schritte
{: #byb-simulation .sectiontitle}
Aktivieren Sie die Gerätesimulation für Ihre Benutzer-ID. 
1. Melden Sie sich bei {{site.data.keyword.iot_short_notm}} an.
2. Wählen Sie im Hauptnavigationsbereich **Einstellungen** aus.
3. Aktivieren Sie im Abschnitt **Daten und Geräte** den Gerätesimulator.

Wenn die Gerätesimulation für Ihre Benutzer-ID aktiviert ist, werden alle aktivierten, simulierten Geräte automatisch gestartet, wenn Sie sich beim {{site.data.keyword.iot_short_notm}}-Dashboard anmelden.

## Geräte simulieren
{: #process-simulation .sectiontitle}
Wenn er aktiviert ist, steht der Gerätesimulator auf allen Dashboardseiten zur Verfügung. In einer Nachricht, die in der rechten unteren Ecke angezeigt wird, ist angegeben, wie viele Simulationen ausgeführt werden.

**Wichtig:** Die simulierten Geräte und Gerätetypen, die Sie für Ihre Benutzer-ID definieren, stehen auch anderen Benutzern der {{site.data.keyword.iot_short_notm}}-Organisation zur Verfügung. Um aber simulierte Daten für eigene Geräte zu generieren, müssen Sie beim {{site.data.keyword.iot_short_notm}}-Dashboard in einer aktiven Benutzersitzung angemeldet sein. 

Gehen Sie wie folgt vor, um die Gerätedaten zu simulieren:
1. Klicken Sie vom {{site.data.keyword.iot_short_notm}}-Dashboard aus auf die Nachricht "0 Simulationen werden ausgeführt".
3. Klicken Sie im Konfigurationsfenster **Simulationen**, das nun angezeigt wird, auf **Simulation erstellen**.
4. Konfigurieren Sie die Simulationsdetails.  
Klicken Sie auf **Simulation importieren/exportieren**, um eine [vorhandene Konfiguration](#reuse) zu importieren, oder konfigurieren Sie die Details manuell:

   1. Wählen Sie einen vorhandenen Gerätetyp aus, für den Daten simuliert werden sollen, oder erstellen Sie einen neuen Gerätetyp, indem Sie den Gerätetypnamen eingeben.
   2. Ändern Sie den Standardnamen für den Ereignistyp. 
   3. Legen Sie unter **Zeitplan** die Häufigkeit des Ereignisses fest.
   4. Bearbeiten Sie die Ereignisnutzdaten.   
   Bearbeiten Sie das Beispiel der JSON-Nutzdaten, indem Sie Eigenschaften und die entsprechenden Werte hinzufügen, oder verwenden Sie [Funktionen](#functions), um generische Datenpunkte dynamisch hinzuzufügen.   
   Sie können auch eine [CSV-Ereignisnutzdatendatei](#csv) hochladen, um die Nutzdaten zu konfigurieren.   
   {: tip}
5. Klicken Sie auf **Neuer Ereignistyp**, um mehr Ereignistypen hinzuzufügen und für den Gerätetyp zu konfigurieren. 
5. Aktivieren Sie **Ereignisse als Protokolldaten speichern**, um später auf die Statusdaten Ihres simulierten Geräts zugreifen zu können.   
Wenn die Protokolldaten aktiviert sind, werden für die {{site.data.keyword.iot_short_notm}} [Datenverwaltung ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/GA_information_management/ga_im_definitions.html){: new_window}-Komponenten erstellt und auf den Status des simulierten Geräts kann von der zugehörigen logischen Schnittstelle aus zugegriffen werden.   
**Wichtig:** Nachdem Sie den Gerätetyp aktiviert haben, um Protokolldaten zu speichern, können Sie keinen Ereignistyp hinzufügen oder entfernen. Sie können auch keine Felder in den Ereignisnutzdaten ändern. 
5. Klicken Sie auf **Speichern**, um den Gerätetyp zu erstellen.   
Sie können nun ein oder mehrere simulierte Geräte erstellen. 
6. Klicken Sie auf **Simuliertes Gerät erstellen**, um ein Gerät zu erstellen und mit dem Senden der Daten zu beginnen.   
**Tipp:** Um mehrere Geräte zu erstellen, klicken Sie auf **1 x** und wählen die Anzahl der Geräte aus, die erstellt werden sollen.   
7. Wenn Sie weitere Simulationen erstellen möchten, klicken Sie auf **Neue Simulation** und wiederholen Sie die Konfigurationsschritte für jedes Gerät, für das Sie angepasste Einstellungen anwenden möchten.   
Die Nachricht in der rechte unteren Ecke der Anzeige zeigt die Anzahl der aktiven Simulationen an.
8. Suchen Sie auf der Seite **Geräte** eines der simulierten Geräte und wählen Sie die Registerkarte **Kürzliche Ereignisse** aus, um zu überprüfen, ob die simulierten Ereignisse ordnungsgemäß funktionieren.

Sie können [Ihre simulierten Ereigniskonfigurationen exportieren](#reuse), um sie wiederzuverwenden oder gemeinsam mit anderen zu nutzen. 

## Ereignistypfunktionen
{: #functions .sectiontitle}

Sie können eine Reihe von Sonderfunktionen verwenden, um dynamische Daten für Ihre Ereignistypen zu erstellen. 

Funktion | Verwendung | Beispiel 
:--- | :---  | :--  
`random(lower, upper)`  | Generiert eine Zufallszahl in einem angegebenen Bereich. | `{"random": random(0, 100)}`  
`$counter` | Zeigt die Anzahl der simulierten Geräte des aktuellen Typs an. | `{"total": $counter}`  
`increment(start, increment)` | Gibt den Startwert und das Inkrement für seine Erhöhung an. |`{"myNumber": increment(10, 1)}` </br> In diesem Beispiel beginnt `myNumber` bei 10 und wird jeweils um 1 erhöht, wenn Nutzdaten gesendet werden. 


## CSV-Ereignisnutzdatendatei
{: #csv .sectiontitle}

Wenn Sie kontrollierte Ereignisdaten für bestimmte Szenarien erstellen möchten, können Sie den Datenfluss in einer CSV-Eingabedatei konfigurieren. 

### Anforderungen
Die CSV-Datei muss die folgenden Anforderungen erfüllen: 
- Jeder Wert ist ein gültiges [JSON-Basiselement ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://json.org){: new_window}. Es gelten folgende Ausnahmen: 
  - string:   
  Beispiel: "Hello world"
  - number:  
  Beispiel: 0, 0.1, -22, -2.43
  - boolean:  
  'true' oder 'false'
  - null:  
  Null
  - **Nicht unterstützt:**
    - objects  
    Beispiel: {}
    - arrays  
    Beispiel: []
- Werte müssen durch Kommas begrenzt sein. 
- Zeilen müssen durch ein Zeilenvorschubzeichen (`\n`) getrennt werden.
- Die Kopfzeile muss aus genau einem Zeichenfolgewert bestehen. 


### CSV-Beispieldatei
```
"temperature", "confidence","status"
1, 0.1, "normal"
2, 0.2, "normal"
3, 0.3, "error"
4, 0.4, "normal"
```

Die erste Zeile oder "Kopfzeile" bestimmt die Eigenschaften, die in der Geräte-JSON in allen generierten Ereignisobjekten der Geräte-JSON enthalten sind.
Jede nachfolgende Zeile oder "Datenzeile" legt den Wert dieser Eigenschaften in jedem generierten Ereignisobjekt der Geräte-JSON fest. 

**Tipp:** Wenn Sie die CSV-Datei importieren, können Sie **Simulierte Daten aus Datei wiederholt abspielen** auswählen, um die Datenzeilen in der Reihenfolge zu durchlaufen und so einen fortlaufenden Datenfeed zu ezeugen. Wenn dieser Schalter nicht eingeschaltet ist, wird jede Datenzeile in CSV einmal mit der Frequenz gesendet, die durch den Zeitplan festgelegt ist. 

Die CSV-Beispieldatei führt zu Ereignisnutzdaten des folgenden Typs: 
```JSON
{
  "temperature": 1,
  "confidence": 0.1,
  "status": "normal"
}
```

## Simulation gemeinsam nutzen und wiederverwenden
{: #reuse .sectiontitle}

Sie können Ihre Simulationsdetails exportieren, um sie wiederzuverwenden oder gemeinsam mit anderen zu nutzen: 
1. Klicken Sie im Fenster **Simulationen** auf **Importieren/exportieren**.
2. Wählen Sie die Registerkarte **Exportieren** aus.
3. Kopieren Sie die Simulationsdetails in die Zwischenablage oder laden Sie sie in einer JSON-Datei herunter.
