---
title: Personnalisation des info-bulles dans Power BI Desktop
description: Créer des info-bulles personnalisées pour les éléments visuels par glisser-déplacer
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/07/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: efbae4250b7b3cab18892cf519bfac5da3a88e1b
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/06/2020
ms.locfileid: "73868668"
---
# <a name="customizing-tooltips-in-power-bi-desktop"></a>Personnalisation des info-bulles dans Power BI Desktop
Les info-bulles offrent un moyen élégant de fournir des informations contextuelles et des détails supplémentaires sur les points de données d’un élément visuel. L’illustration suivante montre une info-bulle appliquée à un graphique dans Power BI Desktop.

![Info-bulle par défaut](media/desktop-custom-tooltips/custom-tooltips-1.png)

Quand une visualisation est créée, l’info-bulle par défaut indique la valeur et la catégorie du point de données. Il existe de nombreux cas où le fait de personnaliser les informations d’une info-bulle est utile et fournit du contexte et des informations supplémentaires aux utilisateurs qui visualisent l’élément visuel. Les info-bulles personnalisées vous permettent de spécifier des points de données supplémentaires qui s’affichent avec l’info-bulle.

## <a name="how-to-customize-tooltips"></a>Comment personnaliser les info-bulles
Pour créer une info-bulle personnalisée, dans la zone **Champs** du volet **Visualisations**, faites glisser un champ dans le compartiment **Info-bulles**, présenté dans l’illustration suivante. Dans l’illustration suivante, deux champs ont été placés dans le compartiment **Info-bulles**.

![Ajout de champs d’info-bulle](media/desktop-custom-tooltips/custom-tooltips-2.png)

Après avoir ajouté les info-bulles au champ, il suffit de pointer sur un point de données dans la visualisation pour que les valeurs des champs s’affichent dans l’info-bulle.

![Info-bulle personnalisée](media/desktop-custom-tooltips/custom-tooltips-3.png)

## <a name="customizing-tooltips-with-aggregation-or-quick-calcs"></a>Personnalisation des info-bulles avec la fonction d’agrégation ou de calculs rapides
Vous pouvez aller un peu plus loin dans la personnalisation d’une info-bulle en sélectionnant une fonction d’agrégation ou un *Calcul rapide*. Pour ce faire, sélectionnez la flèche à côté du champ situé dans le compartiment **Info-bulles**, puis choisissez l’une des options disponibles.

![Info-bulle avec Calcul rapide](media/desktop-custom-tooltips/custom-tooltips-4.png)

Il existe plusieurs façons de personnaliser les **info-bulles**, via les champs disponibles dans un jeu de données, dans le but de communiquer des informations et des indications rapides aux utilisateurs qui visualisent vos tableaux de bord et rapports.

