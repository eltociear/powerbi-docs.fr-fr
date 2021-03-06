---
title: Partager un tableau de bord lié à un fichier Excel dans OneDrive - Power BI
description: Consultez les informations relatives au partage de tableaux de bord connectés à un classeur Excel sur OneDrive Entreprise, avec des vignettes épinglées de ce classeur.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 08/02/2018
LocalizationGroup: Share your work
ms.openlocfilehash: ee70a90ee104f1144595bd346b85d858f0aed49f
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96411583"
---
# <a name="share-a-power-bi-dashboard-that-links-to-an-excel-file-in-onedrive"></a>Partager un tableau de bord Power BI avec des liens vers un fichier Excel dans OneDrive
Dans Power BI, vous pouvez vous [connecter à des classeurs Excel sur OneDrive Entreprise](../connect-data/service-excel-workbook-files.md) et épingler des vignettes sur un tableau de bord à partir de ce classeur. Quand vous partagez ce tableau de bord, ou créez un pack de contenu qui l’inclut :

* Vos collègues peuvent afficher les vignettes sans avoir besoin d’autorisations pour le classeur lui-même. Ainsi, vous pouvez créer un pack de contenu en sachant que vos collègues peuvent afficher les vignettes créées à partir du classeur Excel sur OneDrive.
* Le fait de cliquer sur la vignette ouvre le classeur dans Power BI. Le classeur s’ouvre uniquement si vos collègues ont au moins des [autorisations de lecture](https://support.office.com/article/Share-documents-or-folders-in-Office-365-1fe37332-0f9a-4719-970e-d2578da4941c) sur le classeur sur OneDrive Entreprise.

## <a name="share-a-dashboard-that-contains-workbook-tiles"></a>Partager un tableau de bord contenant des vignettes de classeur
Pour partager un tableau de bord lié à un classeur Excel sur OneDrive Entreprise, consultez [Partager un tableau de bord](service-share-dashboards.md). La différence est que vous avez la possibilité de modifier les autorisations du classeur Excel lié avant de le partager.

  ![Boîte de dialogue Partager le tableau de bord](media/service-share-dashboard-that-links-to-excel-onedrive/pbi_share_workbk.png)

1. Entrez l’adresse de messagerie de vos collègues.
2. Pour autoriser vos collègues à afficher le classeur Excel dans Power BI, sélectionnez **Accéder à OneDrive Entreprise pour définir les autorisations du classeur**.
3. Sur OneDrive, [modifiez les autorisations](https://support.office.com/article/Share-files-and-folders-and-change-permissions-9fcc2f7d-de0c-4cec-93b0-a82024800c07) en fonction des besoins.
4. Sélectionnez **Partager**.

>[!NOTE]
>Vos collègues ne sont pas en mesure d’épingler des vignettes supplémentaires à partir de ce classeur, ni d’apporter des modifications au classeur Excel à partir de Power BI.
> 
> 

## <a name="create-an-organizational-content-pack-with-a-dashboard-that-contains-workbook-tiles"></a>Créer un pack de contenu d’organisation avec un tableau de bord contenant des vignettes de classeur
Quand vous [publiez un pack de contenu](service-organizational-content-pack-create-and-publish.md), vous autorisez l’accès à certains collègues ou groupes. Quand vous publiez un pack de contenu contenant des liens de classeur, vous pouvez modifier les autorisations du classeur Excel lié avant de le publier.

1. Dans l’écran **Créer un pack de contenu** , entrez les adresses e-mail, nommez et décrivez le pack de contenu et téléchargez une image.
2. Sélectionnez le tableau de bord et/ou le rapport lié au classeur Excel sur OneDrive Entreprise.
   
    ![Classeur Excel dans un pack de contenu](media/service-share-dashboard-that-links-to-excel-onedrive/pbi_contpack_workbk.png)
3. Sélectionnez **Accéder à OneDrive Entreprise pour définir les autorisations du classeur**.
4. Sur OneDrive, [modifiez les autorisations](https://support.office.com/article/Share-files-and-folders-and-change-permissions-9fcc2f7d-de0c-4cec-93b0-a82024800c07) en fonction des besoins.
5. Sélectionnez **Publier**.

## <a name="share-a-dashboard-from-a-power-bi-workspace"></a>Partager un tableau de bord à partir d’un espace de travail Power BI
Le partage d’un tableau de bord à partir d’un espace de travail Power BI est similaire au partage d’un tableau de bord à partir de votre propre espace de travail, sauf que les fichiers se trouvent dans un site d’espace de travail Microsoft 365, et non dans votre espace OneDrive Entreprise privé. Modifiez les autorisations du classeur Excel avant de partager le tableau de bord avec des personnes n’appartenant pas à l’espace de travail.

![Partager à partir de OneDrive](media/service-share-dashboard-that-links-to-excel-onedrive/pbi_onedriveshare.png)

## <a name="next-steps"></a>Étapes suivantes
* [Épingler une vignette à un tableau de bord Power BI à partir d’Excel](../create-reports/service-dashboard-pin-tile-from-excel.md)
* [Fondamentaux pour les concepteurs dans le service Power BI](../fundamentals/service-basic-concepts.md)
* D’autres questions ? [Posez vos questions à la communauté Power BI](https://community.powerbi.com/)
