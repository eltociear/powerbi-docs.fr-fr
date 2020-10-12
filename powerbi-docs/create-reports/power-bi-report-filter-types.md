---
title: Types de filtres dans les rapports Power BI
description: Découvrez les différents types de filtres de rapports dans Power BI, notamment le filtre de page, le filtre de visualisation ou le filtre de rapport.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/25/2019
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: 0dfd55a710ed13f9f17ad2f4e1f01ed5101f189a
ms.sourcegitcommit: 6bc66f9c0fac132e004d096cfdcc191a04549683
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2020
ms.locfileid: "91749388"
---
# <a name="types-of-filters-in-power-bi-reports"></a>Types de filtres dans les rapports Power BI

Les filtres ne se comportent pas tous de la même façon, car ils ne sont pas créés de la même façon. La façon dont vous les créez influence leur comportement dans le nouveau volet de filtre en mode édition. Dans cet article, nous décrivons les différents types de filtres : les différentes façons dont vous les créez et ce à quoi ils servent. En savoir plus sur comment [ajouter des filtres aux rapports](power-bi-report-add-filter.md). 

![Volet de filtre](media/power-bi-report-filter-types/power-bi-filter-pane.png)

Commençons par les deux types de filtres courants : automatique et manuel.

## <a name="manual-filters"></a>Filtres manuels 

Les filtres manuels sont les filtres que les créateurs de rapports glissent et déposent n’importe où dans le nouveau volet de filtre. Les utilisateurs avec l’autorisation d’édition pour le rapport peuvent modifier, supprimer, effacer, masquer, verrouiller, renommer ou trier ce filtre dans le nouveau volet.

## <a name="automatic-filters"></a>Filtres automatiques 

Les filtres automatiques sont les filtres qui sont automatiquement ajoutés au niveau visuel du volet de filtre lorsque vous générez un visuel. Ces filtres sont basés sur les champs qui composent votre visuel. Les utilisateurs avec l’autorisation d’édition pour le rapport peuvent modifier, effacer, masquer, verrouiller, renommer ou trier ce filtre dans le nouveau volet. Ils ne peuvent pas supprimer des filtres automatiques, car le visuel fait référence à ces champs.

## <a name="more-advanced-filters"></a>Autres filtres avancés

Les types de filtres suivants sont moins courants, mais il est important de les comprendre s’ils apparaissent dans votre rapport. En outre, vous pourriez les trouver utiles pour créer le filtre approprié pour votre rapport.

## <a name="include-and-exclude-filters"></a>Filtres Inclure/Exclure

Les filtres Inclure et Exclure sont automatiquement ajoutés au volet de filtre lorsque vous utilisez la fonctionnalité Inclure ou Exclure pour un visuel. Les utilisateurs avec l’autorisation d’édition pour le rapport peuvent supprimer, verrouiller, masquer ou trier ce filtre dans le nouveau volet. Ils ne peuvent pas modifier, effacer ou renommer un filtre Inclure ou Exclure, car il est associé à la fonctionnalité Inclure et Exclure des visuels.

![Filtre Exclure](media/power-bi-report-filter-types/power-bi-filters-exclude.png)

## <a name="drill-down-filters"></a>Filtres Descendre dans la hiérarchie

Les filtres Descendre dans la hiérarchie sont automatiquement ajoutés au volet de filtre lorsque vous utilisez la fonctionnalité Descendre dans la hiérarchie pour un visuel dans votre rapport. Les utilisateurs avec l’autorisation d’édition pour le rapport peuvent modifier ou effacer le filtre dans le nouveau volet. Ils ne peuvent pas supprimer, masquer, verrouiller, renommer ou trier ce filtre, car il est associé à la fonctionnalité Descendre dans la hiérarchie des visuels. Pour supprimer le filtre Descendre dans la hiérarchie, vous cliquez sur le bouton Monter dans la hiérarchie pour le visuel.

![Filtre Descendre dans la hiérarchie](media/power-bi-report-filter-types/power-bi-filters-drill-down.png)

## <a name="cross-drill-filters"></a>Filtres Exploration croisée

Les filtres Exploration croisée sont automatiquement ajoutés au nouveau volet lorsqu’un filtre Descendre dans la hiérarchie est passé à un autre visuel sur la page de rapport via la fonctionnalité Filtrage croisé ou Sélection croisée. Les utilisateurs avec l’autorisation d’édition sur le rapport ne peuvent pas supprimer, effacer, masquer, verrouiller, renommer ou trier ce filtre, car il est associé à la fonctionnalité Descendre dans la hiérarchie des visuels. Ils ne peuvent pas non plus modifier ce filtre, car il provient de la fonctionnalité Descendre dans la hiérarchie dans un autre visuel. Pour supprimer le filtre Descendre dans la hiérarchie, vous cliquez sur le bouton Monter dans la hiérarchie dans le visuel qui transmet le filtre.

## <a name="drillthrough-filters"></a>Filtres d'extraction

Les filtres d’extraction sont transmis d’une page à l’autre par le biais de la fonctionnalité d’extraction. Ils s’affichent dans le volet d’extraction. Il existe deux types de filtres d’extraction. Le premier type est celui qui appelle l’extraction. Les éditeurs de rapport peuvent modifier, supprimer, effacer, masquer ou verrouiller ce type de filtre. Le deuxième type est le filtre d’extraction qui est passé à la cible, en fonction des filtres au niveau de la page de la page source. Les éditeurs de rapport peuvent modifier, supprimer ou effacer ce type de filtre d’extraction temporaire. Ils ne peuvent pas verrouiller ou masquer ce filtre pour les utilisateurs finaux.

## <a name="url-filters"></a>Filtres d’URL

Les filtres d’URL sont ajoutés au nouveau volet via l’ajout d’un paramètre de requête URL. Les utilisateurs avec l’autorisation d’édition pour le rapport peuvent modifier, supprimer ou effacer le filtre dans le nouveau volet. Ils ne peuvent pas masquer, verrouiller, renommer ou trier ce filtre, car il est associé au paramètre d’URL. Pour supprimer le filtre, vous supprimez le paramètre de l’URL. Voici un exemple d’URL avec un paramètre :

app.powerbi.com/groups/me/apps/*app-id*/reports/*report-id*/ReportSection?filter=Stores~2FStatus%20eq%20'Off'

![Filtre d’URL](media/power-bi-report-filter-types/power-bi-filter-url.png)

En savoir plus sur [filtres d’URL](../collaborate-share/service-url-filters.md).

## <a name="pass-through-filters"></a>Filtres directs

Les filtres directs sont des filtres au niveau du visuel créés par l’intermédiaire des sessions de questions/réponses. Les auteurs peuvent supprimer, masquer ou trier ces filtres dans le nouveau volet. Toutefois, ils ne peuvent pas renommer, modifier, effacer ou verrouiller ces filtres.

![Filtre direct avec Questions et réponses](media/power-bi-report-filter-types/power-bi-filters-qna.png)

## <a name="comparing-filter-types"></a>Comparaison des types de filtres

Le tableau ci-dessous compare ce que les auteurs peuvent faire avec les différents types de filtres.

| Type de filtre | Modifier | Effacer | Supprimer | Masquer | Verrouiller | Trier | Renommer |
|----|----|----|----|----|----|----|----|
| Filtres manuels | Y | Y | Y | Y | Y | Y | Y |
| Filtres automatiques | Y | Y | N | Y | Y | Y | Y |
| Filtres Inclure/Exclure | N | N | Y | Y | Y | Y | N |
| Filtres Descendre dans la hiérarchie | Y | Y | N | N | N | N | N |
| Filtres d’extraction croisée | N | N | N | N | N | N | N |
| Filtres d’extraction (invoquent l’extraction) | Y | Y | Y | Y | Y | N | N |
| Filtres d’extraction (temporaires) | Y | Y | Y | N | N | N | N |
| Filtres d’URL - Temporaires | Y | Y | Y | N | N | N | N |
| Filtres directs | N | N | Y | Y | N | Y | N |



## <a name="next-steps"></a>Étapes suivantes

[Ajouter des filtres aux rapports](power-bi-report-add-filter.md)

[Découvrir le volet Filtres du rapport](../consumer/end-user-report-filter.md)

[Filtres et mise en évidence dans les rapports](power-bi-reports-filters-and-highlighting.md)

D’autres questions ? [Posez vos questions à la communauté Power BI](https://community.powerbi.com/)
