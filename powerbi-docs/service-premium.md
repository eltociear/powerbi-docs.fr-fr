---
title: Présentation de Microsoft Power BI Premium
description: Power BI Premium permet à votre organisation ou à votre équipe de bénéficier de performances plus fiables et de plus gros volumes de données sans qu’il soit nécessaire d’acquérir une licence pour chaque utilisateur.
author: minewiskan
ms.author: owend
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 01/15/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: a048f589b19acd1a7c38a5b81cf781d1e76b7b5b
ms.sourcegitcommit: 187d20180d9bae5a2ec53748cede9e7301e0343e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/23/2019
ms.locfileid: "56725337"
---
# <a name="what-is-microsoft-power-bi-premium"></a>Présentation de Microsoft Power BI Premium

Microsoft Power BI Premium fournit à votre organisation des ressources dédiées à l’exécution du service Power BI. Il vous offre des performances plus fiables et permet de traiter de gros volumes de données. Premium permet également une diffusion étendue du contenu sans qu’il soit nécessaire d’acquérir une licence Pro par utilisateur du contenu.  

## <a name="premium-capacity-and-shared-capacity"></a>Capacité Premium et capacité partagée

Pour tirer parti de Power BI Premium, attribuez des espaces de travail à une *capacité Premium*. Une capacité Premium est une ressource dédiée à votre organisation. Les espaces de travail non affectés à une capacité Premium sont attribués à une *capacité partagée*. Avec une capacité partagée, vos charges de travail s’exécutent sur des ressources de calcul partagées par d’autres clients.

L’illustration suivante montre la relation entre la capacité Premium et une capacité partagée, en prenant l’exemple de l’organisation Contoso.

![Illustration de Power BI Premium](media/service-premium/premium-chart.png)

| Zone | Description |
| --- | --- |
| **(1)** Éléments d’une capacité Premium | <ul><li>L’accès à des espaces de travail d’application (en tant que membres ou administrateurs) et la publication d’applications nécessitent une licence Power BI Pro.<li>Une licence Pro est nécessaire pour partager une application, mais pas pour l’utiliser.<li>Tous les destinataires du tableau de bord, quelle que soit la licence qui leur est attribuée, peuvent définir des alertes de données.<li>Les API REST d’incorporation utilisent un compte de service avec une licence Pro, et non un compte d’utilisateur.</ul> |
| **(2)** Mon espace de travail en mode Capacité partagée | <ul><li>Le partage et l’utilisation d’une application nécessitent une licence Pro.</ul> |
| **(3)** Espaces de travail d’applications en mode Capacité partagée | <ul><li>L’utilisation d’une application nécessite une licence Pro.</ul>|
| | |

Dans une capacité partagée, Power BI impose plus de limites aux utilisateurs individuels afin de garantir une expérience de qualité à tous les utilisateurs. Par défaut, votre espace de travail se trouve dans une capacité partagée, notamment votre espace *Mon espace de travail* personnel et vos espaces de travail d’application.

Le tableau suivant résume les différences entre la capacité partagée et la capacité Premium :

|  | Capacité partagée | Capacité Power BI Premium |
| --- | --- | --- |
| **Fréquence d’actualisation** |8/jour |48/jour |
| Isolement avec matériel dédié |![Non disponible](media/service-premium/not-available.png) |![](media/service-premium/available.png) |
| Distribution d’entreprise à *tous les utilisateurs* | | |
| Applications et partage |![Non disponible](media/service-premium/not-available.png) |![](media/service-premium/available.png) |
| API et commandes incorporées |![Non disponible](media/service-premium/not-available.png) |![](media/service-premium/available.png)<sup>[1](#fnt1)</sup> |
| Publier des rapports Power BI localement |![Non disponible](media/service-premium/not-available.png) |![](media/service-premium/available.png) |
| | | |

<a name="fnt1">1</a> Améliorations prévues dans Power BI Premium.



### <a name="premium-capacity-nodes"></a>Nœuds de capacité Premium

Power BI Premium est disponible dans des configurations de nœuds aux capacités différentes en termes de cœurs virtuels. Pour plus d’informations sur les offres et les coûts d’une référence SKU spécifique, voir [Prix de Power BI](https://powerbi.microsoft.com/pricing/). Un [module de calcul de coût](https://powerbi.microsoft.com/calculator/) est également disponible. Pour plus d’informations sur la planification d’une capacité d’analytique incorporée, consultez le [livre blanc Planification d’un déploiement de Power BI en entreprise](https://aka.ms/pbienterprisedeploy). Pour résumer :

* Les nœuds P peuvent être utilisés pour les déploiements incorporés ou pour les déploiements de services.

* Les nœuds EM sont réservés aux déploiements incorporés. Les nœuds EM n’ont pas accès aux fonctionnalités premium comme le partage d’applications avec des utilisateurs qui ne disposent pas d’une licence Power BI Pro.

| Nœud de capacité | Total des v-cores<br/>*(Back-end+front-end)*  | Cœurs virtuels back-end <sup>[1](#fn1)</sup> | Cœurs virtuels front-end <sup>[2](#fn2)</sup> | Limites de connexions actives/DirectQuery | Actualisations simultanées max. |  Disponibilité
| --- | --- | --- | --- | --- | --- | --- | --- |
| EM1 (de mois en mois) |1 v-core |0,5 cœur virtuel, 2,5 Go de RAM |0,5 cœur virtuel |3,75 par seconde |  1 | Disponible |
| EM2 (de mois en mois) |2 cœurs virtuels |1 cœur virtuel, 5 Go de RAM |1 v-core |7,5 par seconde |  2 | Disponible |
| EM3 (de mois en mois) |4 cœurs virtuels |2 cœurs virtuels, 10 Go de RAM |2 cœurs virtuels | | 3 |  Disponible |
| P1 |8 cœurs virtuels |4 cœurs virtuels, 25 Go de RAM |4 cœurs virtuels |30 par seconde | 6 | Disponible (de mois en mois est également disponible) |
| P2 |16 cœurs virtuels |8 cœurs virtuels, 50 Go de RAM |8 cœurs virtuels |60 par seconde | 12 | Disponible |
| P3 |32 cœurs virtuels |16 cœurs virtuels, 100 Go de RAM |16 cœurs virtuels |120 par seconde | 24 | Disponible |
| | | | | | | |

<a name="fn1">1</a> : Les cœurs virtuels front-end sont responsables du service web. Par exemple, des tableaux de bord et des rapports, des droits d’accès, de la planification, des API, des chargements et téléchargements et, plus généralement, de tout ce qui concerne l’expérience utilisateur. 

<a name="fn2">2</a> : Les cœurs virtuels back-end gèrent l’essentiel : traitement des requêtes, gestion du cache, exécution des serveurs R, actualisation des données, traitement du langage naturel, flux en temps réel et rendu côté serveur des rapports et images. Avec les v-cores principaux, une partie de la mémoire est également réservée. Car il est impératif de disposer d’une mémoire suffisante pour traiter les modèles de données volumineux ou les grands nombres de jeux de données actifs.

## <a name="workloads-in-premium-capacity"></a>Charges de travail dans une capacité Premium

Considérez une charge de travail dans Power BI comme un des nombreux services que vous pouvez présenter aux utilisateurs. Par défaut, les capacités pour **Power BI Premium** et **Power BI Embedded** prennent en charge uniquement la charge de travail associée aux requêtes Power BI exécutées dans le cloud.

Nous offrons désormais la prise en charge de la préversion de deux charges de travail supplémentaires : les **rapports paginés** et les **flux de données**. Vous autorisez ces charges de travail dans le portail d’administration Power BI ou via l’API REST de Power BI. Vous définissez également la mémoire maximale que chaque charge de travail peut consommer pour pouvoir contrôler la façon dont les différentes charges de travail s’affectent mutuellement. Pour plus d’informations, consultez [Configurer des charges de travail](service-admin-premium-manage.md#configure-workloads).

### <a name="default-memory-settings"></a>Paramètres de mémoire par défaut

Les tableaux suivants présentent les valeurs de mémoire par défaut et minimales en fonction des différents [nœuds de capacité](#premium-capacity-nodes) disponibles. La mémoire est allouée dynamiquement aux flux de données, mais elle est allouée statiquement aux rapports paginés. Pour plus d’informations, consultez la section suivante, [Considérations pour les rapports paginés](#considerations-for-paginated-reports).

#### <a name="microsoft-office-skus-for-software-as-a-service-saas-scenarios"></a>Références (SKU) Microsoft Office pour les scénarios SaaS (Software as a Service)

|                     | EM3                      | P1                       | P2                      | P3                       |
|---------------------|--------------------------|--------------------------|-------------------------|--------------------------|
| Rapports paginés | N/A | 20 % par défaut ; 10 % minimum | 20 % par défaut ; 5 % minimum | 20 % par défaut ; 2,5 % minimum |
| Flux de données | 20 % par défaut ; 8 % minimum  | 20 % par défaut ; 4 % minimum  | 20 % par défaut ; 2 % minimum | 20 % par défaut ; 1 % minimum  |
| | | | | |

#### <a name="microsoft-azure-skus-for-platform-as-a-service-paas-scenarios"></a>Références (SKU) Microsoft Azure pour les scénarios PaaS (Platform as a Service)

|                  | A1                       | A2                       | A3                      | A4                       | A5                      | A6                        |
|-------------------|--------------------------|--------------------------|-------------------------|--------------------------|-------------------------|---------------------------|
| Rapports paginés | N/A                      | N/A                      | N/A                     | 20 % par défaut ; 10 % minimum | 20 % par défaut ; 5 % minimum | 20 % par défaut ; 2,5 % minimum |
| Flux de données         | 27 % par défaut ; 27 % minimum | 20 % par défaut ; 16 % minimum | 20 % par défaut ; 8 % minimum | 20 % par défaut ; 4 % minimum  | 20 % par défaut ; 2 % minimum | 20 % par défaut ; 1 % minimum   |

### <a name="considerations-for-paginated-reports"></a>Considérations pour les rapports paginés

Si vous utilisez la charge de travail des rapports paginés, n’oubliez pas que les rapports paginés vous permettent d’exécuter votre propre code lors de la génération d’un rapport (par exemple, pour modifier dynamiquement la couleur du texte en fonction du contenu). De ce fait, nous sécurisons la capacité de Power BI Premium en exécutant des rapports paginés dans un espace contenu au sein de la capacité. Nous affectons la mémoire maximale que vous spécifiez à cet espace, que la charge de travail soit active ou non. Si vous utilisez des rapports Power BI ou des flux de données dans la même capacité, veillez à définir pour les rapports paginés une mémoire suffisamment faible qui n’affecte pas négativement les autres charges de travail.

dans de rares cas, la charge de travail des rapports paginés peut devenir indisponible. La charge de travail affiche alors un état d’erreur dans le portail d’administration, et les utilisateurs voient des délais d’expiration pour la génération des rapports. Pour résoudre ce problème, désactivez la charge de travail, puis réactivez-la.

## <a name="power-bi-report-server"></a>Power BI Report Server

Power BI Premium offre également la possibilité d’exécuter Power BI Report Server localement dans votre organisation. Pour en savoir plus, consultez [Bien démarrer avec Power BI Report Server](report-server/get-started.md).

## <a name="next-steps"></a>Étapes suivantes

[FAQ Power BI Premium](service-premium-faq.md)
[Guide pratique pour acheter Power BI Premium](service-admin-premium-purchase.md)
[Gérer Power BI Premium](service-admin-premium-manage.md)
[Livre blanc sur Microsoft Power BI Premium](https://aka.ms/pbipremiumwhitepaper)
[Livre blanc sur la planification d’un déploiement de Power BI dans une entreprise](https://aka.ms/pbienterprisedeploy)

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
