---
title: "Se connecter à ClickDimensions avec Power BI"
description: ClickDimensions pour Power BI
services: powerbi
documentationcenter: 
author: joeshoukry
manager: kfile
backup: maggiesMSFT
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/16/2017
ms.author: yshoukry
ms.openlocfilehash: cde6ca545d37b2ba490578bf43e7de95b10931d7
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2017
---
# <a name="connect-to-clickdimensions-with-power-bi"></a>Se connecter à ClickDimensions avec Power BI
Le pack de contenu ClickDimensions pour Power BI permet aux utilisateurs d’utiliser les données marketing ClickDimensions dans Power BI, donnant ainsi aux équipes de gestion une analyse approfondie de leurs efforts de ventes et marketing. Visualisez et analysez les interactions de la messagerie, les visites web et les envois de formulaire dans les rapports et tableaux de bord Power BI.

Connectez-vous au [pack de contenu ClickDimensions](https://app.powerbi.com/getdata/services/click-dimensions) pour Power BI.

## <a name="how-to-connect"></a>Comment se connecter
1. Sélectionnez **Obtenir des données** en bas du volet de navigation gauche.
   
   ![](media/service-connect-to-clickdimensions/getdata.png)
2. Dans la zone **Services** , sélectionnez **Obtenir**.
   
   ![](media/service-connect-to-clickdimensions/services.png)
3. Sélectionnez **ClickDimensions** \>  **Obtenir**.
   
   ![](media/service-connect-to-clickdimensions/clickdimensions.png)
4. Indiquez l'emplacement de votre centre de données (US, EU ou AU), puis sélectionnez **Suivant**.
   
   ![](media/service-connect-to-clickdimensions/params.png)
5. Pour la **méthode d’authentification**, sélectionnez **De base** \> **Se connecter**. Quand vous y êtes invité, entrez vos informations d’identification ClickDimensions. Voir les détails sur la [recherche de ces paramètres](#FindingParams) ci-dessous.
   
    ![](media/service-connect-to-clickdimensions/creds.png)
6. Après l’approbation, le processus d’importation démarre automatiquement. Une fois terminé, de nouveaux tableau de bord, rapport et modèle apparaîtront dans le volet de navigation. Sélectionnez le tableau de bord pour afficher vos données importées.
   
     ![](media/service-connect-to-clickdimensions/dashboard.png)

**Et maintenant ?**

* Essayez de [poser une question dans la zone Q&R](service-q-and-a.md) en haut du tableau de bord.
* [Modifiez les vignettes](service-dashboard-edit-tile.md) dans le tableau de bord.
* [Sélectionnez une vignette](service-dashboard-tiles.md) pour ouvrir le rapport sous-jacent.
* Même si une actualisation quotidienne de votre jeu de données est planifiée, vous pouvez modifier la planification de l’actualisation ou essayer d’actualiser le jeu de données sur demande à l’aide de l’option **Actualiser maintenant**.

## <a name="system-requirements"></a>Configuration requise
Pour utiliser le pack de contenu Power BI, vous devez indiquer le centre de données correspondant dans votre compte et vous connecter avec votre compte ClickDimensions. Si vous ne savez pas quel centre de données indiquer, contactez votre administrateur.

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Recherche de paramètres
La clé de compte se trouve dans Paramètres CRM \> Paramètres ClickDimensions. Copiez la clé de compte à partir de Paramètres ClickDimensions et collez-la dans le champ Nom d’utilisateur.  

![](media/service-connect-to-clickdimensions/crm.png)  

Copiez le jeton Power BI à partir de Paramètres ClickDimensions et collez-le dans le champ Nom d’utilisateur. Le jeton Power BI se trouve dans Paramètres CRM \> Paramètres ClickDimensions.  

![](media/service-connect-to-clickdimensions/crm2.png)  

## <a name="next-steps"></a>Étapes suivantes
[Prise en main de Power BI](service-get-started.md)

[Obtenir des données dans Power BI](service-get-data.md)

