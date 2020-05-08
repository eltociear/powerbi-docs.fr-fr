---
title: Sources de données de rapport paginé dans Power BI Report Server
description: En savoir plus sur les sources de données auxquelles les rapports paginés (.rdl) peuvent se connecter dans Power BI Report Server.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 05/17/2018
ms.author: maggies
ms.openlocfilehash: 7cb5772e6ccdc1e4036d70f65a3a28210a4f6df1
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "78260712"
---
# <a name="paginated-report-data-sources--in-power-bi-report-server"></a>Sources de données de rapport paginé dans Power BI Report Server
Les rapports paginés Reporting Services dans Power BI Report Server prennent en charge les mêmes sources de données que celles prises en charge dans SQL Server Reporting Services. Consultez la liste [Sources de données prises en charge par Reporting Services](https://docs.microsoft.com/sql/reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs).

## <a name="connect-to-oracle-data-sources-with-useinstalleduiculture"></a>Se connecter à des sources de données Oracle data avec UseInstalledUICulture

Pour se connecter à des sources de données Oracle, Power BI Report Server utilise le fournisseur de données Oracle pour .NET (ODP.NET), qui est indépendant de NLS.

Par défaut, le serveur de rapports utilise la culture d’interface utilisateur du premier client pour charger ODP.NET.  Par conséquent, toutes les connexions suivantes à Oracle à partir du serveur de rapports seront dans cette culture d’interface utilisateur initiale jusqu’au redémarrage du service.  Cette approche peut causer des problèmes de rendu d’un rapport en raison d’incompatibilités dans la mise en forme de la culture d’interface utilisateur.

Pour offrir une meilleure expérience dans Power BI Report Server, nous avons introduit un paramètre de configuration nommé UseInstalledUICulture. Quand UseInstalledUICulture est défini sur true, le serveur de rapports charge toujours ODP.NET dans la culture d’interface utilisateur du serveur au lieu de la culture du premier client.
Ce paramètre est disponible dans Power BI Report Server à partir de la version du service publiée en février.

Pour activer la fonctionnalité, modifiez le fichier rsreportserver.config d’une entrée d’extension ORACLE comme indiqué ci-dessous.
```xml
<Extension Name="ORACLE" Type="Microsoft.ReportingServices.DataExtensions.OracleClientConnectionWrapper,Microsoft.ReportingServices.DataExtensions">
    <Configuration>
        <UseInstalledUICulture>true</UseInstalledUICulture>
    </Configuration>
</Extension>
```

## <a name="next-steps"></a>Étapes suivantes
Maintenant que vous vous êtes connecté à votre source de données, [créez un rapport paginé](quickstart-create-paginated-report.md).  


D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
