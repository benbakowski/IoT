---

copyright:
  years: 2017, 2019
lastupdated: "2019-02-13"
---

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

<p>Diese {{site.data.keyword.Bluemix}}-Dokumentationssammlung bezieht sich auf den Lite-Preisstrukturplan von {{site.data.keyword.iot_full}} und enthält grundlegende Informationen zum Einstieg, API-Referenzinformationen und allgemeine Informationen zur Fehlerbehebung.
Die vollständige Dokumentation zum {{site.data.keyword.iot_short_notm}}-Feature finden Sie in der [{{site.data.keyword.iot_short_notm}}-Produktdokumentation![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html) im IBM Knowledge Center. Weitere Informationen zu den verschiedenen Plänen finden Sie in [{{site.data.keyword.iot_short_notm}}-Servicepläne](/docs/IoT/plans_overview.html#plans_overview).
</p>
{: important}

Mithilfe des {{site.data.keyword.iot_full}}-Gerätesimulators können Sie simulierte Ereignisse für Geräte einrichten. Sie können die Daten für simulierte Ereignisse verwenden, um mit allen Funktionen versehene {{site.data.keyword.iot_short_notm}}-Komponenten zu untersuchen, zu testen und vorzuführen.
{: shortdesc}

Sie können vorhandene Gerätetypen und Geräte verwenden. Der Simulator ermöglicht Ihnen das Generieren neuer Geräte für vorhandene Typen. Sie können die Ereignisdetails für jedes Gerät konfigurieren oder eine Standardkonfiguration einrichten, die auf alle Geräte angewendet wird. Sie können eine Konfiguration für simulierte Ereignisse exportieren, sodass sie wiederverwendet oder gemeinsam genutzt werden kann, um andere Simulationen einzurichten.

Gehen Sie wie folgt vor, um die Gerätedaten zu simulieren:

1. Melden Sie sich bei {{site.data.keyword.iot_short_notm}} an.
2. Wählen Sie im Hauptnavigationsbereich **Einstellungen** aus.
3. Aktivieren Sie im Abschnitt **Daten und Geräte** den Gerätesimulator. 
4. Wählen Sie im Hauptnavigationsbereich **Geräte** aus. In einer Nachricht, die in der rechten unteren Ecke angezeigt wird, ist angegeben, dass momentan keine Simulationen ausgeführt werden.
5. Klicken Sie auf die Nachricht "0 Simulationen werden ausgeführt".
6. Klicken Sie im Popup-Fenster **Simulationen** auf **Simulation erstellen**. 
7. Wählen Sie einen vorhandenen Gerätetyp aus, für den Daten simuliert werden sollen, oder erstellen Sie einen neuen Gerätetyp, indem Sie den Gerätetypnamen eingeben. 
8. Klicken Sie auf **Simulation importieren/exportieren**, um eine vorhandene Konfiguration zu verwenden, oder konfigurieren Sie die Simulationsdetails für den Gerätetyp manuell: 
   1. Klicken Sie auf **+ Neuer Ereignistyp**, um einen Ereignistyp zum Gerätetyp hinzuzufügen. 
   2. Geben Sie einen Namen für den Ereignistyp ein. 
   3. Legen Sie unter **Zeitplan** die Häufigkeit des Ereignisses fest. 
   3. Bearbeiten Sie die Ereignistypdetails im JSON-Format und speichern Sie den aktualisierten Ereignistyp.

   <p> Sie können die folgenden speziellen Variablen verwenden, wenn Sie Ereignisse konfigurieren:  
        - `range`: Diese Variable wird durch eine nach dem Zufallsprinzip bestimmte Zahl ersetzt, die zwischen den beiden angegebenen Werten liegt. Beispiel: `{"random": range(300, 100)}`  
        - `$counter`: Diese Variable wird durch die Anzahl der Geräte ersetzt, die im Simulator für den aktuellen Typ hinzugefügt werden. Beispiel: `{"total": $counter}`  
        - `increment`: Diese Variable gibt die Anfangszahl und das Inkrement an, um das diese erhöht wird. Beispiel: `{"myNumber": increment(10, 1)}`. In diesem Fall beginnt `myNumber` mit 10 und erhöht sich jedes Mal, wenn Nutzdaten gesendet werden, um 1 (also 10, 11, 12 usw.). </p>
   {: tip}

9. Wählen Sie ein registriertes Gerät für die Simulation aus oder erstellen Sie ein neues Gerät, indem Sie den Gerätenamen eingeben. 
10. Wenn Sie weitere Simulationen erstellen möchten, klicken Sie auf **Neue Simulation** und wiederholen Sie die Konfigurationsschritte für jedes Gerät, für das Sie angepasste Einstellungen anwenden möchten. Die Nachricht in der rechte unteren Ecke der Anzeige zeigt die Anzahl der aktiven Simulationen an.
11. **Optional:** Nachdem Sie Simulationen für Geräte konfiguriert haben, müssen Sie die Simulationsdetails exportieren, damit sie wiederverwendet oder gemeinsam genutzt werden können:
    1. Klicken Sie im Popup-Fenster **Simulationen** auf **Importieren/exportieren**.
    2. Wählen Sie die Registerkarte **Exportieren** aus.
    3. Kopieren Sie die Simulationsdetails in die Zwischenablage oder laden Sie sie in einer JSON-Datei herunter.
12. Suchen Sie auf der Seite **Geräte** eines der simulierten Geräte und wählen Sie die Registerkarte **Kürzliche Ereignisse** aus, um zu überprüfen, ob die simulierten Ereignisse ordnungsgemäß funktionieren.
