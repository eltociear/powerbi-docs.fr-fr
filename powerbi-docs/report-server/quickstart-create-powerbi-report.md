---
title: Créer un rapport Power BI pour Power BI Report Server
description: Découvrez comment créer un rapport Power BI pour Power BI Report Server en quelques étapes simples.
services: powerbi
documentationcenter: ''
author: maggiesMSFT
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 3/22/2018
ms.author: maggies
ms.openlocfilehash: 4d860c9d18d1053b6c6cff55be2735eea6e86703
ms.sourcegitcommit: 493f160d04ed411ff4741c599adc63ba1f65230f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33814286"
---
# <a name="create-a-power-bi-report-for-power-bi-report-server"></a>Créer un rapport Power BI pour Power BI Report Server
Vous pouvez stocker et gérer des rapports Power BI localement sur le portail web Power BI Report Server tout comme vous pouvez stocker des rapports Power BI dans le cloud, dans le service Power BI (https://powerbi.com)). Créez et modifiez des rapports dans Power BI Desktop, puis publiez-les sur le portail web. Les lecteurs au sein de votre organisation peuvent alors les consulter dans un navigateur ou dans une application mobile Power BI sur un appareil mobile.

![Rapport Power BI dans le portail web](media/quickstart-create-powerbi-report/report-server-powerbi-report.png)

Voici quatre étapes rapides pour démarrer.

## <a name="step-1-install-power-bi-desktop-optimized-for-power-bi-report-server"></a>Étape 1 : Installer Power BI Desktop optimisé pour Power BI Report Server

Si vous avez déjà créé des rapports Power BI dans Power BI Desktop, vous êtes presque prêt à créer des rapports Power BI pour Power BI Report Server. Nous vous recommandons d’installer la version de Power BI Desktop optimisée pour Power BI Report Server afin d’être certain que le serveur et l’application soient toujours synchronisés. Vous pouvez avoir les deux versions de Power BI Desktop sur le même ordinateur.

1. Dans le portail web de votre serveur de rapports, sélectionnez la flèche **Télécharger** > **Power BI Desktop**.

    ![Télécharger Power BI Desktop à partir du portail web](media/quickstart-create-powerbi-report/report-server-download-web-portal.png)

    Vous pouvez aussi accéder directement à [Microsoft Power BI Desktop](https://www.microsoft.com/download/details.aspx?id=56723) (optimisé pour Power BI Report Server - mars 2018) dans le Centre de téléchargement Microsoft.

2. Dans la page du Centre de téléchargement, sélectionnez **Télécharger**.

3. En fonction de votre ordinateur, sélectionnez :

    - **PBIDesktopRS.msi** (version 32 bits) ou

    - **PBIDesktopRS_x64.msi** (version 64 bits).

4. Après avoir téléchargé le programme d’installation, exécutez l’Assistant Installation de Power BI Desktop (mars 2018).

2. À l’issue de l’installation, cochez **Démarrer Power BI Desktop maintenant**.
   
    Power BI Desktop démarre et vous pouvez l’utiliser. Vous pouvez voir que vous disposez de la version adéquate, car « Power BI Desktop (mars 2018) » apparaît dans la barre de titre.

    ![Version Power BI Desktop de mars 2018](media/quickstart-create-powerbi-report/report-server-desktop-march-2018.png)

3. Si vous n’êtes pas familiarisé avec Power BI Desktop, songez à regarder les vidéos proposées sur l’écran d’accueil.
   
    ![Écran de démarrage de Power BI Desktop](media/quickstart-create-powerbi-report/report-server-powerbi-desktop-start.png)

## <a name="step-2-select-a-data-source"></a>Étape 2 : sélectionner une source de données
Vous pouvez vous connecter à un vaste éventail de sources de données. Pour en savoir plus, voir [Connexion à des sources de données](connect-data-sources.md).

1. Dans l’écran de bienvenue, sélectionnez **Obtenir les données**.
   
    Ou bien, sous l’onglet **Accueil**, sélectionnez **Obtenir les données**.
2. Sélectionnez votre source de données, en l’occurrence, **Analysis Services**.
   
    ![Sélectionner une source de données](media/quickstart-create-powerbi-report/report-server-get-data-ssas.png)
3. Spécifiez le **Serveur** et, éventuellement, la **Base de données**. Assurez-vous que l’option **Connexion directe** est activée, puis sélectionnez **OK**.
   
    ![Nom du serveur](media/quickstart-create-powerbi-report/report-server-ssas-server-name.png)
4. Choisissez le serveur de rapports dans lequel enregistrer vos rapports.
   
    ![Sélection du serveur de rapports](media/quickstart-create-powerbi-report/report-server-select-server.png)

## <a name="step-3-design-your-report"></a>Étape 3 : créer votre rapport
C’est la partie amusante la plus agréable : créer des éléments visuels illustrant vos données.

Par exemple, vous pouvez créer un graphique en entonnoir de valeurs de clients et de groupe par revenu annuel.

![Concevoir un rapport](media/quickstart-create-powerbi-report/report-server-create-funnel.png)

1. Dans **Visualisations**, sélectionnez **Graphique en entonnoir**.
2. Faites glisser le champ à compter vers le puits **Valeurs**. S’il ne s’agit pas d’un champ numérique, Power BI Desktop le convertit automatiquement en valeur *Nombre de*.
3. Faites glisser le champ à grouper vers puits **Groupe**.

En savoir plus sur la [conception d’un rapport Power BI](../desktop-report-view.md).

## <a name="step-4-save-your-report-to-the-report-server"></a>Étape 4 : enregistrer votre rapport sur le serveur de rapports
Une fois le rapport prêt, enregistrez-le sur le serveur de rapports Power BI Report Server que vous avez choisi à l’étape 2.

1. Dans le menu **Fichier**, sélectionnez **Enregistrer sous** > **Power BI Report Server**.
   
    ![Enregistrer sur le serveur de rapports](media/quickstart-create-powerbi-report/report-server-save-as-powerbi-report-server.png)
2. Vous pouvez à présent l’afficher dans le portail web.
   
    ![Afficher le rapport dans le portail web](media/quickstart-create-powerbi-report/report-server-powerbi-report.png)

## <a name="considerations-and-limitations"></a>Considérations et limitations
Les rapports dans Power BI Report Server et dans le service Power BI (http://powerbi.com)) fonctionnent pratiquement de la même manière, mais certaines fonctionnalités diffèrent.

### <a name="in-a-browser"></a>Dans un navigateur
Les rapports Power BI Report Server prennent en charge toutes les visualisations, à savoir :

* Éléments visuels personnalisés

Les rapports Power BI Report Server ne prennent pas en charge les fonctionnalités suivantes :

* Visuels R
* ArcGIS Maps
* Fil d’Ariane
* Fonctionnalités en préversion Power BI Desktop

### <a name="in-the-power-bi-mobile-apps"></a>Dans les applications mobiles Power BI
Les rapports Power BI Report Server prennent en charge toutes les fonctionnalités de base des [applications mobiles Power BI](../mobile-apps-for-mobile-devices.md), à savoir :

* [Disposition des rapports pour téléphone](../desktop-create-phone-report.md) : vous pouvez optimiser un rapport pour les applications mobiles Power BI. Sur votre téléphone mobile, les rapports optimisés ont une icône ![icône de disposition de rapport sur téléphone](media/quickstart-create-powerbi-report/power-bi-rs-mobile-optimized-icon.png) et une disposition spéciales.
  
    ![Rapports optimisés pour les téléphones](media/quickstart-create-powerbi-report/power-bi-rs-mobile-optimized-report.png)

Les rapports Power BI Report Server ne prennent pas en charge les fonctionnalités suivantes dans les applications mobiles Power BI :

* Visuels R
* ArcGIS Maps
* Éléments visuels personnalisés
* Fil d’Ariane
* Filtrage basé sur la géolocalisation ou codes barres

## <a name="next-steps"></a>Étapes suivantes
### <a name="power-bi-desktop"></a>Power BI Desktop
Il existe de nombreuses ressources excellentes pour la création de rapports dans Power BI Desktop. Ce lien constitue un bon point de départ.

* [Prise en main de Power BI Desktop](../desktop-getting-started.md)

### <a name="power-bi-report-server"></a>Power BI Report Server
* [Installer Power BI Desktop optimisé pour Power BI Report Server](install-powerbi-desktop.md)  
* [Manuel de l’utilisateur Power BI Report Server](user-handbook-overview.md)  

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
