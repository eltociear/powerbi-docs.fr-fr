---
title: "Sources de données prises en charge par DirectQuery dans Power BI"
description: "Obtenez la liste des sources de données pouvant utiliser DirectQuery."
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
ms.date: 01/24/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 3630d876f3e32cbe981d7fb5bcc38d9da1a257f2
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/24/2018
---
# <a name="data-sources-supported-by-directquery-in-power-bi"></a>Sources de données prises en charge par DirectQuery dans Power BI
**Power BI Desktop** et le **service Power BI** possèdent de nombreuses sources de données auxquelles vous pouvez vous connecter pour accéder aux données. Cet article décrit quelles sources de données pour Power BI prennent en charge la méthode de connexion appelée **DirectQuery**. Pour plus d’informations sur DirectQuery, consultez [**DirectQuery dans Power BI**](desktop-directquery-about.md).

Les sources de données suivantes prennent en charge DirectQuery dans Power BI :

* Amazon Redshift
* Azure HDInsight Spark (bêta)
* Azure SQL Database
* Azure SQL Data Warehouse
* Google BigQuery (bêta)
* IBM Netezza (bêta)
* Impala (version 2.x)
* Oracle Database (version 12 et versions ultérieures)
* SAP Business Warehouse (bêta)
* SAP HANA
* Snowflake
* Spark (bêta) (version 0.9 et versions ultérieures)
* SQL Server
* Base de données Teradata
* Vertica (bêta)

Les sources de données dont le nom est suivi de **(bêta)** ou **(préversion)** peuvent être modifiées et ne sont pas prises en charge pour la production. Elles peuvent également ne pas être prises en charge après la publication d’un rapport vers le **service Power BI**, ce qui signifie que l’ouverture d’un rapport publié ou l’exploration du jeu de données peut entraîner une erreur.

La seule différence entre les sources de données **(bêta)** et **(préversion)** est que les sources **(préversion)** doivent être activées en tant que fonctionnalité en préversion pour être disponibles. Pour activer un connecteur de données **(préversion)** : dans **Power BI Desktop**, accédez à **Fichier > Options et paramètres**, puis à **Paramètres > Options > Fonctionnalités en préversion**.

## <a name="on-premises-gateway-requirements"></a>Exigences de passerelle locale
Le tableau suivant indique si une **passerelle de données locale** est nécessaire pour se connecter à la source de données spécifiée après la publication d’un rapport vers le **service Power BI**.

| Source | Passerelle obligatoire ? |
| --- | --- |
| SQL Server |Oui |
| Azure SQL Database |Non |
| Azure SQL Data Warehouse |Non |
| SAP HANA |Oui |
| Base de données Oracle |Oui |
| Base de données Teradata |Oui |
| Amazon Redshift |Non |
| Impala (version 2.x) |Oui |
| Snowflake (préversion) |Pas encore pris en charge dans le **service Power BI** |
| Spark (bêta), version 0.9 et versions ultérieures |Pas encore pris en charge dans le **service Power BI** |
| Azure HDInsight Spark (bêta) |Pas encore pris en charge dans le **service Power BI** |
| IBM Netezza (bêta) |Pas encore pris en charge dans le **service Power BI** |
| SAP Business Warehouse (bêta) |Pas encore pris en charge dans le **service Power BI** |

## <a name="next-steps"></a>Étapes suivantes
Pour plus d’informations sur DirectQuery, consultez les ressources suivantes :

* [DirectQuery dans Power BI](desktop-directquery-about.md)
* [DirectQuery et SAP HANA](desktop-directquery-sap-hana.md)
* [DirectQuery et SAP BW](desktop-directquery-sap-bw.md)
* [Passerelle de données locale](service-gateway-onprem.md)

