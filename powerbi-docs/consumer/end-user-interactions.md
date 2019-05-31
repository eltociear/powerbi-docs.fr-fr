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
ms.sourcegitcommit: d88cc6a87d4ba82ad2c4d496a3634f927e4ac529
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66413180"
---
# <a name="how-visuals-cross-filter-each-other-in-a-power-bi-report"></a>Comment les visuels s’entrefiltrent dans un rapport Power BI
Une des grandes fonctionnalités de Power BI est la façon dont tous les éléments visuels sur une page de rapport sont interconnectés. Si vous sélectionnez un point de données sur l’un des éléments visuels, tous les autres éléments visuels de la page qui contiennent ces données changent en fonction de cette sélection. 

![vidéo sur l’interaction des éléments visuels](media/end-user-interactions/interactions.gif)

Par défaut, en sélectionnant un point de données dans une visualisation sur une page de rapport effectue un filtrage croisé, croisée et explorez les autres visualisations sur la page. 

Cela peut être utile pour identifier la façon dont une valeur dans vos données contribue à un autre. Par exemple, en sélectionnant le segment Moderation dans le graphique en anneau, de met en évidence la contribution à partir de ce segment à chaque colonne dans le nombre Total d’unités par graphique de mois, et elle a filtré le graphique en courbes à droite.

![image d’éléments visuels de l’interaction](media/end-user-interactions/power-bi-interactions.png)

Consultez [À propos du filtrage et de la mise en évidence](../power-bi-reports-filters-and-highlighting.md). 

L’interaction exacte des éléments visuels sur une page est définie par le *concepteur* du rapport. Les concepteurs disposent d’options qui permettent d’activer et de désactiver les interactions visuelles et de modifier le comportement par défaut du filtrage croisé, de la sélection croisée et de l’exploration. 
  
> [!NOTE]
> Les termes *filtrage croisé* et *sélection croisée* permettent de distinguer le comportement décrit ici de celui qui résulte de l’utilisation du volet **Filtres** pour filtrer et mettre en évidence des visualisations.  

## <a name="considerations-and-troubleshooting"></a>Considérations et résolution des problèmes
- Si le rapport contient une visualisation qui prend en charge [FORAGE](../power-bi-visualization-drill-down.md), par défaut, exploration d’une visualisation n’a aucun impact sur les autres visualisations sur la page de rapport.     
- Si vous utilisez visualA pour interagir avec visualB, les filtres au niveau du visuel à partir de visualA s’appliqueront à visualB.

## <a name="next-steps"></a>Étapes suivantes
[Utilisation des filtres de rapport](../power-bi-how-to-report-filter.md)
