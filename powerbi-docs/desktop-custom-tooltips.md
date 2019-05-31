---
title: Personnalisation des info-bulles dans Power BI Desktop
description: Créer des info-bulles personnalisées pour les éléments visuels par glisser-déplacer
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/07/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: d5259ba22287a8a2ade3107e4320c39713dcb45e
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "65239748"
---
# <a name="customizing-tooltips-in-power-bi-desktop"></a>Personnalisation des info-bulles dans Power BI Desktop
Les info-bulles offrent un moyen élégant de fournir des informations contextuelles et des détails supplémentaires sur les points de données d’un élément visuel. L’illustration suivante montre une info-bulle appliquée à un graphique dans Power BI Desktop.

![Info-bulle par défaut](media/desktop-custom-tooltips/custom-tooltips-1.png)

Quand une visualisation est créée, l’info-bulle par défaut indique la valeur et la catégorie du point de données. Il existe plusieurs instances lors de la personnalisation de l’info-bulle d’informations est utile et peut fournir un contexte supplémentaire et des informations aux utilisateurs qui visualisent l’élément visuel. Les info-bulles personnalisées vous permettent de spécifier des points de données supplémentaires qui s’affichent avec l’info-bulle.

## <a name="how-to-customize-tooltips"></a>Comment personnaliser les info-bulles
Pour créer une info-bulle personnalisée, dans le **champs** du **visualisations** volet faites glisser un champ dans le **info-bulles** compartiment, illustré dans l’image suivante. Dans l’illustration suivante, deux champs ont été placés dans le compartiment **Info-bulles**.

![Ajout de champs d’info-bulle](media/desktop-custom-tooltips/custom-tooltips-2.png)

Après avoir ajouté les info-bulles au champ, il suffit de pointer sur un point de données dans la visualisation pour que les valeurs des champs s’affichent dans l’info-bulle.

![Info-bulle personnalisée](media/desktop-custom-tooltips/custom-tooltips-3.png)

## <a name="customizing-tooltips-with-aggregation-or-quick-calcs"></a>Personnalisation des info-bulles avec la fonction d’agrégation ou de calculs rapides
Vous pouvez aller un peu plus loin dans la personnalisation d’une info-bulle en sélectionnant une fonction d’agrégation ou un *Calcul rapide*. Pour ce faire, sélectionnez la flèche à côté du champ situé dans le compartiment **Info-bulles**, puis choisissez l’une des options disponibles.

![Info-bulle avec Calcul rapide](media/desktop-custom-tooltips/custom-tooltips-4.png)

Il existe plusieurs façons de personnaliser **info-bulles**, à l’aide de n’importe quel champ disponible dans votre jeu de données, pour transmettre des informations rapides et des informations aux utilisateurs qui visualisent vos tableaux de bord ou des rapports.

