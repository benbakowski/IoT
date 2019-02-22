---

copyright:
  years: 2016, 2019
lastupdated: "2019-02-13"

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:important: .important}

# Benutzerzugriff verwalten
{: #managing-user-access}

<p>Diese {{site.data.keyword.Bluemix}}-Dokumentationssammlung bezieht sich auf den Lite-Preisstrukturplan von {{site.data.keyword.iot_full}} und enthält grundlegende Informationen zum Einstieg, API-Referenzinformationen und allgemeine Informationen zur Fehlerbehebung.
Die vollständige Dokumentation zum {{site.data.keyword.iot_short_notm}}-Feature finden Sie in der [{{site.data.keyword.iot_short_notm}}-Produktdokumentation![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html) im IBM Knowledge Center. Weitere Informationen zu den verschiedenen Plänen finden Sie in [{{site.data.keyword.iot_short_notm}}-Servicepläne](/docs/IoT/plans_overview.html#plans_overview).
</p>
{: important}

Auf der Seite 'Mitglieder' des Dashboards können Sie den Zugriff auf die {{site.data.keyword.iot_full}}-Organisation steuern und verwalten. Sie können Benutzer hinzufügen, indem Sie sie hinzufügen, einladen oder importieren. Durch die Zuweisung von Rollen können Sie Ihren Benutzern unterschiedliche Zugriffsebenen zuordnen.
{:shortdesc}

## Benutzer hinzufügen
{: #adding-new-users}

Auf der Seite **Mitglieder** des Dashboards können Sie einzelne Mitglieder mithilfe der Funktion 'Hinzufügen' hinzufügen. Darüber hinaus ist es möglich, Mitglieder gleichzeitig mithilfe der Funktion 'Importieren' hinzuzufügen.

Mitgliederkonten haben standardmäßig kein Ablaufdatum. Wenn Sie Ihrer {{site.data.keyword.iot_short_notm}}-Organisation Mitglieder hinzufügen, können Sie für deren Konto optional ein Ablaufdatum festlegen.

### Mitglieder zur {{site.data.keyword.iot_short_notm}}-Organisation hinzufügen

Zum Hinzufügen von Mitgliedern zu Ihrer Organisation benötigen Sie die IBM ID des Mitglieds. Eine Bestätigung des Mitglieds benötigen Sie zum Hinzufügen des Mitglieds nicht.

Gehen Sie wie folgt vor, um Ihrer {{site.data.keyword.iot_short_notm}}-Organisation ein einzelnes Mitglied hinzuzufügen:
1. Klicken Sie in Ihrem {{site.data.keyword.iot_short_notm}}-Dashboard in der Navigationsleiste auf **Mitglieder**. 
2. Klicken Sie auf **Mitglieder hinzufügen** und wählen Sie die Registerkarte **Hinzufügen** aus.
3. Geben Sie die IBM ID des Mitglieds ein.
4. Wählen Sie eine Rolle für das Mitglied aus.
5. Optional: Legen Sie ein Ablaufdatum fest. 
6. Klicken Sie auf **Hinzufügen**.

Zum gleichzeitigen Hinzufügen mehrerer Mitglieder müssen Sie eine CSV-Datei (`.csv`) hochladen, die für jedes Mitglied die IBM ID, die Rolle und das optionale Ablaufdatum enthält. Informationen finden Sie in [CSV-Datei erstellen](#constructing-your-csv).
1. Klicken Sie in Ihrem {{site.data.keyword.iot_short_notm}}-Dashboard in der Navigationsleiste auf **Mitglieder**. 
2. Klicken Sie auf **Mitglieder hinzufügen** und wählen Sie die Registerkarte **Importieren** aus.
3. Durchsuchen Sie Ihre Dateien oder ziehen Sie die CSV-Datei (`.csv`) in das Fenster **CSV-Upload**.
4. Wählen Sie eine Standardrolle aus, die verwendet werden soll, wenn eine in der CSV-Datei angegebene Rolle nicht erkannt wird.
5. Ordnen Sie die Spaltennummern in Ihrer CSV-Datei der entsprechenden Einträgen für die IBMid, die Rolle und ein optionales Ablaufdatum zu.
6. Wählen Sie das passende Komma- oder Semikolonspaltentrennzeichen aus, das mit dem Trennzeichen in Ihrer CSV-Datei (`.csv`) übereinstimmt.
7. Klicken Sie auf **Importieren**, um die IBMids zu importieren, und erstellen Sie die Mitglieder.


### CSV-Datei erstellen
{: #constructing-your-csv}

Beim Erstellen einer CSV-Datei für den Import von Mitgliedern in Ihre Organisation müssen Sie sicherstellen, dass Sie für die von Ihnen verwendete Methode die erforderlichen Informationen einschließen. Verwenden Sie zum Trennen von Spalten entweder Kommas oder Semikola.  
**Wichtig:** Stellen Sie beim Hochladen der CSV-Datei sicher, dass Sie unter **CSV-Einstellungen** das richtige Spaltentrennzeichen auswählen.

CSV-Beispieldatei mit Kommatrennzeichen:  
```
user1@sample.com,PD_DEVELOPER_USER,2018-03-13
user2@sample.com,PD_OPERATOR_USER,2018-03-13
user3@sample.com,PD_ADMIN_USER,2018-03-13
```
Wo die folgenden Spalteneinträge verwendet werden:  
- Spalte 1: Die E-Mail-Adresse des Benutzers.  
Wenn Sie Mitglieder hinzufügen, stellen Sie sicher, dass die verwendeten E-Mail-Adressen gültigen IBMids entsprechen. Wenn Sie Mitglieder einladen, können Sie alle gültigen E-Mail-Adressen verwenden. 
- Spalte 2: Die Rolle, die dem Benutzer zugewiesen wird.  
Geben Sie eine der folgenden Rollen ein:
 - PD_ADMIN_USER
 - PD_OPERATOR_USER
 - PD_DEVELOPER_USER
 - PD_ANALYST_USER
 - PD_READER_USER  
 Weitere Informationen zu Benutzerrollen finden Sie in [Benutzer-, Anwendungs- und Gateway-Rollen ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/roles_index.html#user_roles){: new_window}. 
- Spalte 3: Datum im ISO 6801-Format (z. B. `2018-03-13`), das dem Benutzerablaufdatum entspricht.

## Benutzer bearbeiten
{: #editing-users}

Beim Bearbeiten eines Benutzer können Sie die Benutzerrolle ändern, ein Ablaufdatum hinzufügen, entfernen oder ändern sowie Zugriff auf eine Organisation hinzufügen oder entfernen.

1. Klicken Sie in Ihrem {{site.data.keyword.iot_short_notm}}-Dashboard in der Navigationsleiste auf **Mitglieder**. 
2. Klicken Sie auf das Symbol **Bearbeiten** neben dem Benutzer, den Sie bearbeiten möchten.
3. Nehmen Sie die gewünschten Änderungen für den Benutzer vor.
4. Klicken Sie auf **Speichern**.

## Benutzerzugriff sperren
{: #blocking-users}

Sie können den Zugriff von Benutzern auf die {{site.data.keyword.iot_short_notm}}-Organisation sperren, ohne die Zugehörigkeit zu der Organisation zu ändern.

1. Klicken Sie in Ihrem {{site.data.keyword.iot_short_notm}}-Dashboard in der Navigationsleiste auf **Mitglieder**. 
2. Klicken Sie auf den Schalter neben dem Benutzer, für den der Zugriff auf die {{site.data.keyword.iot_short_notm}}-Organisation gesperrt werden soll.

## Benutzerzugriff einschränken
{: #limiting-users}

Die Zugriffssteuerung auf Ressourcenebene ermöglicht Ihnen die Einschränkung des Zugriffs auf Geräte innerhalb einer Organisation. Sie können Ressourcengruppen verwenden, um die Geräte anzugeben, die von den einzelnen Benutzern oder API-Schlüsseln verwaltet werden können. Weitere Informationen zur Vorgehensweise bei der Konfiguration der Zugriffssteuerung auf Ressourcenebene finden Sie in [Zugriffssteuerung auf Ressourcenebene konfigurieren ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/reference/rlac.html#configure_RLAC){: new_window}. 

## Benutzer entfernen
{: #removing-users}

Sie können Benutzer vollständig aus der {{site.data.keyword.iot_short_notm}}-Organisation entfernen. Das Entfernen von Benutzern kann nicht rückgängig gemacht werden, d. h. die betreffenden Benutzer müssen erneut [zur Plattform hinzugefügt werden](#adding-new-users), um den Zugriff wiederherzustellen.

1. Klicken Sie in Ihrem {{site.data.keyword.iot_short_notm}}-Dashboard in der Navigationsleiste auf **Mitglieder**. 
2. Klicken Sie auf das Symbol **Löschen** neben dem Benutzer, der entfernt werden soll. 
3. Klicken Sie im Bestätigungsdialogfenster auf **Löschen**. 
