---
title: "Afficher les données et les enregistrements dans les visuels Power BI Desktop"
description: "Fonctionnalités Afficher les données et Afficher les enregistrements de Power BI Desktop pour une exploration approfondie"
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/09/2017
ms.author: davidi
ms.openlocfilehash: c43ec48d1bd34a5df2578c6cc117dd3e3bbdb64f
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2017
---
# <a name="use-see-data-and-see-records-in-power-bi-desktop"></a>Utiliser Afficher les données et Afficher les enregistrements dans Power BI Desktop
Dans **Power BI Desktop**, vous pouvez explorer les détails de n’importe quel visuel et afficher une représentation textuelle des données ou éléments de données du visuel sélectionné. Ces fonctionnalités sont parfois appelées *clic*, *extraction* ou *extraction des détails*.

Vous pouvez utiliser **Afficher les enregistrements** pour afficher les lignes sous-jacentes d’un élément de données sélectionné à partir d’un visuel ou **Afficher les données** pour afficher une version textuelle des valeurs utilisées dans le visuel. Il existe certaines limitations à l’utilisation des fonctionnalités **Afficher les données** et **Afficher les enregistrements**, qui sont présentées à la fin de cet article.

![](media/desktop-see-data-see-records/see-data-see-records_1.png)

## <a name="using-see-data-in-power-bi-desktop"></a>Utiliser Afficher les données dans Power BI Desktop
Le bouton **Afficher les données** se trouve dans l’onglet **Données / Explorer** dans la section **Outils d’élément visuel** du ruban.

![](media/desktop-see-data-see-records/see-data-see-records_2.png)

Vous pouvez également **afficher les données** en cliquant avec le bouton droit sur un visuel, puis en sélectionnant **Afficher les données** dans le menu qui s’affiche.

![](media/desktop-see-data-see-records/see-data-see-records_3.png)

> [!NOTE]
> Vous devez pointer la souris sur un point de données du visuel pour que le menu contextuel soit disponible.
> 
> 

Lorsque vous sélectionnez **Afficher les données**, **Power BI Desktop** se concentre sur le visuel et les données que vous avez sélectionnés et réserve l’espace du canevas à l’affichage du visuel et de la représentation textuelle des données. Le visuel est affiché sur la moitié supérieure du canevas et les données s’affichent dans la moitié inférieure, comme illustré dans l’image suivante. Il s’agit de la vue *horizontale*.

![](media/desktop-see-data-see-records/see-data-see-records_4.png)

Vous pouvez également basculer vers une *vue verticale* (ou revenir à la *vue horizontale*), en sélectionnant l’icône dans l’angle supérieur droit.

![](media/desktop-see-data-see-records/see-data-see-records_5.png)

Pour revenir au rapport, sélectionnez **< Retour au rapport** dans l’angle supérieur gauche du canevas.

![](media/desktop-see-data-see-records/see-data-see-records_6.png)

## <a name="using-see-records-in-power-bi-desktop"></a>Utiliser Afficher les enregistrements dans Power BI Desktop
Vous pouvez également vous concentrer sur un élément de données d’un visuel et explorer les données sous-jacentes. Une fois que le visuel est sélectionné, il existe deux façons d’utiliser **Afficher les enregistrements**. Activez le bouton bascule **Afficher les enregistrements** dans le ruban **Données / Explorer**, puis cliquez sur un élément de données. Ou cliquez avec le bouton droit sur un élément de données, puis sélectionnez **Afficher les enregistrements** dans le menu qui s’affiche.

![](media/desktop-see-data-see-records/see-data-see-records_7.png)

> [!NOTE]
> Si le visuel sélectionné ne prend pas en charge **Afficher les enregistrements**, le bouton du ruban est grisé.
> 
> 

Une fois que **Afficher les enregistrements** est sélectionné, **Power BI Desktop** se concentre sur cet élément de données et consacre la zone du canevas à l’affichage des données de cet élément, comme indiqué dans l’image suivante.

![](media/desktop-see-data-see-records/see-data-see-records_8.png)

Pour revenir au rapport, sélectionnez le bouton **Retour au rapport** dans l’angle supérieur gauche du canevas.

## <a name="limitations"></a>Limites
Il existe quelques limitations à prendre en compte lors de l’utilisation des fonctionnalités **Afficher les données** ou **Afficher les enregistrements** :

* Seuls les types de visuel suivants sont pris en charge :
  * **Barres**
  * **Colonne**
  * **Carte**
  * **Compartimentages**
  * **Carte choroplèthe**
  * **Secteur**
  * **Graphique en anneau**
  * **Entonnoir**
* Vous ne pouvez pas utiliser **Afficher les enregistrements** lorsque votre visuel utilise une mesure calculée.
* Vous ne pouvez pas utiliser **Afficher les enregistrements** quand vous êtes connecté à un modèle (MD) multidimensionnel en direct.

## <a name="next-steps"></a>Étapes suivantes
Il existe toutes sortes de fonctionnalités de mise en forme de rapports et de gestion des données dans **Power BI Desktop**. Consultez les ressources suivantes pour voir quelques exemples :

* [Utiliser le regroupement et le compartimentage dans Power BI Desktop](desktop-grouping-and-binning.md)
* [Utiliser le quadrillage, l’alignement sur la grille, l’ordre de plan, l’alignement et la distribution dans les rapports Power BI Desktop](desktop-gridlines-snap-to-grid.md)

