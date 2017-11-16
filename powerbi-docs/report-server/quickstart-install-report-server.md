---
title: "Démarrage rapide : installer Power BI Report Server"
description: "L’installation de Power BI Report Server est un processus très rapide. Du téléchargement à la configuration en passant par l’installation, vous devriez être opérationnel en quelques minutes."
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
ms.date: 06/28/2017
ms.author: asaxton
ms.openlocfilehash: 2e616369333d3bb2747ec20eb2072b69d5b9f9d5
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2017
---
# <a name="quickstart-install-power-bi-report-server"></a>Démarrage rapide : installer Power BI Report Server
L’installation de Power BI Report Server est un processus très rapide. Du téléchargement à la configuration en passant par l’installation, vous devriez être opérationnel en quelques minutes.

Nous vous expliquons brièvement ici comment installer un serveur de rapports si vous voulez juste être rapidement opérationnel avec un nouveau serveur. Pour des informations plus détaillées sur l’installation d’un serveur de rapports, voir [Installer Power BI Report Server](install-report-server.md).

 **Télécharger** ![télécharger](media/quickstart-install-report-server/download.png "télécharger")

Pour télécharger Power BI Report Server, accédez à [Rapports locaux avec Power BI Report Server](https://powerbi.microsoft.com/report-server/). Pour télécharger Power BI Desktop optimisé pour Power BI Report Server, accédez au [Centre de téléchargement Microsoft](https://go.microsoft.com/fwlink/?linkid=837581).

![conseil](media/quickstart-install-report-server/fyi-tip.png "conseil") Pour les notes de publication actuelles, voir [Notes de publication de Power BI Report Server](release-notes.md).

<iframe width="640" height="360" src="https://www.youtube.com/embed/zacaEb9A4F0?showinfo=0" frameborder="0" allowfullscreen></iframe>

## <a name="before-you-begin"></a>Avant de commencer
Avant d’installer Power BI Report Server, il est recommandé de lire l’article [Configurations matérielle et logicielle requises pour Installer Power BI Report Server](system-requirements.md).

## <a name="step-1-download"></a>Étape 1 : télécharger
Téléchargez les fichiers d’installation pour Power BI Report Server localement. Pour télécharger Power BI Report Server, accédez au [Centre de téléchargement Microsoft](https://go.microsoft.com/fwlink/?linkid=839351).

![Télécharger Power BI Report Server](media/quickstart-install-report-server/download-pbireportserver.png)

## <a name="step-2-run-installer"></a>Étape 2 : exécuter le programme d’installation
Exécutez le fichier PowerBIReportServer.exe que vous avez téléchargé et suivez les indications des écrans d’installation. Vous aurez la possibilité de choisir le chemin d’installation ainsi que de sélectionner l’édition à installer. Vous avez le choix entre une version d’évaluation de 180 jours, une édition développeur et la possibilité d’installer à l’aide d’une clé de produit.

![Installer Power BI Report Server](media/quickstart-install-report-server/pbireportserver-install.png)

## <a name="step-3-configure-the-server"></a>Étape 3 : configurer le serveur
Une fois l’installation terminée, vous allez exécuter le Gestionnaire de configuration pour achever la configuration de votre serveur. Vous devez créer une base de données de catalogues ReportServer et vérifier le portail web et les URL de service web.

![Configurer Power BI Report Server](media/quickstart-install-report-server/pbireportserver-configure.png)

## <a name="step-4-browse-to-web-portal"></a>Étape 4 : accéder au portail web
À présent que vous avez effectué la configuration, vous devriez être en mesure d’accéder au portail web de votre serveur dans un navigateur. Par défaut, l’URL est `http://localhost/reports`. Vous allez également pouvoir naviguer à l’aide du nom de l’ordinateur plutôt que de celui de l’hôte local par défaut, en supposant qu’aucun type de pare-feu ne vous bloque.

![Portail web de Power BI Report Server web](media/quickstart-install-report-server/web-portal.png)

## <a name="next-steps"></a>Étapes suivantes
[Manuel de l’administrateur](admin-handbook-overview.md)  
[Trouver la clé de produit de votre serveur de rapports](find-product-key.md)  
[Installer Power BI Report Server](install-report-server.md)  
[Installer Power BI Desktop optimisé pour Power BI Report Server](install-powerbi-desktop.md)  
[Prise en charge du navigateur pour Power BI Report Server](browser-support.md)

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)

