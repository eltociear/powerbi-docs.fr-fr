---
title: Conseils et astuces pour la mise en forme dans les rapports
description: Conseils et astuces pour la mise en forme dans les rapports Power BI
author: mihart
ms.author: mihart
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: pbi-visuals
ms.topic: conceptual
ms.date: 10/29/2020
LocalizationGroup: Visualizations
ms.openlocfilehash: 0ab6b799c8c78ab2e76a63a3ec5ee3f37f960b03
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96415746"
---
# <a name="tips-and-tricks-for-formatting-in-reports"></a>Conseils et astuces pour la mise en forme dans les rapports

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]    

Power BI vous permet de personnaliser vos rapports de diverses façons. Cet article fournit des astuces pour rendre vos visualisations Power BI plus attrayantes, plus intéressantes et mieux adaptées à vos besoins.

Ces astuces sont répertoriées ci-dessous. Vous en avez une autre à proposer ? Great! Envoyez-la nous et nous verrons si nous pouvons l’ajouter à notre liste.

* Appliquer un thème à l’ensemble du rapport
* Modifier la couleur d’un seul point de données
* Mise en forme conditionnelle
* Baser les couleurs du graphique sur une valeur numérique
* Baser la couleur des points de données sur une valeur de champ
* Personnaliser les couleurs de l’échelle de couleurs
* Utiliser des échelles de couleurs divergentes
* Ajouter de la couleur aux lignes des tableaux
* Comment annuler dans Power BI

Pour apporter des changements, vous devez disposer d’autorisations de modification du rapport. Dans Power BI Desktop, ouvrez le rapport en affichage **Rapport**. Dans le service Power BI, cela signifie ouvrir le rapport et sélectionner **Modifier** dans la barre de menus, comme l’illustre l’image suivante.

![où trouver le menu Edition](media/service-tips-and-tricks-for-color-formatting/power-bi-editing-view.png)

Quand les volets **Filtres** et **Visualisations** s’affichent sur le côté droit du canevas de rapport, vous pouvez commencer la personnalisation. Si les volets ne s’affichent pas, sélectionnez la flèche située en haut à droite pour les ouvrir.

![canevas de rapport en mode Edition](media/service-tips-and-tricks-for-color-formatting/power-bi-edit-filter.png)

## <a name="apply-a-theme"></a>Appliquer un thème
Avec les thèmes de rapport, vous pouvez appliquer des changements de conception à l’ensemble de votre rapport, par exemple en utilisant les couleurs de votre entreprise, en changeant des jeux d’icônes ou en appliquant une nouvelle mise en forme visuelle par défaut. Quand vous appliquez un thème de rapport, tous les visuels du rapport utilisent les couleurs et la mise en forme du thème sélectionné. Pour en savoir plus, consultez [Utiliser les thèmes de rapport](../create-reports/desktop-report-themes.md).

![Changer l’icône de thème dans la barre de menus](media/service-tips-and-tricks-for-color-formatting/power-bi-themes.png)

Ici, nous avons appliqué le thème **Innover** au rapport Ventes et marketing.

![Thème Innover appliqué](media/service-tips-and-tricks-for-color-formatting/power-bi-theme-innovate.png)

## <a name="change-the-color-of-a-single-data-point"></a>Modifier la couleur d’un seul point de données
Parfois, il peut être nécessaire de mettre en évidence un point de données particulier. Il peut s’agir du chiffre de ventes pour le lancement d’un nouveau produit ou de l’amélioration des scores de qualité après la mise en place d’un nouveau programme. Avec Power BI, vous pouvez mettre en évidence un point de données spécifique en modifiant sa couleur.

La visualisation suivante classe les unités vendues par segment de produit. 

![Remplacer les couleurs des données par du gris](media/service-tips-and-tricks-for-color-formatting/power-bi-format.png)

Maintenant imaginez que vous souhaitez appeler le segment **Convenience** pour afficher les performances de ce tout nouveau segment, à l’aide de la couleur. Voici les étapes à suivre :

Développez la carte **Couleurs des données**, puis positionnez le curseur **Tout afficher** sur Activé. Cela affiche les couleurs de chaque élément de données de la visualisation. Vous pouvez maintenant modifier les points de données de votre choix.

![Volet Mise en forme avec Tout afficher activé](media/service-tips-and-tricks-for-color-formatting/power-bi-show-all.png)

Définissez **Convenience** sur la couleur orange. 

![Histogramme avec une colonne orange](media/service-tips-and-tricks-for-color-formatting/power-bi-one-color.png)

Une fois sélectionné, le point de données **Convenience** se distingue facilement par sa couleur orange.

Même si vous modifiez les types de visualisations, puis revenez, Power BI se souvient de votre sélection et conserve la couleur orange pour **Convenience**.

Vous pouvez modifier la couleur d’un point de données pour un, plusieurs ou tous les éléments de données dans la visualisation. Vous pouvez choisir que votre visuel imite les couleurs jaune, vert et bleu de votre entreprise. 

![graphique à barres avec des barres vertes, jaunes et bleues](media/service-tips-and-tricks-for-color-formatting/power-bi-corporate.png)

Vous pouvez réaliser toutes sortes de choses avec les couleurs. Dans la section suivante, nous parlerons de mise en forme conditionnelle.

## <a name="conditional-formatting-for-visualizations"></a>Mise en forme conditionnelle pour les visualisations
Il est souvent utile de définir les couleurs d’une visualisation de façon dynamique, en fonction de la valeur numérique d’un champ. Cela vous permet, par exemple, d’afficher une valeur différente pour la taille d’une barre, et d’afficher deux valeurs sur un même graphique. Vous pouvez également utiliser cette méthode pour mettre en évidence des points de données supérieurs (ou inférieurs) à une certaine valeur (par exemple, en mettant en surbrillance les régions à faible rentabilité).

Les sections suivantes présentent différentes manières de baser les couleurs sur une valeur numérique.

### <a name="base-the-color-of-data-points-on-a-value"></a>Baser la couleur des points de données sur une valeur
Pour changer la couleur en fonction d’une valeur, sélectionnez une visualisation pour l’activer. Ouvrez le volet Mise en forme en sélectionnant l’icône représentant un rouleau, puis choisissez la carte **Couleurs des données**. Sous **Couleur par défaut**, sélectionnez l’icône fx.  

![sélectionner l’option de mise en forme conditionnelle en cliquant sur les trois points verticaux](media/service-tips-and-tricks-for-color-formatting/power-bi-conditional.png)

Dans le volet **Couleur par défaut**, utilisez les listes déroulantes pour identifier les champs à utiliser pour la mise en forme conditionnelle. Dans cet exemple, nous avons sélectionné le champ **Sales fact** > **Total Units**. Nous avons aussi choisi le bleu clair pour **Valeur la plus basse** et le bleu foncé pour **Valeur la plus élevée**. 

![paramètres de mise en forme conditionnelle par couleur des données](media/service-tips-and-tricks-for-color-formatting/power-bi-conditional-formatting2-new.png)

![histogramme avec couleurs par défaut appliquées](media/service-tips-and-tricks-for-color-formatting/power-bi-default-colors.png)

Vous pouvez également mettre en forme la couleur du visuel à l’aide d’un champ qui ne fait pas partie du visuel. Dans l’image suivante, **%Market Share SPLY YTD** est utilisé. 

![Histogramme avec plusieurs nuances de bleu](media/service-tips-and-tricks-for-color-formatting/power-bi-conditional-colors.png)


Comme vous pouvez le voir, bien que nous ayons vendu plus d’unités des deux catégories **Productivity** (Productivité) et **Extreme** (Extrême) (leurs colonnes sont plus hautes), la catégorie **Moderation** (Modération) a une valeur **%Market Share SPLY YTD** (% de parts de marché à la même période l’an dernier/à ce jour) plus élevée (la couleur de sa colonne est plus foncée).

### <a name="customize-the-colors-used-in-the-color-scale"></a>Personnaliser les couleurs de l’échelle de couleurs
Vous pouvez également modifier la façon dont les valeurs sont mappées aux couleurs. Dans l’image suivante, les couleurs des valeurs **Minimum** et **Maximum** sont définies respectivement sur orange et vert.

Dans cette première image, notez comment les barres du graphique reflètent le dégradé. La valeur la plus élevée est verte, la plus basse est orange, et chacune des barres situées entre ces deux extrêmes possède une nuance du spectre allant du vert à l’orange.

![Histogramme présentant un dégradé de couleurs du vert à l’orange](media/service-tips-and-tricks-for-color-formatting/power-bi-conditional4.png)

Maintenant, nous allons voir ce qui se passe si nous indiquons des valeurs numériques dans les zones **Minimum** et **Maximum**. Sélectionnez **Personnalisé** dans les zones déroulantes **Minimum** et **Maximum**, puis définissez **Minimum** sur 3 500 et **Maximum** sur 6 000.

![Mettre en forme de façon conditionnelle en fonction des nombres](media/service-tips-and-tricks-for-color-formatting/power-bi-conditional-formatting-numbers.png)

Quand nous définissons ces valeurs, le dégradé n’est plus appliqué aux valeurs du graphique qui sont inférieures à la valeur **Minimum** ou supérieures à la valeur **Maximum**. Toute barre ayant une valeur supérieure à la valeur **Maximum** est de couleur verte et toute barre dont la valeur est inférieure à la valeur **Minimum** est de couleur rouge.

![résultat de la mise en forme conditionnelle en fonction des nombres](media/service-tips-and-tricks-for-color-formatting/power-bi-conditional3.png)

### <a name="use-diverging-color-scales"></a>Utiliser des échelles de couleurs divergentes
Parfois, vos données peuvent avoir une échelle naturellement divergente. Par exemple, une plage de températures dispose d’un centre naturel qui correspond au point de congélation et un score de rentabilité possède un milieu naturel (zéro).

Pour utiliser des échelles de couleurs divergentes, cochez la case **Divergent**. Quand **Divergent** est activé, un autre sélecteur de couleurs (appelé **Centre**) s’affiche, comme indiqué dans l’image suivante.

![Boîte de dialogue Couleur par défaut avec Échelle de couleurs sélectionné](media/service-tips-and-tricks-for-color-formatting/power-bi-diverging-colors.png)

Quand le curseur **Divergent** est activé, vous pouvez définir séparément les couleurs des valeurs **Minimum**, **Maximum** et **Centre**. Dans l’image suivante, **Centre** a la valeur 0,2 pour **% Market Share SPLY YTD**. Les barres dont la valeur est supérieure à 1 seront donc d’une nuance de vert et les barres dont la valeur est inférieure à 1 seront d’une nuance de rouge.

![Histogramme avec barres rouges et vertes](media/service-tips-and-tricks-for-color-formatting/power-bi-diverging.png)

## <a name="add-color-to-table-rows"></a>Ajouter de la couleur aux lignes des tableaux
Les tableaux et les matrices offrent de nombreuses options de mise en forme des couleurs. 

![Capture d’écran montrant une table avec des lignes blanches et grises en alternance.](media/service-tips-and-tricks-for-color-formatting/power-bi-table.png)

L’une des méthodes les plus rapides pour appliquer une couleur à un tableau ou une matrice consiste à ouvrir l’onglet Mise en forme et à sélectionner **Style**.  Dans l’image ci-dessous, nous avons sélectionné **Bold header flashy rows** (Lignes fluo d’en-tête en gras).

![Capture d’écran montrant l’option de style Lignes voyantes avec en-tête en gras qui rend la ligne d’en-tête noire et les autres lignes vert clair et sombre.](media/service-tips-and-tricks-for-color-formatting/power-bi-table-style.png)

Testez d’autres options de mise en forme des couleurs. Dans cette image, nous avons modifié la couleur d’arrière-plan sous **En-têtes de colonne**, ainsi que la **Couleur d’arrière-plan** et la **Couleur d’arrière-plan alternative** des **Valeurs** (lignes).

![Capture d’écran montrant les sélecteurs de valeur pour la couleur d’arrière-plan et la couleur d’arrière-plan alternative.](media/service-tips-and-tricks-for-color-formatting/power-bi-table-rows.png)

## <a name="how-to-undo-in-power-bi"></a>Comment annuler dans Power BI
Comme de nombreux autres services et logiciels Microsoft, Power BI permet d’annuler facilement la dernière commande. Par exemple, supposons que vous ayez modifié la couleur d’un point de données ou d’une série de points de données, et que vous n’aimiez pas la couleur une fois que vous la voyez dans la visualisation. Vous voulez rétablir la couleur précédente, mais vous ne vous souvenez pas exactement de quelle couleur il s’agissait.

Pour **Annuler** votre dernière action ou les quelques actions précédentes, il vous suffit de taper CTRL+Z.

Pour abandonner toutes les modifications apportées à une carte Mise en forme, sélectionnez **Rétablir les valeurs par défaut**.

![Carte Mise en forme indiquant Rétablir les valeurs par défaut en bas](media/service-tips-and-tricks-for-color-formatting/power-bi-revert.png)

## <a name="give-us-your-feedback"></a>Faites-nous part de vos commentaires
Vous avez une astuce que vous aimeriez partager ? Envoyez-la nous et nous verrons si nous pouvons l’inclure dans notre rubrique.

## <a name="next-steps"></a>Étapes suivantes
[Prise en main de la mise en forme des couleurs et des propriétés d’axe](service-getting-started-with-color-formatting-and-axis-properties.md)

[Partage des rapports](../collaborate-share/service-share-reports.md).

