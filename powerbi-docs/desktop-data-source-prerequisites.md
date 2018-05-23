---
title: Conditions préalables pour les sources de données Power BI
description: Conditions préalables de source de données Power BI
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 05/02/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: de694a7fb57b3466a9bd8282973d52584f664cb7
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
---
# <a name="power-bi-data-source-prerequisites"></a>Conditions préalables pour les sources de données Power BI
Pour chaque fournisseur de données, Power BI prend en charge une version de fournisseur spécifique sur les objets. Pour plus d’informations sur les sources de données accessibles à Power BI, consultez [Sources de données](desktop-data-sources.md). Le tableau suivant décrit ces conditions.

| Sources de données | Fournisseur | Version minimale du fournisseur | Version minimale de la source de données | Objets de source de données pris en charge | Lien de téléchargement |
| --- | --- | --- | --- | --- | --- |
| SQL Server |ADO.net (intégré à .Net Framework) |.NET Framework 3.5 (uniquement) |SQL Server 2005+ |Tables/vues, fonctions scalaires, fonctions de table |Inclus dans .NET Framework 3.5 ou version ultérieure |
| Access |Moteur de base de données Microsoft Access (ACE) |ACE 2010 SP1 |Pas de restriction |Tables/vues |[Lien de téléchargement](http://go.microsoft.com/fwlink/?linkid=285987&clcid=0x409) |
| Excel (fichiers .xls uniquement) (voir remarque 1) |Moteur de base de données Microsoft Access (ACE) |ACE 2010 SP1 |Pas de restriction |Tables, feuilles |[Lien de téléchargement](http://go.microsoft.com/fwlink/?linkid=285987&clcid=0x409) |
| Oracle (voir remarque 2) |ODP.NET |ODAC 11.2 Release 5 (11.2.0.3.20) |9.x + |Tables/vues |[Lien de téléchargement](http://go.microsoft.com/fwlink/?linkid=272376&clcid=0x409) |
| | System.Data.OracleClient (intégré dans .NET Framework) |.NET Framework 3.5 |9.x+ |Tables/vues |Inclus dans .NET Framework 3.5 ou version ultérieure |
| IBM DB2 |Client ADO.Net d’IBM (partie intégrante du package de pilotes de serveur de données IBM) |10.1 |9.1+ |Tables/vues |[Lien de téléchargement](http://go.microsoft.com/fwlink/?linkid=274911&clcid=0x409) |
| MySQL |Connector/Net |6.6.5 |5.1 |Tables/vues, fonctions scalaires |[Lien de téléchargement](http://go.microsoft.com/fwlink/?linkid=278885&clcid=0x409) |
| PostgreSQL |Fournisseur NPGSQL ADO.NET |2.0.12 |7.4 |Tables/vues |[Lien de téléchargement](http://go.microsoft.com/fwlink/?linkid=282716&clcid=0x409) |
| Teradata |Fournisseur de données .NET pour Teradata |14+ |12+ |Tables/vues |[Lien de téléchargement](http://go.microsoft.com/fwlink/?linkid=278886&clcid=0x409) |
| SAP Sybase SQL Anywhere |iAnywhere.Data.SQLAnywhere pour .NET 3.5 |16+ |16+ |Tables/vues |[Lien de téléchargement](http://go.microsoft.com/fwlink/?linkid=324846) |

>[!NOTE]
>Les fichiers Excel qui ont une extension .xlsx ne nécessitent pas l’installation d’un fournisseur distinct.

>[!NOTE]
>Les fournisseurs Oracle nécessitent aussi le logiciel client Oracle (version 8.1.7+).
> 
> 

