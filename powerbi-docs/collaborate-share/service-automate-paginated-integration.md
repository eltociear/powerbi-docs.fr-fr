---
title: Exporter des rapports paginés avec Power Automate
description: Découvrez comment créer des flux Power Automate pour exporter des rapports paginés Power BI.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 11/17/2020
ms.author: maggies
LocalizationGroup: Get started
ms.openlocfilehash: 7cc3969b735c64de39ac41fdc6acf2152c4cda35
ms.sourcegitcommit: 8afdd3601209636c9ab92d75f967d4ee0a2cab26
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2020
ms.locfileid: "95011941"
---
# <a name="export-power-bi-paginated-reports-with-power-automate"></a>Exporter des rapports paginés Power BI avec Power Automate

Avec [Power Automate](/power-automate/getting-started), vous pouvez automatiser l’exportation et la distribution des rapports paginés Power BI dans divers formats et scénarios pris en charge. Dans cet article, vous allez découvrir les modèles à utiliser pour créer vos propres flux en vue d’exporter vos rapports paginés.  

## <a name="prerequisites"></a>Prérequis  

Pour suivre la procédure, veillez à disposer des éléments suivants :

- Au minimum un espace de travail situé dans votre locataire Power BI et disposant d’une capacité réservée. La capacité en question peut correspondre à n’importe quelle référence SKU A4/P1 – A6/P3. En savoir plus sur les [capacités réservées dans Power BI Premium](../admin/service-premium-what-is.md).
- Un accès aux connecteurs standard dans Power Automate, qui sont fournis avec tous les abonnements Office 365.

## <a name="create-a-flow-from-a-template"></a>Créer un flux à partir d’un modèle 

1. Connectez-vous à Power Automate [flow.microsoft.com](https://flow.microsoft.com/). 
1. Sélectionnez **Modèles**, puis recherchez  **rapports paginés**. 

    :::image type="content" source="media/service-automate-paginated-integration/power-bi-paginate-automate.png" alt-text="Capture d’écran de modèles Power Automate pour les rapports paginés Power BI.":::

## <a name="select-a-template"></a>Sélectionner un modèle 

Sélectionnez un modèle dans la liste pour utiliser une procédure pas à pas.  

- [Enregistrez un rapport paginé Power BI dans OneDrive Entreprise ou dans un dossier SharePoint Online](service-automate-paginated-onedrive-sharepoint.md).  
- [Exportez un rapport paginé Power BI pour les éléments d’une liste SharePoint Online ou pour chaque ligne d’un tableau Excel Online.](service-automate-paginated-excel-sharepoint-list.md)
- Enregistrez un rapport paginé Power BI dans un dossier système local.

## <a name="next-steps"></a>Étapes suivantes

- [API d’exportation des rapports paginés Power BI](../developer/embedded/export-paginated-report.md)
- [Bien démarrer avec Power Automate](/power-automate/getting-started/)
- D’autres questions ? [Posez vos questions à la communauté Power BI](https://community.powerbi.com/)
