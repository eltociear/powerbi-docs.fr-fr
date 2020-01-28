---
title: Comparer Power BI Report Server et le service Power BI
description: Cet article compare les fonctionnalités de Power BI Report Server et du service Power BI.
keywords: ''
author: maggiesMSFT
ms.author: maggies
ms.topic: overview
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.custom: mvc
ms.date: 01/16/2020
ms.openlocfilehash: f7f163a8930d8bd90d6270f59e8afa602e89dd57
ms.sourcegitcommit: 3d6b27e3936e451339d8c11e9af1a72c725a5668
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76160831"
---
# <a name="comparing-power-bi-report-server-and-the-power-bi-service"></a>Comparer Power BI Report Server et le service Power BI

Power BI Report Server et le service Power BI ont de nombreuses similitudes et quelques différences clés. Ce tableau détaille ces différents éléments.

## <a name="features-of-power-bi-report-server-and-the-power-bi-service"></a>Fonctionnalités de Power BI Report Server et du service Power BI

| Fonctionnalités | Power BI Report Server | Service Power BI | Notes |
|---------|---------|---------|---------|
| Déploiement | Local ou hébergé dans le cloud | Cloud | Power BI Report Server peut être déployé sur des machines virtuelles Azure (hébergées dans le cloud) si vous disposez d’une licence Power BI Premium |
| Données source | Cloud et/ou local | Cloud et/ou local |  |
| Licence | Power BI Premium ou SQL Server EE avec la Software Assurance (SA) | Power BI Pro et/ou Power BI Premium | |  
| Cycle de vie | Stratégie de cycle de vie moderne | Service entièrement géré |  |
| Cycle de mise en production | Trois fois par an (janvier, mai, septembre) | Une fois par mois | Les derniers correctifs et fonctionnalités sont d’abord disponibles pour le service Power BI. La plupart des fonctionnalités de base sont intégrées à Power BI Report Server dans les prochaines versions, et certaines fonctionnalités sont uniquement destinées au service Power BI. |
| Créer des rapports Power BI dans Power BI Desktop | Oui | Oui |  |
| Créer des rapports Power BI dans le navigateur | Non | Oui |  |
| Héberger des jeux de données partagés Power BI et s’y connecter | Non | Oui | [Introduction aux jeux de données entre plusieurs espaces de travail](../service-datasets-across-workspaces.md) |
| Passerelle obligatoire | Non | Oui, pour les sources de données locales |  |
| Streaming en temps réel | Non | Oui | [Streaming en temps réel dans Power BI](../service-real-time-streaming.md) |
| Tableaux de bord | Non | Oui | [Tableaux de bord dans le service Power BI](../consumer/end-user-dashboards.md) |
| Distribuer un groupe de rapports à l’aide d’applications | Non | Oui | [Créer et publier des applications avec des tableaux de bord et des rapports](../service-create-distribute-apps.md) |
| Packs de contenu | Non | Oui | [Packs de contenu d’organisation : Introduction](../service-organizational-content-pack-introduction.md) |
| Se connecter à des services comme Salesforce | Oui | Oui | [Se connecter aux services que vous utilisez](../service-connect-to-services.md) avec des packs de contenu dans le service Power BI. Dans Power BI Report Server, utilisez des connecteurs certifiés pour vous connecter à des services. Pour plus d’informations, consultez [Sources de données de rapport Power BI dans Power BI Report Server](data-sources.md). |
| Questions et réponses | Non | Oui | [Questions et réponses dans Power BI Desktop et le service Power BI](../power-bi-tutorial-q-and-a.md) 
| Informations rapides | Non | Oui | [Générer automatiquement des informations sur les données avec Power BI](../consumer/end-user-insights.md) |
| Analyser dans Excel | Non | Oui | [Analyser dans Excel](../service-analyze-in-excel.md) 
| Rapports paginés | Oui | Oui | [Les rapports paginés sont disponibles dans le service Power BI](../paginated-reports-report-builder-power-bi.md) en préversion dans une capacité Premium |
| Applications mobiles Power BI | Oui | Oui | [Vue d’ensemble des applications mobiles Power BI](../consumer/mobile/mobile-apps-for-mobile-devices.md) |
| Cartes ArcGIS | Non | Oui | [Cartes ArcGIS dans le service Power BI et Power BI Desktop par ESRI](../visuals/power-bi-visualization-arcgis.md) |
| Abonnements par courrier électronique pour les rapports Power BI | Non | Oui | [Vous abonner vous-même ou abonner d’autres utilisateurs](../service-report-subscribe.md) à un rapport ou à un tableau de bord dans le service Power BI |
| Abonnements par courrier électronique pour les rapports paginés | Oui | Oui | [Vous abonner vous-même et d’autres utilisateurs à des rapports paginés dans le service Power BI](../consumer/paginated-reports-subscriptions.md)<br><br>[Distribution des e-mails dans Reporting Services](https://docs.microsoft.com/sql/reporting-services/subscriptions/e-mail-delivery-in-reporting-services)  |
| Alertes de données | Non | Oui | [Alertes de données](../service-set-data-alerts.md) dans le service Power BI
| Sécurité au niveau des lignes (RLS) | Oui | Oui | Disponible dans DirectQuery (source de données) et en mode d’importation <br><br>Sécurité au niveau des lignes dans le [service Power BI](../service-admin-rls.md) <br><br>Sécurité au niveau des lignes dans [Power BI Report Server](row-level-security-report-server.md) |
| Mode plein écran | Non | Oui | [Mode plein écran](../consumer/end-user-focus.md) dans le service Power BI |
| Collaboration Office 365 avancée | Non | Oui | [Collaborer dans un espace de travail](../service-collaborate-power-bi-workspace.md) avec Office 365 |
| Visuels R | Non | Oui | [Créer des visuels R](../desktop-r-visuals.md) dans Power BI Desktop et publiez-les sur le service Power BI. Vous ne pouvez pas enregistrer les rapports Power BI avec des visuels R dans Power BI Report Server.  |
| Fonctionnalités en préversion | Non | Oui | [Accéder aux fonctionnalités en préversion du service Power BI](../consumer/end-user-preview-features.md) |
| Visuels personnalisés | Oui | Oui | [Éléments visuels personnalisés dans Power BI](../developer/power-bi-custom-visuals.md) |
| Modèles composites | Non | Oui |
| Power BI Desktop | Version optimisée pour Report Server, disponible en téléchargement avec Report Server | Version optimisée pour le service Power BI, disponible sur le Windows Store | [Power BI Desktop pour Report Server](https://powerbi.microsoft.com/report-server/) <br><br> [Power BI Desktop pour le service Power BI](https://aka.ms/pbidesktopstore) |

## <a name="next-steps"></a>Étapes suivantes

[Installer Power BI Report Server](install-report-server.md)
