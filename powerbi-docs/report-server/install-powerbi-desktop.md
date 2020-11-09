---
title: Installer Power BI Desktop optimisé pour Power BI Report Server
description: Découvrez comment installer Power BI Desktop optimisé pour Power BI Report Server
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: how-to
ms.date: 10/16/2020
ms.openlocfilehash: 62add0b1268b06bb227bdc1b8ec2e4ae59358c57
ms.sourcegitcommit: a5fa368abad54feb44a267fe26c383a731c7ec0d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93044752"
---
# <a name="install-power-bi-desktop-optimized-for-power-bi-report-server"></a>Installer Power BI Desktop optimisé pour Power BI Report Server

Afin de créer des rapports Power BI pour Power BI Report Server, vous devez télécharger et installer la version de Power BI Desktop qui est optimisée pour Power BI Report Server. Il s’agit d’une version différente de Power BI Desktop utilisée avec le service Power BI. Par exemple, la version de Power BI Desktop pour le service Power BI comprend des fonctionnalités d’évaluation. Ces fonctionnalités ne sont pas dans la version de Power BI Report Server tant qu’elles ne sont pas en disponibilité générale. Elle est nécessaire pour s’assurer que le serveur de rapports peut interagir avec une version connue des rapports et du modèle. 

Pas de panique. Vous pouvez installer Power BI Desktop et Power BI Desktop optimisé pour Power BI Report Server côte à côte sur le même ordinateur.

## <a name="download-and-install-power-bi-desktop"></a>Télécharger et installer Power BI Desktop

Le moyen le plus simple d’avoir la version la plus récente de Power BI Desktop optimisée pour Power BI Report Server est de démarrer à partir du portail web de votre serveur de rapports.

1. Dans le portail web de votre serveur de rapports, sélectionnez la flèche **Télécharger** > **Power BI Desktop**.

    ![Télécharger Power BI Desktop à partir du portail web](media/install-powerbi-desktop/report-server-download-web-portal.png)

    Vous pouvez accéder à la page d’accueil de [Power BI Report Server](https://powerbi.microsoft.com/report-server/) et sélectionner les **options de téléchargement avancées**.

2. Dans la page du Centre de téléchargement, sélectionnez une langue, puis sélectionnez **Télécharger**.

3. En fonction de votre ordinateur, sélectionnez : 

    - **PBIDesktopRS.msi** (version 32 bits) ou
    - **PBIDesktopRS_x64.msi** (version 64 bits).

1. Après avoir téléchargé le programme d’installation, exécutez l’Assistant Installation de Power BI Desktop.

2. À la fin de l’installation, sélectionnez **Lancer Power BI Desktop**.

    Power BI Desktop démarre et vous pouvez l’utiliser.

## <a name="verify-youre-using-the-correct-version"></a>Vérifier que vous utilisez la version correcte
Il est facile de vérifier que vous utilisez la bonne version de Power BI Desktop : Regardez la barre de titre ou l’écran de démarrage dans Power BI Desktop. Vous pouvez voir que vous disposez de la version adéquate, car **Power BI Desktop (octobre 2020)** s’affiche dans la barre de titre. De plus, les couleurs du logo Power BI sont inversées, jaune sur fond noir au lieu de noir sur fond jaune.

![Power BI Desktop - Octobre 2020](media/install-powerbi-desktop/power-bi-report-server-desktop-may-2020.png)

La barre de titre de la version de Power BI Desktop pour le service Power BI n’indique pas le mois et l’année.

## <a name="file-extension-association"></a>Association d’extension de fichier
Supposons que vous ayez installé Power BI Desktop et Power BI Desktop optimisé pour Power BI Report Server sur la même machine. Votre installation la plus récente de Power BI Desktop présente une association avec les fichiers .pbix. Par conséquent, quand vous double-cliquez sur un fichier .pbix, la version de Power BI Desktop que vous avez installée en dernier démarre.

Si vous avez Power BI Desktop, puis que vous installez Power BI Desktop optimisé pour Power BI Report Server, tous les fichiers .pbix s’ouvrent dans Power BI Desktop optimisé pour Power BI Report Server par défaut. Si vous préférez que Power BI Desktop soit démarré par défaut lors de l’ouverture d’un fichier pbix, réinstallez [Power BI Desktop à partir du Microsoft Store](https://aka.ms/pbidesktopstore).

Vous pouvez toujours commencer par ouvrir la version de Power BI Desktop que vous souhaitez utiliser, puis ouvrir le fichier à partir de Power BI Desktop.

Voici la méthode la plus sûre pour ouvrir systématiquement la bonne version de Power BI Desktop. Commencez par modifier un rapport Power BI à partir de Power BI Report Server ou créez un rapport Power BI à partir du service Power BI.

## <a name="considerations-and-limitations"></a>Considérations et limitations

Les rapports Power BI dans Power BI Report Server, dans le service Power BI (`https://app.powerbi.com`) et dans les applications mobiles Power BI fonctionnent pratiquement de la même manière, mais certaines caractéristiques diffèrent.

### <a name="selecting-a-language"></a>Sélection d’une langue

Pour Power BI Desktop optimisé pour Power BI Report Server, vous sélectionnez la langue d’installation de l’application. Vous ne pouvez pas la changer après, mais vous pouvez installer une version dans une autre langue.

### <a name="report-visuals-in-a-browser"></a>Visuels de rapport dans un navigateur

Les rapports Power BI Report Server prennent en charge presque toutes les visualisations, notamment les visuels Power BI. Les rapports Power BI Report Server ne prennent pas en charge les fonctionnalités suivantes :

* Visuels R
* ArcGIS Maps
* Fil d’Ariane
* Fonctionnalités en préversion Power BI Desktop

### <a name="reports-in-the-power-bi-mobile-apps"></a>Rapports dans les applications mobiles Power BI

Les rapports Power BI Report Server prennent en charge toutes les fonctionnalités de base des [applications mobiles Power BI](../consumer/mobile/mobile-apps-for-mobile-devices.md), à savoir :

* [Disposition des rapports pour téléphone](../create-reports/desktop-create-phone-report.md) : Vous pouvez optimiser un rapport pour les applications mobiles Power BI. Sur votre téléphone mobile, les rapports optimisés ont une icône ![icône de disposition de rapport sur téléphone](media/install-powerbi-desktop/power-bi-rs-mobile-optimized-icon.png) et une disposition spéciales.
  
    ![Rapports optimisés pour les téléphones](media/install-powerbi-desktop/power-bi-rs-mobile-optimized-report.png)

Les rapports Power BI Report Server ne prennent pas en charge les fonctionnalités suivantes dans les applications mobiles Power BI :

* Visuels R
* ArcGIS Maps
* Visuels Power BI
* Fil d’Ariane
* Filtrage basé sur la géolocalisation ou codes barres

### <a name="custom-security"></a>Sécurité personnalisée

Power BI Desktop optimisé pour Power BI Report Server ne prend pas en charge la sécurité personnalisée. Si votre Power BI Report Server est configuré avec une extension de sécurité personnalisée, vous ne pouvez pas enregistrer un rapport Power BI à partir de Power BI Desktop (optimisé pour Power BI Report Server) sur l’instance Power BI Report Server. Vous devez enregistrer le fichier de rapport .pbix à partir de Power BI Desktop et le charger sur le site du portail Power BI Report Server.

### <a name="saving-reports-to-a-power-bi-report-server-in-a-different-domain"></a>Enregistrement de rapports sur un serveur Power BI Report Server dans un autre domaine

Quand vous enregistrez un rapport Power BI sur Power BI Report Server, vos informations d’identification Windows sont utilisées. L’enregistrement direct sur un serveur de rapports dans un domaine différent de celui de vos informations d’identification Windows n’est pas pris en charge. Vous pouvez utiliser à la place un navigateur web pour visualiser le serveur de rapports et charger manuellement le fichier à partir de votre machine.

## <a name="next-steps"></a>Étapes suivantes

À présent que Power BI Desktop est installé, vous pouvez commencer à créer des rapports Power BI.

[Créer un rapport Power BI pour Power BI Report Server](quickstart-create-powerbi-report.md)  
[Présentation de Power BI Report Server](get-started.md)

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)

