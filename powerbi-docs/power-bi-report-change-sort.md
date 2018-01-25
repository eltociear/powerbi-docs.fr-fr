---
title: "Modifier le mode tri d’un graphique dans un rapport Power BI"
description: "Modifier le mode tri d’un graphique dans un rapport Power BI"
services: powerbi
documentationcenter: 
author: mihart
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
ms.date: 01/20/2018
ms.author: mihart
ms.openlocfilehash: aeb22c23b0ef22afd44592c1ceb90537878042d9
ms.sourcegitcommit: 2ae323fbed440c75847dc55fb3e21e9c744cfba0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2018
---
# <a name="change-how-a-chart-is-sorted-in-a-power-bi-report"></a>Modifier le mode tri d’un graphique dans un rapport Power BI
Dans un rapport Power BI, vous pouvez trier la plupart des visualisations par ordre alphabétique en fonction des noms de catégories du graphique ou des valeurs numériques de chaque catégorie. Par exemple, ce graphique est trié par nom de magasin.

![](media/power-bi-report-change-sort/pbi_chartsortcategory.png)

Il est facile de passer du tri par catégorie (nom de magasin) au tri par valeur (ventes par mètres carrés).

1. Sélectionnez les points de suspension (...) et choisissez **Trier par Sales Per Sq Ft** (Ventes par m²).
2. Si nécessaire, sélectionnez l’icône de tri ![](media/power-bi-report-change-sort/sorticon.png) pour passer à un tri **Décroissant**.

   ![](media/power-bi-report-change-sort/sortby.gif)

   **REMARQUE**: certains éléments visuels ne peuvent pas être triés.  C’est le cas, par exemple, des visuels suivants : Treemap, Carte géographique, Carte choroplèthe, Nuage de points, Jauge, Carte, Carte de plusieurs ligne, Cascade.

<a name="other"></a>
## <a name="sorting-using-other-criteria"></a>Tri à l’aide d’autres critères
Il peut parfois être utile de trier un visuel selon un autre champ ou d’autres critères.  Par exemple, vous pouvez être amené à effectuer un tri par mois (et non par ordre alphabétique) ou bien un tri par nombres entiers plutôt qu’un tri par chiffre (0, 1, 9, 20 et non 0, 1, 20, 9).  

Dans certains cas, vous pouvez trier le visuel de la manière souhaitée, par exemple, par mois.  Si ce n’est pas possible, ce peut être parce que le jeu de données sous-jacent au rapport a besoin de quelques ajustements. Plusieurs solutions s’offrent à vous :

* Dans Power BI Desktop, [utilisez l’onglet Modélisation des outils de données pour trier par une autre colonne](desktop-sort-by-column.md).
* Dans Excel, si vous êtes le propriétaire du jeu de données, ajoutez une nouvelle colonne qui concatène le nom et le numéro du mois. Ensuite, actualisez ou réimportez le jeu de données pour afficher la nouvelle colonne dans la zone Champs.
* Dans Excel, vérifiez que vos colonnes numériques sont marquées au format « nombre entier » ou « décimal », et non au format « texte ».

## <a name="next-steps"></a>Étapes suivantes
En savoir plus sur les [visualisations dans les rapports Power BI](power-bi-report-visualizations.md).

[Power BI – Concepts de base](service-basic-concepts.md)

D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)
