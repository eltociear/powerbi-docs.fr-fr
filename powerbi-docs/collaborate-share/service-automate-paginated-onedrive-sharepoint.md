---
title: Enregistrer un rapport paginé dans OneDrive Entreprise ou SharePoint Online
description: Dans cet article, vous allez utiliser Power Automate pour automatiser l’enregistrement d’un rapport paginé Power BI dans OneDrive Entreprise ou dans un dossier SharePoint Online.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 11/17/2020
ms.author: maggies
LocalizationGroup: Get started
ms.openlocfilehash: 67f49d19e3488b80a980719220fcc4715a6952e7
ms.sourcegitcommit: b2693047fce6a4e0c3ea07013404e99fc9cc1901
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94904963"
---
# <a name="save-a-paginated-report-to-onedrive-for-business-or-sharepoint-online"></a>Enregistrer un rapport paginé dans OneDrive Entreprise ou SharePoint Online

Avec [Power Automate](/power-automate/getting-started), vous pouvez automatiser l’exportation et la distribution des rapports paginés Power BI dans divers formats et scénarios pris en charge. Dans cet article, vous allez utiliser Power Automate pour automatiser l’enregistrement d’un rapport paginé Power BI dans OneDrive Entreprise ou dans un dossier SharePoint Online.

:::image type="content" source="media/service-automate-paginated-onedrive-sharepoint/paginated-onedrive-flow.png" alt-text="Capture d’écran du flux Power Automate pour enregistrer un rapport paginé dans OneDrive ou SharePoint Online":::

Vous recherchez d’autres modèles Power Automate pour les rapports paginés Power BI ? Consultez [Exporter des rapports paginés Power BI avec Power Automate](service-automate-paginated-integration.md). 

## <a name="prerequisites"></a>Prérequis  

Pour suivre la procédure, veillez à disposer des éléments suivants :

- Au minimum un espace de travail situé dans votre locataire Power BI et disposant d’une capacité réservée. La capacité en question peut correspondre à n’importe quelle référence SKU A4/P1 – A6/P3. En savoir plus sur les [capacités réservées dans Power BI Premium](../admin/service-premium-what-is.md).
- Un accès aux connecteurs standard dans Power Automate, qui sont fournis avec tous les abonnements Office 365.

## <a name="save-a-paginated-report-to-onedrive-for-business-or-a-sharepoint-online-folder"></a>Enregistrer un rapport paginé dans OneDrive Entreprise ou dans un dossier SharePoint Online 

Avec l’un de ces modèles, vous allez configurer les exportations récurrentes d’un rapport paginé dans un format souhaité vers OneDrive Entreprise ou un dossier SharePoint Online. S’il s’agit de la première fois que vous utilisez l’action d’exportation vers un fichier pour les rapports paginés dans Power Automate, consultez les prérequis avant de commencer. 

> [!NOTE]
> Les étapes et les images suivantes montrent comment configurer un flux à l’aide du modèle **Enregistrer un rapport paginé Power BI dans OneDrive Entreprise**. Suivez ces mêmes étapes pour créer un flux à l’aide du modèle **Enregistrer un rapport paginé Power BI dans un dossier SharePoint Online**. Lorsque vous sélectionnez l’emplacement vers lequel vous souhaitez exporter votre rapport paginé, sélectionnez un dossier SharePoint Online au lieu d’un dossier OneDrive Entreprise. 

1. Connectez-vous à Power Automate [flow.microsoft.com](https://flow.microsoft.com/). 
1. Sélectionnez **Modèles**, puis recherchez  **rapports paginés**. 

    :::image type="content" source="media/service-automate-paginated-integration/power-bi-paginate-automate.png" alt-text="Capture d’écran de modèles Power Automate pour les rapports paginés Power BI.":::

1. Sélectionnez **Enregistrer un rapport paginé Power BI dans OneDrive Entreprise** ou **Enregistrer un rapport paginé Power BI dans un dossier SharePoint Online**. Vérifiez que vous êtes connecté à Power BI, ainsi qu’à OneDrive Entreprise ou SharePoint Online.

    :::image type="content" source="media/service-automate-paginated-onedrive-sharepoint/onedrive-template-step1.png" alt-text="Capture d’écran de la sélection du modèle Power BI pour OneDrive Entreprise.":::
1. Sélectionnez **Continuer**.  


1. Pour définir la **Périodicité** de votre flux, sélectionnez une option dans **Fréquence** et entrez la valeur d’**intervalle** souhaitée.

    :::image type="content" source="media/service-automate-paginated-onedrive-sharepoint/onedrive-template-2-recurrence.png" alt-text="Sélection de la périodicité du flux.":::

1. (Facultatif) Sélectionnez **Afficher les options avancées** pour définir d’autres paramètres de **Périodicité**, comme **Fuseau horaire**, **Heure de début**, **Aux jours indiqués**, **Aux heures indiquées** et **Aux minutes indiquées**.  

    :::image type="content" source="media/service-automate-paginated-onedrive-sharepoint/onedrive-template-3-advanced-recurrence.png" alt-text="Périodicité dans les options avancées.":::

1. Dans la zone **Espace de travail**, sélectionnez un espace de travail situé dans une capacité réservée. Dans la zone **Rapport**, sélectionnez le rapport paginé que vous souhaitez exporter vers l’espace de travail sélectionné. Dans la zone **Format d’exportation**, sélectionnez le format d’exportation souhaité. Si vous le souhaitez, vous pouvez spécifier des paramètres pour le rapport paginé. Pour obtenir une description détaillée des paramètres, consultez la [référence sur le connecteur pour l’API REST Power BI](/connectors/powerbi/#export-to-file-for-paginated-reports).  

    :::image type="content" source="media/service-automate-paginated-onedrive-sharepoint/onedrive-template-4-export-format.png" alt-text="Sélection du rapport paginé, de l’espace de travail et du format d’exportation.":::

1. Dans **Chemin du dossier**, sélectionnez le dossier OneDrive Entreprise ou SharePoint Online vers lequel vous souhaitez exporter votre rapport paginé.

    :::image type="content" source="media/service-automate-paginated-onedrive-sharepoint/onedrive-template-5-create-file.png" alt-text="Sélection de la destination et création du fichier.":::

1. Power Automate génère automatiquement un **nom de fichier** et un **contenu de fichier**. Vous pouvez changer le nom du fichier, mais vous devez conserver le **contenu de fichier** généré automatiquement. 

1. Lorsque vous avez terminé, sélectionnez  **Étape suivante**  ou **Enregistrer**. Power Automate crée et évalue le flux, et vous informe s’il trouve des erreurs. 

1. En cas d’erreurs, sélectionnez  **Modifier le flux** pour les corriger. Sinon, vous pouvez sélectionner la flèche **Retour** pour afficher les détails du flux et pour exécuter le nouveau flux. 

    Lorsque vous exécutez le flux, Power Automate exporte un rapport paginé au format spécifié vers OneDrive Entreprise ou SharePoint Online.  

## <a name="next-steps"></a>Étapes suivantes

- [Exporter des rapports paginés Power BI avec Power Automate](service-automate-paginated-integration.md)
- [Bien démarrer avec Power Automate](/power-automate/getting-started/)
- D’autres questions ? [Posez vos questions à la communauté Power BI](https://community.powerbi.com/)
