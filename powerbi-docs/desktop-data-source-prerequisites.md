---
title: "Conditions préalables pour les sources de données Power BI"
description: "Conditions préalables de source de données Power BI"
services: powerbi
documentationcenter: 
author: davidiseminger
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
ms.date: 09/06/2017
ms.author: davidi
ms.openlocfilehash: 38a304fc3a8bc671baefeaef31d07ef576c0ad5a
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2017
---
# <a name="power-bi-data-source-prerequisites"></a>Conditions préalables pour les sources de données Power BI
Pour chaque fournisseur de données, Power BI prend en charge une version de fournisseur spécifique sur les objets. Pour plus d’informations sur les sources de données accessibles à Power BI, consultez [Sources de données](desktop-data-sources.md). Le tableau suivant décrit ces conditions.

| Sources de données | Fournisseur | Version minimale du fournisseur | Version minimale de la source de données | Objets de source de données pris en charge | Lien de téléchargement |
| --- | --- | --- | --- | --- | --- |
| SQL Server |ADO.net (intégré à .Net Framework) |.Net Framework 3.5 (uniquement) |SQL Server 2005+ |Tables/vues, fonctions scalaires, fonctions de table |Inclus dans .NET Framework 3.5 ou version ultérieure |
| Access |Moteur de base de données Microsoft Access (ACE) |ACE 2010 SP1 |Pas de restriction |Tables/vues |[Lien de téléchargement](http://go.microsoft.com/fwlink/?linkid=285987&clcid=0x409) |
| Excel (fichiers .xls uniquement) (voir remarque 1) |Moteur de base de données Microsoft Access (ACE) |ACE 2010 SP1 |Pas de restriction |Tables, feuilles |[Lien de téléchargement](http://go.microsoft.com/fwlink/?linkid=285987&clcid=0x409) |
| Oracle (voir remarque 2) |ODP.NET |ODAC 11.2 Release 5 (11.2.0.3.20) |9.x + |Tables/vues |[Lien de téléchargement](http://go.microsoft.com/fwlink/?linkid=272376&clcid=0x409) |
| System.Data.OracleClient (intégré dans .Net Framework) |.NET Framework 3.5 |9.x+ |Tables/vues |Inclus dans .NET Framework 3.5 ou version ultérieure | |
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

