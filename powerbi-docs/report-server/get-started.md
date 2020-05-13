---
title: Présentation de Power BI Report Server
description: Obtenez une vue d’ensemble de Power BI Report Server pour comprendre la manière dont il s’intègre avec SQL Server Reporting Services (SSRS) et les autres composants de Power BI.
keywords: ''
author: maggiesMSFT
ms.author: maggies
ms.date: 04/29/2020
ms.topic: overview
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.custom: mvc
ms.openlocfilehash: 39ccb9120b7dd61d7f160c296d2de799b7f3fe23
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83141103"
---
# <a name="what-is-power-bi-report-server"></a>Présentation de Power BI Report Server

Power BI Report Server est un serveur de rapports local avec un portail web dans lequel vous affichez et gérez les rapports et indicateurs de performance clés. Il est fourni avec les outils nécessaires pour créer des rapports Power BI, des rapports paginés, des rapports mobiles et des indicateurs de performance clés. Vos utilisateurs peuvent accéder à ces rapports de différentes façons : les afficher dans un navigateur web ou un appareil mobile, ou sous forme d’e-mail dans leur boîte de réception.

![Portail web de Power BI Report Server web](media/get-started/power-bi-report-server-overview.png)

## <a name="comparing-power-bi-report-server"></a>Comparaison de Power BI Report Server 
Power BI Report Server ressemble à la fois à SQL Server Reporting Services et au service en ligne Power BI, mais avec quelques différences. Comme le service Power BI, Power BI Report Server héberge des rapports Power BI (.pbix), des fichiers Excel et des rapports paginés (.rdl). Comme Reporting Services, Power BI Report Server est installé localement. Les fonctionnalités de Power BI Report Server sont un sur-ensemble de Reporting Services : tout ce que vous pouvez faire dans Reporting Services, vous pouvez aussi le faire avec Power BI Report Server, avec en plus la prise en charge des rapports Power BI. Consultez [Comparer Power BI Report Server et le service Power BI](compare-report-server-service.md) pour plus d’informations.

## <a name="licensing-power-bi-report-server"></a>Gestion des licences Power BI Report Server
Power BI Report Server est disponible sous deux licences différentes : [Power BI Premium](../admin/service-premium-what-is.md) et [SQL Server Enterprise](https://www.microsoft.com/sql-server/sql-server-2017-editions) avec Software Assurance. Une licence Power BI Premium vous permet de créer un déploiement hybride combinant ressources dans le cloud et ressources locales.  

> [!NOTE]
> Pour Power BI Premium, Power BI Report Server est uniquement inclus dans les références (SKU) P. Il n’est pas inclus dans les références (SKU) EM.

## <a name="web-portal"></a>Portail web
Le point d’entrée de Power BI Report Server est un portail web sécurisé affichable dans n’importe quel navigateur moderne. Ici, vous accédez à l’ensemble de vos rapports et indicateurs de performance clés. Le contenu du portail web est organisé sous forme d’une hiérarchie standard de dossiers. Dans les dossiers, le contenu est regroupé par type : rapports Power BI, rapports mobiles, rapports paginés, indicateurs de performance clés et classeurs Excel. Les jeux de données partagés et les sources de données partagées sont dans leurs propres dossiers, et vous pouvez les utiliser en tant que modules pour vos rapports. Vous marquez des favoris pour les afficher dans un dossier unique. Vous créez également des indicateurs de performance clés directement dans le portail web. 

![Portail web de Power BI Report Server web](media/get-started/web-portal.png)

Selon vos autorisations, vous pouvez gérer le contenu dans le portail web. Vous pouvez planifier le traitement des rapports, accéder à des rapports à la demande et vous abonner à des rapports publiés. Vous pouvez également [personnaliser](https://docs.microsoft.com/sql/reporting-services/branding-the-web-portal) votre portail web. 

En savoir plus sur le [portail web Power BI Report Server](https://docs.microsoft.com/sql/reporting-services/web-portal-ssrs-native-mode).

## <a name="power-bi-reports"></a>Rapports Power BI
Vous créez des rapports Power BI (.pbix) avec la version Power BI Desktop optimisée pour le serveur de rapports. Puis vous publiez et affichez ces rapports dans le portail web de votre propre environnement.

![Rapports Power BI reports dans Power BI Report Server](media/get-started/powerbi-reports.png)

Un rapport Power BI est un affichage sous plusieurs angles d’un modèle de données, comportant des visualisations de différentes observations et informations concernant ce modèle de données.  Un rapport peut comprendre une seule visualisation ou des pages remplies de visualisations. Selon votre rôle, vous pouvez lire et explorer des rapports, ou les créer pour d’autres utilisateurs.

Pour plus d’informations, consultez [Installation de Microsoft Power BI Desktop](install-powerbi-desktop.md).

## <a name="paginated-reports"></a>Rapports paginés
Les rapports paginés (.rdl) sont des rapports de style document avec des visualisations, dans lesquels des tables se développent horizontalement et verticalement pour afficher toutes les données et page après page, selon les besoins. Ils conviennent bien pour la génération de documents à disposition fixe, précis au pixel près, optimisés pour l’impression, tels que des fichiers PDF et Word. 

![Rapports paginés dans Power BI Report Server](media/get-started/paginated-reports.png)

Vous pouvez créer des rapports paginés à l’aide du [Générateur de rapports](https://docs.microsoft.com/sql/reporting-services/report-builder/report-builder-in-sql-server-2016) ou du Concepteur de rapports dans [SQL Server Data Tools (SSDT)](https://docs.microsoft.com/sql/reporting-services/tools/reporting-services-in-sql-server-data-tools-ssdt).

## <a name="reporting-services-mobile-reports"></a>Rapports mobiles Reporting Services
Les rapports mobiles se connectent aux données locales, avec une disposition réactive qui s’adapte aux différents appareils et aux différentes façons dont vous les conservez. Vous les créez dans l’Éditeur de rapports mobiles Microsoft SQL Server.

En savoir plus sur les [Rapports mobiles Reporting Services](https://docs.microsoft.com/sql/reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher). 

## <a name="report-server-programming-features"></a>Fonctionnalités de programmation de Report Server
Tirez parti des fonctionnalités de programmation de Power BI Report Server pour étendre et personnaliser vos rapports avec des API pour intégrer ou étendre le traitement des données et des rapports dans des applications personnalisées.

Plus de [Documentation pour les développeurs de Reporting Services](https://docs.microsoft.com/sql/reporting-services/reporting-services-developer-documentation).

## <a name="next-steps"></a>Étapes suivantes
[Installer Power BI Report Server](install-report-server.md)  
[Télécharger le Générateur de rapports](https://www.microsoft.com/download/details.aspx?id=53613)  

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
