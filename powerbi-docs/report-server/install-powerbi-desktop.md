---
title: Installer Power BI Desktop optimisé pour Power BI Report Server
description: Découvrez comment installer Power BI Desktop optimisé pour Power BI Report Server
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 05/22/2019
ms.openlocfilehash: 54713c9c978554521d68aeb7b4c25d681ddb3d69
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66187463"
---
# <a name="install-power-bi-desktop-optimized-for-power-bi-report-server"></a>Installer Power BI Desktop optimisé pour Power BI Report Server

Afin de créer des rapports Power BI pour Power BI Report Server, vous devez télécharger et installer Power BI Desktop optimisé pour Power BI Report Server. Il s’agit d’une version différente de Power BI Desktop utilisée avec le service Power BI. Par exemple, la version de Power BI Desktop pour le service Power BI présente des fonctionnalités en préversion qui ne sont pas dans la version Power BI Report Server tant qu’elles ne sont pas publiées. Elle est nécessaire pour s’assurer que le serveur de rapports peut interagir avec une version connue des rapports et du modèle. 

La bonne nouvelle est que vous pouvez installer Power BI Desktop et Power BI Desktop optimisé pour Power BI Report Server côte à côte sur le même ordinateur.

## <a name="download-and-install-power-bi-desktop"></a>Télécharger et installer Power BI Desktop

Le moyen le plus simple d’avoir la version la plus récente de Power BI Desktop optimisée pour Power BI Report Server est de démarrer à partir du portail web de votre serveur de rapports.

1. Dans le portail web de votre serveur de rapports, sélectionnez la flèche **Télécharger** > **Power BI Desktop**.

    ![Télécharger Power BI Desktop à partir du portail web](media/install-powerbi-desktop/report-server-download-web-portal.png)

    Ou accédez directement à [Microsoft Power BI Desktop](https://www.microsoft.com/download/details.aspx?id=56723) (optimisé pour Power BI Report Server - mai 2019) dans du Microsoft Download Center.

2. Dans la page du Centre de téléchargement, sélectionnez **Télécharger**.

3. En fonction de votre ordinateur, sélectionnez : 

    - **PBIDesktopRS.msi** (version 32 bits) ou

    - **PBIDesktopRS_x64.msi** (version 64 bits).

1. Après avoir téléchargé le programme d’installation, exécutez l’Assistant Installation de Power BI Desktop (mai 2019).

2. À la fin de l’installation, sélectionnez **lancer Power BI Desktop**.

    Power BI Desktop démarre et vous pouvez l’utiliser.

## <a name="verify-youre-using-the-correct-version"></a>Vérifier que vous utilisez la version correcte
Il est facile de vérifier que vous utilisez la bonne version de Power BI Desktop : Regardez la barre de titre ou l’écran de démarrage dans Power BI Desktop. La barre de titre indique le mois et l’année de publication. De plus, les couleurs du logo Power BI sont inversées, jaune sur fond noir au lieu de noir sur fond jaune.

![Barre de titre pour Power BI Desktop optimisé pour Power BI Report Server](media/install-powerbi-desktop/power-bi-report-server-desktop-may-2019.png)

La barre de titre de la version Power BI Desktop du service Power BI n’affiche pas le mois et l’année.

## <a name="file-extension-association"></a>Association d’extension de fichier
Si vous installez Power BI Desktop et Power BI Desktop optimisé pour Power BI Report Server sur le même ordinateur, l’installation la plus récente de Power BI Desktop présente une association avec les fichiers .pbix. Par conséquent, quand vous double-cliquez sur un fichier .pbix, la version de Power BI Desktop que vous avez installée en dernier démarre.

Si vous avez Power BI Desktop, puis que vous installez Power BI Desktop optimisé pour Power BI Report Server, tous les fichiers .pbix s’ouvrent dans Power BI Desktop optimisé pour Power BI Report Server par défaut. Si vous préférez que Power BI Desktop soit démarré par défaut lors de l’ouverture d’un fichier pbix, réinstallez [Power BI Desktop à partir du Microsoft Store](http://aka.ms/pbidesktopstore).

Vous pouvez toujours commencer par ouvrir la version de Power BI Desktop que vous souhaitez utiliser, puis ouvrir le fichier à partir de Power BI Desktop.

Modification d’un rapport Power BI à partir de Power BI Report Server ou la création d’un nouveau rapport Power BI à partir du portail web, s’ouvre toujours la version appropriée de Power BI Desktop.

## <a name="considerations-and-limitations"></a>Considérations et limitations

Les rapports Power BI dans Power BI Report Server, dans le service Power BI (http://app.powerbi.com) et dans les applications mobiles Power BI fonctionnent pratiquement de la même manière, mais certaines fonctionnalités diffèrent.

### <a name="in-a-browser"></a>Dans un navigateur

Rapports Power BI Report Server prennent en charge presque toutes les visualisations, y compris des éléments visuels personnalisés. Les rapports Power BI Report Server ne prennent pas en charge les fonctionnalités suivantes :

* Visuels R
* ArcGIS Maps
* Fil d’Ariane
* Fonctionnalités en préversion Power BI Desktop

### <a name="in-the-power-bi-mobile-apps"></a>Dans les applications mobiles Power BI

Les rapports Power BI Report Server prennent en charge toutes les fonctionnalités de base des [applications mobiles Power BI](../consumer/mobile/mobile-apps-for-mobile-devices.md), à savoir :

* [Disposition des rapports pour téléphone](../desktop-create-phone-report.md) : Vous pouvez optimiser un rapport pour les applications mobiles Power BI. Sur votre téléphone mobile, les rapports optimisés ont une icône ![icône de disposition de rapport sur téléphone](media/install-powerbi-desktop/power-bi-rs-mobile-optimized-icon.png) et une disposition spéciales.
  
    ![Rapports optimisés pour les téléphones](media/install-powerbi-desktop/power-bi-rs-mobile-optimized-report.png)

Les rapports Power BI Report Server ne prennent pas en charge les fonctionnalités suivantes dans les applications mobiles Power BI :

* Visuels R
* ArcGIS Maps
* Éléments visuels personnalisés
* Fil d’Ariane
* Geo filtrage ou codes barres

## <a name="power-bi-desktop-for-earlier-versions-of-power-bi-report-server"></a>Power BI Desktop pour les versions antérieures de Power BI Report Server

Si votre serveur de rapports est d’une version antérieure, vous avez besoin de la version correspondante de Power BI Desktop. Voici le lien pour télécharger la version précédente.

- Microsoft Power BI Desktop ([optimisé pour Power BI Report Server - janvier 2019](https://go.microsoft.com/fwlink/?linkid=2055039))

## <a name="next-steps"></a>Étapes suivantes

À présent que Power BI Desktop est installé, vous pouvez commencer à créer des rapports Power BI.

[Créer un rapport Power BI pour Power BI Report Server](quickstart-create-powerbi-report.md)  
[Présentation de Power BI Report Server](get-started.md)

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
