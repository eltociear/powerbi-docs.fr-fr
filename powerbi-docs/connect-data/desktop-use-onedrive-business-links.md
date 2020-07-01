---
title: Utilisation des liens OneDrive Entreprise dans Power BI Desktop
description: Utilisation des liens OneDrive Entreprise dans Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 05/27/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 88aa1335433dba38e5f18ca7463077543db2c923
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85222460"
---
# <a name="use-onedrive-for-business-links-in-power-bi-desktop"></a>Utilisation des liens OneDrive Entreprise dans Power BI Desktop
De nombreux utilisateurs ont des classeurs Excel stockés dans OneDrive Entreprise qui pourraient parfaitement être utilisés avec Power BI Desktop. Avec Power BI Desktop, vous pouvez utiliser les liens en ligne pour les fichiers Excel stockés dans OneDrive Entreprise pour créer des rapports et des visuels. Vous pouvez utiliser un compte de groupe OneDrive Entreprise ou votre compte OneDrive Entreprise individuel.

L’obtention d’un lien en ligne de OneDrive Entreprise nécessite d’effectuer quelques étapes spécifiques. Les sections suivantes détaillent ces étapes, ce qui vous permet de partager le lien de fichier au sein des groupes, sur différentes machines, et avec vos collègues.

## <a name="get-a-link-from-excel"></a>Obtenir un lien d’Excel
1. Accédez à votre emplacement OneDrive Entreprise avec un navigateur. Faites un clic droit sur le fichier que vous souhaitez utiliser, puis sélectionnez **Ouvrir dans Excel**
   
   > [!NOTE]
   > L’interface de votre navigateur peut différer de celle de l’image. Il existe de nombreuses façons de sélectionner **Ouvrir dans Excel** pour les fichiers de l’interface de votre navigateur OneDrive Entreprise. Vous pouvez utiliser n’importe quelle option qui vous permet d’ouvrir le fichier dans Excel.
   
   ![](media/desktop-use-onedrive-business-links/odb-links_02.png)

2. Dans Excel, sélectionnez **Fichier** > **Informations**, puis sélectionnez le bouton **Copier le chemin d’accès**, comme illustré sur l’image suivante.
   
   ![](media/desktop-use-onedrive-business-links/onedrive-copy-path.png)

## <a name="use-the-link-in-power-bi-desktop"></a>Utiliser le lien dans Power BI Desktop
Dans Power BI Desktop, vous pouvez utiliser le lien que vous venez de copier dans le presse-papiers. Procédez comme suit :

1. Dans Power BI Desktop, sélectionnez **Obtenir des données** > **Web**.
   
   ![](media/desktop-use-onedrive-business-links/power-bi-web-link-onedrive.png)
2. L’option **De base** étant sélectionnée, collez le lien dans la boîte de dialogue **À partir du web**.
3. Supprimez la chaîne *?web=1* à la fin du lien afin que Power BI Desktop puisse accéder correctement à votre fichier, puis sélectionnez **OK**.
   
    ![](media/desktop-use-onedrive-business-links/power-bi-web-link-confirmation.png) 
4. Si Power BI Desktop vous demande des informations d’identification, choisissez **Windows** (pour les sites SharePoint locaux) ou **Compte professionnel** (pour les sites Microsoft 365 ou OneDrive Entreprise).
   
   ![](media/desktop-use-onedrive-business-links/odb-links_06.png)

   Une boîte de dialogue **Navigateur** s’affiche et vous permet d’effectuer une sélection dans la liste de tableaux, de feuilles et de plages du classeur Excel. Ensuite, vous pouvez utiliser le fichier OneDrive Entreprise comme n’importe quel autre fichier Excel. Vous pouvez créer des rapports et les utiliser dans des jeux de données comme vous le feriez avec n’importe quelle autre source de données.

> [!NOTE]
> Pour utiliser un fichier OneDrive Entreprise en tant que source de données dans le service Power BI, avec l’option d’**actualisation du service** activée pour ce fichier, veillez à sélectionner **OAuth2** comme **Méthode d’authentification** lors de la configuration de vos paramètres d’actualisation. Sinon, vous pouvez rencontrer une erreur (comme *Échec de la mise à jour des informations d’identification de la source de données*) quand vous tentez de vous connecter ou d’effectuer une actualisation. Si vous sélectionnez **OAuth2** comme méthode d’authentification, vous résolvez cette erreur d’informations d’identification.
> 
> 

