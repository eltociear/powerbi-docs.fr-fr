---
title: Graphiques en anneau dans Power BI
description: Graphiques en anneau dans Power BI
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/11/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 0e870163552e64594e574669ed8dea6937633282
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "75757718"
---
# <a name="create-and-use-doughnut-charts-in-power-bi"></a>Créer et utiliser des graphiques en anneau dans Power BI

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Un graphique en anneau est similaire à un graphique en secteurs, car il représente aussi la relation de parties par rapport à un ensemble. La seule différence est que le centre est vide et qu’il y a de la place pour une étiquette ou une icône.

## <a name="prerequisite"></a>Prérequis

Ce tutoriel utilise le [fichier PBIX de l’exemple Analyse de la vente au détail](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix).

1. Dans la section supérieure gauche de la barre de menus, sélectionnez **Fichier** > **Ouvrir**.
   
2. Rechercher votre copie du **fichier PBIX de l’exemple Analyse de la vente au détail**

1. Ouvrez le **fichier PBIX de l’exemple Analyse de la vente au détail** dans la vue Rapport ![Capture d’écran de l’icône de la vue Rapport.](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Select ![Capture d’écran de l’onglet jaune.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) pour ajouter une nouvelle page.


## <a name="create-a-doughnut-chart"></a>Créer un graphique en anneau

1. Démarrez dans une page de rapport vierge et, dans le volet Champs, sélectionnez **Sales** \> **Last Year Sales** (Ventes > Ventes de l’année dernière).  
   
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


