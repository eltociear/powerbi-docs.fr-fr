---
title: Afficher les données utilisées pour créer la visualisation Power BI
description: Ce document explique comment afficher les données utilisées pour créer un visuel dans Power BI et les exporter dans un fichier .csv.
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/4/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 5417511b12c85cb467c3613671a1e101541c9609
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/06/2020
ms.locfileid: "73880620"
---
# <a name="show-the-data-that-was-used-to-create-the-visualization"></a>Afficher les données utilisées pour créer la visualisation
## <a name="show-data"></a>Afficher les données
Une visualisation Power BI est construite à l’aide des données de vos jeux de données. Si vous voulez voir les calculs sous-jacents, Power BI vous permet d’*afficher* les données utilisées pour créer le visuel. Lorsque vous sélectionnez **Afficher les données**, Power BI affiche les données sous (ou à côté de) la visualisation.

Vous pouvez également exporter les données utilisées pour créer la visualisation au format .xlsx ou .csv et les afficher dans Excel. Pour plus d’informations, consultez [Exporter des données à partir des visualisations Power BI](power-bi-visualization-export-data.md).

> [!NOTE]
> Les options *Afficher les données* et *Exporter les données* sont disponibles dans le service Power BI et dans Power BI Desktop. Toutefois, Power BI Desktop offre un niveau de détails supplémentaire. [*Afficher les enregistrements* affiche les lignes réelles du jeu de données](../desktop-see-data-see-records.md).
> 
> 

## <a name="using-show-data"></a>Utiliser *Afficher les données* 
1. Dans Power BI Desktop, sélectionnez une visualisation pour l’activer.

2. Sélectionnez **Autres actions** (...) et choisissez **Afficher les données**. 
    ![option d’affichage pour Afficher les données](media/service-reports-show-data/power-bi-more-action.png)


3. Par défaut, les données s’affichent sous l’élément visuel.
   
   ![affichage vertical du visuel et des données](media/service-reports-show-data/power-bi-show-data-below.png)

4. Pour modifier l’orientation, sélectionnez la disposition verticale ![petite capture d’écran de l’icône utilisée pour passer à une disposition verticale](media/service-reports-show-data/power-bi-vertical-icon-new.png) dans l’angle supérieur droit de la visualisation.
   
   ![affichage horizontal du visuel et des données](media/service-reports-show-data/power-bi-show-data-side.png)
5. Pour exporter les données vers un fichier .csv, sélectionnez les points de suspension, puis choisissez **Exporter des données**.
   
    ![sélectionner Exporter des données](media/service-reports-show-data/power-bi-export-data-new.png)
   
    Pour plus d’informations sur l’exportation des données vers Excel, voir [Exporter les données de visualisations Power BI](power-bi-visualization-export-data.md).
6. Pour masquer les données, désélectionnez **Explorer** > **Afficher les données**.

## <a name="using-show-records"></a>Utiliser Afficher les enregistrements
Vous pouvez également vous concentrer sur un enregistrement de données et explorer les données qui se trouvent derrière. 

1. Pour utiliser **Afficher les enregistrements**, sélectionnez une visualisation pour l’activer. 

2. Dans le ruban Desktop, sélectionnez l’onglet **Outils pour les visuels** > **Données/Explorer** > **Afficher les enregistrements**. 

    ![Capture d’écran avec l’option Afficher les enregistrements sélectionnée.](media/service-reports-show-data/power-bi-see-record.png)

3. Sélectionnez un point de données ou une ligne dans la visualisation. Dans cet exemple, nous avons sélectionné la quatrième colonne à partir de la gauche. Power BI montre l’enregistrement du jeu de données correspondant à ce point de données.

    ![Capture d’écran d’un enregistrement d’un jeu de données.](media/service-reports-show-data/power-bi-row.png)

4. Sélectionnez **Retour au rapport** pour revenir au canevas de rapport Desktop. 

## <a name="considerations-and-troubleshooting"></a>Considérations et résolution des problèmes

- Si le bouton **Afficher les enregistrements** du ruban est désactivé et grisé, cela signifie que la visualisation sélectionnée ne prend pas en charge l’affichage des enregistrements.
- Vous ne pouvez pas modifier les données dans la vue Afficher les enregistrements et les enregistrer dans le rapport.
- Vous ne pouvez pas utiliser l’option Afficher les enregistrements si votre visuel utilise une mesure calculée.
- Vous ne pouvez pas utiliser l’option Afficher les enregistrements quand vous êtes connecté à un modèle multidimensionnel (MD) actif.  

## <a name="next-steps"></a>Étapes suivantes
[Exporter des données à partir des visualisations Power BI](power-bi-visualization-export-data.md)    

D’autres questions ? [Posez vos questions à la communauté Power BI](https://community.powerbi.com/)

