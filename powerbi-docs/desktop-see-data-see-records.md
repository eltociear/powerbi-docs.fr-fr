---
title: Afficher les données et les enregistrements dans les visuels Power BI Desktop
description: Fonctionnalités Afficher les données et Afficher les enregistrements de Power BI Desktop pour une exploration approfondie
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 02/22/2018
ms.author: davidi
LocalizationGroup: Learn more
ms.openlocfilehash: 219687e7e5a98cecdaaa5d17291fc0841a4b165f
ms.sourcegitcommit: 2a7bbb1fa24a49d2278a90cb0c4be543d7267bda
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "34285735"
---
# <a name="use-see-data-and-see-records-in-power-bi-desktop"></a>Utiliser Afficher les données et Afficher les enregistrements dans Power BI Desktop
Dans **Power BI Desktop**, vous pouvez explorer les détails d’une visualisation et consulter des représentations textuelles des données sous-jacentes ou enregistrements de données individuelles du visuel sélectionné. Ces fonctionnalités sont parfois appelées *interactif*, *extraction* ou *extraction jusqu’aux détails*.

Vous pouvez utiliser **Consulter les données** pour afficher une version textuelle des valeurs utilisées par la visualisation sélectionnée ou utiliser **Consulter les enregistrements** pour afficher toutes les données d’un enregistrement ou d’un point de données sélectionné. 

![Consulter les données et Consulter les enregistrements](media/desktop-see-data-see-records/see-data-record.png)

>[!IMPORTANT]
>**Consulter les données** et **Consulter les enregistrements** prennent en charge uniquement les types de visualisation suivants :
>  - Graphique à barres
>  - Histogramme
>  - Graphique en anneau
>  - Carte choroplèthe
>  - Entonnoir
>  - Carte
>  - Graphique en secteurs
>  - Treemap

## <a name="use-see-data-in-power-bi-desktop"></a>Utiliser Consulter les données dans Power BI Desktop

**Consulter les données** vous montre les données sous-jacentes d’une visualisation. **Consulter les données** s’affiche dans l’onglet **Données / Explorer** dans la section **Outils visuels** du ruban lorsqu’une visualisation est sélectionnée.

![Consulter les données dans le ruban](media/desktop-see-data-see-records/see-data1.png)

Vous pouvez également consulter les données en cliquant avec le bouton de droite sur une visualisation, puis en sélectionnant **Afficher les données** dans le menu qui s’affiche ; ou en sélectionnant les points de suspension (...) **Plus d’options** dans le coin supérieur droit d’une visualisation, puis en sélectionnant **Afficher les données**.

![Cliquez avec le bouton de droite sur Afficher les données](media/desktop-see-data-see-records/see-data2.png)&nbsp;&nbsp;![Afficher des données Plus d’options](media/desktop-see-data-see-records/see-data3.png)

> [!NOTE]
> Vous devez pointer la souris sur un point de données du visuel pour que le menu contextuel soit disponible.

Lorsque vous sélectionnez **Consulter les données** ou **Afficher les données**, le canevas de Power BI Desktop affiche en même temps le visuel et la représentation textuelle des données. Dans *l’affichage horizontal*, le visuel est affiché dans la moitié supérieure du canevas et les données s’affichent dans la moitié inférieure. 

![affichage horizontal](media/desktop-see-data-see-records/see-data4a.png)

Vous pouvez également basculer vers un affichage horizontal ou un *affichage vertical* en sélectionnant l’icône dans l’angle supérieur droit du canevas.

![activez/désactivez l’affichage vertical](media/desktop-see-data-see-records/see-data4.png)

Pour revenir au rapport, sélectionnez **< Retour au rapport** dans l’angle supérieur gauche du canevas.

![Retour au rapport](media/desktop-see-data-see-records/see-data5.png)

## <a name="use-see-records-in-power-bi-desktop"></a>Utiliser Consulter les enregistrements dans Power BI Desktop

Vous pouvez également vous concentrer sur un enregistrement de données et explorer les données qui se trouvent derrière. Pour utiliser **Consulter les enregistrements**, sélectionnez une visualisation, puis sélectionnez **Consulter les enregistrements** dans l’onglet **Données/Exploration** dans la section **Outils du visuel** du ruban, puis sélectionnez un point de données ou une ligne sur la visualisation. 

![Consulter les enregistrements dans le ruban](media/desktop-see-data-see-records/see-record1.png)

> [!NOTE]
> Si le bouton **Consulter les enregistrements** du ruban est désactivé et grisé, cela signifie que la visualisation sélectionnée ne prend pas en charge **Consulter les enregistrements**.

Vous pouvez également cliquez avec le bouton de droite sur un élément de données et sélectionnez **Consulter les enregistrements** dans le menu qui s’affiche.

![Consulter les enregistrements en cliquant avec le bouton de droite](media/desktop-see-data-see-records/see-record2.png)

Lorsque vous sélectionnez **Consulter les enregistrements** pour un élément de données, le canevas de Power BI Desktop affiche toutes les données associées à l’élément sélectionné. 

![](media/desktop-see-data-see-records/see-record3.png)

Pour revenir au rapport, sélectionnez **< Retour au rapport** dans l’angle supérieur gauche du canevas.

![](media/desktop-see-data-see-records/see-record4.png)

> [!NOTE]
>**Consulter les enregistrements** présente les limitations suivantes :
> - Vous ne pouvez pas modifier les données dans l’affichage **Consulter les enregistrements** et les enregistrer à nouveau dans le rapport.
> - Vous ne pouvez pas utiliser **Afficher les enregistrements** lorsque votre visuel utilise une mesure calculée.
> - Vous ne pouvez pas utiliser **Consulter les enregistrements** quand vous êtes connecté à un modèle MD (multidimensionnel) en direct.

## <a name="next-steps"></a>Étapes suivantes
Il existe toutes sortes de fonctionnalités de mise en forme de rapports et de gestion des données dans **Power BI Desktop**. Consultez les ressources suivantes pour voir quelques exemples :

* [Utiliser le regroupement et le compartimentage dans Power BI Desktop](desktop-grouping-and-binning.md)
* [Utiliser le quadrillage, l’alignement sur la grille, l’ordre de plan, l’alignement et la distribution dans les rapports Power BI Desktop](desktop-gridlines-snap-to-grid.md)

