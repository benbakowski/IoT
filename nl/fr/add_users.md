---

copyright:
  years: 2016, 2019
lastupdated: "2019-04-05"

keywords: user access, Add function, members dashboard

subcollection: iot-platform

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:important: .important}

# Gestion des accès utilisateur
{: #managing-user-access}

<p>Cette série de documents {{site.data.keyword.cloud}} concerne le plan de tarification {{site.data.keyword.iot_full}} Lite et inclut le guide d'initiation, les références d'API et les informations générales relatives au traitement des incidents.
Pour la documentation complète de la fonction {{site.data.keyword.iot_short_notm}}, voir [la documentation du produit {{site.data.keyword.iot_short_notm}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/fr/SSQP8H/iot/overview/overview.html) dans l'IBM Knowledge Center.  Vous trouverez davantage d'informations sur les divers plans dans [{{site.data.keyword.iot_short_notm}}Plans de service](/docs/services/IoT?topic=iot-platform-plans_overview#plans_overview). 
</p>
{: important}

Depuis la page Membres du tableau de bord, vous pouvez contrôler et gérer les accès à votre organisation {{site.data.keyword.iot_full}}. Vous pouvez ajouter des utilisateurs en les ajoutant, en les invitant ou en les important. Vous pouvez également accorder différents niveaux d'accès à vos utilisateurs en affectant des rôles.
{:shortdesc}

## Ajout d'utilisateurs
{: #adding-new-users}

Depuis la page **Membres** du tableau de bord, vous pouvez ajouter des membres individuels avec la fonction Ajouter. Vous pouvez également ajouter plusieurs membres simultanément avec la fonction Importer.

Par défaut, les comptes des membres n'arrivent jamais à expiration. Si vous le souhaitez, lorsque vous ajoutez des utilisateurs à votre organisation {{site.data.keyword.iot_short_notm}}, vous pouvez définir une date d'expiration pour leur compte.

### Ajout de membres à votre organisation {{site.data.keyword.iot_short_notm}}

Pour ajouter un membre à votre organisation, vous devez disposer de son IBMid. Vous n'avez pas besoin de sa confirmation.

Pour ajouter un membre à votre organisation {{site.data.keyword.iot_short_notm}} :
1. Dans votre tableau de bord {{site.data.keyword.iot_short_notm}}, cliquez sur **Membres** dans la barre de navigation.
2. Cliquez sur **Ajouter des membres** et sélectionnez l'onglet **Ajouter**.
3. Entrez l'IBMid du membre.
4. Sélectionnez un rôle pour le membre.
5. Facultatif : définissez une date d'expiration.
6. Cliquez sur **Ajouter**.

Pour ajouter plusieurs membres en même temps, vous devez télécharger un fichier `.csv` contenant l'IBMid, le rôle et la date d'expiration facultative pour chaque membre. Pour plus d'informations, voir [Construction de votre fichier CSV](#constructing-your-csv).
1. Dans votre tableau de bord {{site.data.keyword.iot_short_notm}}, cliquez sur **Membres** dans la barre de navigation.
2. Cliquez sur **Ajouter des membres** et sélectionnez l'onglet **Importer**.
3. Recherchez vos fichiers ou faites glisser le fichier `.csv` dans la fenêtre **Télécharger le fichier CSV**.
4. Sélectionnez un rôle par défaut à utiliser si un rôle indiqué dans le fichier CSV n'est pas reconnu.
5. Mappez les numéros de colonne de votre fichier CSV aux entrées d'IBMid, de rôle et de date d'expiration facultative correspondantes.
6. Sélectionnez la virgule ou le point-virgule comme séparateur de colonne approprié selon le séparateur utilisé dans votre fichier `.csv`.
7. Cliquez sur **Importer** pour importer les IBMid et créez les membres.


### Construction de votre fichier CSV
{: #constructing-your-csv}

Lorsque vous construisez un fichier CSV pour importer des membres dans votre organisation, veillez à inclure les informations requises pour la méthode que vous utilisez. Utilisez des virgules ou des points-virgule pour séparer les colonnes.  
**Important :** lorsque vous téléchargez le fichier CSV, sous **Paramètres CSV**, veillez à sélectionner le séparateur de colonne approprié.

Exemple de fichier CSV avec la virgule comme délimiteur :  
```
user1@sample.com,PD_DEVELOPER_USER,2018-03-13
user2@sample.com,PD_OPERATOR_USER,2018-03-13
user3@sample.com,PD_ADMIN_USER,2018-03-13
```
Où les entrées de colonne suivantes sont utilisées :  
- Colonne 1 : adresse électronique de l'utilisateur.  
Si vous ajoutez des membres, veillez à utiliser l'adresse électronique qui correspond à un IBMid valide. Si vous invitez des membres, vous pouvez utiliser n'importe quelle adresse électronique valide.
- Colonne 2 : rôle à affecter à l'utilisateur.  
Entrez l'un des rôles suivants :
 - PD_ADMIN_USER
 - PD_OPERATOR_USER
 - PD_DEVELOPER_USER
 - PD_ANALYST_USER
 - PD_READER_USER  
 Pour plus d'informations sur les rôles d'utilisateur, voir [Rôles d'utilisateur, d'application et de passerelle ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/fr/SSQP8H/iot/platform/roles_index.html#user_roles){: new_window}.
- Colonne 3 : date ISO 6801 (par exemple, `2018-03-13`) correspondant à la date d'expiration de l'utilisateur.

## Edition d'utilisateurs
{: #editing-users}

Vous pouvez éditer les utilisateurs pour modifier leur rôle, ajouter, retirer ou modifier une date d'expiration d'accès ou ajouter ou retirer des droits d'accès à l'organisation.

1. Dans votre tableau de bord {{site.data.keyword.iot_short_notm}}, cliquez sur **Membres** dans la barre de navigation.
2. Cliquez sur l'icône **Editer** en regard de l'utilisateur à éditer.
3. Apportez les modifications souhaitées à l'utilisateur.
4. Cliquez sur **Sauvegarder**.

## Blocage de l'accès utilisateur
{: #blocking-users}

Il est possible de bloquer l'accès des utilisateurs à l'organisation {{site.data.keyword.iot_short_notm}} tout en conservant l'appartenance de ces utilisateurs à l'organisation.

1. Dans votre tableau de bord {{site.data.keyword.iot_short_notm}}, cliquez sur **Membres** dans la barre de navigation.
2. Cliquez sur le bouton à bascule en regard de l'utilisateur dont vous souhaitez bloquer l'accès à l'organisation {{site.data.keyword.iot_short_notm}}.

## Limitation de l'accès utilisateur
{: #limiting-users}

Le contrôle d'accès au niveau de la ressource permet de limiter l'accès aux terminaux dans une organisation. Vous pouvez utiliser des groupes de ressources pour spécifier les terminaux que chaque utilisateur ou clé d'API peut gérer. Pour plus d'informations sur la façon de configurer le contrôle d'accès au niveau de la ressource, voir [Configuration du contrôle d'accès au niveau de la ressource ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/fr/SSQP8H/iot/platform/reference/rlac.html#configure_RLAC){: new_window}.

## Retrait d'utilisateurs
{: #removing-users}

Les utilisateurs peuvent être entièrement retirés de l'organisation {{site.data.keyword.iot_short_notm}}. Le retrait d'utilisateurs ne peut pas être annulé, et vous devez [ajoutés les utilisateurs à la plateforme](#adding-new-users) pour restaurer leur accès.

1. Dans votre tableau de bord {{site.data.keyword.iot_short_notm}}, cliquez sur **Membres** dans la barre de navigation.
2. Cliquez sur l'icône **Supprimer** en regard de l'utilisateur à retirer.
3. Cliquez sur **Supprimer** dans la boîte de dialogue de confirmation.
