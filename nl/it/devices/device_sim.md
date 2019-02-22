---

copyright:
  years: 2017, 2019
lastupdated: "2019-02-13"
---

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

<p>Questa raccolta di documentazione {{site.data.keyword.Bluemix}} è relativa al piano dei prezzi {{site.data.keyword.iot_full}} Lite e include le informazioni introduttive di base, le guide di riferimento API e delle informazioni generali per la risoluzione dei problemi.
Per la documentazione completa della funzione {{site.data.keyword.iot_short_notm}}, vedi la [documentazione del prodotto {{site.data.keyword.iot_short_notm}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html) nell'IBM Knowledge Center. Ulteriori informazioni sui vari piani sono disponibili in [Piani di servizio {{site.data.keyword.iot_short_notm}}](/docs/IoT/plans_overview.html#plans_overview). 
</p>
{: important}

Utilizzando il simulatore del dispositivo {{site.data.keyword.iot_full}}, puoi configurare gli eventi simulati per i dispositivi. Puoi anche utilizzare i dati dell'evento simulato per informazioni, verifica e per dimostrare la funzionalità completa delle funzioni {{site.data.keyword.iot_short_notm}}.
{: shortdesc}

Puoi utilizzare i dispositivi e i tipi di dispositivo esistenti e il simulatore ti abilita a generare nuovi dispositivi per i tipi esistenti. Puoi configurare i dettagli dell'evento di ogni dispositivo o impostare una configurazione predefinita che si applica a tutti i dispositivi. Puoi esportare una configurazione dell'evento simulata in modo che possa essere riutilizzata o condivisa per configurare altre simulazioni.

Per simulare i dati del dispositivo:

1. Accedi a {{site.data.keyword.iot_short_notm}}.
2. Dal pannello di navigazione principale, seleziona **Settings**.
3. Nella sezione **Data and Devices**, attiva il simulatore del dispositivo.
4. Dal pannello di navigazione principale, seleziona **Devices**. Un messaggio nell'angolo destro in basso della schermata indica che nessun simulatore è in esecuzione.
5. Fa clic sul messaggio "0 Simulations running".
6. Nella finestra a comparsa **Simulations**, fai clic su **Create Simulation**.
7. Seleziona un tipo di dispositivo esistente per cui desideri simulare i dati oppure crea un nuovo tipo di dispositivo immettendo il nome del tipo di dispositivo.
8. Fai clic su **Import/Export Simulation** per utilizzare una configurazione esistente oppure configura manualmente i dettagli della simulazione per il tipo di dispositivo:
   1. Fai clic su **+ New Event Type** per aggiungere un tipo di evento al tipo di dispositivo.
   2. Immetti un nome per il tipo di evento.
   3. In **Schedule**, imposta la frequenza dell'evento.
   3. Modifica i dettagli del tipo di evento nel formato JSON e salva il tipo di evento aggiornato.

   <p> Puoi utilizzare le seguenti variabili speciali quando configuri gli eventi:  
        - `range`:  questa variabile viene sostituita da un numero casuale compreso tra i due valori forniti, ad esempio: `{"random": range(300, 100)}`  
        - `$counter`: questa variabile viene sostituita dal numero di dispositivi aggiunti nel simulatore per il tipo corrente, ad esempio: `{"total": $counter}`  
        - `increment`: questa variabile indica il numero iniziale e l'incremento in base al quale aumenta, ad esempio: `{"myNumber": increment(10, 1)}`. In questo caso, `myNumber` inizia da 10 e aumenta di 1 ogni volta che viene inviato un payload (10, 11, 12 e così via).</p>
   {: tip}

9. Seleziona un dispositivo registrato per la simulazione oppure crea un nuovo dispositivo immettendo il nome dispositivo.
10. Per creare più simulazioni, fai clic su **New Simulation** e ripeti i passi di configurazione per ciascun dispositivo a cui desideri applicare le impostazioni personalizzate. Il messaggio in basso a destra nella schermata mostra il numero di simulazioni attive.
11. **Facoltativo:** dopo aver configurato le simulazioni dei dispositivi, esportane i dettagli in modo che possano essere riutilizzati o condivisi:
    1. Nella finestra a comparsa **Simulations**, fai clic su **Import/Export**.
    2. Seleziona la scheda **Export**.
    3. Copia i dettagli della simulazione negli appunti o scaricali in un file JSON.
12. Nella pagina **Devices**, scegli uno dei dispositivi simulati e seleziona la scheda **Recent Events** per verificare che gli eventi simulati funzionino.
