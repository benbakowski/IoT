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
{:important: .important}

# Traitement des incidents liés à {{site.data.keyword.iot_short_notm}}
{: #ts}

<p>Cette série de documents {{site.data.keyword.Bluemix}} concerne le plan de tarification {{site.data.keyword.iot_full}} Lite et inclut le guide d'initiation, les références d'API et les informations générales relatives au traitement des incidents.
Pour la documentation complète de la fonction {{site.data.keyword.iot_short_notm}}, voir [la documentation du produit {{site.data.keyword.iot_short_notm}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/fr/SSQP8H/iot/overview/overview.html) dans l'IBM Knowledge Center. Vous trouverez davantage d'informations sur les divers plans dans [Plans de service {{site.data.keyword.iot_short_notm}}](/docs/IoT/plans_overview.html#plans_overview).
</p>
{: important}

Voici les réponses aux questions fréquentes sur le traitement des incidents liés à l'utilisation d'{{site.data.keyword.iot_full}} sur {{site.data.keyword.Bluemix_notm}}.
{:shortdesc}

## Problème lors de l'accès à votre organisation {{site.data.keyword.iot_short_notm}}
{: #access-expiry-problem}

Vous ne pouvez pas vous connecter à une organisation {{site.data.keyword.iot_short_notm}} dont vous êtes propriétaire.
{:shortdesc}

Vous ne pouvez pas vous connecter à votre organisation {{site.data.keyword.iot_short_notm}} directement en utilisant l'URL de l'organisation ou en utilisant `https://internetofthings.ibmcloud.com`.
{: tsSymptoms}

Votre accès à votre organisation {{site.data.keyword.iot_short_notm}} est peut-être arrivé à expiration. Les organisations {{site.data.keyword.iot_short_notm}} qui ont été créées à l'aide d'{{site.data.keyword.Bluemix}} utilisent des profils utilisateur temporaires par défaut.
{: tsCauses}

Vous pouvez résoudre ce problème en accédant à votre organisation {{site.data.keyword.iot_short_notm}} à l'aide de {{site.data.keyword.Bluemix_notm}} et en modifiant les paramètres d'expiration de votre profil utilisateur. Pour modifier les paramètres d'expiration de votre profil utilisateur :

1. Dans votre tableau de bord {{site.data.keyword.Bluemix_notm}}, ouvrez votre service {{site.data.keyword.iot_short_notm}}.
2. Cliquez sur **Membres** dans la barre de navigation.
3. Cliquez sur l'icône **Editer**.
4. Désélectionnez la case à cocher **L'accès arrive à expiration** et cliquez sur **Sauvegarder**.
{: tsResolve}

## Problème lors de la connexion à {{site.data.keyword.iot_short_notm}}
{: #connection_problem}

Votre connexion à {{site.data.keyword.iot_short_notm}} s'interrompt de manière inattendue.
{:shortdesc}

Lorsque vous tentez de vous connecter à {{site.data.keyword.iot_short_notm}}, une erreur s'affiche dans votre terminal ou votre application.
{: tsSymptoms}

Plusieurs terminaux peuvent tenter de se connecter avec le même ID de client et les mêmes données d'identification. Cependant, une connexion et une seule est autorisée par ID de client. Plusieurs connexions simultanées ne peuvent pas utiliser le même ID. Les applications peuvent partager la même clé d'API, mais MQTT requiert que l'ID de client soit toujours unique.
{: tsCauses}

Vous pouvez écarter ce motif en vérifiant que plusieurs terminaux ne tentent pas de se connecter avec les mêmes données d'identification.
{: tsResolve}

## Déconnexion par intermittence d'un terminal à {{site.data.keyword.iot_short_notm}}
{: #disconnection_problem}

La connexion de votre terminal à {{site.data.keyword.iot_short_notm}} s'interrompt par intermittence de manière inattendue.
{:shortdesc}

Un terminal connecté au service {{site.data.keyword.iot_short_notm}} est déconnecté par intermittence. Il se reconnecte, mais il est de nouveau déconnecté de manière inattendue au bout d'un certain temps.
{: tsSymptoms}

Il se peut que lorsque vous vous connectez, vous utilisiez une valeur trop faible pour une option de commande ping MQTT, ce qui peut donner l'impression qu'un dépassement de délai d'attente s'est produit pour la connexion. Par exemple, si MQTT client est défini de manière incorrecte, les commandes ping ne sont pas reçues à temps, et la connexion prend fin.
{: tsCauses}

Pour résoudre ce problème, vous pouvez vérifier que vous avez correctement défini les paramètres ping et KeepAlive pour votre connexion.   
{: tsResolve}
