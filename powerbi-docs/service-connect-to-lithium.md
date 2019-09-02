---
title: Se connecter à Lithium avec Power BI
description: Lithium pour Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: tebercov
LocalizationGroup: Connect to services
ms.openlocfilehash: c2f6564c83c7234b626686a6fe4c76f65b354e58
ms.sourcegitcommit: b53a6f5575f5f8bc443ecdca9c72525ce123518f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70185521"
---
# <a name="connect-to-lithium-with-power-bi"></a>Se connecter à Lithium avec Power BI

Lithium crée des relations de confiance entre les meilleures marques du monde et leurs clients, en aidant les personnes à obtenir des réponses et à partager leurs expériences. En connectant le pack de contenu Lithium à Power BI, vous pouvez obtenir des chiffres clés sur votre communauté en ligne qui vous aideront à dynamiser les ventes, à réduire les coûts de service et à fidéliser davantage. 

[!INCLUDE [include-short-name](./includes/service-deprecate-content-packs.md)]

Connectez-vous au [Pack de contenu Lithium](https://app.powerbi.com/getdata/services/lithium) pour Power BI.

>[!NOTE]
>Le pack de contenu Power BI utilise l’API Lithium. Des appels en trop grand nombre à l’API peuvent entraîner des frais supplémentaires au niveau de Lithium. Vérifiez avec votre administrateur Lithium.

## <a name="how-to-connect"></a>Comment se connecter
1. Sélectionnez **Obtenir des données** en bas du volet de navigation gauche.
   
   ![](media/service-connect-to-lithium/pbi_getdata.png) 
2. Dans la zone **Services** , sélectionnez **Obtenir**.
   
   ![](media/service-connect-to-lithium/pbi_getservices.png) 
3. Sélectionnez **Lithium** \> **Obtenir**.
   
   ![](media/service-connect-to-lithium/lithiumconnect.png)
4. Spécifiez l’URL de votre communauté Lithium. Le format de cette URL est *https://community.yoursite.com* .
   
   ![](media/service-connect-to-lithium/params.png)
5. Quand vous y êtes invité, entrez vos informations d’identification Lithium. Sélectionnez **oAuth 2** comme mécanisme d’authentification et cliquez sur **Se connecter** , puis suivez le flux d’authentification de Lithium.
   
   ![](media/service-connect-to-lithium/creds.png)
   
   ![](media/service-connect-to-lithium/creds2.png)
6. Une fois le flux de connexion terminé, le processus d’importation commence. Une fois terminé, de nouveaux tableau de bord, rapport et modèle apparaîtront dans le volet de navigation. Sélectionnez le tableau de bord pour afficher vos données importées.
   
    ![](media/service-connect-to-lithium/lithium.png)

**Et maintenant ?**

* Essayez de [poser une question dans la zone Q&R](consumer/end-user-q-and-a.md) en haut du tableau de bord.
* [Modifiez les vignettes](service-dashboard-edit-tile.md) dans le tableau de bord.
* [Sélectionnez une vignette](consumer/end-user-tiles.md) pour ouvrir le rapport sous-jacent.
* Même si une actualisation quotidienne de votre jeu de données est planifiée, vous pouvez modifier la planification de l’actualisation ou essayer d’actualiser le jeu de données sur demande à l’aide de l’option **Actualiser maintenant**.

## <a name="system-requirements"></a>Configuration requise
Le pack de contenu Lithium nécessite une communauté Lithium version 15.9 ou ultérieure. Contactez votre administrateur Lithium pour confirmer.

## <a name="next-steps"></a>Étapes suivantes
[Qu’est-ce que Power BI ?](power-bi-overview.md)

[Fondamentaux pour les concepteurs dans le service Power BI](service-basic-concepts.md)

