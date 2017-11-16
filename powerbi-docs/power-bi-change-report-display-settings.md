---
title: "Modifier la taille d’une page de rapport (didacticiel)"
description: "Didacticiel : modifier les paramètres d’affichage d’une page dans un rapport Power BI"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: modifying
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/25/2017
ms.author: mihart
ms.openlocfilehash: a5cc05e26012f88e889612788d4479a370063d4f
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2017
---
# <a name="change-the-size-of-a-report-page-tutorial"></a>Modifier la taille d’une page de rapport (didacticiel)
Dans [l’article précédent et la vidéo qui l’accompagne](power-bi-report-display-settings.md), vous avez découvert deux paramètres permettant de contrôler l’affichage des pages dans les rapports Power BI : **Affichage** et **Taille de la page**. Mettons cela en pratique.

## <a name="first-lets-change-the-page-view-setting"></a>Tout d’abord, nous allons modifier le paramètre d’affichage de la page.
1. Ouvrez un rapport en mode Lecture ou en mode Édition. Cet exemple utilise la page « New Stores » (Nouveaux magasins) de l’[Exemple Analyse de la vente au détail](sample-retail-analysis.md).  Cette page s’affiche avec le paramètre **Ajuster à la page** .  Dans ce cas, la page de rapport s’affiche sans barre de défilement, mais certains titres et détails sont difficilement lisibles car trop petits.
   
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
Tous les rapports Power BI sont par défaut en mode **Ajuster à la page**. Mais que se passe-t-il si vous voulez toujours ouvrir cette page de rapport en mode **Taille réelle** ?

1. Dans la page **New stores** (Nouveaux magasins) du rapport, revenez à l’affichage **Taille réelle**.
   
   ![](media/power-bi-change-report-display-settings/power-bi-actual-size.png)
2. Enregistrez le rapport sous un nom différent en sélectionnant **Fichier > Enregistrer sous**. Vous avez maintenant 2 copies de ce rapport. Dans le rapport d’origine, la page **New stores** continue de s’ouvrir dans l’affichage par défaut alors que le nouveau rapport s’ouvre dans l’affichage **Taille réelle**. Voyons ce que cela donne.
   
   ![](media/power-bi-change-report-display-settings/power-bi-save-as.png)
3. Sélectionnez le nom de l’espace de travail en cours dans la barre de navigation supérieure pour revenir à cet espace de travail.  
   
   ![](media/power-bi-change-report-display-settings/power-bi-my-workspace.png)
4. Sélectionnez l’onglet **Rapports**, puis choisissez le nouveau rapport que vous venez de créer (signalé par un astérisque jaune).
   
    ![](media/power-bi-change-report-display-settings/power-bi-new-report2.png)
5. Le rapport s’ouvre dans sa **Taille réelle**.
   
   ![](media/power-bi-change-report-display-settings/power-bi-actal-size2.png)

## <a name="now-lets-explore-the-page-size-setting"></a>Explorons maintenant le paramètre de *taille de la page*.
Les paramètres de taille de page sont disponibles uniquement en [mode Édition](service-interact-with-a-report-in-editing-view.md). Pour ouvrir un rapport en mode Édition, vous devez disposer des autorisations de propriétaire sur ce rapport. Si vous vous êtes connecté à l’un de nos [exemples](sample-datasets.md), vous disposez des autorisations de propriétaire sur ces rapports.

1. Ouvrez la page « District Monthly Sales » (Ventes mensuelles par région) de l’[Exemple Analyse de la vente au détail](sample-retail-analysis.md) en mode Édition.
2. Assurez-vous qu’aucune visualisation n’est sélectionnée sur le canevas.  Dans le volet **Visualisations**, sélectionnez l’icône représentant un rouleau ![](media/power-bi-change-report-display-settings/power-bi-paintroller.png).
3. Sélectionnez **Taille de la page** &gt; **Type** pour afficher les options de taille de page.
   
   ![](media/power-bi-change-report-display-settings/power-bi-page-size-menu-new.png)
4. Sélectionnez **Lettre**.  Sur le canevas, seul le contenu qui s’ajuste au format lettre 816 x 1056 pixels reste affiché dans la partie blanche du canevas.
   
   ![](media/power-bi-change-report-display-settings/power-bi-letter-new.png)
5. Si nous définissons le paramètre **Affichage** à « Ajuster à la largeur », notre canevas affiche désormais uniquement le contenu de la page qui tient dans le format lettre.
   
   ![](media/power-bi-change-report-display-settings/power-bi-fit-to-width-new.png)
6. Sélectionnez **Taille de la page** **Ratio 16:9**.
   
   ![](media/power-bi-change-report-display-settings/power-bi-16-to-9-new.png)
   
   La page du rapport s’affiche dans les proportions suivantes : 16 en largeur par 9 en hauteur. La taille réelle, en pixels, actuellement utilisée est indiquée dans les champs grisés Largeur et Hauteur (1280 x 720). Il y a beaucoup d’espace vide autour du canevas du rapport, car nous avons précédemment défini le paramètre **Affichage** sur « Ajuster à la largeur ».
7. Explorez les autres options **Taille de la page** proposées.

## <a name="using-page-view-and-page-size-together"></a>Utilisation conjointe des paramètres Affichage et Taille de la page
Utilisez les deux paramètres Affichage et Taille de la page pour créer un rapport optimisé lorsqu’il est incorporé dans une autre application.

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

Pour en savoir plus, voir [Rapports dans Power BI](service-reports.md).

D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)

