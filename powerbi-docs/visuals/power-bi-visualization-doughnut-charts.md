---
title: Graphiques en anneau dans Power BI
description: Graphiques en anneau dans Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 09/24/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: ab292964bb1b6b1f4218d41c46eb2c28c82a034c
ms.sourcegitcommit: ce8332a71d4d205a1f005b703da4a390d79c98b6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2018
ms.locfileid: "47416748"
---
# <a name="doughnut-charts-in-power-bi"></a>Graphiques en anneau dans Power BI
Un graphique en anneau est similaire à un graphique en secteurs, car il représente aussi la relation de parties par rapport à un ensemble. La seule différence est que le centre est vide et qu’il y a de la place pour une étiquette ou une icône.

## <a name="create-a-doughnut-chart"></a>Créer un graphique en anneau
Ces instructions utilisent l’Exemple Analyse de la vente au détail pour créer un graphique en anneau qui affiche les ventes de cette année par catégorie. [Téléchargez l’exemple](../sample-datasets.md) pour le service Power BI ou Power BI Desktop.

1. Démarrez sur une [page de rapport vide](../power-bi-report-add-page.md). Si vous utilisez le service Power BI, veillez à ouvrir le rapport en [mode Édition](../service-interact-with-a-report-in-editing-view.md).

2. Dans le volet Champs, sélectionnez **Sales** \> **Last Year Sales** (Ventes > Ventes de l’année dernière).  
   
3. Dans le volet Visualisations, sélectionnez l’icône de graphique en anneau ![icône de graphique en anneau](media/power-bi-visualization-doughnut-charts/power-bi-icon.png) pour convertir votre histogramme en graphique en anneau. Si **Last Year Sales** (Ventes de l’année dernière) ne figure pas dans la zone **Valeurs**, faites-le glisser vers cette zone.
     
   ![Volet de visualisation avec anneau sélectionné](media/power-bi-visualization-doughnut-charts/power-bi-doughnut-chart.png)

4. Sélectionnez **Élément** \> **Catégorie** pour l’ajouter à la zone **Légende**. 
     
    ![anneau en regard du volet Champs](media/power-bi-visualization-doughnut-charts/power-bi-doughnut-done.png)

5. Si vous le souhaitez, [ajustez la taille et la couleur du texte du graphique](power-bi-visualization-customize-title-background-and-legend.md). 

## <a name="considerations-and-troubleshooting"></a>Considérations et résolution des problèmes
* La somme des valeurs du graphique en anneau doit atteindre 100 %.
* L’utilisation d’un trop grand nombre de catégories peut rendre le graphique difficile à lire et à analyser.
* Les graphiques en anneau sont davantage adaptés pour comparer une section spécifique par rapport à l’ensemble que pour comparer des sections individuelles entre elles. 

## <a name="next-steps"></a>Étapes suivantes
[Graphiques en entonnoir dans Power BI](power-bi-visualization-funnel-charts.md)

[Types de visualisation dans Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)


