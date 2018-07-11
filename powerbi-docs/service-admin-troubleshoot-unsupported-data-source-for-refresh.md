---
title: Résolution des problèmes liés à la non prise en charge d’une source de données pour l’actualisation
description: Résolution des problèmes liés à la non prise en charge d’une source de données pour l’actualisation
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 12/06/2017
ms.author: mblythe
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 864e7a3d78386f6996d866f45558add3b51faa69
ms.sourcegitcommit: ba447d7cc94418d7d3cf6fdcb686ec1a859258a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37145186"
---
# <a name="troubleshooting-unsupported-data-source-for-refresh"></a>Résolution des problèmes liés à la non prise en charge d’une source de données pour l’actualisation
Une erreur peut s’afficher lorsque vous tentez de configurer un jeu de données pour une actualisation planifiée.

        You cannot schedule refresh for this dataset because it gets data from sources that currently don’t support refresh.

Cela se produit quand la source de données que vous avez utilisée, dans Power BI Desktop, n’est pas prise en charge pour l’actualisation. Vous devez trouver la source de données utilisée et la comparer à la liste des sources de données prises en charge disponible dans la rubrique [Actualiser des données dans Power BI](refresh-data.md). 

## <a name="find-the-data-source"></a>Rechercher la source de données
Si vous ne savez pas quelle source de données a été utilisée, effectuez les étapes suivantes dans Power BI Desktop.  

1. Dans Power BI Desktop, vérifiez que vous êtes dans le volet **Rapport** .  
   ![](media/service-admin-troubleshoot-unsupported-data-source-for-refresh/tshoot-report-pane.png)
2. Sélectionnez **Modifier les requêtes** dans la barre du ruban.  
   ![](media/service-admin-troubleshoot-unsupported-data-source-for-refresh/tshoot-edit-queries.png)
3. Sélectionnez **Éditeur avancé**.  
   ![](media/service-admin-troubleshoot-unsupported-data-source-for-refresh/tshoot-advanced-editor.png)
4. Notez le fournisseur indiqué pour la source.  Dans cet exemple, le fournisseur est ActiveDirectory.  
   ![](media/service-admin-troubleshoot-unsupported-data-source-for-refresh/tshoot-provider.png)
5. Comparez le fournisseur à la liste des sources de données prises en charge disponible dans la rubrique [Actualiser des données dans Power BI](refresh-data.md).  Vous constaterez qu’Active Directory n’est pas une source de données prise en charge pour l’actualisation.  

## <a name="next-steps"></a>Étapes suivantes
[Actualisation des données](refresh-data.md)  
[Power BI Gateway - Personal](service-gateway-personal-mode.md)  
[Passerelle de données locale](service-gateway-onprem.md)  
[Résolution des problèmes de passerelle de données locale](service-gateway-onprem-tshoot.md)  
[Résolution des problèmes liés à Power BI Gateway - Personal](service-admin-troubleshooting-power-bi-personal-gateway.md)  

D’autres questions ? [Essayez d’interroger la communauté Power BI](http://community.powerbi.com/)

