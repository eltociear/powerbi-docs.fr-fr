---
title: Utilisation du volet Analytique dans Power BI Desktop
description: "Créer des lignes de référence dynamiques pour des objets visuels dans Power BI Desktop"
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
ms.date: 10/12/2017
ms.author: davidi
ms.openlocfilehash: add95532f645c143aea0f58200f9e3b1467320d0
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2017
---
# <a name="using-the-analytics-pane-in-power-bi-desktop"></a>Utilisation du volet Analytique dans Power BI Desktop
Avec le volet **Analyse** de **Power BI Desktop**, vous pouvez ajouter des *lignes de référence* dynamiques aux visuels et mettre en relief les analyses ou les tendances importantes. Le volet **Analyse** se trouve dans la zone **Visualisations** de Power BI Desktop, dès la version publiée en août 2016 (version 2.37.4464.321 ou version ultérieure), comme indiqué ci-dessous.

![](media/desktop-analytics-pane/analytics-pane_1.png)

> [!NOTE]
> Le volet **Analyse** s’affiche uniquement quand vous sélectionnez un élément visuel sur la zone de dessin de Power BI Desktop.
> 
> 

## <a name="enable-forecasting-preview"></a>Activer les prévisions (version préliminaire)
En outre, avec la version **Power BI Desktop** (2.39.4526.362 ou ultérieure) de septembre 2016, vous pouvez également effectuer des *prévisions* à partir du volet **Analyse**. Vous devez activer cette fonctionnalité en version préliminaire. Pour cela, accédez à **Fichier > Options et paramètres -> Options**, puis sélectionnez **Fonctionnalités en version préliminaire** dans le volet gauche. Pour activer cette fonctionnalité, activez la case à cocher en regard du paramètre **Prévisions**, comme illustré dans l’image suivante. Vous devez redémarrer **Power BI Desktop** pour que les modifications entrent en vigueur.

![](media/desktop-analytics-pane/analytics-pane_1b.png)

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

1. Sélectionnez ou créez un élément visuel, puis sélectionnez l’icône **Analyse** dans la section **Visualisations**.
   
   ![](media/desktop-analytics-pane/analytics-pane_2.png)
2. Sélectionnez la flèche vers le bas pour le type de ligne que vous souhaitez créer afin de développer ses options. Dans ce cas, nous allons sélectionner **Ligne moyenne**.
   
   ![](media/desktop-analytics-pane/analytics-pane_3.png)
3. Pour créer une ligne, sélectionnez **+ Ajouter**. Vous pouvez ensuite spécifier un nom pour la ligne en double-cliquant sur la zone de texte, puis en entrant votre nom.
   
   Il existe toutes sortes d’options de ligne. Vous pouvez sélectionner sa *couleur*, sa *transparence*, son *style* et sa *position* (par rapport à des éléments de données de l’élément visuel) et l’ajout de l’étiquette. Et surtout, vous pouvez sélectionner la **mesure** sur laquelle sera fondée votre ligne dans l’élément visuel, dans la liste déroulante **Mesure**, qui est automatiquement remplie avec les éléments de données de l’élément visuel. Dans ce cas, nous allons sélectionner *Weather* (Météo) comme mesure, lui attribuer une étiquette *Average Weather* (Météo moyenne) et personnaliser certaines des autres options, comme indiqué ci-dessous.
   
   ![](media/desktop-analytics-pane/analytics-pane_4.png)
4. Si vous souhaitez afficher une étiquette de données, déplacez le curseur de l’**étiquette de données**. En procédant ainsi, vous obtenez un grand nombre d’options supplémentaires pour l’étiquette de données, comme illustré dans l’image suivante.
   
   ![](media/desktop-analytics-pane/analytics-pane_5.png)
5. Notez le numéro qui s’affiche en regard de l’élément **Ligne moyenne** dans le volet **Analyse**. Ce dernier indique le nombre de lignes dynamiques dont vous disposez actuellement sur votre élément visuel, ainsi que leur type. Si nous ajoutons une **Ligne Max** pour *Cost of Living* (Coût de la vie), vous pouvez voir que le volet **Analyse** affiche désormais également une ligne de référence dynamique **Ligne Max** appliquée à cet élément visuel.
   
   ![](media/desktop-analytics-pane/analytics-pane_6.png)

Si l’élément visuel que vous avez sélectionné ne peut comporter de lignes de référence dynamiques (dans ce cas, un élément visuel **Carte**), vous verrez les éléments suivants en sélectionnant le volet **Analyse**.

![](media/desktop-analytics-pane/analytics-pane_7.png)

Vous pouvez mettre en relief des analyses intéressantes en créant des lignes de référence dynamiques avec le volet **Analyse**.

Nous prévoyons d’ajouter davantage de fonctionnalités, notamment le développement d’éléments visuels auxquels peuvent s’appliquer des lignes de référence dynamiques, n’hésitez pas à revenir consulter les nouveautés.

## <a name="apply-forecasting"></a>Appliquer des prévisions
Vous pouvez utiliser la fonctionnalité **Prévision** en sélectionnant un visuel, puis en développant la section **Prévision** du volet **Analyse**. Vous pouvez spécifier de nombreuses entrées pour modifier la prévision, comme *Longueur de la prévision*, *Intervalle de confiance*, etc. L’illustration suivante montre un visuel de base sur lequel la prévision a été appliquée, mais vous pouvez utiliser votre imagination (et tester la fonctionnalité *Prévisions*) pour voir comment cette fonctionnalité peut s’appliquer à vos modèles.

![](media/desktop-analytics-pane/analytics-pane_8.png)

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
Power BI Desktop vous permet d’effectuer des tâches très diverses. Pour plus d’informations sur ses fonctionnalités, passez en revue les ressources suivantes :

* [Nouveautés dans Power BI Desktop](desktop-latest-update.md)
* [Télécharger Power BI Desktop](desktop-get-the-desktop.md)
* [Prise en main de Power BI Desktop](desktop-getting-started.md)
* [Présentation des requêtes dans Power BI Desktop](desktop-query-overview.md)
* [Types de données dans Power BI Desktop](desktop-data-types.md)
* [Mettre en forme et combiner des données dans Power BI Desktop](desktop-shape-and-combine-data.md)
* [Tâches courantes relatives aux requêtes dans Power BI Desktop](desktop-common-query-tasks.md)    

