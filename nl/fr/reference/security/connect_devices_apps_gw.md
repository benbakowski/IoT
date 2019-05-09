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

# Informations de connexion pour les applications, les terminaux et les passerelles
{: #connect_devices_apps_gw}

<p>Cette série de documents {{site.data.keyword.cloud}} concerne le plan de tarification {{site.data.keyword.iot_full}} Lite et inclut le guide d'initiation, les références d'API et les informations générales relatives au traitement des incidents.
Pour la documentation complète de la fonction {{site.data.keyword.iot_short_notm}}, voir la [documentation du produit {{site.data.keyword.iot_short_notm}} ![Icône de lien externe](../../../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/fr/SSQP8H/iot/overview/overview.html) dans l'IBM Knowledge Center. Vous trouverez davantage d'informations sur les divers plans dans [{{site.data.keyword.iot_short_notm}}Plans de service](/docs/services/IoT?topic=iot-platform-plans_overview#plans_overview). 
</p>
{: important}

Vous pouvez connecter des applications, des terminaux et des passerelles à {{site.data.keyword.iot_full}} en utilisant le protocole MQTT. Vous pouvez également utiliser l'API REST HTTP pour connecter des terminaux à {{site.data.keyword.iot_short_notm}}.
{: shortdesc}


## URL de connexion client
{: #client_connect_url}

Pour connecter des clients de terminal, d'application et de passerelle à votre instance {{site.data.keyword.iot_short_notm}}, utilisez les URL de connexion suivantes :

### Adresse de messagerie

<pre class="pre"><var class="keyword varname">orgId</var>.messaging.internetofthings.ibmcloud.com</pre>
{: codeblock}

### URL de connexion de l'API REST HTTP

<pre class="pre"><code class="hljs">https://<var class="keyword varname">orgId</var>.internetofthings.ibmcloud.com/api/v0002/device/types/<var class="keyword varname">typeId</var>/devices/<var class="keyword varname">deviceId</var>/events/<var class="keyword varname">eventId</var></code></pre>
{: codeblock}

**Remarques**
- Où *orgId* est l'ID d'organisation unique qui a été généré lorsque vous avez enregistré l'instance de service.
- Si vous connectez un terminal ou une application au service Quickstart, spécifiez 'quickstart' comme valeur *orgId*.

### Sécurité du port
{: #client_port_security}

Les terminaux, les passerelles et les applications se connectent à {{site.data.keyword.iot_short_notm}} avec le protocole MQTT ou HTTP. Les connexions peuvent être sécurisées ou non.

|Type de connexion |Protocole|Numéro de port|
|:---|:---|:---|
|Non sécurisée*|MQTT et HTTP|1883 ou 80|
|Sécurisée (TLS)|MQTT et HTTPS|8883 ou 443|

&ast; Les ports 1883 et 80 sont désactivés par défaut pour la messagerie. Pour des informations sur la modification du paramètre par défaut, voir [Configuration des politiques de sécurité ![Icône de lien externe](../../../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/fr/SSQP8H/iot/platform/reference/security/set_up_policies.html#set_up_policies.html){: new_window}.

MQTT est pris en charge via TCP et des WebSockets. Les clients MQTT se connectent en utilisant des données d'identification appropriées, telles que des jetons d'authentification pour les terminaux et des clés et des jetons d'API pour les applications. Etant donné que la messagerie MQTT via le port non sécurisé 1883 envoie ces données d'identification sous forme de texte brut, utilisez toujours les alternatives sécurisées 8883 ou 443 à la place. Les données d'identification TLS sont toujours chiffrées lorsqu'elles sont envoyées via des ports sécurisés. N'oubliez pas que vous devez activer TLS dans l'application (par exemple, en utilisant la méthode `tls_set()` dans la bibliothèque Python MQTT). A défaut, les données seront peut-être envoyées de manière non sécurisée.

Lorsque vous utilisez la messagerie MQTT sécurisée sur les ports 8883 ou 443, les bibliothèques client plus récentes font automatiquement confiance au certificat par défaut qui est présenté par {{site.data.keyword.iot_short_notm}}. Si ce n'est pas le cas pour votre environnement client, vous pouvez télécharger et utiliser la chaîne de certificats complète à partir de [messaging.pem ![Icône de lien externe](../../../../icons/launch-glyph.svg "Icône de lien externe")](https://github.com/ibm-watson-iot/iot-python/blob/master/src/wiotp/sdk/messaging.pem){: new_window}. Si vous avez téléchargé un certificat personnalisé, il peut être nécessaire de vérifier que la chaîne de confiance appropriée a été ajoutée à votre environnement client.

## Configuration du pare-feu
{: #firewall_configuration .sectiontitle}

Pour connecter des terminaux et des applications à {{site.data.keyword.iot_short_notm}}, vous devez vous assurer que votre éventuel pare-feu est configuré pour autoriser le trafic sur des ports spécifiques. Un pare-feu peut se trouver sur votre machine locale, sur votre routeur ou faire partie de votre réseau d'entreprise.

Assurez-vous que les adresses IP requises sont ouvertes et activées pour la communication.

|Région | Adresse IP|Ports de messagerie</br> (non sécurisés) | Ports de messagerie (sécurisés)|
|:---|:---|:---| :---|
|us-south|169.45.2.16/28* </br>169.46.7.56/29</br>169.48.234.208/29</br>169.62.202.128/29|1883,80 | 8883,443|
|eu-gb|159.8.169.208/28* </br>158.175.111.152/29</br>158.176.104.24/29</br>141.125.70.152/29|1883,80 | 8883,443|
|eu-de|159.122.121.80/28* </br>149.81.125.176/29</br>158.177.82.208/29</br>161.156.96.80/29|1883,80 | 8883,443|
|Quickstart|169.45.2.16/28* </br>169.46.7.56/29</br>169.48.234.208/29</br>169.62.202.128/29|1883,80 | non disponible|
|Dedicated {{site.data.keyword.iot_short_notm}}|Contactez votre interlocuteur {{site.data.keyword.IBM}}.|-| - |
&ast; N'est plus valable après le premier trimestre 2019.

## Exigences TLS
{: #tls_requirements}

Certaines bibliothèques client TLS (Transport Layer Security) ne prennent pas en charge les domaines qui incluent un caractère générique. Si vous ne pouvez pas changer les bibliothèques, désactivez la vérification des certificats.

Les exigences TLS varient selon que vous vous connectez à {{site.data.keyword.iot_short_notm}} avec le protocole MQTT ou HTTP. Les sections ci-après présentent les suites de chiffrement prises en charge si le
certificat de serveur par défaut est utilisé. Si vous utilisez votre propre certificat de client, les suites de chiffrement utilisables varient en fonction du certificat utilisé.

### Exigences TLS pour les connexions MQTT

{{site.data.keyword.iot_short_notm}} nécessite TLS v1.2. Vérifiez qu'au moins l'une des suites de chiffrement suivantes est autorisée :

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

### Exigences TLS pour les connexions HTTP

Si vous utilisez le certificat de serveur par défaut, {{site.data.keyword.iot_short_notm}} nécessite TLS v1.2. Vérifiez qu'au moins l'une des suites de chiffrement suivantes est autorisée :


- TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA
- TLS_DHE_RSA_WITH_AES_128_CBC_SHA
- TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA
- TLS_DHE_RSA_WITH_AES_256_CBC_SHA
- TLS_RSA_WITH_AES_256_CBC_SHA
- TLS_RSA_WITH_AES_128_CBC_SHA

Augmentez la puissance de votre chiffrement en utilisant les chiffrements de confidentialité persistante ECDHE ou DHE dans votre liste de chiffrements.

## Authentification client MQTT
{: #mqtt_authentication}

**Important :** chaque client MQTT requiert un ID de client unique. Si vous tentez de connecter un client dans votre organisation à l'aide d'un ID de client déjà connecté, la première connexion est déconnectée.

Les terminaux et les passerelles qui sont directement connectés à {{site.data.keyword.iot_short_notm}} affichent une icône de statut sur le tableau de bord pour indiquer qu'ils sont connectés. Les terminaux qui sont indirectement connectés via une passerelle sont affichés comme des terminaux étant déconnectés car le tableau de bord ne reconnaît pas les terminaux qui sont connectés via une passerelle.

### Identificateurs de client MQTT

Pour que les terminaux, les applications et les passerelles puissent s'authentifier, définissez chaque client MQTT en utilisant les identificateurs de client et le format suivants :

|Type de client |ID|Format d'ID MQTT|
|:---|:---|:---|
|Applications|a|<pre class="pre">a:<var class="keyword varname">orgId</var>:<var class="keyword varname">appId</var></pre>
|Applications évolutives|A|<pre class="pre">A:<var class="keyword varname">orgId</var>:<var class="keyword varname">appId</var></pre>
|Terminaux|d|<pre class="pre">d:<var class="keyword varname">orgId</var>:<var class="keyword varname">deviceType</var>:<var class="keyword varname">deviceId</var></pre>|
|Passerelles|g|<pre class="pre">g:<var class="keyword varname">orgId</var>:<var class="keyword varname">typeId</var>:<var class="keyword varname">deviceId</var></pre>|

Où
- *orgId* est l'ID d'organisation unique composé de six caractères qui a été généré lorsque vous avez enregistré le chaîne.
- *appId* est un identificateur de chaîne unique défini par l'utilisateur pour le client.
- *deviceId* identifie un terminal ou une passerelle de façon unique parmi tous les types de terminal et de passerelle, et s'apparente à un numéro de série.
- *device_type* est l'identificateur du type de terminal qui se connecte, et s'apparente à un numéro de modèle.
- *typeId* est l'identificateur du type de passerelle qui se connecte, et s'apparente à un numéro de modèle.

Les valeurs pour *appId*, *type_id*, *device_type* et *device_id* ne doivent pas dépasser 36 caractères et ne peuvent contenir que les caractères suivants :
- Caractères alphanumériques (a-z, A-Z, 0-9)
- Tirets (-)
- Traits de soulignement (_)
- Points (. )

**Remarques :**
- Lorsque vous vous connectez au service Quickstart, l'authentification n'est pas obligatoire.
- Vous n'avez pas besoin d'enregistrer une application avant de vous connecter.

Pour des informations sur le format des abonnements partagés, voir [Connectivité MQTT pour les applications ![Icône de lien externe](../../../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/fr/SSQP8H/iot/platform/applications/mqtt.html){: new_window}.


### Connexion d'applications à l'aide de MQTT

Les applications {{site.data.keyword.iot_short_notm}} requièrent une clé d'API pour se connecter à une organisation. Lorsqu'une clé d'API est enregistrée, un jeton est généré et doit être utilisé avec cette clé d'API.

Le code suivant fournit un exemple de clé d'API :

<pre class="pre">a-<var class="keyword varname">orgId</var>-a84ps90Ajs</pre>
{: codeblock}

L'exemple suivant illustre un jeton d'authentification standard :

```
 MP$08VKz!8rXwnR-Q*
```

Lorsque vous établissez une connexion MQTT à l'aide d'une clé d'API, assurez-vous de respecter les exigences suivantes :

- L'ID de client MQTT doit être au format suivant : a:*orgId*:*appId*
- Le nom d'utilisateur MQTT doit correspondre à la clé d'API, par exemple, a-*orgId*-a84ps90Ajs
- Le mot de passe MQTT doit correspondre au jeton d'authentification, par exemple, *MP$08VKz!8rXwnR-Q**

Pour plus d'informations, voir [Connectivité MQTT pour les applications ![Icône de lien externe](../../../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/fr/SSQP8H/iot/platform/applications/mqtt.html){: new_window}.

### Authentification de terminal

#### Noms d'utilisateur
Le service {{site.data.keyword.iot_short_notm}} ne prend en charge que l'authentification basée sur un jeton pour les terminaux ; par conséquent, chaque terminal ne possède qu'un seul nom d'utilisateur valide.
La valeur `use-token-auth` indique au service que le jeton d'authentification pour la passerelle ou le terminal est utilisé comme mot de passe pour la connexion MQTT.

Pour plus d'informations, voir [Connectivité MQTT pour les terminaux ![Icône de lien externe](../../../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/fr/SSQP8H/iot/platform/devices/mqtt.html){: new_window}.

#### Mots de passe
Si le client utilise l'authentification basée sur un jeton, soumettez le jeton d'authentification de terminal comme mot de passe pour toutes les connexions MQTT.
