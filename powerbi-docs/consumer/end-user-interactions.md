---
title: Comprendre l’interaction des visuels dans un rapport
description: Documentation pour les utilisateurs finaux de Power BI qui explique comment les éléments visuels interagissent sur une page de rapport.
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 10/03/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 28e6cea55b02fabddd0b2f118631a09c0344b66f
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73863088"
---
# <a name="how-visuals-cross-filter-each-other-in-a-power-bi-report"></a>Comment les visuels s’entrefiltrent dans un rapport Power BI
Une des grandes fonctionnalités de Power BI est la façon dont tous les éléments visuels sur une page de rapport sont interconnectés. Si vous sélectionnez un point de données sur l’un des éléments visuels, tous les autres éléments visuels de la page qui contiennent ces données changent en fonction de cette sélection. 

![vidéo sur l’interaction des éléments visuels](media/end-user-interactions/interactions.gif)

## <a name="how-visuals-interact-with-each-other"></a>Interactions entre les visuels

Par défaut, quand vous sélectionnez un point de données dans un visuel d’une page de rapport, cela entraîne un filtrage croisé ou une sélection croisée dans les autres visuels de la page. L’interaction exacte des éléments visuels sur une page est définie par le *concepteur* du rapport. Les *concepteurs* disposent d’options qui permettent d’activer et de désactiver les interactions visuelles, et de modifier le comportement par défaut du filtrage croisé, de la sélection croisée et de l’[exploration](end-user-drill.md). 

Si vous débutez avec les hiérarchies ou l’exploration, vous pouvez consulter des informations complètes à ce sujet dans cet article sur l’[exploration dans Power BI](end-user-drill.md). 

Le filtrage croisé et la sélection croisée peuvent être utiles pour savoir comment une valeur dans vos données impacte une autre valeur. Par exemple, la sélection du segment Moderation (Modération) dans le graphique en anneau permet de montrer l’impact de ce segment sur chaque colonne du graphique « Total units by Month » (Nombre total d’unités par mois) et de filtrer le graphique en courbes.

![image montrant l’interaction des visuels](media/end-user-interactions/power-bi-interactions.png)

Consultez [À propos du filtrage et de la mise en évidence](end-user-report-filter.md). 


  
> [!NOTE]
> Les termes *filtrage croisé* et *sélection croisée* permettent de distinguer le comportement décrit ici de celui qui résulte de l’utilisation du volet **Filtres** pour filtrer et mettre en évidence des visuels.  

## <a name="considerations-and-troubleshooting"></a>Considérations et résolution des problèmes
- Si votre rapport comprend un visuel qui prend en charge l’[exploration](end-user-drill.md), par défaut, le fait d’explorer un visuel n’a aucun effet sur les autres visuels de la page du rapport.     
- Si vous utilisez le visuel A pour interagir avec le visuel B, les filtres appliqués au niveau du visuel A seront appliqués au visuel B.

## <a name="next-steps"></a>Étapes suivantes
[Utilisation des filtres de rapport](../power-bi-how-to-report-filter.md)
