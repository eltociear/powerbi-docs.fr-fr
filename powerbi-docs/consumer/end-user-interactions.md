---
title: Comprendre comment les éléments visuels interagissent dans un rapport (pour les consommateurs de rapports)
description: Documentation pour les utilisateurs finaux de Power BI qui explique comment les éléments visuels interagissent sur une page de rapport.
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 08/28/2018
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: c87f99b768f52fe7f6b565c47ed7e434b167a046
ms.sourcegitcommit: dc8b8a2cf2dcc96ccb46159802ebd9342a7fa840
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/11/2018
ms.locfileid: "49112058"
---
# <a name="visualization-interactions-in-a-power-bi-report"></a>Interactions avec les visualisations dans un rapport Power BI
Une des grandes fonctionnalités de Power BI est la façon dont tous les éléments visuels sur une page de rapport sont interconnectés. Si vous sélectionnez un point de données sur l’un des éléments visuels, tous les autres éléments visuels de la page qui contiennent ces données changent en fonction de cette sélection. 

![vidéo sur l’interaction des éléments visuels](media/end-user-interactions/interactions.gif)

Par défaut, vous pouvez utiliser les visualisations d’une page de rapport pour filtrer et mettre en évidence les autres visualisations de la page et les explorer. On parle alors de « filtrage croisé » et de « mise en évidence croisée ». Par exemple, si vous sélectionnez un état sur une visualisation de carte, l’histogramme peut être mis en évidence et le graphique en courbes filtré pour afficher uniquement les données qui s’appliquent à cet état.

Consultez [À propos du filtrage et de la mise en évidence](../power-bi-reports-filters-and-highlighting.md). Et si vous avez une visualisation qui prend en charge l’[exploration](../power-bi-visualization-drill-down.md), par défaut, l’exploration d’une visualisation n’a aucun impact sur les autres visualisations de la page de rapport. 

L’interaction exacte des éléments visuels sur une page est définie par le *concepteur* du rapport. Les concepteurs disposent d’options qui permettent d’activer et de désactiver les interactions visuelles et de modifier le comportement par défaut du filtrage croisé, de la sélection croisée et de l’exploration.
  
> [!NOTE]
> Les termes *filtrage croisé* et *sélection croisée* permettent de distinguer le comportement décrit ici de celui qui résulte de l’utilisation du volet **Filtres** pour filtrer et mettre en évidence des visualisations.  

### <a name="next-steps"></a>Étapes suivantes
[Utilisation des filtres de rapport](../power-bi-how-to-report-filter.md)
