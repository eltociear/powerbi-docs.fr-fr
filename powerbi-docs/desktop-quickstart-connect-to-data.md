---
title: 'Démarrage rapide : Se connecter aux données dans Power BI Desktop'
description: Découvrez comment vous connecter aux sources de données disponibles dans Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: quickstart
ms.date: 01/10/2020
ms.author: davidi
LocalizationGroup: quickstart
ms.openlocfilehash: 5aed52ec232d3e603d69bfe93640187401279ff6
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "75885236"
---
# <a name="quickstart-connect-to-data-in-power-bi-desktop"></a>Démarrage rapide : Se connecter aux données dans Power BI Desktop

Dans ce guide de démarrage rapide, vous vous connectez aux données à l’aide de Power BI Desktop, ce qui constitue la première étape de la création de modèles de données et de rapports.

![Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_01.png)

Si vous n’êtes pas inscrit à Power BI, [inscrivez-vous à un essai gratuit](https://app.powerbi.com/signupredirect?pbi_source=web) avant de commencer.

## <a name="prerequisites"></a>Conditions préalables

Pour effectuer les étapes de cet article, vous avez besoin des ressources suivantes :

* Télécharger et installer Power BI Desktop, qui est une application gratuite qui s’exécute sur votre ordinateur local. Vous pouvez [télécharger Power BI Desktop](https://powerbi.microsoft.com/desktop) directement, ou l’obtenir à partir du [Microsoft Store](https://aka.ms/pbidesktopstore).
* [Téléchargez cet exemple de classeur Excel](https://go.microsoft.com/fwlink/?LinkID=521962), puis créez un dossier appelé *C:\PBID-qs* dans lequel vous pouvez stocker le fichier Excel. Les étapes ultérieures de ce guide de démarrage rapide utilisent cet emplacement pour le stockage du classeur Excel téléchargé.
* Bon nombre de connecteurs de données dans Power BI Desktop requièrent Internet Explorer 10 (ou une version plus récente) pour l’authentification.

## <a name="launch-power-bi-desktop"></a>Démarrer Power BI Desktop

Après avoir installé Power BI Desktop, lancez l’application sur votre ordinateur local. Vous voyez un tutoriel Power BI. Suivez le tutoriel ou fermez la boîte de dialogue pour commencer avec un canevas vierge. Le canevas est l’endroit où vous créez des visuels et des rapports à partir de vos données.

![Power BI Desktop avec un canevas vierge](media/desktop-quickstart-connect-to-data/qs-connect-data_01.png)

## <a name="connect-to-data"></a>Se connecter aux données

Avec Power BI Desktop, vous pouvez vous connecter à de nombreux types de données différents. Ces sources incluent les sources de données courantes, comme un fichier Microsoft Excel. Vous pouvez vous connecter à des services en ligne hébergeant toutes sortes de données comme Salesforce, Microsoft Dynamics, Stockage Blob Azure, et bien plus encore.

Pour vous connecter à des données, dans le ruban **Accueil**, sélectionnez **Obtenir les données**.

![Obtenir des données dans le ruban Accueil](media/desktop-quickstart-connect-to-data/qs-connect-data_02.png)

La fenêtre **Obtenir des données** s’affiche. Vous pouvez choisir l’une des multiples sources de données auxquelles Power BI Desktop peut se connecter. Dans ce guide de démarrage rapide, utilisez le classeur Excel que vous avez téléchargé à l’étape [Prérequis](#prerequisites).

![Obtenir des données de toutes les sources](media/desktop-quickstart-connect-to-data/qs-connect-data_03.png)

Puisque cette source de données est un fichier Excel, sélectionnez **Excel** dans la fenêtre **Obtenir des données**, puis sélectionnez le bouton **Se connecter**.

Power BI vous invite à indiquer l’emplacement du fichier Excel auquel vous connecter. Le fichier téléchargé est appelé *Exemple financier*. Sélectionnez ce fichier, puis sélectionnez **Ouvrir**.

![Obtenir des données du fichier Exemple financier](media/desktop-quickstart-connect-to-data/qs-connect-data_04.png)

Power BI Desktop charge alors le classeur et lit son contenu, puis affiche les données disponibles dans le fichier dans la fenêtre **Navigator**. Dans cette fenêtre, vous pouvez ensuite choisir les données à charger dans Power BI Desktop. Sélectionnez les tables en cochant la case de chaque table que vous souhaitez importer. Importez les deux tables disponibles.

![Sélectionner des données dans la fenêtre Navigateur](media/desktop-quickstart-connect-to-data/qs-connect-data_05.png)

Après avoir effectué vos sélections, choisissez **Charger** pour importer les données dans Power BI Desktop.

## <a name="view-data-in-the-fields-pane"></a>Afficher les données dans le volet Champs

Une fois les tables chargées, le volet **Champs** affiche les données. Vous pouvez développer chaque table en sélectionnant la flèche à côté de son nom. Dans l’image suivante, la table *financials* est développée, montrant chacun de ses champs.

![Obtenir des données](media/desktop-quickstart-connect-to-data/qs-connect-data_06.png)

Et voilà ! Vous vous êtes connecté à des données dans Power BI Desktop, vous avez chargé ces données et vous voyez maintenant tous les champs disponibles dans ces tables.

## <a name="next-steps"></a>Étapes suivantes

Une fois que vous êtes connecté aux données, vous pouvez effectuer toutes sortes d’opérations avec Power BI Desktop. Vous pouvez notamment créer des visuels et des rapports. Pour commencer, examinez les ressources suivantes :

* [Prise en main de Power BI Desktop](desktop-getting-started.md)
