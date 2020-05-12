---
title: Création d’un visuel de matrice dans Power BI
description: Découvrez comment le visuel de matrice permet d’effectuer des dispositions échelonnées et une mise en évidence granulaire dans Power BI.
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 02/10/2020
ms.author: rien
LocalizationGroup: Visualizations
ms.openlocfilehash: 0a9bebd51e64c18e0c354386e168661542b9c5bf
ms.sourcegitcommit: a199dda2ab50184ce25f7c9a01e7ada382a88d2c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82866584"
---
# <a name="create-matrix-visualizations-in-power-bi"></a>Créer des visualisations de matrice dans Power BI

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Le visuel Matrice est similaire à une table.  Une table prend en charge deux dimensions et les données sont plates, ce qui signifie que les valeurs dupliquées sont affichées et non agrégées. Une matrice facilite l’affichage des données de manière claire entre plusieurs dimensions : elle prend en charge une disposition échelonnée. La matrice agrège automatiquement les données et permet de descendre dans la hiérarchie. 

Vous pouvez créer des visuels de matrice dans des rapports **Power BI Desktop** et mettre en évidence des éléments au sein de la matrice en les croisant avec d’autres visuels sur cette page de rapports. Par exemple, vous pouvez sélectionner des lignes, des colonnes, et même des cellules individuelles pour les mettre en évidence croisée. De même, les sélections de cellules individuelles et de plusieurs cellules peuvent être copiées et collées dans d’autres applications. 

![matrice croisée mise en surbrillance et graphique en anneau](media/desktop-matrix-visual/matrix-visual_2a.png)

De nombreuses fonctionnalités sont associées à la matrice, que nous allons passer en revue dans les sections suivantes de cet article.

> [!NOTE]
> Pour que vous puissiez partager votre rapport avec un collègue Power BI, il faut que vous disposiez tous deux de licences individuelles Power BI Pro ou que le rapport soit enregistré dans une capacité Premium.

## <a name="understanding-how-power-bi-calculates-totals"></a>Comprendre comment Power BI calcule les totaux

Avant de passer à l’utilisation du visuel Matrice, il est important d’apprendre comment Power BI calcule les valeurs des totaux et des sous-totaux dans les tables et les matrices. Pour les lignes des totaux et des sous-totaux, Power BI évalue la mesure sur toutes les lignes dans les données sous-jacentes : il ne s’agit pas d’une simple addition des valeurs des lignes visibles ou affichées. Les valeurs obtenues dans la ligne du total peuvent donc être différentes de ce à quoi on pourrait s’attendre.

Regardez les visuels de matrice suivants. 

![compare la table et la matrice](media/desktop-matrix-visual/matrix-visual_3.png)

Dans cet exemple, chaque ligne du visuel de la matrice tout à droite affiche le *Montant* de chaque combinaison vendeur/date. Toutefois, dans la mesure où chaque vendeur apparaît sur plusieurs dates, les chiffres sont susceptibles de s’afficher plusieurs fois. C’est pourquoi le total exact calculé à partir des données sous-jacentes n’est pas égal à la simple addition des valeurs visibles. Il s’agit d’un modèle courant, selon lequel la valeur additionnée correspond à l’élément de l’ensemble de départ dans une relation multivoque.

Lorsque vous examinez des totaux et des sous-totaux, n’oubliez pas que ces valeurs sont basées sur les données sous-jacentes. Elles ne sont pas uniquement basées sur des valeurs visibles.


## <a name="expanding-and-collapsing-row-headers"></a>Développer et réduire des en-têtes de lignes
Il existe deux manières de développer des en-têtes de lignes. La première se fait par le biais du menu contextuel, qui comporte des options pour développer l’en-tête de ligne sélectionné, le niveau tout entier ou absolument tout jusqu’au dernier niveau de la hiérarchie. Il existe des options similaires pour réduire les en-têtes de lignes.

![](media/desktop-matrix-visual/power-bi-expand1.png)

Vous pouvez également ajouter des boutons +/-aux en-têtes de lignes grâce au volet Mise en forme sous la carte **En-têtes de lignes**. Par défaut, les icônes correspondent à la mise en forme de l’en-tête de ligne, mais vous pouvez personnaliser la couleur et la taille des icônes séparément si vous le souhaitez.

Une fois activées, elles fonctionnent comme les icônes de tableau croisé dynamique dans Excel.

![](media/desktop-matrix-visual/power-bi-expand2.png)

L’état de développement de la matrice sera enregistré avec le rapport. Une matrice peut être épinglée à un tableau de bord développé ou réduit. Lorsque cette vignette de tableau de bord est sélectionnée et que le rapport s’ouvre, l’état de développement peut encore être modifié dans le rapport. 

![](media/desktop-matrix-visual/power-bi-expand3.png)

> [!NOTE]
> Si vous créez un rapport en plus d’un modèle multidimensionnel Analysis Services, des considérations spécifiques doivent être prises en compte pour développer/réduire si le modèle utilise la fonctionnalité de membre par défaut. Pour plus d’informations, consultez [Utiliser des modèles multidimensionnels dans Power BI](../desktop-default-member-multidimensional-models.md)

## <a name="using-drill-down-with-the-matrix-visual"></a>Utilisation de la descente dans la hiérarchie avec le visuel de matrice
Le visuel de la matrice vous permet d’effectuer toutes sortes d’opérations intéressantes de descente dans la hiérarchie qui n’étaient pas possibles avant. Vous pouvez notamment descendre dans la hiérarchie en utilisant les lignes, les colonnes, voire des sections et cellules individuelles. Voyons comment ces opérations fonctionnent.

### <a name="drill-down-on-row-headers"></a>Descendre dans la hiérarchie sur des en-têtes de ligne

Dans le volet Visualisations, lorsque vous ajoutez plusieurs champs à la section **Lignes** du puits **Champs**, vous permettez la descente dans la hiérarchie sur les lignes du visuel Matrice. Cette opération est similaire à la création d’une hiérarchie, qui vous permet de descendre (et remonter) dans cette hiérarchie et d’analyser les données à chaque niveau.

Dans l’image suivante, la section **Lignes** contient les éléments *Étape de vente* et *Taille de l’opportunité*, qui créent un regroupement (ou une hiérarchie) dans les lignes, à partir duquel nous pouvons extraire.

![Carte de filtres montrant les lignes choisies](media/desktop-matrix-visual/power-bi-rows-matrix.png)

Lorsque le visuel comporte un regroupement créé dans la section **Lignes**, le visuel lui-même affiche les icônes *Explorer* et *Développer* dans l’angle supérieur gauche du visuel.

![matrice avec contrôles d’exploration mis en avant](media/desktop-matrix-visual/power-bi-matrix-drilldown.png)

À l’instar du comportement des fonctions Explorer et Développer dans d’autres visuels, ces boutons permettent de descendre (ou remonter) dans la hiérarchie. Dans ce cas, nous pouvons descendre dans la hiérarchie d’*Étape de vente* à *Taille de l’opportunité*, comme l’illustre l’image suivante, où l’icône Descendre d’un niveau dans la hiérarchie (en forme de fourche) a été sélectionnée.

![matrice avec hiérarchie forme de fourche](media/desktop-matrix-visual/power-bi-matrix-drill3.png)

Outre l’utilisation de ces icônes, vous pouvez sélectionner une de ces en-têtes de lignes et descendre dans la hiérarchie en effectuant des choix dans le menu qui s’affiche.

![options de menu pour les lignes de la matrice](media/desktop-matrix-visual/power-bi-matrix-menu.png)

Notez que ce menu affiche quelques options qui produisent des résultats différents :

La sélection de l’option **Descendre dans la hiérarchie** a pour effet de développe la matrice pour *ce* niveau de ligne *en excluant* tous les autres en-têtes de ligne à l’exception de celui qui était sélectionné. Dans l’image suivante, **Proposition** > **Descendre dans la hiérarchie** a été sélectionné. Vous pouvez constater que d’autres lignes de niveau supérieur n’apparaissent plus dans la matrice. Cette manière d’explorer est utile et s’avèrera particulièrement appréciable lorsque nous aborderons la section Sélection croisée.

![la matrice de descente d’un niveau dans la hiérarchie](media/desktop-matrix-visual/power-bi-drill-down-matrix.png)

Sélectionnez l’icône **Monter dans la hiérarchie** pour revenir à la vue de niveau supérieur précédente. Si vous sélectionnez ensuite **Proposition** > **Afficher le niveau suivant**, vous obtenez une liste alphabétique de tous les éléments du niveau suivant (en l’occurrence, le champ *Taille de l’opportunité*), sans la catégorisation de hiérarchie de niveau supérieur.

![matrice utilisant Afficher le niveau suivant](media/desktop-matrix-visual/power-bi-next-level-matrix.png)

Sélectionnez l’icône **Monter dans la hiérarchie** en haut à gauche pour que la matrice affiche toutes les catégories de niveau supérieur, puis sélectionnez **Proposition** > **Développer au prochain niveau** pour voir toutes les valeurs des deux niveaux de la hiérarchie - *Étape de vente* et *Nombre d’opportunité*.

![matrice utilisant Développer le niveau suivant](media/desktop-matrix-visual/power-bi-matrix-expand-next.png)

Vous pouvez également utiliser l’élément de menu **Développer** pour contrôler davantage l’affichage.  Par exemple, sélectionnez **Proposition** > **Développer** > **Sélection**. Power BI affiche une ligne de total pour chaque *Étape de vente* et toutes les options de *Taille d’opportunité* pour *Proposition*.

![Matrice après avoir appliqué Développer à la proposition](media/desktop-matrix-visual/power-bi-matrix-expand.png)

### <a name="drill-down-on-column-headers"></a>Descendre dans la hiérarchie sur des en-têtes de colonne
Tout comme sur des lignes, nous pouvons descendre dans la hiérarchie sur des colonnes. Dans l’image suivante, la zone du champ **Colonnes** comprend deux champs, ce qui crée une hiérarchie similaire à celle que nous avons utilisée pour les lignes plus haut dans cet article. Dans le puits du champ **colonnes**, nous avons *Région* et *Segment*. Dès que le deuxième champ a été ajouté à **Colonnes**, un nouveau menu déroulant affiché sur le visuel, il affiche actuellement **Lignes**.

![Matrice après l’ajout de la deuxième valeur de colonne](media/desktop-matrix-visual/power-bi-matrix-row.png)

Pour Explorer sur les colonnes, sélectionnez **Colonnes** à partir du menu *Explorer* qui se trouve en haut à gauche de la matrice. Sélectionnez la région *Est* et choisissez **Descendre dans la hiérarchie**.

![menu pour descendre dans la hiérarchie des colonnes](media/desktop-matrix-visual/power-bi-matrix-column.png)

Lorsque vous sélectionnez **Descendre dans la hiérarchie**, le niveau suivant de la hiérarchie de colonne pour *Région > Est* s’affiche, en l’occurrence *Nombre d’opportunités*. L'autre région est masquée.

![matrice avec colonne Descendre d’un niveau dans la hiérarchie](media/desktop-matrix-visual/power-bi-matrix-column-drill.png)

Les autres éléments du menu opèrent sur les colonnes de la même manière que sur les lignes (consultez la section précédente, **Descendre dans la hiérarchie sur des en-têtes de ligne**). Nous pouvons **Afficher le niveau suivant** et **Développer au prochain niveau** avec des colonnes comme nous pouvions le faire avec les lignes.

> [!NOTE]
> Les icônes Descendre dans la hiérarchie et Monter dans la hiérarchie dans l’angle supérieur gauche du visuel de matrice s’appliquent uniquement aux lignes. Pour descendre dans la hiérarchie sur des colonnes, vous devez utiliser le menu contextuel.

## <a name="stepped-layout-with-matrix-visuals"></a>Disposition échelonnée avec des visuels de matrice

Le visuel Matrice met automatiquement en retrait les sous-catégories dans une hiérarchie sous chaque parent. C’est ce qu’on appelle une disposition échelonnée.

Dans la version d’origine du visuel de matrice, les sous-catégories s’affichaient dans une colonne tout à fait distincte, occupant beaucoup plus d’espace que le visuel. L’image suivante présente le tableau dans le visuel Matrice d’origine. Vous pouvez constater que les sous-catégories apparaissent dans une colonne distincte.

![Capture d’écran de l’ancien visuel de matrice montrant les sous-catégories dans une colonne distincte.](media/desktop-matrix-visual/matrix-visual_14.png)

Dans l’image suivante, vous voyez un visuel Matrice avec une disposition échelonnée en action. Notez que les sous-catégories (Accessoires d’ordinateur, Ordinateurs de bureau, ordinateurs portables, Moniteurs, etc.) de la catégorie *Ordinateurs* apparaissent légèrement en retrait, produisant un visuel plus clair et plus concentré.

![mode de formatage actuel des données par la matrice](media/desktop-matrix-visual/matrix-visual_13.png)

Vous pouvez aisément ajuster les paramètres de la disposition échelonnée. Le visuel Matrice étant sélectionné, dans la section **Format** (icône de rouleau à peinture) du volet **Visualisations**, développez la section En-têtes de ligne. Vous avez deux options : le commutateur de disposition échelonnée (qui active ou désactive cette option) et le retrait de la disposition échelonnée (qui spécifie l’importance du retrait en pixels).

![Carte d’en-têtes de lignes affichant le contrôle de disposition échelonnée](media/desktop-matrix-visual/power-bi-stepped-matrix.png)

Si vous désactivez la disposition échelonnée, Power BI affiche les sous-catégories dans une autre colonne au lieu de s’afficher en retrait sous la catégorie parente.

## <a name="subtotals-and-grand-totals-with-matrix-visuals"></a>Sous-totaux et totaux généraux avec visuels Matrice

Vous pouvez activer ou désactiver des sous-totaux dans les visuels Matrice, aussi bien pour les lignes que les colonnes. Dans l’image suivante, vous pouvez voir que les sous-totaux de ligne sont définis sur **Activé** et pour s’afficher au bas.

![matrice montrant les totaux et les sous-totaux](media/desktop-matrix-visual/power-bi-subtotals.png)

Quand vous activez **Sous-totaux** et que vous ajoutez une étiquette, Power BI ajoute aussi une ligne (et la même étiquette) pour la valeur de total général. Pour mettre en forme le total général, sélectionnez l’option de format pour **Total général**. 

![matrice montrant la carte Total général](media/desktop-matrix-visual/power-bi-grand-total.png)

Si vous voulez désactiver les sous-totaux et le total général, dans la section Format du volet Visualisations, développez la carte **Sous-totaux**. Mettez le curseur des sous-totaux de ligne sur la position **Désactivé**. Lorsque vous procédez ainsi, les sous-totaux ne sont pas affichés.

![matrice avec sous-totaux désactivés](media/desktop-matrix-visual/power-bi-no-subtotals.png)

Le même processus s’applique pour les sous-totaux des colonnes.

## <a name="add-conditional-icons"></a>Ajouter des icônes conditionnelles
Ajoutez des signaux visuels à votre table ou matrice avec des *icônes conditionnelles*. 

Dans la section Format du volet Visualisations, développez la carte **Mise en forme conditionnelle**. Mettez le curseur **Icônes** sur la position **Activé** et sélectionnez **Contrôles avancés**.

![Matrice avec l’écran Icônes affiché](media/desktop-matrix-visual/power-bi-icons.png)

Ajustez les conditions, les icônes et les couleurs de votre matrice, puis sélectionnez **OK**. Dans cet exemple, nous avons utilisé un indicateur rouge pour les valeurs basses, un cercle violet pour les valeurs élevées et un triangle jaune pour tout ce qui se trouve entre les deux. 

![Matrice avec les icônes affichées](media/desktop-matrix-visual/power-bi-icons-applied.png)

## <a name="cross-highlighting-with-matrix-visuals"></a>Sélection croisée avec des visuels de matrice

Avec le visuel Matrice, tous les éléments de la matrice peuvent être sélectionnés comme base pour une sélection croisée. Lorsque vous sélectionnez une colonne dans une Matrice, Power BI met cette colonne en surbrillance, comme tous les autres visuels sur la page de rapport. Ce type de sélection croisée est une fonctionnalité courante d’autres visuels et sélections de points de données et est à présent également disponible pour le visuel Matrice.

De plus, la combinaison Ctrl+Clic fonctionne également pour la sélection croisée. Par exemple, dans l’image suivante, une collection de sous-catégories a été sélectionnée dans le visuel Matrice. Notez comment les éléments non sélectionnés dans le visuel sont grisés, et comment les autres visuels de la page reflètent les sélections opérées dans le visuel Matrice.

![Capture d’écran du visuel Matrice, ainsi que deux autres visuels illustrant la fonction Ctrl + clic pour la sélection croisée.](media/desktop-matrix-visual/matrix-visual_16.png)

## <a name="copying-values-from-power-bi-for-use-in-other-applications"></a>Copie des valeurs à partir de Power BI pour une utilisation dans d’autres applications

Votre matrice ou votre table peuvent avoir du contenu que vous souhaitez utiliser dans d’autres applications : Dynamics CRM, Excel et autres rapports de Power BI. Avec le clic droit Power BI, vous pouvez copier une cellule unique ou une sélection de cellules dans votre Presse-papiers. Ensuite, collez-les dans l’autre application.


* Pour copier la valeur d’une cellule unique, sélectionnez la cellule, cliquez avec le bouton droit, puis choisissez **Copier la valeur**. Avec la valeur de cellule non mise en forme dans votre Presse-papiers, vous pouvez maintenant la coller dans une autre application.

    ![Capture d’écran du visuel de matrice avec une flèche pointant vers une valeur et le menu contextuel développé avec les options Copier la valeur et Copier la sélection.](media/desktop-matrix-visual/power-bi-cell-copy.png)



* Pour copier plusieurs cellules, sélectionnez une plage de cellules ou utilisez la touche CTRL pour sélectionner une ou plusieurs cellules. 

    ![Capture d’écran du visuel de matrice avec une flèche pointant de trois valeurs vers le menu contextuel développé avec les options Copier la valeur et Copier la sélection.](media/desktop-matrix-visual/power-bi-copy.png)

* La copie inclut les en-têtes de colonne et de ligne.

    ![Capture d’écran montrant des lignes et des colonnes d’Excel avec les valeurs collés dedans.](media/desktop-matrix-visual/power-bi-copy-selection.png)

* Pour créer une copie du visuel lui-même ne contenant que les cellules sélectionnées, sélectionnez une ou plusieurs cellules à l’aide de la touche CTRL, cliquez avec le bouton droit de la souris, puis choisissez **Copier le visuel**

    ![Capture d'écran montrant l'option de copie du visuel](media/desktop-matrix-visual/power-bi-copy-visual.png)

* La copie sera une autre visualisation matricielle, mais ne contiendra que vos données copiées.

    ![Capture d'écran montrant un exemple visuel de la copie](media/desktop-matrix-visual/power-bi-copy-visual-example.png)

## <a name="setting-a-matrix-value-as-a-custom-url"></a>Définir une valeur de matrice comme URL personnalisée

Si vous avez une colonne ou une mesure qui contient des URL de site web, vous pouvez utiliser la mise en forme conditionnelle pour appliquer ces URL à des champs sous forme de liens actifs. Vous trouverez cette option sous la carte **Mise en forme conditionnelle** dans le volet Mise en forme.

![Carte de filtres montrant les lignes choisies](media/desktop-matrix-visual/power-bi-web-url.png)

Activez **URL Web**, puis sélectionnez un champ à utiliser comme URL de la colonne. Une fois appliquées, les valeurs de ce champ (colonne) deviennent des liens actifs. Placez le curseur dessus pour voir le lien, puis sélectionnez-le pour accéder à cette page. 

Pour plus d’informations, consultez [Mise en forme conditionnelle des tableaux](../desktop-conditional-table-formatting.md).

## <a name="shading-and-font-colors-with-matrix-visuals"></a>Couleurs d’ombrage et de police avec les visuels Matrice
Avec le visuel de matrice, vous pouvez appliquer la mise en forme conditionnelle (couleurs et ombrage ainsi que barres de données) à l’arrière-plan des cellules de la matrice et une mise en forme conditionnelle au texte et aux valeurs elles-mêmes.

Pour appliquer la mise en forme conditionnelle, sélectionnez le visuel de matrice et ouvrez le volet **Mise en forme**. Développez la carte **Mise en forme conditionnelle** et, pour **Couleur d’arrière-plan**, **Couleur de police** ou **Barres de données**, mettez le curseur sur **Activé**. Activer l’une de ces options a pour effet d’afficher un lien pour *Contrôles avancés*, qui vous permet de personnaliser les couleurs et les valeurs de la mise en forme des couleurs.
  
  ![Volet Mise en forme montrant le contrôle des barres de données](media/desktop-matrix-visual/power-bi-matrix-data-bars.png)

Sélectionnez *Contrôles avancés* pour afficher une boîte de dialogue, ce qui vous permet d’effectuer des ajustements. Cet exemple montre la boîte de dialogue pour **Barres de données**.

![Volet Barres de données](media/desktop-matrix-visual/power-bi-data-bars.png)

## <a name="considerations-and-troubleshooting"></a>Considérations et résolution des problèmes

* Si les données texte des en-têtes ou des cellules de votre matrice contiennent des caractères de nouvelle ligne, ces caractères sont ignorés, sauf si vous activez l’option « retour automatique à la ligne » dans la carte de volet de mise en forme associée à l’élément. 

## <a name="next-steps"></a>Étapes suivantes

[Visuel Power Apps pour Power BI](power-bi-visualization-powerapp.md)

[Types de visualisation dans Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)
