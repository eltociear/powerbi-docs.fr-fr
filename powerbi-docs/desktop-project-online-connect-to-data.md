---
title: 'Project Online : se connecter à des données au moyen de Power BI Desktop'
description: 'Project Online : se connecter à des données au moyen de Power BI Desktop'
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 815566f715bb4544fc4b002ea2c31e21e2684792
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75760816"
---
# <a name="connect-to-project-online-data-through-power-bi-desktop"></a>Se connecter à des données Project Online via Power BI Desktop
Vous pouvez vous connecter à des données dans Project Online au moyen de Power BI Desktop.

## <a name="step-1-download-power-bi-desktop"></a>Étape 1 : Télécharger Power BI Desktop
1. [Téléchargez Power BI Desktop](https://go.microsoft.com/fwlink/?LinkID=521662), puis exécutez le programme d’installation pour installer **Power BI Desktop** sur votre ordinateur.

## <a name="step-2-connect-to-project-online-with-odata"></a>Étape 2 : Se connecter à Project Online avec OData
1. Ouvrez **Power BI Desktop**.
2. Dans l’écran de *bienvenue*, sélectionnez **Obtenir des données**.
3. Choisissez **Flux OData**, puis sélectionnez **Se connecter**.
4. Entrez l’adresse de votre flux OData dans la zone URL, puis cliquez sur OK.
   
   Si l’adresse de votre site Project Web App ressemble à *https://\<nom_client\>.sharepoint.com/sites/pwa*, l’adresse que vous devez entrer pour votre flux OData est *https://\<nom_client\>.sharepoint.com/sites/pwa/\_api/Projectdata*.
   
   Dans notre exemple, nous utilisons https://contoso.sharepoint.com/sites/pwa/default.aspx
5. Power BI Desktop vous invite à vous authentifier avec votre compte Office 365. Sélectionnez Compte professionnel, puis entrez vos informations d’identification.
   
   ![](media/desktop-project-online-connect-to-data/image.png)

Le compte que vous utilisez pour vous connecter au flux OData doit disposer d’au moins un accès Visionneuse de portefeuilles au site Project Web App. 

À ce stade, vous pouvez choisir les tables auxquelles vous souhaitez vous connecter et créer une requête.  Vous ignorez par où commencer ?  Le billet de blog suivant montre comment créer un burn down chart pour vos données Project Online.  Il décrit comment se connecter à Project Online avec Power Query, mais la procédure s’applique également à Power BI Desktop.

[Création de burn down charts pour Project à l’aide de Power Pivot et Power Query](https://blogs.office.com/2014/03/24/creating-burndown-charts-for-project-using-power-pivot-and-power-query/)

