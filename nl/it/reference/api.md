---

copyright:

years: 2017, 2019
lastupdated: "2019-04-16"

keywords: own organization, Extension HTTP APIs, API Use, AT&T Extension, Administer AT&T

subcollection: iot-platform

---

{:new_window: target="\_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:tip: .tip}
{:pre: .pre}
{:important: .important}


# API
{: #api_overview}

<p>Questa raccolta di documentazione {{site.data.keyword.cloud}} è relativa al piano dei prezzi {{site.data.keyword.iot_full}} Lite e include le informazioni introduttive di base, le guide di riferimento API e delle informazioni generali per la risoluzione dei problemi.
Per la documentazione completa della funzione {{site.data.keyword.iot_short_notm}}, vedi la [documentazione del prodotto {{site.data.keyword.iot_short_notm}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html) nell'IBM Knowledge Center. Ulteriori informazioni sui vari piani sono disponibili in [Piani di servizio {{site.data.keyword.iot_short_notm}}](/docs/services/IoT?topic=iot-platform-plans_overview#plans_overview). 
</p>
{: important}

Sono disponibili molte API per lo sviluppo del codice per i dispositivi, i gateway e le applicazioni collegate a {{site.data.keyword.iot_full}}.

Le API HTTP sono protette dall'autenticazione di base HTTP. Quando generi una chiave API utilizzando il dashboard, ti vengono presentati un token di autenticazione e una chiave. Per ulteriori informazioni sui token e sulle chiavi API, vedi [Connessione chiave API ![Icona link esterno](../../../icons/launch-glyph.svg)](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/platform_authorization.html#api-key){: new_window}.


## Informazioni sulle API HTTP
{: #api_about}

Ogni organizzazione {{site.data.keyword.iot_short_notm}} viene identificata da un ID organizzazione di 6 caratteri, necessario nel nome host per qualsiasi chiamata API HTTP.   

### Documenti API
{: #api_docs}

Per visualizzare i documenti API, vai alla pagina [IBM Watson IoT Platform REST APIs ![Icona link esterno](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/index.html){: new_window}. Da questa pagina di destinazione, puoi accedere alla documentazione per le API {{site.data.keyword.iot_short_notm}} disponibili. 

### Documenti API interattivi

Per visualizzare e utilizzare i documenti API interattivi, puoi accedere all'URL di base per la tua organizzazione al seguente indirizzo: 

`https://<orgId>.internetofthings.ibmcloud.com/docs/index.html`

Da questa pagina di destinazione, puoi accedere alla documentazione per le API {{site.data.keyword.iot_short_notm}} disponibili. Per avere l'accesso per eseguire le chiamate API direttamente dalla documentazione, è necessario che tu sia autorizzato. 

Per essere autorizzato automaticamente, completa la seguente procedura: 

1. Accedi al dashboard {{site.data.keyword.iot_short_notm}}.
2. Nello stesso browser, apri una nuova scheda e vai alla pagina di destinazione dei documenti API interattivi. 

Se non sei collegato al dashboard {{site.data.keyword.iot_short_notm}}, completa la seguente procedura:

1. Vai alla pagina di destinazione dei documenti API interattivi. 
2. Seleziona `Authorize`.
3. Nella casella `Available authorizations`, imposta il nome utente sulla chiave API e la password sul token di autenticazione. Seleziona `Authorize`.
4. Chiudi la casella `Available authorizations`. **Importante:** non selezionare `Logout`.

Una volta autorizzato, vai alle chiamate API specifiche e utilizza il pulsante `Try it out` per eseguire le chiamate API direttamente dalla documentazione. 

<!-- To authenticate requests to the application API, set the username to the API key and the password to the authentication token. -->
