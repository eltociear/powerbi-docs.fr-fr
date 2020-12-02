---
title: Utiliser un segment ou un filtre de date relative dans Power BI
description: Découvrez comment utiliser un segment ou un filtre pour limiter les plages de dates relatives dans Power BI.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: rien
ms.service: powerbi
ms.subservice: pbi-visuals
ms.topic: how-to
ms.date: 09/09/2020
LocalizationGroup: Create reports
ms.openlocfilehash: 8d83a2b655c7a4dd788e34ce5744daaac0f73f63
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96397438"
---
# <a name="creating-a-relative-date-slicer-and-filter-in-power-bi"></a>Création d’un segment et d’un filtre de date relative dans Power BI

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]

Un **segment de date relative** ou un **filtre de date relative** permet d’appliquer des filtres basés sur le temps à n’importe quelle colonne de date dans votre modèle de données. Par exemple, vous pouvez utiliser le **segment de date relative** pour afficher uniquement les données de vente produites durant les 30 derniers jours (ou mois, mois calendaires, etc.). Quand vous actualisez les données, la période relative applique automatiquement la contrainte de date relative appropriée.

![Capture d’écran d’un rapport sur lequel une flèche pointe vers un segment de date relative](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-01.png)

Pour que vous puissiez partager votre rapport avec un collègue Power BI, il faut que vous disposiez tous deux de licences individuelles Power BI Pro ou que le rapport soit enregistré dans une capacité Premium.

## <a name="create-the-relative-date-range-slicer"></a>Création du segment de plage de dates relatives

Vous pouvez utiliser le segment de date relative comme tout autre segment. Créez un visuel de **segment** pour votre rapport, puis sélectionnez une valeur de date pour **Champ**. Dans l’image suivante, nous avons sélectionné le champ *OrderDate*.

![Capture d’écran du volet Visualisations avec des flèches pointant vers l’icône du visuel de segment et vers la zone Champ.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-02.png)

Sélectionnez le segment sur votre canevas, puis sur le caret dans le coin supérieur droit du visuel de segment. Si le visuel comporte des données de date, le menu présente l’option **Relatif**.

![Capture d’écran du visuel de segment avec le caret mis en évidence et une flèche pointant vers Relatif.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-03.png)

Pour le segment de date relative, sélectionnez *Relatif*.

Vous pouvez ensuite sélectionner les paramètres.

Pour le premier paramètre du *segment de date relative*, vos choix sont les suivants :

![Capture d’écran des options de configuration Relatif avec le premier paramètre mis en évidence.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-04.png)

* Dernier
* Suivant
* This

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

Si vous sélectionnez **Mois** dans cette liste et entrez *2* dans le paramètre du milieu, voici ce qui se produit :

* Si la date du jour est le 20 juillet :

    - Les données incluses dans les visuels limités par le segment affichent les données des deux mois précédents,
    - À partir du 21 mai jusqu’au 20 juillet (date d’aujourd’hui).

En comparaison, si vous sélectionnez *Mois (calendaires)* , les visuels limités affichent les données du 1er mai jusqu’au 30 juin (les deux derniers mois calendaires complets).

## <a name="create-the-relative-date-range-filter"></a>Création du filtre de plage de dates relatives

Vous pouvez aussi créer un filtre de plage de dates relatives pour la page de votre rapport ou pour l’intégralité de votre rapport. Pour cela, faites glisser un champ de date dans la zone **Filtres au niveau de la page** ou **Filtres au niveau du rapport** dans le volet **Champ**.

![Capture d’écran montrant le déplacement du champ OrderDate vers la zone Filtres au niveau de la page.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-06.png)

Une fois cette opération effectuée, vous pouvez changer la plage de dates relatives. Pour cela, effectuez les mêmes étapes que pour personnaliser le **segment de date relative**. Sélectionnez **Filtrage de date relative** dans la liste déroulante **Type de filtre**.

![Capture d’écran montrant la liste déroulante Type de filtre et le pointeur de la souris sur Filtrage de date relative.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-07.png)

Une fois **Filtrage de date relative** sélectionné, trois sections à modifier apparaissent, notamment une zone numérique intermédiaire, comme pour le segment.

![Capture d’écran de Filtres au niveau du rapport avec des flèches pointant vers les options Afficher les éléments quand la valeur.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-08.png)

## <a name="limitations-and-considerations"></a>Considérations et limitations

Les considérations et limitations suivantes s’appliquent actuellement à l’utilisation du **segment et du filtre de plage de dates relatives**.

* Le type de données pour le champ dans le segment doit être une date et non le texte par défaut. Si ce n’est pas le cas, les options associées ne s’affichent pas dans le segment.
* Les modèles de données dans **Power BI** n’incluent pas les informations de fuseau horaire. Ces modèles peuvent stocker des heures, mais sans indication de leur fuseau horaire.
* Le segment et le filtre sont toujours basés sur l’heure UTC (temps universel coordonné). Si vous définissez un filtre dans un rapport et que vous l’envoyez à un collègue qui se trouve dans un autre fuseau horaire, vous voyez tous les deux les mêmes données. Sauf si vous vous situez dans le fuseau horaire UTC, votre collègue et vous devez tenir compte du décalage temporel que vous rencontrez.
* Vous pouvez convertir à l’heure UTC les données capturées dans un fuseau horaire local en utilisant l’**Éditeur de requête**.

## <a name="next-steps"></a>Étapes suivantes

- [Utilisation d’un segment et d’un filtre d’heure relative dans Power BI](../create-reports/slicer-filter-relative-time.md)
- [Segments dans Power BI](power-bi-visualization-slicers.md)
