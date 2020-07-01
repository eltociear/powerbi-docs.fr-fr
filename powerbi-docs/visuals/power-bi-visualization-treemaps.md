---
title: Graphiques de compartimentage dans Power BI
description: Graphiques de compartimentage dans Power BI
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 05/05/2020
ms.author: rien
LocalizationGroup: Visualizations
ms.openlocfilehash: 6331209d40defc4f97a2de670be207e86eaabfef
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85237401"
---
# <a name="treemaps-in-power-bi"></a>Graphiques de compartimentage dans Power BI

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Les treemaps utilisent des rectangles imbriqués pour présenter des données sous forme hiérarchique. Chaque niveau de la hiérarchie est représenté par un rectangle de couleur (une branche) qui contient d’autres rectangles plus petits (les feuilles). Power BI définit la taille de l’espace à l’intérieur de chaque rectangle selon sur la valeur mesurée. Les rectangles sont disposés par taille du haut à gauche (le plus grand) au bas à droite (le plus petit).

![Capture d’écran du treemap Count of Product by Category et Manufacturer.](media/power-bi-visualization-treemaps/pbi-nancy-viz-treemap.png)

Imaginons que j’utilise ce graphique pour analyser mes ventes, les branches supérieures correspondent aux catégories de vêtements : **Urban**, **Rural**, **Youth** et **Mix**. Power BI divise les rectangles de votre catégorie en feuilles correspondant aux fabricants de vêtements dans cette catégorie. Ces feuilles auront une taille et une nuance qui dépendent du nombre d’articles vendus.

Dans la branche **Urban** ci-dessus, un grand nombre de vêtements **VanArsdel** a été vendu. Les ventes de vêtements **Natura** et **Fama** sont moindres. Seuls quelques articles **Leo** ont été vendus. Par conséquent, la branche **Urban** de votre treemap se présentera comme suit :

* le plus grand rectangle pour **VanArsdel** dans le coin supérieur gauche ;

* des rectangles légèrement plus petits pour **Natura** et **Fama** ;

* un grand nombre d’autres rectangles pour tous les autres vêtements vendus ;

* un tout petit rectangle pour **Leo**.

Vous pourriez ainsi comparer le nombre d’articles vendus dans les autres catégories de vêtements d’après la taille et le nuance de chaque nœud feuille : plus le rectangle est grand et sombre, plus les ventes sont élevées.


## <a name="when-to-use-a-treemap"></a>Quand faut-il utiliser un treemap ?

Les treemaps sont conseillés :

* pour afficher de grandes quantités de données hiérarchiques ;

* quand un graphique à barres ne peut pas afficher correctement toutes les valeurs ;

* pour montrer la proportion de chaque partie par rapport à l’ensemble ;

* pour montrer le modèle de distribution de la mesure entre chaque niveau de catégories dans la hiérarchie ;

* pour représenter les attributs selon un codage par taille et couleur ;

* pour repérer les modèles, les valeurs inhabituelles, les principaux contributeurs et les exceptions.

## <a name="prerequisite"></a>Prérequis

Ce tutoriel utilise le [fichier PBIX de l’exemple Analyse de la vente au détail](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix).

1. Dans la section supérieure gauche de la barre de menus, sélectionnez **Fichier** > **Ouvrir**.
   
2. Rechercher votre copie du **fichier PBIX de l’exemple Analyse de la vente au détail**

1. Ouvrez le **fichier PBIX de l’exemple Analyse de la vente au détail** dans la vue Rapport ![Capture d’écran de l’icône de la vue Rapport.](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Sélectionner ![Capture d’écran de l’onglet jaune.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) pour ajouter une nouvelle page.

> [!NOTE]
> Pour que vous puissiez partager votre rapport avec un collègue Power BI, il faut que vous disposiez tous deux de licences individuelles Power BI Pro ou que le rapport soit enregistré dans une capacité Premium.    



Une fois que vous obtenez le jeu de données **Retail Analysis Sample (Analyse de la vente au détail)** , vous pouvez commencer.

## <a name="create-a-basic-treemap"></a>Créer un treemap simple

Vous allez créer un rapport et ajouter un treemap simple.


1. Dans le volet **Champs**, sélectionnez la mesure **Ventes** > **Ventes de l’année dernière**.

   ![Capture d’écran de l’option Ventes > Ventes de l’année dernière et du visuel obtenu.](media/power-bi-visualization-treemaps/treemapfirstvalue-new.png)

1. Sélectionnez l’icône du treemap ![Capture d’écran de l’icône treemap](media/power-bi-visualization-treemaps/power-bi-treemap-icon.png) pour convertir le graphique en treemap.

   ![Capture d’écran du treemap sans configuration.](media/power-bi-visualization-treemaps/treemapconvertto-new.png)

1. Sélectionnez **Item** (Élément) > **Category** (Catégorie) : ceci va également ajouter **Category** à **Group** (Groupe).

    Power BI crée un treemap dont les rectangles ont une taille proportionnelle au total des ventes et une couleur distincte pour chaque catégorie représentée. Pour résumer, vous avez créé une hiérarchie qui représente visuellement la quantité relative du total des ventes par catégorie. La catégorie **Men’s** enregistre les meilleures ventes, alors que la catégorie **Hosiery** enregistre les plus basses.

    ![Capture d’écran du treemap configuré.](media/power-bi-visualization-treemaps/power-bi-complete.png)

1. Sélectionnez **Store** (Magasin) > **Chain** (Chaîne) : ceci va également ajouter **Chain** à **Details** (Détails) pour compléter votre treemap. Vous pouvez à présent comparer les ventes de l’année dernière par catégorie et par chaîne.

   ![Capture d’écran du treemap avec l’option Magasin > Chaîne ajoutée aux détails.](media/power-bi-visualization-treemaps/power-bi-details.png)

   > [!NOTE]
   > Les détails et la saturation des couleurs ne peuvent pas être utilisés en même temps.

1. Pointez sur une zone **Chaîne** pour afficher l’info-bulle correspondant à cette portion de la **Catégorie**.

    Par exemple, si vous pointez sur **Fashions Direct** dans le rectangle **090-Home**, l’info-bulle pour la portion Fashions Direct de la catégorie Home s’affiche.

   ![Capture d’écran de l’info-bulle Accueil qui s’affiche.](media/power-bi-visualization-treemaps/treemaphoverdetail-new.png)


## <a name="highlighting-and-cross-filtering"></a>Mise en surbrillance et filtrage croisé

La mise en surbrillance d’une **Category** (Catégorie) ou d’un **Detail** (Détail) dans un treemap entraîne la mise en surbrillance et le filtrage croisés des autres visualisations sur la page du rapport. Pour poursuivre, ajoutez des visuels à cette page de rapport ou copiez le treemap dans l’une des autres pages de ce rapport. L’image ci-dessous montre que le treemap a été copié dans la page **Vue d’ensemble**. 

1. Dans le treemap, sélectionnez une **catégorie** ou une **chaîne** au sein d’une **catégorie**. Cela mettra en surbrillance croisée les autres visualisations sur la page. Le fait de sélectionner par exemple la catégorie **050-Shoes** vous montre que le montant des ventes de chaussures de l’année dernière était de **16 352 432 $** avec **Fashions Direct** comptant pour **2 174 185 $** .

   ![Capture d’écran du rapport Vue d’ensemble des ventes en magasin montrant la surbrillance croisée.](media/power-bi-visualization-treemaps/treemaphiliting.png)

1. Dans le graphique en secteurs **Ventes de l’année dernière par chaîne**, sélectionnez le secteur **Fashions Direct** pour filtrer le graphique de compartimentage.
   ![Démonstration GIF de la fonctionnalité de filtrage croisé.](media/power-bi-visualization-treemaps/treemapnoowl.gif)

1. Pour gérer la mise en surbrillance croisée et le filtrage croisé des tableaux entre eux, consultez [Modifier l’interaction des visuels dans un rapport Power BI](../create-reports/service-reports-visual-interactions.md).

## <a name="next-steps"></a>Étapes suivantes

* [Graphiques en cascade dans Power BI](power-bi-visualization-waterfall-charts.md)

* [Types de visualisation dans Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)

