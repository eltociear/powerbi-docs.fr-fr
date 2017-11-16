---
title: "Personnalisation des info-bulles dans Power BI Desktop"
description: "Créer des info-bulles personnalisées pour les éléments visuels par glisser-déplacer"
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 09/06/2017
ms.author: davidi
ms.openlocfilehash: a54cc745cb341188efb511d66a71b185a7967212
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2017
---
# <a name="customizing-tooltips-in-power-bi-desktop"></a>Personnalisation des info-bulles dans Power BI Desktop
Les info-bulles offrent un moyen élégant de fournir des informations contextuelles et des détails supplémentaires sur les points de données d’un élément visuel. L’illustration suivante montre une info-bulle appliquée à un graphique dans Power BI Desktop.

![](media/desktop-custom-tooltips/custom-tooltips_1.png)

Quand une visualisation est créée, l’info-bulle par défaut indique la valeur et la catégorie du point de données. Il existe de nombreux cas où le fait de pouvoir personnaliser les informations d’une info-bulle serait utile et fournirait du contexte et des informations supplémentaires aux utilisateurs qui visualisent l’élément visuel. Les info-bulles personnalisées vous permettent de spécifier des points de données supplémentaires qui s’affichent avec l’info-bulle.

## <a name="how-to-customize-tooltips"></a>Comment personnaliser les info-bulles
Pour créer une info-bulle personnalisée, dans la zone **Champs** du volet **Visualisations**, il vous suffit de faire glisser un champ dans le compartiment **Info-bulles**, présenté dans l’illustration suivante. Dans l’illustration suivante, quatre champs ont été placés dans le compartiment **Info-bulles**.

![](media/desktop-custom-tooltips/custom-tooltips_2.png)

Après avoir ajouté les info-bulles à la zone Champs, il suffit de pointer sur un point de données dans la visualisation pour que les valeurs des champs s’affichent dans l’info-bulle.

![](media/desktop-custom-tooltips/custom-tooltips_3.png)

## <a name="customizing-tooltips-with-aggregation-or-quick-calcs"></a>Personnalisation des info-bulles avec la fonction d’agrégation ou de calculs rapides
Vous pouvez aller un peu plus loin dans la personnalisation d’une info-bulle en sélectionnant une fonction d’agrégation ou un *Calcul rapide*. Pour ce faire, sélectionnez la flèche à côté du champ situé dans le compartiment **Info-bulles**, puis choisissez l’une des options disponibles.

![](media/desktop-custom-tooltips/custom-tooltips_4.png)

Il existe plusieurs façons de personnaliser les **info-bulles**, via les champs disponibles dans un jeu de données, dans le but de communiquer des informations et des indications rapides aux utilisateurs qui visualisent vos tableaux de bord et rapports.

