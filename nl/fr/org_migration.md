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

# Migration de {{site.data.keyword.iot_short_notm}} Lite vers {{site.data.keyword.iot_short_notm}} dans un environnement hors production ou de production 
{: #org_migration}

<p>Cette série de documents {{site.data.keyword.Bluemix}} concerne le plan de tarification {{site.data.keyword.iot_full}} Lite et inclut le guide d'initiation, les références d'API et les informations générales relatives au traitement des incidents. Pour la documentation complète de la fonction {{site.data.keyword.iot_short_notm}}, voir [la documentation du produit {{site.data.keyword.iot_short_notm}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/fr/SSQP8H/iot/overview/overview.html) dans l'{{site.data.keyword.IBM}} Knowledge Center. Vous trouverez davantage d'informations sur les divers plans dans [Plans de service {{site.data.keyword.iot_short_notm}}](/docs/IoT/plans_overview.html#plans_overview). </p>
{: important}

Après vous être initié à Watson IoT Platform avec le plan Lite et une fois que vous avez compris sa place dans votre environnement IoT, vous pouvez procéder à la mise à niveau vers [Watson IoT Platform dans un environnement hors production ou vers l'un des plans de production ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/fr/SSQP8H/iot/overview/overview.html){: new_window}.
{:shortdesc}

**Remarque :** ce document s'adresse uniquement aux utilisateurs qui possèdent une instance Lite. Si vous avez déjà créé des instances IoT Platform avec les plans Standard ou Advanced Security, {{site.data.keyword.IBM}} vous aidera à migrer votre instance existante de {{site.data.keyword.iot_short_notm}} vers le nouveau plan hors production ou de production. 

## Présentation du processus de migration
{: #org_migration_overview}

En migrant vers {{site.data.keyword.iot_short_notm}}, vous supprimez la limite du plan Lite de 500 terminaux et de consommation mensuelle de données. 

Les plans {{site.data.keyword.iot_short_notm}} incluent les composants supplémentaires suivants, qui prennent en charge l'architecture d'application IoT de bout en bout : 

- {{site.data.keyword.messagehub}} - version hébergée par {{site.data.keyword.IBM_notm}} de la plateforme de diffusion en flux Kafka que votre application peut utiliser pour recevoir des données IoT. 
- {{site.data.keyword.dashdbshort}} pour le stockage des données d'analyse. 
- Base de données {{site.data.keyword.cloudantfull}} pour les données de séries temporelles. 
- {{site.data.keyword.cos_full}} pour la conservation de données à long terme. 

Ce document décrit les types de données que vous pouvez migrer depuis une instance Lite existante vers une version complète. 

**Remarque :** en général, il est plus facile de configurer votre environnement {{site.data.keyword.iot_short_notm}} hors production ou de production à partir de zéro, car celui-ci inclut des composants et des fonctions qui ne font pas partie du service {{site.data.keyword.iot_short_notm}} Lite. De plus, les terminaux et les utilisateurs créés pour le test dans la version Lite ne seront probablement pas ceux que vous utiliserez pour la production. 

Toutefois, si vous voulez transférer certains de vos paramètres Lite existants, les sections ci-après vous guideront tout au long du processus. 

La documentation sur les [API {{site.data.keyword.iot_short_notm}}](/docs/IoT/reference/api.html#api_overview) explique comment appeler les API et leur ensemble complet de paramètres. 


## Avant de commencer
{: #org_migration_byb}

Pour pouvoir démarrer le processus de migration, vous devez acheter {{site.data.keyword.iot_short_notm}} (pour un environnement de production ou hors production). Lors de votre achat, l'équipe {{site.data.keyword.IBM_notm}} chargée des opérations met à votre disposition une nouvelle instance {{site.data.keyword.iot_short_notm}}. Celle-ci inclut un nouvel ID d'organisation alphanumérique à six caractères. 


## Migration des utilisateurs
{: #user_migration}

[Les API de gestion des utilisateurs ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/security.html#!/Authorization_-_User_Management){: new_window} permettent l'exportation et l'importation en bloc des utilisateurs {{site.data.keyword.iot_short_notm}} et peuvent être utilisées pour exporter et importer les utilisateurs que vous voulez conserver dans votre nouvelle organisation. 

1. Exportez les utilisateurs depuis l'organisation Lite.   
Utilisez la commande `GET /authorization/users` pour exporter tous vos utilisateurs depuis votre organisation de compte Lite en tant qu'objet JSON. 
2. Nettoyez la liste des utilisateurs.   
Si nécessaire, éditez la structure JSON pour retirer les utilisateurs que vous ne voulez pas migrer dans votre nouvelle organisation. 
3. Importez les utilisateurs dans la nouvelle organisation.   
Utilisez la commande `POST /authorization/users/multiple` pour importer la liste JSON éditée d'utilisateurs dans la nouvelle organisation. 

A présent, les utilisateurs ont accès à la nouvelle organisation, qui apparaît dans le sélecteur d'organisations dans le tableau de bord {{site.data.keyword.iot_short_notm}}. 

##  Migration des terminaux   
{: #device_migration}

Vous pouvez migrer les terminaux comme suit :   
1. Migrez les types de terminal que vous voulez conserver dans la nouvelle organisation.   
2. Migrez les terminaux eux-mêmes dans la nouvelle organisation.   
3. Mettez à jour le nom d'hôte que les terminaux utilisent pour se connecter à {{site.data.keyword.Bluemix_short}} afin d'utiliser votre nouvel ID d'organisation. 
4. Migrez les éventuelles informations de gestion des données que vous avez créées sur la plateforme Lite.    
Il peut s'agir d'interfaces logiques et physiques de terminal, d'objets et de règles. 

<p>Les types de terminal et les terminaux peuvent être migrés en bloc avec les API suivantes :
<table>
<tr>
<th> Documentation d'API </th>
<th> API d'exportation </th>
<th> API d'importation </th>
</tr>
<tr>
<td> [API de type de terminal ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/org-admin.html) </td>
<td> `GET /device/types` </td>
<td> `POST /device/types` </td>
</tr>
<tr>
<td>  [API de terminal ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/org-admin.html#!/Device_Bulk_Configuration) </td>
<td> `GET /bulk/devices` </td>
<td>  `POST /bulk/devices/add`</td>
</tr>
</table>
</p>
{: tip}


**Important :** {{site.data.keyword.iot_short_notm}} ne stocke pas les jetons d'authentification de terminal, mais uniquement leur version avec sel de cryptage. Par conséquent, l'appel `GET /bulk/devices` ne peut pas renvoyer les jetons d'authentification pour les terminaux stockés. Si vous disposez d'un enregistrement des jetons d'authentification de terminal, vous pouvez ajouter les jetons d'authentification à l'objet JSON avant de procéder au chargement en bloc. Sinon, vous devez générer de nouveaux jetons d'authentification de terminal pour chaque terminal et les copier sur les terminaux.   

Si vous utilisez des certificats de terminal pour authentifier les terminaux plutôt que des jetons d'authentification, cette tâche n'est pas nécessaire. Toutefois, si vous utilisez des certificats de terminal, vous devez télécharger les certificats qui ont été utilisés, afin de les signer dans la nouvelle organisation. 


## Mise à jour des terminaux 
{: #update_devices}

Lorsque vos terminaux sont enregistrés dans la nouvelle organisation, vous devez mettre à jour la configuration ou le code présent sur chaque terminal existant en vue de l'utilisation du nom d'hôte de la nouvelle organisation. 

Pour les clients de messagerie MQTT et HTTP, utilisez le nom d'hôte suivant :   
`<orgId>.messaging.internetofthings.ibmcloud.com`

Faites pointer les clients d'API REST sur le nom d'hôte suivant :   
`<orgId>.internetofthings.ibmcloud.com`

**Important :** si vous avez généré de nouveaux jetons d'authentification pour vos terminaux, vous devez les copier sur chaque terminal. 


## Migration de la gestion des terminaux 
{: #device_management}

Les [API de gestion des données ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/state-mgmt.html){: new_window} incluent des API pour l'exportation et l'importation d'interfaces logiques et physiques de terminal, de définitions d'objet et de règles. 

**Important :** actuellement, {{site.data.keyword.iot_short_notm}} ne prend pas en charge le concept des actifs jumeaux pour l'ingestion de données. 

## Tableaux et cartes 
{: #boards_cards}

{{site.data.keyword.iot_short_notm}} n'inclut pas d'API pour l'importation et l'exportation des définitions et des personnalisations des tableaux et des cartes. Vous devez recréer ces dernières manuellement dans la nouvelle organisation. 

## Activation des extensions requises 
{: #extensions}

Vous devez recréer les extensions que vous avez activées sur la plateforme Lite, comme les liens vers {{site.data.keyword.messagehub}}, {{site.data.keyword.cloudant_short_notm}} et Jasper, dans la nouvelle organisation. 

## Migration des applications
{: #application_migration}

Si vous avez développé des applications qui appellent des API proposées avec le service {{site.data.keyword.iot_short_notm}} Lite, par exemple pour envoyer ou recevoir des données, ou pour administrer le service, vous devez les mettre à jour pour qu'elles utilisent une instance {{site.data.keyword.iot_short_notm}} de production ou hors production. Cette exigence est également valable pour les flux Node-RED que vous utilisez.
La migration implique : 
- La mise à jour des applications pour qu'elles utilisent un nouvel ID d'organisation à six caractères. 
- La mise à jour des applications pour qu'elles utilisent la clé d'API et les données d'identification de jeton que vous avez créées pour votre nouvelle instance de service. 

**Important :** si vous utilisez une liaison Cloud Foundry pour transmettre l'ID d'organisation et les données d'identification à l'application, vous devez utiliser un autre mécanisme car la nouvelle instance {{site.data.keyword.iot_short_notm}} n'est pas mise à disposition en vue de son exécution dans votre espace Cloud Foundry. 

### Génération de données d'identification de connexion d'API 

Le processus de migration à suivre dépend de la nature de votre application. En général, dans tous les cas, la première étape consiste à acquérir une clé d'API et un jeton d'authentification que votre application devra utiliser. 

1. Connectez-vous au tableau de bord principal de votre nouveau service {{site.data.keyword.iot_short_notm}}. 
2. Sélectionnez l'onglet **Utilisation**. 
3. Cliquez sur le lien **Afficher les détails** pour afficher les informations sur le service {{site.data.keyword.iot_short_notm}}.   
Les informations suivantes sont affichées :
   - L'ID d'organisation à six caractères 
   - La clé d'API et le jeton   
   Il est recommandé de générer de nouvelles clés d'API pour chacune de vos applications au lieu d'utiliser la clé d'API affichée ici. Ainsi, vous pouvez définir les droits appropriés pour chaque application. 
   - L'URL de l'hôte. 
4. Créez une combinaison de clé d'API et de jeton d'authentification pour votre application.  
Vous aurez besoin de ces éléments lorsque vous configurerez l'application pour qu'elle se connecte à votre organisation.    
   1.  Cliquez sur `Lancer`.  
   Le tableau de bord du service sous-jacent que vous avez utilisé pour administrer le service {{site.data.keyword.iot_short_notm}} Lite s'ouvre. 
   2. Sélectionnez **Applications**.
   3. Cliquez sur **Générer une clé d'API**
   4. Copiez les valeurs de la clé d'API et du jeton d'authentification qui sont affichées.
   5. Sélectionnez un rôle approprié à votre application.    
   6. Ajoutez un commentaire pour pouvoir identifier facilement cette combinaison de clé d'API et de jeton d'authentification.
   7. Cliquez sur **Générer**.
   8. **Important :** effectuez une copie locale du jeton d'authentification. Celui-ci ne peut pas être recréé une fois que vous avez fermé la fenêtre. 


### Mise à jour d'une application Node-RED 
Vous devez configurer vos noeuds Node-RED pour la connexion à votre nouvelle instance {{site.data.keyword.iot_short_notm}}. Vos noeuds `ibmiot` ne pourront plus utiliser l'option d'authentification `BluemixService` ; par conséquent, vous devez sélectionner l'option `Clé d'API` à la place. 
1. Ouvrez le noeud `ibmiot` pour l'éditer. 
2. Dans les propriétés du noeud, sélectionnez **Clé d'API**.
3. Cliquez sur l'icône d'édition à côté de la zone Clé d'API, puis entrez la clé d'API et le jeton d'authentification que vous avez sauvegardés à l'étape précédente. 
4. Sauvegardez vos modifications et redéployez votre flux Node-RED. 

### Mise à jour d'une application qui n'utilise pas de liaison Cloud Foundry 
Identifiez l'emplacement dans lequel votre application stocke l'ID d'organisation, la clé d'API et le jeton d'authentification, et remplacez ces éléments par les valeurs que vous avez sauvegardées précédemment. 

Si votre application utilise l'un des logiciels SDK de {{site.data.keyword.iot_short_notm}}, ces valeurs se trouvent probablement dans un fichier de propriétés.
{: tip}

### Mise à jour d'une application qui utilise une liaison Cloud Foundry 

{{site.data.keyword.Bluemix_short}} fournit un mécanisme qui permet de lier des applications Cloud Foundry à un ou plusieurs services Cloud Foundry. Vous pouvez établir les liaisons via l'interface de ligne de commande {{site.data.keyword.Bluemix_short}} ou en créant une `connexion` entre l'application et le service dans le tableau de bord {{site.data.keyword.Bluemix_short}}. 

Lorsqu'une application est liée à un service, les données d'identification (clé d'API et jeton d'authentification) du service sont copiées dans la variable d'environnement `VCAP_SERVICES` depuis l'emplacement à partir duquel l'application peut les extraire. 

**Important :** ce mécanisme de liaison ne peut pas être utilisé avec le nouveau service {{site.data.keyword.iot_short_notm}}. Vous devez trouver dans votre application le code qui procède à la lecture depuis `VCAP_SERVICES` et le remplacer par le code qui lit les valeurs depuis l'emplacement dans lequel vous stockez désormais la clé d'API et le jeton d'authentification. Pour terminer la mise à jour, vous devez régénérer et redéployer votre application. 
