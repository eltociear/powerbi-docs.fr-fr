---
title: Types d’informations pris en charge par Power BI
description: Informations rapides et Afficher les informations avec Power BI
services: powerbi
documentationcenter: ''
author: mihart
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 03/02/2018
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: c295eea46e6e8d182147f877548a385ce4602bad
ms.sourcegitcommit: 5e1f7d2673efe25c47b9b9f315011055bfe92c8f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/09/2018
---
# <a name="types-of-insights-supported-by-power-bi"></a>Types d’informations pris en charge par Power BI
## <a name="how-does-insights-work"></a>Comment fonctionnent les informations ?
Power BI effectue des recherches rapides dans différents sous-ensembles de votre jeu de données tout en appliquant un jeu d’algorithmes sophistiqués pour détecter les informations potentiellement intéressantes. Power BI analyse autant que possible le jeu de données dans le délai imparti.

Vous pouvez exécuter des informations sur un jeu de données ou une vignette de tableau de bord.   

## <a name="what-types-of-insights-can-we-find"></a>Quels types d’informations pouvons-nous trouver ?
Voici certains des algorithmes que nous utilisons :

## <a name="category-outliers-topbottom"></a>Valeurs hors norme de catégorie (de haut en bas)
Met en évidence les cas où, pour une mesure dans le modèle, un ou deux membres d’une dimension ont des valeurs beaucoup plus grandes que d’autres membres de la dimension.  

![Exemple de valeurs hors norme de catégorie](media/service-insight-types/pbi_auto_insight_types_category_outliers.png)

## <a name="change-points-in-a-time-series"></a>Points de changement dans une série chronologique
Met en surbrillance les cas où il existe des modifications significatives dans les tendances d’une série chronologique de données.

![Exemple de points de changement dans une série chronologique](media/service-insight-types/pbi_auto_insight_types_changepoint.png)

## <a name="correlation"></a>Corrélation
Détecte les cas où plusieurs mesures montrent une corrélation les unes avec les autres lorsqu’elles sont représentées par rapport à une dimension du jeu de données.

![Exemple de corrélation](media/service-insight-types/pbi_auto_insight_types_correlation.png)

## <a name="low-variance"></a>Écart faible
Détecte les cas où des points de données ne sont pas éloigné de la moyenne.

![Exemple d’écart faible](media/service-insight-types/power-bi-low-variance.png)

## <a name="majority-major-factors"></a>Majorité (facteurs majeurs)
Recherche les cas où une majorité d’une valeur totale peut être attribuée à un facteur unique en cas de répartition par une autre dimension.  

![Exemple de facteurs majeurs](media/service-insight-types/pbi_auto_insight_types_majority.png)

## <a name="overall-trends-in-time-series"></a>Tendances générales dans une série chronologique
Détecte les tendances vers le haut ou vers le bas dans les données d’une série chronologique.

![Exemple de tendances générales dans une série chronologique](media/service-insight-types/pbi_auto_insight_types_trend.png)

## <a name="seasonality-in-time-series"></a>Caractère saisonnier d’une série chronologique
Recherche des modèles récurrents dans les données d’une série chronologiques, comme un caractère saisonnier (hebdomadaire, mensuel ou annuel).

![Exemple de caractère saisonnier](media/service-insight-types/pbi_auto_insight_types_seasonality_new.png)

## <a name="steady-share"></a>Partage stable
Met en évidence les cas où il existe une corrélation parent-enfant entre le partage d’une valeur enfant par rapport à la valeur globale du parent dans une variable continue.

![Exemple de partage stable](media/service-insight-types/pbi_auto_insight_types_steadyshare.png)

## <a name="time-series-outliers"></a>Valeurs hors norme d’une série chronologique
Pour les données d’une série chronologique, détecte les cas où il existe des dates ou heures avec des valeurs fondamentalement différentes des autres valeurs de date et d’heure.

![Exemple de valeurs hors norme d’une série chronologique](media/service-insight-types/pbi_auto_insight_types_time_series_outliers.png)

## <a name="next-steps"></a>Étapes suivantes
[Informations Power BI](service-insights.md)

Si vous possédez un jeu de données, [optimisez-le pour la fonction Informations](service-insights-optimize.md).

D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)

