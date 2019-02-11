---
title: Superviser les capacités Power BI Premium avec le portail d’administration
description: Utilisez le portail d’administration Power BI pour superviser vos capacités Premium.
author: minewiskan
ms.author: owend
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 02/05/2019
LocalizationGroup: Premium
ms.openlocfilehash: 59097c07719e4bb8db188e8a86db377076aea7a9
ms.sourcegitcommit: 54d44deb6e03e518ad6378656c769b06f2a0b6dc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55794125"
---
# <a name="monitor-capacities-in-the-admin-portal"></a>Superviser les capacités dans le portail d’administration

Cet article décrit comment vous pouvez utiliser la zone de Paramètres de capacité dans le portail d’administration pour obtenir un aperçu rapide des performances de votre capacité.  Pour obtenir les métriques les plus détaillées sur votre capacité, il est préférable d’utiliser l’application [Métriques de capacité Power BI Premium](service-admin-premium-monitor-capacity.md).

## <a name="capacity-metrics"></a>Métriques de capacité

La zone **Paramètres de capacité** du portail d’administration fournit quatre jauges qui indiquent les charges placées et les ressources utilisées par votre capacité au cours des sept derniers jours. Ces quatre vignettes fonctionnent sur une fenêtre de temps horaire qui indique le nombre d’heures où la métrique correspondante a été supérieure à 80 % au cours des sept derniers jours. Cette métrique indique une dégradation potentielle de l’expérience de l’utilisateur final.

![Utilisation en 7 jours](media/service-admin-premium-monitor-capacity/usage-in-days.png)

| **Métrique** | **Description** |
| --- | --- |
| Processeur |Nombre de fois où l’utilisation du processeur a dépassé 80 %. |
| Écroulement de la mémoire |Représente la sollicitation de la mémoire sur les cœurs du serveur principal. Plus précisément, cette métrique indique le nombre de fois où des jeux de données ont été supprimés de la mémoire en raison de la sollicitation de celle-ci résultant de l’utilisation de nombreux jeux de données. |
| Utilisation de la mémoire |Utilisation moyenne de la mémoire, indiquée en gigaoctets (Go). |
| Requêtes directes/s | Nombre de fois où le nombre de requêtes directes (DirectQuery) et de connexions actives ont dépassé 80 % de la limite. <br>  Le nombre total de requêtes DirectQuery et de connexions actives par seconde est limité. Les limites sont 30/s pour P1, 60/s pour P2 et 120/s pour P3.  En ce qui concerne la limitation ci-dessus, les requêtes DirectQuery et les connexions actives sont comptabilisées ensemble. Par exemple, si vous avez 15 requêtes DirectQuerys et 15 connexions actives par seconde, vous avez atteint votre limite.<br> Ceci s’applique tant aux connexions locales qu’aux connexions cloud. |
|  |  |

Les métriques reflètent l’utilisation sur la dernière semaine.  Si vous souhaitez avoir une vue plus détaillée des métriques, cliquez sur les vignettes de résumé.  Des graphiques détaillés s’affichent pour chacune des métriques de votre capacité Premium. Le graphique suivant affiche les détails de la métrique de l’UC.

![Graphique d’utilisation détaillé - Processeur](media/service-admin-premium-monitor-capacity/premium-usage-detailed-chart-cpu.png)

Ces graphiques récapitulent les données de la dernière semaine par heure. Ils permettent d’isoler plus facilement les événements liés aux performances spécifiques dans votre capacité Premium.

Vous pouvez également exporter les données sous-jacentes de chacune des métriques dans un fichier csv.  Cette exportation fournit des informations détaillées par intervalle de trois minutes pour chaque jour de la dernière semaine.

## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous avez compris comment surveiller les capacités de Power BI Premium, vous pouvez en savoir plus sur l’optimisation des capacités.

> [!div class="nextstepaction"]
> [Gestion et optimisation des ressources de capacité de Power BI Premium](service-premium-understand-how-it-works.md)
