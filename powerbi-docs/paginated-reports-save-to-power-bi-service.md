---
title: Publier un rapport paginé dans le service Power BI (préversion)
description: Dans ce tutoriel, vous apprendrez à publier un rapport paginé dans le service Power BI en le chargeant depuis votre ordinateur local.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 11/05/2018
ms.author: maggies
ms.openlocfilehash: e1d26271b557c0e2fbd20324ae6fb7630a459b03
ms.sourcegitcommit: 5e83fa6c93a0bc6599f76cc070fb0e5c1fce0082
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56216007"
---
# <a name="publish-a-paginated-report-to-the-power-bi-service-preview"></a>Publier un rapport paginé dans le service Power BI (préversion)

Dans cet article, vous apprendrez à publier un rapport paginé dans le service Power BI en le chargeant depuis votre ordinateur local. Vous pouvez charger des rapports paginés vers Mon espace de travail ou d’autres espaces de travail, tant que l’espace de travail figure dans une capacité Premium. Recherchez l’icône en forme de losange ![Icône en forme de losange pour la capacité Power BI Premium](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) en regard du nom de l'espace de travail. 

Si la source de données de votre rapport est locale, vous devez [créer une passerelle](#create-a-gateway-to-an-on-premises-data-source) après avoir chargé le rapport.

## <a name="add-a-workspace-to-a-premium-capacity"></a>Ajouter un espace de travail à une capacité Premium

Si l’espace de travail n’affiche aucune icône en forme de losange ![Icône en forme de losange pour la capacité Power BI Premium](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) en regard du nom, vous devez ajouter l’espace de travail à une capacité Premium. 

1. Sélectionnez **Espaces de travail**, choisissez les points de suspension (**…**) en regard du nom de l’espace de travail, puis sélectionnez **Membres**.

    ![Sélectionner Modifier l’espace de travail](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-edit-workspace.png)

1. Dans la boîte de dialogue **Modifier l’espace de travail**, développez **Avancé**, puis basculez le commutateur **Capacité dédiée** sur **On**.

    ![Sélectionner une capacité dédiée](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-edit-workspace-dialog.png)

   Vous ne pourrez peut-être pas modifier cette option. Dans ce cas, contactez votre administrateur de capacité Power BI Premium afin qu’il vous donne des droits d’attribution pour ajouter votre espace de travail à une capacité Premium.


## <a name="upload-a-paginated-report"></a>Charger un rapport paginé

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

   Votre rapport apparaît dans la liste des rapports.

    ![Rapport paginé dans la liste des rapports](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-wwi-report.png)

1. Sélectionnez-le pour l’ouvrir dans le service Power BI. S’il possède des paramètres, vous devez les sélectionner avant de pouvoir afficher le rapport.
 
    ![Sélectionner les paramètres](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-parameters.png)

## <a name="create-a-gateway"></a>Créer une passerelle

Comme tout autre rapport Power BI, si la source des données du rapport est locale, vous devez créer ou vous connecter à une passerelle pour accéder aux données.

1. En regard du nom du rapport, sélectionnez **Gérer**.

   ![Gérer le rapport paginé](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-manage.png)

1. Consultez l’article du service Power BI [Installer une passerelle](service-gateway-install.md) pour plus d’informations et connaître les prochaines étapes.

### <a name="gateway-limitations"></a>Limitations de la passerelle

Actuellement, les passerelles ne prennent pas en charge les paramètres à valeurs multiples.


## <a name="next-steps"></a>Étapes suivantes

- [Afficher un rapport paginé dans le service Power BI](paginated-reports-view-power-bi-service.md)
- [Présentation des rapports paginés dans Power BI Premium (préversion)](paginated-reports-report-builder-power-bi.md)

