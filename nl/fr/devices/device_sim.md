---

copyright:
  years: 2017, 2019
lastupdated: "2019-04-05"

keywords: device simulator, devices

subcollection: iot-platform

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

<p>Cette série de documents {{site.data.keyword.cloud}} concerne le plan de tarification {{site.data.keyword.iot_full}} Lite et inclut le guide d'initiation, les références d'API et les informations générales relatives au traitement des incidents.
Pour la documentation complète de la fonction {{site.data.keyword.iot_short_notm}}, voir [la documentation du produit {{site.data.keyword.iot_short_notm}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/fr/SSQP8H/iot/overview/overview.html) dans l'IBM Knowledge Center.  Vous trouverez davantage d'informations sur les divers plans dans [{{site.data.keyword.iot_short_notm}}Plans de service](/docs/services/IoT?topic=iot-platform-plans_overview#plans_overview). 
</p>
{: important}

Utilisez le simulateur de terminal {{site.data.keyword.iot_full}} pour configurer des événements simulés afin que les terminaux découvrent, testent et démontrent pleinement le fonctionnement de {{site.data.keyword.iot_short_notm}} sans qu'il soit nécessaire que vous enregistriez et connectiez des terminaux réels.
{: shortdesc}

Grâce au simulateur de terminal, vous pouvez créer des terminaux simulés pour des types de terminal existants ou créer de nouveaux terminaux et types de terminal. Chaque terminal simulé peut utiliser des détails d'événement uniques, mais vous pouvez également créer une configuration par défaut qui s'applique à tous les terminaux.

## Avant de commencer
{: #byb-simulation .sectiontitle}
Activez la simulation de terminal pour votre ID utilisateur.
1. Connectez-vous à {{site.data.keyword.iot_short_notm}}.
2. Dans le panneau de navigation principal, sélectionnez **Paramètres**.
3. Dans la section **Données et terminaux**, activez le simulateur de terminal.

Si la simulation de terminal est activée pour votre ID utilisateur, tous les terminaux simulés démarrent automatiquement lorsque vous vous connectez au tableau de bord {{site.data.keyword.iot_short_notm}}.

## Simulation de terminaux
{: #process-simulation .sectiontitle}
Une fois activé, le simulateur de terminal est disponible sur toutes les pages du tableau de bord. Un message dans l'angle inférieur droit de l'écran indique le nombre de simulations en cours d'exécution.

**Important :** Les terminaux et types de terminal que vous définissez pour votre ID utilisateur sont disponibles pour d'autres utilisateurs de l'organisation {{site.data.keyword.iot_short_notm}}. Toutefois, si vous souhaitez générer des données simulées pour vos terminaux, vous devez être connecté au tableau de bord {{site.data.keyword.iot_short_notm}} dans une session utilisateur active.

Pour simuler des données de terminal :
1. A partir du tableau de bord {{site.data.keyword.iot_short_notm}}, cliquez sur le message "0 simulation en cours d'exécution".
3. Dans la fenêtre de configuration **Simulations** qui s'affiche, cliquez sur **Créer une simulation**.
4. Configurez les détails de la simulation.  
Cliquez sur **Importer/Exporter une simulation** pour importer une [configuration existante](#reuse) ou configurez manuellement les détails suivants :
   1. Sélectionnez un type de terminal existant pour lequel simuler des données ou créez un type de terminal en entrant le nom du type de terminal.
   2. Modifiez le nom par défaut du type d'événement.
   3. Sous **Programmation**, définissez la fréquence de l'événement.
   4. Editez la charge utile d'événement.  
   Editez l'exemple de contenu JSON en ajoutant des propriétés et leurs valeurs correspondantes ou utilisez les [fonctions](#functions) pour ajouter des points de données générés dynamiquement.  
   Vous pouvez également transférer un [fichier de charge utile d'événement CSV](#csv) afin de configurer la charge utile.  
   {: tip}
5. Cliquez sur **Nouveau type d'événement** pour ajouter et configurer davantage de types d'événement pour le type de terminal.
5. Activez **Sauvegarder les événements en tant que données d'historique** de sorte que vos données d'état de terminal simulé soient disponibles pour un accès ultérieur.   
Les données d'historique étant activées, les composants de [gestion de données {{site.data.keyword.iot_short_notm}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/SSQP8H/iot/platform/GA_information_management/ga_im_definitions.html){: new_window} sont créés et l'état de terminal simulé est accessible à partir de l'interface logique associée.   
**Important :** Après avoir activé le type de terminal pour la sauvegarde des données d'historique, vous ne pouvez pas ajouter ou retirer de types d'événement, ni modifier les champs figurant dans les charges utiles d'événement.
5. Cliquez sur **Sauvegarder** pour créer le type de terminal.  
Vous êtes maintenant prêt à créer un ou plusieurs terminaux simulés.
6. Cliquez sur **Créer un terminal simulé** pour créer un terminal et commencer à envoyer des données.  
**Astuce :** Pour créer plusieurs terminaux, cliquez sur **1 x** et sélectionnez le nombre de terminaux à créer.  
7. Afin de créer plusieurs simulations, cliquez sur **Nouvelle simulation** et répétez les étapes de configuration pour chaque terminal auquel appliquer les paramètres personnalisés.   
Le message qui s'affiche dans l'angle inférieur droit de l'écran indique le nombre de simulations actives.
8. Dans la page **Terminaux**, accédez à l'un des terminaux simulés et sélectionnez l'onglet **Evénements récents** pour vérifier que les événements simulés sont opérationnels.

Vous pouvez [exporter vos configurations d'événement simulé](#reuse) afin de les réutiliser ou les partager.

## Fonctions des types d'événement
{: #functions .sectiontitle}

Vous pouvez utiliser un certain nombre de fonctions spéciales pour créer des données dynamiques pour vos types d'événement.

Fonction | Utilisation | Exemple  
:--- | :---  | :--  
`random(lower, upper)`  | Génère un nombre aléatoire dans la plage indiquée.  | `{"random": random(0, 100)}`  
`$counter` | Affiche le nombre de terminaux simulés du type en cours. | `{"total": $counter}`  
`increment(start, increment)` | Indique la valeur de départ et l'incrément en fonction duquel elle augmente. |`{"myNumber": increment(10, 1)}` </br> Dans cet exemple, `myNumber` commence à 10 et augmente de 1 en 1 à chaque envoi de contenu.


## Fichier de charge d'événement CSV
{: #csv .sectiontitle}

Si vous souhaitez créer des données d'événement contrôlées pour certains scénarios, vous pouvez configurer le flux de données dans un fichier d'entrée CSV.

### Conditions requises
Le fichier CSV doit répondre aux exigences suivantes :
- Chaque valeur est un [objet primitif JSON valide ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://json.org){: new_window} sauf indication contraire :
  - chaîne :   
  Exemple : "Hello world"
  - nombre :  
  Exemple : 0, 0.1, -22, -2.43
  - booléen :  
true ou false
  - null :  
  null
  - **Non pris en charge :**
    - objets  
    Exemple : {}
    - tableaux  
    Exemple : []
- Les valeurs doivent être délimitées par des virgules.
- Les lignes doivent être délimitées par le caractère de retour à la ligne (`\n`).
- La ligne d'en-tête doit être composée de valeurs de chaîne uniquement.


### Exemple de fichier CSV
```
"temperature", "confidence","status"
1, 0.1, "normal"
2, 0.2, "normal"
3, 0.3, "error"
4, 0.4, "normal"
```

La première ligne ou "ligne d'en-tête" détermine les propriétés incluses dans le JSON de terminal dans tous les objets d'événement JSON de terminal générés.
Chaque ligne suivante ou "ligne de données" définit la valeur de ces propriétés dans chaque objet d'événement JSON de terminal généré.

**Astuce :** Lorsque vous importez le fichier CSV, vous pouvez sélectionner **Mettre en boucle les données simulées à partir du fichier** pour parcourir les lignes de données dans l'ordre et atteindre un flux de données continu. Si cette bascule n'est pas définie, chaque ligne de données du CSV est envoyée une fois à la fréquence définie par la planification.

L'exemple de fichier CSV génère des charges d'événement du type suivant :
```JSON
{
  "temperature": 1,
  "confidence": 0.1,
  "status": "normal"
}
```

## Partage et réutilisation des simulations
{: #reuse .sectiontitle}

Vous pouvez exporter les détails de simulation pour les réutiliser ou les partager :
1. Dans la fenêtre **Simulations**, cliquez sur **Importation/Exportation**.
2. Sélectionnez l'onglet **Exporter**.
3. Copiez les détails de la simulation dans le presse-papiers ou téléchargez-les dans un fichier JSON.
