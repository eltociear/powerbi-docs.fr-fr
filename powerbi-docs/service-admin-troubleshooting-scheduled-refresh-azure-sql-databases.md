---
title: Dépannage d’une actualisation planifiée pour Azure SQL Database
description: Dépannage d’une actualisation planifiée pour Azure SQL Database dans Power BI
author: mgblythe
manager: kfile
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: troubleshooting
ms.date: 09/04/2019
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 6d71a1202ba996b70c7477a33ccab936bebbfc5e
ms.sourcegitcommit: e5cf19e16112c7dad1591c3b38d232267ffb3ae1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72542808"
---
# <a name="troubleshooting-scheduled-refresh-for-azure-sql-databases-in-power-bi"></a>Dépannage d’une actualisation planifiée pour Azure SQL Database dans Power BI

Pour plus d’informations sur l’actualisation, consultez [Actualiser des données dans Power BI](refresh-data.md) et [Configurer une actualisation planifiée](refresh-scheduled-refresh.md).

Pendant la configuration de l’actualisation planifiée pour une base de données Azure SQL, si vous obtenez une erreur avec le code d’erreur 400 pendant la modification des informations d’identification, essayez de procéder comme suit pour configurer la règle de pare-feu appropriée :

1. Connectez-vous au [portail Azure](https://portal.azure.com).

1. Accédez à la base de données Azure SQL pour laquelle vous configurez l’actualisation.

1. En haut du panneau **Vue d’ensemble**, sélectionnez **Définir le pare-feu du serveur**.

1. Dans le panneau **Paramètres de pare-feu**, vérifiez que l’option **Autoriser l’accès aux services Azure** a la valeur **ON** (Activé).

    ![Services Azure autorisés](media/service-admin-troubleshooting-scheduled-refresh-azure-sql-databases/azurerefresh.png)  

D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)
