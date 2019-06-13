---
title: Se connecter aux journaux d’audit Azure avec Power BI
description: Journaux d’Audit Azure pour Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 02/06/2018
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 005913bc6af73f9b20db3cff7d12733f721eef3a
ms.sourcegitcommit: 762857c8ca09ce222cc3f8b006fa1b65d11e4ace
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66720588"
---
# <a name="connect-to-azure-audit-logs-with-power-bi"></a>Se connecter aux journaux d’audit Azure avec Power BI
Avec le pack de contenu Journaux d’audit Azure, vous pouvez analyser et visualiser les informations stockées dans les journaux d’audit. Power BI récupère vos données, génère un tableau de bord par défaut et crée des rapports basés sur ces données.

[Connectez-vous au pack de contenu des journaux d’audit Azure](https://app.powerbi.com/getdata/services/azure-audit-logs) ou obtenez davantage d’informations sur l’[intégration des journaux d’audit Azure](https://powerbi.microsoft.com/integrations/azure-audit-logs) avec Power BI.

## <a name="how-to-connect"></a>Comment se connecter
1. Sélectionnez **Obtenir des données** en bas du volet de navigation gauche.  
   
    ![](media/service-connect-to-azure-audit-logs/getdata.png)
2. Dans la zone **Services** , sélectionnez **Obtenir**.  
   
    ![](media/service-connect-to-azure-audit-logs/services.png) 
3. Sélectionnez **Journaux d’audit Azure** > **Obtenir**.  
   
   ![](media/service-connect-to-azure-audit-logs/azureauditlogs.png)
4. À l’invite, entrez votre **ID d’abonnement Azure**. Pour plus de détails sur la recherche de votre [ID d’abonnement](#FindingParams), voir plus bas.   
   
    ![](media/service-connect-to-azure-audit-logs/parameters.png)
5. Pour la **Méthode d’authentification**, sélectionnez **oAuth2** \> **Se connecter**.
   
    ![](media/service-connect-to-azure-audit-logs/creds.png)
6. Entrez vos informations d’identification de compte pour terminer le processus de connexion.
   
    ![](media/service-connect-to-azure-audit-logs/login.png)
7. Power BI récupère vos données Journaux d’audit Azure et crée un tableau de bord et un rapport prêts à l’emploi. 
   
    ![](media/service-connect-to-azure-audit-logs/dashboard.png)

**Et maintenant ?**

* Essayez de [poser une question dans la zone Q&R](consumer/end-user-q-and-a.md) en haut du tableau de bord.
* [Modifiez les vignettes](service-dashboard-edit-tile.md) dans le tableau de bord.
* [Sélectionnez une vignette](consumer/end-user-tiles.md) pour ouvrir le rapport sous-jacent.
* Même si une actualisation quotidienne de votre jeu de données est planifiée, vous pouvez modifier la planification de l’actualisation ou essayer d’actualiser le jeu de données sur demande à l’aide de l’option **Actualiser maintenant**.

## <a name="system-requirements"></a>Configuration requise
Le pack de contenu des journaux d’audit d’Azure nécessite l’accès aux journaux d’audit dans le portail Azure. Vous trouverez plus de détails [ici](/azure/azure-resource-manager/resource-group-audit/).

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Recherche de paramètres
Il existe deux moyens faciles de trouver votre ID d’abonnement.

1. Sur https://portal.azure.com -&gt; Parcourir -&gt; Abonnements - &gt; ID d’abonnement
2. Sur https://manage.windowsazure.com -&gt; Paramètres  -&gt; ID d’abonnement

Votre ID d’abonnement est une longue série de chiffres et de caractères, semblable à l’exemple à l’étape\#4 ci-dessus. 

## <a name="troubleshooting"></a>Résolution des problèmes
Si vous voyez une erreur d’informations d’identification ou une erreur liée à une tentative d’actualiser en raison d’informations d’identification non valides, essayez de supprimer toutes les instances du pack de contenu des journaux d’audit Azure et de vous reconnecter.

## <a name="next-steps"></a>Étapes suivantes
[Qu’est-ce que Power BI ?](power-bi-overview.md)  
[Fondamentaux pour les concepteurs dans le service Power BI](service-basic-concepts.md)  

