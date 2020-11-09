---
title: Configurations matérielle et logicielle requises pour l’installation de Power BI Report Server
description: Cet article mentionne les configurations matérielle et logicielle requises pour installer et exécuter Power BI Report Server.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 10/29/2020
ms.openlocfilehash: 30e8f1cb1ef8f12d9573d77a70771eef915a2704
ms.sourcegitcommit: a5fa368abad54feb44a267fe26c383a731c7ec0d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93044798"
---
# <a name="hardware-and-software-requirements-for-installing-power-bi-report-server"></a>Configurations matérielle et logicielle requises pour l’installation de Power BI Report Server

Cet article mentionne les configurations matérielle et logicielle requises pour installer et exécuter Power BI Report Server.

## <a name="processor-memory-and-operating-system-requirements"></a>Processeur, mémoire et système d'exploitation requis

| Composant | Condition requise |
| --- | --- |
| .NET Framework |4.8<br><br>Vous pouvez installer manuellement le .NET Framework à partir de la page [Microsoft .NET Framework 4.8 (programme d’installation web) pour Windows](https://support.microsoft.com/en-us/help/4503548/).<br/><br/> Pour obtenir plus d’informations, des recommandations et des instructions sur .NET Framework 4.8, consultez le [guide de déploiement du .NET Framework pour les développeurs](/dotnet/framework/deployment/deployment-guide-for-developers).<br/><br/>Avant l’installation de .NET Framework 4.8, Windows 8.1 et Windows Server 2012 R2 nécessitent la [mise à jour KB2919355](https://support.microsoft.com/kb/2919355). |
| Disque dur |Power BI Report Server nécessite au minimum 1 Go d’espace disponible sur le disque dur.<br><br>Un espace supplémentaire est requis sur le serveur de base de données hébergeant la base de données du serveur de rapports. |
| Mémoire |**Minimum :** 1 GB<br/><br/> **Recommandé :** au moins 4 Go |
| Vitesse du processeur |**Minimum :** processeur x64, 1,4 GHz<br/><br/> **Recommandé :** 2.0 GHz ou plus rapide |
| Type de processeur |Processeur x64 : AMD Opteron, AMD Athlon 64, Intel Xeon avec prise en charge d’Intel EM64T, Intel Pentium IV avec prise en charge d’EM64T |
| Système d’exploitation |Windows Server 2019 Datacenter<br><br>Windows Server 2019 Standard<br><br>Windows Server 2016 Datacenter<br><br>Windows Server 2016 Standard<br><br>Windows 10 Famille<br><br>Windows 10 Professionnel<br><br>Windows 10 Entreprise<br> |

> [!NOTE]
> L’installation de Power BI Report Server est prise en charge uniquement sur des processeurs x64.


## <a name="database-server-version-requirements"></a>Conditions requises pour une version du serveur de bases de données

SQL Server est utilisé pour héberger les bases de données des serveurs de rapports. L’instance du moteur de base de données SQL Server peut être locale ou distante. Voici les versions prises en charge du moteur de base de données SQL Server qui peuvent être utilisées pour héberger les bases de données des serveurs de rapports :

* Azure SQL Managed Instance (Power BI Report Server, version de janvier 2020 ou ultérieure)
* SQL Server 2019
* SQL Server 2017
* SQL Server 2016
* SQL Server 2014
* SQL Server 2012

Lorsque vous créez la base de données du serveur de rapports sur un ordinateur distant, vous devez configurer la connexion pour utiliser un compte d’utilisateur de domaine ou un compte de service ayant accès au réseau. Si vous décidez d’utiliser une instance distante de SQL Server, choisissez attentivement quelles informations d’identification le serveur de rapports doit utiliser pour se connecter à l’instance SQL Server. Pour plus d’informations, consultez [Configurer la connexion de base de données d’un serveur de rapports](/sql/reporting-services/install-windows/configure-a-report-server-database-connection-ssrs-configuration-manager).

## <a name="considerations"></a>Considérations

Power BI Report Server installe les valeurs par défaut pour configurer les principaux paramètres requis pour rendre un serveur de rapports opérationnel. Elle comporte les impératifs suivants :

* Les langues prises en charge pour Power BI Report Server sont l’anglais, l’allemand, l’espagnol, le japonais, l’italien, le français, le russe, le chinois simplifié, le chinois traditionnel, le portugais (Brésil) et le coréen.
* Un moteur de base de données SQL Server doit être disponible après l’installation et avant de configurer la base de données pour le serveur de rapports. L’instance du moteur de base de données héberge la base de données du serveur de rapports que le Gestionnaire de configuration de Reporting Services doit créer. Le moteur de base de données n’est pas requis pour l’expérience d’installation réelle.
* [Fonctionnalités des services de rapports prises en charge par les éditions de SQL Server](/sql/reporting-services/reporting-services-features-supported-by-the-editions-of-sql-server-2016) met en avant les différences entre les éditions de SQL Server.
* Le compte d’utilisateur qui exécute l’installation doit être membre du groupe d’administrateurs local.
* Le compte d’utilisateur qui exécute le Gestionnaire de configuration de Reporting Services doit disposer d’autorisations d’accès et de création sur les bases de données de l’instance du moteur de base de données hébergeant les bases de données du serveur de rapports.
* Le programme d’installation doit pouvoir utiliser les valeurs par défaut pour réserver les URL donnant accès au serveur de rapports et au portail web. Ces valeurs sont le port 80, un caractère générique fort et les noms de répertoire virtuel au format **ReportServer** et **Reports**.

## <a name="read-only-domain-controller-rodc"></a>Contrôleur de domaine en lecture seule (RODC)

 Vous pouvez installer le serveur de rapports dans un environnement qui comporte un contrôleur de domaine en lecture seule (RODC). Reporting Services doit cependant pouvoir accéder à un contrôleur de domaine en lecture/écriture pour fonctionner correctement. Si Reporting Services n’a accès qu’à un RODC, vous risquez de rencontrer des erreurs lors de l’administration du service.

## <a name="power-bi-reports-and-analysis-services-live-connections"></a>Rapports Power BI et connexions actives Analysis Services

Vous pouvez utiliser une connexion active à des instances tabulaires ou multidimensionnelles. Pour fonctionner correctement, votre serveur Analysis Services doit être de la version et de l’édition appropriées.

| **Version du serveur** | **Référence (SKU) requise** |
| --- | --- |
| 2012 SP1 CU4 ou version ultérieure |Business Intelligence et Enterprise |
| 2014 |Business Intelligence et Enterprise |
| 2016 et versions ultérieures |Référence (SKU) standard ou version ultérieure |

## <a name="next-steps"></a>Étapes suivantes

[Présentation de Power BI Report Server](get-started.md)  
[Vue d’ensemble de l’administrateur](admin-handbook-overview.md)  
[Installer Power BI Report Server](install-report-server.md)  
[Télécharger le Générateur de rapports](https://www.microsoft.com/download/details.aspx?id=53613)  
[Télécharger SQL Server Data Tools (SSDT)](/sql/ssdt/download-sql-server-data-tools-ssdt)

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
