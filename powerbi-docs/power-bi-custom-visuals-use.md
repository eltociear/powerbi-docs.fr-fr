---
title: "Ajout d’un élément visuel personnalisé à un rapport (Power BI Desktop)"
description: "Ajout d’un élément visuel personnalisé à un rapport dans Power BI Desktop"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: complete
qualitydate: 03/15/2016
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 09/27/2017
ms.author: mihart
ms.openlocfilehash: b3a3e34fac546ee57cd66924e72a2c93aa647850
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2017
---
# <a name="add-a-custom-visual-to-a-report-desktop"></a>Ajout d’un élément visuel personnalisé à un rapport (Power BI Desktop)
Vous avez [téléchargé un modèle d’élément visuel personnalisé](service-custom-visuals-office-store.md) et vous l’avez enregistré sur votre ordinateur ou dans un autre emplacement.  L’étape suivante consiste à importer ce modèle de visuel personnalisé dans un rapport pour qu’il apparaisse en tant qu’option dans votre volet Visualisation.

![](media/power-bi-custom-visuals-use/pbi-custom-viz-icon.png)

Un modèle d’élément visuel personnalisé est ajouté à un rapport spécifique pendant son importation. Si vous souhaitez utiliser le modèle d’élément visuel dans un autre rapport, vous devez aussi l’importer dans ce rapport. Quand un rapport comportant un élément visuel personnalisé est enregistré à l’aide de l’option **Enregistrer sous** , une copie du modèle d’élément visuel personnalisé est enregistrée avec le nouveau rapport.

1. Ouvrez Power BI Desktop, puis sélectionnez le rapport dans lequel vous souhaitez ajouter la visualisation personnalisée.   
2. Vous pouvez importer un modèle d’élément visuel personnalisé de deux façons : à partir du menu **Fichier** ou à partir du volet **Visualisations** .
   
    **Dans le menu Fichier du bureau**
   
    Dans le menu **Fichier** du rapport, choisissez **Importer** &gt; **Élément visuel personnalisé Power BI**. Vous devez être en mode Édition.    
   
      ![](media/power-bi-custom-visuals-use/power-bi-import.png)
   
    **Dans le volet Visualisation**
   
    Dans le volet **Visualisations** , choisissez **Insérer (...)**.    
   
      ![](media/power-bi-custom-visuals-use/insertpane.png)
   
    Sélectionnez **Importer un élément visuel personnalisé**.  
   
      ![](media/power-bi-custom-visuals-use/insertpane.png)
3. **Examinez l’avertissement**.
   
    Un visuel personnalisé a accès aux données du rapport, et lorsque vous partagez un rapport qui contient des visuels personnalisés, vos collègues peuvent accéder à ces mêmes données. Veillez à examiner l’élément visuel personnalisé pour vous assurer qu’il provient d’une source digne de confiance. Microsoft vous recommande de travailler avec votre service informatique si vous n’êtes pas sûr de vouloir utiliser un visuel personnalisé spécifique obtenu à partir de la boutique en ligne Office, par e-mail ou à partir d’une autre source.
   
    ![](media/power-bi-custom-visuals-use/caution.png)
4. Accédez à l’emplacement où vous avez enregistré le visuel personnalisé .pbiviz, puis ouvrez ce dernier.
5. Une icône (également appelée *modèle*) est ajoutée à votre volet **Visualisations**.
   
    ![](media/power-bi-custom-visuals-use/visualuse.png)
6. Sélectionnez le modèle d’élément visuel personnalisé pour l’ajouter à votre rapport comme vous le feriez avec les autres modèles dans le volet Visualisations. Ajoutez des champs et des filtres, puis créez votre élément visuel.
7. Mettez en forme l’élément visuel personnalisé comme vous le feriez pour n’importe quel autre élément visuel.  Dans le volet **Visualisations**, sélectionnez l’icône représentant un rouleau. Les options de mise en forme disponibles peuvent varier selon le type d’élément visuel.

## <a name="considerations-and-troubleshooting"></a>Considérations et résolution des problèmes
* Pour permettre la prise en charge des visuels personnalisés dans l’[exportation vers PowerPoint](service-publish-to-powerpoint.md), ou leur [affichage dans des e-mails reçus quand un client s’abonne à des pages de rapport](service-report-subscribe.md), ces visuels doivent être définis en tant que *visuels personnalisés certifiés* ayant passé le processus de certification de visuel personnalisé de Microsoft.  Pour afficher la liste des *visuels personnalisés certifiés* et pour en savoir plus sur le processus de certification, voir [Visuels personnalisés certifiés](power-bi-custom-visuals-certified.md).

## <a name="next-steps"></a>Étapes suivantes
[Télécharger et utiliser les visuels personnalisés de l’Office Store](service-custom-visuals-office-store.md)  
[Ajout d’un visuel personnalisé à un rapport dans le service Power BI](power-bi-report-add-custom-visual.md)  
[Publier des visuels personnalisés dans l’Office Store](developer/office-store.md)  
[Visualisations personnalisées dans Power BI](power-bi-custom-visuals.md)  
D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)

