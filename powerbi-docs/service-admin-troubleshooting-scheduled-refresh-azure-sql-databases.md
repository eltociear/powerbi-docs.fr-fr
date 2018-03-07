---
title: "Dépannage d’une actualisation planifiée pour Azure SQL Database"
description: "Dépannage d’une actualisation planifiée pour Azure SQL Database dans Power BI"
services: powerbi
documentationcenter: 
author: markingmyname
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/06/2017
ms.author: davidi
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 5f699ed013f35edd4f958b3c958e56ebeb05029c
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/24/2018
---
# <a name="troubleshooting-scheduled-refresh-for-azure-sql-databases-in-power-bi"></a>Dépannage d’une actualisation planifiée pour Azure SQL Database dans Power BI
Pour obtenir des instructions détaillées sur la configuration d’une actualisation planifiée, consultez [Actualiser des données dans Power BI](refresh-data.md).

Pendant la configuration de l’actualisation planifiée d’Azure SQL Database, si vous obtenez une erreur avec le code d’erreur 400 pendant la modification des informations d’identification, essayez de procéder comme suit pour configurer la règle de pare-feu appropriée :

1. Connectez-vous à votre portail de gestion Azure.
2. Accédez au serveur SQL Azure pour lequel vous configurez l’actualisation.
3. Activez « Services Windows Azure » dans la section des services autorisés.

![](media/service-admin-troubleshooting-scheduled-refresh-azure-sql-databases/azurerefresh.png)  

D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)

