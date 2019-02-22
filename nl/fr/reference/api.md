---

copyright:

years: 2017, 2019
lastupdated: "2019-02-13"

---

{:new_window: target="\_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:important: .important}


# API
{: #api_overview}

<p>Cette série de documents {{site.data.keyword.Bluemix}} concerne le plan de tarification {{site.data.keyword.iot_full}} Lite et inclut le guide d'initiation, les références d'API et les informations générales relatives au traitement des incidents.
Pour la documentation complète de la fonction {{site.data.keyword.iot_short_notm}}, voir [la documentation du produit {{site.data.keyword.iot_short_notm}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/fr/SSQP8H/iot/overview/overview.html) dans l'IBM Knowledge Center. Vous trouverez davantage d'informations sur les divers plans dans [Plans de service {{site.data.keyword.iot_short_notm}}](/docs/IoT/plans_overview.html#plans_overview).
</p>
{: important}

Plusieurs API sont disponibles à des fins de développement de code pour les terminaux, les passerelles et les applications qui se connectent à {{site.data.keyword.iot_full}}.

Les API HTTP sont protégées avec l'authentification de base HTTP. Lorsque vous générez une clé d'API à l'aide du tableau de bord, une clé et un jeton d'authentification s'affichent. Pour plus d'informations sur les clés d'API et les jetons, voir [Connexion de clé d'API ![Icône de lien externe](../../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/fr/SSQP8H/iot/platform/platform_authorization.html#api-key). 


## A propos des API HTTP
{: #api_about}

Après vous être enregistré auprès de votre propre organisation, vous recevez un ID d'organisation composé de six caractères, qui est requis dans le nom d'hôte pour tout appel API HTTP. L'URL de base de votre organisation est accessible à l'adresse suivante :

https://<**orgId**>.internetofthings.ibmcloud.com/api/v0002

Pour authentifier les demandes envoyées à l'API d'application, affectez la clé d'API au nom d'utilisateur et le jeton d'authentification au mot de passe.

Pour les API de messagerie, utilisez l'adresse suivante :

https://<**orgId**>.messaging.internetofthings.ibmcloud.com/api/v0002

## API HTTP
{: #api_http}

API                     | A utiliser pour...       
------------- | -------------
[Administration des organisations![Icône de lien externe](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/orgAdmin.html){: new_window} | Configurer une organisation (y compris créer et supprimer des terminaux), vérifier l'utilisation, consulter le statut de service, et diagnostiquer les problèmes de connexion.
[Sécurité ![Icône de lien externe](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/security.html){: new_window} | Gérer l'authentification et les autorisations des utilisateurs, des clés d'interface de programmation et des terminaux.
[Gestion des informations ![Icône de lien externe](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/info-mgmt.html){: new_window} |  Accéder aux données d'événement de terminal, ainsi qu'obtenir et mettre à jour des emplacements de terminal et obtenir des informations météorologiques pour ces emplacements. 
[Gestion des données  ![Icône de lien externe](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/state-mgmt.html){: new_window}   |   Organiser et intégrer les données en provenance et en direction de {{site.data.keyword.iot_short_notm}}.
[Gestion des terminaux ![Icône de lien externe](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/deviceMgmt.html){: new_window} | Interagir avec des terminaux gérés à l'aide du protocole de gestion des terminaux.
[Messagerie ![Icône de lien externe](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/http-messaging.html){: new_window}   | Publier des événements et envoyer des commandes à l'aide de HTTP.
[Gestion des risques ![Icône de lien externe](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/riskmgmt.html){: new_window}   | Gérer les politique de gestion des risques et les rapports associés.

## API HTTP d'extension
{: #api_extension}

API                     | A utiliser pour...       
------------- | -------------
[Extension AT&T ![Icône de lien externe](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/ext-atnt.html){: new_window} | Administrer des terminaux AT&T.
[Extension Jasper  ![Icône de lien externe](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/ext-jasper.html){: new_window} | Administrer des terminaux Jasper.
[Extension Orange  ![Icône de lien externe](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/ext-orange.html){: new_window} | Afficher les données de carte SIM à partir des terminaux qui sont connectés à votre organisation {{site.data.keyword.iot_short_notm}} et exécuter l'installation d'une carte SIM Orange.

## API HTTP bêta
{: #api_beta}

API                     | A utiliser pour...       
------------- | -------------
[Restaurer les terminaux supprimés ![Icône de lien externe](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002-beta/restore-device-beta.html){: new_window}   | Un terminal supprimé par erreur peut être restauré pendant 14 jours.
