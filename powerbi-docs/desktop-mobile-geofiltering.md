---
title: Définir des filtres géographiques dans Power BI Desktop pour les applications mobiles
description: Quand vous définissez un filtrage géographique pour votre modèle dans Power BI Desktop, vous pouvez filtrer les données en fonction de votre emplacement automatiquement dans les applications mobiles Power BI.
author: maggiesMSFT
manager: kfile
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/16/2018
ms.author: maggies
LocalizationGroup: Model your data
ms.openlocfilehash: b8887ba39d3c6d3123d3308eddba2994fbfe6485
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "61296042"
---
# <a name="set-geographic-filters-in-power-bi-desktop-for-the-mobile-apps"></a>Définir des filtres géographiques dans Power BI Desktop pour les applications mobiles
Dans Power BI Desktop, vous pouvez [catégoriser les données géographiques](desktop-data-categorization.md) dans une colonne pour que Power BI Desktop sache comment traiter les valeurs des éléments visuels d’un rapport. Qui plus est, quand vous et vos collègues affichez ensuite ce rapport dans l’application mobile Power BI, Power BI fournit automatiquement les filtres géographiques correspondant à votre emplacement. 

Par exemple, supposons que vous soyez responsable des ventes et en déplacement pour rendre visite à des clients et que vous souhaitiez filtrer rapidement le total des ventes et des profits pour le client avec lequel vous avez rendez-vous. Vous souhaitez détailler les données pour votre emplacement actuel, que ce soit par département, ville ou adresse réelle. Plus tard, vous souhaitez rendre visite à d’autres clients situés à proximité si vous en avez le temps. Vous pouvez [filtrer le rapport en fonction de votre emplacement pour rechercher ces clients](consumer/mobile/mobile-apps-geographic-filtering.md).

> [!NOTE]
> Dans l’application mobile, vous ne pouvez filtrer par emplacement que si les noms géographiques qui figurent dans le rapport sont en anglais, par exemple « New York City » ou « Germany ».
> 
> 

## <a name="identify-geographic-data-in-your-report"></a>Identifier les données géographiques de votre rapport
1. Dans Power BI Desktop, passez à Vue de données ![Icône Vue Données](media/desktop-mobile-geofiltering/pbi_desktop_data_icon.png).
2. Sélectionnez une colonne de données géographiques, par exemple une colonne Ville.
   
    ![Colonne Ville](media/desktop-mobile-geofiltering/power-bi-desktop-geo-column.png)
3. Dans l’onglet **Modélisation**, sélectionnez **Catégorie de données**, puis la catégorie appropriée, c’est-à-dire **Ville** pour notre exemple.
   
    ![Zone Catégorie de données](media/desktop-mobile-geofiltering/power-bi-desktop-geo-category.png)
4. Définissez des catégories de données géographiques pour tous les autres champs du modèle. 
   
   > [!NOTE]
   > Vous pouvez définir plusieurs colonnes pour chaque catégorie de données dans un modèle, mais dans ce cas le modèle ne peut pas effectuer de filtrage géographique dans l’application mobile Power BI. Pour utiliser le filtrage géographique dans les applications mobiles, définissez une seule colonne pour chaque catégorie de données, par exemple une colonne **Ville**, une colonne **Département ou région** et une colonne **Pays**. 
   > 
   > 

## <a name="create-visuals-with-your-geographic-data"></a>Créer des visuels avec vos données géographiques
1. Passez au mode Rapport ![Icône Mode Rapport](media/desktop-mobile-geofiltering/power-bi-desktop-report-icon.png), puis créez des visuels qui utilisent les champs géographiques de vos données. 
   
    ![Rapport avec carte](media/desktop-mobile-geofiltering/power-bi-desktop-geo-report.png)
   
    Dans cet exemple, le modèle contient également une colonne calculée qui affiche la ville et l’État dans une même colonne. En savoir plus sur la [création de colonnes calculées dans Power BI Desktop](desktop-calculated-columns.md).
   
    ![Champ Ville + État](media/desktop-mobile-geofiltering/power-bi-desktop-city-state-column.png)
2. Publiez le rapport dans le service Power BI.

## <a name="view-the-report-in-power-bi-mobile-app"></a>Afficher le rapport dans l’application mobile Power BI
1. Ouvrez le rapport dans une [application mobile Power BI](consumer/mobile/mobile-apps-for-mobile-devices.md).
2. Si vous êtes dans un emplacement géographique avec des données dans le rapport, vous pouvez le filtrer automatiquement en fonction de votre emplacement.
   
    ![Filtre géographique dans l’application mobile](media/desktop-mobile-geofiltering/power-bi-mobile-geo-map-set-filter.png)

En savoir plus sur le [filtrage d’un rapport par emplacement dans les applications mobiles Power BI](consumer/mobile/mobile-apps-geographic-filtering.md).

## <a name="next-steps"></a>Étapes suivantes
* [Catégorisation des données dans Power BI Desktop](desktop-data-categorization.md)  
* Vous avez des questions ? [Essayez d’interroger la communauté Power BI](http://community.powerbi.com/)

