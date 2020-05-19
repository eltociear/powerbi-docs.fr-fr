---
title: Guide pratique pour configurer des charges de travail dans Power BI Premium
description: Découvrez comment configurer des charges de travail dans une capacité Power BI Premium.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 05/11/2020
LocalizationGroup: Premium
ms.openlocfilehash: f76763eba578c05102eda60077f110ba752949bc
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83274509"
---
# <a name="configure-workloads-in-a-premium-capacity"></a>Configurer des charges de travail dans une capacité Premium

Cet article décrit comment activer et configurer des charges de travail pour les capacités Power BI Premium. Par défaut, les capacités prennent en charge uniquement la charge de travail qui est associée aux requêtes Power BI en cours d’exécution. Vous pouvez également activer et configurer des charges de travail supplémentaires pour **[IA (Cognitive Services)](../transform-model/service-cognitive-services.md)** , **[Flux de données](../transform-model/service-dataflows-overview.md#dataflow-capabilities-on-power-bi-premium)** et **[Rapports paginés](../paginated-reports/paginated-reports-save-to-power-bi-service.md)** .

## <a name="default-memory-settings"></a>Paramètres de mémoire par défaut

Les charges de travail de requête sont optimisées pour, et limitées par, les ressources déterminées par votre référence SKU de capacité Premium. Les capacités Premium prennent également en charge des charges de travail supplémentaires pouvant utiliser les ressources de votre capacité. Les valeurs de mémoire par défaut pour ces charges de travail dépendent des nœuds de capacité disponibles pour votre référence SKU. Les paramètres de mémoire maximale ne sont pas cumulés. La mémoire, à hauteur de la valeur maximale spécifiée, est allouée de façon dynamique pour l’IA et les dataflows, mais allouée de façon statique pour les rapports paginés.

|                   | EM1 / A1                  | EM2 / A2                  | EM3 / A3                  | P1 / A4                  | P2 / A5                  | P3 / A6                   |
|-------------------|---------------------------|---------------------------|---------------------------|--------------------------|--------------------------|---------------------------|
| Intelligence artificielle                | Non pris en charge               | 40 % par défaut ; 40 % minimum  | 20 % par défaut ; 20 % minimum  | 20 % par défaut ; 8 % minimum  | 20 % par défaut ; 4 % minimum  | 20 % par défaut ; 2 % minimum   |
| Jeux de données          | 100 % par défaut ; 67 % minimum | 100 % par défaut ; 40 % minimum | 100 % par défaut ; 20 % minimum | 100 % par défaut ; 8 % minimum | 100 % par défaut ; 4 % minimum | 100 % par défaut ; 2 % minimum  |
| Dataflows         | 40 % par défaut ; 40 % minimum  | 24 % par défaut ; 24 % minimum  | 20 % par défaut ; 12 % minimum  | 20 % par défaut ; 5 % minimum  | 20 % par défaut ; 3 % minimum  | 20 % par défaut ; 2 % minimum   |
| Rapports paginés | Non pris en charge               | Non pris en charge               | Non pris en charge               | 20 % par défaut ; 10 % minimum | 20 % par défaut ; 5 % minimum  | 20 % par défaut ; 2,5 % minimum |
|                   |                           |                           |                           |                          |                          |                           |

## <a name="workload-settings"></a>Paramètres de charge de travail

### <a name="ai-preview"></a>IA (Préversion)

La charge de travail d’intelligence artificielle (IA) vous permet d’utiliser Cognitive Services et Machine Learning automatisé dans Power BI. Utilisez les paramètres suivants pour contrôler le comportement de la charge de travail.

| Nom du paramètre | Description |
|---------------------------------|----------------------------------------|
| **Mémoire maximale (%)** | Pourcentage maximal de mémoire disponible que les processus IA peuvent utiliser dans une capacité. |
| **Autoriser l’utilisation depuis Power BI Desktop** | Ce paramètre est réservé pour une utilisation ultérieure et n’apparaît pas dans tous les locataires. |
| **Autoriser la génération de modèles Machine Learning** | Spécifie si les analystes métier peuvent entraîner, valider et appeler des modèles Machine Learning directement dans Power BI. Pour plus d’informations, consultez [Machine Learning automatisé dans Power BI (préversion)](../transform-model/service-machine-learning-automated.md). |
| **Activer le parallélisme pour les demandes IA** | Spécifie si les demandes IA peuvent s’exécuter en parallèle. |
|  |  |

### <a name="datasets"></a>Jeux de données

La charge de travail des jeux de données est activée par défaut et ne peut pas être désactivée. Utilisez les paramètres suivants pour contrôler le comportement de la charge de travail. Des informations d’utilisation supplémentaires sont fournies sous le tableau pour certains paramètres.

| Nom du paramètre | Description |
|---------------------------------|----------------------------------------|
| **Mémoire maximale (%)** | Pourcentage maximal de mémoire disponible que les jeux de données peuvent utiliser dans une capacité. |
| **Point de terminaison XMLA** | Spécifie que les connexions à partir d’applications clientes respectent l’appartenance au groupe de sécurité définie au niveau de l’espace de travail et au niveau de l’application. Pour plus d’informations, consultez [Se connecter à des jeux de données avec des applications et des outils clients](service-premium-connect-tools.md). |
| **Nombre maximal de lignes intermédiaires** | Nombre maximal de lignes intermédiaires retournées par DirectQuery. La valeur par défaut est 1000000 et la plage autorisée est comprise entre 100000 et 2147483647. |
| **Taille max. du jeu de données hors connexion (Go)** | Taille maximale du jeu de données hors connexion en mémoire. Il s’agit de la taille compressée sur le disque. La valeur par défaut est 0 (ce qui correspond à la limite la plus élevée définie par la référence SKU). La plage autorisée est comprise entre 0 et la taille limite de la capacité. |
| **Nombre maximal de lignes de résultat** | Nombre maximal de lignes retournées dans une requête DAX. La valeur par défaut est -1 (aucune limite) et la plage autorisée est comprise entre 100000 et 2147483647. |
| **Limite de mémoire de requête (%)** | Pourcentage maximal de mémoire disponible dans la charge de travail qui peut être utilisé pour exécuter une requête MDX ou DAX. La valeur par défaut est 0, ce qui entraîne l’application de la limite de mémoire de requête automatique propre à la référence SKU. |
| **Délai d’expiration de la requête (secondes)** | Durée maximale avant l’expiration d’une requête. La valeur par défaut est 3600 secondes (1 heure). La valeur 0 indique que les requêtes n’expirent pas. |
| **Actualisation automatique des pages (préversion)** | Commutateur pour autoriser les espaces de travail Premium à avoir des rapports avec l’actualisation automatique des pages. |
| **Intervalle minimal d'actualisation** | Si l’actualisation automatique de la page est activée, il s’agit de l’intervalle minimal autorisé pour l’intervalle d’actualisation de la page. La valeur par défaut est de cinq minutes, et la valeur minimale autorisée est d’une seconde. |
|  |  |  |

#### <a name="max-intermediate-row-set-count"></a>Nombre maximal de lignes intermédiaires

Utilisez ce paramètre pour contrôler l’impact des rapports qui consomment beaucoup de ressources ou qui sont mal conçus. Quand une requête sur un jeu de données DirectQuery génère une très grande quantité de résultats de la base de données source, cela peut entraîner une hausse soudaine de l’utilisation de la mémoire et de la charge de traitement. Cette situation peut provoquer un problème de ressources insuffisantes pour d’autres utilisateurs et rapports. Ce paramètre permet à l’administrateur de la capacité d’ajuster le nombre de lignes qu’une requête individuelle peut extraire de la source de données.

Sinon, si la capacité prend en charge plus d’un million de lignes, qui est la valeur par défaut, et que vous avez un jeu de données volumineux, augmentez ce paramètre pour extraire plus de lignes.

Notez que ce paramètre s’applique uniquement aux requêtes DirectQuery, alors que le paramètre [Nombre maximal de lignes intermédiaires](#max-result-row-set-count) concerne les requêtes DAX.

#### <a name="max-offline-dataset-size"></a>Taille max. du jeu de données hors connexion

Utilisez ce paramètre pour empêcher les créateurs de rapports de publier un jeu de données volumineux qui peut avoir un impact négatif sur la capacité. Notez que Power BI ne peut pas déterminer la taille en mémoire réelle tant que le jeu de données n’a pas été chargé en mémoire. Un jeu de données d’une taille hors connexion plus petite peut avoir une empreinte mémoire plus grande qu’un jeu de données d’une taille hors connexion plus grande.

Si vous avez un jeu de données plus grand que la taille que vous spécifiez pour ce paramètre, le jeu de données échoue à se charger quand un utilisateur tente d’y accéder. Le chargement du jeu de données peut également échouer si la taille de ce dernier est supérieure à la mémoire maximale configurée pour la charge de travail des jeux de données.

Pour préserver les performances du système, une limite stricte spécifique à la référence SKU pour la taille maximale du jeu de données hors connexion est appliquée, quelle que soit la valeur configurée. Cette limite stricte ne s’applique pas aux jeux de données Power BI qui sont optimisés pour les grandes tailles de données. Pour plus d’informations, consultez [Grands modèles dans Power BI Premium](service-premium-large-models.md).

|                                           | EM1 / A1 | EM2 / A2 | EM3 / A3 | P1 / A4 | P2 / A5 | P3 / A6 |   
|-------------------------------------------|----------|----------|----------|---------|---------|---------|
| Limite stricte pour la taille maximale des jeux de données hors connexion | 3 Go     | 5 Go     | 6 Go     | 10 Go   | 10 Go   | 10 Go   |
|                                           |          |          |          |         |         |         |

#### <a name="max-result-row-set-count"></a>Nombre maximal de lignes de résultat

Utilisez ce paramètre pour contrôler l’impact des rapports qui consomment beaucoup de ressources ou qui sont mal conçus. Si cette limite est atteinte dans une requête DAX, les utilisateurs des rapports voient l’erreur suivante. Ils doivent alors copier les détails de l’erreur et contacter un administrateur.

![Impossible de charger les données de cet élément visuel](media/service-admin-premium-workloads/could-not-load-data.png)

Notez que ce paramètre s’applique uniquement aux requêtes DAX, alors que le paramètre [Nombre maximal de lignes intermédiaires](#max-intermediate-row-set-count) concerne les requêtes DirectQuery.

#### <a name="query-memory-limit"></a>Limite de mémoire de requête

Utilisez ce paramètre pour contrôler l’impact des rapports qui consomment beaucoup de ressources ou qui sont mal conçus. Certaines requêtes et certains calculs peuvent générer des résultats intermédiaires qui utilisent beaucoup de mémoire sur la capacité. Cette situation peut ralentir fortement l’exécution d’autres requêtes, donner lieu à l’éviction d’autres jeux de données de la capacité et provoquer des erreurs de mémoire insuffisante pour d’autres utilisateurs de la capacité.

Ce paramètre s’applique à toutes les requêtes DAX et MDX exécutées par les rapports Power BI, les rapports Analyser dans Excel, ainsi que d’autres outils susceptibles de se connecter via le point de terminaison XMLA.

Notez que les opérations d’actualisation des données peuvent également exécuter des requêtes DAX dans le cadre de l’actualisation des vignettes de tableaux de bord et des caches de visuels une fois les données du jeu de données actualisées. De telles requêtes peuvent également échouer en raison de ce paramètre, ce qui peut faire apparaître l’opération d’actualisation des données en état d’échec, même si les données du jeu de données ont bien été mises à jour.

Le paramètre par défaut est 0, ce qui entraîne l’application de la limite de mémoire de requête automatique propre à la référence SKU suivante.

|                              | EM1 / A1 | EM2 / A2 | EM3 / A3 | P1 / A4 | P2 / A5 | P3 / A6 |   
|------------------------------|----------|----------|----------|---------|---------|---------|
| Limite de mémoire de requête automatique | 1 Go     | 2 Go     | 2 Go     | 6 Go    | 6 Go    | 10 Go   |
|                              |          |          |          |         |         |         |

Pour préserver les performances du système, une limite stricte de 10 Go est appliquée pour toutes les requêtes exécutées par les rapports Power BI, quelle que soit la limite de mémoire de requête configurée par l’utilisateur. Cette limite stricte ne s’applique pas aux requêtes envoyées par des outils qui utilisent le protocole Analysis Services (également appelé XMLA). Les utilisateurs doivent essayer de simplifier la requête ou ses calculs si la requête utilise trop de mémoire.

#### <a name="query-timeout"></a>Délai d’expiration de la requête

Utilisez ce paramètre pour mieux contrôler les requêtes de longue durée, lesquelles peuvent ralentir le chargement des rapports pour les utilisateurs.

Ce paramètre s’applique à toutes les requêtes DAX et MDX exécutées par les rapports Power BI, les rapports Analyser dans Excel, ainsi que d’autres outils susceptibles de se connecter via le point de terminaison XMLA.

Notez que les opérations d’actualisation des données peuvent également exécuter des requêtes DAX dans le cadre de l’actualisation des vignettes de tableaux de bord et des caches de visuels une fois les données du jeu de données actualisées. De telles requêtes peuvent également échouer en raison de ce paramètre, ce qui peut faire apparaître l’opération d’actualisation des données en état d’échec, même si les données du jeu de données ont bien été mises à jour.

Ce paramètre s’applique à chaque requête, et pas à la durée d’exécution de toutes les requêtes liées à la mise à jour d’un jeu de données ou d’un rapport. Prenez l’exemple suivant :

- Le paramètre **Délai d’expiration de la requête** a la valeur 1 200 (20 minutes).
- Il y a cinq requêtes à exécuter, chacune d’elles s’exécutant en 15 minutes.

La durée totale d’exécution de toutes les requêtes est de 75 minutes, mais le délai maximal défini n’est pas atteint, car les différentes requêtes s’exécutent individuellement en moins de 20 minutes.

Notez que les rapports Power BI ignorent cette valeur par défaut et appliquent un délai d’expiration très inférieur pour chaque requête sur la capacité. Le délai d’expiration par requête est généralement de trois minutes environ.

#### <a name="automatic-page-refresh-preview"></a>Actualisation automatique des pages (préversion)

Lorsqu’elle est activée, l’actualisation automatique des pages permet aux utilisateurs de votre capacité Premium d’actualiser les pages de leur rapport à un intervalle défini, pour les sources DirectQuery. En tant qu’administrateur de capacité, vous pouvez effectuer les opérations suivantes :

- Activer et désactiver l’actualisation automatique des pages
- Définir un intervalle minimal d'actualisation

L’illustration suivante montre l’emplacement du paramètre d’intervalle d’actualisation automatique :

![paramètre administrateur pour l’intervalle d’actualisation automatique](media/service-admin-premium-workloads/automatic-refresh-interval.png)

Les requêtes créées par l’actualisation automatique de la page vont directement à la source de données. Il est donc important de tenir compte de la fiabilité et de la charge sur ces sources lorsque vous autorisez l’actualisation automatique de la page dans votre organisation. 

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

Lors de l’actualisation d’un dataflow, la charge de travail du dataflow génère un conteneur pour chaque entité dans le dataflow. Chaque conteneur peut prendre de la mémoire jusqu’au volume spécifié dans le paramètre Taille du conteneur. La valeur par défaut pour toutes les références SKU est 700 Mo. Vous pouvez souhaiter modifier ce paramètre si :

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

Les rapports paginés offrent les mêmes possibilités que les rapports SQL Server Reporting Services (SSRS) actuels, y compris la possibilité pour les créateurs de rapports d’ajouter du code personnalisé.  Les auteurs peuvent alors modifier dynamiquement les rapports, par exemple en changeant les couleurs de texte en fonction des expressions de code.  Pour assurer une isolation appropriée, les rapports paginés sont générés dans un bac à sable (sandbox) protégé pour chaque capacité. La génération de rapports avec la même capacité peut provoquer des effets secondaires entre les rapports. De la même façon que vous pouvez restreindre les auteurs autorisés à publier du contenu sur une instance de SSRS, nous vous recommandons de suivre une pratique similaire avec les rapports paginés. Assurez-vous que les auteurs qui publient du contenu sur une capacité sont approuvés par l’organisation. Vous pouvez renforcer la sécurité de votre environnement en provisionnant plusieurs capacités et en affectant des auteurs différents à chacune d’elles. 

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


> [!IMPORTANT]
> Si votre capacité Power BI Premium subit une utilisation intensive des ressources entraînant des problèmes de performances ou de fiabilité, vous pouvez recevoir des e-mails de notification pour identifier et résoudre le problème. Il peut s’agir d’un moyen simplifié de dépanner les capacités surchargées. Pour plus d’informations, consultez les [notifications de capacité et de fiabilité](service-interruption-notifications.md#capacity-and-reliability-notifications).


## <a name="next-steps"></a>Étapes suivantes

[Optimisation des capacités Power BI Premium](service-premium-capacity-optimize.md)
[Préparation des données en libre-service dans Power BI](../transform-model/service-dataflows-overview.md)
[Présentation des rapports paginés dans Power BI Premium](../paginated-reports/paginated-reports-report-builder-power-bi.md)
[Actualisation automatique des pages dans Power BI Desktop (préversion)](../create-reports/desktop-automatic-page-refresh.md)

D’autres questions ? [Poser des questions à la communauté Power BI](https://community.powerbi.com/)
