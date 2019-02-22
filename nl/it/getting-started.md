---

copyright:
  years: 2016, 2019
lastupdated: "2019-02-13"

---

{:new_window: target="\_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:important: .important}


# Esercitazione introduttiva
{: #gettingstartedtemplate .task}

<p>Questa raccolta di documentazione {{site.data.keyword.Bluemix}} è relativa al piano dei prezzi {{site.data.keyword.iot_full}} Lite e include le informazioni introduttive di base, le guide di riferimento API e delle informazioni generali per la risoluzione dei problemi.
Per la documentazione completa della funzione {{site.data.keyword.iot_short_notm}}, vedi la [documentazione del prodotto {{site.data.keyword.iot_short_notm}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html) nell'IBM Knowledge Center. Ulteriori informazioni sui vari piani sono disponibili in [Piani di servizio {{site.data.keyword.iot_short_notm}}](/docs/IoT/plans_overview.html#plans_overview). 
</p>
{: important}

In questa esercitazione di introduzione a {{site.data.keyword.iot_short_notm}}, connettiamo un dispositivo IoT a {{site.data.keyword.iot_short_notm}}.
{:shortdesc}

## Informazioni su quest'attività
{: #about .sectiontitle}  

Prima di poter iniziare a ricevere i dati dai tuoi dispositivi IoT, devi collegarli a  {{site.data.keyword.iot_short_notm}}. La connessione di un dispositivo a {{site.data.keyword.iot_short_notm}} implica la registrazione del dispositivo con {{site.data.keyword.iot_short_notm}} e quindi l'utilizzo delle informazioni di registrazione per configurare il dispositivo da collegare a {{site.data.keyword.iot_short_notm}}.

## Prima di cominciare
{: #byb .sectiontitle}  

Prima di poter iniziare a utilizzare {{site.data.keyword.iot_short_notm}}, devi disporre dei seguenti elementi:  
* Un account [{{site.data.keyword.Bluemix}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/registration/){: new_window}.
* Un'istanza {{site.data.keyword.iot_short_notm}}.  
Puoi creare un'istanza {{site.data.keyword.iot_short_notm}} direttamente dalla pagina [{{site.data.keyword.iot_short_notm}} nel catalogo dei servizi {{site.data.keyword.Bluemix_short}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/catalog/services/internet-of-things-platform/){:new_window}.  
* Un dispositivo che soddisfa i seguenti requisiti:  
  *	Il tuo dispositivo deve essere in grado di comunicare utilizzando i protocolli HTTP o MQTT.
  * I messaggi del dispositivo devono essere conformi ai requisiti del payload del messaggio di {{site.data.keyword.iot_short_notm}}.  
Per ulteriori informazioni, vedi [Developing devices on {{site.data.keyword.iot_short_notm}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/devices/device_dev_index.html){: new_window}.

A seconda della tua situazione, esplora le seguenti opzioni:

 |  |   Il servizio è stato distribuito | Il servizio non è stato distribuito
 | -------------| ------------- | -------------
  |**Ho un dispositivo da collegare** | Attieniti al processo descritto in questo argomento. | Esplora la connessione del dispositivo in [Play with {{site.data.keyword.iot_short_notm}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://discover-iot.eu-gb.mybluemix.net/?cm_mc_uid=44491599487314618721024&cm_mc_sid_50200000=1462798151#/play){:new_window}.
  |**Non ho un dispositivo da connettere** | [Simula i dati del dispositivo](/docs/IoT/devices/device_sim.html) oppure [connetti il tuo smartphone ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://discover-iot.eu-gb.mybluemix.net/?cm_mc_uid=44491599487314618721024&cm_mc_sid_50200000=1462798151#/play/device/smartphone){:new_window}. | Introduzione a [{{site.data.keyword.iot_short_notm}} Starter](https://console.bluemix.net/docs/IoT-starter/iot500.html#gettingstartedtemplate){:new_window}.



## Passo 1: registra il tuo dispositivo
{: #step1 .sectiontitle}  
La registrazione di un dispositivo implica la classificazione del dispositivo come un tipo dispositivo, dando al dispositivo un nome e fornendo le informazioni sul dispositivo. Quindi fornisci un token di connessione o accetta un token generato da {{site.data.keyword.iot_short_notm}}.

**Suggerimento:** puoi registrare i tuoi dispositivi uno per volta dal [dashboard {{site.data.keyword.iot_short_notm}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://internetofthings.ibmcloud.com){: new_window} oppure puoi utilizzare l'[API {{site.data.keyword.iot_short_notm}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/org-admin.html#!/Device_Bulk_Configuration/post_bulk_devices_add){: new_window} per aggiungere più dispositivi.

Per aggiungere un dispositivo dal dashboard {{site.data.keyword.iot_short_notm}}:
1. Nella console {{site.data.keyword.Bluemix_notm}}, fai clic su **Avvia** nella pagina dei dettagli del servizio {{site.data.keyword.iot_short_notm}}.

    Si apre la console web {{site.data.keyword.iot_short_notm}} in una nuova scheda del browser al seguente URL:

    ```
    https://org_id.internetofthings.ibmcloud.com/dashboard/#/overview
    ```

    Dove *org_id* è l'ID della tua organizzazione {{site.data.keyword.iot_short_notm}}.

2. Nel dashboard della panoramica, dal pannello del menu, seleziona **Devices** e fai clic su **Add Device**.

3. Crea un tipo di dispositivo per il dispositivo che stai aggiungendo.

    Ogni dispositivo collegato a {{site.data.keyword.iot_short_notm}} deve essere associato a un tipo dispositivo. I tipi di dispositivo sono gruppi di dispositivi che condividono caratteristiche comuni.

    1. Fai clic su **Create device type**.
    2. Immetti un nome dispositivo, come `my_device_type`, e una descrizione per il tipo di dispositivo.

        > **Nota:** il nome del tipo di dispositivo non deve avere una lunghezza superiore ai 36 caratteri e può contenere solo caratteri alfanumerici (a-z, A-Z, 0-9) e i seguenti caratteri: `_`, `.` e `-`.

    3. Facoltativo: immetti i metadati e gli attributi per il tipo dispositivo.

        Puoi aggiungere e modificare gli attributi e i metadati successivamente.
        {: tip}

4. Fai clic su **Next** per avviare il processo di aggiunta del tuo dispositivo con il tipo dispositivo.

5. Immetti un ID dispositivo, ad esempio `my_first_device`.

    L'ID dispositivo viene utilizzato per identificare il dispositivo nel dashboard {{site.data.keyword.iot_short_notm}} ed è anche un parametro obbligatorio per la connessione del tuo dispositivo a {{site.data.keyword.iot_short_notm}}.

    > **Nota:** il nome del tipo di dispositivo non deve avere una lunghezza superiore ai 36 caratteri e può contenere solo caratteri alfanumerici (a-z, A-Z, 0-9) e i seguenti caratteri: `_`, `.` e `-`.

    Per i dispositivi connessi alla rete, l'ID dispositivo può essere l'indirizzo MAC del dispositivo senza i caratteri due punti di separazione.

5. Fai clic su **Next** per completare il processo.

6. Fornisci un token di autenticazione o accetta un token generato automaticamente. Se scegli di creare un tuo token, assicurati che abbia un nome di lunghezza compresa tra gli 8 e i 36 caratteri e che contenga solo caratteri alfanumerici e i seguenti caratteri: `_`, `.`, `!`, `&`, `@`, `?`, `\*`, `+`, `(`, `)` e `-`.

    Il token non deve contenere sequenze di caratteri ripetuti, parole del dizionario, nomi utente o altre sequenze predefinite.

7. Verifica che le informazioni di riepilogo siano corrette e quindi fai clic su **Add** per aggiungere la connessione.

8. Nella pagina delle informazioni del dispositivo, copia e salva i seguenti dettagli:

    * ID organizzazione
    * Tipo dispositivo
    * ID dispositivo
    * Metodo di autenticazione
    * Token di autenticazione

    Ti serviranno l'ID organizzazione, il tipo di dispositivo, l'ID dispositivo e il token di autenticazione per configurare il tuo dispositivo per la connessione a {{site.data.keyword.iot_short_notm}}.

## Passo 2: connetti il tuo dispositivo a {{site.data.keyword.iot_short_notm}}
{: #step2 .sectiontitle}  

Dopo aver registrato il dispositivo con {{site.data.keyword.iot_short_notm}}, puoi utilizzare le informazioni registrate per collegare il dispositivo e avviare la ricezione dei dati.

**Suggerimento:** le ricette di connessione sono disponibili per alcuni dispositivi comunemente utilizzati in [Device connection recipes ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://developer.ibm.com/recipes/tutorials/category/internet-of-things-iot/){: new_window} su {{site.data.keyword.IBM_notm}}.com.

Per connettere un dispositivo a {{site.data.keyword.iot_short_notm}}:
1. Configura il tuo dispositivo per la messaggistica MQTT ed esegui l'autenticazione utilizzando l'ID organizzazione, il tipo di dispositivo, l'ID dispositivo e il token di autenticazione.

2. Invio dei messaggi del dispositivo alla tua organizzazione {{site.data.keyword.iot_short_notm}} utilizzando il protocollo MQTT.

    Le seguenti informazioni sono necessarie quando connetti il tuo dispositivo:

    * URL: *org_id*.messaging.internetofthings.ibmcloud.com

      Dove *org_id* è l'ID della tua organizzazione {{site.data.keyword.iot_short_notm}}.

    * Porta:
      * 1883
      * 8883 (crittografata)
      * 443 (socket web)
    * ID dispositivo: d:_id_organizzzione:tipo_dispositivo:id_dispositivo_
    * Nome utente: use-token-auth
    * Password: _Token di autenticazione_
    * Formato argomento evento: iot-2/evt/_id_evento/fmt/stringa_formato_

      Dove _id_evento_ specifica il nome evento visualizzato in {{site.data.keyword.iot_short_notm}} e _stringa_formato_ è il formato dell'evento, come ad esempio JSON.

    * Formato messaggio: JSON

  Per ulteriori informazioni, vedi [MQTT connectivity for devices ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/devices/mqtt.html){:new_window}.


## Operazioni successive  
{: #related .sectiontitle}

Estendi le funzioni di analisi dei dati creando e connettendo le tue applicazioni per utilizzare i dati del dispositivo.
- Per ulteriori informazioni su come collegare tipi di dispositivi specifici a {{site.data.keyword.iot_short_notm}}, consulta [developerWorks recipes ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://developer.ibm.com/recipes/tutorials/category/internet-of-things-iot/){:new_window}.
- Consulta le [librerie client ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/iot_platform_client_lib.html){:new_window} per gli strumenti per creare il codice per l'integrazione e la connessione dei tuoi dispositivi e delle tue applicazioni.
- Esplora la [documentazione API {{site.data.keyword.iot_short_notm}}](/docs/IoT/reference/api.html).
- [Connetti un servizio {{site.data.keyword.cloudantfull}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/cloudant_connector.html){:new_window} al tuo {{site.data.keyword.iot_short_notm}} per archiviare i dati del dispositivo cronologici.
- Per avvalerti dell'insieme di funzioni [{{site.data.keyword.iot_short_notm}} completo ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html){:new_window}, puoi acquistare uno dei piani Connection and Analytics Service e migrare quindi il tuo ambiente esistente.

Per migrare i piani, contatta il tuo rappresentante {{site.data.keyword.IBM}} oppure apri un ticket di supporto.

È anche disponibile una serie più dettagliata di guide introduttive e di applicazioni di esempio che guidano attraverso le basi dello sviluppo di un sistema prototipo IoT end-to-end pronto per la produzione con {{site.data.keyword.iot_short_notm}} nella documentazione del prodotto {{site.data.keyword.iot_short_notm}} nell'{{site.data.keyword.IBM_notm}} Knowledge Center. Se sei uno sviluppatore che non ha dimestichezza con l'utilizzo di {{site.data.keyword.iot_short_notm}}, utilizza i processi passo dopo passo nella sezione [Getting started guides ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/getting_started/getting-started-iot-overview.html#getting-started){:new_window}.
