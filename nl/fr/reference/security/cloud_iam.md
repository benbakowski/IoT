---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-22"

keywords: Cloud IAM Authentication, IAM OAuth token, IBM Watson

subcollection: iot-platform

---

{:new_window: target="\_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:important: .important}


# Authentification et autorisation de {{site.data.keyword.iamshort}} pour {{site.data.keyword.iot_short_notm}} (bêta)
{: #cloud_iam}

<p>Cette série de documents {{site.data.keyword.cloud}} concerne le plan de tarification {{site.data.keyword.iot_full}} Lite et inclut le guide d'initiation, les références d'API et les informations générales relatives au traitement des incidents.
Pour la documentation complète de la fonction {{site.data.keyword.iot_short_notm}}, voir la [documentation du produit {{site.data.keyword.iot_short_notm}} ![Icône de lien externe](../../../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/fr/SSQP8H/iot/overview/overview.html) dans l'{{site.data.keyword.IBM_notm}} Knowledge Center. Vous trouverez davantage d'informations sur les divers plans dans [{{site.data.keyword.iot_short_notm}}Plans de service](/docs/services/IoT?topic=iot-platform-plans_overview#plans_overview). 
</p>
{: important}

Les API {{site.data.keyword.iot_full}} prennent en charge l'authentification et l'autorisation des utilisateurs avec {{site.data.keyword.iamshort}} (IAM).

L'authentification et l'autorisation d'{{site.data.keyword.iamlong}} pour {{site.data.keyword.iot_short_notm}} est disponible uniquement dans le cadre d'un programme bêta limité. Il est possible que des mises à jour ultérieures incluent des modifications incompatibles avec la version en cours de cette fonction. Essayez-la et [dites-nous ce que vous en pensez ![Icône de lien externe](../../../../icons/launch-glyph.svg)](https://developer.ibm.com/answers/smart-spaces/17/internet-of-things.html){: new_window}.
{: important}

{{site.data.keyword.iamshort}} est intégré à {{site.data.keyword.cloud_notm}} et est utilisé pour authentifier et autoriser les administrateurs et les développeurs qui ont besoin de configurer et de gérer leurs services {{site.data.keyword.IBM_notm}}. Les utilisateurs qui doivent accéder au tableau de bord {{site.data.keyword.iot_short_notm}} sont authentifiés à l'aide de {{site.data.keyword.iamshort}}. La source d'identité de {{site.data.keyword.iamshort}} peut être une liste d'utilisateurs IBMid enregistrés ou un service de répertoire de clients prenant en charge SAML.  

{{site.data.keyword.iot_short_notm}} prend également en charge l'authentification des utilisateurs via {{site.data.keyword.appid_short_notm}}. {{site.data.keyword.appid_short_notm}} est utilisé pour authentifier les utilisateurs qui ont besoin d'accéder à des applications hébergées dans {{site.data.keyword.cloud_notm}}. En général, les utilisateurs d'{{site.data.keyword.appid_short_notm}} n'effectuent pas d'activités d'administration ou de développement dans un service cloud. Pour plus d'informations, voir [Authentification via l'{{site.data.keyword.appid_short_notm}} dans Watson IoT Platform ![Icône de lien externe](../../../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/fr/SSQP8H/iot/platform/app_id.html#app_id){: new_window}.

IAM permet aux utilisateurs d'obtenir un jeton OAuth IAM et de l'utiliser pour authentifier les appels API. Par exemple, un utilisateur qui dispose de l'interface de ligne de commande {{site.data.keyword.containershort_notm}} peut utiliser la commande suivante :

`bx iam oauth-tokens`

La commande renvoie le jeton IAM de l'utilisateur connecté au format suivant :

`IAM Token: Bearer <some token>`

Un utilisateur peut également utiliser le noeud final de jeton IAM pour se connecter et extraire son jeton IAM, comme illustré dans l'exemple suivant :
`curl -s 'https://iam.cloud.ibm.com/identity/token?grant_type=urn:ibm:params:oauth:grant-type:apikey&response_type=cloud_iam&apikey=<apikey>' -H'Content-Type:x-www-form-urlencoded' -XPOST`

Cet exemple d'API utilise une clé d'API IAM pour demander le jeton IAM et renvoie `Bearer <token>`. 

Ensuite, lorsqu'un utilisateur appelle une API {{site.data.keyword.iot_short_notm}}, il peut fournir l'en-tête d'autorisation `Authorization: Bearer <token>` dans ses appels API. 

## Génération d'un jeton IAM
{: #iam_generate}

Vous pouvez choisir le mode d'automatisation de la création du jeton IAM en fonction de la façon dont vous vous authentifiez auprès d'{{site.data.keyword.cloud_notm}} et du type d'ID {{site.data.keyword.cloud_notm}} que vous utilisez.

Si vous utilisez un ID non fédéré, vous pouvez choisir l'une des options suivantes pour créer un jeton IAM :
 - **Nom d'utilisateur et mot de passe {{site.data.keyword.cloud_notm}} :** vous pouvez créer un jeton pour automatiser entièrement la création de votre jeton d'accès IAM. 
 - **Générer une clé d'API {{site.data.keyword.cloud_notm}} :** utilisez des clés d'API {{site.data.keyword.cloud_notm}}, qui dépendent du compte {{site.data.keyword.cloud_notm}} pour lequel elles sont générées. Vous ne pouvez pas combiner votre clé d'API {{site.data.keyword.cloud_notm}} avec un autre ID de compte dans un même jeton IAM. Pour accéder aux clusters créés avec un compte autre que celui sur lequel votre clé d'API {{site.data.keyword.cloud_notm}} repose, vous devez vous connecter au compte pour générer une nouvelle clé d'API.

Si vous utilisez un ID fédéré, vous pouvez choisir l'une des options suivantes pour créer un jeton IAM :
 - **Générer une clé d'API {{site.data.keyword.cloud_notm}} : les clés d'API ** {{site.data.keyword.cloud_notm}} dépendent du compte {{site.data.keyword.cloud_notm}} pour lequel elles sont générées. Vous ne pouvez pas combiner votre clé d'API {{site.data.keyword.cloud_notm}} avec un autre ID de compte dans un même jeton IAM. Pour accéder aux clusters créés avec un compte autre que celui sur lequel votre clé d'API {{site.data.keyword.cloud_notm}} repose, vous devez vous connecter au compte pour générer une nouvelle clé d'API.
 - **Utiliser un code d'accès à un usage **: si vous vous authentifiez auprès d'{{site.data.keyword.cloud_notm}} à l'aide d'un code d'accès à usage unique, vous ne pouvez pas entièrement automatiser la création de votre jeton IAM car l'extraction de votre code d'accès à usage unique nécessite une interaction manuelle avec votre navigateur Web. Pour automatiser complètement la création de votre jeton IAM, vous devez créer une clé d'API {{site.data.keyword.cloud_notm}} à la place.

Lorsque vous créez votre jeton d'accès, les informations de corps incluses dans votre demande varient en fonction de la méthode d'authentification {{site.data.keyword.cloud_notm}} que vous utilisez. Remplacez les valeurs suivantes :
- `<my_username>` = votre nom d'utilisateur {{site.data.keyword.cloud_notm}}.
- `<my_password>` = votre mot de passe {{site.data.keyword.cloud_notm}}.
- `<my_api_key>` = votre clé d'API {{site.data.keyword.cloud_notm}}.
- `<my_passcode>` = votre code d'accès à usage unique {{site.data.keyword.cloud_notm}}. Exécutez `bx login --sso` et suivez les instructions figurant dans la sortie de l'interface de ligne de commande pour extraire votre code d'accès à usage unique à l'aide de votre navigateur Web.

Exemple :
`POST https://iam.<region>.cloud.ibm.com/identity/token`

Pour spécifier une région {{site.data.keyword.cloud_notm}}, passez en revue les abréviations de région utilisées sur les noeuds finaux de l'API. Pour plus d'informations, voir les [noeuds finaux d'API pour les régions {{site.data.keyword.cloud_notm}}![Icône de lien externe](../../../../icons/launch-glyph.svg)](https://cloud.ibm.com/docs/containers/cs_regions.html#bluemix_regions){: new_window}. 

Paramètre d'entrée	 | Valeurs
---------------- | -----------
En-tête	| Content-Type:application/x-www-form-urlencoded<br>Authorization: Basic Xng7Png=<br>Remarque : vous obtenez `Xng7Png=`, l'autorisation codée dans l'URL pour le nom d'utilisateur bx et le mot de passe bx.
Corps pour le nom d'utilisateur et le mot de passe {{site.data.keyword.cloud_notm}}	|	grant_type: password<br>response_type: cloud_iam, uaa<br>username: `<my_username>`<br>password: `<my_password>`<br>uaa_client_id: cf<br>uaa_client_secret:<br>Remarque : ajoutez la clé uaa_client_secret sans aucun valeur spécifiée.
Corps pour les clés d'API {{site.data.keyword.cloud_notm}}	|	grant_type: urn:ibm:params:oauth:grant-type:apikey<br>response_type: cloud_iam<br>uaa<br>apikey: `<my_api_key>`<br>uaa_client_id: cf<br>uaa_client_secret:<br>Remarque : ajoutez la clé uaa_client_secret sans aucun valeur spécifiée.
Corps pour le code d'accès à usage unique {{site.data.keyword.cloud_notm}}	|	grant_type: urn:ibm:params:oauth:grant-type:passcode<br>response_type: cloud_iam, uaa<br>passcode: `<my_passcode>`<br>uaa_client_id: cf<br>uaa_client_secret:<br>Remarque : ajoutez la clé uaa_client_secret sans aucun valeur spécifiée.

Exemple de sortie d'API :

```
{
"access_token": "<iam_token>",
"refresh_token": "<iam_refresh_token>",
"uaa_token": "<uaa_token>",
"uaa_refresh_token": "<uaa_refresh_token>",
"token_type": "Bearer",
"expires_in": 3600,
"expiration": 1493747503
}
```
Le jeton IAM figure dans la zone **access_token** de la sortie de votre API.

L'exemple suivant montre comment utiliser le jeton IAM lorsque vous appelez des API.

```
GET https://org.domain/api/v0002/bulk/devices
```

Paramètre d'entrée   |	Valeurs
----------------- | -----------
En-têtes	|	Content-Type: application/json<br>Authorization: bearer `<iam_token>`
