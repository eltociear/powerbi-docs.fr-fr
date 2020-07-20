---
title: 'Service tiers : Connecteur Google Analytics'
description: 'Service tiers : Connecteur Google Analytics pour Power BI Desktop'
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: ec290ce53155f24a9213a4849ecb82abd6cfc592
ms.sourcegitcommit: e8ed3d120699911b0f2e508dc20bd6a9b5f00580
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2020
ms.locfileid: "86263657"
---
# <a name="use-the-google-analytics-connector-for-power-bi-desktop"></a>Utiliser le connecteur Google Analytics pour Power BI Desktop
> [!NOTE]
> Le pack de contenu et le connecteur Google Analytics de Power BI Desktop s’appuient sur l’API Core Reporting de Google Analytics. Ses fonctionnalités et sa disponibilité peuvent donc varier au fil du temps.

Vous pouvez vous connecter aux données Google Analytics à l’aide du connecteur **Google Analytics**. Pour vous connecter aux données, procédez comme suit :

1. Dans **Power BI Desktop**, sélectionnez **Obtenir des données** dans l’onglet de ruban **Accueil**.
2. Dans la fenêtre **Obtenir des données**, sélectionnez **Services en ligne** parmi les catégories du volet gauche.
3. Sélectionnez **Google Analytics** dans les sélections du volet droit.
4. Au bas de la fenêtre, sélectionnez **Se connecter**.  
   ![Capture d’écran de l’onglet Accueil, montrant le ruban Obtenir des données avec Google Analytics sélectionné et le bouton Se connecter.](media/service-google-analytics-connector/tps_googleanalytics_1.png)

Une boîte de dialogue s’affiche, expliquant, entre autres éclaircissements, que le connecteur est un service tiers et que la disponibilité et les fonctionnalités de celui-ci peuvent changer avec le temps.  
![Capture d’écran de la boîte de dialogue de connexion, montrant un avertissement indiquant que le connecteur s’appuie sur un service tiers.](media/service-google-analytics-connector/tps_googleanalytics_2.png)

Quand vous sélectionnez **Continuer**, vous êtes invité à vous connecter à Google Analytics.  
![Capture d’écran de l’invite Google Analytics, montrant que vous devez vous connecter.](media/service-google-analytics-connector/tps_googleanalytics_3.png)

Quand vous entrez vos informations d’identification, une boîte de dialogue vous informe que Power BI souhaite avoir un accès hors connexion. Voici comment utiliser **Power BI Desktop** pour accéder à vos données Google Analytics.  

Lorsque vous acceptez, **Power BI Desktop** indique que vous êtes actuellement connecté.  
![Capture d’écran de l’invite Google Analytics indiquant que vous êtes connecté.](media/service-google-analytics-connector/tps_googleanalytics_5.png)

Sélectionnez **Se connecter** pour connecter vos données Google Analytics à **Power BI Desktop** et charger les données.  
![Capture d’écran de la boîte de dialogue Charger, montrant que les données Google Analytics sont connectées et chargées.](media/service-google-analytics-connector/tps_googleanalytics_6.png)

## <a name="changes-to-the-api"></a>Modifications apportées à l’API
Nous nous efforçons de publier des mises à jour en fonction des modifications. Toutefois, il se peut que l’API soit modifiée d’une manière qui affecte les résultats des requêtes que nous générons. Dans certains cas, certaines requêtes peuvent ne plus être prises en charge. En raison de cette dépendance, nous ne pouvons pas garantir les résultats de vos requêtes lors de l’utilisation de ce connecteur.

Pour plus d’informations sur les modifications apportées à l’API Google Analytics, consultez le [journal des modifications](https://developers.google.com/analytics/devguides/changelog)

