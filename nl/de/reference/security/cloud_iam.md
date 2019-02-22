---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-13"

---

{:new_window: target="\_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:important: .important}


# Authentifizierung und Berechtigung mit {{site.data.keyword.iamshort}} für {{site.data.keyword.iot_short_notm}} (Beta)
{: #cloud_iam}

<p>Diese {{site.data.keyword.Bluemix}}-Dokumentationssammlung bezieht sich auf den Lite-Preisstrukturplan von {{site.data.keyword.iot_full}} und enthält grundlegende Informationen zum Einstieg, API-Referenzinformationen und allgemeine Informationen zur Fehlerbehebung.
Die vollständige Dokumentation zum {{site.data.keyword.iot_short_notm}}-Feature finden Sie in der [{{site.data.keyword.iot_short_notm}}-Produktdokumentation![Symbol für externen Link](../../../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html) im {{site.data.keyword.IBM_notm}} Knowledge Center. Weitere Informationen zu den verschiedenen Plänen finden Sie in [{{site.data.keyword.iot_short_notm}}-Servicepläne](/docs/IoT/plans_overview.html#plans_overview).
</p>
{: important}

{{site.data.keyword.iot_full}}-APIs unterstützen die Authentifizierung und Berechtigung von Benutzern mithilfe von {{site.data.keyword.iamshort}} (IAM). 

Die Authentifizierung und Berechtigung mit {{site.data.keyword.iamlong}} für {{site.data.keyword.iot_short_notm}} ist nur im Rahmen eines eingeschränkten Betaprogramms verfügbar. Zukünftige Aktualisierungen enthalten möglicherweise Änderungen, die mit der aktuellen Version dieses Features nicht kompatibel sind. Starten Sie einen Versuch und [senden Sie uns Ihren Erfahrungsbericht ![Symbol für externen Link](../../../../icons/launch-glyph.svg)](https://developer.ibm.com/answers/smart-spaces/17/internet-of-things.html){: new_window}.
{: important}

{{site.data.keyword.iamshort}} ist in {{site.data.keyword.Bluemix_notm}} integriert und wird für die Authentifizierung und Berechtigung von Administratoren und Entwicklern verwendet, die {{site.data.keyword.IBM_notm}}-Services konfigurieren und verwalten. Benutzer, die Zugriff auf das {{site.data.keyword.iot_short_notm}}-Dashboard benötigen, werden mit {{site.data.keyword.iamshort}} authentifiziert. Bei der Identitätsquelle für {{site.data.keyword.iamshort}} kann es sich um registrierte IBMid-Benutzer handeln oder um den Verzeichnisservice eines Kunden, der SAML unterstützt.   

{{site.data.keyword.iot_short_notm}} unterstützt auch die Authentifizierung von Benutzern über {{site.data.keyword.appid_short_notm}}. Mit {{site.data.keyword.appid_short_notm}} können Benutzer authentifiziert werden, die Zugriff auf Anwendungen benötigen, die in der {{site.data.keyword.Bluemix_notm}} gehostet werden. {{site.data.keyword.appid_short_notm}}-Benutzer führen normalerweise keine Administrator- oder Entwickleraktivitäten für einen Cloud-Service aus. Weitere Informationen finden Sie in [Authentifizierung mit {{site.data.keyword.appid_short_notm}} für Watson IoT Platform ![Symbol für externen Link](../../../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/app_id.html#app_id){: new_window}. 

Mit IAM können Benutzer ein IAM-OAuth-Token anfordern und für die Authentifizierung von API-Aufrufen verwenden. Ein Benutzer mit installierter {{site.data.keyword.containershort_notm}}-CLI kann beispielsweise den folgenden Befehl verwenden:

`bx iam oauth-tokens`

Der Befehl gibt das IAM-Token des angemeldeten Benutzers im folgenden Format zurück:

`IAM Token: Bearer <some token>`

Ein Benutzer kann auch den IAM-Tokenendpunkt verwenden, um sich anzumelden und sein IAM-Token abzurufen, wie im folgenden Beispiel gezeigt:
`curl -s 'https://iam.bluemix.net/oidc/token?grant_type=urn:ibm:params:oauth:grant-type:apikey&response_type=cloud_iam&apikey=<apikey>' -H'Content-Type:x-www-form-urlencoded' -XPOST`

In diesem API-Beispiel wird ein IAM-API-Schlüssel verwendet, um das IAM-Token anzufordern, und das Trägertoken (`Bearer <token>`) wird zurückgegeben. 

Wenn dann ein Benutzer eine {{site.data.keyword.iot_short_notm}}-API aufruft, kann er den Berechtigungsheader `Authorization: Bearer <token>` in den API-Aufrufen angeben. 

## IAM-Token generieren
{: #iam_generate}

Sie können auswählen, wie die Erstellung des IAM-Tokens automatisiert werden soll. Dies ist abhängig von Ihrer Authentifizierung bei {{site.data.keyword.Bluemix_notm}} und dem Typ der {{site.data.keyword.Bluemix_notm}}-ID, die Sie verwenden. 

Wenn Sie eine nicht föderierte ID verwenden, können Sie eine der folgenden Optionen für die Erstellung eines IAM-Tokens auswählen:
 - **{{site.data.keyword.Bluemix_notm}}-Benutzername und Kennwort:** Sie können ein Token erstellen, mit dem die Erstellung des IAM-Zugriffstokens vollständig automatisiert wird. 
 - **{{site.data.keyword.Bluemix_notm}}-API-Schlüssel generieren:** Sie können {{site.data.keyword.Bluemix_notm}}-API-Schlüssel verwenden, die vom {{site.data.keyword.Bluemix_notm}}-Konto abhängig sind, für das sie generiert werden. Es ist nicht möglich, Ihren {{site.data.keyword.Bluemix_notm}}-API-Schlüssel mit einer anderen Konto-ID im selben IAM-Token zu kombinieren. Für den Zugriff auf Cluster, die mit einem Konto erstellt wurden, bei dem es sich nicht um das Konto handelt, auf dem der {{site.data.keyword.Bluemix_notm}}-API-Schlüssel basiert, müssen Sie sich bei dem entsprechenden Konto anmelden und einen neuen API-Schlüssel generieren. 

Wenn Sie eine föderierte ID verwenden, können Sie eine der folgenden Optionen für die Erstellung eines IAM-Tokens auswählen:
 - **{{site.data.keyword.Bluemix_notm}}-API-Schlüssel generieren:** {{site.data.keyword.Bluemix_notm}}-API-Schlüssel sind abhängig von dem {{site.data.keyword.Bluemix_notm}}-Konto, für das sie generiert wurden. Es ist nicht möglich, Ihren {{site.data.keyword.Bluemix_notm}}-API-Schlüssel mit einer anderen Konto-ID im selben IAM-Token zu kombinieren. Für den Zugriff auf Cluster, die mit einem Konto erstellt wurden, bei dem es sich nicht um das Konto handelt, auf dem der {{site.data.keyword.Bluemix_notm}}-API-Schlüssel basiert, müssen Sie sich bei dem entsprechenden Konto anmelden und einen neuen API-Schlüssel generieren. 
 - **Einmaligen Kenncode verwenden:** Wenn Sie für die Authentifizierung bei {{site.data.keyword.Bluemix_notm}} einen einmaligen Kenncode verwenden, kann die Erstellung des IAM-Tokens nicht vollständig automatisiert werden, da für das Abrufen des einmaligen Kenncodes eine manuelle Interaktion mit Ihrem Web-Browser erforderlich ist. Wenn Sie die Erstellung des IAM-Tokens vollständig automatisieren möchten, müssen Sie stattdessen einen {{site.data.keyword.Bluemix_notm}}-API-Schlüssel erstellen. 

Bei der Erstellung des Zugriffstokens variieren die Hauptteilinformationen der Anforderung abhängig von der verwendeten {{site.data.keyword.Bluemix_notm}}-Authentifizierungsmethode. Ersetzen Sie die folgenden Werte: 
- `<my_username>` = Ihr {{site.data.keyword.Bluemix_notm}}-Benutzername. 
- `<my_password>` = Ihr {{site.data.keyword.Bluemix_notm}}-Kennwort. 
- `<my_api_key>` = Ihr {{site.data.keyword.Bluemix_notm}}-API-Schlüssel. 
- `<my_passcode>` = Ihr einmaliger {{site.data.keyword.Bluemix_notm}}-Kenncode. Führen Sie den Befehl `bx login --sso` aus und befolgen Sie die Anweisungen in der CLI-Ausgabe, um Ihren einmaligen Kenncode über den Web-Browser abzurufen.

Beispiel:
`POST https://iam.<region>.bluemix.net/oidc/token`

Verwenden Sie für die Angabe einer {{site.data.keyword.Bluemix_notm}}-Region die Regionsabkürzungen in den API-Endpunkten. Weitere Informationen finden Sie in [API-Endpunkte für {{site.data.keyword.Bluemix_notm}}-Regionen ![Symbol für externen Link](../../../../icons/launch-glyph.svg)](https://console.bluemix.net/docs/containers/cs_regions.html#bluemix_regions){: new_window}. 

Eingabeparameter | Werte
---------------- | -----------
Header	| Content-Type:application/x-www-form-urlencoded<br>Berechtigung: Basic Xng7Png=<br>Hinweis: Sie erhalten `Xng7Png=`, die URL-codierte Berechtigung für den Benutzernamen bx und das Kennwort bx. 
Hauptteil für {{site.data.keyword.Bluemix_notm}}-Benutzernamen und -Kennwort |	grant_type: password<br>response_type: cloud_iam, uaa<br>username: `<my_username>`<br>password: `<my_password>`<br>uaa_client_id: cf<br>uaa_client_secret:<br>Hinweis: Fügen Sie den Schlüssel 'uaa_client_secret' hinzu, ohne dass ein Wert angegeben ist.
Hauptteil für {{site.data.keyword.Bluemix_notm}}-API-Schlüssel |	grant_type: urn:ibm:params:oauth:grant-type:apikey<br>response_type: cloud_iam<br>uaa<br>apikey: `<my_api_key>`<br>uaa_client_id: cf<br>uaa_client_secret:<br>Hinweis: Fügen Sie den Schlüssel 'uaa_client_secret' hinzu, ohne dass ein Wert angegeben ist.
Hauptteil für einmaligen {{site.data.keyword.Bluemix_notm}}-Kenncode |	grant_type: urn:ibm:params:oauth:grant-type:passcode<br>response_type: cloud_iam, uaa<br>passcode: `<my_passcode>`<br>uaa_client_id: cf<br>uaa_client_secret:<br>Hinweis: Fügen Sie den Schlüssel 'uaa_client_secret' hinzu, ohne dass ein Wert angegeben ist.

Beispiel für API-Ausgabe:

```
{
"access_token": "<iam-token>",
"refresh_token": "<iam-aktualisierungstoken>",
"uaa_token": "<uaa-token>",
"uaa_refresh_token": "<uaa-aktualisierungstoken>",
"token_type": "Bearer",
"expires_in": 3600,
"expiration": 1493747503
}
```
Sie finden das IAM-Token im Feld **access_token** der API-Ausgabe.

Das folgende Beispiel zeigt, wie das IAM-Token beim Aufrufen von APIs verwendet wird.

```
GET https://org.domain/api/v0002/bulk/devices
```

Eingabeparameter |	Werte
----------------- | -----------
Header	|	Content-Type: application/json<br>Authorization: bearer `<iam_token>`
