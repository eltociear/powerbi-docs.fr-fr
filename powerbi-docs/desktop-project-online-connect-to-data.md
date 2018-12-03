---
title: 'Project Online : se connecter à des données au moyen de Power BI Desktop'
description: 'Project Online : se connecter à des données au moyen de Power BI Desktop'
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 3773f1cb13eb967c511245f57cf59c7159d68fba
ms.sourcegitcommit: 2ae660a7b70fce23eb58b159d049eca44a664f2c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2018
ms.locfileid: "52669885"
---
# <a name="project-online-connect-to-data-through-power-bi-desktop"></a>Project Online : se connecter à des données au moyen de Power BI Desktop
Vous pouvez vous connecter à des données dans Project Online au moyen de Power BI Desktop.

### <a name="step-1-download-power-bi-desktop"></a>Étape 1 : télécharger Power BI Desktop
1. [Téléchargez Power BI Desktop](http://go.microsoft.com/fwlink/?LinkID=521662), puis exécutez le programme d’installation pour installer **Power BI Desktop** sur votre ordinateur.

### <a name="step-2-connect-to-project-online-with-odata"></a>Étape 2 : se connecter à Project Online avec OData
1. Ouvrez **Power BI Desktop**.
2. Dans l’écran de *bienvenue*, sélectionnez **Obtenir des données**.
3. Choisissez **Flux OData**, puis sélectionnez **Se connecter**.
4. Entrez l’adresse de votre flux OData dans la zone URL, puis cliquez sur OK.
   
   Si l’adresse de votre site Project Web App ressemble à https://\<nom_client\>.sharepoint.com/sites/pwa, l’adresse que vous devez entrer pour votre flux OData est https://\<nom_client\>.sharepoint.com/sites/pwa/\_api/Projectdata.
   
   Dans notre exemple, nous utilisons https://contoso.sharepoint.com/sites/pwa/default.aspx
5. Power BI Desktop vous invite à vous authentifier avec votre compte Office 365. Sélectionnez Compte professionnel, puis entrez vos informations d’identification.
   
   ![](media/desktop-project-online-connect-to-data/image.png)

Il est à noter que le compte que vous utilisez pour vous connecter au flux OData doit disposer d’au moins un accès Visionneuse de portefeuilles au site Project Web App. 

À ce stade, vous pouvez choisir les tables auxquelles vous souhaitez vous connecter et créer une requête.  Vous ignorez par où commencer ?  Le billet de blog suivant montre comment créer un burndown chart pour vos données Project Online.  Il décrit comment se connecter à Project Online avec Power Query, mais la procédure s’applique également à Power BI Desktop.

[Création de burndown charts pour Project à l’aide de Power Pivot et Power Query](http://blogs.office.com/2014/03/24/creating-burndown-charts-for-project-using-power-pivot-and-power-query/)

