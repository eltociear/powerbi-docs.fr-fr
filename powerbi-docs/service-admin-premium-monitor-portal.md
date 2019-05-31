---
title: Superviser les capacités Power BI Premium avec le portail d’administration
description: Utilisez le portail d’administration Power BI pour superviser vos capacités Premium.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/10/2019
LocalizationGroup: Premium
ms.openlocfilehash: 36b03a67e7c02702a70b6486880cc8eabf93e823
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "65564890"
---
# <a name="monitor-capacities-in-the-admin-portal"></a>Superviser les capacités dans le portail d’administration

Le **intégrité** onglet dans le **les paramètres de capacité** zone dans le portail d’administration fournit un métriques récapitulatives sur vos charges de travail de la capacité et est activées.  

![La capacité onglet intégrité dans le portail](media/service-admin-premium-monitor-portal/admin-portal-health.png)

Si vous avez besoin de mesures plus complètes, utilisez la [métriques de capacité Power BI Premium](service-admin-premium-monitor-capacity.md) application. L’application fournit le zoom et de filtrage, et les mesures plus détaillés pour presque tous les aspects qui affectent les performances de capacité. Pour plus d’informations, consultez [capacités Premium de moniteur avec l’application](service-admin-premium-monitor-capacity.md).

## <a name="system-metrics"></a>Mesures système

Sur le **intégrité** sous l’onglet du niveau le plus élevé, l’utilisation du processeur et utilisation de la mémoire fournissent un aperçu rapide des mesures plus importantes pour la capacité. Ces mesures sont cumulatifs, y compris tous les deux activés pour la capacité des charges de travail.

| **Métrique** | **Description** |
| --- | --- |
| UTILISATION DU PROCESSEUR | Utilisation moyenne du processeur, sous forme de pourcentage d’UC totale disponible. |
| UTILISATION DE LA MÉMOIRE | Utilisation moyenne de mémoire en gigaoctets (Go).|

## <a name="workload-metrics"></a>Métriques de charge de travail

Pour chaque charge de travail est activé pour la capacité. Utilisation du processeur et utilisation de la mémoire sont affichées.

| **Métrique** | **Description** |
| --- | --- |
| UTILISATION DU PROCESSEUR | Utilisation moyenne du processeur, sous forme de pourcentage d’UC totale disponible. |
| UTILISATION DE LA MÉMOIRE | Utilisation moyenne de mémoire en gigaoctets (Go).|

### <a name="detailed-workload-metrics"></a>Métriques de charge de travail détaillé

Chaque charge de travail a des mesures supplémentaires. Le type des métriques affichées dépendent de la charge de travail. Pour afficher des mesures détaillées pour une charge de travail, cliquez sur Développer (bas).

![Développez de contrôle d’intégrité de la charge de travail](media/service-admin-premium-monitor-portal/admin-portal-health-expand.png)

#### <a name="dataflows"></a>Flux de données

##### <a name="dataflow-operations"></a>Opérations de flux de données

| **Métrique** | **Description** |
| --- | --- |
| Nombre total | total des actualisations pour chaque flux de données. |
| Nombre de succès | Actualisations de réussite total pour chaque flux de données.|
| Durée moyenne (min) | durée moyenne d’actualisation du flux de données, en minutes |
| Durée maximale (min) | durée de l’actualisation la plus longue en cours d’exécution pour le flux de données, en minutes. |
| Temps d’attente moyen (min) | délai moyen entre l’heure planifiée et le début d’une actualisation du flux de données, en minutes. |
| Temps d’attente maximal (min) | délai d’attente maximal du flux de données, en minutes.  |

#### <a name="datasets"></a>Jeux de données

##### <a name="refresh"></a>Actualiser

| **Métrique** | **Description** |
| --- | --- |
| Nombre total | nombre total d’actualisations pour chaque jeu de données. |
| Nombre de succès | Actualisations de réussite total pour chaque jeu de données. |
| Nombre d’échecs | Nombre total échec des actualisations pour chaque jeu de données. |
| Taux de réussite  | Nombre d’actualisations réussites divisé par les total actualisations pour mesurer. Fiabilité. |
| Durée moyenne (min) | durée moyenne d’actualisation du jeu de données, en minutes.  |
| Durée maximale (min) | durée de l’actualisation la plus longue en cours d’exécution pour le jeu de données, en minutes. |
| Temps d’attente moyen (min) | délai moyen entre l’heure planifiée et le début d’une actualisation du jeu de données, en minutes. |
| Temps d’attente maximal (min) | délai d’attente maximal du jeu de données, en minutes. |

##### <a name="query"></a>Requête

| **Métrique** | **Description** |
| --- | --- |
| Nombre total | Nombre total de requêtes exécutées pour le jeu de données. |
| Durée moyenne (ms) |durée moyenne des requêtes pour le jeu de données, en millisecondes|
| Durée maximale (ms) |Durée de la requête dont l’exécution est la plus longue dans le jeu de données, en millisecondes. |
| Temps d'attente moyen (ms) |Temps d’attente moyen des requêtes pour le jeu de données, en millisecondes. |
| Temps d’attente maximal (ms) |Durée de la requête à l’attente la plus longue dans le jeu de données, en millisecondes. |

##### <a name="eviction"></a>Eviction

| **Métrique** | **Description** |
| --- | --- |
| Nombre de modèle | Le nombre total de suppressions dans le jeu de données pour cette capacité. Quand une capacité est confrontée à une sollicitation de la mémoire, le nœud supprime un ou plusieurs jeux de données de la mémoire. Les jeux de données qui sont inactifs (ceux pour lesquels aucune opération d’interrogation ou d’actualisation n’est en cours d’exécution) sont supprimés en premier. Ensuite, l’ordre d’éviction est basé sur une mesure dite « dernier récemment utilisé (LRU) ». |

#### <a name="paginated-reports"></a>Rapports paginés

##### <a name="report-execution"></a>Exécution des rapports

| **Métrique** | **Description** |
| --- | --- |
| Nombre d’exécutions  | Le nombre de fois où le rapport a été exécuté et affiché par les utilisateurs.|

##### <a name="report-usage"></a>Utilisation des rapports

| **Métrique** | **Description** |
| --- | --- |
| Nombre de succès | Le nombre de fois où que le rapport a été affiché par un utilisateur. |
| Nombre d’échecs |Le nombre de fois où que le rapport a été affiché par un utilisateur.|
| Nombre de lignes |nombre de lignes de données dans le rapport. |
| Durée de récupération de données (ms) |délai moyen nécessaire pour récupérer des données pour le rapport, en millisecondes. De longs délais peuvent indiquer des requêtes lentes ou d’autres problèmes au niveau de la source de données.  |
| Durée de traitement (ms) |délai moyen nécessaire pour traiter les données pour un rapport, en millisecondes. |
| Durée de rendu (ms) |délai moyen nécessaire pour afficher un rapport dans le navigateur, en millisecondes. |

> [!NOTE]
> Détaillée des métriques pour le **AI** charge de travail ne sont pas encore disponibles.

## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous avez compris comment surveiller les capacités de Power BI Premium, vous pouvez en savoir plus sur l’optimisation des capacités.

> [!div class="nextstepaction"]
> [Optimisation des capacités Power BI Premium](service-premium-capacity-optimize.md)
