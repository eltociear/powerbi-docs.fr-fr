---
title: Comparer Power BI Report Server et le service Power BI
description: Cet article compare les fonctionnalités de Power BI Report Server et du service Power BI.
services: powerbi
keywords: ''
author: maggiesMSFT
ms.author: maggies
ms.component: powerbi-report-server
ms.date: 05/07/2018
ms.topic: overview
ms.service: powerbi
manager: kfile
ms.custom: mvc
ms.openlocfilehash: d0a3e2870edc8b18cb982c33582c7578aa67f2c3
ms.sourcegitcommit: 493f160d04ed411ff4741c599adc63ba1f65230f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33813895"
---
# <a name="comparing-power-bi-report-server-and-the-power-bi-service"></a>Comparer Power BI Report Server et le service Power BI

Power BI Report Server et le service Power BI partagent de nombreuses similitudes et quelques différences clés. Ce tableau détaille ces différents éléments.

| Fonctionnalités | Power BI Report Server | Service Power BI | Notes
|---------|---------|---------|---------|
| Déploiement | Local ou hébergé dans le cloud | Cloud | Power BI Report Server peut être déployé sur des machines virtuelles Azure (hébergées dans le cloud) si vous disposez d’une licence Power BI Premium
| Données source | Cloud et/ou local | Cloud et/ou local |  
| Licence | Power BI Premium ou SQL Server EE avec SA | Power BI Pro et/ou Power BI Premium |  
| Cycle de vie | Stratégie de cycle de vie moderne | Service entièrement géré |  
| Cycle de mise en production | Tous les 4 mois | Une fois par mois | Les derniers correctifs et fonctionnalités sont d’abord disponibles pour le service Power BI. La plupart des fonctionnalités de base sont intégrées à Power BI Report Server dans les prochaines versions, et certaines fonctionnalités sont uniquement destinées au service Power BI.
| Créer des rapports Power BI dans Power BI Desktop | Oui | Oui |  
| Créer des rapports Power BI dans le navigateur | Non | Oui |  
| Passerelle obligatoire | Non | Oui, pour les sources de données locales |  
| Streaming en temps réel | Non | Oui | [Streaming en temps réel dans Power BI](../service-real-time-streaming.md)
| Tableaux de bord | Non | Oui | [Tableaux de bord dans le service Power BI](../service-dashboards.md) 
| Distribuer un groupe de rapports à l’aide d’applications | Non | Oui | [Créer et publier des applications avec des tableaux de bord et des rapports](../service-create-distribute-apps.md) 
| Packs de contenu | Non | Oui | [Introduction aux packs de contenu d’organisation](../service-organizational-content-pack-introduction.md) 
| Se connecter à des services comme Salesforce | Non | Oui | [Se connecter aux services que vous utilisez](../service-connect-to-services.md) avec le service Power BI
| Questions/Réponses | Non | Oui | [Questions et réponses dans Power BI Desktop et le service Power BI](../power-bi-q-and-a.md) 
| Insights rapides | Non | Oui | [Générer automatiquement des informations sur les données avec Power BI](../service-insights.md) 
| Analyser dans Excel | Non | Oui | [Analyser dans Excel](../service-analyze-in-excel.md) 
| Rapports paginés | Oui | Non | Les rapports paginés ne sont pas disponibles dans le service Power BI, mais vous pouvez [épingler des éléments de rapport paginé à des tableaux de bord Power BI](https://docs.microsoft.com/sql/reporting-services/pin-reporting-services-items-to-power-bi-dashboards)
| Applications mobiles Power BI | Oui | Oui | [Vue d’ensemble des applications mobiles Power BI](../mobile-apps-for-mobile-devices.md) 
| Cartes ArcGIS | Non | Oui | [Cartes ArcGIS dans le service Power BI et Power BI Desktop par ESRI](../power-bi-visualization-arcgis.md)
| Abonnements par courrier électronique pour les rapports Power BI | Non | Oui | [S’abonner à un rapport ou un tableau de bord](../service-report-subscribe.md) dans le service Power BI 
| Abonnements par courrier électronique pour les rapports paginés | Oui | Non | [Remise du courrier électronique dans Reporting Services](https://docs.microsoft.com/sql/reporting-services/subscriptions/e-mail-delivery-in-reporting-services)  
| Alertes de données | Non | Oui | [Alertes de données](../service-set-data-alerts.md) dans le service Power BI
| Sécurité au niveau des lignes | Uniquement par le biais d’une source de données en mode DirectQuery | Disponible dans DirectQuery (source de données) et en mode d’importation | [Sécurité au niveau des lignes](../service-admin-rls.md) avec Power BI 
| Mode plein écran | Non | Oui | [Mode plein écran](../service-fullscreen-mode.md) dans le service Power BI 
| Collaboration Office 365 avancée | Non | Oui | [Collaborer dans un espace de travail d’application](../service-collaborate-power-bi-workspace.md) avec Office 365 
| Visuels R | Non | Oui | [Créer des visuels R](../service-r-visuals.md) dans le service Power BI  
| Fonctionnalités en préversion | Non | Oui | [Accéder aux fonctionnalités en préversion du service Power BI](../service-preview-features.md) 
| Éléments visuels personnalisés | Oui | Oui | [Éléments visuels personnalisés dans Power BI](../power-bi-custom-visuals.md) 
| Power BI Desktop | Version optimisée pour Report Server, disponible en téléchargement avec Report Server | Version optimisée pour le service Power BI, disponible sur le Windows Store | [Power BI Desktop pour Report Server](https://powerbi.microsoft.com/report-server/) <br><br> [Power BI Desktop pour le service Power BI](http://aka.ms/pbidesktopstore)

## <a name="next-steps"></a>Étapes suivantes
[Installer Power BI Report Server](install-report-server.md)  



