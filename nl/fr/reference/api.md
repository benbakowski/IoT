---

copyright:

years: 2017, 2019
lastupdated: "2019-04-16"

keywords: own organization, Extension HTTP APIs, API Use, AT&T Extension, Administer AT&T

subcollection: iot-platform

---

{:new_window: target="\_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:tip: .tip}
{:pre: .pre}
{:important: .important}


# API
{: #api_overview}

<p>Cette série de documents {{site.data.keyword.cloud}} concerne le plan de tarification {{site.data.keyword.iot_full}} Lite et inclut le guide d'initiation, les références d'API et les informations générales relatives au traitement des incidents.
Pour la documentation complète de la fonction {{site.data.keyword.iot_short_notm}}, voir [la documentation du produit {{site.data.keyword.iot_short_notm}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/fr/SSQP8H/iot/overview/overview.html) dans l'IBM Knowledge Center.  Vous trouverez davantage d'informations sur les divers plans dans [{{site.data.keyword.iot_short_notm}}Plans de service](/docs/services/IoT?topic=iot-platform-plans_overview#plans_overview). 
</p>
{: important}

Plusieurs API sont disponibles à des fins de développement de code pour les terminaux, les passerelles et les applications qui se connectent à {{site.data.keyword.iot_full}}.

Les API HTTP sont protégées grâce à l'authentification de base HTTP. Lorsque vous générez une clé d'API à l'aide du tableau de bord, une clé et un jeton d'authentification s'affichent. Pour plus d'informations sur les clés d'API et les jetons, voir [Connexion de clé d'API ![Icône de lien externe](../../../icons/launch-glyph.svg)](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/platform_authorization.html#api-key){: new_window}.


## A propos des API HTTP
{: #api_about}

Chaque organisation {{site.data.keyword.iot_short_notm}} est identifiée par un ID d'organisation à 6 caractères, qui est requis dans le nom d'hôte de n'importe quel appel API.   

### Documentation des API
{: #api_docs}

Pour visualiser la documentation des API, accédez à la page [IBM Watson IoT Platform REST APIs ![Icône de lien externe](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/index.html){: new_window}. Cette page d'arrivée permet d'accéder à la documentation des API {{site.data.keyword.iot_short_notm}} disponibles.

### Documentation interactive des API

Pour afficher et utiliser la documentation interactive des API, accédez à l'URL de base de votre organisation à l'adresse suivante :

`https://<orgId>.internetofthings.ibmcloud.com/docs/index.html`

Cette page d'arrivée permet d'accéder à la documentation des API {{site.data.keyword.iot_short_notm}} disponibles. Si vous souhaitez exécuter les appels API directement à partir de la documentation, vous devez disposer des droits d'accès appropriés.

Pour être automatiquement autorisé, procédez comme suit :

1. Connectez-vous au tableau de bord {{site.data.keyword.iot_short_notm}}.
2. Dans le même navigateur, ouvrez un nouvel onglet et accédez à la page d'arrivée de la documentation interactive des API.

Si vous n'êtes pas connecté au tableau de bord {{site.data.keyword.iot_short_notm}}, procédez comme suit :

1. Accédez à la page d'arrivée de la documentation interactive des API.
2. Sélectionnez `Authorize`.
3. Dans la boîte de dialogue `Available authorizations`, définissez le nom d'utilisateur sur la clé d'API et le mot de passe sur le jeton d'authentification. Sélectionnez `Authorize`.
4. Fermez la boîte de dialogue `Available authorizations`. **Important :** Ne sélectionnez pas `Logout`.

Une fois que vous êtes autorisé, accédez aux appels API spécifiques et cliquez sur le bouton `Try it out` pour les exécuter directement à partir de la documentation.

<!-- To authenticate requests to the application API, set the username to the API key and the password to the authentication token. -->
