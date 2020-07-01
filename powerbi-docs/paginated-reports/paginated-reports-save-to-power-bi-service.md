---
title: Publier un rapport paginé dans le service Power BI
description: Dans ce tutoriel, vous apprendrez à publier un rapport paginé dans le service Power BI en le chargeant depuis votre ordinateur local.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: how-to
ms.date: 05/04/2020
ms.openlocfilehash: edda0fa0232430541af1fc1766fd5d8bc23c5e1c
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85221020"
---
# <a name="publish-a-paginated-report-to-the-power-bi-service"></a>Publier un rapport paginé dans le service Power BI

Dans cet article, vous apprendrez à publier un rapport paginé dans le service Power BI en le chargeant depuis votre ordinateur local. Vous pouvez charger des rapports paginés vers Mon espace de travail ou d’autres espaces de travail, tant que l’espace de travail figure dans une capacité Premium. Recherchez l’icône en forme de losange ![Icône en forme de losange pour la capacité Power BI Premium](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) en regard du nom de l'espace de travail. 

Si la source de données de votre rapport est locale, vous devez créer une passerelle après avoir chargé le rapport. Consultez la section [Créer une passerelle](#create-a-gateway) plus loin dans cet article.

## <a name="add-a-workspace-to-a-premium-capacity"></a>Ajouter un espace de travail à une capacité Premium

Si l’espace de travail n’affiche aucune icône en forme de losange ![Icône en forme de losange pour la capacité Power BI Premium](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) en regard du nom, vous devez ajouter l’espace de travail à une capacité Premium. 

1. Sélectionnez **Espaces de travail**, choisissez les points de suspension ( **…** ) en regard du nom de l’espace de travail, puis sélectionnez **Membres**.

    ![Sélectionner Modifier l’espace de travail](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-edit-workspace.png)

1. Dans la boîte de dialogue **Modifier l’espace de travail**, développez **Avancé**, puis basculez le commutateur **Capacité dédiée** sur **On**.

    ![Sélectionner une capacité dédiée](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-edit-workspace-dialog.png)

   Vous ne pourrez peut-être pas modifier cette option. Dans ce cas, contactez votre administrateur de capacité Power BI Premium afin qu’il vous donne des droits d’attribution pour ajouter votre espace de travail à une capacité Premium.

## <a name="from-report-builder-publish-a-paginated-report"></a>À partir de Report Builder, publier un rapport paginé

1. Créez votre rapport paginé dans le Générateur de rapports et enregistrez-le sur votre ordinateur local.

1. Dans le menu **Fichier** de Report Builder, sélectionnez **Enregistrer sous**.

    ![Menu Fichier> Enregistrer > Enregistrer sous](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-save-as.png)

    Si vous n’êtes pas encore connecté à Power BI, vous devez vous y connecter ou créer un compte dès maintenant. Dans l’angle supérieur droit de Report Builder, sélectionnez **Se connecter** et effectuez les étapes.

2. Dans la liste des espaces de travail à gauche, sélectionnez un espace de travail dont le nom est suivi de l’icône de diamant ![icône de diamant pour la capacité Power BI Premium](media/paginated-reports-save-to-power-bi-service/premium-diamond.png). Tapez un **nom de fichier** dans la zone > **Enregistrer**. 

    ![Sélectionner un espace de travail Premium](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-workspace.png)

4. Ouvrez le service Power BI dans un navigateur et accédez à l’espace de travail Premium dans lequel vous avez publié le rapport paginé. Sous l’onglet **Rapports**, vous voyez votre rapport.

    ![Rapport paginé dans la liste des rapports](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-wwi-report.png)

5. Sélectionnez le rapport paginé pour l’ouvrir dans le service Power BI. S’il possède des paramètres, vous devez les sélectionner avant de pouvoir afficher le rapport.

    ![Sélectionner les paramètres](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-parameters.png)

6. Si la source de données de votre rapport est locale, découvrez comment [créer une passerelle](#create-a-gateway) dans cet article pour accéder à la source de données.

## <a name="from-the-power-bi-service-upload-a-paginated-report"></a>À partir du service Power BI, charger un rapport paginé

Vous pouvez aussi charger un rapport paginé à partir du service Power BI.

1. Créez votre rapport paginé dans le Générateur de rapports et enregistrez-le sur votre ordinateur local.

1. Ouvrez le service Power BI dans un navigateur et accédez à l’espace de travail Premium où vous souhaitez publier le rapport. Notez l’icône en forme de losange ![Icône en forme de losange pour la capacité Power BI Premium](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) en regard du nom. 

1. Sélectionnez **Obtenir les données**.

    ![Obtenir les données Power BI](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-get-data.png)

1. Dans la zone **Fichiers** , sélectionnez **Obtenir**.

    ![Obtenir des fichiers Power BI](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-files-get.png)

1. Sélectionnez **Fichier local** > naviguez jusqu’au rapport paginé > **Ouvrir**.

    ![Sélectionner un fichier local](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-local-file.png)

1. Sélectionnez **Continuer** > **Modifier les informations d'identification**.

    ![Sélectionner Modifier les informations d’identification](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-edit-credentials.png)

1. Configurer vos informations d’identification > **Connexion**.

    ![Modifier les informations d’identification](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-credentials.png)

   Sous l’onglet **Rapports**, vous voyez votre rapport.

    ![Rapport paginé dans la liste des rapports](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-wwi-report.png)

1. Sélectionnez-le pour l’ouvrir dans le service Power BI. S’il possède des paramètres, vous devez les sélectionner avant de pouvoir afficher le rapport.
 
    ![Sélectionner les paramètres](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-parameters.png)

6. Si la source de données de votre rapport est locale, découvrez comment [créer une passerelle](#create-a-gateway) dans cet article pour accéder à la source de données.

## <a name="create-a-gateway"></a>Créer une passerelle

Comme tout autre rapport Power BI, si la source des données du rapport est locale, vous devez créer ou vous connecter à une passerelle pour accéder aux données.

1. En regard du nom du rapport, sélectionnez **Gérer**.

   ![Gérer le rapport paginé](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-manage.png)

1. Consultez l’article du service Power BI [Qu’est-ce qu’une passerelle de données locale ?](../connect-data/service-gateway-onprem.md) pour plus d’informations et connaître les prochaines étapes.



## <a name="next-steps"></a>Étapes suivantes

- [Afficher un rapport paginé dans le service Power BI](../consumer/paginated-reports-view-power-bi-service.md)
- [Présentation des rapports paginés dans Power BI Premium](paginated-reports-report-builder-power-bi.md)
- [Tutoriel : Incorporer des rapports paginés Power BI dans une application pour vos clients](../developer/embedded/embed-paginated-reports-customers.md)
