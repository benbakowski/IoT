---

copyright:
  years: 2015, 2019
lastupdated: "2019-04-05"

keywords: Client connection URLs, MQTT protocol, device authentication tokens

subcollection: iot-platform

---

{:new_window: target="\_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}
{:pre: .pre}
{:important: .important}

# Informazioni di connessione per le applicazioni, i dispositivi e i gateway
{: #connect_devices_apps_gw}

<p>Questa raccolta di documentazione {{site.data.keyword.cloud}} è relativa al piano dei prezzi {{site.data.keyword.iot_full}} Lite e include le informazioni introduttive di base, le guide di riferimento API e delle informazioni generali per la risoluzione dei problemi.
Per la documentazione completa della funzione {{site.data.keyword.iot_short_notm}}, vedi la [documentazione del prodotto {{site.data.keyword.iot_short_notm}} ![Icona link esterno](../../../../icons/launch-glyph.svg "icona link esterno")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/overview/overview.html) nell'IBM Knowledge Center. Ulteriori informazioni sui vari piani sono disponibili in [Piani di servizio {{site.data.keyword.iot_short_notm}}](/docs/services/IoT?topic=iot-platform-plans_overview#plans_overview). 
</p>
{: important}

Puoi connettere applicazioni, dispositivi e gateway a {{site.data.keyword.iot_full}} utilizzando il protocollo MQTT. Puoi anche utilizzare l'API REST HTTP per collegare i dispositivi a {{site.data.keyword.iot_short_notm}}.
{: shortdesc}


## URL di connessione client
{: #client_connect_url}

Per collegare i client dispositivo, applicazione e gateway alla tua stanza {{site.data.keyword.iot_short_notm}}, utilizza le seguenti connessioni URL:

### Indirizzo di messaggistica

<pre class="pre"><var class="keyword varname">orgId</var>.messaging.internetofthings.ibmcloud.com</pre>
{: codeblock}

### API REST HTTP per l'URL di connessione

<pre class="pre"><code class="hljs">https://<var class="keyword varname">orgId</var>.internetofthings.ibmcloud.com/api/v0002/device/types/<var class="keyword varname">typeId</var>/devices/<var class="keyword varname">deviceId</var>/events/<var class="keyword varname">eventId</var></code></pre>
{: codeblock}

**Note
**
- Dove *orgId* è l'ID dell'organizzazione univoco generato quando hai registrato l'istanza del servizio.
- Se stai collegando un dispositivo o un'applicazione al servizio Quickstart, specifica 'quickstart' per il valore *orgId*.

### Porta di sicurezza
{: #client_port_security}

Dispositivi, gateway e applicazioni si connettono a {{site.data.keyword.iot_short_notm}} utilizzando il protocollo MQTT o quello HTTP. Le connessioni possono essere non protette o protette.

|Tipo di connessione |Protocollo|Numero di porta|
|:---|:---|:---|
|Non protetta*|MQTT e HTTP|1883 o 80|
|Protetta (TLS)|MQTT e HTTPS|8883 o 443|

&ast; Le porte 1883 e 80 sono disabilitate per impostazione predefinita per la messaggistica. Per informazioni sulla modifica dell'impostazione predefinita, vedi [Configuring security policies ![Icona link esterno](../../../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/reference/security/set_up_policies.html#set_up_policies.html){: new_window}.

MQTT è supportato per TCP e i socket web. I client MQTT si collegano utilizzando le credenziali appropriate, come i token di autenticazione del dispositivo per i dispositivi e i token e le chiavi API per le applicazioni. Poiché la messaggistica MQTT nella porta non sicura 1883 invia tali credenziali in testo semplice, utilizza invece sempre le alternative sicure 8883 o 443. Le credenziali TLS sono sempre crittografate quando vengono inviate su porte sicure. Tieni presente che devi abilitare TLS nell'applicazione (ad es. utilizzando il metodo `tls_set()` nella libreria MQTT Python). Altrimenti, i dati potrebbero essere inviati in modo non sicuro.

Quando utilizzi la messaggistica MQTT sicura sulle porte 8883 o 443, le librerie client più recenti ritengono attendibile automaticamente il certificato predefinito presentato da {{site.data.keyword.iot_short_notm}}. Se non è questo il caso per il tuo ambiente client, puoi scaricare e utilizzare la catena di certificati completa da [messaging.pem ![Icona link esterno](../../../../icons/launch-glyph.svg "Icona link esterno")](https://github.com/ibm-watson-iot/iot-python/blob/master/src/wiotp/sdk/messaging.pem){: new_window}. Se hai caricato un certificato personalizzato, è possibile che tu debba assicurati che al tuo ambiente client venga aggiunta la catena di attendibilità appropriata.

## Configurazione del firewall
{: #firewall_configuration .sectiontitle}

Per connettere dispositivi e applicazioni a {{site.data.keyword.iot_short_notm}}, devi assicurarti che un eventuale firewall sia configurato per consentire il traffico su porte specifiche. Un firewall può trovarsi sulla tua macchina locale, sul tuo router o come parte della tua rete aziendale.

Assicurati che gli indirizzi IP richiesti siano aperti e abilitati per la comunicazione.

|Regione | Indirizzo IP|Porte di messaggistica</br> (non protette) | Porte di messaggistica (protette)|
|:---|:---|:---| :---|
|us-south|169.45.2.16/28* </br>169.46.7.56/29</br>169.48.234.208/29</br>169.62.202.128/29|1883,80 | 8883,443|
|eu-gb|159.8.169.208/28* </br>158.175.111.152/29</br>158.176.104.24/29</br>141.125.70.152/29|1883,80 | 8883,443|
|eu-de|159.122.121.80/28* </br>149.81.125.176/29</br>158.177.82.208/29</br>161.156.96.80/29|1883,80 | 8883,443|
|Quickstart|169.45.2.16/28* </br>169.46.7.56/29</br>169.48.234.208/29</br>169.62.202.128/29|1883,80 | non disponibile|
|{{site.data.keyword.iot_short_notm}} dedicato|Contatta il tuo rappresentante {{site.data.keyword.IBM}}.|-| - |
&ast; Non più utilizzato dopo il primo trimestre del 2019.

## Requisiti TLS
{: #tls_requirements}

Alcune librerie client TLS (Transport Layer Security) non supportano i domini che includono un carattere jolly. Se non puoi modificare correttamente le librerie, disabilita il controllo del certificato.

I tuoi requisiti TLS dipendono se ti stai connettendo {{site.data.keyword.iot_short_notm}} utilizzando il protocollo MQTT o HTTP. Le seguenti sezioni mostrano le suite di crittografia supportate se viene utilizzato il certificato server predefinito. Se stai utilizzando il tuo proprio certificato,
le suite di crittografia supportate dipendono dal certificato utilizzato.

### Requisiti TLS per le connessioni MQTT

{{site.data.keyword.iot_short_notm}} richiede TLS v1.2. Assicurati che sia consentita almeno una delle seguenti suite di crittografia:

- TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256
- TLS_DHE_RSA_WITH_AES_128_GCM_SHA256
- TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA
- TLS_DHE_RSA_WITH_AES_128_CBC_SHA
- TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384
- TLS_DHE_RSA_WITH_AES_256_GCM_SHA384
- TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA
- TLS_DHE_RSA_WITH_AES_256_CBC_SHA
- TLS_RSA_WITH_AES_128_GCM_SHA256
- TLS_RSA_WITH_AES_256_GCM_SHA384

### Requisiti TLS per le connessioni HTTP

Se stai utilizzando il certificato server predefinito, {{site.data.keyword.iot_short_notm}} richiede TLS v1.2. Assicurati che sia consentita almeno una delle seguenti suite di crittografia:


- TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA
- TLS_DHE_RSA_WITH_AES_128_CBC_SHA
- TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA
- TLS_DHE_RSA_WITH_AES_256_CBC_SHA
- TLS_RSA_WITH_AES_256_CBC_SHA
- TLS_RSA_WITH_AES_128_CBC_SHA

Aumenta l'efficacia della tua codifica utilizzando i forward secrecy ECDHE o DHE nel tuo elenco di crittografie.

## Autenticazione client MQTT
{: #mqtt_authentication}

**Importante:** ogni client MQTT richiede un ID client univoco. Se tenti di collegare un client alla tua organizzazione utilizzando un ID client che è già collegato, la prima connessione viene scollegata.

I dispositivi e i gateway collegati direttamente a {{site.data.keyword.iot_short_notm}} visualizzano un'icona di stato sul dashboard che indica che sono collegati. I dispositivi che sono collegati indirettamente tramite un gateway vengono mostrati come scollegati perché il dashboard non è a conoscenza dei dispositivi collegati tramite un gateway.

### Identificativi client MQTT

Per i dispositivi, le applicazioni e i gateway correttamente autenticati, definisci ogni client MQTT utilizzando il seguente formato e identificativi client:

|Tipo di client |ID|Formato ID MQTT|
|:---|:---|:---|
|Applicazioni|a|<pre class="pre">a:<var class="keyword varname">orgId</var>:<var class="keyword varname">appId</var></pre>
|Applicazioni scalabili|A|<pre class="pre">A:<var class="keyword varname">orgId</var>:<var class="keyword varname">appId</var></pre>
|Dispositivi|d|<pre class="pre">d:<var class="keyword varname">orgId</var>:<var class="keyword varname">deviceType</var>:<var class="keyword varname">deviceId</var></pre>|
|Gateway|g|<pre class="pre">g:<var class="keyword varname">orgId</var>:<var class="keyword varname">typeId</var>:<var class="keyword varname">deviceId</var></pre>|

Dove
- *orgId* è l'ID dell'organizzazione a sei caratteri univoco generato quando hai registrato il servizio.
- *appId* è un identificativo stringa univoco definito dall'utente per il client.
- *deviceId* identifica univocamente un dispositivo o un gateway tra tutti i tipi ed è simile a un numero di serie.
- *device_type* è l'identificativo del tipo dispositivo collegato ed è simile al numero di modello.
- *typeId* è un identificativo del tipo di gateway collegato ed è simile al numero di modello.

I valori *appId*, *type_id*, *device_type* e *device_id* non devono essere maggiori di 36 caratteri e possono contenere solo:
- Caratteri alfanumerici (a-z, A-Z, 0-9)
- Trattini ( - )
- Caratteri di sottolineatura ( _ )
- Punti ( . )

**Note:**
- Quando ti colleghi al servizio Quickstart, l'autenticazione non è richiesta.
- Non hai bisogno di registrare un'applicazione prima del collegamento.

Per informazioni sul formato delle sottoscrizioni condivise, vedi [MQTT connectivity for applications ![Icona link esterno](../../../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/applications/mqtt.html){: new_window}.


### Connessione delle applicazioni utilizzando MQTT

Le applicazioni {{site.data.keyword.iot_short_notm}} richiedono una chiave API per collegarsi in un'organizzazione. Quando viene registrata una chiave API, viene generato un token, che deve essere utilizzato con tale chiave API.

Il seguente codice fornisce un esempio di una chiave API:

<pre class="pre">a-<var class="keyword varname">orgId</var>-a84ps90Ajs</pre>
{: codeblock}

Il seguente esempio mostra un token di autenticazione tipico:

```
 MP$08VKz!8rXwnR-Q*
```

Quando effettui una connessione MQTT utilizzando una chiave API, assicurati di rispettare i seguenti requisiti:

- L'ID client MQTT deve essere nel seguente formato: a:*orgId*:*appId*
- Il nome utente MQTT è la chiave API, ad esempio, a-*orgId*-a84ps90Ajs
- La password MQTT è il token di autenticazione, ad esempio *MP$08VKz!8rXwnR-Q**

Per ulteriori informazioni, vedi [MQTT connectivity for applications ![Icona link esterno](../../../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/applications/mqtt.html){: new_window}.

### Autenticazione del dispositivo

#### Nomi utente
Il servizio {{site.data.keyword.iot_short_notm}} supporta solo le autenticazioni basate sui token per i dispositivi; quindi, ogni dispositivo ha solo un nome utente valido.
Un valore di `use-token-auth` indica al servizio che viene utilizzato il token di autenticazione per il gateway o per il dispositivo come password per la connessione MQTT.

Per ulteriori informazioni, vedi [MQTT connectivity for devices ![Icona link esterno](../../../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/devices/mqtt.html){: new_window}.

#### Password
Se il client sta utilizzando l'autenticazione basata sul token, inoltra il token di autenticazione del dispositivo come password per tutte le connessioni MQTT.
