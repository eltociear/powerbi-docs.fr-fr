---
title: Types d’informations pris en charge par Power BI
description: Informations rapides et Afficher les informations avec Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 10/02/2019
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: 7f754c1164448be88a3269cb8e3d129b63a6115f
ms.sourcegitcommit: 5410a17c6325406c9d9364585d7c26de4d9488ae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72379907"
---
# <a name="types-of-insights-supported-by-power-bi"></a>Types d’informations pris en charge par Power BI

La service Power BI peut automatiquement rechercher des insights dans vos tableaux de bord ou rapports.

## <a name="how-does-insights-work"></a>Comment fonctionnent les informations ?
Power BI recherche rapidement différents sous-ensembles de votre jeu de données. Au fil de la recherche, Power BI applique un ensemble d’algorithmes sophistiqués pour découvrir des insights potentiellement intéressants. Power BI analyse autant que possible le jeu de données dans le délai imparti.

Vous pouvez exécuter des informations sur un jeu de données ou une vignette de tableau de bord.   

## <a name="what-types-of-insights-can-we-find"></a>Quels types d’informations pouvons-nous trouver ?
Voici certains des algorithmes que nous utilisons :

## <a name="category-outliers-topbottom"></a>Valeurs hors norme de catégorie (de haut en bas)
Met en évidence les cas où, pour une mesure dans le modèle, un ou deux membres d’une dimension ont des valeurs beaucoup plus grandes que d’autres membres de la dimension.  

![Exemple de valeurs hors norme de catégorie](./media/end-user-insight-types/pbi_auto_insight_types_category_outliers.png)

## <a name="change-points-in-a-time-series"></a>Points de changement dans une série chronologique
Met en surbrillance les cas où il existe des modifications significatives dans les tendances d’une série chronologique de données.

![Exemple de points de changement dans une série chronologique](./media/end-user-insight-types/pbi_auto_insight_types_changepoint.png)

## <a name="correlation"></a>Corrélation
Détecte les cas où plusieurs mesures montrent une corrélation les unes avec les autres lorsqu’elles sont représentées par rapport à une dimension du jeu de données.

![Exemple de corrélation](./media/end-user-insight-types/pbi_auto_insight_types_correlation.png)

## <a name="low-variance"></a>Écart faible
Détecte les cas où des points de données ne sont pas éloignés de la moyenne.

![Exemple d’écart faible](./media/end-user-insight-types/power-bi-low-variance.png)

## <a name="majority-major-factors"></a>Majorité (facteurs majeurs)
Recherche les cas où une majorité d’une valeur totale peut être attribuée à un facteur unique en cas de répartition par une autre dimension.  

![Exemple de facteurs majeurs](./media/end-user-insight-types/pbi_auto_insight_types_majority.png)

## <a name="overall-trends-in-time-series"></a>Tendances générales dans une série chronologique
Détecte les tendances vers le haut ou vers le bas dans les données d’une série chronologique.

![Exemple de tendances générales dans une série chronologique](./media/end-user-insight-types/pbi_auto_insight_types_trend.png)

## <a name="seasonality-in-time-series"></a>Caractère saisonnier d’une série chronologique
Recherche des modèles récurrents dans les données d’une série chronologiques, comme un caractère saisonnier (hebdomadaire, mensuel ou annuel).

![Exemple de caractère saisonnier](./media/end-user-insight-types/pbi_auto_insight_types_seasonality_new.png)

## <a name="steady-share"></a>Partage stable
Met en évidence les cas où il existe une corrélation parent-enfant entre le partage d’une valeur enfant par rapport à la valeur globale du parent dans une variable continue.

![Exemple de partage stable](./media/end-user-insight-types/pbi_auto_insight_types_steadyshare.png)

## <a name="time-series-outliers"></a>Valeurs hors norme d’une série chronologique
Pour les données d’une série chronologique, détecte les cas où il existe des dates ou heures avec des valeurs fondamentalement différentes des autres valeurs de date et d’heure.

![Exemple de valeurs hors norme d’une série chronologique](./media/end-user-insight-types/pbi_auto_insight_types_time_series_outliers.png)

## <a name="next-steps"></a>Étapes suivantes
[Informations Power BI](end-user-insights.md)

D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)

