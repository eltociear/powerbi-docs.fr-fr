---
title: "Visuels des indicateurs de performance clés (didacticiel)"
description: "créer un indicateur de performance clé dans power bi"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: xmja6EpqaO0
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 08/09/2017
ms.author: mihart
ms.openlocfilehash: 23b322c9fbc4c203a5b20aa45bb41c2cb6cb7f0f
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2017
---
# <a name="kpi-visuals-tutorial"></a>Visuels des indicateurs de performance clés (didacticiel)
Un indicateur de performance clé (KPI) est un indice visuel qui représente la marge de progression réalisée en vue d’atteindre un objectif mesurable. Pour plus d’informations sur les indicateurs de performances clés, consultez [Microsoft Developer Network](https://msdn.microsoft.com/library/hh272050).

## <a name="when-to-use-a-kpi"></a>Quand utiliser un indicateur de performance clé ?
Les indicateurs de performances clés sont recommandés :

* pour mesurer la progression (dans quel domaine suis-je en avance ou en retard ?)
* pour mesurer ce qu’il vous reste à faire pour atteindre un objectif (suis-je en avance ou en retard ?)   

## <a name="kpi-visual-requirements"></a>Configuration requise pour les visuels d’indicateurs de performances clés
Un indicateur de performance clé (KPI) se base sur une mesure spécifique et est conçu pour vous aider à évaluer le statut et la valeur actuelle d’une mesure par rapport à un objectif défini. Ainsi, les visuels d’indicateurs de performances clés nécessitent une mesure de *base* qui évalue une mesure ou un valeur, en fonction d’une valeur définie ou d’une *cible* et d’un seuil ou d’un objectif.

> [!NOTE]
> Actuellement, un jeu de données d’indicateurs de performances clés doit contenir des valeurs cibles pour un indicateur de performance clé. Si votre jeu de données n’en contient pas, vous pouvez créer des objectifs en ajoutant une feuille Excel contenant des objectifs à votre modèle de données ou fichier PBIX.
> 
> 

## <a name="how-to-create-a-kpi"></a>Création d’un indicateur de performance clé
Pour effectuer la procédure, connectez-vous à Power BI et sélectionnez **Obtenir des données > Exemples > Exemple Analyse de la vente au détail**. Nous allons créer un indicateur de performance clé qui mesure la progression réalisée en vue d’atteindre un objectif de vente.

Vous pouvez également écouter Will qui vous montre comment créer des éléments visuels de métrique uniques : jauges, cartes et indicateurs de performance clés.

<iframe width="560" height="315" src="https://www.youtube.com/embed/xmja6EpqaO0?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

1. Sélectionnez **Ventes > Nombre total d’unités cette année**.  Il s’agit de l’indicateur.
2. Ajoutez **Temps > Mois**.  Ceci représente la tendance.
3. IMPORTANT : Triez le graphique par **mois**. Une fois que vous convertissez la visualisation en indicateur de performance clé, il n’existe aucune option de tri.
4. Convertissez l’élément visuel en indicateur de performance clé en sélectionnant l’icône correspondante dans le volet de visualisation.
   
    ![](media/power-bi-visualization-kpi/power-bi-kpi-icon.png)
5. Ajoutez un objectif. Ajoutez les ventes de l’année précédente comme objectif. Faites glisser **Nombre total d’unités l’année dernière** dans le champ **Objectifs cibles**.
   
    ![](media/power-bi-visualization-kpi/power-bi-kpi.png)
6. Vous pouvez aussi formater l’indicateur de performance clé en sélectionnant l’icône représentant un rouleau qui ouvre le volet de Mise en forme.
   
   * **Indicateur** : contrôle les unités d’affichage de l’indicateur et les décimales.
   * **Axe de tendance** : quand il est **activé**, l’axe de tendance est affiché en arrière-plan de l’élément visuel de l’indicateur de performance clé.  
   * **Objectifs** : quand il est **activé**, l’élément visuel affiche l’objectif et la distance restante pour atteindre l’objectif, sous forme de pourcentage.
   * **Statut** : certains indicateurs de performances clés sont considérés comme *meilleurs* pour des valeurs plus élevées et d’autres sont considérés comme *meilleurs* pour des valeurs plus faibles. Par exemple, les bénéfices par rapport au temps d’attente. De manière générale, une valeur plus élevée pour les bénéfices est mieux considérée qu’une valeur de temps d’attente élevée (généralement considérée comme moins bonne). Cette fonction permet de sélectionner le comportement d’un indicateur de performance clé. Par défaut, le statut est le suivant : **plus c’est élevé, mieux c’**.
7. Une fois l’indicateur de performance clé paramétré comme vous le souhaitez, [épinglez-le à un tableau de bord](service-dashboard-pin-tile-from-report.md).

Les Indicateurs de performances clés sont également disponibles sur vos appareils mobiles, ce qui vous permet de toujours rester connecté

## <a name="considerations-and-troubleshooting"></a>Considérations et résolution des problèmes
* Si votre indicateur de performance clé ne ressemble pas à celui ci-dessus, vous devez peut-être effectuer un tri par mois. Étant donné que les indicateurs de performance clés n’ont pas d’option de tri, vous devez trier par mois *avant* de convertir votre visualisation en indicateur de performance clé.

## <a name="next-steps"></a>Étapes suivantes
[Rapports dans Power BI](service-reports.md)

[Visualisations dans des rapports Power BI](power-bi-report-visualizations.md)

[Power BI – Concepts de base](service-basic-concepts.md)

D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)

