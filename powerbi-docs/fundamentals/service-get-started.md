---
title: 'Tutoriel : Bien démarrer avec la création dans le service Power BI'
description: Bien démarrer avec le service en ligne Power BI (app.powerbi.com)
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: tutorial
ms.date: 07/02/2020
ms.author: maggies
LocalizationGroup: Get started
ms.openlocfilehash: ee3919be08cfb2af2ad0e82e9f0f35b5d13147c6
ms.sourcegitcommit: 20cfd157af587b3910a2b6deec9518dca4105d71
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "85943324"
---
# <a name="tutorial-get-started-creating-in-the-power-bi-service"></a>Tutoriel : Bien démarrer avec la création dans le service Power BI
Ce tutoriel présente certaines des fonctionnalités du *service Power BI*. Il vous montre comment vous connecter aux données, créer un rapport et un tableau de bord, et poser des questions sur vos données. Le service Power BI propose bien d’autres fonctionnalités, mais ce tutoriel ne vous en montre qu’un échantillon. Pour comprendre comment le service Power BI s’intègre aux autres offres de Power BI, nous vous recommandons de lire [Qu’est-ce que Power BI](power-bi-overview.md).

Êtes-vous davantage un *lecteur* de rapport qu’un créateur ? L’article [Découverte du service Power BI](../consumer/end-user-experience.md) est un bon point de départ pour vous.

:::image type="content" source="media/service-get-started/power-bi-service-rearranged-dashboard.png" alt-text="Capture d’écran du tableau de bord Financial Sample":::

Ce tutoriel vous montre comment effectuer les étapes suivantes :

> [!div class="checklist"]
> * Vous connecter à votre compte Power BI en ligne ou en créer un si vous n’en avez pas.
> * Ouvrir le service Power BI
> * Obtenir des données et les ouvrir dans la vue Rapport
> * Utiliser ces données pour créer des visualisations et les enregistrer sous forme de rapport
> * Créer un tableau de bord en épinglant des vignettes du rapport
> * Ajouter d’autres visualisations à votre tableau de bord à l’aide de l’outil Questions et réponses en langage naturel.
> * Redimensionner, réorganiser et modifier les détails des vignettes sur le tableau de bord.
> * Nettoyer les ressources en supprimant le jeu de données, le rapport et le tableau de bord

## <a name="sign-up-for-the-power-bi-service"></a>S’inscrire au service Power BI
Vous devez être titulaire d’une licence Power BI Pro pour créer du contenu dans Power BI. Si vous n’avez pas de compte Power BI, [inscrivez-vous pour un essai gratuit de Power BI Pro](https://app.powerbi.com/signupredirect?pbi_source=web) avant de commencer.

## <a name="step-1-get-data"></a>Étape 1 : Obtenir des données

Souvent, quand vous voulez créer un rapport Power BI, vous utilisez Power BI Desktop. Power BI Desktop offre plus de possibilités. Vous pouvez transformer, mettre en forme et modéliser des données avant de commencer à concevoir un rapport. Cette fois-ci, nous allons utiliser le service Power BI pour créer un rapport de A à Z.

Dans ce tutoriel, les données proviennent d’un simple fichier Microsoft Excel. Comment procéder ? [Téléchargez le fichier Financial Sample](https://go.microsoft.com/fwlink/?LinkID=521962).

1. Pour commencer, ouvrez le service Power BI (app.powerbi.com) dans votre navigateur. 

    Vous n’avez pas de compte ? Ne vous inquiétez pas, vous pouvez vous [inscrire ici pour bénéficier d’un essai gratuit de Power BI Pro](https://app.powerbi.com/signupredirect?pbi_source=web).

1. Dans le volet de navigation, sélectionnez **Mon espace de travail**.

1. Dans **Mon espace de travail**, sélectionnez **Nouveau** > **Charger un fichier**.

    La page **Obtenir des données** s’ouvre.   

3. Sous la section **Créer du contenu**, vérifiez que **Fichiers** est sélectionné, puis sélectionnez l’emplacement où vous avez enregistré le fichier Excel.
   
    :::image type="content" source="media/service-get-started/power-bi-service-get-data-local-file.png" alt-text="Capture d’écran de Créer du contenu > Fichiers.":::

5. Recherchez le fichier sur votre ordinateur, puis choisissez **Ouvrir**.

5. Dans ce tutoriel, nous sélectionnons **Importer** pour ajouter le fichier Excel comme jeu de données, que nous utilisons ensuite pour créer des rapports et des tableaux de bord. Si vous sélectionnez **Charger**, le classeur Excel entier est chargé dans Power BI, où vous pouvez l’ouvrir et le modifier dans Excel en ligne.
   
   :::image type="content" source="media/service-get-started/power-bi-import.png" alt-text="Capture d’écran montrant l’option Importer sélectionnée.":::
6. Quand votre jeu de données est prêt, sélectionnez **Plus d’options (...)** en regard de votre jeu de données Financial Sample, puis **Créer un rapport**.
1. Ouvrez l’éditeur de rapport. 

    :::image type="content" source="media/service-get-started/power-bi-service-datasets.png" alt-text="Capture d’écran de Tout le contenu > Créer un rapport.":::

    Le canevas de rapport est vide. Nous voyons les volets **Filtres**, **Visualisations** et **Champs** à droite.

    :::image type="content" source="media/service-get-started/power-bi-service-blank-report.png" alt-text="Capture d’écran d’un canevas de rapport vide.":::

    > [!TIP]
    > Sélectionnez le bouton de navigation globale en haut à gauche pour réduire le volet de navigation. Votre canevas peut ainsi occuper plus de place.
    >
    >:::image type="content" source="media/service-get-started/power-bi-global-nav-button.png" alt-text="Bouton de navigation globale.":::
    >

7. Vous êtes actuellement en mode Edition. Notez l’option **Mode Lecture** dans la barre de menus. 

    :::image type="content" source="media/service-get-started/power-bi-service-reading-view.png" alt-text="Capture d’écran de l’option Mode Lecture.":::

    En mode Edition, vous pouvez modifier des rapports puisque vous êtes à la fois le *propriétaire* et le *créateur* du rapport. Quand vous partagez votre rapport avec vos collègues, ces derniers ne peuvent souvent interagir avec ce rapport qu’en mode Lecture. Ils sont donc des *consommateurs* de rapports dans **Mon espace de travail**. 

## <a name="step-2-create-a-chart-in-a-report"></a>Étape 2 : Créer un graphique dans un rapport
Maintenant que vous êtes connecté aux données, vous pouvez les explorer. Si vous trouvez quelque chose d’intéressant, vous pouvez l’enregistrer dans le canevas du rapport. Vous pouvez ensuite l’épingler à un tableau de bord pour le superviser et voir comment il évolue dans le temps. Mais commençons par le commencement.
    
1. Dans l’éditeur de rapport, accédez tout d’abord au volet **Champs** à droite de la page pour créer une visualisation. Sélectionnez le champ **Gross Sales**, puis le champ **Date**.
   
   :::image type="content" source="media/service-get-started/power-bi-service-fields-pane-selected.png" alt-text="Capture d’écran de la liste de champs.":::

    Power BI analyse les données et crée une visualisation sous forme d’histogramme. 

    > [!NOTE]
    > Si vous avez sélectionné le champ **Date** en premier à la place du champ **Gross Sales**, vous voyez une table. Pas de souci. Nous allons changer la visualisation à l’étape suivante.

    Des symboles Sigma apparaissent en regard de certains champs, car Power BI a détecté qu’ils contiennent des valeurs numériques.

    :::image type="content" source="media/service-get-started/power-bi-sigma-fields.png" alt-text="Champs avec des symboles Sigma.":::

2. Examinons à présent les données d’une autre façon. Les graphiques en courbes sont de bons visuels pour afficher des valeurs dans le temps. Dans le volet **Visualisations**, sélectionnez l’icône **Graphique en courbes**.
   
   :::image type="content" source="media/service-get-started/power-bi-service-select-line-chart.png" alt-text="Capture d’écran de l’éditeur de rapport avec le graphique en courbes sélectionné.":::

3. Comme ce graphique semble intéressant, nous allons l’*épingler* à un tableau de bord. Pointez sur la visualisation, puis sélectionnez l’icône en forme d’épingle.
   
   :::image type="content" source="media/service-get-started/power-bi-service-pin-visual.png" alt-text="Capture d’écran de l’icône Épingler.":::

4. Comme ce rapport est nouveau, vous êtes invité à l’enregistrer avant de pouvoir épingler une visualisation à un tableau de bord. Donnez un nom à votre rapport (par exemple, *Financial Sample report*), puis sélectionnez **Enregistrer**. 

    Vous examinez à présent le rapport en mode Lecture. 

6. Sélectionnez une nouvelle fois l’icône **Épingler**.
 
5. Sélectionnez **Nouveau tableau de bord** et nommez-le par exemple *Financial Sample dashboard*. 
   
   :::image type="content" source="media/service-get-started/power-bi-pin.png" alt-text="Capture d’écran du nom du tableau de bord.":::
  
    Un message de réussite (en haut à droite) vous indique que la visualisation a été ajoutée sous forme de vignette à votre tableau de bord.
   
    :::image type="content" source="media/service-get-started/power-bi-pin-success.png" alt-text="Boîte de dialogue Épinglé au tableau de bord.":::

    Une fois cette visualisation épinglée, elle est stockée dans votre tableau de bord. Les données restent à jour pour que vous puissiez suivre les dernières valeurs en un coup d’œil. Toutefois, si vous changez de type de visualisation dans le rapport, la visualisation dans le tableau de bord ne change pas.

7. Sélectionnez **Accéder au tableau de bord** pour voir votre nouveau tableau de bord avec le graphique en courbes que vous avez épinglé sous forme de vignette. 
   
   :::image type="content" source="media/service-get-started/power-bi-service-dashboard-tile.png" alt-text="Capture d’écran du tableau de bord avec la visualisation épinglée.":::
   
8. Notez la nouvelle vignette dans votre tableau de bord. Power BI vous renvoie sur le rapport en mode Lecture.

1. Pour revenir en mode Edition, sélectionnez **Plus d’options** (...) dans la barre de menus > **Modifier**.

    :::image type="content" source="media/service-get-started/power-bi-service-edit-report.png" alt-text="Capture d’écran de l’option Modifier sélectionnée pour modifier le rapport.":::

    Une fois en mode Edition, vous pouvez continuer à explorer et à épingler des vignettes.

## <a name="step-3-explore-with-qa"></a>Étape 3 : Explorer avec Questions et réponses

Pour une exploration rapide de vos données, essayez de poser une question dans la zone de Questions et réponses. Questions et réponses vous permet d’exécuter des requêtes en langage naturel sur vos données. Dans un tableau de bord, la zone Questions et réponses est en haut (**Poser une question sur vos données**), sous la barre de menus. Dans un rapport, elle se trouve dans la barre de menus supérieure (**Poser une question**).

1. Pour revenir au tableau de bord, sélectionnez **Mon espace de travail** dans la barre d’en-tête noire de **Power BI**.

    :::image type="content" source="media/service-get-started/power-bi-service-go-my-workspace.png" alt-text="Capture d’écran de Revenir à Mon espace de travail.":::

1. Dans **Mon espace de travail**, sélectionnez votre tableau de bord.

    :::image type="content" source="media/service-get-started/power-bi-service-dashboard-tab.png" alt-text="Capture d’écran de Sélectionner votre tableau de bord.":::

1. Sélectionnez **Poser une question sur vos données**. Questions et réponses propose automatiquement un certain nombre de suggestions. 

    :::image type="content" source="media/service-get-started/power-bi-service-new-qanda.png" alt-text="Capture du canevas Questions et réponses.":::

    > [!NOTE]
    > Si vous ne voyez pas les suggestions, activez **Nouvelle expérience de Questions et réponses**.

    :::image type="content" source="media/service-get-started/power-bi-new-qna-experience.png" alt-text="Capture d’écran de l’activation de Nouvelle expérience Questions et réponses.":::

1. Certaines suggestions retournent une valeur unique. Par exemple, sélectionnez **what is the average cog**.

    Questions et réponses recherche une réponse et la présente sous forme de *carte*.

3. Sélectionnez **Épingler un visuel** et épinglez cette visualisation au tableau de bord Financial Sample.

    :::image type="content" source="media/service-get-started/power-bi-qna-pin-tile.png" alt-text="Capture d’écran de l’épinglage du visuel.":::

1. Revenez à Questions et réponses et sélectionnez **Montrer toutes les suggestions**.
1. Sélectionnez **total profit by country**. 

    :::image type="content" source="media/service-get-started/power-bi-qna-total-profit-country.png" alt-text="Capture d’écran du total des bénéfices par pays.":::

1. Épinglez aussi la carte au tableau de bord Financial Sample.

1. Dans le tableau de bord, sélectionnez la carte que vous venez d’épingler. Questions et réponses s’ouvre à nouveau. 
1. Placez le curseur après *by country* dans la zone Questions et réponses, puis tapez *as bar*. Power BI crée un graphique à barres avec les résultats.

    :::image type="content" source="media/service-get-started/power-bi-qna-profit-country-bar.png" alt-text="Capture d’écran d’une visualisation sous forme de graphique à barres.":::

1. Épinglez aussi le graphique à barres à votre tableau de bord Financial Sample.

4. Sélectionnez **Quitter Questions et réponses** pour revenir sur votre tableau de bord, où vous voyez les nouvelles vignettes que vous avez créées. 

   :::image type="content" source="media/service-get-started/power-bi-service-dashboard-qna.png" alt-text="Capture d’écran du tableau de bord avec les visuels Questions et réponses épinglés.":::

   Même si vous remplacez la carte par un graphique à barres dans Questions et réponses, cette vignette continue à montrer une carte puisque c’est bien une carte que vous avez épinglée. 

## <a name="step-4-reposition-tiles"></a>Étape 4 : Repositionner les vignettes

Nous pouvons réorganiser les vignettes pour optimiser l’utilisation de l’espace du tableau de bord.

1. Faites glisser vers le haut le coin en bas à droite de la vignette du graphique en courbes *Gross Sales*, jusqu’à ce qu’il soit à la même hauteur que la vignette Sales, puis relâchez-le.

    :::image type="content" source="media/service-get-started/power-bi-service-resize-tile.png" alt-text="Capture d’écran du redimensionnement de la vignette.":::

    À présent, les deux vignettes ont la même hauteur.

1. Sélectionnez **Plus d’options (...)** pour la vignette Average of COGS > **Modifier les détails**. 

    :::image type="content" source="media/service-get-started/power-bi-tile-edit-details.png" alt-text="Capture d’écran du menu Plus d’options pour une vignette.":::

1. Dans la zone **Titre**, tapez *Average Cost of Goods Sold* > **Appliquer**.

    :::image type="content" source="media/service-get-started/power-bi-tile-details-dialog.png" alt-text="Capture d’écran de la boîte de dialogue Modifier les détails.":::

1. Réorganisez les autres visuels pour qu’ils tiennent tous à l’écran.

    C’est mieux.

    :::image type="content" source="media/service-get-started/power-bi-service-rearranged-dashboard.png" alt-text="Capture d’écran du tableau de bord réorganisé.":::


## <a name="clean-up-resources"></a>Nettoyer les ressources
Maintenant que vous avez terminé le tutoriel, vous pouvez supprimer le jeu de données, le rapport et le tableau de bord. 

1. Sélectionnez **Mon espace de travail** dans la barre d’en-tête noire de **Power BI**.
2. Sélectionnez **Plus d’options (...)** en regard du jeu de données Financial Sample > **Supprimer**.

    :::image type="content" source="media/service-get-started/power-bi-service-delete-dataset.png" alt-text="Capture d’écran de la suppression du jeu de données.":::

    Vous voyez un avertissement indiquant que **toutes les vignettes de rapport et de tableau de bord contenant des données de ce jeu de données seront également supprimées**.

4. Sélectionnez **Supprimer**.

## <a name="next-steps"></a>Étapes suivantes

Améliorez vos tableaux de bord en ajoutant des vignettes de visualisation et en les [renommant, redimensionnant, associant et repositionnant](../create-reports/service-dashboard-edit-tile.md).
