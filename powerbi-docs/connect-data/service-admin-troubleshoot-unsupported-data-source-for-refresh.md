---
title: Résolution des problèmes liés à la non prise en charge d’une source de données pour l’actualisation
description: Résolution des problèmes liés à la non prise en charge d’une source de données pour l’actualisation
author: davidiseminger
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: troubleshooting
ms.date: 05/08/2020
ms.author: davidi
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 49af2febbecb5061c4acb9ee20c3b707e3b81dff
ms.sourcegitcommit: be424c5b9659c96fc40bfbfbf04332b739063f9c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91634892"
---
# <a name="troubleshooting-unsupported-data-source-for-refresh"></a>Résolution des problèmes liés à la non prise en charge d’une source de données pour l’actualisation
Une erreur peut s’afficher lorsque vous tentez de configurer un jeu de données pour une actualisation planifiée.

```output
You cannot schedule refresh for this dataset because it gets data from sources that currently don’t support refresh.
```

Cela se produit quand la source de données que vous avez utilisée, dans Power BI Desktop, n’est pas prise en charge pour l’actualisation. Vous devez trouver la source de données utilisée et la comparer à la liste des sources de données prises en charge disponible dans la rubrique [Actualiser des données dans Power BI](refresh-data.md). 

## <a name="find-the-data-source"></a>Rechercher la source de données
Si vous ne savez pas quelle source de données a été utilisée, effectuez les étapes suivantes dans Power BI Desktop.  

1. Dans Power BI Desktop, vérifiez que vous êtes dans le volet **Rapport** .  
   ![Volet Rapport Desktop](media/service-admin-troubleshoot-unsupported-data-source-for-refresh/tshoot-report-pane.png)
2. Sélectionnez **Modifier les requêtes** dans la barre du ruban.  
   ![Modifier les requêtes](media/service-admin-troubleshoot-unsupported-data-source-for-refresh/tshoot-edit-queries.png)
3. Sélectionnez **Éditeur avancé**.  
   ![Éditeur avancé](media/service-admin-troubleshoot-unsupported-data-source-for-refresh/tshoot-advanced-editor.png)
4. Notez le fournisseur indiqué pour la source.  Dans cet exemple, le fournisseur est ActiveDirectory.  
   ![Fournisseur de source de données](media/service-admin-troubleshoot-unsupported-data-source-for-refresh/tshoot-provider.png)
5. Comparez le fournisseur à la liste des sources de données prises en charge disponible dans [Sources de données Power BI](power-bi-data-sources.md).

> [!NOTE]
> Pour plus d’informations sur les problèmes d’actualisation liés aux sources de données dynamiques, y compris les sources de données qui incluent des requêtes créées manuellement, consultez [Actualisation et sources de données dynamiques](refresh-data.md#refresh-and-dynamic-data-sources).


## <a name="next-steps"></a>Étapes suivantes
[Actualisation des données](refresh-data.md)  
[Power BI Gateway - Personal](service-gateway-personal-mode.md)  
[On-premises data gateway (Passerelle de données locale)](service-gateway-onprem.md)  
[Résolution des problèmes de passerelle de données locale](service-gateway-onprem-tshoot.md)  
[Résolution des problèmes liés à Power BI Gateway - Personal](service-admin-troubleshooting-power-bi-personal-gateway.md)  

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
