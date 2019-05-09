---

copyright:
  years: 2017, 2019
lastupdated: "2019-04-05"

keywords: device simulator, devices

subcollection: iot-platform

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:important: .important}


# Simulazione dei dati del dispositivo
{: #sim_device_data}

<p>Questa raccolta di documentazione {{site.data.keyword.cloud}} è relativa al piano dei prezzi {{site.data.keyword.iot_full}} Lite e include le informazioni introduttive di base, le guide di riferimento API e delle informazioni generali per la risoluzione dei problemi.
Per la documentazione completa della funzione {{site.data.keyword.iot_short_notm}}, vedi la [documentazione del prodotto {{site.data.keyword.iot_short_notm}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html) nell'IBM Knowledge Center. Ulteriori informazioni sui vari piani sono disponibili in [Piani di servizio {{site.data.keyword.iot_short_notm}}](/docs/services/IoT?topic=iot-platform-plans_overview#plans_overview). 
</p>
{: important}

Utilizza il simulatore del dispositivo {{site.data.keyword.iot_full}} per configurare gli eventi simulati per i dispositivi per acquisire informazioni, verificare e illustrare le funzioni {{site.data.keyword.iot_short_notm}} pienamente funzionanti senza dover registrare e collegare i dispositivi effettivi.
{: shortdesc}

Utilizzando il simulatore del dispositivo, puoi creare dispositivi simulati per i tipi di dispositivi esistenti oppure puoi creare nuovi dispositivi e tipi di dispositivo. Ogni dispositivo simulato può utilizzare dettagli dell'evento univoci, ma puoi anche creare una configurazione predefinita che viene applicata a tutti i dispositivi. 

## Prima di cominciare
{: #byb-simulation .sectiontitle}
Abilita la simulazione del dispositivo per il tuo ID utente. 
1. Accedi a {{site.data.keyword.iot_short_notm}}.
2. Dal pannello di navigazione principale, seleziona **Settings**.
3. Nella sezione **Data and Devices**, attiva il simulatore del dispositivo.

Se la simulazione del dispositivo è abilitata per il tuo ID utente, tutti i dispositivi simulati abilitati vengono avviati automaticamente quando accedi al dashboard {{site.data.keyword.iot_short_notm}}.

## Simulazione dei dispositivi
{: #process-simulation .sectiontitle}
Quando attivato, il simulatore del dispositivo è disponibile su tutte le pagine del dashboard. Un messaggio nell'angolo in basso a destra della schermata indica il numero di simulazioni in esecuzione. 

**Importante:** i tipi di dispositivo e i dispositivi simulati che definisci per il tuo ID utente sono disponibili per tutti gli altri utenti dell'organizzazione {{site.data.keyword.iot_short_notm}}. Tuttavia, per generare i dati simulati per i tuoi dispositivi, devi essere collegato al dashboard {{site.data.keyword.iot_short_notm}} in una sessione utente attiva. 

Per simulare i dati del dispositivo:
1. Dal dashboard {{site.data.keyword.iot_short_notm}}, fai clic sul messaggio "0 Simulations running".
3. Nella finestra di configurazione **Simulations** che viene aperta, fai clic su **Create Simulation**.
4. Configura i dettagli della simulazione.  
Fai clic su **Import/Export Simulation** per importare una [configurazione esistente](#reuse) oppure per configurare manualmente i dettagli:
   1. Seleziona un tipo di dispositivo esistente per cui desideri simulare i dati oppure crea un nuovo tipo di dispositivo immettendo il nome del tipo di dispositivo.
   2. Modifica il nome predefinito per il tipo di evento. 
   3. In **Schedule**, imposta la frequenza dell'evento.
   4. Modifica il payload dell'evento.  
   Modifica il payload JSON di esempio aggiungendo le proprietà e i relativi valori corrispondenti oppure utilizza le [funzioni](#functions) per aggiungere i punti dati generati dinamicamente.   
   Puoi anche caricare un [file del payload dell'evento CSV](#csv) per configurare il payload.  
   {: tip}
5. Fai clic su **New Event Type** per aggiungere e configurare più tipi di evento per il tipo di dispositivo. 
5. Abilita **Save events as historical data** per rendere i tuoi dati sullo stato del dispositivo simulato disponibili per un accesso successivo.   
Con i dati cronologici abilitati, vengono creati i componenti per la {{site.data.keyword.iot_short_notm}} [gestione dei dati ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/GA_information_management/ga_im_definitions.html){: new_window} ed è possibile accedere allo stato del dispositivo simulato dall'interfaccia logica associata.  
**Importante:** dopo aver abilitato il tipo di dispositivo per salvare i dati cronologici, non puoi aggiungere o rimuovere i tipi di evento, né puoi modificare i campi presenti nei payload dell'evento.
5. Fai clic su **Save** per creare il tipo di dispositivo.   
Ora sei pronto per creare uno o più dispositivi simulati.
6. Fai clic su **Create Simulated Device** per creare un dispositivo e iniziare a inviare i dati.   
**Suggerimento:** per creare più di un dispositivo, fai clic su **1 x** e seleziona il numero di dispositivi da creare.   
7. Per creare più simulazioni, fai clic su **New Simulation** e ripeti i passi di configurazione per ciascun dispositivo a cui desideri applicare le impostazioni personalizzate.   
Il messaggio nell'angolo in basso a destra della schermata mostra il numero di simulazioni attive. 
8. Nella pagina **Devices**, scegli uno dei dispositivi simulati e seleziona la scheda **Recent Events** per verificare che gli eventi simulati funzionino.

Puoi [esportare le tue configurazioni dell'evento simulato](#reuse) per il riutilizzo o la condivisione. 

## Funzioni del tipo di evento
{: #functions .sectiontitle}

Puoi utilizzare un numero di funzioni speciali per creare dati dinamici per i tuoi tipi di evento. 

Funzione | Utilizzo | Esempio  
:--- | :---  | :--  
`random(lower, upper)`  | Genera un numero casuale nell'intervallo specificato.  | `{"random": random(0, 100)}`  
`$counter` | Visualizza il numero di dispositivi simulati del tipo corrente. | `{"total": $counter}`  
`increment(start, increment)` | Specifica il valore iniziale e l'incremento con il quale aumenta. |`{"myNumber": increment(10, 1)}` </br> In questo esempio, `myNumber` inizia con 10 e aumenta di 1 ogni volta che viene inviato un payload.


## File del payload dell'evento CSV
{: #csv .sectiontitle}

Se vuoi creare i dati evento controllati per determinati scenari, puoi configurare il flusso di dati in un file di input CSV. 

### Requisiti
Il file CSV deve soddisfare i seguenti requisiti:
- Ciascun valore è una [primitiva JSON ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://json.org){: new_window} valida, ad eccezione di quanto indicato:
  - stringa:   
  Esempio: "Hello world"
  - numero:  
  Esempio: 0, 0.1, -22, -2.43
  - booleano:  
  true o false
  - null:  
  null
  - **Non supportato:**
    - oggetti  
    Esempio: {}
    - array  
    Esempio: []
- I valori devono essere delimitati da virgole. 
- Le righe devono essere delimitate utilizzando il carattere di nuova riga (`\n`).
- La riga di intestazione deve essere composta solo da valori stringa. 


### File CSV di esempio
```
"temperature", "confidence","status"
1, 0.1, "normal"
2, 0.2, "normal"
3, 0.3, "error"
4, 0.4, "normal"
```

La prima riga o "riga di intestazione" determina le proprietà incluse nel JSON del dispositivo in tutti gli oggetti dell'evento JSON del dispositivo generati.
Ogni riga successiva o "riga di dati" imposta il valore di tali proprietà in ogni oggetto dell'evento JSON del dispositivo generato. 

**Suggerimento:** quando importi il file CSV, puoi selezionare **Loop simulated data from file** per scorrere le righe di dati in sequenza per ottenere un feed di dati continuo. Se questa attivazione non è configurata, ogni riga di dati nel CSV viene inviata una volta con la frequenza impostata dalla pianificazione. 

Il file CSV di esempio genera file payload dell'evento del seguente tipo: 
```JSON
{
  "temperature": 1,
  "confidence": 0.1,
  "status": "normal"
}
```

## Condivisione e riutilizzo delle simulazioni
{: #reuse .sectiontitle}

Puoi esportare i tuoi dettagli della simulazione per il riutilizzo o la condivisione: 
1. Nella finestra **Simulations**, fai clic su **Import/Export**.
2. Seleziona la scheda **Export**.
3. Copia i dettagli della simulazione negli appunti o scaricali in un file JSON.
