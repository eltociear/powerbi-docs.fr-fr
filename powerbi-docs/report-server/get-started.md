---
title: "Prise en main de Power BI Report Server"
description: "Découvrez comment installer Power BI Report Server. "
services: powerbi
documentationcenter: 
author: guyinacube
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
ms.date: 11/01/2017
ms.author: maghan
ms.openlocfilehash: a1dc05e722d4b50321b1fc825eeab9284d2d88b5
ms.sourcegitcommit: eec6b47970bf69ed30638d1a20051f961ba792f2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/06/2018
---
# <a name="get-started-with-power-bi-report-server"></a>Prise en main de Power BI Report Server
Créez, déployez et gérez localement des rapports Power BI mobiles et paginés avec la gamme d’outils et services prêts à l’emploi de Power BI Report Server.

## <a name="create-deploy-and-manage-reports"></a>Créer, déployer et gérer des rapports
Power BI Report Server est une solution que les clients déploient localement pour créer, publier et gérer des rapports, puis remettre ceux-ci aux utilisateurs appropriés de différentes façons, que ce soit par voie d’affichage dans un navigateur web ou sur un appareil mobile, ou par l’envoi d’un e-mail à leur boîte aux lettres.

Power BI Report Server offre une divers produits :

* un portail web moderne que vous pouvez consulter à l’aide de n’importe quel navigateur récent, via lequel vous pouvez organiser et afficher des rapports et indicateurs de performance clés, et sur lequel vous pouvez également stocker des classeurs Excel ;
* des rapports Power BI créés avec Power BI Desktop, que vous pouvez afficher à l’intérieur du portail web dans votre propre environnement ;
* des rapports paginés qui vous permettent de créer des rapports d’aspect moderne, avec les outils nécessaires pour les créer ;
* des rapports mobiles avec une disposition réactive qui s’adapte aux différents appareils et aux différentes façons dont vous les conservez.

Poursuivez votre lecture pour en savoir plus sur chacune de ces solutions.

### <a name="whats-new-in-power-bi-report-server"></a>Nouveautés dans Power BI Report Server
Les sources suivantes vous permettent de vous tenir informé des nouvelles fonctionnalités de Power BI Report Server.

* [Nouveautés dans Power BI Report Server](whats-new.md)
* [Blog Microsoft Power BI](https://powerbi.microsoft.com/blog/)
* [Blog de l’équipe SQL Server Reporting Services](https://blogs.msdn.microsoft.com/sqlrsteamblog/)
* [Chaîne YouTube Guy in a Cube](https://aka.ms/guyinacube)

## <a name="web-portal"></a>Portail web
![](media/get-started/web-portal.png)

Pour les utilisateurs finaux de Power BI Report Server, la porte d’entrée est un portail web moderne affichable dans n’importe quel navigateur moderne. Le nouveau portail vous permet d’accéder à l’ensemble de vos rapports et indicateurs de performance clés.

Vous pouvez [personnaliser](https://docs.microsoft.com/sql/reporting-services/branding-the-web-portal) votre portail web. Vous pouvez également créer des indicateurs de performance clés directement dans le portail web. Des indicateurs de performance clés permettent de voir des métriques métier clés en un coup d’œil dans le navigateur, sans nécessité d’ouvrir un rapport.

Le contenu du portail web est organisé par types : rapports Power BI, rapports mobiles, rapports paginés et indicateurs de performance clés, ainsi que classeurs Excel, datasets partagés et sources de données à utiliser comme blocs de construction pour vos rapports. Vous pouvez stocker et gérer ces éléments ici en toute sécurité dans la hiérarchie de dossiers traditionnelle. Vous pouvez marquer vos favoris et gérer le contenu si ce rôle vous est attribué.

Vous pouvez également planifier le traitement des rapports, accéder à des rapports à la demande et vous abonner à des rapports publiés sur le nouveau portail web.

Informations complémentaires sur le [portail Web](https://docs.microsoft.com/sql/reporting-services/web-portal-ssrs-native-mode).

## <a name="power-bi-reports"></a>Rapports Power BI
![](media/get-started/powerbi-reports.png)

Un rapport Power BI est un affichage sous plusieurs angles d’un dataset, comportant des visualisations de différentes observations et informations concernant ce dataset.  Un rapport peut comprendre une seule visualisation ou des pages remplies de visualisations. Selon votre fonction principale, vous pouvez être quelqu’un qui crée des rapports et/ou qui consomme ou utilise ceux-ci.

Les rapports sont basés sur un seul jeu de données. Les visualisations dans un rapport représentent chacune une pépite d’informations. Par ailleurs, les visualisations ne sont pas statiques. Vous pouvez ajouter et supprimer des données, modifier les types de visualisations et appliquer des filtres et segments à mesure que vous explorez les données pour découvrir des informations et trouver des réponses. Plus encore qu’un tableau de bord, un rapport est hautement interactif et personnalisable, et les visualisations s’actualisent à mesure que les données sous-jacentes changent.

## <a name="paginated-reports"></a>Rapports paginés
![](media/get-started/paginated-reports.png)

Les rapports paginés sont des rapports de style document paginé qui contiennent d’autant plus de pages que la quantité de données et de lignes dans les tables est importante. Ils conviennent bien pour la génération de documents à disposition fixe, précis au pixel près, optimisés pour l’impression, tels que des fichiers PDF et Word.

Vous pouvez créer des rapports d’aspect moderne à l’aide du [Générateur de rapports](https://docs.microsoft.com/sql/reporting-services/report-builder/report-builder-in-sql-server-2016) ou du Concepteur de rapports dans [SQL Server Data Tools (SSDT)](https://docs.microsoft.com/sql/reporting-services/tools/reporting-services-in-sql-server-data-tools-ssdt).

## <a name="report-server-programming-features"></a>Fonctionnalités de programmation de Report Server
Tirez parti des fonctionnalités de programmation de Power BI Report Server pour étendre et personnaliser vos fonctionnalités de création de rapports avec des API pour intégrer ou étendre le traitement des données et des rapports dans des applications personnalisées.

Plus de [Documentation pour les développeurs de Reporting Services](https://docs.microsoft.com/sql/reporting-services/reporting-services-developer-documentation).

## <a name="next-steps"></a>Étapes suivantes
[Manuel de l’utilisateur](user-handbook-overview.md)  
[Manuel de l’administrateur](admin-handbook-overview.md)  
[Démarrage rapide : installer Power BI Report Server](quickstart-install-report-server.md)  
[Installer le Générateur de rapports](https://docs.microsoft.com/sql/reporting-services/install-windows/install-report-builder)  
[Télécharger SQL Server Data Tools (SSDT)](http://go.microsoft.com/fwlink/?LinkID=616714)

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)

