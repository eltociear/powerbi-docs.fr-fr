---
title: Mettre à l'échelle votre capacité Power BI Embedded | Microsoft Docs
description: Cet article explique pas à pas comment mettre à l’échelle une capacité Power BI Embedded dans Microsoft Azure.
author: KesemSharabi
ms.author: kesharab
services: power-bi-embedded
editor: ''
tags: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.date: 01/31/2019
ms.openlocfilehash: 0b44c9326b11491e5b9f42b4110da482f52b58dc
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96417264"
---
# <a name="scale-your-power-bi-embedded-capacity-in-the-azure-portal"></a>Mettre à l’échelle une capacité Power BI Embedded dans le Portail Microsoft Azure

Cet article explique pas à pas comment mettre à l’échelle une capacité Power BI Embedded dans Microsoft Azure. La mise à l’échelle vous permet d’accroître ou de diminuer la taille de votre capacité.

Cela suppose que vous avez créé une capacité Power BI Embedded. Si ce n’est pas le cas, consultez [Créer une capacité Power BI Embedded dans le Portail Microsoft Azure](azure-pbie-create-capacity.md) pour commencer.

> [!NOTE]
> La durée d’une opération de mise à l’échelle est d’environ une minute. Pendant ce temps, la capacité n’est pas disponible. Le chargement du contenu incorporé peut échouer.

## <a name="scale-a-capacity"></a>Mettre à l’échelle une capacité

1. Connectez-vous au [portail Azure](https://portal.azure.com/).

2. Sélectionnez **Tous les services** > **Power BI Embedded** pour voir vos capacités.

    ![Tous les services dans le Portail Microsoft Azure](media/azure-pbie-scale-capacity/azure-portal-more-services.png)

3. Sélectionnez la capacité que vous voulez mettre à l’échelle.

    ![Liste des capacités Power BI Embedded dans le Portail Microsoft Azure](media/azure-pbie-scale-capacity/azure-portal-capacity-list.png)

4. Sélectionnez **Niveau tarifaire** sous **Mettre à l’échelle** au sein de votre capacité.

    ![Option Niveau tarifaire sous Mettre à l’échelle](media/azure-pbie-scale-capacity/azure-portal-scale-pricing-tier.png)

    Votre niveau tarifaire actuel présente un contour bleu.

    ![Niveau tarifaire actuel avec un contour bleu](media/azure-pbie-scale-capacity/azure-portal-current-tier.png)

5. Pour monter ou descendre en puissance, sélectionnez le niveau souhaité. Le nouveau niveau sélectionné présente un contour bleu en pointillés. Sélectionnez **Sélectionner** pour passer au nouveau niveau.

    ![Sélectionner le nouveau niveau](media/azure-pbie-scale-capacity/azure-portal-select-new-tier.png)

    La mise à l’échelle de votre capacité peut prendre entre une et deux minutes.

6. Confirmez votre niveau en affichant l’onglet vue d’ensemble. Le niveau tarifaire actuel est répertorié.

    ![Confirmer le niveau actuel](media/azure-pbie-scale-capacity/azure-portal-confirm-tier.png)

## <a name="next-steps"></a>Étapes suivantes

Pour suspendre ou démarrer votre capacité, consultez [Suspendre et démarrer une capacité Power BI Embedded dans le Portail Microsoft Azure](azure-pbie-pause-start.md).

Pour commencer à incorporer du contenu Power BI dans votre application, consultez [Guide pratique pour incorporer vos tableaux de bord, rapports et vignettes Power BI](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding-content/).

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
