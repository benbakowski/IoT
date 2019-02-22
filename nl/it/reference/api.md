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


# API
{: #api_overview}

<p>Questa raccolta di documentazione {{site.data.keyword.Bluemix}} è relativa al piano dei prezzi {{site.data.keyword.iot_full}} Lite e include le informazioni introduttive di base, le guide di riferimento API e delle informazioni generali per la risoluzione dei problemi.
Per la documentazione completa della funzione {{site.data.keyword.iot_short_notm}}, vedi la [documentazione del prodotto {{site.data.keyword.iot_short_notm}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html) nell'IBM Knowledge Center. Ulteriori informazioni sui vari piani sono disponibili in [Piani di servizio {{site.data.keyword.iot_short_notm}}](/docs/IoT/plans_overview.html#plans_overview). 
</p>
{: important}

Sono disponibili molte API per lo sviluppo del codice per i dispositivi, i gateway e le applicazioni collegate a {{site.data.keyword.iot_full}}.

Le API HTTP sono protette con l'autenticazione di base HTTP. Quando generi una chiave API utilizzando il dashboard, ti vengono presentati un token di autenticazione e una chiave. Per ulteriori informazioni sui token e sulle chiavi API, vedi [API key connection ![Icona link esterno](../../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/platform_authorization.html#api-key).


## Informazioni sulle API HTTP
{: #api_about}

Dopo la registrazione per la tua organizzazione, ti viene fornito un ID dell'organizzazione di 6 caratteri che è necessario nel nome host per qualsiasi chiamata API HTTP. È possibile accedere all'URL di base della tua organizzazione al seguente indirizzo:

https://<**orgId**>.internetofthings.ibmcloud.com/api/v0002

Per autenticare le richieste nell'API dell'applicazione, imposta in nome utente sulla chiave API e la password sul token di autenticazione.

Per le API di messaggistica, utilizza il seguente indirizzo:

https://<**orgId**>.messaging.internetofthings.ibmcloud.com/api/v0002

## API HTTP
{: #api_http}

API                     | Utilizzata per ...       
------------- | -------------
[Organization Administration ![Icona link esterno](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/orgAdmin.html){: new_window} | Configura un'organizzazione (incluse la creazione e l'eliminazione dei dispositivi), controlla l'utilizzo, vedi lo stato del servizio ed esegue la diagnostica dei problemi di connessione del dispositivo.
[Security ![Icona link esterno](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/security.html){: new_window} | Gestisce l'autenticazione e l'autorizzazione di utenti, chiavi API e dispositivi.
[Information Management ![Icona link esterno](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/info-mgmt.html){: new_window} |Accede ai dati evento del dispositivo, ottiene e aggiorna anche l'ubicazione del dispositivo e ottiene le informazioni sul meteo per tale ubicazione. 
[Data Management  ![Icona link esterno](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/state-mgmt.html){: new_window}   |   Organizza e integra i dati in entrata e in uscita di {{site.data.keyword.iot_short_notm}}.
[Device Management ![Icona link esterno](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/deviceMgmt.html){: new_window} | Interagisce con i dispositivi gestiti utilizzando il protocollo di gestione del dispositivo.
[Messaging ![Icona link esterno](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/http-messaging.html){: new_window}   | Pubblica gli eventi e invia i comandi utilizzando HTTP.
[Risk Management ![Icona link esterno](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/riskmgmt.html){: new_window}   |Gestisce le politiche e i report di gestione dei rischi.

## Estensione API HTTP
{: #api_extension}

API                     | Utilizzata per ...       
------------- | -------------
[AT&T Extension ![Icona link esterno](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/ext-atnt.html){: new_window} | Gestisce i dispositivi AT&T.
[Jasper Extension  ![Icona link esterno](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/ext-jasper.html){: new_window} | Gestisce i dispositivi Jasper.
[Orange Extension  ![Icona link esterno](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/ext-orange.html){: new_window} | Visualizza i dati della SIM card dai dispositivi collegati ala tua organizzazione {{site.data.keyword.iot_short_notm}} e ha una SIM card Orange installata.

## API HTTP beta
{: #api_beta}

API                     | Utilizzata per ...       
------------- | -------------
[Restore Deleted Devices ![Icona link esterno](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002-beta/restore-device-beta.html){: new_window}   | Se un dispositivo viene eliminato per errore, puoi ripristinarlo entro 14 giorni.
