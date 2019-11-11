---
title: Paramètres d’affichage de page dans un rapport Power BI
description: Paramètres d’affichage des pages et de mode Page pour un rapport
author: maggiesMSFT
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/29/2019
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: 183ce793342253775f641406620447e7b0f44020
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73875139"
---
# <a name="page-display-settings-in-a-power-bi-report"></a>Paramètres d’affichage de page dans un rapport Power BI
Nous sommes conscients qu’il est essentiel de préserver la qualité de présentation de vos rapports. Cela n’est pas toujours évident, car vous et vos collègues pouvez consulter ces rapports sur des écrans de taille et de proportions différentes. 

L’affichage par défaut est **Ajuster à la page** et la taille d’affichage par défaut est **16:9**. Si vous voulez verrouiller des proportions différentes ou présenter votre rapport d’une autre façon, deux outils peuvent vous y aider : les paramètres de ***mode Page*** et les paramètres ***Taille de la page***.


<iframe width="560" height="315" src="https://www.youtube.com/embed/5tg-OXzxe2g" frameborder="0" allowfullscreen></iframe>


## <a name="where-to-find-page-view-settings-in-the-power-bi-service-and-power-bi-desktop"></a>Emplacement des paramètres de mode Page dans le service Power BI et Power BI Desktop
Les paramètres de mode Page sont disponibles aussi bien dans le service Power BI que dans Power BI Desktop, mais l’interface est un peu différente. Les sections suivantes expliquent où vous pouvez trouver des paramètres d’affichage dans chaque outil Power BI.

### <a name="in-power-bi-desktop"></a>Dans Power BI Desktop
En mode Rapport, sélectionnez l’onglet **Affichage** pour ouvrir les paramètres de mode Page, ainsi que les paramètres du mode téléphone.

  ![Paramètres de mode Page Desktop](media/power-bi-report-display-settings/power-bi-desktop-view-settings.png)

### <a name="in-the-power-bi-service-apppowerbicom"></a>Dans le service Power BI (app.powerbi.com)
Dans le service Power BI, ouvrez un rapport, puis sélectionnez **Affichage** à partir de la barre de menus supérieure gauche.

![Paramètres de mode Page de service](media/power-bi-report-display-settings/power-bi-change-page-view.png)

Les paramètres de mode Page sont disponibles à la fois en [mode Lecture et en mode Édition](consumer/end-user-reading-view.md). En mode Édition, le propriétaire d’un rapport peut affecter des paramètres de mode Page à certaines pages d’un rapport. Ces paramètres sont alors enregistrés avec le rapport. Quand un collègue ouvre ce rapport en mode Lecture, il voit les pages du rapport s’afficher avec les paramètres du propriétaire. En mode Lecture, les collègues peuvent modifier *certains* des paramètres de **mode Page**, mais les modifications ne sont pas enregistrées lorsqu’ils quittent le rapport.

## <a name="page-view-settings"></a>Paramètres de mode Page
Le premier ensemble de paramètres de mode Page contrôle l’affichage de votre page de rapport dans la fenêtre du navigateur. Choisissez parmi les options suivantes :

* **Ajuster à la page** (valeur par défaut) : le contenu est ajusté en fonction de la page
* **Ajuster à la largeur** : le contenu est ajusté en fonction de la largeur de la page
* **Taille réelle** : le contenu est affiché dans sa taille réelle

Le deuxième ensemble de paramètres de mode Page contrôle le positionnement des objets sur le canevas de rapport. Choisissez parmi les options suivantes :

* **Afficher le quadrillage** : activez le quadrillage pour vous aider à positionner les objets sur le canevas de rapport.
* **Aligner sur la grille** : utilisez cette option avec **Afficher le quadrillage** pour positionner et aligner précisément les objets sur le canevas de rapport. 
* **Verrouiller les objets** : verrouillez tous les objets sur le canevas afin qu’ils ne puissent pas être déplacés ni redimensionnés.
* **Volet Sélection** : le volet **Sélection** liste tous les objets sur le canevas. Vous pouvez décider lesquels afficher et masquer.

    ![volet sélection](media/power-bi-report-display-settings/power-bi-selection-pane.png)



## <a name="page-size-settings"></a>Paramètres Taille de la page
![modifier les paramètres de taille de la page](media/power-bi-report-display-settings/power-bi-page-size.png)

Les paramètres **Taille de la page** sont disponibles uniquement pour les propriétaires de rapports. Dans le service Power BI (app.powerbi.com), vous devez donc ouvrir le rapport en [mode Édition](consumer/end-user-reading-view.md). Les paramètres **Taille de la page** figurent dans le volet **Visualisations** et permettent de contrôler les proportions et la taille réelle (en pixels) d’affichage du canevas de rapport :   

* Proportions 4:3
* Proportions 16:9 (par défaut)
* Cortana
* Lettre
* Personnalisé (hauteur et largeur en pixels)

## <a name="next-steps"></a>Étapes suivantes
[Vue Rapport dans Power BI Desktop](desktop-report-view.md)

[Modifier les paramètres de mode Page et Taille de la page dans vos propres rapports Power BI](consumer/end-user-report-view.md)

En savoir plus sur les [rapports dans Power BI](consumer/end-user-reports.md)

[Fondamentaux pour les concepteurs dans le service Power BI](service-basic-concepts.md)

D’autres questions ? [Posez vos questions à la communauté Power BI](https://community.powerbi.com/)

