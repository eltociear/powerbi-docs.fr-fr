---
title: Vue d’ensemble de l’administration, Power BI Report Server
description: Cet article fournit une vue d’ensemble de l’administration de Power BI Report Server, un emplacement local destiné au stockage et à la gestion de vos rapports Power BI, mobiles et paginés.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 05/22/2019
ms.openlocfilehash: a1c8e11fbf3b157a0d9fc1a897347875b82226fa
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96387255"
---
# <a name="admin-overview-power-bi-report-server"></a>Vue d’ensemble de l’administration, Power BI Report Server
Cet article fournit une vue d’ensemble de l’administration de Power BI Report Server, un emplacement local destiné au stockage et à la gestion de vos rapports Power BI, mobiles et paginés. Cet article présente les concepts permettant de planifier, déployer et gérer Power BI Report Server, avec des liens vers plus d’informations.

![Capture d’écran de Power BI Report Server montrant les options de connexion.](media/admin-handbook-overview/admin-handbook.png)
 
## <a name="installing-and-migration"></a>Installation et migration
Vous devez installer Power BI Report Server pour pouvoir commencer à l’utiliser. Des articles existent qui expliquent comment gérer cette tâche.

Avant de d’installer, de mettre à niveau ou de migrer vers Power BI Report Server, examinez la [configuration système requise](system-requirements.md) pour le serveur de rapports.

### <a name="installing"></a>Installing
Si vous déployez un nouveau Power BI Report Server, le document suivant peut vous aider. 

[Installer Power BI Report Server](install-report-server.md)

### <a name="migration"></a>Migration
Il n’existe pas de mise à niveau sur place pour SQL Server Reporting Services. Si vous disposez d’une instance de SQL Server Reporting Services existante que vous voulez changer en Power BI Report Server, vous devez la migrer. Vous pouvez effectuer une migration pour d’autres raisons. Pour plus de détails, voir le document relatif à la migration.

[Migrer une installation de serveur de rapports](migrate-report-server.md)

## <a name="configuring-your-report-server"></a>Configuration de votre serveur de rapports
Lors de la configuration de votre serveur de rapports, vous disposez de nombreuses options. Allez-vous utiliser SSL ? Configurez-vous un serveur de courrier ? Souhaitez-vous une intégration avec le service Power BI pour pouvoir épingler des visualisations ?

L’essentiel de la configuration doit s’effectuer dans le Gestionnaire de configuration du serveur de rapports. Pour plus de détails, voir la documentation du [Gestionnaire de configuration](/sql/reporting-services/install-windows/reporting-services-configuration-manager-native-mode).

## <a name="security"></a>Sécurité
La sécurité et la protection sont importantes pour toute organisation. Pour découvrir l’authentification, l’autorisation, les rôles et les permissions, consultez la documentation relative à la [sécurité](/sql/reporting-services/security/reporting-services-security-and-protection).

## <a name="next-steps"></a>Étapes suivantes
[Installer Power BI Report Server](install-report-server.md)  
[Trouver la clé de produit de votre serveur de rapports](find-product-key.md)  
[Installer Power BI Desktop optimisé pour Power BI Report Server](install-powerbi-desktop.md)  
[Télécharger le Générateur de rapports](https://www.microsoft.com/download/details.aspx?id=53613)  
[Télécharger SQL Server Data Tools (SSDT)](/sql/ssdt/download-sql-server-data-tools-ssdt)

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)