---
title: Changer la taille d’une page de rapport
description: Changer les paramètres d’affichage d’une page dans un rapport Power BI
author: mihart
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 01/24/2018
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: c2b9a106c4007af868cf69902ce511da8e03e75f
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34244558"
---
# <a name="change-the-size-of-a-report-page"></a>Changer la taille d’une page de rapport
Dans [l’article précédent et la vidéo qui l’accompagne](power-bi-report-display-settings.md), vous avez découvert deux paramètres permettant de contrôler l’affichage des pages dans les rapports Power BI : **Affichage** et **Taille de la page**. Les modes Affichage et Taille de la page sont disponibles dans le service Power BI et dans Power BI Desktop. Ils ont presque le même fonctionnement, mais dans ce didacticiel, nous utilisons le service Power BI.

### <a name="prerequisites"></a>Conditions préalables
- Service Power BI   
- [Rapport Exemple Analyse de la vente au détail](sample-retail-analysis.md)

## <a name="first-lets-change-the-page-view-setting"></a>Tout d’abord, nous allons modifier le paramètre d’affichage de la page.

1. Ouvrez le rapport en mode Lecture ou en mode Édition et sélectionnez l’onglet de rapport correspondant à **New Stores (Nouveaux magasins)**. Par défaut, cette page de rapport s’affiche avec le paramètre **Ajuster à la page**.  Dans ce cas, la page de rapport s’affiche sans barre de défilement, mais certains titres et détails sont difficilement lisibles car trop petits.

   ![](media/power-bi-change-report-display-settings/pbi_fit_to_page.png)
2. Assurez-vous qu’aucune visualisation n’est sélectionnée sur le canevas. Sélectionnez **Affichage** et passez en revue les options d’affichage.

    * En mode Lecture, vous verrez ceci.

     ![](media/power-bi-change-report-display-settings/power-bi-page-view-menu-new.png)
    * En mode Edition, vous verrez ceci.

    ![](media/power-bi-change-report-display-settings/power-bi-view-editing-view.png)

1. Voyons comment la page s’affiche avec le paramètre **Taille réelle**.

   ![](media/power-bi-change-report-display-settings/power-bi-actal-size2.png)

   Pas très bien. Le tableau de bord a maintenant deux barres de défilement.
2. Changez le paramètre en **Ajuster à la largeur**.

   ![](media/power-bi-change-report-display-settings/pbi_fit_to_width.png)

   L’affichage est meilleur. Nous avons maintenant des barres de défilement, mais les détails sont plus faciles à lire.

## <a name="change-the-default-view-for-a-report-page"></a>Modifier l’affichage par défaut d’une page de rapport
Si vous êtes le *créateur* du rapport, vous pouvez modifier l’affichage par défaut de vos pages de rapport. Lorsque vous partagez votre rapport avec d’autres utilisateurs, les pages du rapport s’ouvrent avec l’affichage que vous avez défini. Les *consommateurs* du rapport sont en mesure de modifier l’affichage, mais ils ne peuvent pas enregistrer leurs modifications une fois qu’ils quittent le rapport.

1. Dans la page **New stores** (Nouveaux magasins) du rapport, revenez à l’affichage **Taille réelle**.

   ![](media/power-bi-change-report-display-settings/power-bi-actual-size.png)

2. Sur la page de rapport **District Monthly Sales (Ventes mensuelles par région)**, définissez l’affichage sur **Ajuster à la largeur**.

3. Sur la page de rapport **Vue d’ensemble**, laissez le paramètre d’affichage par défaut.

4. Enregistrez maintenant le rapport en sélectionnant **Fichier > Enregistrer**. À la prochaine ouverture de ce rapport, les pages seront affichées avec les nouveaux paramètres d’affichage. Voyons ce que cela donne.

   ![](media/power-bi-change-report-display-settings/power-bi-save.png)
3. Sélectionnez le nom de l’espace de travail en cours dans la barre de navigation supérieure pour revenir à cet espace de travail.  

   ![](media/power-bi-change-report-display-settings/power-bi-my-workspace.png)
4. Sélectionnez l’onglet **Rapports** et choisissez le même rapport (Exemple Analyse de la vente au détail).

    ![](media/power-bi-change-report-display-settings/power-bi-new-report2.png)
5. Ouvrez chaque page du rapport pour voir les nouveaux paramètres.

   ![](media/power-bi-change-report-display-settings/power-bi-page-view.gif)

## <a name="now-lets-explore-the-page-size-setting"></a>Explorons maintenant le paramètre de *taille de la page*.
Les paramètres de taille de page sont disponibles uniquement en [mode Édition](service-interact-with-a-report-in-editing-view.md). Vous devez donc disposer d’autorisations de modification (*créateur*) sur le rapport pour modifier les paramètres de taille de page. Si vous vous êtes connecté à l’un de nos [exemples](sample-datasets.md), vous disposez des autorisations de *créateur* sur ces rapports.

1. Ouvrez la page « District Monthly Sales » (Ventes mensuelles par région) de l’[Exemple Analyse de la vente au détail](sample-retail-analysis.md) en mode Édition.
2. Assurez-vous qu’aucune visualisation n’est sélectionnée sur le canevas.  Dans le volet **Visualisations**, sélectionnez l’icône représentant un rouleau ![](media/power-bi-change-report-display-settings/power-bi-paintroller.png).
3. Sélectionnez **Taille de la page** &gt; **Type** pour afficher les options de taille de page.

   ![](media/power-bi-change-report-display-settings/power-bi-page-size-menu-new.png)
4. Sélectionnez **Lettre**.  Sur le canevas, seul le contenu qui s’ajuste au format lettre 816 x 1056 pixels reste affiché dans la partie blanche du canevas.

   ![](media/power-bi-change-report-display-settings/power-bi-letter-new.png)
5. Sélectionnez **Taille de la page** **Ratio 16:9**.

   ![](media/power-bi-change-report-display-settings/power-bi-16-to-9-new.png)

   La page du rapport s’affiche dans les proportions suivantes : 16 en largeur par 9 en hauteur. La taille réelle, en pixels, actuellement utilisée est indiquée dans les champs grisés Largeur et Hauteur (1280 x 720). Il y a beaucoup d’espace vide autour du canevas du rapport, car nous avons précédemment défini le paramètre **Affichage** sur « Ajuster à la largeur ».
7. Explorez les autres options **Taille de la page** proposées.

## <a name="use-page-view-and-page-size-together"></a>Utilisation conjointe des paramètres Affichage et Taille de la page
Utilisez les deux paramètres Affichage et Taille de la page pour créer un rapport optimisé lorsqu’il est partagé avec des collègues ou incorporé dans une autre application.

Dans cet exercice, vous allez créer une page de rapport qui s’affiche dans une application qui a de l’espace pour une taille de 500 pixels de large sur 750 pixels de haut.

L'étape précédente rappelle que notre page de rapport s’affiche actuellement en 1 280 x 720 pixels. Nous savons donc que nous allons devoir tout redimensionner et réorganiser si nous voulons que tous nos éléments visuels apparaissent.

1. Redimensionnez et déplacez les éléments visuels afin qu’ils occupent moins de la moitié de la zone de canevas en cours.

    ![](media/power-bi-change-report-display-settings/power-bi-custom-view.gif)
2. Sélectionnez **Taille de la page** &gt; **Personnalisé**.
3. Définissez la largeur sur 500 et la hauteur sur 750.

    ![](media/power-bi-change-report-display-settings/power-bi-custom-new.png)
4. Ajustez la page de rapport afin qu’elle s’affiche de façon optimale. Passez du mode **Affichage > Taille réelle** au mode **Affichage > Ajuster à la page** pour effectuer quelques ajustements.

    ![](media/power-bi-change-report-display-settings/power-bi-final-new.png)

## <a name="next-steps"></a>Étapes suivantes
[Créer des rapports pour Cortana](service-cortana-answer-cards.md)

Revenir à [Paramètres d’affichage de page dans un rapport Power BI](power-bi-report-display-settings.md)

D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)
