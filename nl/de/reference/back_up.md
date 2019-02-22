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



# Datensicherung
{: #back_up}

<p>Diese {{site.data.keyword.Bluemix}}-Dokumentationssammlung bezieht sich auf den Lite-Preisstrukturplan von {{site.data.keyword.iot_full}} und enthält grundlegende Informationen zum Einstieg, API-Referenzinformationen und allgemeine Informationen zur Fehlerbehebung.
Die vollständige Dokumentation zum {{site.data.keyword.iot_short_notm}}-Feature finden Sie in der [{{site.data.keyword.iot_short_notm}}-Produktdokumentation![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html) im IBM Knowledge Center. Weitere Informationen zu den verschiedenen Plänen finden Sie in [{{site.data.keyword.iot_short_notm}}-Servicepläne](/docs/IoT/plans_overview.html#plans_overview).
</p>
{: important}

Verwenden Sie die folgenden Informationen, um sich mit der Datensicherungsstrategie für {{site.data.keyword.iot_full}} vertraut zu machen.

## Welche Datentypen werden gesichert?

Momentan werden im Rahmen der {{site.data.keyword.iot_short_notm}}-Strategie die folgenden Typen von Clientdaten gesichert:

- Informationen zur Organisation
- Gerätedaten
- API-Schlüssel und Tokens
- Benutzerdaten
- Alle Datensätze von Gerätemanagementanforderungen einschließlich des Protokolls der initialisierten Anforderungen, z. B. der aktuelle Status der Anforderung
- Definitionen von Anforderungsbundles für das angepasste Gerätemanagement

**Hinweis:** Alle Daten für eine Organisation werden 14 Tage lang nach der Servicebereitstellung aufbewahrt. Um eine Organisation wiederherzustellen, wenden Sie sich innerhalb des 14-Tage-Fensters an den Support.

## Welche Datentypen werden nicht gesichert?

Die folgenden Datentypen werden in {{site.data.keyword.iot_short_notm}} nicht gesichert:

- Geräteereignisse
- Daten zum transienten Nachrichtenstatus, z. B. für momentan ausgeführte Daten
- MQTT-Nachrichten, die im Rahmen einer Gerätemanagementanforderung gesendet und empfangen werden
<!-- - Analytics rules and alert configuration -->

## Wie häufig werden Daten gesichert und wo werden sie gespeichert?

Daten werden alle 24 Stunden gesichert.

Die Daten werden getrennt vom {{site.data.keyword.iot_short_notm}}-Hauptservice an einem anderen Standort gespeichert. Dadurch besteht eine geografische Redundanz und die Services können wiederhergestellt werden, wenn es zu einem größeren Störfall kommt. Die betroffenen Kunden werden kontaktiert, wenn eine Datenwiederherstellung erforderlich wird. Alle Daten werden verschlüsselt und ihre Behandlung entspricht den lokalen Datenschutzanforderungen.

Momentan werden die folgenden Auslagerungsstandorte für die Datensicherung verwendet:

Standort                   | Sicherungsstandort                      
------------- | -------------
IBM Cloud - Vereinigte Staaten (Süden) (Dallas)| Washington
IBM Cloud - Großbritannien (London) | Frankfurt
IBM Cloud - Deutschland (Frankfurt) | London
IBM Cloud Dedicated | Auf Basis der Kundenanforderung bei Bestellung von {{site.data.keyword.iot_short_notm}} Dedicated

**Hinweis:** Zukünftige Standorte können sich ändern, um den Gesetzen zum Datenschutz Rechnung zu tragen, z. B. in Bezug auf die möglichen Auswirkungen des Brexit auf die Regelungen der EU-Datensouveränität.
