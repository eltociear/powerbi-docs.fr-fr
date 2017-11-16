---
title: "Didacticiel : analyses de Facebook à l’aide de Power BI Desktop"
description: "Didacticiel : analyses de Facebook à l’aide de Power BI Desktop"
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 09/06/2017
ms.author: davidi
ms.openlocfilehash: 3642a252467d504b61eb81f82d0b96f64a24f22b
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2017
---
# <a name="tutorial-facebook-analytics-using-power-bi-desktop"></a>Didacticiel : analyses de Facebook à l’aide de Power BI Desktop
Dans ce didacticiel, vous allez apprendre à importer et à visualiser des données provenant de **Facebook**. Au cours du didacticiel, vous allez découvrir comment vous connecter à une page Facebook spécifique (la page Power BI), comment appliquer des opérations de transformation de données et comment créer des visualisations.

Voici les étapes à que vous allez suivre :

* **Tâche 1** : se connecter à une page Facebook
* **Tâche 2**: créer des visualisations dans la vue Rapport
  
  * **Étape 1**: créer une visualisation Treemap
* **Tâche 3**: mettre en forme les données dans la vue Requête
  
  * **Étape 1**: fractionner la colonne de date et d’heure en deux
  * **Étape 2**: ajouter une valeur d’agrégat à partir d’une table connexe
* **Tâche 4**: créer des visualisations supplémentaires dans la vue Rapport
  
  * **Étape 1**: charger la requête dans votre rapport
  * **Étape 2**: créer un graphique en courbes et un graphique à barres

## <a name="task-1-connect-to-a-facebook-page"></a>**Tâche 1 : se connecter à une page Facebook**
Dans cette tâche, les données sont importées de la [page Facebook de Microsoft Power BI](https://www.facebook.com/microsoftbi) (dont voici l’URL : *https://www.facebook.com/microsoftbi )*.

Toute personne peut se connecter à cette page et effectuer ces étapes ; aucune information d’identification particulière n’est nécessaire, à part votre propre compte Facebook, que vous utilisez dans cette étape.

![](media/desktop-tutorial-facebook-analytics/1.png)

1. Dans la boîte de dialogue **Prise en main** ou sous **l’onglet Accueil du ruban**, sélectionnez **Obtenir des données**.
2. La boîte de dialogue **Obtenir des données** apparaît, vous permettant d’effectuer votre choix parmi toutes sortes de sources de données. Sélectionnez **Facebook** dans le groupe **Autre**.
   
   ![](media/desktop-tutorial-facebook-analytics/t_fb_getdataother.png)
   
   Quand vous sélectionnez **Connexion**, une boîte de dialogue s’affiche pour vous avertir des risques liés à l’utilisation d’un service tiers.
   
   ![](media/desktop-tutorial-facebook-analytics/t_fb_connectingtotps.png)
3. Quand vous cliquez sur Continuer, la boîte de dialogue **Facebook** s’affiche. Collez le nom de la page (**microsoftbi**) dans la zone de texte **Nom d’utilisateur**. Sélectionnez **Publications** dans la liste déroulante **Connexion**.
   
   ![](media/desktop-tutorial-facebook-analytics/2.png)
4. Cliquez sur **OK**.
5. Quand vous êtes invité à indiquer vos informations d’identification, connectez-vous à l’aide de votre compte Facebook et autorisez l’accès de Power BI via votre compte.
   
   ![](media/desktop-tutorial-facebook-analytics/facebookcredentials.png)

Après vous être connecté à la page, vous verrez les données chargées dans le modèle. 

![](media/desktop-tutorial-facebook-analytics/t_fb_1-loadpreview.png)

**L’Éditeur de requête** affiche alors les données. **L’Éditeur de requête** fait partie de Power BI Desktop, mais il se charge dans une fenêtre distincte. C’est dans celle-ci que vous effectuerez tous vos transformations sur vos connexions de données.

![](media/desktop-tutorial-facebook-analytics/t_fb_1-intoqueryeditor.png)

Quand vos données sont prêtes, vous pouvez les charger dans Power BI Desktop. Sélectionnez **Charger et fermer** dans le ruban **Accueil**.

![](media/desktop-tutorial-facebook-analytics/t_fb_1-loadandclose.png)

Une boîte de dialogue affiche la progression du chargement des données dans le modèle de données Power BI Desktop.

![](media/desktop-tutorial-facebook-analytics/t_fb_1-loading.png)

Une fois les données chargées, vous êtes dirigé vers la vue **Rapport**, dont la liste **Champs** à droite répertorie les colonnes de la table.

![](media/desktop-tutorial-facebook-analytics/fbdesigner1.png)

## <a name="task-2-create-visualizations-using-the-report-view"></a>**Tâche 2 : créer des visualisations dans la vue Rapport**
Les données étant récupérées de la page, vous pouvez rapidement et facilement mieux les connaître à l’aide de visualisations.

**Étape 1 :** créer une visualisation Treemap

Pour créer une visualisation, rien de plus facile. Il suffit de faire glisser un champ à partir de la **liste Champs** et de le déplacer dans le **canevas de rapport**.

Faites glisser le champ **type** dans le **canevas de rapport**. Power BI Desktop crée une visualisation dans le **canevas de rapport**. Ensuite, faites glisser le champ **type** à partir du volet **Champs** (le même champ que vous venez de faire glisser dans le **canevas de rapport** ) dans la zone **Valeur** pour créer une visualisation **Barre**.

![](media/desktop-tutorial-facebook-analytics/fbdesigner2.png)

Nous pouvons facilement modifier le type de visualisation en sélectionnant une autre icône dans le volet **Visualisation**. Choisissons à présent le type **Treemap** en sélectionnant l’icône correspondante dans **Visualisations**, comme le montre l’image suivante.

![](media/desktop-tutorial-facebook-analytics/fbdesigner3.png)

Ajoutons une légende, puis modifions la couleur d’un point de données. Sélectionnez l’icône **Format** dans le volet **Visualisations** (l’icône **Format** ressemble à un pinceau).

![](media/desktop-tutorial-facebook-analytics/fbdesigner3a.png)

Quand vous sélectionnez la flèche orientée vers le bas à côté de **Légende**, la section se développe pour vous montrer comment personnaliser la légende pour la visualisation sélectionnée. Dans le cas présent, nous avons effectué les sélections suivantes :

* nous avons déplacé le curseur **Légende** sur **Activé** pour faire apparaître une légende ;
* nous avons sélectionné **Droite** dans la liste déroulante **Position de la légende** ;
* nous avons déplacé le curseur **Titre** sur **Activé** pour afficher un titre de légende ;
* enfin, nous avons tapé **type** comme titre de la légende.

La visualisation illustrée ci-après reflète l’application de ces paramètres.

![](media/desktop-tutorial-facebook-analytics/fbdesigner3b.png)

Nous allons maintenant changer la couleur de l’un des points de données. Nous souhaitons afficher le point de données link en bleu pour qu’il soit plus proche de la couleur traditionnelle des liens hypertexte.

Sélectionnez la flèche à côté de **Couleurs des données** pour développer cette section. En regard de la couleur de chaque point de données figure une flèche de sélection permettant de sélectionner une couleur différente.

![](media/desktop-tutorial-facebook-analytics/fbdesigner3c.png)

Cliquez sur la flèche orientée vers le bas dans la zone de couleur d’un point de données pour afficher une boîte de dialogue de sélection vous permettant de choisir une couleur. Dans le cas présent, nous allons choisir « bleu clair ».

![](media/desktop-tutorial-facebook-analytics/fbdesigner3d.png)

C’est mieux. L’illustration suivante reflète la nouvelle couleur du point de données dans la visualisation, ainsi que la mise à jour automatique de la légende et de la couleur dans la section **Couleurs des données**.

![](media/desktop-tutorial-facebook-analytics/fbdesigner3e.png)

## <a name="task-3-shape-data-in-the-table"></a>**Tâche 3 : mettre en forme les données de la table**
Après avoir importé la table sélectionnée, vous constaterez peut-être que vous devrez mettre en forme et nettoyer les données pour en tirer le meilleur parti.

**Étape 1 :** fractionner la colonne de date et d’heure en deux

Dans cette étape, vous allez fractionner la colonne **created\_time** pour récupérer les valeurs de date et d’heure. Chaque fois que vous êtes dans Power BI Desktop et que vous souhaitez modifier une requête existante, vous devez lancer l’ **Éditeur de requête**. Pour cela, sélectionnez **Modifier les requêtes** sous l’onglet **Accueil**.

![](media/desktop-tutorial-facebook-analytics/t_fb_editquery.png)

1. Dans **l’Éditeur de requête**, faites défiler la grille jusqu’à ce que vous aperceviez la colonne **created\_time**
2. Cliquez avec le bouton droit sur un en-tête de colonne dans la grille **d’aperçu de requête**, puis cliquez sur **Fractionner la colonne \> Par délimiteur** pour fractionner les colonnes. Choisissez **Personnalisé** dans la liste déroulante des délimiteurs, puis entrez « **T** ». Notez que vous pouvez également effectuer cette opération dans le groupe **Gérer les colonnes** de l’onglet **Accueil** du ruban.
   
   ![](media/desktop-tutorial-facebook-analytics/9.png)
   
   ![](media/desktop-tutorial-facebook-analytics/10.png)
3. Renommez les colonnes créées **created\_date** et **created\_time** respectivement.
4. Sélectionnez la nouvelle colonne, **created\_time**, **** et dans le ruban de la **vue Requête**, accédez à l’onglet **Ajouter une colonne**, puis sélectionnez **Heure\>Heure** sous le groupe **Date et heure de début**. Cette opération ajoute une nouvelle colonne qui ne reprend que la composante « heure ».
   
   ![](media/desktop-tutorial-facebook-analytics/11.png)
5. Affectez à la nouvelle colonne **Heure** le type **Nombre entier**. Pour cela, accédez à l’onglet **Accueil** et sélectionnez la liste déroulante **Type de données** ou cliquez avec le bouton droit sur la colonne et sélectionnez **Transformer\>Nombre entier**.
   
   ![](media/desktop-tutorial-facebook-analytics/12.png)

**Étape 2 :** ajouter une valeur d’agrégat à partir d’une table connexe

Dans cette étape, vous ajoutez le nombre de partages à partir de la valeur imbriquée en vue de l’utiliser dans les visualisations.

1. Continuez à faire défiler vers la droite jusqu’à ce qu’apparaisse la colonne **shares**. La valeur imbriquée indique que nous devons faire une autre transformation pour obtenir les valeurs réelles.
2. Dans la partie supérieure droite de l’en-tête de colonne, sélectionnez l’icône ![](media/desktop-tutorial-facebook-analytics/14.png) pour ouvrir le générateur **Développer/Agréger**. Sélectionnez **count**, puis appuyez sur **OK**. Cette opération ajoute le nombre de partages pour chaque ligne de notre table.
   
   ![](media/desktop-tutorial-facebook-analytics/15.png)
   
   Une fois les données chargées, attribuez à la colonne le nom **shares**. Pour ce faire, vous pouvez double-cliquer sur le nom de la colonne ; cliquer avec le bouton droit sur la colonne ; ou dans le ruban de la **vue Requête**, sous l’onglet **Transformer**, dans le groupe **N’importe quelle colonne**, sélectionner **Renommer**.
3. Enfin, sélectionnez le type **Nombre entier** pour la nouvelle colonne **shares**. Quand la colonne est sélectionnée, vous pouvez modifier le type en cliquant avec le bouton droit sur la colonne et en sélectionnant **Transformer\>Nombre entier** ou **** en accédant à l’onglet **Accueil** et en sélectionnant la liste déroulante **Type de données**.

### <a name="query-steps-created"></a>Étapes de requête créées
Quand vous effectuez des transformations dans la vue Requête, des étapes de requête sont créées et répertoriées dans le volet **Paramètres d’une requête**, dans la liste **ÉTAPES APPLIQUÉES**. À chaque étape de requête correspond une formule Query, également appelée langage « M ».

![](media/desktop-tutorial-facebook-analytics/16.png)

| Tâche | Étape de requête | Formule |
| --- | --- | --- |
| Se connecter à une source Facebook |Source |Facebook.Graph  (&quot;https://graph.facebook.com/microsoftbi/posts&quot;) |
| **Fractionner les colonnes** pour obtenir les valeurs souhaitées |Split Column by Delimiter |Table.SplitColumn  (Source,&quot;created_time&quot;,Splitter.SplitTextByDelimiter(&quot;T&quot;),{&quot;created_time.1&quot;, &quot;created_time.2&quot;}) |
| **Modifier le type** des nouvelles colonnes (étape automatique) |Changed Type |Table.TransformColumnTypes (#&quot;Fractionner la colonne par délimiteur&quot;,{{&quot;created_time.1&quot;, type date}, {&quot;created_time.2&quot;, type time}}) |
| **Renommer **une colonne**** |Renamed Columns |Table.RenameColumns  (#&quot;Type modifié&quot;,{{&quot;created_time.1&quot;, &quot;created_date&quot;}, {&quot;created_time.2&quot;, &quot;created_time&quot;}}) |
| **Insérer **une colonne**** |Inserted Hour |Table.AddColumn  (#&quot;Colonnes renommées&quot;, &quot;Hour&quot;, each Time.Hour([created_time]), type number) |
| **Modifier le type ** |Type modifié 1 |Table.TransformColumnTypes  (#&quot;Heure insérée&quot;,{{&quot;Hour&quot;, type text}}) |
| **Développer **des valeurs dans une table imbriquée**** |Expand shares |Table.ExpandRecordColumn  (#&quot;Type modifié 1&quot;, &quot;shares&quot;, {&quot;count&quot;}, {&quot;shares.count&quot;}) |
| **Renommer **la colonne**** |Renamed Columns1 |Table.RenameColumns  (#&quot; Développer shares&quot;,{{&quot;shares.count&quot;, &quot;shares&quot;}}) |
| **Modifier le type** |Changed Type2 |Table.TransformColumnTypes  (#&quot;Colonnes renommées 1&quot;,{{&quot;shares&quot;, Int64.Type}}) |

## <a name="task-4-create-additional-visualizations-using-the-report-view"></a>**Tâche 4 : créer des visualisations supplémentaires dans la vue Rapport**
Les données ayant la forme nécessaire pour le reste de notre analyse, nous pouvons charger la table résultante dans notre rapport et créer des visualisations supplémentaires.

**Étape 1 :** charger la requête dans votre rapport

Pour charger les résultats de requête pour le rapport, nous devons sélectionner **Charger et fermer** dans **l’Éditeur de requête**. Cette opération charge nos modifications dans Power BI Desktop et ferme l’ **Éditeur de requête**.

![](media/desktop-tutorial-facebook-analytics/t_fb_1-loadandclose.png)

Dans Power BI Desktop, nous devons nous assurer que nous sommes bien dans la vue **Rapport**. Sélectionnez l’icône située en haut de la barre gauche dans Power BI Desktop.

![](media/desktop-tutorial-facebook-analytics/17.png)

**Étape 2 :** créer un graphique en courbes et un graphique à barres

Pour créer une visualisation, nous pouvons faire glisser-déplacer des champs de la **liste Champs** dans le **canevas de rapport**.

1. Faites glisser le champ **shares** dans le canevas de **rapport** pour créer un graphique à barres. Faites ensuite glisser created\_date dans le graphique. Power BI Desktop modifie la visualisation en **graphique en courbes**.
   
   ![](media/desktop-tutorial-facebook-analytics/19.png)
2. Ensuite, faites glisser le champ **shares** et déplacez-le dans le **canevas de rapport**. Maintenant, faites glisser le champ **Hour** dans la section **Axe** sous la **liste Champs**.
   
   ![](media/desktop-tutorial-facebook-analytics/20.png)
3. Nous pouvons facilement modifier le type de visualisation en cliquant sur une autre icône dans le volet **Visualisation**. La flèche dans l’image ci-dessous indique l’icône **Graphique à barres**.
   
   ![](media/desktop-tutorial-facebook-analytics/21.png)
4. Modifiez le type de visualisation en spécifiant **Graphique à barres**.
5. Le **Graphique à barres** est créé, mais nous souhaiterions trier les valeurs sur l’axe dans l’autre sens (de la valeur la plus élevée à la plus petite). Sélectionnez la flèche orientée vers le bas à côté de **l’Axe Y** pour développer cette section. Nous devons remplacer le type d’axe **Continu** par le type **Catégorie** pour trier les valeurs dans l’ordre souhaité. L’illustration ci-dessous montre l’axe avant la modification, tandis que celle d’après présente le résultat désiré.

![](media/desktop-tutorial-facebook-analytics/22.png)

C’est mieux. Nous disposons à présent de trois visualisations que nous pouvons redimensionner pour remplir la page de rapport.

![](media/desktop-tutorial-facebook-analytics/23.png)

Comme vous pouvez le voir, vous pouvez facilement personnaliser les visualisations dans votre rapport pour présenter les données de la façon souhaitée. Power BI Desktop fournit une expérience de bout en bout transparente, allant de la récupération de données d’un large éventail de sources de données à la visualisation de ces données au moyen de méthodes interactives et enrichies, en passant par leur mise en forme en fonction des besoins d’analyse. Une fois que votre rapport est prêt, vous pouvez [le charger dans Power BI](desktop-upload-desktop-files.md) et créer des tableaux de bord basés sur celui-ci, que vous pouvez partager avec d’autres utilisateurs de Power BI.

Vous pouvez télécharger le résultat final de ce didacticiel [ici](http://download.microsoft.com/download/1/4/E/14EDED28-6C58-4055-A65C-23B4DA81C4DE/FacebookAnalytics.pbix)

### <a name="where-else-can-i-get-more-information"></a>Où obtenir des informations supplémentaires ?
* [Autres didacticiels Power BI Desktop](http://go.microsoft.com/fwlink/?LinkID=521937)
* [Vidéos relatives à Power BI Desktop](http://go.microsoft.com/fwlink/?LinkID=519322)
* [Forum Power BI](http://go.microsoft.com/fwlink/?LinkID=519326)
* [Blog Power BI](http://go.microsoft.com/fwlink/?LinkID=519327)



