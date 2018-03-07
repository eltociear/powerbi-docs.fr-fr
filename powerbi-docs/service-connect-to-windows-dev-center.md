---
title: "Se connecter au Centre de développement Windows avec Power BI"
description: "Centre de développement Windows pour Power BI"
services: powerbi
documentationcenter: 
author: SarinaJoan
manager: kfile
backup: maggiesMSFT
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 246c1dc22d120ac01fe5276bbd0a2dd95b0dbc1f
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/24/2018
---
# <a name="connect-to-windows-dev-center-with-power-bi"></a>Se connecter au Centre de développement Windows avec Power BI
Explorez et étudiez les données d’analyse d’application du Centre de développement Windows dans Power BI avec le pack de contenu Power BI. Les données sont actualisées automatiquement une fois par jour.

Connectez-vous au [pack de contenu du Centre de développement Windows](https://app.powerbi.com/getdata/services/devcenter) pour Power BI.

## <a name="how-to-connect"></a>Comment se connecter
1. Sélectionnez **Obtenir des données** en bas du volet de navigation gauche.
   
   ![](media/service-connect-to-windows-dev-center/getdata.png)
2. Dans la zone **Services** , sélectionnez **Obtenir**.
   
   ![](media/service-connect-to-windows-dev-center/services.png)
3. Sélectionnez **Centre de développement Windows** \>  **Obtenir**.
   
   ![](media/service-connect-to-windows-dev-center/windowsdev.png)
4. Entrez l’ID d’application d’une application que vous possédez et cliquez sur Suivant. Voir les détails sur la [recherche de ces paramètres](#FindingParams) ci-dessous.
   
   ![](media/service-connect-to-windows-dev-center/params.png)
5. Pour la **Méthode d’authentification**, sélectionnez **oAuth2** \> **Se connecter**. Quand vous y êtes invité, entrez les informations d’identification Azure Active Directory associées à votre compte du Centre de développement Windows (pour plus d’informations, consultez [Configuration requise](#Requirements)).
   
    ![](media/service-connect-to-windows-dev-center/creds.png)
   
    ![](media/service-connect-to-windows-dev-center/creds2.png)
6. Après l’approbation, le processus d’importation démarre automatiquement. Une fois terminé, de nouveaux tableau de bord, rapport et modèle apparaîtront dans le volet de navigation. Sélectionnez le tableau de bord pour afficher vos données importées et choisissez une vignette pour accéder aux rapports sous-jacents.
   
    ![](media/service-connect-to-windows-dev-center/dashboard.png)
   
    ![](media/service-connect-to-windows-dev-center/report.png)

**Et maintenant ?**

* Essayez de [poser une question dans la zone Q&R](power-bi-q-and-a.md) en haut du tableau de bord.
* [Modifiez les vignettes](service-dashboard-edit-tile.md) dans le tableau de bord.
* [Sélectionnez une vignette](service-dashboard-tiles.md) pour ouvrir le rapport sous-jacent.
* Même si une actualisation quotidienne de votre jeu de données est planifiée, vous pouvez modifier la planification de l’actualisation ou essayer d’actualiser le jeu de données sur demande à l’aide de l’option **Actualiser maintenant**.

## <a name="whats-included"></a>Ce qui est inclus
Le pack de contenu Power BI du Centre de développement inclut les données d’analyse de votre application et les acquisitions de produits in-app, les évaluations, les avis et l’intégrité de l’application. Les données sont limitées aux 3 derniers mois. et est une plage dynamique, ce qui signifie que les dates incluses sont mises à jour à mesure que le jeu de données est actualisé.

<a name="Requirements"></a>

## <a name="system-requirements"></a>Configuration requise
Ce pack de contenu nécessite la publication d’au moins une application dans le Windows Store, ainsi qu’un compte du Centre de développement Windows (plus de détails [ici](https://msdn.microsoft.com/windows/uwp/publish/manage-account-users)).

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Recherche de paramètres
L’ID de l’application est disponible sur la page Identité des applications, dans la section Gestion des applications.

L’ID de l’application se trouve à la fin de votre URL pour Windows 10 Store, https://www.microsoft.com/store/apps/ **{Id_application}**

## <a name="next-steps"></a>Étapes suivantes
[Prise en main de Power BI](service-get-started.md)

[Obtenir des données dans Power BI](service-get-data.md)

