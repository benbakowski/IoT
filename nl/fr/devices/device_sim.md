---

copyright:
  years: 2017, 2019
lastupdated: "2019-02-13"
---

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:important: .important}


# Simulation de données de terminal
{: #sim_device_data}

<p>Cette série de documents {{site.data.keyword.Bluemix}} concerne le plan de tarification {{site.data.keyword.iot_full}} Lite et inclut le guide d'initiation, les références d'API et les informations générales relatives au traitement des incidents.
Pour la documentation complète de la fonction {{site.data.keyword.iot_short_notm}}, voir [la documentation du produit {{site.data.keyword.iot_short_notm}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/fr/SSQP8H/iot/overview/overview.html) dans l'IBM Knowledge Center. Vous trouverez davantage d'informations sur les divers plans dans [Plans de service {{site.data.keyword.iot_short_notm}}](/docs/IoT/plans_overview.html#plans_overview).
</p>
{: important}

Le simulateur de terminal {{site.data.keyword.iot_full}} permet de configurer les événements simulés de terminaux. Vous pouvez exploiter les données d'événements simulés pour découvrir, tester et démontrer pleinement le fonctionnement de {{site.data.keyword.iot_short_notm}}.
{: shortdesc}

Vous pouvez vous servir des terminaux et types de terminal existants, et le simulateur vous permet de générer de nouveaux terminaux pour des types existants. Vous avez la possibilité de configurer les détails d'événement de chaque terminal ou d'appliquer une configuration par défaut à l'ensemble des terminaux. Enfin, vous pouvez exporter une configuration d'événement simulé afin de la réutiliser ou de la partager pour configurer d'autres simulations.

Pour simuler des données de terminal :

1. Connectez-vous à {{site.data.keyword.iot_short_notm}}.
2. Dans le panneau de navigation principal, sélectionnez **Paramètres**.
3. Dans la section **Données et terminaux**, activez le simulateur de terminal.
4. Dans le panneau de navigation principal, sélectionnez **Terminaux**. Un message dans le coin inférieur droit de l'écran indique qu'aucune simulation n'est en cours d'exécution.
5. Cliquez sur le message "0 simulation en cours d'exécution".
6. Dans la fenêtre en incrustation **Simulations**, cliquez sur **Créer une simulation**.
7. Sélectionnez un type de terminal existant pour lequel simuler des données ou créez un type de terminal en entrant le nom du type de terminal. 
8. Cliquez sur **Importer/Exporter une simulation** pour utiliser une configuration existante ou configurez manuellement les détails de la simulation pour le type de terminal. 
   1. Cliquez sur **+ Nouveau type d'événement** pour ajouter un type d'événement au type de terminal. 
   2. Entrez un nom pour le type d'événement. 
   3. Sous **Programmation**, définissez la fréquence de l'événement. 
   3. Editez les détails du type d'événement au format JSON et sauvegardez le type d'événement mis à jour.

   <p> Vous pouvez utiliser les variables spéciales suivantes lors de la configuration d'événements :  
        - `range` : cette variable est remplacée par un nombre aléatoire compris entre les deux valeurs fournies, par exemple `{"random": range(300, 100)}`.   
        - `$counter` : cette variable est remplacée par le nombre de terminaux qui sont ajoutés dans le simulateur pour le type en cours, par exemple `{"total": $counter}`.   
        - `increment` : cette variable indique le nombre de départ et l'incrément en fonction duquel il augmente, par exemple `{"myNumber": increment(10, 1)}`. En l'occurrence, `myNumber` commence à 10 et augmente d'1 point à chaque fois qu'un contenu est envoyé (10, 11, 12, etc.). </p>
   {: tip}

9. Sélectionnez un terminal enregistré pour la simulation ou créez un terminal en entrant le nom du terminal. 
10. Afin de créer plusieurs simulations, cliquez sur **Nouvelle simulation** et répétez les étapes de configuration pour chaque terminal auquel appliquer les paramètres personnalisés. Le message qui apparaît dans le coin inférieur droit de l'écran affiche le nombre de simulations actives.
11. **Facultatif :** après avoir configuré les simulations pour les terminaux, exportez les détails de sorte qu'ils puissent être réutilisés ou partagés :
    1. Dans la fenêtre en incrustation **Simulations**, cliquez sur **Importation/Exportation**.
    2. Sélectionnez l'onglet **Exporter**.
    3. Copiez les détails de la simulation dans le presse-papiers ou téléchargez-les dans un fichier JSON.
12. Dans la page **Terminaux**, accédez à l'un des terminaux simulés et sélectionnez l'onglet **Evénements récents** pour vérifier que les événements simulés sont opérationnels.
