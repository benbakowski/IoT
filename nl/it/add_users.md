---

copyright:
  years: 2016, 2019
lastupdated: "2019-02-13"

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:important: .important}

# Gestione dell'accesso utente
{: #managing-user-access}

<p>Questa raccolta di documentazione {{site.data.keyword.Bluemix}} è relativa al piano dei prezzi {{site.data.keyword.iot_full}} Lite e include le informazioni introduttive di base, le guide di riferimento API e delle informazioni generali per la risoluzione dei problemi.
Per la documentazione completa della funzione {{site.data.keyword.iot_short_notm}}, vedi la [documentazione del prodotto {{site.data.keyword.iot_short_notm}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html) nell'IBM Knowledge Center. Ulteriori informazioni sui vari piani sono disponibili in [Piani di servizio {{site.data.keyword.iot_short_notm}}](/docs/IoT/plans_overview.html#plans_overview). 
</p>
{: important}

Dalla pagina Member del dashboard, puoi controllare e gestire l'accesso alla tua organizzazione {{site.data.keyword.iot_full}}. Puoi aggiungere gli utenti aggiungendoli, invitandoli o importandoli. Puoi anche fornire diversi livelli di accesso ai tuoi utenti assegnando dei ruoli.
{:shortdesc}

## Aggiunta di utenti
{: #adding-new-users}

Dalla pagina **Members** del dashboard, puoi aggiungere singoli membri utilizzando la funzione di aggiunta. Puoi anche aggiungere membri contemporaneamente utilizzando la funzione di importazione.

Per impostazione predefinita, gli account dei membri non scadono. Quando aggiungi utenti alla tua organizzazione {{site.data.keyword.iot_short_notm}}, puoi facoltativamente impostare una data di scadenza per il loro account.

### Aggiunta di membri alla tua organizzazione {{site.data.keyword.iot_short_notm}}

Per aggiungere un membro alla tua organizzazione, avrai bisogno dell'ID IBM del membro. Per aggiungere un membro, non hai bisogno della conferma da parte del membro.

Per aggiungere un solo membro alla tua organizzazione {{site.data.keyword.iot_short_notm}}:
1. Nel tuo dashboard {{site.data.keyword.iot_short_notm}}, fai clic su **Members** dalla barra di navigazione.
2. Fai clic su **Add Members** e seleziona la scheda **Add**.
3. Immetti l'ID IBM del membro.
4. Seleziona un ruolo per il membro.
5. Facoltativo: imposta una data di scadenza.
6. Fai clic su **Add**.

Per aggiungere più membri contemporaneamente, devi caricare un file `.csv` che contiene l'ID IBM, il ruolo e la data di scadenza facoltativa per ogni membro. Per informazioni, consulta [Messa a punto del tuo file CSV](#constructing-your-csv).
1. Nel tuo dashboard {{site.data.keyword.iot_short_notm}}, fai clic su **Members** dalla barra di navigazione.
2. Fai clic su **Add Members** e seleziona la scheda **Import**.
3. Fai clic sui tuoi file o trascina il file `.csv` nella finestra **Upload CSV**.
4. Seleziona un ruolo predefinito da utilizzare se non viene riconosciuto un ruolo specificato nel file CSV.
5. Associa i numeri di colonna nel tuo file CSV alle voci di ID IBM, ruolo e data di scadenza facoltativa corrispondenti.
6. Seleziona il separatore di colonna punto e virgola o virgola che corrisponde al separatore utilizzato nel tuo file `.csv`.
7. Fai clic su **Import** per importare gli ID IBM e creare i membri.


### Messa a punto del tuo file CSV
{: #constructing-your-csv}

Quando metti a punto un file CSV per importare i membri nella tua organizzazione, assicurati di includere le informazioni obbligatorie per il metodo che stai utilizzando. Utilizza le virgole o i punti e virgola per separare le colonne.  
**Importante:** quando carichi il file CSV, in **CSV settings**, assicurati di selezionare il separatore di colonna corretto.

File CSV di esempio con la delimitazione con virgola:  
```
user1@sample.com,PD_DEVELOPER_USER,2018-03-13
user2@sample.com,PD_OPERATOR_USER,2018-03-13
user3@sample.com,PD_ADMIN_USER,2018-03-13
```
Dove vengono utilizzate le seguenti voci di colonna:  
- Colonna 1: l'indirizzo email dell'utente.  
Se stai aggiungendo dei membri, assicurati di utilizzare l'indirizzo email che corrisponde a un ID IBM valido. Se stai invitando i membri, puoi utilizzare qualsiasi indirizzo email valido.
- Colonna 2: il ruolo che deve essere assegnato all'utente.  
Immetti uno dei seguenti ruoli:
 - PD_ADMIN_USER
 - PD_OPERATOR_USER
 - PD_DEVELOPER_USER
 - PD_ANALYST_USER
 - PD_READER_USER  
 Per ulteriori informazioni sui ruoli utente, vedi [User, application, and gateway roles ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/roles_index.html#user_roles){: new_window}.
- Colonna 3: la data ISO 6801 (ad esempio, `2018-03-13`) che corrisponde alla data di scadenza dell'utente.

## Modifica degli utenti
{: #editing-users}

Gli utenti possono modificare il proprio ruolo, aggiungere, rimuovere o modificare una data di scadenza di accesso, oppure aggiungere o rimuovere l'accesso all'organizzazione.

1. Nel tuo dashboard {{site.data.keyword.iot_short_notm}}, fai clic su **Members** dalla barra di navigazione.
2. Fai clic sull'icona **Edit** accanto all'utente che desideri modificare.
3. Apporta le modifiche desiderate all'utente.
4. Fai clic su **Save**.

## Blocco dell'accesso utenti
{: #blocking-users}

Gli utenti possono essere bloccati dall'accedere all'organizzazione {{site.data.keyword.iot_short_notm}}, mentre ancora mantengono l'appartenenza all'organizzazione.

1. Nel tuo dashboard {{site.data.keyword.iot_short_notm}}, fai clic su **Members** dalla barra di navigazione.
2. Fai clic sull'attivazione accanto all'utente che desideri bloccare dall'accedere all'organizzazione {{site.data.keyword.iot_short_notm}}.

## Limitazione dell'accesso utente
{: #limiting-users}

Il controllo dell'accesso a livello delle risorse ti consente di limitare l'accesso ai dispositivi in un'organizzazione. Puoi utilizzare i gruppi di risorse per specificare i dispositivi che ogni utente o chiave API possono gestire. Per ulteriori informazioni su come configurare un controllo dell'accesso a livello delle risorse, vedi [Configuring resource-level access control ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/reference/rlac.html#configure_RLAC){: new_window}.

## Rimozione di utenti
{: #removing-users}

Gli utenti possono essere rimossi completamente dall'organizzazione {{site.data.keyword.iot_short_notm}}. La rimozione degli utenti non può essere annullata e gli utenti devono essere [aggiunti alla piattaforma](#adding-new-users) per ripristinare l'accesso.

1. Nel tuo dashboard {{site.data.keyword.iot_short_notm}}, fai clic su **Members** dalla barra di navigazione.
2. Fai clic sull'icona **Delete** accanto all'utente da rimuovere.
3. Fai clic su **Delete** nella finestra di dialogo di conferma.
