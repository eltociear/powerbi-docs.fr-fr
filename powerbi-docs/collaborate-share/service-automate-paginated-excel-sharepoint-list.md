---
title: Exporter un rapport paginé pour chaque ligne d’un tableau Excel Online ou d’une liste SharePoint
description: Dans cet article, vous allez utiliser Power Automate afin d’automatiser l’exportation d’un rapport paginé pour chaque ligne d’un tableau Excel Online ou d’une liste SharePoint Online.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 11/17/2020
ms.author: maggies
LocalizationGroup: Get started
ms.openlocfilehash: acb90e65d63871925fe39c38d2141b85652fd68a
ms.sourcegitcommit: b2693047fce6a4e0c3ea07013404e99fc9cc1901
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94904953"
---
# <a name="export-a-paginated-report-for-each-row-in-an-excel-online-table-or-sharepoint-list"></a>Exporter un rapport paginé pour chaque ligne d’un tableau Excel Online ou d’une liste SharePoint

Avec [Power Automate](/power-automate/getting-started), vous pouvez automatiser l’exportation et la distribution des rapports paginés Power BI dans divers formats et scénarios pris en charge. Dans cet article, vous allez utiliser un modèle Power Automate pour automatiser l’exportation périodique d’un ou de plusieurs rapports paginés. Vous allez les exporter au format souhaité pour chaque ligne d’un tableau Excel Online ou d’une liste SharePoint Online. Vous pouvez distribuer le rapport paginé exporté vers OneDrive Entreprise ou un site SharePoint Online, ou l’envoyer par e-mail via Office 365 Outlook.

:::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-overview.png" alt-text="Exporter un rapport paginé à partir d’un tableau Excel Online.":::

Chaque ligne de votre tableau Excel Online ou de votre liste SharePoint Online peut correspondre à un utilisateur qui doit recevoir un rapport paginé sous la forme d’un abonnement. Chaque ligne peut également correspondre à un rapport paginé que vous souhaitez distribuer. Votre tableau ou votre liste nécessite une colonne qui indique comment distribuer un rapport, qu’il s’agisse de OneDrive, SharePoint Online ou Outlook. Le flux Power Automate utilise cette colonne dans son instruction switch.

Vous recherchez d’autres modèles Power Automate pour les rapports paginés Power BI ? Consultez [Exporter des rapports paginés Power BI avec Power Automate](service-automate-paginated-integration.md).

## <a name="prerequisites"></a>Prérequis  

Pour suivre la procédure, veillez à disposer des éléments suivants :

- Au minimum un espace de travail situé dans votre locataire Power BI et disposant d’une capacité réservée. La capacité en question peut correspondre à n’importe quelle référence SKU A4/P1 – A6/P3. En savoir plus sur les [capacités réservées dans Power BI Premium](../admin/service-premium-what-is.md).
- Un accès aux connecteurs standard dans Power Automate, qui sont fournis avec tous les abonnements Office 365.
- Si vous utilisez un tableau Excel Online, celui-ci doit être converti au format tableau dans Excel. Pour savoir comment procéder, consultez [Créer un tableau](https://support.microsoft.com/office/create-a-table-in-excel-bf0ce08b-d012-42ec-8ecf-a2259c9faf3f).

## <a name="export-a-paginated-report-for-each-row-in-a-table-or-list"></a>Exporter un rapport paginé pour chaque ligne d’un tableau ou d’une liste

> [!NOTE]
> Les étapes et les images suivantes montrent comment configurer un flux à l’aide du modèle **Exporter un rapport paginé Power BI pour chaque ligne d’un tableau Excel Online**. Vous pouvez suivre ces mêmes étapes pour créer un flux à l’aide du modèle **Exporter un rapport paginé Power BI pour les éléments d’une liste SharePoint Online**. Contrairement à un tableau Excel Online, une liste SharePoint Online contient des informations expliquant comment exporter le rapport paginé.  

1. Connectez-vous à Power Automate [flow.microsoft.com](https://flow.microsoft.com/). 
1. Sélectionnez **Modèles**, puis recherchez  **rapports paginés**. 

    :::image type="content" source="media/service-automate-paginated-integration/power-bi-paginate-automate.png" alt-text="Capture d’écran de modèles Power Automate pour les rapports paginés Power BI.":::

1. Sélectionnez le modèle **Exporter un rapport paginé Power BI pour chaque ligne d’un tableau Excel Online** ou **Exporter un rapport paginé Power BI pour les éléments d’une liste SharePoint Online**. Vérifiez que vous êtes connecté à Excel Online, Power BI, OneDrive Entreprise, SharePoint Online et Office 365 Outlook. Sélectionnez **Continuer**.  

   :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-excel-online-1.png" alt-text="Exporter un rapport paginé Power BI pour chaque ligne d’un tableau Excel Online.":::

1. Pour définir la **Périodicité** de votre flux, sélectionnez une option dans **Fréquence** et entrez la valeur d’**intervalle** souhaitée.

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-recurrence-2.png" alt-text="Sélectionnez une périodicité pour votre flux.":::

1. (Facultatif) Sélectionnez **Afficher les options avancées** pour définir d’autres paramètres de **Périodicité**, comme **Fuseau horaire**, **Heure de début**, **Aux jours indiqués**, **Aux heures indiquées** et **Aux minutes indiquées**.

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-advanced-recurrence-3.png" alt-text="Facultatif : sélectionnez des options de périodicité avancées.":::

1. Dans la zone **Emplacement**, sélectionnez OneDrive Entreprise ou le site SharePoint Online dans lequel vous avez enregistré votre tableau Excel Online ou votre liste SharePoint Online. Ensuite, sélectionnez **Bibliothèque de documents** dans la liste déroulante.

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-location-4.png" alt-text="Sélectionnez l’emplacement du tableau Excel Online.":::

1. Sélectionnez le fichier Excel Online ou la liste SharePoint Online dans la zone **Fichier**. Sélectionnez le nom du tableau ou de la liste dans la liste déroulante **Tableau**. 
 
    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-file-table-5.png" alt-text="Sélectionnez le fichier Excel Online et le nom du tableau.":::

    > [!TIP]
    > Pour savoir comment mettre en forme des données sous forme de tableau Excel, consultez [Créer un tableau](https://support.microsoft.com/office/create-a-table-in-excel-bf0ce08b-d012-42ec-8ecf-a2259c9faf3f). 

1. Initialisez une variable à utiliser pour le nom de fichier. Vous pouvez conserver ou modifier les valeurs par défaut **Nom** et **Valeur**, mais vous devez conserver le **Type** en tant que **Chaîne**.  

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-name-type-6.png" alt-text="Renseignez le nom et la valeur, mais gardez la valeur Chaîne pour le type.":::

1. Dans **Appliquer à chacun**, la zone **Sélectionner une sortie de l’étape précédente** est définie sur **Valeur** par défaut. Ce paramètre itère au sein des actions contenues dans **Appliquer à chacun** pour chaque ligne de votre tableau Excel Online ou de votre liste SharePoint Online.  

1. Dans la zone **Espace de travail**, sélectionnez un espace de travail situé dans une capacité dédiée. Dans la zone **Rapport**, sélectionnez le rapport paginé que vous souhaitez exporter vers l’espace de travail sélectionné. Si vous sélectionnez **Entrer une valeur personnalisée** dans la liste déroulante, vous pouvez définir **Espace de travail** et **Rapport** comme des colonnes de votre tableau Excel Online ou de votre liste SharePoint Online. Ces colonnes doivent contenir respectivement les ID d’espace de travail et les ID de rapport.  

1. Sélectionnez un **Format d’exportation** dans la liste déroulante ou définissez-le sur une colonne de votre tableau Excel Online qui contient les formats d’exportation souhaités, par exemple, PDF, DOCX ou PPTX. Si vous le souhaitez, vous pouvez spécifier des paramètres pour le rapport paginé. Pour obtenir une description détaillée des paramètres, consultez la [référence sur le connecteur pour l’API REST Power BI](/connectors/powerbi/#export-to-file-for-paginated-reports).

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-export-format-9.png" alt-text="Renseignez le champ Exporter vers un fichier pour les rapports paginés.":::

1. Dans la zone **Valeur**, entrez un nom pour le rapport paginé une fois celui-ci exporté. N’oubliez pas d’indiquer une extension de fichier. Vous pouvez la définir de manière statique, par exemple .pdf, .docx ou .pptx. Vous pouvez également la définir de façon dynamique en sélectionnant la colonne de votre tableau Excel correspondant au format d’exportation souhaité. 

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-output-value-10.png" alt-text="Sélectionnez le nom du rapport et une extension de fichier.":::

1. Dans l’action **Basculer**, renseignez le champ **On** (Si) en indiquant la colonne de votre tableau Excel Online qui correspond à la méthode de remise souhaitée : **OneDrive**, **SharePoint** ou **E-mail**. 

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-switch-11.png" alt-text="Sous Basculer, indiquez la colonne de votre tableau Excel Online dans la zone On (Si).":::

1. Dans **Cas**, **Cas 2** et **Cas 3**, entrez les valeurs présentes dans la colonne du tableau Excel Online que vous avez sélectionnée à l’étape précédente.  

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-case-1-2-3-12.png" alt-text="Entrez des valeurs pour Cas, Cas 2 et Cas 3.":::

1. Si vous enregistrez votre rapport paginé dans OneDrive, sélectionnez le **Chemin du dossier** où il doit être enregistré.  

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-case-onedrive-13.png" alt-text="Si vous enregistrez dans OneDrive.":::

1. Si vous enregistrez votre rapport paginé dans SharePoint Online, entrez l’**Adresse du site** et le **Chemin du dossier** où il doit être enregistré. 

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-case-sharepoint-14.png" alt-text="Si vous enregistrez votre rapport paginé dans SharePoint Online.":::

1. Si vous envoyez votre rapport paginé par e-mail via Outlook, renseignez les champs **À**, **Objet** et **Corps**. Ces champs peuvent comprendre du contenu statique ou du contenu dynamique issu de votre tableau Excel Online ou de votre liste SharePoint Online. Power Automate joint automatiquement votre rapport paginé à cet e-mail.  

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-case-email-15.png" alt-text="Si vous envoyez votre rapport paginé par e-mail via Outlook.":::

1. Lorsque vous avez terminé, sélectionnez  **Étape suivante**  ou **Enregistrer**. Power Automate crée et évalue le flux, et vous informe s’il trouve des erreurs. 

1. En cas d’erreurs, sélectionnez  **Modifier le flux** pour les corriger. Sinon, vous pouvez sélectionner la flèche **Retour** pour afficher les détails du flux et exécuter le nouveau flux. 


## <a name="next-steps"></a>Étapes suivantes

- [Exporter des rapports paginés Power BI avec Power Automate](service-automate-paginated-integration.md)
- [Bien démarrer avec Power Automate](/power-automate/getting-started/)
- D’autres questions ? [Posez vos questions à la communauté Power BI](https://community.powerbi.com/)

