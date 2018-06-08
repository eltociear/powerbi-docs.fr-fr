---
title: Configurations matérielle et logicielle requises pour l’installation de Power BI Report Server
description: Vous trouverez ici les configurations matérielle et logicielle requises pour installer et exécuter Power BI Report Server.
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-report-server
ms.topic: conceptual
ms.date: 05/18/2018
ms.author: maghan
ms.openlocfilehash: 3b0e9c148b86d8bf762a31cca5c3421df454502d
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34481726"
---
# <a name="hardware-and-software-requirements-for-installing-power-bi-report-server"></a>Configurations matérielle et logicielle requises pour l’installation de Power BI Report Server
Vous trouverez ici les configurations matérielle et logicielle requises pour installer et exécuter Power BI Report Server.

## <a name="processor-memory-and-operating-system-requirements"></a>Configurations requises du processeur, de la mémoire et du système d’exploitation
| Composant | Configuration requise |
| --- | --- |
| .NET Framework |4.6<br><br>Vous pouvez installer manuellement .NET Framework à partir de la page [Microsoft .NET Framework 4.6 (programme d’installation Web) pour Windows](http://support.microsoft.com/kb/3045560).<br/><br/> Pour plus d’informations, des recommandations et des instructions concernant .NET Framework 4.6, voir [Guide de déploiement de .NET Framework pour les développeurs](http://msdn.microsoft.com/library/ee942965\(v=vs.110\).aspx).<br/><br/>Avant l’installation de .NET Framework 4.6, Windows 8.1 et Windows Server 2012 R2 nécessitent la [Mise à jour KB2919355](http://support.microsoft.com/kb/2919355). |
| Disque dur |Power BI Report Server nécessite au minimum 1 Go d’espace disponible sur le disque dur.<br><br>Un espace supplémentaire est requis sur le serveur de base de données hébergeant la base de données du serveur de rapports. |
| Mémoire |**Minimum :** 1 GB<br/><br/> **Recommandé :** au moins 4 Go |
| Vitesse du processeur |**Minimum :** processeur x64 : 1,4 GHz<br/><br/> **Recommandé :** processeur cadencé à 2,0 GHz ou plus |
| Type de processeur |Processeur x64 : AMD Opteron, AMD Athlon 64, Intel Xeon avec prise en charge d’Intel EM64T, Intel Pentium IV avec prise en charge d’EM64T |
| Système d’exploitation |Windows Server 2016 Datacenter<br><br>Windows Server 2016 Standard<br><br>Windows Server 2012 R2 Datacenter<br><br>Windows Server 2012 R2 Standard<br><br>Windows Server 2012 R2 Essentials<br><br>Windows Server 2012 R2 Foundation<br><br>Windows Server 2012 Datacenter<br><br>Windows Server 2012 Standard<br><br>Windows Server 2012 Essentials<br><br>Windows Server 2012 Foundation<br><br>Windows 10 Famille<br><br>Windows 10 Professionnel<br><br>Windows 10 Entreprise<br><br>Windows 8.1<br><br>Windows 8.1 Professionnel<br><br>Windows 8.1 Entreprise<br><br>Windows 8<br><br>Windows 8 Professionnel<br><br>Windows 8 Entreprise |

> [!NOTE]
> L’installation de Power BI Report Server est prise en charge uniquement sur des processeurs x64.
> 
> 

## <a name="database-server-version-requirements"></a>Exigences liées aux versions du serveur de base de données
SQL Server est utilisé pour héberger les bases de données des serveurs de rapports. L’instance du moteur de base de données SQL Server peut être locale ou distante. Voici les versions prises en charge du moteur de base de données SQL Server qui peuvent être utilisées pour héberger les bases de données des serveurs de rapports :

* SQL Server 2017
* SQL Server 2016
* SQL Server 2014
* SQL Server 2012
* SQL Server 2008 R2
* SQL Server 2008

La création de la base de données du serveur de rapports sur un ordinateur distant nécessite que vous configuriez la connexion pour que celle-ci utilise un compte d’utilisateur de domaine ou un compte de service qui a accès au réseau. Si vous décidez d’utiliser une instance distante de SQL Server, choisissez attentivement quelles informations d’identification le serveur de rapports doit utiliser pour se connecter à l’instance SQL Server. Pour plus d’informations, consultez [Configurer la connexion de base de données d’un serveur de rapports](https://docs.microsoft.com/sql/reporting-services/install-windows/configure-a-report-server-database-connection-ssrs-configuration-manager).

## <a name="considerations"></a>Considérations
Power BI Report Server installe les valeurs par défaut pour configurer les principaux paramètres requis pour rendre un serveur de rapports opérationnel. Les conditions requises sont les suivantes :

* Un moteur de base de données SQL Server doit être disponible après l’installation et avant de configurer la base de données pour le serveur de rapports. L’instance du moteur de base de données héberge la base de données du serveur de rapports que le Gestionnaire de configuration de Reporting Services doit créer. Le moteur de base de données n’est pas requis pour l’expérience d’installation réelle.
* Le compte d’utilisateur utilisé pour exécuter l’installation doit être membre du groupe Administrateurs local.
* Le compte d’utilisateur utilisé pour le Gestionnaire de configuration de Reporting Services doit disposer d’autorisations d’accès et de création sur les bases de données de l’instance du moteur de base de données hébergeant les bases de données du serveur de rapports.
* Le programme d’installation doit pouvoir utiliser les valeurs par défaut pour réserver les URL donnant accès au serveur de rapports et au portail web. Ces valeurs sont le port 80, un caractère générique fort et les noms de répertoire virtuel au format **ReportServer** et **Reports**.

## <a name="read-only-domain-controller-rodc"></a>Contrôleur de domaine en lecture seule (RODC)
 Si le serveur de rapports peut être installé dans un environnement disposant d’un contrôleur de domaine en lecture seule (RODC), pour fonctionner correctement, Reporting Services doit avoir accès à un contrôleur de domaine en lecture-écriture. Si Reporting Services a accès uniquement à un RODC, il se peut que vous rencontriez des erreurs lors de la tentative d’administrer le service.

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
[Installer le Générateur de rapports](https://docs.microsoft.com/sql/reporting-services/install-windows/install-report-builder)  
[Télécharger SQL Server Data Tools (SSDT)](http://go.microsoft.com/fwlink/?LinkID=616714)

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)

