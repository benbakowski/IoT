---

copyright:
  years: 2016, 2019
lastupdated: "2019-04-05"

keywords: Watson IoT Platform, Watson IoT Platform organization, IoT Platform, troubleshooting

subcollection: iot-platform

---

{:new_window: target="\_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:important: .important}

# {{site.data.keyword.iot_short_notm}} - Fehlerbehebung
{: #ts}

<p>Diese {{site.data.keyword.cloud}}-Dokumentationssammlung bezieht sich auf den Lite-Preisstrukturplan von {{site.data.keyword.iot_full}} und enthält grundlegende Informationen zum Einstieg, API-Referenzinformationen und allgemeine Informationen zur Fehlerbehebung.
Die vollständige Dokumentation zum {{site.data.keyword.iot_short_notm}}-Feature finden Sie in der [{{site.data.keyword.iot_short_notm}}-Produktdokumentation![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html) im IBM Knowledge Center. Weitere Informationen zu den verschiedenen Plänen finden Sie in [{{site.data.keyword.iot_short_notm}}-Servicepläne](/docs/services/IoT?topic=iot-platform-plans_overview#plans_overview).
</p>
{: important}

Hier finden Sie Antworten auf allgemeine Fragen zur Fehlerbehebung bei der Verwendung von {{site.data.keyword.iot_full}} in {{site.data.keyword.cloud_notm}}.
{:shortdesc}

## Fehler beim Zugriff auf Ihre {{site.data.keyword.iot_short_notm}}-Organisation
{: #access-expiry-problem}

Sie können sich bei einer {{site.data.keyword.iot_short_notm}}-Organisation nicht anmelden, deren Eigner Sie sind.
{:shortdesc}

Sie können sich bei Ihrer {{site.data.keyword.iot_short_notm}}-Organisation weder mit der URL der Organisation noch über die Webadresse `https://internetofthings.ibmcloud.com` direkt anmelden.
{: tsSymptoms}

Die Zugriffsberechtigung für Ihre {{site.data.keyword.iot_short_notm}}-Organisation ist möglicherweise abgelaufen. Für {{site.data.keyword.iot_short_notm}}-Organisationen, die unter Verwendung von {{site.data.keyword.cloud}} erstellt wurden, werden standardmäßig temporäre Benutzerprofile verwendet.
{: tsCauses}

Zur Behebung dieses Problem können Sie über {{site.data.keyword.cloud_notm}} auf Ihre {{site.data.keyword.iot_short_notm}}-Organisation zugreifen und die Ablaufeinstellungen für Ihr Benutzerprofil ändern. Gehen Sie wie folgt vor, um die Ablaufeinstellungen für Ihr Benutzerprofil zu ändern:

1. Öffnen Sie in Ihrem {{site.data.keyword.cloud_notm}}-Dashboard Ihren {{site.data.keyword.iot_short_notm}}-Service.
2. Klicken Sie in der Navigationsleiste auf **Mitglieder**.
3. Klicken Sie auf das Bearbeitungssymbol****.
4. Löschen Sie den Inhalt des Kontrollkästchens **Zugriff läuft ab** und klicken Sie auf **Speichern**.
{: tsResolve}

## Problem beim Herstellen einer Verbindung zu {{site.data.keyword.iot_short_notm}}
{: #connection_problem}

Ihre Verbindung zu {{site.data.keyword.iot_short_notm}} wird unerwartet gelöscht oder unterbrochen.
{:shortdesc}

Wenn Sie versuchen, eine Verbindung zu {{site.data.keyword.iot_short_notm}} herzustellen, empfängt Ihr Gerät oder Ihre Anwendung einen Fehler.
{: tsSymptoms}

Möglicherweise versuchen mehrere Geräte, eine Verbindung mit derselben Client-ID und denselben Berechtigungsnachweisen herzustellen. Pro Client-ID ist nur eine einzige eindeutige Verbindung zulässig. Mehrere gleichzeitige Verbindungen, die dieselbe ID verwenden, sind nicht möglich. Anwendungen können denselben API-Schlüssel gemeinsam nutzen; MQTT erfordert jedoch, dass die Client-ID jeweils eindeutig ist.
{: tsCauses}

Sie können diese Ursache ausschließen, indem Sie sicherstellen, dass Sie nicht über mehrere Geräte verfügen, die versuchen, mit denselben Berechtigungsnachweisen eine Verbindung herzustellen.
{: tsResolve}

## Sporadisches Auftreten einer Unterbrechung der Verbindung des Geräts zu {{site.data.keyword.iot_short_notm}}
{: #disconnection_problem}

Sporadisches Auftreten einer Löschung der Geräteverbindung zu {{site.data.keyword.iot_short_notm}}
{:shortdesc}

Es tritt sporadisch auf, dass die Verbindung für ein mit dem {{site.data.keyword.iot_short_notm}}-Service verbundenes Gerät unterbrochen wird. Das Gerät stellt die Verbindung wieder her, aber die Verbindung wird nach einem kurzen Zeitraum wieder unterbrochen.
{: tsSymptoms}

Möglicherweise verwenden Sie beim Herstellen einer Verbindung einen zu niedrigen Wert für eine MQTT-Ping-Option, wodurch es so aussieht, als habe die Verbindung das Zeitlimit überschritten. Wenn das Client-MQTT falsch festgelegt wurde, werden Pingsignale nicht zeitnah empfangen und die Verbindung wird geschlossen.
{: tsCauses}

Sie können dieses Problem beheben, indem Sie bestätigen, dass Sie die Parameter für Ping und Keepalive für Ihre Verbindung richtig festgelegt haben.   
{: tsResolve}
