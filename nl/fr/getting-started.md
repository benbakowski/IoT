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


# Tutoriel d'initiation
{: #getting-started .task}

<p>Cette série de documents {{site.data.keyword.Bluemix}} concerne le plan de tarification {{site.data.keyword.iot_full}} Lite et inclut le guide d'initiation, les références d'API et les informations générales relatives au traitement des incidents.
Pour la documentation complète de la fonction {{site.data.keyword.iot_short_notm}}, voir [la documentation du produit {{site.data.keyword.iot_short_notm}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/fr/SSQP8H/iot/overview/overview.html) dans l'IBM Knowledge Center. Vous trouverez davantage d'informations sur les divers plans dans [Plans de service {{site.data.keyword.iot_short_notm}}](/docs/IoT/plans_overview.html#plans_overview).
</p>
{: important}

Dans ce tutoriel d'initiation à {{site.data.keyword.iot_short_notm}}, nous connectons un terminal IoT à {{site.data.keyword.iot_short_notm}}.
{:shortdesc}

## A propos de cette tâche
{: #about .sectiontitle}  

Avant de pouvoir commencer à recevoir des données depuis vos terminaux IoT, vous devez connecter vos terminaux à {{site.data.keyword.iot_short_notm}}. La connexion d'un terminal à {{site.data.keyword.iot_short_notm}} implique son enregistrement auprès de {{site.data.keyword.iot_short_notm}} et l'utilisation des informations d'enregistrement pour configurer le terminal afin qu'il se connecte à {{site.data.keyword.iot_short_notm}}.

## Avant de commencer
{: #byb .sectiontitle}  

Pour pouvoir commencer à utiliser {{site.data.keyword.iot_short_notm}}, vous devez disposer des éléments suivants :   
* Un compte [{{site.data.keyword.Bluemix}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net/registration/){: new_window}.
* Une instance {{site.data.keyword.iot_short_notm}}.   
Vous pouvez créer une instance {{site.data.keyword.iot_short_notm}} directement depuis la [page {{site.data.keyword.iot_short_notm}} dans le catalogue des services {{site.data.keyword.Bluemix_short}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/catalog/services/internet-of-things-platform/){:new_window}.  
* Un terminal qui remplit les exigences suivantes :   
  *	Votre terminal doit pouvoir communiquer à l'aide des protocoles HTTP ou MQTT.
  * Les messages du terminal doivent remplir les exigences relatives à la charge de message {{site.data.keyword.iot_short_notm}}.  
Pour plus d'informations, voir [Développement de terminaux sur {{site.data.keyword.iot_short_notm}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/fr/SSQP8H/iot/platform/devices/device_dev_index.html){: new_window}.

Explorez les options suivantes en fonction de votre situation : 

 |  |   Le service est déployé | Le service n'est pas déployé
 | -------------| ------------- | -------------
  |**J'ai un terminal à connecter** | Suivez le processus présenté dans cette rubrique. | Explorez la connexion de terminal dans la [démonstration Play with {{site.data.keyword.iot_short_notm}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://discover-iot.eu-gb.mybluemix.net/?cm_mc_uid=44491599487314618721024&cm_mc_sid_50200000=1462798151#/play){:new_window}.
  |**Je n'ai pas de terminal à connecter** | [Simulez des données de terminal](/docs/IoT/devices/device_sim.html) ou [connectez votre smartphone ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://discover-iot.eu-gb.mybluemix.net/?cm_mc_uid=44491599487314618721024&cm_mc_sid_50200000=1462798151#/play/device/smartphone){:new_window}. | Initiez-vous avec le [module de démarrage {{site.data.keyword.iot_short_notm}}](https://console.bluemix.net/docs/IoT-starter/iot500.html#gettingstartedtemplate){:new_window}.



## Etape 1 : enregistrez votre terminal
{: #step1 .sectiontitle}  
L'enregistrement d'un terminal implique de le classifier sous un type de terminal, de lui attribuer un nom et de fournir des informations le concernant. Vous indiquez ensuite un jeton de connexion ou acceptez un jeton qui est généré par {{site.data.keyword.iot_short_notm}}.

**Astuce :** vous pouvez enregistrer vos terminaux un à un depuis le [tableau de bord {{site.data.keyword.iot_short_notm}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe ")](https://internetofthings.ibmcloud.com){: new_window}, ou utiliser l'[API {{site.data.keyword.iot_short_notm}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/org-admin.html#!/Device_Bulk_Configuration/post_bulk_devices_add){: new_window} pour ajouter plusieurs terminaux simultanément. 

Pour ajouter un terminal depuis le tableau de bord {{site.data.keyword.iot_short_notm}} :
1. Dans la console {{site.data.keyword.Bluemix_notm}}, cliquez sur **Lancer** dans la page des détails du service {{site.data.keyword.iot_short_notm}}.

    La console web {{site.data.keyword.iot_short_notm}} s'ouvre dans un nouvel onglet de navigateur à l'URL suivante :

    ```
    https://org_id.internetofthings.ibmcloud.com/dashboard/#/overview
    ```

    Où *org_id* est l'ID de votre organisation {{site.data.keyword.iot_short_notm}}.

2. Dans le tableau de bord Présentation, à partir du panneau de menu, sélectionnez **Terminaux**, puis cliquez sur **Ajouter un terminal**.

3. Créez un type de terminal pour le terminal que vous ajoutez.

    Chaque terminal connecté à {{site.data.keyword.iot_short_notm}} doit être associé à un type de terminal. Les types de terminal sont des groupes de terminaux ayant des caractéristiques communes.

    1. Cliquez sur **Créer un type de terminal**.
    2. Entrez un nom de type de terminal, par exemple, `my_device_type`, et une description pour
le type de terminal.

        > **Remarque :** le nom du type de terminal ne doit pas comporter plus de 36 caractères et ne peut contenir que des caractères alphanumériques (a-z, A-Z, 0-9) et les caractères suivants : `_`, `.`, `-`.

    3. Facultatif : entrez des métadonnées et des attributs de type de terminal.

        Vous pourrez ajouter et éditer des attributs et des métadonnées ultérieurement.
        {: tip}

4. Cliquez sur **Suivant** pour commencer le processus d'ajout de votre terminal avec le type de terminal sélectionné.

5. Entrez un ID de terminal, par exemple, `my_first_device`.

    L'ID de terminal permet d'identifier le terminal dans le tableau de bord {{site.data.keyword.iot_short_notm}}. Il constitue
aussi un paramètre indispensable à la connexion de votre terminal à {{site.data.keyword.iot_short_notm}}.

    > **Remarque :** le nom du type de terminal ne doit pas comporter plus de 36 caractères et ne peut contenir que des caractères alphanumériques (a-z, A-Z, 0-9) et les caractères suivants : `_`, `.`, `-`.

    Pour les terminaux connectés à un réseau, l'ID de chaque terminal peut être son adresse MAC sans les signes deux-points de séparation.

5. Cliquez sur **Suivant** pour finaliser le processus.

6. Fournissez un jeton d'authentification ou acceptez un jeton généré automatiquement. Si vous choisissez de créer votre propre jeton, assurez-vous qu'il comporte entre 8 et 36 caractères et qu'il ne contient que des caractères alphanumériques et les caractères suivants : `_`, `.`, `!`, `&`, `@`, `?`, `\*`, `+`, `(`, `)` et `-`.

    Le jeton ne doit pas contenir de séquences de caractères répétés, de mots du dictionnaire, de noms d'utilisateur ni d'autres séquences prédéfinies.

7. Vérifiez que les informations récapitulatives sont correctes, puis cliquez sur **Ajouter** pour ajouter la connexion.

8. Dans la page Informations sur le terminal, copiez et sauvegardez les détails suivants :

    * ID d'organisation
    * Type de terminal
    * ID de terminal
    * Méthode d'authentification 
    * Jeton d'authentification

    Vous aurez besoin d'un ID d'organisation, d'un type de terminal, d'un ID de terminal et d'un jeton d'authentification pour configurer votre terminal afin qu'il se connecte à {{site.data.keyword.iot_short_notm}}.

## Etape 2 : connectez votre terminal à {{site.data.keyword.iot_short_notm}}
{: #step2 .sectiontitle}  

Après avoir enregistré un terminal auprès de {{site.data.keyword.iot_short_notm}}, vous pouvez utiliser les informations d'enregistrement pour connecter le terminal et commencer à recevoir des données de terminal.

**Astuce :** des recettes de connexion sont disponibles pour certains terminaux couramment utilisés à l'adresse [Device connection recipes ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://developer.ibm.com/recipes/tutorials/category/internet-of-things-iot/){: new_window} sur le site {{site.data.keyword.IBM_notm}}.com.

Pour connecter un terminal à {{site.data.keyword.iot_short_notm}} :
1. Configurez votre terminal pour la messagerie MQTT et de sorte qu'il puisse s'authentifier avec
l'ID d'organisation, le type de terminal, l'ID de terminal et le jeton d'authentification.

2. Envoyez des messages du terminal à votre organisation {{site.data.keyword.iot_short_notm}} en utilisant le protocole MQTT.

    Les informations suivantes sont requises lors de la connexion de votre terminal :

    * URL : *org_id*.messaging.internetofthings.ibmcloud.com

      Où *org_id* est l'ID de votre organisation {{site.data.keyword.iot_short_notm}}.

    * Port :
      * 1883
      * 8883 (chiffré)
      * 443 (websockets)
    * ID de terminal : d:_org_id:device_type:device_id_
    * Nom d'utilisateur : use-token-auth
    * Mot de passe : _jeton d'authentification_
    * Format de sujet d'événement : iot-2/evt/_event_id/fmt/format_string_

      Où _event_id_ spécifie le nom d'événement affiché dans {{site.data.keyword.iot_short_notm}} et _format_string_ est le format de l'événement, par exemple, JSON.

    * Format de message : JSON

  Pour plus d'informations, voir [Connectivité MQTT pour les terminaux ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/fr/SSQP8H/iot/platform/devices/mqtt.html){:new_window}.


## Etapes suivantes  
{: #related .sectiontitle}

Etendez les fonctions d'analyse de données en créant et en connectant vos propres applications afin qu'elles consomment des données de terminal. 
- Pour plus d'informations sur la connexion de types de terminal spécifiques à {{site.data.keyword.iot_short_notm}}, voir les [recettes developerWorks ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://developer.ibm.com/recipes/tutorials/category/internet-of-things-iot/){:new_window}.
- Consultez les [bibliothèques client ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/fr/SSQP8H/iot/platform/iot_platform_client_lib.html){:new_window} en quête d'outils de construction du code pour l'intégration et la connexion de vos terminaux et de vos applications. 
- Explorez la [documentation d'API {{site.data.keyword.iot_short_notm}}](/docs/IoT/reference/api.html).
- <dMD:A HREF="https://www.ibm.com/support/knowledgecenter/fr/SSQP8H/iot/platform/cloudant_connector.html">Connectez un service {{site.data.keyword.cloudantfull}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe"){:new_window} à votre instance {{site.data.keyword.iot_short_notm}} pour stocker les données de terminal historiques. 
- Pour bénéficier de l'[ensemble de fonctions {{site.data.keyword.iot_short_notm}} complet ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/fr/SSQP8H/iot/overview/overview.html){:new_window}, vous pouvez acheter l'un des plans Connection and Analytics Service, puis migrer votre environnement existant. 

Pour migrer des plans, contactez votre interlocuteur {{site.data.keyword.IBM}} ou ouvrez un ticket de demande de service. 

Un ensemble plus détaillé de guides d'initiation et de modèles d'application permettant de découvrir les bases du développement d'un prototype Iot de bout en bout prêt à être utilisé en production avec {{site.data.keyword.iot_short_notm}} est également disponible dans la documentation du produit {{site.data.keyword.iot_short_notm}}, dans l'{{site.data.keyword.IBM_notm}} Knowledge Center. Si vous êtes novice en développement avec {{site.data.keyword.iot_short_notm}}, utilisez les processus détaillés dans la section [Guides d'initiation ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/fr/SSQP8H/iot/platform/getting_started/getting-started-iot-overview.html#getting-started){:new_window}. 
