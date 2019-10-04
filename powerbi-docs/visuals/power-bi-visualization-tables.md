---
title: Visualisations de tableaux dans les rapports et les tableaux de bord Power BI
description: Ce didacticiel explique comment utiliser les visualisations de tableaux dans les rapports et les tableaux de bord Power BI, et notamment comment redimensionner la largeur des colonnes.
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/24/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 65410dc15600307ba11a2c48db1689be5a458383
ms.sourcegitcommit: e2de2e8b8e78240c306fe6cca820e5f6ff188944
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71193128"
---
# <a name="tables-in-power-bi-reports-and-dashboards"></a>Tableaux dans les rapports et les tableaux de bord Power BI

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Un tableau est une grille qui contient les données connexes dans une série logique de lignes et colonnes. Il peut également contenir des en-têtes et une ligne de totaux. Les tableaux fonctionnent correctement avec des comparaisons quantitatives où vous examinez de nombreuses valeurs pour une même catégorie. Par exemple, ce tableau montre cinq mesures différentes pour la **Catégorie**.

![Capture d’un tableau qui montre cinq mesures différentes pour la Catégorie.](media/power-bi-visualization-tables/power-bi-table-grid3.png)

Créez des tables dans les rapports et mettez les éléments en surbrillance croisée dans la table avec d’autres visuels sur la même page de rapport. Vous pouvez également sélectionner des lignes, colonnes et cellules pour les mettre en évidence croisée. Vous pouvez aussi copier et coller des sélections de cellules individuelles et de plusieurs cellules dans d’autres applications.

## <a name="when-to-use-a-table"></a>Quand utiliser un tableau ?

Les tableaux sont recommandés :

* pour afficher et comparer des données détaillées et des valeurs exactes (au lieu de représentations visuelles) ;

* pour afficher des données dans un format tabulaire ;

* pour afficher des données numériques par catégories.

## <a name="prerequisite"></a>Prérequis

Ce tutoriel utilise le [fichier PBIX de l’exemple Analyse de la vente au détail](http://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix).

1. Dans la section supérieure gauche de la barre de menus, sélectionnez **Fichier** > **Ouvrir**.
   
2. Rechercher votre copie du **fichier PBIX de l’exemple Analyse de la vente au détail**

1. Ouvrez le **fichier PBIX de l’exemple Analyse de la vente au détail** dans la vue Rapport ![Capture d’écran de l’icône de la vue Rapport.](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Sélectionner ![Capture d’écran de l’onglet jaune.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) pour ajouter une nouvelle page.


## <a name="create-a-table"></a>Créer un tableau

Vous allez créer le tableau illustré au début de cet article pour afficher les valeurs de ventes par catégorie d’article.


1. Dans le volet **Champs**, sélectionnez **Élément** > **Catégorie**.

    Power BI crée automatiquement un tableau qui répertorie toutes les catégories.

    ![résultat de l’ajout de Catégorie](media/power-bi-visualization-tables/power-bi-table1.png)

1. Sélectionnez **Ventes > Prix unitaire moyen** et **Ventes > Ventes de l’année dernière**

1. Puis sélectionnez **Ventes > Ventes de l’année** et choisissez les trois options : **Valeur**, **Objectif**, et **Statut**.

1. Dans le volet **Visualisations**, localisez la zone **Valeurs**, puis sélectionnez les valeurs jusqu’à ce que l’ordre des colonnes du graphique corresponde à la première image de cette page. Faites glisser les valeurs dans la zone si nécessaire. La zone **Valeurs** doit ressembler à ceci :

    ![zone Valeurs](media/power-bi-visualization-tables/power-bi-table2.png)


## <a name="format-the-table"></a>Mettre en forme le tableau

Il existe de nombreuses façons de mettre en forme un tableau. Cet article n’en couvre que quelques-unes. Un excellent moyen d’en apprendre davantage sur les autres options de mise en forme consiste à ouvrir le volet **Mise en forme** (icône de ![rouleau à peindre](media/power-bi-visualization-tables/power-bi-format.png)), puis à explorer les options.

* Essayez de mettre en forme la grille du tableau. Nous allons appliquer ici un quadrillage vertical de couleur bleue, ajouter de l’espace aux lignes, et augmenter la taille de contour et de texte.

    ![carte Grille](media/power-bi-visualization-tables/power-bi-table-gridnew.png)

    ![tableau montrant les résultats](media/power-bi-visualization-tables/power-bi-table-grid3.png)

* Pour les en-têtes de colonne, modifiez la couleur d’arrière-plan, ajoutez un contour et augmentez la taille de la police.

    ![Carte En-têtes de colonne](media/power-bi-visualization-tables/power-bi-table-column-headers.png)

    ![mise en forme des en-têtes dans un tableau](media/power-bi-visualization-tables/power-bi-table-column2.png)

* Vous pouvez même appliquer la mise en forme aux colonnes individuelles et aux en-têtes de colonnes. Commencez par développer **Mise en forme des champs** et sélectionnez la colonne à mettre en forme dans la liste déroulante. Selon les valeurs des colonnes, **Mise en forme des champs** vous permet de définir des éléments tels que : unités d’affichage, couleur de police, nombre de places décimales, arrière-plan, alignement et bien plus encore. Une fois que vous avez ajusté les paramètres, décidez s’il faut appliquer ces paramètres à l’en-tête et à toutes les lignes également.

    ![Mise en forme des champs pour Ventes de cette année](media/power-bi-visualization-tables/power-bi-field-formatting.png)

    ![Mise en forme des champs pour Ventes de cette année dans le tableau](media/power-bi-visualization-tables/power-bi-field-formatting-1.png)

* Après quelques retouches supplémentaires de la mise en forme, voici notre tableau final.

    ![tableau avec toutes les mises en forme à ce stade](media/power-bi-visualization-tables/power-bi-table-format.png)

### <a name="conditional-formatting"></a>Mise en forme conditionnelle

*Mise en forme conditionnelle* est un type de mise en forme. Power BI applique une mise en forme conditionnelle aux champs de la section **Valeurs** du volet **Visualisations**.

Dans le contexte des tables, la mise en forme conditionnelle vous permet de spécifier des couleurs personnalisées d’arrière-plan et de police de cellule en fonction des valeurs de cellule, notamment en utilisant des couleurs de dégradé.

1. Dans le volet **Visualisations**, sélectionnez l’icône **Champs** ![icône champs](media/power-bi-visualization-tables/power-bi-fields-icon.png).

1. Sélectionnez la flèche vers le bas en regard de la valeur dans la zone de configuration **Valeurs** que vous voulez mettre en forme (ou cliquez avec le bouton droit sur le champ).

    > [!NOTE]
    > Vous pouvez uniquement gérer la mise en forme conditionnelle des champs dans la zone **Valeurs** de la zone **Champs**.

    ![chemin permettant d’accéder à Échelles de couleurs de l’arrière-plan](media/power-bi-visualization-tables/power-bi-conditional-formatting-background.png)

1. Sélectionnez **Couleur d’arrière-plan**.

1. Dans la boîte de dialogue qui s’affiche, vous pouvez configurer la couleur, ainsi que les valeurs **Minimum** et **Maximum**. Si vous sélectionnez l’option **Divergent**, vous pouvez également configurer une valeur **Centrale** en option.

    ![écran Échelles de couleurs de l’arrière-plan](media/power-bi-visualization-tables/power-bi-conditional-formatting-background2.png)

    Nous allons appliquer une mise en forme personnalisée à nos valeurs de prix unitaire moyen. Sélectionnez **Divergent**, ajoutez des couleurs, puis choisissez **OK**.

    ![tableau montrant des couleurs divergentes](media/power-bi-visualization-tables/power-bi-conditional-formatting-data-background.png)
1. Ajoutez au tableau un nouveau champ contenant des valeurs positives et négatives. Sélectionnez **Sales > Total Sales Variance** (Ventes > Écart total sur les ventes).

    ![montre un nouveau champ à droite](media/power-bi-visualization-tables/power-bi-conditional-formatting2.png)

1. Ajoutez à la barre de données une mise en forme conditionnelle en sélectionnant la flèche vers le bas en regard de **Total Sales Variance**, puis en choisissant **Mise en forme conditionnelle > Barres de données**.

    ![chemin permettant d’accéder à Barres de données](media/power-bi-visualization-tables/power-bi-conditional-formatting-data-bars.png)

1. Dans la boîte de dialogue qui s’affiche, définissez des couleurs pour la **Barre positive** et la **Barre négative**, sélectionnez l’option **Afficher seulement la barre**, puis apportez d’autres modifications souhaitées.

    ![Afficher uniquement la barre coché](media/power-bi-visualization-tables/power-bi-data-bars.png)

1. Sélectionnez **OK**.

    Des barres de données remplacent les valeurs numériques dans le tableau, rendant celui-ci plus lisible.

    ![même tableau mais avec des barres dans la dernière colonne](media/power-bi-visualization-tables/power-bi-conditional-formatting-data-bars2.png)

Si vous souhaitez supprimer la mise en forme conditionnelle d’une visualisation, cliquez à nouveau avec le bouton droit sur le champ et de sélectionner **Supprimer la mise en forme conditionnelle**.

> [!TIP]
> L’option Mise en forme conditionnelle est également disponible dans le volet **Mise en forme**. Sélectionnez la valeur à mettre en forme, puis **activez** les options **Échelles de couleurs** ou **Barres de données** pour appliquer les paramètres par défaut. Ou bien, pour personnaliser les paramètres, sélectionnez **Contrôles avancés**.

## <a name="copy-values-from-power-bi-tables-for-use-in-other-applications"></a>Copier les valeurs à partir des tables Power BI pour une utilisation dans d’autres applications

Votre table ou matrice peut avoir un contenu que vous aimeriez utiliser dans d’autres applications, comme Dynamics CRM, Excel et même d’autres rapports Power BI. Dans Power BI, lorsque vous cliquez avec le bouton droit dans une cellule, vous pouvez copier les données d’une cellule unique ou d’une sélection de cellules dans votre Presse-papiers et les coller dans d’autres applications.

Pour copier la valeur d’une cellule unique :

1. Sélectionnez la cellule que vous voulez copier.

1. Cliquez avec le bouton droit de la souris dans la cellule.

1. Sélectionnez **Copier** > **Copier la valeur**.

    ![options de copie](media/power-bi-visualization-tables/power-bi-copy-value.png)

    Avec la valeur de cellule non mise en forme dans votre Presse-papiers, vous pouvez la coller dans une autre application.

Pour copier plusieurs cellules :

1. Sélectionnez une plage de cellules ou utilisez la touche **Ctrl** pour choisir une ou plusieurs cellules.

1. Cliquez avec le bouton droit de la souris à l’intérieur d’une des cellules que vous avez sélectionnées.

1. Sélectionnez **Copier** > **Copier la sélection**.

    ![options de copie](media/power-bi-visualization-tables/power-bi-copy-selection.png)

## <a name="adjust-the-column-width-of-a-table"></a>Ajustez la largeur de colonne d’un tableau

Parfois, Power BI tronque l’en-tête d’une colonne dans un tableau de bord et sur un rapport. Pour afficher le nom entier de la colonne, placez le pointeur au-dessus de l’espace à droite de l’en-tête pour faire apparaître les doubles flèches, puis sélectionnez-les et faites-les glisser.

![gros plan vidéo sur le redimensionnement de colonne](media/power-bi-visualization-tables/resizetable.gif)

## <a name="considerations-and-troubleshooting"></a>Considérations et résolution des problèmes

Quand vous appliquez une mise en forme de colonne, vous ne pouvez choisir qu’une option d’alignement par colonne : **Automatique**, **Gauche**, **Centre**, **Droite**. Habituellement, une colonne ne contient que du texte ou que des nombres, mais pas une combinaison des deux. Dans les cas où une colonne contient à la fois des nombres et du texte, **Automatique** aligne le texte à gauche et les nombres à droite. Ce comportement prend en charge les langues qui se lisent de gauche à droite.

## <a name="next-steps"></a>Étapes suivantes

* [Treemap dans Power BI](power-bi-visualization-treemaps.md)

* [Types de visualisation dans Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)
