---
title: Personnalisation des info-bulles dans Power BI Desktop
description: Créer des info-bulles personnalisées pour les éléments visuels par glisser-déplacer
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 5fc013df4526c62a9f2e1aa25328119983aaa30e
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/15/2019
ms.locfileid: "54278098"
---
# <a name="customizing-tooltips-in-power-bi-desktop"></a>Personnalisation des info-bulles dans Power BI Desktop
Les info-bulles offrent un moyen élégant de fournir des informations contextuelles et des détails supplémentaires sur les points de données d’un élément visuel. L’illustration suivante montre une info-bulle appliquée à un graphique dans Power BI Desktop.

![Info-bulle par défaut](media/desktop-custom-tooltips/custom-tooltips-1.png)

Quand une visualisation est créée, l’info-bulle par défaut indique la valeur et la catégorie du point de données. Il existe de nombreux cas où le fait de pouvoir personnaliser les informations d’une info-bulle serait utile et fournirait du contexte et des informations supplémentaires aux utilisateurs qui visualisent l’élément visuel. Les info-bulles personnalisées vous permettent de spécifier des points de données supplémentaires qui s’affichent avec l’info-bulle.

## <a name="how-to-customize-tooltips"></a>Comment personnaliser les info-bulles
Pour créer une info-bulle personnalisée, dans la zone **Champs** du volet **Visualisations**, il vous suffit de faire glisser un champ dans le compartiment **Info-bulles**, présenté dans l’illustration suivante. Dans l’illustration suivante, deux champs ont été placés dans le compartiment **Info-bulles**.

![Ajout de champs d’info-bulle](media/desktop-custom-tooltips/custom-tooltips-2.png)

Après avoir ajouté les info-bulles au champ, il suffit de pointer sur un point de données dans la visualisation pour que les valeurs des champs s’affichent dans l’info-bulle.

![Info-bulle personnalisée](media/desktop-custom-tooltips/custom-tooltips-3.png)

## <a name="customizing-tooltips-with-aggregation-or-quick-calcs"></a>Personnalisation des info-bulles avec la fonction d’agrégation ou de calculs rapides
Vous pouvez aller un peu plus loin dans la personnalisation d’une info-bulle en sélectionnant une fonction d’agrégation ou un *Calcul rapide*. Pour ce faire, sélectionnez la flèche à côté du champ situé dans le compartiment **Info-bulles**, puis choisissez l’une des options disponibles.

![Info-bulle avec Calcul rapide](media/desktop-custom-tooltips/custom-tooltips-4.png)

Il existe plusieurs façons de personnaliser les **info-bulles**, via les champs disponibles dans un jeu de données, dans le but de communiquer des informations et des indications rapides aux utilisateurs qui visualisent vos tableaux de bord et rapports.

