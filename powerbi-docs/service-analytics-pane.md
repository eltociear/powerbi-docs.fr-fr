---
title: Volet Analyse du service Power BI
description: "Créer des lignes de référence dynamiques pour des visuels dans le service Power BI"
services: powerbi
documentationcenter: 
author: mihart
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
ms.date: 05/02/2017
ms.author: mihart
ms.openlocfilehash: 30fc0731f819f063aa04e856e8acc75a69f64a59
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2017
---
# <a name="analytics-pane-in-power-bi-service"></a>Volet Analyse du service Power BI
Avec le volet **Analyse** de **Service Power BI**, vous pouvez ajouter des *lignes de référence* dynamiques aux visualisations et mettre en relief les analyses ou les tendances importantes.

![](media/service-analytics-pane/power-bi-analytics-pane.png)

> [!NOTE]
> Le volet **Analyse** s’affiche uniquement quand vous sélectionnez un visuel sur le canevas de rapport.
> 
> 

## <a name="using-the-analytics-pane"></a>Utilisation du volet Analyse
Avec le volet **Analyse**, vous pouvez créer les types de lignes de référence dynamiques (toutes les lignes ne sont pas disponibles pour tous les types d’éléments visuels) suivants :

* Ligne de constante de l’axe X
* Ligne de constante de l’axe Y
* Ligne Min
* Ligne Max
* Ligne moyenne
* Ligne médiane
* Ligne Centile

Les sections suivantes montrent comment vous pouvez utiliser le volet **Analyse** et les lignes de référence dynamiques dans vos visualisations.

Pour afficher les lignes de référence dynamiques pour un élément visuel, procédez comme suit :

1. Sélectionnez ou créez un visuel, puis sélectionnez l’icône **Analyse** ![](media/service-analytics-pane/power-bi-analytics-icon.png)dans le volet **Visualisations**.
2. Sélectionnez la flèche vers le bas pour le type de ligne que vous souhaitez créer afin de développer ses options. Dans ce cas, nous allons sélectionner **Ligne moyenne**.
   
   ![](media/service-analytics-pane/power-bi-add.png)
3. Pour créer une ligne, sélectionnez **+ Ajouter**. Vous pouvez ensuite spécifier un nom pour la ligne en double-cliquant sur la zone de texte, puis en entrant votre nom.
   
   Il existe toutes sortes d’options de ligne. Vous pouvez sélectionner sa *couleur*, sa *transparence*, son *style* et sa *position* (par rapport à des éléments de données de l’élément visuel) et l’ajout de l’étiquette. Et surtout, vous pouvez sélectionner la **mesure** sur laquelle sera fondée votre ligne dans l’élément visuel, dans la liste déroulante **Mesure**, qui est automatiquement remplie avec les éléments de données de l’élément visuel. Dans ce cas, nous allons sélectionner *Open store count* (Nombre de magasins ouverts) comme mesure, lui attribuer une étiquette *Avg # Open Stores* (Nombre moyen de magasins ouverts) et personnaliser certaines des autres options, comme indiqué ci-dessous.
   
   ![](media/service-analytics-pane/power-bi-average-line.png)
4. Si vous souhaitez afficher une étiquette de données, déplacez le curseur de l’**étiquette de données**. En procédant ainsi, vous obtenez un grand nombre d’options supplémentaires pour l’étiquette de données.
5. Notez le numéro qui s’affiche en regard de l’élément **Ligne moyenne** dans le volet **Analyse**. Ce dernier indique le nombre de lignes dynamiques dont vous disposez actuellement sur votre élément visuel, ainsi que leur type. Si vous ajoutez une **Ligne de constante** en tant qu’objectif de nombre de magasins (9), vous pouvez voir que le volet **Analyse** affiche à présent également une ligne de référence **Ligne de constante** appliquée à ce visuel.
   
   ![](media/service-analytics-pane/power-bi-reference-lines.png)
   
   Si l’élément visuel que vous avez sélectionné ne peut comporter de lignes de référence dynamiques (dans ce cas, un élément visuel **Carte**), vous verrez les éléments suivants en sélectionnant le volet **Analyse**.
   
   ![](media/service-analytics-pane/power-bi-no-lines.png)

Vous pouvez mettre en relief des analyses intéressantes en créant des lignes de référence dynamiques avec le volet **Analyse**.

Nous prévoyons d’ajouter davantage de fonctionnalités, notamment le développement d’éléments visuels auxquels peuvent s’appliquer des lignes de référence dynamiques, n’hésitez pas à revenir consulter les nouveautés.

## <a name="limitations"></a>Limites
La possibilité d’utiliser des lignes de référence dynamiques est basée sur le type d’élément visuel utilisé. La liste suivante affiche les lignes dynamiques qui sont actuellement disponibles pour des éléments visuels donnés :

L’utilisation complète des lignes dynamiques est disponible sur les éléments visuels suivants :

* Graphique en aires
* Graphique en courbes
* Nuage de points
* Histogramme groupé
* Graphique à barres groupées

Les éléments visuels suivants peuvent utiliser uniquement une *ligne de constante* à partir du volet **Analyse** :

* Aires empilées
* Barres empilées
* Histogrammes empilés
* Barres empilées 100 %
* Histogrammes empilés 100 %

Pour les éléments visuels suivants, une *courbe de tendance* est actuellement la seule option :

* Ligne non empilée
* Histogramme groupé

Enfin, les éléments visuels non cartésiens ne peuvent pas appliquer actuellement des lignes dynamiques à partir du volet **Analyse**, par exemple :

* Matrice
* Graphique en secteurs
* Graphique en anneau
* Table

## <a name="next-steps"></a>Étapes suivantes
[Volet Analyse de Power BI Desktop](desktop-analytics-pane.md)

D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)

