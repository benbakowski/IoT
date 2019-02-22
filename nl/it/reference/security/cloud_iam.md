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


# Autenticazione e autorizzazione di {{site.data.keyword.iamshort}} per {{site.data.keyword.iot_short_notm}} (Beta)
{: #cloud_iam}

<p>Questa raccolta di documentazione {{site.data.keyword.Bluemix}} è relativa al piano dei prezzi {{site.data.keyword.iot_full}} Lite e include le informazioni introduttive di base, le guide di riferimento API e delle informazioni generali per la risoluzione dei problemi.
Per la documentazione completa della funzione {{site.data.keyword.iot_short_notm}}, vedi la [documentazione del prodotto {{site.data.keyword.iot_short_notm}} ![Icona link esterno](../../../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html) nell'{{site.data.keyword.IBM_notm}} Knowledge Center. Ulteriori informazioni sui vari piani sono disponibili in [Piani di servizio {{site.data.keyword.iot_short_notm}}](/docs/IoT/plans_overview.html#plans_overview). 
</p>
{: important}

Le API {{site.data.keyword.iot_full}} supportano l'autenticazione e l'autorizzazione degli utenti utilizzando IAM ({{site.data.keyword.iamshort}}).

L'autenticazione e l'autorizzazione di {{site.data.keyword.iamlong}} per {{site.data.keyword.iot_short_notm}} è disponibile solo come parte di un programma beta limitato. Futuri aggiornamenti possono includere modifiche incompatibili con la versione corrente di questa funzione. Provala e [facci sapere cosa ne pensi ![Icona link esterno](../../../../icons/launch-glyph.svg)](https://developer.ibm.com/answers/smart-spaces/17/internet-of-things.html){: new_window}.
{: important}

{{site.data.keyword.iamshort}} è integrato in {{site.data.keyword.Bluemix_notm}} e viene utilizzato per autenticare e autorizzare gli utenti amministrativi e sviluppatori che devono configurare e gestire i loro servizi {{site.data.keyword.IBM_notm}}. Gli utenti che hanno bisogno di accedere al dashboard {{site.data.keyword.iot_short_notm}} sono autenticati utilizzando {{site.data.keyword.iamshort}}. L'origine dell'identità per {{site.data.keyword.iamshort}} può essere un utente con ID IBM registrato o un servizio di directory del cliente che supporta SAML.  

{{site.data.keyword.iot_short_notm}} supporta anche l'autenticazione degli utenti tramite {{site.data.keyword.appid_short_notm}}. {{site.data.keyword.appid_short_notm}} viene utilizzato per autenticare gli utenti che hanno bisogno di accedere alle applicazioni ospitate in {{site.data.keyword.Bluemix_notm}}. Gli utenti di {{site.data.keyword.appid_short_notm}} in genere non eseguono attività amministrative o di sviluppo su un servizio cloud. Per ulteriori informazioni, vedi [{{site.data.keyword.appid_short_notm}} Authentication for Watson IoT Platform ![Icona link esterno](../../../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/app_id.html#app_id){: new_window}.

IAM consente agli utenti di ottenere un token IAM OAuth e di utilizzarlo per autenticare le chiamate API. Ad esempio, un utente che ha installato la CLI {{site.data.keyword.containershort_notm}} potrebbe utilizzare il seguente comando:

`bx iam oauth-tokens`

Il comando restituisce il token IAM dell'utente collegato nel seguente formato:

`IAM Token: Bearer <some token>`

Un utente può anche utilizzare l'endpoint del token IAM per effettuare l'accesso e richiamare il token IAM, come mostrato nel seguente esempio:
`curl -s 'https://iam.bluemix.net/oidc/token?grant_type=urn:ibm:params:oauth:grant-type:apikey&response_type=cloud_iam&apikey=<apikey>' -H'Content-Type:x-www-form-urlencoded' -XPOST`

Questo esempio di API utilizza una chiave API IAM per richiedere il token IAM e restituisce il `Bearer <token>`.

Quindi, quando un utente chiama un'API {{site.data.keyword.iot_short_notm}}, può fornire l'intestazione di autorizzazione `Authorization: Bearer <token>` nelle sue chiamate API.

## Generazione di un token IAM
{: #iam_generate}

Puoi scegliere il modo in cui automatizzare la creazione del token IAM, a seconda di come esegui l'autenticazione con {{site.data.keyword.Bluemix_notm}} e del tipo di ID {{site.data.keyword.Bluemix_notm}} che usi.

Se utilizzi un ID non federato, puoi scegliere una delle seguenti opzioni per creare un token IAM:
 - **Nome utente e password {{site.data.keyword.Bluemix_notm}}: ** puoi creare un token per automatizzare completamente la creazione del tuo token di accesso IAM.
 - **Genera una chiave API {{site.data.keyword.Bluemix_notm}}:** usa le chiavi API {{site.data.keyword.Bluemix_notm}}, che dipendono dall'account {{site.data.keyword.Bluemix_notm}} per cui vengono generate. Non puoi combinare la tua chiave API {{site.data.keyword.Bluemix_notm}} con un ID dell'account differente nello stesso token IAM. Per accedere ai cluster che sono stati creati con un account diverso da quello su cui si basa la tua chiave API {{site.data.keyword.Bluemix_notm}}, devi accedere all'account per generare una nuova chiave API. 

Se utilizzi un ID federato, puoi scegliere una delle seguenti opzioni per creare un token IAM:
 - **Genera una chiave API {{site.data.keyword.Bluemix_notm}}:** le chiavi API {{site.data.keyword.Bluemix_notm}} dipendono dall'account {{site.data.keyword.Bluemix_notm}} per cui vengono generate. Non puoi combinare la tua chiave API {{site.data.keyword.Bluemix_notm}} con un ID dell'account differente nello stesso token IAM. Per accedere ai cluster che sono stati creati con un account diverso da quello su cui si basa la tua chiave API {{site.data.keyword.Bluemix_notm}}, devi accedere all'account per generare una nuova chiave API. 
 - **Utilizza un passcode monouso:** se effettui l'autenticazione con {{site.data.keyword.Bluemix_notm}} utilizzando un passcode monouso, non puoi automatizzare completamente la creazione del tuo token IAM in quanto il richiamo del tuo passcode monouso richiede un'interazione manuale con il tuo browser web. Per automatizzare completamente la creazione del tuo token IAM, devi creare invece una chiave API {{site.data.keyword.Bluemix_notm}}. 

Quando crei il token di accesso, le informazioni del corpo incluse nella tua richiesta variano in base al metodo di autenticazione di {{site.data.keyword.Bluemix_notm}} che utilizzi. Sostituisci i seguenti valori:
- `<my_username>` = il tuo nome utente {{site.data.keyword.Bluemix_notm}}.
- `<my_password>` = la tua password {{site.data.keyword.Bluemix_notm}}.
- `<my_api_key>` = la tua chiave API {{site.data.keyword.Bluemix_notm}}.
- `<my_passcode>` = il tuo passcode monouso {{site.data.keyword.Bluemix_notm}}. Esegui `bx login --sso` e segui le istruzioni nell'output della CLI per richiamare il passcode monouso utilizzando il tuo browser web.

Esempio:
`POST https://iam.<region>.bluemix.net/oidc/token`

Per specificare una regione {{site.data.keyword.Bluemix_notm}}, rivedi le abbreviazioni delle regioni utilizzate negli endpoint API. Per ulteriori informazioni, vedi il documento relativo agli [endpoint API delle regioni {{site.data.keyword.Bluemix_notm}} ![Icona link esterno](../../../../icons/launch-glyph.svg)](https://console.bluemix.net/docs/containers/cs_regions.html#bluemix_regions){: new_window}.

Parametro di input	 | Valori
---------------- | -----------
Intestazione	| Content-Type:application/x-www-form-urlencoded<br>Authorization: Basic Xng7Png=<br>Nota: ti viene fornito `Xng7Png=`, l'autorizzazione con codifica URL per il nome utente bx e la password bx.
Corpo per il nome utente e la password {{site.data.keyword.Bluemix_notm}} |	grant_type: password<br>response_type: cloud_iam, uaa<br>username: `<my_username>`<br>password: `<my_password>`<br>uaa_client_id: cf<br>uaa_client_secret:<br>Nota: aggiungi la chiave uaa_client_secret senza alcun valore specificato.
Corpo per le chiavi API {{site.data.keyword.Bluemix_notm}} |	grant_type: urn:ibm:params:oauth:grant-type:apikey<br>response_type: cloud_iam<br>uaa<br>apikey: `<my_api_key>`<br>uaa_client_id: cf<br>uaa_client_secret:<br>Nota: aggiungi la chiave uaa_client_secret senza alcun valore specificato.
Corpo per il passcode monouso {{site.data.keyword.Bluemix_notm}} |	grant_type: urn:ibm:params:oauth:grant-type:passcode<br>response_type: cloud_iam, uaa<br>passcode: `<my_passcode>`<br>uaa_client_id: cf<br>uaa_client_secret:<br>Nota: aggiungi la chiave uaa_client_secret senza alcun valore specificato.

Output API di esempio:

```
{
"access_token": "<iam_token>",
"refresh_token": "<iam_refresh_token>",
"uaa_token": "<uaa_token>",
"uaa_refresh_token": "<uaa_refresh_token>",
"token_type": "Bearer",
"expires_in": 3600,
"expiration": 1493747503
}
```
Puoi trovare il token IAM nel campo **access_token** dell'output dell'API.

Il seguente esempio mostra come utilizzare il token IAM durante la chiamata delle API.

```
GET https://org.domain/api/v0002/bulk/devices
```

Parametro di input	 |	Valori
----------------- | -----------
Intestazioni	|	Content-Type: application/json<br>Authorization: bearer `<iam_token>`
