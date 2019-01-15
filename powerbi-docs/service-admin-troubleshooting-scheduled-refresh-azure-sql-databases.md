---
title: Dépannage d’une actualisation planifiée pour Azure SQL Database
description: Dépannage d’une actualisation planifiée pour Azure SQL Database dans Power BI
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 12/06/2017
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 17ee932bf0331940c7b30b020ab8fc43cdc9fdf5
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/15/2019
ms.locfileid: "54274672"
---
# <a name="troubleshooting-scheduled-refresh-for-azure-sql-databases-in-power-bi"></a>Dépannage d’une actualisation planifiée pour Azure SQL Database dans Power BI
Pour obtenir des instructions détaillées sur la configuration d’une actualisation planifiée, consultez [Actualiser des données dans Power BI](refresh-data.md).

Pendant la configuration de l’actualisation planifiée d’Azure SQL Database, si vous obtenez une erreur avec le code d’erreur 400 pendant la modification des informations d’identification, essayez de procéder comme suit pour configurer la règle de pare-feu appropriée :

1. Connectez-vous à votre portail de gestion Azure.
2. Accédez au serveur SQL Azure pour lequel vous configurez l’actualisation.
3. Activez « Services Windows Azure » dans la section des services autorisés.

![Services Azure autorisés](media/service-admin-troubleshooting-scheduled-refresh-azure-sql-databases/azurerefresh.png)  

D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)

