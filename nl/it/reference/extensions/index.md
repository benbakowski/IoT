---

copyright:
  years: 2015, 2019
lastupdated: "2019-02-13"

---

{:new_window: target="\_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:important: .important}

# Integrazioni del servizio esterno
{: #ref-index}

<p>Questa raccolta di documentazione {{site.data.keyword.Bluemix}} è relativa al piano dei prezzi {{site.data.keyword.iot_full}} Lite e include le informazioni introduttive di base, le guide di riferimento API e delle informazioni generali per la risoluzione dei problemi.
Per la documentazione completa della funzione {{site.data.keyword.iot_short_notm}}, vedi la [documentazione del prodotto {{site.data.keyword.iot_short_notm}} ![Icona link esterno](../../../../icons/launch-glyph.svg "icona link esterno")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html) nell'IBM Knowledge Center. Ulteriori informazioni sui vari piani sono disponibili in [Piani di servizio {{site.data.keyword.iot_short_notm}}](/docs/IoT/plans_overview.html#plans_overview). 
</p>
{: important}

L'integrazione del servizio esterno ti consente di accedere ai dati e alle operazioni da servizi di terze parti o esterni nella tua organizzazione {{site.data.keyword.iot_full}}.

## Jasper
{: #jasper}

Jasper è una piattaforma di amministrazione e gestione per i dispositivi SIM. Jasper è integrato nel dashboard {{site.data.keyword.iot_short_notm}}, rende possibile gestire i dispositivi Jasper tramite il dashboard della tua organizzazione {{site.data.keyword.iot_short_notm}}.

### Operazioni supportate per Jasper

L'integrazione Jasper integrata fornita dalla nostra piattaforma fornisce supporto per le seguenti operazioni Jasper:

- Visualizzazione dei dati Jasper complessivi
  - Mostra stato, piano tariffario, utilizzo dati da inizio mese, utilizzo SMS da inizio mese, utilizzo voce da inizio mese, limiti in eccedenza, data di aggiunta e data di modifica.
- Modifica dello stato di attivazione della SIM
  - Seleziona da inventario, pronto per l'attivazione, attivato, disattivato e ritirato.
- Visualizzazione dell'utilizzo della SIM
  - Mostra data di inizio del ciclo, dati totali e fatturabili, SMS totali e fatturabili, voce totale e fatturabile.
  - La data di inizio del ciclo di vita può essere impostata utilizzando un formato della data AAAA-MM-GG.
- Inviare SMS alla SIM
- Modificare il piano tariffario

Puoi accedere alle operazioni supportate nel drill-down del dispositivo di un dispositivo connesso a Jasper dopo che sono stati completati i seguenti passi di configurazione.

### API REST per Jasper
Per accedere all'API REST per Jasper, consulta la sezione dell'estensione Jasper nella documentazione [{{site.data.keyword.iot_short_notm}} HTTP REST API ![Icona link esterno](../../../../icons/launch-glyph.svg "Icona link esterno")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/ext-jasper.html){: new_window}.

### Configurazione di Jasper

Per connettere il tuo servizio Jasper alla tua organizzazione {{site.data.keyword.iot_short_notm}}, devi completare due fasi di configurazione. In primo luogo, {{site.data.keyword.iot_short_notm}} deve essere collegato al tuo servizio Jasper, quindi i tuoi dispositivi {{site.data.keyword.iot_short_notm}} devono essere configurati.


1. Abilita l'estensione Jasper. Per abilitare l'integrazione Jasper con la tua organizzazione {{site.data.keyword.iot_short_notm}}, completa la seguente procedura:
  1. Dal dashboard {{site.data.keyword.iot_short_notm}}, seleziona **Extensions**.
  2. Nella pagina **Extensions**, fai clic su **Add Extension**.
  3. Fai clic su **Add** accanto a Jasper.
  4. Immetti i tuoi nome utente, password, chiave di accesso e ID dominio Jasper.
  5. Fai clic su **Done**.

2. Configura i tuoi dispositivi.
Puoi configurare i dispositivi connessi alla tua organizzazione {{site.data.keyword.iot_short_notm}} e al tuo account Jasper per visualizzare i dati da Jasper nel dashboard {{site.data.keyword.iot_short_notm}}.  
**Importante:** la configurazione di Jasper non può essere applicata come parte del processo di aggiunta del dispositivo. Solo i dispositivi precedentemente connessi possono essere configurati con Jasper.  
Per configurare i tuoi dispositivi collegati a Jasper, completa la seguente procedura:
 1. Nella pagina Devices del tuo dashboard {{site.data.keyword.iot_short_notm}}, trova il dispositivo connesso a Jasper da configurare.
 2. Seleziona il dispositivo per aprire la vista Device Drilldown.
 3. Scorri verso il basso fino a Extension Configuration.
 4. Immetti la configurazione dell'estensione utilizzando il seguente formato JSON e quindi fai clic su **Confirm changes** per salvare la tua configurazione.  

```json  
    {
        "jasper": {
            "iccid": "string"
        }
    }

```

Quando l'organizzazione è configurata correttamente, viene visualizzata la sezione Extensions nella sezione Extensions Configuration nella vista Device Drilldown.

## AT&T
{: #att}

### Operazioni supportate per AT&T

L'estensione AT&T abilita le seguenti operazioni AT&T:

- Visualizzazione generale dei dati AT&T
  - Mostra stato, piano tariffario, utilizzo dati da inizio mese, utilizzo SMS da inizio mese, utilizzo voce da inizio mese, limiti in eccedenza, data di aggiunta e data di modifica.
- Modifica dello stato di attivazione della SIM
  - Seleziona da inventario, pronto per l'attivazione, attivato, disattivato e ritirato.
- Visualizzazione dell'utilizzo della SIM
  - Mostra: data di inizio del ciclo, dati totali e fatturabili, SMS totali e fatturabili, voce totale e fatturabile.
  - La data di inizio del ciclo di vita può essere impostata utilizzando un formato della data AAAA-MM-GG.
- Inviare SMS alla SIM
- Modificare il piano tariffario

### API REST per AT&T
Per accedere all'API REST per AT&T, consulta la sezione dell'estensione AT&T nella documentazione [{{site.data.keyword.iot_short_notm}} HTTP REST API ![Icona link esterno](../../../../icons/launch-glyph.svg "Icona link esterno")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/ext-atnt.html){: new_window}.

### Configurazione di AT&T

Per connettere la tua organizzazione {{site.data.keyword.iot_short_notm}} ad AT&T, devi completare la configurazione dell'organizzazione e del dispositivo.

Per configurare la tua piattaforma {{site.data.keyword.iot_short_notm}}, completa la seguente procedura:

1. Abilita l'estensione AT&T. Per abilitare l'integrazione AT&T con la tua organizzazione {{site.data.keyword.iot_short_notm}}, completa la seguente procedura:
  1. Dal dashboard {{site.data.keyword.iot_short_notm}}, seleziona **Extensions**.
  2. Nella pagina **Extensions**, fai clic su **Add Extension**.
  3. Fai clic su **Add** accanto a AT&T.
  4. Immetti i tuoi nome utente, password, chiave di accesso e ID dominio AT&T.
  5. Fai clic su **Done**.

Per connettere la tua organizzazione {{site.data.keyword.iot_short_notm}} con il tuo account AT&T, devi completare due fasi di configurazione. Completa configurazione della tua organizzazione e quindi configura i tuoi dispositivi.


2. Configura i tuoi dispositivi
Puoi configurare i dispositivi collegati alla tua organizzazione {{site.data.keyword.iot_short_notm}} e al tuo account AT&T per visualizzare i dati da AT&T nel dashboard {{site.data.keyword.iot_short_notm}}.  
**Importante:** la configurazione di AT&T non può essere applicata come parte del processo Add Device. Solo i dispositivi connessi precedentemente possono essere configurati con AT&T.  
Per configurare i tuoi dispositivi collegati a AT&T, completa la seguente procedura:
 1. Nella pagina Devices del tuo dashboard {{site.data.keyword.iot_short_notm}}, trova il dispositivo connesso ad AT&T da configurare.
 2. Seleziona il dispositivo per aprire la vista Device Drilldown.
 3. Scorri verso il basso fino a Extension Configuration.
 4. Immetti la configurazione dell'estensione utilizzando il seguente formato JSON e quindi fai clic su **Confirm changes** per salvare la tua configurazione.  

```json  
    {
        "atnt": {
            "iccid": "string"
        }
    }

```

Quando l'organizzazione è configurata correttamente, viene visualizzata la sezione Extensions nella sezione Extensions Configuration nella vista Device Drilldown.

## Bridge Arm Mbed
{: #arm}

Il bridge consente ai dispositivi Arm Mbed di integrarsi con {{site.data.keyword.iot_short_notm}} e di scambiare messaggi in modo bidirezionale. Per abilitare questa integrazione, devi prima registrare un account Arm Mbed Cloud e fornire le informazioni di connessione richieste per la tua configurazione di {{site.data.keyword.iot_short_notm}}.

### Configurazione


1. Abilita l'estensione del bridge Arm Mbed. Per abilitare l'estensione , completa la seguente procedura:
  1. Dal dashboard {{site.data.keyword.iot_short_notm}}, seleziona **Extensions**.
  2. Nella pagina Extensions, fai clic su **Add Extension**.
  3. Fai clic su **Add** accanto all'estensione del bridge Arm Mbed.
  4. Immetti la tua chiave di accesso per Arm Mbed. Puoi crearla utilizzando il portale Arm Mbed all'indirizzo [https://portal.mbedcloud.com ![Icona link esterno](../../../../icons/launch-glyph.svg "Icona link esterno")](https://portal.mbedcloud.com){: new_window}.
  5. Verifica che le credenziali siano corrette facendo clic sul pulsante **Check Connection**.
  6. Fai clic su **Done**.

### Formato payload

La piattaforma Arm Mbed utilizza due tipi di messaggi in entrata: le notifiche e le risposte asincrone. {{site.data.keyword.iot_short_notm}} può inviare comandi ai dispositivi collegati alla piattaforma Arm Mbed.

#### Notifications

Le notifiche vengono generate dalle modifiche nel dispositivo e nei dati del sensore. Dopo che {{site.data.keyword.iot_short_notm}} elabora il messaggio, questo viene inviato all'argomento di evento del dispositivo allo stesso modo di un dispositivo connesso direttamente a {{site.data.keyword.iot_short_notm}}. Il tipo di evento utilizzato per le notifiche che hanno origine sui dispositivi connessi alla piattaforma Arm Mbed è `notify`.

Il seguente esempio di codice mostra il formato del payload per una notifica inviata dall'API della piattaforma Arm Mbed:

```
{
  "ep":<endpoint/deviceID>,
  "path":<resource path>,
  "ct":<content type>,
  "payload":<Base64 encoded payload>,
  "max-age":<how long the payload is valid, in seconds>
}
```

#### Risposte asincrone

Quando {{site.data.keyword.iot_short_notm}} invia un comando a un dispositivo collegato alla piattaforma Arm Mbed, il dispositivo restituisce un messaggio di conferma a {{site.data.keyword.iot_short_notm}}. Questo messaggio di conferma viene denominato _risposta asincrona_ e utilizza il tipo di evento `asyncResponse`.

Il seguente esempio di codice mostra il formato del payload per una risposta asincrona inviata dal servizio cloud Arm Mbed:

```
{
  "id":<transaction id>,
  "status":<200 is command was sucessfully executed. Check other HTTP response codes>,
  "ct":<content type>,
  "max-age":<how long the payload is valid, in seconds>,
  "payload":<base64 encoded payload>,
  "ep":<endpoint/deviceID affected by the command>,
  "path":<resource path affected by the command>
}
```

#### Invio di comandi alla piattaforma Arm Mbed

{{site.data.keyword.iot_short_notm}} può inviare comandi ai dispositivi collegati alla piattaforma Arm Mbed. I comandi inviati alla piattaforma Arm Mbed devono utilizzare il seguente formato JSON:

```
{
  "method":<PUT or POST>,
  "deviceId":<endpoint/deviceId>,
  "resourceId":<resource path>,
  "payload": <Base64 encoded payload>
}
```
Il metodo scelto è sensibile al maiuscolo/minuscolo. Il carattere `/` iniziale del percorso della risorsa deve essere ignorato.


Il payload deve essere pubblicato sul seguente argomento:

```
iot-2/type/<device_type>/id/<deviceId>/cmd/<command_type>/fmt/<command_format>
```


## Orange
{: #orange}

L'estensione Orange consente di visualizzare i dati della SIM card dai dispositivi connessi a {{site.data.keyword.iot_short_notm}} e di avere una SIM card Orange installata.

### Operazioni supportate per Orange

Se hai un dispositivo connesso al tuo servizio {{site.data.keyword.iot_short_notm}} e una SIM card Orange, puoi utilizzare l'estensione Orange per visualizzare i seguenti dati della SIM card:

- Numero di serie della SIM
- Stato di attivazione
- Ultima modifica stato
- Ultimo aggiornamento stato
- Stato ubicazione

### API REST per Orange
Per accedere all'API REST per Orange, consulta la sezione dell'estensione Orange nella documentazione [{{site.data.keyword.iot_short_notm}} HTTP REST API ![Icona link esterno](../../../../icons/launch-glyph.svg "Icona link esterno")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/ext-orange.html){: new_window}.

### Configurazione di Orange

Per abilitare l'estensione Orange:

1. Dal dashboard {{site.data.keyword.iot_short_notm}}, seleziona **Extensions**.
2. Nella pagina **Extensions**, fai clic su **Add Extension**.
3. Fai clic su **Add** accanto all'estensione Orange.
4. Immetti i tuoi nome utente e password Orange.
6. Fai clic su **Done**.

Dopo aver abilitato l'estensione Orange, ogni dispositivo che ha una SIM card Orange deve essere configurato per visualizzare i dati della SIM Orange.

1. Nella scheda dei dispositivi del tuo dashboard {{site.data.keyword.iot_short_notm}}, trova il dispositivo SIM Orange da configurare.
2. Seleziona il dispositivo e scorri verso il basso fino a **Extension Configuration**.
3. Immetti la configurazione dell'estensione utilizzando il seguente formato JSON e quindi fai clic su **Confirm changes** per salvare la tua configurazione.

```json
    {
        "orange": {
            "serialnumber": "<serial number of Orange SIM>"
        }
    }

```
Quando l'organizzazione è configurata correttamente, viene visualizzata la sezione Extensions nella sezione Extensions Configuration nella vista Device Drilldown.

## Spazio di archiviazione dei dati cronologici
{: #historical_data}

L'estensione dell'archiviazione di dati cronologici ti consente di individuare e configurare servizi di archiviazione dei messaggi compatibili, come ad esempio [{{site.data.keyword.cloudantfull}} ![Icona link esterno](../../../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/cloudant_connector.html){: new_window} o [{{site.data.keyword.messagehub_full}} ![Icona link esterno](../../../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/message_hub.html){: new_window} per i tuoi dati IoT.

## Pacchetti di gestione del dispositivo personalizzati
{: #device_mgmt}

La gestione del dispositivo è una funzione principale di {{site.data.keyword.iot_short_notm}}, tuttavia, può essere estesa per sviluppare ulteriori funzionalità. I pacchetti per la gestione del dispositivo personalizzati devono essere composti da un JSON valido e definire almeno un'azione di gestione del dispositivo personalizzata.

Per ulteriori informazioni sulle funzioni di gestione dei dispositivi personalizzate, compreso un esempio del formato JSON richiesto, vedi [Device management custom extensions ![Icona link esterno](../../../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/devices/device_mgmt/custom_actions.html){: new_window}.

### Aggiunta di un pacchetto di gestione del dispositivo personalizzato

I pacchetti di gestione del dispositivo personalizzati possono essere aggiunti utilizzando il dashboard {{site.data.keyword.iot_short_notm}} o l'API.

Per aggiungere un pacchetto di gestione personalizzato utilizzando il dashboard {{site.data.keyword.iot_short_notm}}:

1. Dal tuo dashboard {{site.data.keyword.iot_short_notm}}, fai clic su **Impostazioni** dalla barra di navigazione.
2. Fai clic su **Pacchetti di gestione del dispositivo personalizzati**.
3. Fai clic sul pulsante **Aggiungi pacchetto**.
4. Selezione il tuo file pacchetto e fai clic su **Apri**.

Per aggiungere un pacchetto di gestione del dispositivo personalizzato tramite l'API, consulta la [Documentazione API {{site.data.keyword.iot_short_notm}} ![Icona link esterno](../../../../icons/launch-glyph.svg "Icona link esterno")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/orgAdmin.html){: new_window}.

## Email
{: #email}

È possibile aggiungere utenti a {{site.data.keyword.iot_short_notm}} utilizzando gli inviti email. Per informazioni, consulta [Gestione dell'accesso utente](/docs/IoT/add_users.html).

Per utilizzare la funzione di invito email, deve essere configurata un'estensione email in modo che utilizzi il servizio online SendGrid o SMTP (Simple Mail Transfer Protocol). L'estensione può inoltre utilizzare l'applicazione {{site.data.keyword.Bluemix_notm}} SendGrid.

### Servizio online SendGrid

Per configurare l'estensione email per l'utilizzo con il servizio online SendGrid, segui questi passi:

1. Richiama la chiave API autorizzata dal tuo account online SendGrid:
2. Nel tuo dashboard {{site.data.keyword.iot_short_notm}}, fai clic su **Extensions** dalla barra di navigazione.
3. Nella sezione **Email**, fai clic su **Setup**.
4. Seleziona **SendGrid with API key**
5. Immetti il nome e l'indirizzo email del tuo amministratore del sito e la chiave API autorizzata.

### Servizio SMTP

Per configurare l'estensione email per l'utilizzo con il servizio SMTP, segui questi passi:

1. Nel tuo dashboard {{site.data.keyword.iot_short_notm}}, fai clic su **Extensions** dalla barra di navigazione.
2. Nella sezione **Email**, fai clic su **Setup**.
3. Seleziona **SMTP**.
4. Immetti i dettagli di configurazione del tuo servizio SMTP.

### Applicazione {{site.data.keyword.Bluemix_notm}} SendGrid

Per configurare l'estensione email per l'utilizzo con l'applicazione {{site.data.keyword.Bluemix_notm}} SendGrid, segui questi passi:

1. Crea un'applicazione fittizia e associa il servizio SendGrid.  
Per richiamare le credenziali di configurazione, aggiungi e associa mediante bind il servizio SendGrid a un'applicazione fittizia.

 1. Dal tuo dashboard {{site.data.keyword.Bluemix_notm}}, fai clic su **Create Service**.
 2. Seleziona il servizio SendGrid dal catalogo e fai clic su **Create**.
 3. Dal dashboard {{site.data.keyword.Bluemix_notm}} aggiungi l'applicazione {{site.data.keyword.runtime_nodejs_full}}.
 4. Fai clic sull'applicazione {{site.data.keyword.runtime_nodejs_notm}} dal dashboard {{site.data.keyword.Bluemix_notm}} e fai clic su **Bind a service or API**.
 5. Seleziona il servizio SendGrid e fai clic su **Add**.
 6. Riprepara l'applicazione {{site.data.keyword.runtime_nodejs_notm}}.
2. Preparazione alla configurazione del servizio {{site.data.keyword.iot_short_notm}}.  
{{site.data.keyword.iot_short_notm}} può essere configurato utilizzando il dashboard {{site.data.keyword.iot_short_notm}} o l'API {{site.data.keyword.iot_short_notm}}.  
 1. Fai clic sull'applicazione {{site.data.keyword.runtime_nodejs_notm}} dal dashboard {{site.data.keyword.Bluemix_notm}}.
 2. Fai clic su **Environment Variables** dalla barra di navigazione.
 3. Copia il JSON visualizzato in un file di testo temporaneo.  
 Il JSON deve essere nel seguente formato:
```
{
  "name": "SendGridServiceName",
  "label": "user-provided",
  "credentials": {
    "password": "xxx",
    "hostname": "smtp.sendgrid.net",
    "username": "username"
  }
}
```
3. Aggiungi i dati di configurazione all'organizzazione {{site.data.keyword.iot_short_notm}}.
 1. Apri il dashboard {{site.data.keyword.iot_short_notm}}.
 2. Fai clic su **Extensions** dalla barra di navigazione.
 3. Fai clic su **Setup** sotto l'icona **Email**.
 4. Seleziona **SendGrid with username**.
 5. Immetti i dati di configurazione dal file di testo temporaneo.
 6. Fai clic su **Done**.
