---
title: Filtrer un rapport en fonction de l’emplacement géographique dans une application mobile Power BI
description: Découvrez comment filtrer un rapport en fonction de votre emplacement géographique dans les applications mobiles Microsoft Power BI, si le propriétaire du rapport a défini des balises géographiques.
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: how-to
ms.date: 03/11/2020
ms.author: painbar
ms.openlocfilehash: 4cf94628b1d423d5b382e718d850fc403d516083
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85234323"
---
# <a name="filter-a-report-by-geographic-location-in-the-power-bi-mobile-apps"></a>Filtrer un rapport en fonction de l’emplacement géographique dans les applications mobiles Power BI
S’applique à :

| ![iPhone](./media/mobile-apps-geographic-filtering/iphone-logo-50-px.png) | ![iPad](./media/mobile-apps-geographic-filtering/ipad-logo-50-px.png) | ![Téléphone Android](./media/mobile-apps-geographic-filtering/android-phone-logo-50-px.png) | ![Tablette Android](./media/mobile-apps-view-dashboard/android-tablet-logo-50-px.png) | ![Téléphone Windows](./media/mobile-apps-geographic-filtering/win-10-logo-50-px.png) |
|:--- |:--- |:--- |:--- |:--- |
| iPhone |iPad |Téléphones Android |Tablettes Android |Téléphones Windows 10 |

Quand vous consultez un rapport Power BI sur votre appareil mobile, pouvez-vous voir une petite icône en forme de punaise dans le coin supérieur droit ? Si oui, cela signifie que vous pouvez filtrer ce rapport en fonction de votre emplacement géographique.

> [!NOTE]
> Vous pouvez filtrer par emplacement seulement si les noms géographiques qui figurent dans le rapport sont en anglais, par exemple « New York City » ou « Germany ». Les téléphones Windows 10 prennent en charge le filtrage géographique, mais pas les tablettes et PC Windows 10.

>[!NOTE]
>La prise en charge des applications mobiles Power BI pour les **téléphones utilisant Windows 10 Mobile** ne sera plus disponible après le 16 mars 2021. [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2121400)

## <a name="filter-your-report-by-your-geographic-location"></a>Filtrer un rapport en fonction de votre emplacement géographique
1. Ouvrez un rapport dans l’application mobile Power BI sur votre appareil mobile.
2. Si le rapport contient des données géographiques, un message vous demande d’autoriser Power BI à accéder à votre emplacement. Cliquez sur **Autoriser**, puis appuyez à nouveau sur **Autoriser**.
3. Appuyez sur la punaise ![Icône en forme de punaise](./media/mobile-apps-geographic-filtering/power-bi-mobile-geo-icon.png). Vous pouvez filtrer par ville, état/province ou pays/région, selon les données disponibles dans le rapport. Le filtre répertorie uniquement les options qui correspondent à votre emplacement actuel.
   
    ![Filtre sous forme de punaise](./media/mobile-apps-geographic-filtering/power-bi-mobile-geo-map-set-filter.png)

## <a name="why-dont-i-see-location-tags-on-a-report"></a>Pourquoi ne puis-je pas voir les balises d’emplacement sur un rapport ?
Vous devez respecter les trois conditions suivantes pour voir les balises d’emplacement. 

* La personne qui a créé le rapport dans Power BI Desktop doit avoir [classé les données géographiques](../../transform-model/desktop-mobile-geofiltering.md) pour au moins une colonne, comme Ville, État ou Pays/région.
* Vous êtes dans un des emplacements contenant des données dans cette colonne.
* Vous utilisez l’un des appareils mobiles suivants :
  * iOS (iPad, iPhone, iPod).
  * Android (téléphone, tablette).
  * Téléphone Windows 10 (les autres appareils Windows 10 tels que les tablettes et PC ne prennent pas en charge le filtrage géographique).

En savoir plus sur la [définition d’un filtrage géographique](../../transform-model/desktop-mobile-geofiltering.md) dans Power BI Desktop.

### <a name="next-steps"></a>Étapes suivantes
* [Se connecter aux données Power BI réelles](mobile-apps-data-in-real-world-context.md) avec les applications mobiles
* [Catégorisation des données dans Power BI Desktop](../../transform-model/desktop-data-categorization.md) 
* Des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
