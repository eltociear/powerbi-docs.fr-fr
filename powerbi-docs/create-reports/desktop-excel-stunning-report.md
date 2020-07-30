---
title: 'Tutoriel : Générer un rapport exceptionnel à partir d’un classeur Excel dans Power BI Desktop'
description: Ce tutoriel explique comment créer rapidement un rapport exceptionnel à partir d’un classeur Excel.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 07/21/2020
ms.author: maggies
LocalizationGroup: Data from files
ms.openlocfilehash: b628502ad5658388065a197c1c722a59dd9ad2b4
ms.sourcegitcommit: e9cd61eaa66eda01cc159251d7936a455c55bd84
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "86973014"
---
# <a name="tutorial-from-excel-workbook-to-stunning-report-in-power-bi-desktop"></a>Tutoriel : Générer un rapport exceptionnel à partir d’un classeur Excel dans Power BI Desktop

Dans ce tutoriel, vous allez créer un rapport de bout en bout en 20 minutes. 

Votre responsable souhaite voir un rapport sur vos derniers chiffres de vente. Il vous a demandé un rapport de synthèse de ce qui suit : 

- En quel mois et quelle année les bénéfices ont-ils été les plus élevés ? 
- Où la société rencontre-t-elle le plus de succès (par pays) ? 
- Dans quel produit et quel segment l’entreprise doit-elle continuer à investir ? 

À l’aide de notre exemple de classeur financier, nous pouvons générer ce rapport en un rien de temps. Voici à quoi ressemblera le rapport final : Allons-y ! 

:::image type="content" source="media/desktop-excel-stunning-report/power-bi-excel-formatted-report.png" alt-text="Capture d’écran du rapport Power BI dans le service Power BI."::: 

Dans ce tutoriel, vous allez découvrir comment :

> [!div class="checklist"]
> * Télécharger les exemples de données.
> * Préparer vos données avec quelques transformations.
> * Créer un rapport avec un titre, trois visuels et un segment.
> * Publier votre rapport sur le service Power BI pour pouvoir le partager avec vos collègues.

## <a name="prerequisites"></a>Prérequis

- Avant de commencer, vous devez [télécharger Power BI Desktop](https://powerbi.microsoft.com/desktop/).
- Si vous envisagez de publier votre rapport sur le service Power BI et que vous n’êtes pas encore inscrit, [inscrivez-vous pour obtenir un essai gratuit](https://app.powerbi.com/signupredirect?pbi_source=web).

## <a name="download-the-sample"></a>Télécharger l’exemple

Pour suivre la procédure, vous devez télécharger l’exemple de classeur. 

1. Téléchargez l’[exemple de classeur Excel « Financial Sample »](https://go.microsoft.com/fwlink/?LinkID=521962).
1. Ouvrez Power BI Desktop.
1. Dans la section **Données** du ruban **Accueil**, sélectionnez **Excel**.
1. Accédez à l’emplacement où vous avez enregistré l’exemple de classeur, puis sélectionnez **Ouvrir**.

## <a name="prepare-your-data"></a>Préparer vos données 

Dans le **Navigateur**, vous avez la possibilité de *transformer* ou de *charger* les données. Le Navigateur fournit un aperçu de vos données pour vous permettre de vérifier que vous disposez de la plage de données appropriée. Les types de données numériques sont en italique. Si vous devez apporter des modifications, transformez vos données avant le chargement. Pour faciliter la lecture des visualisations par la suite, nous voulons transformer les données maintenant. À mesure que vous effectuez chaque transformation, celle-ci est ajoutée à la liste sous **Paramètres de requête** dans **Étapes appliquées**. 

1. Sélectionnez la table **Financials**, puis choisissez **Transformer les données**. 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-financial-navigator.png" alt-text="Capture d’écran du Navigateur Power BI avec des exemples de données financières."::: 

1. Sélectionnez la colonne **Units Sold** (Unités vendues). Sous l’onglet **Accueil**, sélectionnez **Type de données**, puis **Nombre entier**. Choisissez **Remplacer l’actuelle** pour changer le type de colonne. 

    L’étape de nettoyage des données effectuée le plus souvent par les utilisateurs consiste à changer les types de données. Ici, les unités vendues sont au format décimal. Cela n’a pas vraiment de sens d’avoir 0,2 ou 0,5 unité vendue, n’est-ce pas ? Nous allons donc remplacer cela par des nombres entiers. 

    :::image type="content" source="media/desktop-excel-stunning-report/power-query-whole-number.png" alt-text="Capture d’écran de la modification d’un nombre décimal en nombre entier."::: 

1. Sélectionnez la colonne **Segment**. Sous l’onglet **Transformer**, sélectionnez **Format**, puis **MAJUSCULES**.

    Nous souhaitons également rendre les segments plus faciles à voir dans le graphique par la suite. Nous allons mettre en forme la colonne Segment. 

     :::image type="content" source="media/desktop-excel-stunning-report/power-query-upper-case.png" alt-text="Capture d’écran de la modification des en-têtes minuscules en majuscules.":::

1. Remplaçons le nom de la colonne (**Month Name**) par **Month**. Double-cliquez sur la colonne **Month Name**, puis renommez-la **Month**.  

     :::image type="content" source="media/desktop-excel-stunning-report/power-query-month-name.png" alt-text="Capture d’écran du changement de nom de la colonne.":::

1. Dans la colonne **Product**, sélectionnez la liste déroulante et décochez la case en regard de **Montana**. 

     Nous savons que le produit Montana a été abandonné le mois dernier. Nous souhaitons donc filtrer et supprimer ces données de notre rapport pour éviter toute confusion. 

     :::image type="content" source="media/desktop-excel-stunning-report/power-query-montana.png" alt-text="Capture d’écran de la suppression des valeurs Montana.":::

1. Vous constatez que chaque transformation a été ajoutée à la liste sous **Paramètres de requête** dans **Étapes appliquées**.

    :::image type="content" source="media/desktop-excel-stunning-report/power-query-applied-steps.png" alt-text="Capture d’écran de la liste des étapes appliquées.":::

1. De retour sous l’onglet **Accueil**, sélectionnez **Fermer et appliquer**. Nos données sont presque prêtes pour la création d’un rapport. 

    Vous voyez le symbole Sigma dans la liste Champs ? Power BI a détecté que ces champs sont numériques. Power BI indique également le champ de date avec un symbole de calendrier.

     :::image type="content" source="media/desktop-excel-stunning-report/power-bi-fields-list-sigmas-date.png" alt-text="Capture d’écran de la liste Champs avec des champs numériques et un champ de date.":::

### <a name="extra-credit-write-a-measure-in-dax"></a>Crédit supplémentaire : Écrire une mesure en DAX

L’écriture de *mesures* dans le langage de formule *DAX* est super puissante pour la modélisation des données. Il y a beaucoup à apprendre sur DAX dans la documentation de Power BI. Pour le moment, nous allons écrire une mesure de base et joindre deux tables. 

1. Sélectionnez **Vue de données** sur la gauche. 
 
    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-data-view.png" alt-text="Capture d’écran de l’icône Vue de données.":::

1. Dans le ruban **Accueil**, sélectionnez **Nouvelle table**. 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-new-table.png" alt-text="Capture d’écran de l’icône Nouvelle table.":::

1. Tapez cette mesure pour générer une table de calendrier de toutes les dates comprises entre le 1er janvier 2013 et le 31 décembre 2014.  

    `Calendar = CALENDAR(DATE(2013,01,01),Date(2014,12,31))` 

2. Cochez la case pour valider.

     :::image type="content" source="media/desktop-excel-stunning-report/power-bi-dax-expression.png" alt-text="Capture d’écran de l’expression DAX.":::

1. À présent, sélectionnez **Vue du modèle** sur la gauche. 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-model-view.png" alt-text="Capture d’écran de l’icône Vue du modèle.":::

1. Faites glisser le champ **Date** de la table Financials vers le champ **Date** de la table Calendar pour joindre les tables, puis créez une *relation* entre elles.  

     :::image type="content" source="media/desktop-excel-stunning-report/power-bi-date-relationship.png" alt-text="Capture d’écran de la relation entre les champs Date.":::

## <a name="build-your-report"></a>Créer votre rapport 

Maintenant que vous avez transformé et chargé vos données, vous pouvez créer votre rapport. Dans le volet Champs à droite figurent les champs du modèle de données que vous avez créé. 

Nous allons créer le rapport final, un visuel à la fois. 

:::image type="content" source="media/desktop-excel-stunning-report/power-bi-report-by-numbers.png" alt-text="Capture d’écran de tous les éléments du rapport, par nombre.":::

### <a name="visual-1-add-a-title"></a>Visuel 1 : Ajouter un titre 

1. Dans le ruban **Insertion**, sélectionnez **Zone de texte**. Tapez « Rapport de synthèse – Rapport financier ». 
1. Sélectionnez le texte que vous avez tapé. Affectez la valeur 20 à la taille de police et appliquez la mise en gras. 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-title-executive-summary.png" alt-text="Capture d’écran de la mise en forme du titre.":::

1. Dans le volet Visualisations, basculez l’**Arrière-plan** sur **Désactivé**. 
1. Redimensionnez la zone pour qu’elle tienne sur une seule ligne. 

### <a name="visual-2-profit-by-date"></a>Visuel 2 : Bénéfices par date 

À présent, nous allons créer un graphique en courbes pour voir le mois et l’année où le bénéfice a été le plus élevé. 

1. À partir du volet Champs, faites glisser le champ **Profit** vers une zone vide sur le canevas de rapport. Par défaut, Power BI affiche un histogramme avec une colonne, Profit. 
1. Faites glisser le champ **Date** vers le même visuel. Power BI met à jour l’histogramme pour afficher le bénéfice des deux années.

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-column-year.png" alt-text="Capture d’écran de l’histogramme de bénéfices.":::

1. Dans la section **Champs** du volet Visualisations, sélectionnez la liste déroulante dans la valeur **Axe**. Modifiez **Date** en remplaçant **Hiérarchie de dates** par **Date**.

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-date-hierarchy.png" alt-text="Capture d’écran du remplacement de Hiérarchie de dates par Date.":::

    Power BI met à jour l’histogramme pour afficher les bénéfices pour chaque mois.

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-column-month.png" alt-text="Capture d’écran de l’histogramme par mois.":::

1. Dans le volet Visualisations, choisissez le type de visualisation **Graphique en courbes**. 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-profit-date-line-chart.png" alt-text="Capture d’écran de la sélection de graphique à barres.":::

    Maintenant, il est facile de voir que les bénéfices ont été le plus élevé en décembre 2014.

### <a name="visual-3-profit-by-country"></a>Visuel 3 : Bénéfices par pays 

Créez une carte pour voir dans quel pays les bénéfices ont été les plus élevés.

1. À partir du volet Champs, faites glisser le champ **Country** dans une zone vide de votre canevas de rapport pour créer une carte.
1. Faites glisser le champ **Profit** sur la carte.

    Power BI crée un élément visuel de type Carte dont les bulles représentent les bénéfices relatifs de chaque emplacement. 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-map-visual.png" alt-text="Capture d’écran de la création d’un graphique de carte.":::

    L’Europe semble générer plus de bénéfices que l’Amérique du Nord. 

### <a name="visual-4-sales-by-product-and-segment"></a>Visuel 4 : Ventes par produit et segment 

Créez un graphique à barres pour déterminer dans quels segments et sociétés il faut investir.

1. Faites glisser les deux graphiques que vous avez créés pour qu’ils soient côte à côte dans la moitié supérieure du canevas. Conservez un peu d’espace sur le côté gauche du canevas. 
1. Sélectionnez une zone vide dans la moitié inférieure de votre canevas de rapport. 

1. Dans le volet Champs, sélectionnez les champs **Sales**, **Product** et **Segment**. 

    Power BI crée automatiquement un histogramme groupé. 

1. Faites glisser le graphique pour qu’il soit suffisamment large pour remplir l’espace sous les deux graphiques du haut.

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-clustered-column-chart.png" alt-text="Capture d’écran d’un histogramme groupé.":::

    Il semble que l’entreprise doive continuer à investir dans le produit Paseo et à cibler les secteurs Small Business et Government.  

### <a name="visual-5-year-slicer"></a>Visuel 5 : Segment d’année 

Les segments sont un outil précieux pour filtrer les visuels d’une page de rapport à une sélection spécifique. Ici, nous pouvons créer un segment pour examiner en détail les performances de chaque mois et année.  

1. Dans le volet Champs, sélectionnez le champ **Date** et faites-le glisser vers la zone vide à gauche du canevas. 
2. Dans le volet Visualisations , choisissez **Segment**. 
3. Dans la section Champs du volet Visualisations, sélectionnez la liste déroulante dans **Champs**. Supprimez Quarter et Day pour que seules Year et Month soient conservés. 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-date-hierarchy-trim.png" alt-text="Capture d’écran de la modification de la hiérarchie de dates.":::

4. Développez chaque année et redimensionnez le visuel afin que tous les mois soient visibles.

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-hierarchy-date-slicer.png" alt-text="Capture d’écran du segment de hiérarchie de dates.":::

Maintenant, si votre responsable souhaite voir uniquement les données de 2013, vous pouvez utiliser le segment pour basculer d’une année à une autre ou vers des mois spécifiques de chaque année. 

### <a name="extra-credit-format-the-report"></a>Crédit supplémentaire : Mettre en forme le rapport

Si vous souhaitez appliquer une légère mise en forme à ce rapport pour le rendre un peu plus attrayant, voici quelques étapes simples à effectuer. 

**Thème**

- Dans le ruban **Affichage**, choisissez le thème **Executive**.  

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-theme-executive.png" alt-text="Capture d’écran de la sélection du thème Executive."::: 

**Embellir les visuels** 

Apportez les modifications suivantes sous l’onglet **Format** dans le volet Visualisations.

:::image type="content" source="media/desktop-excel-stunning-report/power-bi-format-tab-visualizations.png" alt-text="Capture d’écran de l’onglet Format dans le volet Visualisations.":::

1. Sélectionnez le visuel 2. Dans la section **Titre**, remplacez **Texte du titre** par « Bénéfices par mois et par année » et choisissez une **Taille du texte** de **16 pt**. Basculez **Ombre** sur **Activé**. 

1. Sélectionnez le visuel 3. Dans la section **Styles de la carte**, choisissez **Nuances de gris** comme **Thème**. Dans la section **Titre**, choisissez une **Taille du texte** de **16 pt**. Basculez **Ombre** sur **Activé**.

1. Sélectionnez le visuel 4. Dans la section **Titre**, choisissez une **Taille du texte** de **16 pt**. Basculez **Ombre** sur **Activé**.

1. Sélectionnez le visuel 5. Dans la section **Contrôles de sélection**, basculez **Afficher l’option « Tout sélectionner »** sur **Activé**. Dans la section **En-tête de segment**, augmentez la **Taille du texte** à **16 pt**. 

**Ajouter une forme d’arrière-plan pour le titre**

1. Dans le ruban **Insertion**, sélectionnez **Formes** > **Rectangle**. Placez-le en haut de la page et étirez-le pour qu’il occupe toute la largeur de la page et la hauteur du titre. 
1. Dans le volet **Format de la forme**, dans la section **Ligne**, affectez la valeur **100%** à la **Transparence**. 
1. Dans la section **Remplissage**, choisissez **Couleur de thème 5 #6B91C9** (bleu) comme **Couleur de remplissage**. 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-theme-color-5.png" alt-text="Capture d’écran de la couleur de thème 5.":::

1. Sous l’onglet **Format**, sélectionnez **Reculer** > **Mettre en arrière-plan**. 
1. Sélectionnez le texte du visuel 1, le titre, et remplacez la couleur de la police par **Blanc**. 

**Ajouter une forme d’arrière-plan pour les visuels 2 et 3**

1. Dans le ruban **Insertion**, sélectionnez **Formes** > **Rectangle**, puis étirez-le pour qu’il occupe toute la largeur et la hauteur des visuels 2 et 3. 
1. Dans le volet **Format de la forme**, dans la section **Ligne**, affectez la valeur **100%** à la **Transparence**. 
1. Sous l’onglet **Format**, sélectionnez **Reculer** > **Mettre en arrière-plan**. 

### <a name="finished-report"></a>Rapport terminé

Voici à quoi ressemblera votre rapport finalisé :  

:::image type="content" source="media/desktop-excel-stunning-report/power-bi-excel-formatted-report.png" alt-text="Capture d’écran du rapport final mis en forme.":::

En résumé, ce rapport répond aux principales questions de votre responsable : 

- En quel mois et quelle année les bénéfices ont-ils été les plus élevés ? 

    Décembre 2014 

- Dans quel pays la société rencontre-t-elle le plus de succès ? 

    En Europe, plus précisément en France et en Allemagne. 

- Dans quel produit et quel segment l’entreprise doit-elle continuer à investir ? 

    L’entreprise doit continuer à investir dans le produit Paseo et à cibler les secteurs Small Business et Government. 

## <a name="save-your-report"></a>Enregistrer votre rapport

- Dans le menu **Fichier**, sélectionnez **Enregistrer**.

## <a name="publish-to-the-power-bi-service-to-share"></a>Publier sur le service Power BI en vue du partage 

Pour partager votre rapport avec votre responsable et vos collègues, publiez-le sur le service Power BI. Quand vous partagez avec des collègues disposant d’un compte Power BI, ils peuvent interagir avec votre rapport, mais ne peuvent pas enregistrer les modifications. 

1. Dans Power BI Desktop, sélectionnez **Publier** dans le ruban **Accueil**. 

    Vous devrez peut-être vous connecter au service Power BI. Si vous n’avez pas encore de compte, vous pouvez demander un [essai gratuit](https://app.powerbi.com/signupredirect?pbi_source=web).

1. Sélectionnez une destination, par exemple **Mon espace de travail** dans le service Power BI > **Sélectionner**.
1. Sélectionnez **Ouvrir « nom_de_votre_fichier » dans Power BI**.

    :::image type="content" source="media/desktop-excel-stunning-report/open-power-bi.png" alt-text="Capture d’écran de l’ouverture de votre rapport dans le service Power BI.":::

    Votre rapport s’ouvre dans le navigateur.

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-excel-report-service.png" alt-text="Capture d’écran du rapport Power BI dans le service Power BI."::: 

1. Sélectionnez **Partager** en haut du rapport pour le partager avec d’autres utilisateurs.

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-share-report.png" alt-text="Capture d’écran du partage de votre rapport à partir du service Power BI.":::

## <a name="next-steps"></a>Étapes suivantes

- [Tutoriel : Analyser des données de vente à partir d’Excel et d’un flux OData](../connect-data/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed.md)

D’autres questions ? [Posez vos questions à la Communauté Power BI](https://community.powerbi.com/).
