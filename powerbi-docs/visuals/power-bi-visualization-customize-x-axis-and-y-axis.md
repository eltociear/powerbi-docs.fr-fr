---
title: Personnaliser les propriétés des axes X et Y
description: Personnaliser les propriétés des axes X et Y
author: msftrien
ms.reviewer: mihart
featuredvideoid: 9DeAKM4SNJM
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 05/06/2020
ms.author: rien
LocalizationGroup: Visualizations
ms.openlocfilehash: b327ca5f4c19638f4afe72abce763601e68fc943
ms.sourcegitcommit: 5ccab484cf3532ae3a16acd5fc954b7947bd543a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/06/2020
ms.locfileid: "93413151"
---
# <a name="customize-x-axis-and-y-axis-properties"></a>Personnaliser les propriétés des axes X et Y

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]    

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Dans ce tutoriel, vous allez découvrir de nombreuses façons de personnaliser les axes X et Y de vos visuels. Certains visuels ne comportent aucun axe. Par exemple, les graphiques en secteurs, n’ont pas d’axes. Et les options de personnalisation varient d’un visuel à un autre. Comme il y a trop d’options pour les couvrir dans un seul article, nous allons examiner certaines des personnalisations les plus utilisées et vous aider à vous familiariser avec l’utilisation de l’onglet **Mise en forme** visuelle dans le canevas de rapport Power BI.  

Regardez comment Amanda personnalise les axes X et Y. Elle montre également les différentes façons de contrôler la concaténation en montant ou en descendant dans la hiérarchie.

> [!NOTE]
> Cette vidéo utilise une version antérieure de Power BI.

<iframe width="560" height="315" src="https://www.youtube.com/embed/9DeAKM4SNJM" frameborder="0" allowfullscreen></iframe>

## <a name="prerequisites"></a>Prérequis

- Power BI Desktop

- [Exemple Analyse de la vente au détail](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix)


## <a name="add-a-new-visualization"></a>Ajouter une nouvelle visualisation

Avant de pouvoir personnaliser la visualisation, vous devez la générer.

1. Dans Power BI Desktop, ouvrez l’exemple Analyse de la vente au détail.  

2. En bas, sélectionnez l’icône de signe plus jaune pour ajouter une nouvelle page. 

    ![signe plus jaune](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-new-page-icon.png)

1. Dans le volet **Visualisations** , sélectionnez l’icône d’histogramme empilé. Cette action ajoute un modèle vide au canevas du rapport.

    ![Capture d’écran du volet Visualisations et d’un histogramme empilé vide](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-column-chart.png)

1. Pour définir les valeurs de l’axe X, dans le volet **Champs** , sélectionnez **Temps** > **FiscalMonth** (MoisFiscal).

1. Pour définir les valeurs de l’axe Y, dans le volet **Champs** , sélectionnez **Sales** > **Last Year Sales** (Ventes > Ventes de l’année dernière) et **Sales** > **This Year Sales** > **Value** (Ventes > Ventes de cette année > Valeur).

    ![Capture d’écran de l’histogramme empilé rempli.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-build-visual.png)

    Vous pouvez désormais personnaliser votre axe X. Power BI offre des options presque illimitées pour mettre en forme votre visualisation. 

## <a name="customize-the-x-axis"></a>Personnaliser l’axe X
Beaucoup de fonctionnalités peuvent être personnalisées pour l’axe X. Vous pouvez ajouter et modifier les étiquettes de données et le titre de l’axe X. Pour les catégories, vous pouvez modifier la largeur, la taille et le remplissage des barres, des colonnes, des lignes et des zones. Pour les valeurs, vous pouvez modifier les unités d’affichage, les décimales et le quadrillage. L’exemple suivant illustre la personnalisation d’un histogramme. Nous allons ajouter quelques personnalisations pour vous familiariser avec les options, puis vous pourrez continuer d’explorer le reste par vous-même.

### <a name="customize-the-x-axis-labels"></a>Personnaliser les étiquettes de l’axe X
Les étiquettes de l’axe X sont affichées sous les colonnes du graphique. En l’état, elles sont difficiles à lire du fait de leur couleur gris clair et de leur petite taille. Nous allons changer leur mise en forme.

1. Dans le volet **Visualisations** , sélectionnez **Mise en forme** (icône représentant un rouleau ![Capture d’écran de l’icône rouleau](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-paintroller-icon.png)) pour afficher les options de personnalisation.

2. Développez les options de l’axe X.

   ![Capture d’écran des options de l’axe X.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-axis-x.png)

3. Déplacez le curseur **Axe X** sur **Activé**.

    ![Capture d’écran du curseur pour l’axe X.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-slider-on.png)

    Vous souhaiterez peut-être définir l’axe X sur **Désactivé** pour différentes raisons, par exemple si la visualisation est suffisamment explicite sans étiquette ou si vous avez besoin de libérer de l’espace dans une page de rapport encombrée afin d’afficher plus de données.

4. Mettez en forme la police, la taille et la couleur du texte :

    - **Couleur**  : Sélectionnez noir

    - **Taille du texte**  : Entrez *14*

    - **Famille de polices**  : Sélectionnez **Arial noir**

    - **Remplissage interne**  : entrez *40 %*

        ![Capture d’écran avec des étiquettes en angle](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-formatting-x.png)
    
5. Vous n’aimez peut-être pas le mode d’affichage du texte de l’axe X sur une diagonale. Plusieurs options s’offrent à vous. 
    - Changez la taille du texte à une valeur inférieure à 14.
    - Agrandissez la visualisation. 
    - Affichez moins de colonnes et ajoutez une barre de défilement en augmentant la valeur **Largeur de catégorie minimale**. 
    
    Ici, nous avons choisi la deuxième option et sélectionné l’une des barres de redimensionnement pour élargir la visualisation. La visualisation restitue maintenant le texte d’une taille de 14 points sans avoir à afficher le texte en angle ni à utiliser une barre de défilement. 

   ![Graphique et volet de mise en forme avec des étiquettes horizontales](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-stretch.png)

### <a name="customize-the-x-axis-title"></a>Personnaliser le titre de l’axe X
Quand le titre de l’axe X est **Activé** , il s’affiche sous les étiquettes de l’axe X. 

1. Commencez par définir le titre de l’axe X sur **Activé**.  

    ![Curseur Titre](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-title-on.png)

    La première chose que vous remarquez est que votre visualisation a maintenant un titre d’axe X par défaut.  Dans ce cas, il s’agit de **MoisFiscal**.

   ![Graphique avec le titre affiché en bas](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-x-title.png)

1. Mettez en forme la police, la taille et la couleur de texte du titre :

    - **Couleur du titre**  : Sélectionnez orange

    - **Titre de l’axe**  : tapez *Mois fiscal* (avec un espace)

    - **Taille du texte du titre**  : entrez *18*

    Une fois les personnalisations effectuées, votre histogramme empilé ressemble à ceci :

    ![Capture d’écran de l’histogramme empilé personnalisé.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-x-title-formatted.png)

1. Enregistrez les modifications que vous avez apportées, puis passez à la section suivante. Si vous devez annuler toutes les modifications, sélectionnez **Rétablir les valeurs par défaut** en bas du volet de personnalisation **Axe X**. Vous allez maintenant personnaliser votre axe Y.

## <a name="customize-the-y-axis"></a>Personnaliser l’axe Y
Beaucoup de fonctionnalités peuvent être personnalisées pour l’axe Y. Vous pouvez ajouter et modifier les étiquettes de données, le titre de l’axe Y et le quadrillage. Pour les valeurs, vous pouvez modifier les unités d’affichage, les décimales, le point de début et le point de fin. Pour les catégories, vous pouvez modifier la largeur, la taille et le remplissage des barres, des colonnes, des lignes et des zones. 

L’exemple suivant poursuit notre personnalisation d’un histogramme. Nous allons apporter quelques modifications pour vous familiariser avec les options, puis vous pourrez continuer d’explorer le reste par vous-même.

### <a name="customize-the-y-axis-labels"></a>Personnaliser les étiquettes de l’axe Y
Les étiquettes de l’axe Y sont affichées à gauche par défaut. En l’état, elles sont difficiles à lire du fait de leur couleur gris clair et de leur petite taille. Nous allons changer leur mise en forme.

1. Développez les options de l’axe Y.

   ![Capture d’écran des options de l’axe Y.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-axis-y.png)

1. Déplacez le curseur **Axe Y** sur **Activé**.  

    ![Capture d’écran du curseur pour l’axe Y.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-y-axis-on.png)

    Vous souhaiterez peut-être désactiver l’axe Y afin de libérer de l’espace pour afficher des données supplémentaires.

1. Mettez en forme la police, la taille et la couleur du texte :

    - **Couleur**  : Sélectionnez noir

    - **Taille du texte**  : entrez *10*

    - **Unités d’affichage**  : sélectionnez **Millions**

    ![Graphique après mise en forme de l’axe Y](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-formatting-y.png)

### <a name="customize-the-y-axis-title"></a>Personnaliser le titre de l’axe Y
Quand le titre de l’axe Y est **Activé** , il s’affiche à côté des étiquettes de l’axe Y. Pour cette visualisation, étant donné que la présence d’un titre pour l’axe Y n’améliore pas le visuel, laissez **Titre** désactivé ( **Off** ). Nous ajouterons des titres d’axe Y à un visuel à deux axes plus tard dans ce tutoriel. 

### <a name="customize-the-gridlines"></a>Personnaliser le quadrillage
Faisons ressortir les lignes du quadrillage en changeant la couleur et en augmentant l’épaisseur du trait :

- **Couleur**  : Sélectionnez orange

- **Épaisseur du trait**  : Entrez *2*

Après toutes ces personnalisations, votre histogramme doit ressembler à ceci :

![Capture d’écran du graphique avec l’axe Y personnalisé.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-gridline.png)

## <a name="customizing-visualizations-with-dual-y-axes"></a>Personnalisation des visualisations ayant deux axes Y

Dans certaines visualisations, il peut être utile d’avoir deux axes Y. Les graphiques combinés en sont un bon exemple. Avant de mettre en forme deux axes Y, nous allons créer un graphique combiné qui compare les tendances des ventes et la marge brute.  

### <a name="create-a-chart-with-two-y-axes"></a>Créer un graphique avec deux axes Y

1. Sélectionnez l’histogramme, puis changez-le en graphique *en courbes et histogramme empilé*. Ce type de visuel prend en charge une seule valeur de graphique en courbes et plusieurs valeurs de colonnes empilables. 

    ![Capture d’écran du volet Visualisation avec l’icône du graphique en courbes et de l’histogramme empilé.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-combo.png)
   

2. Faites glisser **Sales** > **Gross Margin Last Year %** (Ventes > Pourcentage de marge brute de l’année précédente) du volet Champs vers le compartiment **Valeurs de ligne**.

    ![Capture d’écran du graphique en courbes et de l’histogramme empilé avec les trois valeurs clairement représentées.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-add-line.png)

    
3. Modifiez la mise en forme de la visualisation afin de supprimer les étiquettes de l’axe X en angle. 

   ![Graphique combiné et volet de mise en forme avec une taille de police réduite à 12](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-font-size.png)

   Power BI crée deux axes Y, ce qui vous permet d’afficher les valeurs selon une échelle différente. L’axe de gauche mesure le montant des ventes et l’axe de droite mesure le pourcentage de marge brute.

### <a name="format-the-second-y-axis"></a>Mettre en forme le second axe Y
Comme nous avons commencé avec une visualisation comportant un seul axe Y mis en forme, Power BI créé le deuxième axe Y en appliquant les mêmes paramètres. Toutefois, nous pouvons modifier cela. 

1. Dans le volet **Visualisations** , sélectionnez l’icône représentant un rouleau pour afficher les options de mise en forme.

1. Développez les options de l’axe Y.

1. Faites défiler vers le bas jusqu'à l’option **Afficher les valeurs secondaires**. Vérifiez que cette option est activée ( **On** ). Notre second axe Y représente le graphique en courbes.

   ![Capture d’écran de l’option Afficher les valeurs secondaires.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-show-secondary.png)

1. (Facultatif) Personnalisez la couleur de la police, la taille et les unités d’affichage des deux axes. Si vous basculez **Position** sur l’axe des colonnes ou l’axe des lignes, les deux axes changent de côté.

### <a name="add-titles-to-both-axes"></a>Ajouter des titres aux deux axes

Dans une visualisation complexe, il est utile d’ajouter des titres aux axes.  Les titres permettent à vos collègues de mieux comprendre le contenu de votre visualisation.

1. Basculez **Titre** sur **Activé** pour **Axe Y (colonne)** et **Axe Y (ligne)** .

1. Définissez **Style** sur **Afficher le titre uniquement** pour les deux axes.

   ![Capture d’écran des options Titre et Style.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-show-title.png)

1. Votre graphique combiné affiche maintenant les deux axes, chacun avec un titre.

   ![Capture d’écran du graphique personnalisé à deux axes Y.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-titles-on.png)

1. Mettez en forme les titres. Dans cet exemple, nous avons raccourci l’un des titres et réduit la taille de police des deux titres. 
    - Taille de police : **9**
    - **Titre de l’axe** raccourci pour le premier axe Y (l’histogramme) : Ventes l’année dernière/cette année. 
    
     ![Capture d’écran du graphique combiné avec des titres complets affichés.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-dual.png)

    Pour plus d’informations, consultez [Trucs et astuces pour la mise en forme des couleurs dans Power BI](service-tips-and-tricks-for-color-formatting.md) et [Personnaliser le titre, la légende et l’arrière-plan d’une visualisation](power-bi-visualization-customize-title-background-and-legend.md). 
    

## <a name="next-steps"></a>Étapes suivantes

- [Visualisations dans des rapports Power BI](power-bi-report-visualizations.md)

D’autres questions ? [Posez vos questions à la communauté Power BI](https://community.powerbi.com/)
