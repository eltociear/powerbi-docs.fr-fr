---
title: Redémarrer une capacité Power BI Premium
description: Découvrez comment redémarrer une capacité Power BI Premium pour résoudre des problèmes de performance.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-premium
ms.topic: how-to
ms.date: 11/11/2020
LocalizationGroup: Premium
ms.openlocfilehash: 367195e0e09bbfb7de20acfa71b8da9742664ca2
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96413561"
---
# <a name="restart-a-power-bi-premium-capacity"></a>Redémarrer une capacité Power BI Premium

En tant qu’un administrateur Power BI, vous pouvez avoir besoin de redémarrer une capacité Premium. Cet article explique comment redémarrer une capacité et répond à plusieurs questions sur les performances et le redémarrage.

## <a name="why-does-power-bi-provide-this-option"></a>Pourquoi cette option est-elle fournie par Power BI ?

Power BI offre aux utilisateurs la possibilité d’effectuer des analyses complexes sur des quantités gigantesques de données. Malheureusement, ces utilisateurs peuvent provoquer des problèmes de performance en surchargeant le service Power BI avec des travaux, en écrivant des requêtes trop complexes, en créant des références circulaires, etc.

La capacité partagée de Power BI assure une certaine protection contre de telles situations en imposant des limites sur les tailles de fichiers, les planifications d’actualisation et d’autres aspects du service. En revanche, dans une capacité Power BI Premium, la plupart de ces limites sont augmentées. Par conséquent, un seul rapport contenant une expression DAX incorrecte ou un modèle très complexe peut entraîner d’importants problèmes de performance. Lors de son traitement, le rapport peut consommer toutes les ressources disponibles sur la capacité. 

Power BI s’améliore constamment dans la manière de protéger les utilisateurs de la capacité Premium contre ces problèmes. Nous mettons également à la disposition des administrateurs les outils nécessaires pour analyser à quels moments et pourquoi les capacités sont surchargées. Pour plus d’informations, consultez notre [session de formation courte](https://www.youtube.com/watch?v=UgsjMbhi_Bk&feature=youtu.be) et notre [session de formation longue](https://powerbi.tips/2018/07/). En même temps, vous avez besoin d’être en mesure d’atténuer ces problèmes majeurs dès qu’ils se produisent. Le moyen le plus rapide pour cela consiste à redémarrer la capacité.

> [!NOTE]
> Une nouvelle version de Power BI Premium a récemment été publiée. Celle-ci, appelée **Premium Gen2**, est actuellement en préversion. Les capacités de Gen2 en préversion ne nécessitant pas de redémarrages, cette fonctionnalité n’est pas disponible dans Premium Gen2.

## <a name="is-the-restart-process-safe-will-i-lose-any-data"></a>Le processus de redémarrage est-il sûr ? Vais-je perdre des données ?

Tous les tableaux de bord, rapports, données, définitions qui sont enregistrés sur votre capacité sont totalement intacts après un redémarrage. Lorsque vous redémarrez une capacité, les actualisations planifiées et ad hoc en cours sont arrêtées temporairement par le moteur d’actualisation, dans la plupart des cas, puis redémarrent dû à la logique de nouvelle tentative générée dans Power BI. Le service tente d’effectuer à nouveau les actualisations impactées une fois que la capacité est disponible. L’état des actualisations peut ne pas être modifié dans l’interface utilisateur pendant le processus de redémarrage. 

Les utilisateurs qui interagissent avec la capacité perdent le travail non enregistré pendant un processus de redémarrage. Il est donc préférable que les utilisateurs actualisent leurs navigateurs une fois le redémarrage terminé.

## <a name="how-do-i-restart-a-capacity"></a>Comment redémarrer une capacité ?

Suivez ces étapes pour redémarrer une capacité.

1. Dans le portail d’administration Power BI, sous l’onglet **Paramètres de capacité**, accédez à votre capacité. 

1. Ajouter **CapacityRestart**, *l’indicateur de caractéristique*, à votre URL de capacité : `https://app.powerbi.com/admin-portal/capacities/<YourCapacityId>?capacityRestartButton=true`.

1. Sous **Paramètres avancés** > **Redémarrage de la capacité**, sélectionnez **Redémarrer la capacité**.

    ![Redémarrer la capacité](media/service-admin-premium-restart/restart-capacity.png)

1. Dans la boîte de dialogue **Redémarrage de la capacité**, sélectionnez **Oui, redémarrer la capacité**.

    ![Confirmer le redémarrage](media/service-admin-premium-restart/confirm-restart.png)

## <a name="how-can-i-prevent-issues-from-happening-in-the-future"></a>Comment empêcher d’autres problèmes à l’avenir ?

La meilleure façon d’éviter ces problèmes consiste à former les utilisateurs à une modélisation efficace des données. Pour plus d’informations, consultez notre [session de formation](https://powerbi.tips/2018/07/).

Nous vous recommandons également de [superviser vos capacités](service-admin-premium-monitor-capacity.md) régulièrement afin de rechercher d’éventuelles tendances indiquant des problèmes sous-jacents. Nous prévoyons des versions régulières de l’application de supervision et d’autres outils afin de vous permettre de superviser et gérer vos capacités plus efficacement.

## <a name="next-steps"></a>Étapes suivantes

[Qu’est-ce que Power BI Premium ?](service-premium-what-is.md)

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
