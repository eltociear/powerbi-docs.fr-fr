---
title: Utiliser un segment ou un filtre de date relative dans Power BI
description: Découvrez comment utiliser un segment ou un filtre pour limiter les plages de dates relatives dans Power BI.
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/06/2020
ms.author: mihart
LocalizationGroup: Create reports
ms.openlocfilehash: 9ce36bfa61b16bd30e59bc8491af80efdfdc8a35
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "81006782"
---
# <a name="use-a-relative-date-slicer-and-filter-in-power-bi"></a>Utiliser un segment et un filtre de date relative dans Power BI

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

Un **segment de date relative** ou un **filtre de date relative** permet d’appliquer des filtres basés sur le temps à n’importe quelle colonne de date dans votre modèle de données. Par exemple, vous pouvez utiliser le **segment de date relative** pour afficher uniquement les données de vente produites durant les 30 derniers jours (ou mois, mois calendaires, etc.). Quand vous actualisez les données, la période relative applique automatiquement la contrainte de date relative appropriée.

![Capture d’écran d’un rapport avec une flèche pointant vers un segment de date relative.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-01.png)

## <a name="use-the-relative-date-range-slicer"></a>Utiliser le segment de plage de dates relatives

Vous pouvez utiliser le segment de date relative comme tout autre segment. Créez un visuel de **segment** pour votre rapport, puis sélectionnez une valeur de date pour **Champ**. Dans l’image suivante, nous avons sélectionné le champ *OrderDate*.

![Capture d’écran du volet Visualisations avec des flèches pointant vers l’icône du visuel de segment et vers la zone Champ.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-02.png)

Sélectionnez le segment sur votre canevas, puis sur le caret dans le coin supérieur droit du visuel de segment. Si le visuel a des données de date, le menu affiche l’option pour **Relatif**.

![Capture d’écran du visuel de segment avec le caret mis en évidence et une flèche pointant vers Relatif.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-03.png)

Pour le segment de date relative, sélectionnez *Relatif*.

Vous pouvez ensuite sélectionner les paramètres.

Pour le premier paramètre du *segment de date relative*, vos choix sont les suivants :

![Capture d’écran des options de configuration Relatif avec le premier paramètre mis en évidence.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-04.png)

* Last

* Suivant

* Ce

Le deuxième paramètre (milieu) du *segment de date relative* vous permet d’entrer un nombre pour définir la plage de dates relatives.

![Capture d’écran des options de configuration Relatif avec le deuxième paramètre mis en évidence.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-04a.png)

Le troisième paramètre vous permet de choisir la mesure de la date. Vos choix sont les suivants :

![Capture d’écran des options de configuration Relatif avec le troisième paramètre mis en évidence.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-05.png)

* Jours

* Semaines

* Semaines (calendaires)

* Mois

* Mois (calendaires)

* Années

* Années (civiles)

Si vous sélectionnez **Mois** dans cette liste et entrez *2* dans le paramètre du milieu, voilà ce qui se passe :

* Si nous sommes le 20 juillet,

* les données incluses dans les visuels limités par le segment affichent les données des deux mois précédents,

* à partir du 21 mai jusqu’au 20 juillet (date d’aujourd’hui).

En comparaison, si vous sélectionnez *Mois (calendaires)* , les visuels limités affichent les données du 1er mai jusqu’au 30 juin (les deux derniers mois calendaires complets).

## <a name="using-the-relative-date-range-filter"></a>Utilisation du filtre de plage de dates relatives

Vous pouvez aussi créer un filtre de plage de dates relatives pour la page de votre rapport ou pour l’intégralité de votre rapport. Pour cela, faites glisser un champ de date dans la zone **Filtres au niveau de la page** ou **Filtres au niveau du rapport** dans le volet **Champ**.

![Capture d’écran montrant le déplacement du champ OrderDate vers la zone Filtres au niveau de la page.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-06.png)

Une fois cette opération effectuée, vous pouvez changer la plage de dates relatives. Pour cela, effectuez les mêmes étapes que pour personnaliser le **segment de date relative**. Sélectionnez **Filtrage de date relative** dans la liste déroulante **Type de filtre**.

![Capture d’écran montrant la liste déroulante Type de filtre et le pointeur de la souris sur Filtrage de date relative.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-07.png)

Une fois **Filtrage de date relative** sélectionné, trois sections à modifier apparaissent, notamment une zone numérique intermédiaire, comme pour le segment.

![Capture d’écran de Filtres au niveau du rapport avec des flèches pointant vers les options Afficher les éléments quand la valeur.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-08.png)

## <a name="limitations-and-considerations"></a>Considérations et limitations

Les considérations et limitations suivantes s’appliquent actuellement à l’utilisation du **segment et du filtre de plage de dates relatives**.

* Les modèles de données dans **Power BI** n’incluent pas les informations de fuseau horaire. Ces modèles peuvent stocker des heures, mais sans indication de leur fuseau horaire.

* Le segment et le filtre sont toujours basés sur l’heure UTC (temps universel coordonné). Si vous définissez un filtre dans un rapport et que vous l’envoyez à un collègue dans un autre fuseau horaire, vous voyez tous les deux les mêmes données. Sauf si vous vous trouvez dans le fuseau horaire UTC, vous et votre collègue devez tenir compte du décalage de temps que vous allez rencontrer.

* Vous pouvez convertir à l’heure UTC les données capturées dans un fuseau horaire local en utilisant l’**Éditeur de requête**.

## <a name="next-steps"></a>Étapes suivantes

Découvrez comment [utiliser le regroupement et le compartimentage dans Power BI Desktop](../desktop-grouping-and-binning.md).
