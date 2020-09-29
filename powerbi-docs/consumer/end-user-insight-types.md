---
title: Types d’informations pris en charge par Power BI
description: Informations rapides et Afficher les informations avec Power BI
author: mihart
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 09/09/2020
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: 8e8411ea29436a5ee19802d2a970b760062fe59e
ms.sourcegitcommit: cb606d3ae95300683caf1853e229d8981302a8e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2020
ms.locfileid: "90763985"
---
# <a name="types-of-insights-supported-by-power-bi"></a>Types d’informations pris en charge par Power BI

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-yyny.md)]

Vous pouvez demander à Power BI d’examiner vos données et de rechercher des tendances et des modèles intéressants. Ces tendances et ces modèles sont présentés sous forme de visuels, qui sont appelés *insights*. 

Pour découvrir comment utiliser les insights, consultez [Insights Power BI](end-user-insights.md)

![Un ensemble d’insights](media/end-user-insight-types/power-bi-insight.png)

## <a name="how-does-insights-work"></a>Comment fonctionnent les informations ?
Power BI recherche rapidement différents sous-ensembles de votre jeu de données. Au fil de la recherche, Power BI applique un ensemble d’algorithmes sophistiqués pour découvrir des insights potentiellement intéressants. Les *utilisateurs professionnels* de Power BI peuvent exécuter des insights sur les vignettes des tableaux de bord.

## <a name="some-terminology"></a>Un peu de terminologie
Power BI utilise des algorithmes statistiques pour découvrir des insights. Les algorithmes sont listés et décrits dans la section suivante de cet article. Avant d’accéder aux algorithmes, voici les définitions de certains termes qui ne vous sont pas nécessairement familiers. 

* **Mesure** - Une mesure est un champ (numérique) quantitatif qui peut être utilisé pour effectuer des calculs. La somme, la moyenne et le minimum sont des calculs courants. Par exemple, si notre société fabrique et vend des skateboards, nos mesures peuvent être le nombre de skateboards vendus et le bénéfice moyen par an.  
* **Dimension** - Les dimensions sont des données (texte) de catégories. Une dimension décrit une personne, un objet, un élément, des produits, un lieu et une heure. Dans un jeu de données, les dimensions sont un moyen de regrouper des *mesures* en catégories utiles. Pour notre entreprise de skateboards, certaines dimensions peuvent consister à regarder les ventes (une mesure) par modèle, par couleur, par pays ou par campagne marketing.   
* **Corrélation** - Une corrélation nous indique comment le comportement des éléments est lié.  Si leurs modèles d’augmentation et de diminution sont similaires, ils sont corrélés positivement. Si leurs modèles sont opposés, ils sont corrélés négativement. Par exemple, si les ventes de nos skateboards rouges augmentent chaque fois que nous faisons une campagne marketing à la télévision, les ventes des skateboards rouges et la campagne à la télévision sont corrélées positivement.
* **Séries chronologiques** - Une série chronologique est un moyen de montrer le temps sous forme de points de données successifs. Ces points de données peuvent être des incréments, comme des secondes, des heures, des mois ou des années.  
* **Variable continue** - Une variable continue peut être n’importe quelle valeur comprise entre ses limites minimale et maximale ; dans le cas contraire, il s’agit d’une variable discrète. La température, le poids, l’âge et l’heure sont des exemples. Les variables continues peuvent inclure des fractions ou des parties de la valeur. Le nombre total de skateboards bleus vendus est une variable discrète dans la mesure où nous ne pouvons pas vendre un demi-skateboard.  

## <a name="what-types-of-insights-can-you-find"></a>Quels types d’insights pouvez-vous trouver ?
Voici les algorithmes que Power BI utilise. 

### <a name="category-outliers-topbottom"></a>Valeurs hors norme de catégorie (de haut en bas)
Met en évidence les cas où une ou deux catégories ont des valeurs nettement supérieures à celles des autres catégories.  

![Exemple de valeurs hors norme de catégorie](./media/end-user-insight-types/pbi-auto-insight-type-category-outliers.png)

### <a name="change-points-in-a-time-series"></a>Points de changement dans une série chronologique
Met en surbrillance les cas où il existe des modifications significatives dans les tendances d’une série chronologique de données.

![Exemple de points de changement dans une série chronologique](./media/end-user-insight-types/pbi-auto-insight-type-changepoint.png)

### <a name="correlation"></a>Corrélation
Détecte les cas où plusieurs mesures montrent un modèle ou une tendance similaire quand elles sont tracées sur une catégorie ou une valeur du jeu de données.

![Exemple de corrélation](./media/end-user-insight-types/pbi-auto-insight-type-correlation.png)

### <a name="low-variance"></a>Écart faible
Détecte les cas où les points de données d’une dimension ne sont pas éloignés de la moyenne, donc la « variance » est faible. Supposons que vous avez la mesure « ventes » et une dimension « région ». Et dans la région, vous constatez qu’il y a très peu de différences entre les points de données et la moyenne (des points de données). L’aperçu se déclenche lorsque la variance des ventes dans toutes les régions est inférieure à un seuil. En d’autres termes, lorsque les ventes sont assez similaires dans toutes les régions.

![Exemple d’écart faible](./media/end-user-insight-types/power-bi-insights-low-variance.png)

### <a name="majority-major-factors"></a>Majorité (facteurs majeurs)
Recherche les cas où une majorité d’une valeur totale peut être attribuée à un facteur unique en cas de répartition par une autre dimension.  

![Exemple de facteurs majeurs](./media/end-user-insight-types/pbi-auto-insight-type-majority.png)

### <a name="overall-trends-in-time-series"></a>Tendances générales dans une série chronologique
Détecte les tendances vers le haut ou vers le bas dans les données d’une série chronologique.

![Exemple de tendances générales dans une série chronologique](./media/end-user-insight-types/pbi-auto-insight-type-trend.png)

### <a name="seasonality-in-time-series"></a>Caractère saisonnier d’une série chronologique
Recherche des modèles récurrents dans les données d’une série chronologiques, comme un caractère saisonnier (hebdomadaire, mensuel ou annuel).

![Exemple de caractère saisonnier](./media/end-user-insight-types/pbi-auto-insight-type-seasonality-new.png)

### <a name="steady-share"></a>Partage stable
Met en évidence les cas où il existe une corrélation parent-enfant entre le partage d’une valeur enfant par rapport à la valeur globale du parent dans une variable continue. L’aperçu de partage stable s’applique au contexte d’une mesure, d’une dimension et d’une autre dimension date/heure. Cet insight se déclenche lorsqu’une certaine valeur de dimension, par exemple, « la région est », affiche un pourcentage constant de ventes globales sur cette dimension date/heure.

L’aperçu de partage stable est similaire à l’aperçu de faible écart, car ils sont tous deux liés au manque de variance d’une valeur dans le temps. Toutefois, l’aperçu de partage stable mesure le manque de variance du **pourcentage global** dans le temps, tandis que l’aperçu de faible variance mesure le manque de variance des valeurs de mesure absolues sur une dimension.

![Exemple de partage stable](./media/end-user-insight-types/pbi-auto-insight-type-steadyshare.png)

### <a name="time-series-outliers"></a>Valeurs hors norme d’une série chronologique
Pour les données d’une série chronologique, détecte les cas où il existe des dates ou heures avec des valeurs fondamentalement différentes des autres valeurs de date et d’heure.

![Exemple de valeurs hors norme d’une série chronologique](./media/end-user-insight-types/pbi-auto-insight-type-time-series-outliers-purple.png)

## <a name="next-steps"></a>Étapes suivantes
[Informations Power BI](end-user-insights.md)

D’autres questions ? [Posez vos questions à la communauté Power BI](https://community.powerbi.com/)

