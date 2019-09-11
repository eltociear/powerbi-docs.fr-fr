---
title: Sources de données prises en charge par DirectQuery dans Power BI
description: Obtenez la liste des sources de données pouvant utiliser DirectQuery.
author: davidiseminger
ms.author: davidi
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/04/2019
LocalizationGroup: Connect to data
ms.openlocfilehash: 59c55d2e9322b0b7d76a35f4eec0863efe4959e0
ms.sourcegitcommit: 09ee1b4697aad84d8f4c9421015d7e4dbd3cf25f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70302657"
---
# <a name="data-sources-supported-by-directquery-in-power-bi"></a>Sources de données prises en charge par DirectQuery dans Power BI

**Power BI Desktop** et le **service Power BI** possèdent de nombreuses sources de données auxquelles vous pouvez vous connecter pour accéder aux données. Cet article décrit quelles sources de données pour Power BI prennent en charge la méthode de connexion appelée **DirectQuery**. Pour plus d’informations sur DirectQuery, consultez [**DirectQuery dans Power BI**](desktop-directquery-about.md).

Les sources de données suivantes prennent en charge DirectQuery dans Power BI :

* Amazon Redshift
* AtScale (bêta)
* Azure Data Explorer
* Azure HDInsight Spark
* [Azure SQL Database](service-azure-sql-database-with-direct-connect.md)
* [Azure SQL Data Warehouse](service-azure-sql-data-warehouse-with-direct-connect.md)
* Denodo
* Google BigQuery
* HDInsight Interactive Query
* IBM DB2 (Microsoft Provider)
* IBM Netezza
* Impala (version 2.x)
* MarkLogic
* Oracle Database (version 12 et versions ultérieures)
* Oracle Essbase
* PostgreSQL
* Serveur d’applications SAP Business Warehouse
* Serveur de messages SAP Business Warehouse
* SAP HANA
* Snowflake
* Spark (version 0.9 et versions ultérieures)
* SQL Server
* Base de données Teradata
* Vertica

Les sources de données dont le nom est suivi de **(bêta)** ou de **(préversion)** peuvent être modifiées et ne sont pas prises en charge pour une utilisation en production. Elles peuvent aussi ne pas être prises en charge après la publication d’un rapport dans le **service Power BI**, ce qui signifie que l’ouverture d’un rapport publié ou l’exploration du jeu de données peut entraîner une erreur.

La seule différence entre les sources de données **(bêta)** et **(préversion)** est que les sources **(préversion)** doivent être activées en tant que fonctionnalité en préversion pour être disponibles. Pour activer un connecteur de données **(préversion)**  : dans **Power BI Desktop**, accédez à **Fichier > Options et paramètres > Options**, puis sélectionnez **Fonctionnalités en préversion**.

> [!NOTE]
> Les requêtes DirectQuery sur SQL Server nécessitent une authentification avec les informations d’identification de l’authentification Windows actuelles ou avec les informations d’identification de la base de données pour établir un accès. Les autres informations d’identification ne sont pas prises en charge.
>

## <a name="on-premises-gateway-requirements"></a>Exigences de passerelle locale
Le tableau suivant indique si une **passerelle de données locale** est nécessaire pour se connecter à la source de données spécifiée après la publication d’un rapport vers le **service Power BI**.

| Source | Passerelle obligatoire ? |
| --- | --- |
| Amazon Redshift |Non |
| Azure HDInsight Spark (bêta) |Non |
| Azure SQL Database |Non |
| Azure SQL Data Warehouse |Non |
| Google BigQuery |Non |
| IBM Netezza |Oui |
| IBM DB2 (IBM Provider) |Oui |
| IBM DB2 (Microsoft Provider) |Non |
| Base de données Informix IBM |Non |
| Impala (version 2.x) |Oui |
| MySQL |Oui |
| ODBC |Oui |
| Base de données Oracle |Oui |
| PostgreSQL |Oui |
| Serveur d’applications SAP Business Warehouse |Oui |
| Serveur de messages SAP Business Warehouse |Pas encore pris en charge dans le **service Power BI** |
| SAP HANA |Oui |
| Snowflake |Oui |
| Spark (bêta), version 0.9 et versions ultérieures |Oui |
| SQL Server |Oui |
| Sybase |Oui |
| Base de données Teradata |Oui |
| Vertica |Oui |


## <a name="single-sign-on-sso-for-directquery-sources"></a>Authentification unique (SSO) pour les sources DirectQuery

Quand l’option d’authentification unique est activée et que vos utilisateurs accèdent aux rapports basés sur la source de données, Power BI envoie leurs informations d’identification Azure AD dans les requêtes à la source de données sous-jacente. Ainsi, Power BI est en mesure de respecter les paramètres de sécurité qui sont configurés au niveau de la source de données.

L’option d’authentification unique prend effet sur tous les jeux de données qui utilisent cette source de données. Elle n’affecte pas la méthode d’authentification utilisée pour les scénarios d’importation. Les sources de données suivantes prennent en charge l’authentification unique pour les connexions via DirectQuery :

- Azure SQL Database
- Azure SQL Data Warehouse
- Impala
- SAP HANA
- SAP BW
- Spark
- SQL Server
- Teradata

> [!Note]
> L’authentification multifacteur Azure (MFA) n’est pas pris en charge. Les utilisateurs qui souhaitent utiliser l’authentification unique avec DirectQuery doivent être exemptés de l’authentification multifacteur (MFA).

## <a name="next-steps"></a>Étapes suivantes
Pour plus d’informations sur DirectQuery, consultez les ressources suivantes :

* [DirectQuery dans Power BI](desktop-directquery-about.md)
* [DirectQuery et SAP HANA](desktop-directquery-sap-hana.md)
* [DirectQuery et SAP BW](desktop-directquery-sap-bw.md)
* [Passerelle de données locale](service-gateway-onprem.md)

