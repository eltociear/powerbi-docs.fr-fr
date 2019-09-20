---
title: Comprendre l’interaction des visuels dans un rapport
description: Documentation pour les utilisateurs finaux de Power BI qui explique comment les éléments visuels interagissent sur une page de rapport.
author: mihart
manager: kvivek
ms.custom: seodec18
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 05/29/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 7148a52d7c7475fbe685f83b1e1cc325521460db
ms.sourcegitcommit: 52aa112ac9194f4bb62b0910c4a1be80e1bf1276
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2019
ms.locfileid: "66413180"
---
# <a name="how-visuals-cross-filter-each-other-in-a-power-bi-report"></a>Comment les visuels s’entrefiltrent dans un rapport Power BI
Une des grandes fonctionnalités de Power BI est la façon dont tous les éléments visuels sur une page de rapport sont interconnectés. Si vous sélectionnez un point de données sur l’un des éléments visuels, tous les autres éléments visuels de la page qui contiennent ces données changent en fonction de cette sélection. 

![vidéo sur l’interaction des éléments visuels](media/end-user-interactions/interactions.gif)

Par défaut, vous pouvez sélectionner un point de données dans une visualisation d’une page de rapport afin de filtrer, effectuer une sélection croisée et explorer les autres visualisations de la page. 

Cela peut être utile pour savoir comment une valeur de vos données contribue à une autre valeur. Par exemple, la sélection du segment Modération dans le graphique en anneau permet de montrer la contribution de ce segment à chaque colonne du graphique Nombre total d’unités par mois et de filtrer le graphique en courbes à droite.

![image montrant l’interaction des visuels](media/end-user-interactions/power-bi-interactions.png)

Consultez [À propos du filtrage et de la mise en évidence](../power-bi-reports-filters-and-highlighting.md). 

L’interaction exacte des éléments visuels sur une page est définie par le *concepteur* du rapport. Les concepteurs disposent d’options qui permettent d’activer et de désactiver les interactions visuelles et de modifier le comportement par défaut du filtrage croisé, de la sélection croisée et de l’exploration. 
  
> [!NOTE]
> Les termes *filtrage croisé* et *sélection croisée* permettent de distinguer le comportement décrit ici de celui qui résulte de l’utilisation du volet **Filtres** pour filtrer et mettre en évidence des visualisations.  

## <a name="considerations-and-troubleshooting"></a>Considérations et résolution des problèmes
- Si votre rapport comprend une visualisation qui prend en charge l’[exploration](../power-bi-visualization-drill-down.md), par défaut, le fait d’explorer une visualisation n’aura aucun impact sur les autres visualisations de la page du rapport.     
- Si vous utilisez le visuel A pour interagir avec le visuel B, les filtres appliqués au niveau du visuel A seront appliqués au visuel B.

## <a name="next-steps"></a>Étapes suivantes
[Utilisation des filtres de rapport](../power-bi-how-to-report-filter.md)
