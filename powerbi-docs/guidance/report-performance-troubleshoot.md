---
title: Résoudre les problèmes de performances de rapports dans Power BI
description: Guide de résolution des problèmes pour diagnostiquer les performances de rapport lentes dans Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/15/2020
ms.author: v-pemyer
ms.openlocfilehash: a5230a39706ce5d6941c00386160fe10114442e1
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "81527988"
---
# <a name="troubleshoot-report-performance-in-power-bi"></a>Résoudre les problèmes de performances de rapports dans Power BI

Cet article fournit des conseils qui permettent aux développeurs et aux administrateurs de résoudre les problèmes de performances de rapport lentes. Il concerne les rapports Power BI ainsi que les rapports paginés Power BI.

Les rapports lents peuvent être identifiés par les utilisateurs de rapports confrontés à des rapports lents à charger ou à mettre à jour lors de l’interaction avec des segments ou d’autres fonctionnalités. Lorsque les rapports sont hébergés sur une capacité Premium, il est également possible d’identifier les rapports lents en surveillant l’[application Power BI Premium Metrics](../service-admin-premium-monitor-capacity.md). Cette application vous permet de surveiller l’intégrité et la capacité de votre abonnement Power BI Premium.

## <a name="follow-flowchart-steps"></a>Suivre les étapes de l’organigramme

Utilisez l’organigramme suivant pour mieux comprendre la cause du ralentissement des performances et déterminer la mesure à prendre.

:::image type="content" source="media/report-performance-troubleshoot/flowchart.png" alt-text="L’image montre l’organigramme, qui est décrit en détail dans le texte de l’article." border="true":::

Il y a six indicateurs de fin de l’organigramme, chacun décrivant une mesure à prendre :

|Indicateur de fin|Action(s)|
|---------|---------|
|![Indicateur de fin de l’organigramme 1.](media/common/icon-01-red-30x30.png)|Gérer la capacité<br />Mettre à l’échelle la capacité |
|![Indicateur de fin de l’organigramme 2.](media/common/icon-02-red-30x30.png)|Examiner l’activité de capacité pendant l’utilisation des rapports classiques|
|![Indicateur de fin de l’organigramme 3.](media/common/icon-03-red-30x30.png)|Modification de l’architecture<br />Tenir compte d’Azure Analysis Services<br />Vérifier la passerelle locale|
|![Indicateur de fin de l’organigramme 4.](media/common/icon-04-red-30x30.png)|Tenir compte d’Azure Analysis Services<br />Tenir compte de Power BI Premium|
|![Indicateur de fin de l’organigramme 5.](media/common/icon-05-red-30x30.png)|Utiliser l’analyseur de performances Power BI Desktop<br />Optimiser le rapport, le modèle ou DAX|
|![Indicateur de fin de l’organigramme 6.](media/common/icon-06-red-30x30.png)|Créer un ticket de support|

## <a name="take-action"></a>Effectuer une action

Il faut tout d’abord comprendre si le rapport lent est hébergé sur une capacité Premium.

### <a name="premium-capacity"></a>Capacité Premium

Lorsque le rapport est hébergé sur une capacité Premium, utilisez l’**application Power BI Premium Metrics** pour déterminer si la capacité d’hébergement de rapports dépasse souvent les ressources de capacité. C’est le cas pour l’UC si elle dépasse souvent 80 %. Pour la mémoire, c’est le cas lorsque la [métrique de mémoire active](../service-premium-metrics-app.md#the-active-memory-metric) dépasse 50. En cas de pression sur les ressources, il peut être temps de [gérer ou de mettre à l’échelle la capacité](../service-admin-premium-manage.md) (indicateur de fin de l’organigramme 1). Lorsqu’il existe des ressources adéquates, examinez l’activité de la capacité pendant l’utilisation des rapports classiques (indicateur de fin de l’organigramme 2).

### <a name="shared-capacity"></a>Capacité partagée

Lorsque le rapport est hébergé sur une capacité partagée, il n’est pas possible de surveiller l’intégrité de la capacité. Vous devez adopter une approche d’investigation différente.

Tout d’abord, déterminez si le ralentissement des performances se produit à des moments spécifiques du jour ou du mois. Si c’est le cas et que de nombreux utilisateurs ouvrent le rapport à ces moments, envisagez deux options :

- Augmentez le débit des requêtes en migrant le jeu de données vers [Azure Analysis Services](/azure/analysis-services/analysis-services-overview) ou vers une capacité Premium (indicateur de fin de l’organigramme 4).
- Utilisez l’[Analyseur de performances](../desktop-performance-analyzer.md) Power BI Desktop pour découvrir comment se comportent chacun des éléments de votre rapport, tels que les visuels et les formules DAX. Il est particulièrement utile de déterminer si les problèmes de performances sont dus à la requête ou au rendu visuel (indicateur de fin de l’organigramme 5).

S’il n’y a pas de modèle de temps, vérifiez ensuite si les performances lentes sont limitées à une zone géographique ou à une région spécifique. Si c’est le cas, il est probable que la source de données est distante et que la communication réseau est lente. Dans ce cas, prenez en compte les éléments suivants :

- Modification de l’architecture à l’aide d’[Azure Analysis Services](/azure/analysis-services/analysis-services-overview) (indicateur de fin d’organigramme 3).
- Optimisation des [performances de la passerelle de données locale](/data-integration/gateway/service-gateway-performance) (indicateur de fin d’organigramme 3).

Enfin, si vous constatez qu’il n’existe pas de modèle de temps _et_ que les performances sont lentes dans toutes les régions, vérifiez si les performances sont lentes sur des appareils, des clients ou des navigateurs web spécifiques. Si ce n’est pas le cas, utilisez l’[analyseur de performances Power BI Desktop](../desktop-performance-analyzer.md) comme décrit plus haut pour optimiser le rapport ou le modèle (indicateur de fin d’organigramme 5).

Lorsque vous constatez que des appareils, des clients ou des navigateurs web spécifiques contribuent au ralentissement des performances, nous vous recommandons de créer un ticket de support via la [page de support Power BI](https://powerbi.microsoft.com/support/) (indicateur de fin de l’organigramme 6).

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur cet article, consultez les ressources suivantes :

- [Conseils sur Power BI](index.yml)
- [Surveillance des performances des rapports](monitor-report-performance.md)
- [Analyseur de performances](../desktop-performance-analyzer.md)
- Livre blanc : [Planification d’un déploiement de Power BI en entreprise](https://go.microsoft.com/fwlink/?linkid=2057861)
- Vous avez des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
- Vous avez des suggestions ? [Envoyez-nous vos idées pour améliorer Power BI](https://ideas.powerbi.com/)
