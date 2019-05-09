---

copyright:
  years: 2016, 2019
lastupdated: "2019-04-05"

keywords: Lite plan, migrate, Watson IoT Platform

subcollection: iot-platform

---

{:new_window: target="\_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:important: .important}

# Migrazione di {{site.data.keyword.iot_short_notm}} Lite a {{site.data.keyword.iot_short_notm}} non di produzione o di produzione
{: #org_migration}

<p>Questa raccolta di documentazione {{site.data.keyword.cloud}} è relativa al piano dei prezzi {{site.data.keyword.iot_full}} Lite e include le informazioni introduttive di base, le guide di riferimento API e delle informazioni generali per la risoluzione dei problemi.
Per la documentazione completa della funzione {{site.data.keyword.iot_short_notm}}, vedi la [documentazione del prodotto {{site.data.keyword.iot_short_notm}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html) nell'{{site.data.keyword.IBM}} Knowledge Center. Ulteriori informazioni sui vari piani sono disponibili in [Piani di servizio {{site.data.keyword.iot_short_notm}}](/docs/services/IoT?topic=iot-platform-plans_overview#plans_overview). 
</p>
{: important}

Dopo che hai esaminato attentamente Watson IoT Platform Lite e ti è ben chiaro in che modo può integrarsi nel tuo ambiente IoT, puoi eseguire un upgrade a [Watson IoT Platform non di produzione oppure a uno dei piani di produzione ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html){: new_window}.
{:shortdesc}

**Nota:** questo documento è destinato solo agli utenti che hanno un'istanza Lite. Se hai in precedenza creato delle istanze di IoT Platform con i piani Standard o Advanced Security, {{site.data.keyword.IBM}} lavorerà con te per migrare la tua istanza {{site.data.keyword.iot_short_notm}} esistente ai nuovi piani non di produzione o di produzione.

## Panoramica del processo di migrazione
{: #org_migration_overview}

Eseguendo la migrazione a {{site.data.keyword.iot_short_notm}}, rimuovi i limiti del piano Lite di 500 dispositivi e di consumo di dati mensile.

I piani {{site.data.keyword.iot_short_notm}} includono i seguenti componenti aggiuntivi per supportare l'architettura dell'applicazione IoT end-to-end:

- {{site.data.keyword.messagehub}} - una versione ospitata da {{site.data.keyword.IBM_notm}} della piattaforma di streaming Kafka che la tua applicazione può utilizzare per ricevere i dati IoT.
- {{site.data.keyword.dashdbshort}} per l'archiviazione dei dati analitici.
- DB {{site.data.keyword.cloudantfull}} per i dati delle serie temporali.
- {{site.data.keyword.cos_full}} per la conservazione dei dati a lungo termine.

Questo documento descrive i tipi di dati che potresti voler migrare da un'istanza Lite esistente a una versione completa.

**Nota:** di norma è più facile configurare il tuo ambiente {{site.data.keyword.iot_short_notm}} non di produzione o di produzione da zero poiché include componenti e funzioni oltre il servizio {{site.data.keyword.iot_short_notm}} Lite. Anche i dispositivi e gli utenti creati per la verifica nella versione Lite probabilmente non saranno gli stessi che utilizzerai per la produzione.

Se, tuttavia, vuoi trasferire qualcuna delle tue impostazioni Lite esistenti, le seguenti azioni ti illustrano il processo.

La documentazione sulle [API {{site.data.keyword.iot_short_notm}}]/docs/services/IoT?topic=iot-platform-api_overview#api_overview) fornisce le istruzioni su come richiamare le API e il loro insieme completo di parametri. 


## Prima di cominciare
{: #org_migration_byb}

Prima di poter iniziare il processo di migrazione, devi acquistare {{site.data.keyword.iot_short_notm}} (produzione o non di produzione). All'acquisto, il team delle operazioni {{site.data.keyword.IBM_notm}} eseguirà il provisioning di una nuova istanza {{site.data.keyword.iot_short_notm}} per tuo conto. Ciò includerà un nuovo ID organizzazione alfanumerico di sei caratteri.


## Migrazione di utenti
{: #user_migration}

Le [API di gestione utenti ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/security.html#!/Authorization_-_User_Management){: new_window} forniscono importazioni ed esportazioni in blocco di utenti {{site.data.keyword.iot_short_notm}} e possono essere utilizzate per esportare e importare gli utenti che desideri conservare nella tua nuova organizzazione.

1. Esporta gli utenti dall'organizzazione Lite.  
Utilizza il comando `GET /authorization/users` per esportare tutti i tuoi utenti dalla tua organizzazione dell'account Lite come un oggetto JSON.
2. Ripulisci l'elenco utenti.  
Se necessario, modifica la struttura JSON per rimuovere gli utenti che non desideri migrare alla tua nuova organizzazione.
3. Importa gli utenti alla nuova organizzazione.  
Utilizza il comando `POST /authorization/users/multiple` per importare l'elenco JSON modificato di utenti nella nuova organizzazione. 

Gli utenti ora hanno accesso alla nuova organizzazione, che verrà visualizzata nel selettore delle organizzazioni nel dashboard {{site.data.keyword.iot_short_notm}}.

##  Migrazione di dispositivi  
{: #device_migration}

La migrazione dei dispositivi può essere realizzata nei seguenti passi:  
1. Esegui la migrazione dei tipi di dispositivo che desideri conservare alla nuova organizzazione.  
2. Esegui la migrazione dei dispositivi stessi alla nuova organizzazione.  
3. Aggiorna il nome host utilizzato dai dispositivi per connettersi a {{site.data.keyword.cloud_notm}} per iniziare con il tuo nuovo ID organizzazione.
4. Esegui la migrazione delle eventuali informazioni di gestione dei dati che hai creato nella piattaforma Lite.   
Possono includere regole, oggetti e interfacce fisiche e logiche dei dispositivi.

<p>I tipi di dispositivo e i dispositivi possono essere migrati in blocco con le seguenti API:
<table>
<tr>
<th> Documentazione API </th>
<th> API di esportazione </th>
<th> API di importazione </th>
</tr>
<tr>
<td> [API tipo di dispositivo ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/org-admin.html) </td>
<td> `GET /device/types` </td>
<td> `POST /device/types` </td>
</tr>
<tr>
<td>  [API dispositivo ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/org-admin.html#!/Device_Bulk_Configuration) </td>
<td> `GET /bulk/devices` </td>
<td>  `POST /bulk/devices/add`</td>
</tr>
</table>
</p>
{: tip}


**Importante:** {{site.data.keyword.iot_short_notm}} non archivia i token di autenticazione del dispositivo ma solo la loro versione di cui è stato effettuato il salting. la chiamata `GET /bulk/devices` non è pertanto in grado di restituire i token di autenticazione per i dispositivi archiviati. Se hai un record dei token di autenticazione del dispositivo, puoi eseguirne l'aggiunta all'oggetto JSON prima di eseguire il caricamento in blocco. Altrimenti, devi generare dei nuovi token di autenticazione del dispositivo per ciascun dispositivo e copiarli sui dispositivi.  

Se stai utilizzando dei certificati lato dispositivo per autenticare i dispositivi invece dei token di autenticazione, non hai bisogno di eseguire tale operazione. Tuttavia, se stai utilizzando dei certificati lato dispositivo, devi caricare sulla nuova organizzazione i certificati che venivano utilizzati per il loro accesso.


## Aggiornamento di dispositivi
{: #update_devices}

Quando i tuoi dispositivi sono registrati nella nuova organizzazione, devi aggiornare la configurazione o il codice presenti su ciascuno dei tuoi dispositivi esistenti per utilizzare il nome host della nuova organizzazione.

Per i client di messaggistica MQTT e HTTP, utilizza il seguente nome host:  
`<orgId>.messaging.internetofthings.ibmcloud.com`

Punta i client API REST al seguente nome host:  
`<orgId>.internetofthings.ibmcloud.com`

**Importante:** se hai generato dei nuovi token di autenticazione per i tuoi dispositivi, devi copiarli su ciascun dispositivo.


## Migrazione della gestione dei dispositivi
{: #device_management}

Le [API di gestione dati ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/state-mgmt.html){: new_window} includono le API per esportare e importare le regole, le definizioni di oggetti e le interfacce fisiche e logiche dei dispositivi.

**Importante:** {{site.data.keyword.iot_short_notm}} attualmente non supporta il concetto di gemelli di asset per l'inserimento di dati.

## Tabelle e schede
{: #boards_cards}

{{site.data.keyword.iot_short_notm}} non include delle API per importare ed esportare definizioni e personalizzazioni di tabelle e schede. Devi eseguirne nuovamente la creazione in modo manuale nella nuova organizzazione.

## Abilita qualsiasi estensione richiesta
{: #extensions}

Devi creare nuovamente qualsiasi estensione che hai abilitato nella piattaforma Lite, come ad esempio i link a {{site.data.keyword.messagehub}}, {{site.data.keyword.cloudant_short_notm}} e Jasper nella nuova organizzazione.

## Migrazione di applicazioni
{: #application_migration}

Se hai sviluppato delle applicazioni che richiamano le API offerte con il servizio {{site.data.keyword.iot_short_notm}} Lite ad esempio per inviare o ricevere dati oppure per amministrare il servizio, devi eseguirne l'aggiornamento per utilizzare la tua nuova istanza {{site.data.keyword.iot_short_notm}} di produzione o di non produzione. Ciò vale anche per gli eventuali flussi Node-RED che è possibile tu stia utilizzando.
La migrazione comporta:
- L'aggiornamento delle applicazioni per utilizzare un nuovo ID organizzazione da sei caratteri.
- L'aggiornamento delle applicazioni per utilizzare le credenziali di chiave API e token che crei per la tua nuova istanza del servizio.

**Importante:** se stai utilizzando un'associazione mediante bind di Cloud Foundry per passare l'ID organizzazione e le credenziali all'applicazione, devi utilizzare un meccanismo differente poiché non viene eseguito il provisioning della nuova istanza {{site.data.keyword.iot_short_notm}} per l'esecuzione nel tuo spazio Cloud Foundry.

### Generazione delle credenziali di connessione API

Il processo di migrazione da seguire dipende dalla natura della tua applicazione. Di norma, per tutti i casi, il primo passo consiste nell'acquisire una chiave API e un token di autenticazione perché la tua applicazione possa farne uso.

1. Accedi al dashboard di livello superiore del tuo nuovo servizio {{site.data.keyword.iot_short_notm}}.
2. Seleziona la scheda **Usage**.
3. Fai clic sul link **View Details** per visualizzare le informazioni sul servizio {{site.data.keyword.iot_short_notm}}.  
Vengono visualizzate le seguenti informazioni:
   - L'ID organizzazione di sei caratteri
   - La chiave API e il token.  
   Devi generare delle nuove chiavi API per ciascuna delle tue applicazioni invece di utilizzare la chiave API mostrata qui. Ciò ti consente di impostare le autorizzazioni appropriate per ciascuna applicazione.
   - L'URL dell'host.
4. Crea una combinazione di chiave API e token di autenticazione per la tua applicazione.  
Ne avrai bisogno quando configuri l'applicazione per stabilire una connessione alla tua organizzazione.   
   1.  Fai clic su `Launch`.  
   Questo ti porterà al dashboard del servizio sottostante, che hai usato per amministrare il servizio {{site.data.keyword.iot_short_notm}} Lite.
   2. Seleziona **Apps**.
   3. Fai clic su **Generate API Key**
   4. Copia i valori della chiave API e del token di autenticazione che vengono elencati.
   5. Seleziona un ruolo appropriato per la tua applicazione.   
   6. Aggiungi un commento in modo da identificare più facilmente questa combinazione di chiave API e token di autenticazione.
   7. Fai clic su **Generate**.
   8. **Importante:** crea una copia locale del token di autenticazione. Non è possibile ricrearlo dopo che hai chiuso la finestra.


### Aggiornamento delle applicazioni Node-RED
Dovrai configurare i tuoi nodi Node-RED per stabilire una connessione alla tua nuova istanza {{site.data.keyword.iot_short_notm}}. I tuoi nodi `ibmiot` non saranno più in grado di utilizzare l'opzione di autenticazione `BluemixService` e dovrai pertanto selezionare invece l'opzione `API Key`.
1. Apri il nodo `ibmiot` per la modifica.
2. Nelle proprietà del nodo, seleziona **API Key**.
3. Per il campo API Key, fai clic sull'icona di modifica e immetti quindi la chiave API e il token di autenticazione che hai salvato dal passo precedente.
4. Salva le tue modifiche e ridistribuisci il tuo flusso Node-RED.

### Aggiornamento di un'applicazione che non utilizza un'associazione mediante bind Cloud Foundry
Identifica l'ubicazione in cui la tua applicazione archivia l'ID org, la chiave API e il token di autenticazione e sostituiscili con i valori che hai salvato in precedenza. 

Se la tua applicazione utilizza uno degli SDK {{site.data.keyword.iot_short_notm}}, questi valori saranno probabilmente memorizzati in un file delle proprietà.
{: tip}

### Aggiornamento di un'applicazione che utilizza un'associazione mediante bind Cloud Foundry

{{site.data.keyword.cloud_notm}} fornisce un meccanismo per associare mediante bind le applicazioni Cloud Foundry a uno o più servizi Cloud Foundry. Le associazioni mediante bind possono essere stabilite utilizzando la CLI {{site.data.keyword.cloud_notm}} o creando una connessione (`Connection`) tra l'applicazione e il servizio nel dashboard {{site.data.keyword.cloud_notm}}.

Quando un'applicazione è associata mediante bind a un servizio, le credenziali di chiave API e token di autenticazione vengono copiate nella variabile di ambiente `VCAP_SERVICES` da cui l'applicazione può eseguirne il richiamo.

**Importante:** questo meccanismo di associazione mediante bind non può essere utilizzato con il nuovo servizio {{site.data.keyword.iot_short_notm}}. Devi trovare il codice nella tua applicazione che sta leggendo da `VCAP_SERVICES` e sostituirlo con il codice che legge i valori da un'ubicazione in cui ora archivi la chiave API e il token di autenticazione. Per completare l'aggiornamento, devi ricompilare e ridistribuire la tua applicazione.
