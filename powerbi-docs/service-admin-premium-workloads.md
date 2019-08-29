---
title: Guide pratique pour configurer des charges de travail dans Power BI Premium
description: Découvrez comment configurer des charges de travail dans une capacité Power BI Premium.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 08/21/2019
LocalizationGroup: Premium
ms.openlocfilehash: 2d2eb51c5aad44572f1b427248fd85ef19a6306f
ms.sourcegitcommit: e62889690073626d92cc73ff5ae26c71011e012e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69985693"
---
# <a name="configure-workloads-in-a-premium-capacity"></a>Configurer des charges de travail dans une capacité Premium

Cet article décrit comment activer et configurer des charges de travail pour les capacités Power BI Premium. Par défaut, les capacités prennent en charge uniquement la charge de travail qui est associée aux requêtes Power BI en cours d’exécution. Vous pouvez également activer et configurer des charges de travail supplémentaires pour **[IA (Cognitive Services)](service-cognitive-services.md)** , **[Flux de données](service-dataflows-overview.md#dataflow-capabilities-on-power-bi-premium)** et **[Rapports paginés](paginated-reports-save-to-power-bi-service.md)** .

## <a name="default-memory-settings"></a>Paramètres de mémoire par défaut

Les charges de travail de requête sont optimisées pour, et limitées par, les ressources déterminées par votre référence SKU de capacité Premium. Les capacités Premium prennent également en charge des charges de travail supplémentaires pouvant utiliser les ressources de votre capacité. Les valeurs de mémoire par défaut pour ces charges de travail dépendent des nœuds de capacité disponibles pour votre référence SKU. Les paramètres de mémoire maximale ne sont pas cumulés. La mémoire, à hauteur de la valeur maximale spécifiée, est allouée de façon dynamique pour l’IA et les dataflows, mais allouée de façon statique pour les rapports paginés.

### <a name="microsoft-office-skus-for-software-as-a-service-saas-scenarios"></a>Références (SKU) Microsoft Office pour les scénarios SaaS (Software as a Service)

|                     | EM2                      | EM3                       | P1                      | P2                       | P3                       |
|---------------------|--------------------------|--------------------------|-------------------------|--------------------------|--------------------------|
| Intelligence artificielle | N/A | N/A | 20 % par défaut ; 20 % minimum | 20 % par défaut ; 10 % minimum | 20 % par défaut ; 5 % minimum |
| Dataflows | N/A |20 % par défaut ; 12 % minimum  | 20 % par défaut ; 5 % minimum  | 20 % par défaut ; 3 % minimum | 20 % par défaut ; 2 % minimum  |
| Rapports paginés | N/A |N/A | 20 % par défaut ; 10 % minimum | 20 % par défaut ; 5 % minimum | 20 % par défaut ; 2,5 % minimum |
| | | | | | |

### <a name="microsoft-azure-skus-for-platform-as-a-service-paas-scenarios"></a>Références (SKU) Microsoft Azure pour les scénarios PaaS (Platform as a Service)

|                  | A1                       | A2                       | A3                      | A4                       | A5                      | A6                        |
|-------------------|--------------------------|--------------------------|-------------------------|--------------------------|-------------------------|---------------------------|
| Intelligence artificielle | N/A                      | 20 % par défaut ; 100 % minimum                     | 20 % par défaut ; 50 % minimum                     | 20 % par défaut ; 20 % minimum | 20 % par défaut ; 10 % minimum | 20 % par défaut ; 5 % minimum |
| Dataflows         | 40 % par défaut ; 40 % minimum | 24 % par défaut ; 24 % minimum | 20 % par défaut ; 12 % minimum | 20 % par défaut ; 5 % minimum  | 20 % par défaut ; 3 % minimum | 20 % par défaut ; 2 % minimum   |
| Rapports paginés | N/A                      | N/A                      | N/A                     | 20 % par défaut ; 10 % minimum | 20 % par défaut ; 5 % minimum | 20 % par défaut ; 2,5 % minimum |
| | | | | | |

## <a name="workload-settings"></a>Paramètres de charge de travail

### <a name="ai-preview"></a>IA (Préversion)

La charge de travail d’intelligence artificielle (IA) vous permet d’utiliser Cognitive Services et Machine Learning automatisé dans Power BI. Utilisez les paramètres suivants pour contrôler le comportement de la charge de travail.

| Nom du paramètre | Description |
|---------------------------------|----------------------------------------|
| **Mémoire maximale (%)** | Pourcentage maximal de mémoire disponible que les processus IA peuvent utiliser dans une capacité. |
| **Autoriser l’utilisation depuis Power BI Desktop** | Ce paramètre est réservé pour une utilisation ultérieure et n’apparaît pas dans tous les locataires. |
| **Autoriser la génération de modèles Machine Learning** | Spécifie si les analystes métier peuvent entraîner, valider et appeler des modèles Machine Learning directement dans Power BI. Pour plus d’informations, consultez [Machine Learning automatisé dans Power BI (préversion)](service-machine-learning-automated.md). |
| **Activer le parallélisme pour les demandes IA** | Spécifie si les demandes IA peuvent s’exécuter en parallèle. |
|  |  |

### <a name="datasets"></a>Jeux de données

La charge de travail des jeux de données est activée par défaut et ne peut pas être désactivée. Utilisez les paramètres suivants pour contrôler le comportement de la charge de travail.

| Nom du paramètre | Description |
|---------------------------------|----------------------------------------|
| **Mémoire maximale (%)** | Pourcentage maximal de mémoire disponible que les jeux de données peuvent utiliser dans une capacité. |
| **Point de terminaison XMLA** | Spécifie que les connexions à partir d’applications clientes respectent l’appartenance au groupe de sécurité définie au niveau de l’espace de travail et au niveau de l’application. Pour plus d’informations, consultez [Se connecter à des jeux de données avec des applications et des outils clients](service-premium-connect-tools.md). |
| **Nombre maximal de lignes intermédiaires** | Nombre maximal de lignes intermédiaires retournées par DirectQuery. La valeur par défaut est 1000000 et la plage autorisée est comprise entre 100000 et 2147483647. Utilisez ce paramètre pour contrôler l’impact des rapports qui consomment beaucoup de ressources ou qui sont mal conçus. |
| **Taille max. du jeu de données hors connexion (Go)** | Taille maximale du jeu de données hors connexion en mémoire. Il s’agit de la taille compressée sur le disque. La valeur par défaut est définie par la référence SKU et la plage autorisée est comprise entre 0,1 et 10 Go. Utilisez ce paramètre pour empêcher les créateurs de rapports de publier un jeu de données volumineux qui peut avoir un impact négatif sur la capacité. |
| **Nombre maximal de lignes de résultat** | Nombre maximal de lignes retournées dans une requête DAX. La valeur par défaut est -1 (aucune limite) et la plage autorisée est comprise entre 100000 et 2147483647. Utilisez ce paramètre pour contrôler l’impact des rapports qui consomment beaucoup de ressources ou qui sont mal conçus. |
| **Limite de mémoire de requête (%)** | Pourcentage maximal de mémoire disponible qui peut être utilisé pour des résultats temporaires dans une requête ou une mesure DAX. Utilisez ce paramètre pour contrôler l’impact des rapports qui consomment beaucoup de ressources ou qui sont mal conçus. |
| **Délai d’expiration de la requête (secondes)** | Durée maximale avant l’expiration d’une requête. La valeur par défaut est 3600 secondes (1 heure). La valeur 0 indique que les requêtes n’expirent pas. Utilisez ce paramètre pour mieux contrôler les requêtes longues. |
|  |  |  |

### <a name="dataflows"></a>Dataflows

La charge de travail des dataflows vous permet d’utiliser la préparation des données en libre-service des dataflows pour ingérer, transformer, intégrer et enrichir les données. Utilisez les paramètres suivants pour contrôler le comportement de la charge de travail.

| Nom du paramètre | Description |
|---------------------------------|----------------------------------------|
| **Mémoire maximale (%)** | Pourcentage maximal de mémoire disponible que les dataflows peuvent utiliser dans une capacité. |
| **Moteur de calcul de dataflows avancé (préversion)** | Activez cette option pour un calcul jusqu’à 20 fois plus rapide d’entités calculées lors de l’utilisation de volumes de données à grande échelle. **Vous devez redémarrer la capacité pour activer le nouveau moteur.** Pour plus d’informations, consultez [Moteur de calcul de dataflows avancé](#enhanced-dataflows-compute-engine). |
| **Taille du conteneur** | Taille maximale du conteneur que les dataflows utilisent pour chaque entité dans le dataflow. La valeur par défaut est 700 Mo. Pour plus d’informations, consultez [Taille du conteneur](#container-size). |
|  |  |

#### <a name="enhanced-dataflows-compute-engine"></a>Moteur de calcul de dataflows avancé

Pour tirer parti du nouveau moteur de calcul, fractionnez l’ingestion des données en dataflows séparés et placez la logique de transformation dans des entités calculées de différents dataflows. Cette approche est recommandée, car le moteur de calcul fonctionne sur les dataflows qui référencent un dataflow existant. Il ne fonctionne pas sur les dataflows d’ingestion. Le fait de suivre ce guide garantit que le nouveau moteur de calcul gère les étapes de transformation, telles que les jointures et les fusions, pour des performances optimales.

#### <a name="container-size"></a>Taille du conteneur

Lors de l’actualisation d’un dataflow, la charge de travail du dataflow génère un conteneur pour chaque entité dans le dataflow. Chaque conteneur peut prendre de la mémoire jusqu’au volume spécifié dans le paramètre **Taille du conteneur. La valeur par défaut pour toutes les références SKU est 700 Mo. Vous pouvez souhaiter modifier ce paramètre si :

- L’actualisation des dataflows prend trop de temps ou l’actualisation d’un dataflow échoue en cas d’expiration du délai.
- Les entités de dataflow incluent des étapes de calcul ; par exemple, une jointure.  

Il est recommandé d’utiliser l’application [Métriques de capacité Power BI Premium](service-admin-premium-monitor-capacity.md) pour analyser les performances de la charge de travail Dataflows.

Dans certains cas, l’augmentation de la taille du conteneur peut ne pas améliorer les performances. Par exemple, si le dataflow obtient des données uniquement à partir d’une source sans effectuer de calculs significatifs, il est probable que changer la taille du conteneur ne sera d’aucune utilité. Augmenter la taille du conteneur peut être utile si cela permet à la charge de travail Dataflows d’allouer davantage de mémoire pour les opérations d’actualisation d’entité. Le fait d’allouer davantage de mémoire permet de réduire le temps nécessaire à l’actualisation des entités comportant beaucoup de calculs.

La valeur Taille du conteneur ne peut pas dépasser la mémoire maximale définie pour la charge de travail Dataflows. Par exemple, une capacité P1 dispose de 25 Go de mémoire. Si le paramètre Mémoire maximale (%) de la charge de travail Dataflows est défini sur 20 %, la valeur Taille du conteneur (Mo) ne peut pas dépasser 5 000. Dans tous les cas, la valeur Taille du conteneur ne peut pas dépasser la valeur Mémoire maximale, même si vous définissez une valeur supérieure.

### <a name="paginated-reports"></a>Rapports paginés

La charge de travail des rapports paginés vous permet d’exécuter des rapports paginés, basés sur le format SQL Server Reporting Services standard, dans le service Power BI. Utilisez le paramètre suivant pour contrôler le comportement de la charge de travail.

| Nom du paramètre | Description |
|---------------------------------|----------------------------------------|
| **Mémoire maximale (%)** | Pourcentage maximal de mémoire disponible que les rapports paginés peuvent utiliser dans une capacité. |
|  |  |

Les rapports paginés permettent d’exécuter du code personnalisé lors du rendu d’un rapport. C’est, par exemple, le cas lors du changement dynamique de la couleur du texte en fonction du contenu, ce qui peut prendre de la quantité supplémentaire de mémoire. Power BI Premium génère les rapports paginés dans un espace contenu au sein de la capacité. La valeur Mémoire maximale spécifiée est utilisée, que la charge de travail soit *ou non* active. Si vous changez la valeur par défaut du paramètre Mémoire maximale, veillez à définir une valeur suffisamment faible pour qu’elle n’affecte pas négativement les autres charges de travail.

Dans certains cas, la charge de travail des rapports paginés peut devenir indisponible. La charge de travail affiche alors un état d’erreur dans le portail d’administration, et les utilisateurs voient des délais d’expiration pour la génération des rapports. Pour résoudre ce problème, désactivez la charge de travail, puis réactivez-la.

## <a name="configure-workloads"></a>Configurer des charges de travail

Optimisez les ressources disponibles de votre capacité en activant uniquement les charges de travail qui seront utilisées. Ne changez les paramètres de mémoire et d’autres paramètres que si vous avez constaté que les paramètres par défaut ne répondent pas aux besoins en ressources de votre capacité.

### <a name="to-configure-workloads-in-the-power-bi-admin-portal"></a>Pour configurer des charges de travail dans le portail d’administration Power BI

1. Dans **Paramètres de capacité** > **CAPACITÉS PREMIUM**, sélectionnez une capacité.

1. Sous **PLUS D’OPTIONS**, développez **Charges de travail**.

1. Activez une ou plusieurs charges de travail, puis définissez une valeur pour **Mémoire maximale** et d’autres paramètres.

1. Sélectionnez **Appliquer**.

### <a name="rest-api"></a>API REST

Les charges de travail peuvent être activées et attribuées à une capacité à l’aide des API REST [Capacités](https://docs.microsoft.com/rest/api/power-bi/capacities).

## <a name="monitoring-workloads"></a>Surveillance des charges de travail

L’[application Métriques de capacité Power BI Premium](service-admin-premium-monitor-capacity.md) fournit un jeu de données, des flux de données et des métriques de rapports paginés afin de surveiller les charges de travail activées pour vos capacités. 

## <a name="next-steps"></a>Étapes suivantes

[Optimisation des capacités Power BI Premium](service-premium-capacity-optimize.md)     
[Préparation des données en libre-service dans Power BI avec des dataflows](service-dataflows-overview.md)   
[Présentation des rapports paginés dans Power BI Premium](paginated-reports-report-builder-power-bi.md)   

D’autres questions ? [Poser des questions à la communauté Power BI](http://community.powerbi.com/)