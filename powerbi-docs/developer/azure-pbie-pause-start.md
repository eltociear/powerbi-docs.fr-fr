---
title: Suspendre et démarrer une capacité Power BI Embedded dans le Portail Microsoft Azure | Microsoft Docs
description: Cet article explique pas à pas comment suspendre et démarrer une capacité Power BI Embedded dans Microsoft Azure.
services: power-bi-embedded
author: markingmyname
ms.author: maghan
manager: kfile
editor: ''
tags: ''
ms.service: power-bi-embedded
ms.topic: conceptual
ms.date: 09/28/2017
ms.openlocfilehash: 9f939c0eae4f7ea1f24eec473549dc00191f1b67
ms.sourcegitcommit: fecea174721d0eb4e1927c1116d2604a822e4090
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2018
ms.locfileid: "39360304"
---
# <a name="pause-and-start-your-power-bi-embedded-capacity-in-the-azure-portal"></a>Suspendre et démarrer une capacité Power BI Embedded dans le Portail Microsoft Azure

Cet article explique pas à pas comment suspendre et démarrer une capacité Power BI Embedded dans Microsoft Azure. Vous êtes censé avoir créé une capacité Power BI Embedded. Si ce n’est pas le cas, consultez [Créer une capacité Power BI Embedded dans le Portail Microsoft Azure](azure-pbie-create-capacity.md) pour commencer.

Si vous n’avez pas d’abonnement Azure, créez un [compte gratuit](https://azure.microsoft.com/free/) avant de commencer.

## <a name="pause-your-capacity"></a>Suspendre votre capacité

La suspension de votre capacité vous évite d’être facturé. Cela s’avère utile si vous n’avez pas besoin d’utiliser la capacité pendant un certain temps. Pour suspendre votre capacité, effectuez les étapes suivantes.

> [!NOTE]
> La suspension d’une capacité peut rendre le contenu indisponible dans Power BI. Pour éviter toute interruption, veillez à supprimer l’affectation d’espaces de travail dans votre capacité avant de procéder à la suspension.

1. Connectez-vous au [portail Azure](https://portal.azure.com/).

2. Sélectionnez **Tous les services** > **Power BI Embedded** pour voir vos capacités.

    ![Tous les services dans le Portail Microsoft Azure](media/azure-pbie-pause-start/azure-portal-more-services.png)

3. Sélectionnez la capacité que vous voulez suspendre.

    ![Liste des capacités Power BI Embedded dans le Portail Microsoft Azure](media/azure-pbie-pause-start/azure-portal-capacity-list.png)

4. Sélectionnez **Suspendre** dans les détails de la capacité.

    ![Suspendre votre capacité](media/azure-pbie-pause-start/azure-portal-pause-capacity.png)

5. Sélectionnez **Oui** pour confirmer votre volonté de suspendre la capacité.

    ![Confirmer la suspension](media/azure-pbie-pause-start/azure-portal-confirm-pause.png)

## <a name="start-your-capacity"></a>Démarrer votre capacité

Rétablissez l’utilisation en démarrant votre capacité. Le démarrage de la capacité rétablit aussi la facturation.

1. Connectez-vous au [portail Azure](https://portal.azure.com/).

2. Sélectionnez **Tous les services** > **Power BI Embedded** pour voir vos capacités.

    ![Tous les services dans le Portail Microsoft Azure](media/azure-pbie-pause-start/azure-portal-more-services.png)

3. Sélectionnez la capacité que vous voulez démarrer.

    ![Liste des capacités Power BI Embedded dans le Portail Microsoft Azure](media/azure-pbie-pause-start/azure-portal-capacity-list.png)

4. Sélectionnez **Démarrer** dans les détails de la capacité.

    ![Démarrer votre capacité](media/azure-pbie-pause-start/azure-portal-start-capacity.png)

5. Sélectionnez **Oui** pour confirmer votre volonté de démarrer la capacité.

    ![Confirmer le démarrage](media/azure-pbie-pause-start/azure-portal-confirm-start.png)

Si du contenu est affecté à cette capacité, il devient disponible une fois celle-ci démarrée.

## <a name="next-steps"></a>Étapes suivantes

Si vous souhaitez faire monter ou descendre en puissance votre capacité, consultez [Mettre à l'échelle votre capacité Power BI Embedded](azure-pbie-scale-capacity.md).

Pour commencer à incorporer du contenu Power BI dans votre application, consultez [Guide pratique pour incorporer vos tableaux de bord, rapports et vignettes Power BI](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding-content/).

D’autres questions ? [Essayez d’interroger la communauté Power BI](http://community.powerbi.com/)