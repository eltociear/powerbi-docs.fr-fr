---
title: Trucs et astuces pour la mise en forme des couleurs dans Power BI
description: Trucs et astuces pour la mise en forme des couleurs dans Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/09/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 71ed70344281dec3353b73c8698594d62ef32eae
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/15/2019
ms.locfileid: "54285596"
---
# <a name="tips-and-tricks-for-color-formatting-in-power-bi"></a>Trucs et astuces pour la mise en forme des couleurs dans Power BI
Power BI vous propose de nombreuses façons de personnaliser vos tableaux de bord et vos rapports. Cet article fournit des astuces pour rendre vos visualisations Power BI plus attrayantes, plus intéressantes et mieux adaptées à vos besoins.

Ces astuces sont répertoriées ci-dessous. Vous en avez une autre à proposer ? Excellent ! Envoyez-la nous et nous verrons si nous pouvons l’ajouter à notre liste.

* Modifier la couleur d’un seul point de données
* Baser les couleurs du graphique sur une valeur numérique
* Baser la couleur des points de données sur une valeur de champ
* Personnaliser les couleurs de l’échelle de couleurs
* Utiliser des échelles de couleurs divergentes
* Comment annuler dans Power BI

Pour apporter des modifications, vous devez modifiez un rapport. Ouvrez le rapport, puis sélectionnez **Modifier le rapport** à partir de la zone de menu supérieur, comme illustré dans l’image suivante.

![](media/service-tips-and-tricks-for-color-formatting/power-bi-edit.png)

Quand le volet **Visualisations** s’affiche à droite du canevas de **rapport** , vous pouvez commencer la personnalisation. Si le volet n’apparaît pas, sélectionnez la flèche, à partir de l’angle supérieur droit, pour l’ouvrir.

![](media/service-tips-and-tricks-for-color-formatting/power-bi-formatting-pane.png)

## <a name="change-the-color-of-a-single-data-point"></a>Modifier la couleur d’un seul point de données
Parfois, il peut être nécessaire de mettre en évidence un point de données particulier. Il peut s’agir de chiffres de ventes pour le lancement d’un nouveau produit ou de l’amélioration de la qualité après le lancement d’un nouveau programme. Avec Power BI, vous pouvez mettre en évidence un point de données spécifique en modifiant sa couleur.

La visualisation suivante classe les unités vendues par segment de produit. 

![](media/service-tips-and-tricks-for-color-formatting/power-bi-grey.png)

Maintenant imaginez que vous souhaitez appeler le segment **Convenience** pour afficher les performances de ce tout nouveau segment, à l’aide de la couleur. Voici les étapes à suivre :

Développez la section **Couleurs des données** et activez le curseur pour **Tout afficher**. Cela affiche les couleurs de chaque élément de données de la visualisation. Quand vous pointez sur les points de données, le défilement est activé pour vous permettre de les modifier.

![](media/service-tips-and-tricks-for-color-formatting/power-bi-show-all.png)

Définissez **Convenience** sur la couleur orange. 

![](media/service-tips-and-tricks-for-color-formatting/power-bi-orange.png)

Une fois sélectionné, le point de données **Convenience** se distingue facilement par sa couleur orange.

Même si vous modifiez les types de visualisations, puis revenez, Power BI se souvient de votre sélection et conserve la couleur orange pour **Convenience**.

Vous pouvez modifier la couleur d’un point de données pour un, plusieurs ou tous les éléments de données dans la visualisation. Vous pouvez choisir que votre élément visuel imite les couleurs de votre entreprise. 

![](media/service-tips-and-tricks-for-color-formatting/power-bi-corporate.png)

Vous pouvez réaliser toutes sortes de choses avec les couleurs. Dans la section suivante, nous parlerons des dégradés.

## <a name="base-the-colors-of-a-chart-on-a-numeric-value"></a>Baser les couleurs du graphique sur une valeur numérique
Il est souvent utile de définir les couleurs d’un graphique de façon dynamique, en fonction de la valeur numérique d’un champ. Cela vous permet, par exemple, d’afficher une valeur différente pour la taille d’une barre, ou d’afficher deux valeurs sur un même graphique. Vous pouvez également utiliser cette méthode pour mettre en évidence des points de données supérieurs (ou inférieurs) à une certaine valeur (par exemple, en mettant en surbrillance les régions à faible rentabilité).

Les sections suivantes présentent différentes manières de baser les couleurs sur une valeur numérique.

## <a name="base-the-color-of-data-points-on-a-value"></a>Baser la couleur des points de données sur une valeur
Pour modifier la couleur en fonction d’une valeur, faites glisser le champ sur lequel vous voulez baser les couleurs dans la zone **Saturation de la couleur** du volet **Champs**. Dans l’image suivante, **%Market Share SPLY YTD** a été déplacé dans la zone **Saturation de la couleur**. 

![](media/service-tips-and-tricks-for-color-formatting/power-bi-color-saturation.png)

Et dans le volet Mise en forme, sous **Couleurs des données**, déterminez comment la valeur **%Market Share SPLY YTD** modifiera la couleur et l’ombrage de votre graphique à colonnes. Dans cet exemple, une valeur %Market Share inférieure sera en bleu clair et une valeur plus élevée sera en bleu foncé.


![](media/service-tips-and-tricks-for-color-formatting/power-bi-data-colors2.png)


Comme vous pouvez le voir, bien que nous ayons vendu plus d’unités des deux catégories **Productivity** et **Extreme** (leurs colonnes sont plus haut), la catégorie **Moderation** possède une valeur **%Market Share SPLY YTD** plus élevée (sa couleur de colonne est plus foncée).

![](media/service-tips-and-tricks-for-color-formatting/power-bi-saturation.png)

## <a name="customize-the-colors-used-in-the-color-scale"></a>Personnaliser les couleurs de l’échelle de couleurs
Vous pouvez personnaliser les couleurs de l’échelle de couleurs. Par défaut, la valeur la moins élevée de vos données est mappée sur la couleur la moins saturée (la plus claire) et la valeur la plus élevée est mappée sur la couleur la plus saturée (la plus foncée). Dans l’image ci-dessus, nous avons utilisé un dégradé de bleu. 

Développez **Couleurs des données** pour afficher le dégradé de couleurs utilisé pour visualiser vos données. La plage de couleurs est indiquée dans la barre de dégradé qui affiche le spectre de la valeur **Minimum** à la valeur **Maximum**. La valeur **Minimum** se trouve à gauche et la valeur **Maximum** se trouve à droite.

![](media/service-tips-and-tricks-for-color-formatting/power-bi-data-colors2.png)


Pour modifier l’échelle de manière à utiliser une autre plage de couleurs, sélectionnez la liste déroulante en regard de **Minimum** ou **Maximum**, puis sélectionnez une couleur. L’illustration suivante montre l’attribution de la couleur noir à la valeur **Maximum** et la barre de dégradé montrant le nouveau spectre des couleurs entre les valeurs **Minimum** et **Maximum**.

![](media/service-tips-and-tricks-for-color-formatting/tipstrickscolor_11.png)

Vous pouvez également modifier la façon dont les valeurs sont mappées aux couleurs. Dans l’image suivante, les couleurs des valeurs **Minimum** et **Maximum** sont définies respectivement sur orange et vert.

Dans cette première image, notez comment les barres du graphique reflètent le dégradé. La valeur la plus élevée est verte, la plus basse est orange, et chacune des barres situées entre ces deux extrêmes possède une nuance du spectre allant du vert à l’orange.

![](media/service-tips-and-tricks-for-color-formatting/tipstrickscolor_12.png)

Voyons maintenant ce qui se passe quand nous définissons des valeurs numériques dans les zones des valeurs **Minimum** et **Maximum** situées sous les sélecteurs de couleurs **Minimum** et **Maximum** (illustrés dans l’image suivante). Nous allons définir **Minimum** sur 20 000 000 et **Maximum** sur 20 000 001.

Quand nous définissons ces valeurs, le dégradé n’est plus appliqué aux valeurs du graphique qui sont inférieures à la valeur **Minimum** ou supérieures à la valeur **Maximum**. Toute barre ayant une valeur supérieure à la valeur **Maximum** est de couleur verte et toute barre dont la valeur est inférieure à la valeur **Minimum** est de couleur rouge.

![](media/service-tips-and-tricks-for-color-formatting/tipstrickscolor_13.png)

## <a name="use-diverging-color-scales"></a>Utiliser des échelles de couleurs divergentes
Parfois, vos données peuvent avoir une échelle naturellement divergente. Par exemple, une plage de températures dispose d’un centre naturel qui correspond au point de congélation et un score de rentabilité possède un milieu naturel (zéro).

Pour utiliser des échelles de couleurs divergentes, faites glisser le curseur **Divergent** vers **Activé**. Quand **Divergent** est activé, un autre sélecteur de couleurs et une autre zone de valeur (tous deux appelés **Centre**), s’affichent, comme indiqué dans l’image suivante.

![](media/service-tips-and-tricks-for-color-formatting/tipstrickscolor_14.png)

Quand le curseur **Divergent** est activé, vous pouvez définir séparément les couleurs des valeurs **Minimum**, **Maximum** et **Centre**. Dans l’image suivante, **Centre** est défini sur 1. Par conséquent, les barres dont la valeur est supérieure à 1 seront d’une nuance de vert et les barres dont la valeur est inférieure à 1 seront d’une nuance de rouge.

## <a name="how-to-undo-in-power-bi"></a>Comment annuler dans Power BI
Comme de nombreux autres services et logiciels Microsoft, Power BI permet d’annuler facilement la dernière commande. Par exemple, supposons que vous ayez modifié la couleur d’un point de données ou d’une série de points de données, et que vous n’aimiez pas la couleur une fois que vous la voyez dans la visualisation. Vous voulez rétablir la couleur précédente, mais vous ne vous souvenez pas exactement de quelle couleur il s’agissait.

Pour **Annuler** votre dernière action ou les quelques actions précédentes, procédez comme suit :

- Tapez CTRL + Z

## <a name="feedback"></a>Commentaires
Vous avez une astuce que vous aimeriez partager ? Envoyez-la nous et nous verrons si nous pouvons l’inclure dans notre rubrique.

>[!NOTE]
>Les personnalisations des couleurs, des axes et autres qui sont disponibles quand l’icône **Format** est sélectionnée sont également disponibles dans Power BI Desktop.

## <a name="next-steps"></a>Étapes suivantes
[Prise en main de la mise en forme des couleurs et des propriétés d’axe](service-getting-started-with-color-formatting-and-axis-properties.md)

