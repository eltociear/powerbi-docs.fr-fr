---
title: Mise en forme conditionnelle des tables dans Power BI Desktop
description: Appliquer une mise en forme personnalisée aux tables
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 05/17/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 70aa61d6a02bea1b7058a68b20718008ace1b8c8
ms.sourcegitcommit: 2a7bbb1fa24a49d2278a90cb0c4be543d7267bda
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "34480885"
---
# <a name="conditional-formatting-in-tables"></a>Mise en forme conditionnelle dans les tables 
Avec la mise en forme conditionnelle des tables, vous pouvez spécifier des couleurs de cellule personnalisées en fonction des valeurs des cellules, ou en fonction d’autres valeurs ou champs, et notamment utiliser des couleurs de dégradé. Vous pouvez également afficher les valeurs des cellules avec des barres de données. 

Pour accéder à la mise en forme conditionnelle, dans la zone **Champs** du volet **Visualisations** de Power BI Desktop, sélectionnez la flèche vers le bas à côté de la valeur dans la zone **Valeurs** que vous voulez mettre en forme (ou cliquez avec le bouton droit sur le champ). Vous pouvez uniquement gérer la mise en forme conditionnelle des champs dans la zone **Valeurs** de la zone **Champs**.

![Menu Mise en forme conditionnelle](media/desktop-conditional-table-formatting/table-formatting-0-popup-menu.png)

Les sections suivantes décrivent chacune de ces trois options de mise en forme conditionnelle. Vous pouvez combiner une ou plusieurs options dans une même colonne de table.

> [!NOTE]
> Appliquée à une table, la mise en forme conditionnelle remplace les styles de table personnalisés appliqués aux cellules soumises à une mise en forme conditionnelle.

Pour supprimer la mise en forme conditionnelle d’une visualisation, il suffit de cliquer à nouveau avec le bouton droit sur le champ, et de sélectionner **Supprimer la mise en forme conditionnelle**, puis le type de mise en forme à supprimer.

![Menu Supprimer la mise en forme conditionnelle](media/desktop-conditional-table-formatting/table-formatting-1-remove.png)

## <a name="background-color-scales"></a>Nuances de couleurs de l’arrière-plan

Le fait de sélectionner **Mise en forme conditionnelle**, puis **Échelles de couleurs de l’arrière-plan**, affiche la boîte de dialogue suivante.

![Boîte de dialogue Échelles de couleurs de l’arrière-plan](media/desktop-conditional-table-formatting/table-formatting-1-default-dialog.png)

Vous pouvez sélectionner un champ de votre modèle de données sur lequel baser les couleurs en définissant **Couleur basée sur** sur ce champ. En outre, vous pouvez spécifier le type d’agrégation pour le champ sélectionné avec la valeur **Résumé**. Le champ à mettre en couleur est spécifié dans le champ **Appliquer la couleur à**, ce qui vous permet d’en garder la trace. Vous pouvez appliquer une mise en forme conditionnelle à des champs de date et de texte, à condition de choisir une valeur numérique comme base de la mise en forme.

![Champ Couleur basée sur](media/desktop-conditional-table-formatting/table-formatting-1-apply-color-to.png)

Pour utiliser des valeurs de couleur discrètes pour des plages de valeurs données, sélectionnez **Colorer selon des règles**. Pour utiliser un spectre de couleurs, laissez **Colorer selon des règles** non cochée. 

![Boîte de dialogue Échelles de couleurs de l’arrière-plan](media/desktop-conditional-table-formatting/table-formatting-1-color-by-rules-dialog.png)

### <a name="color-by-rules"></a>Colorer selon des règles

Quand vous sélectionnez **Colorer selon des règles**, vous pouvez entrer une ou plusieurs plages de valeurs, chacune avec une couleur définie.  Chaque plage de valeurs commence par une condition *Si la valeur*, une condition de valeur *et* et une couleur.

![Plage de valeurs de Colorer selon des règles](media/desktop-conditional-table-formatting/table-formatting-1-color-by-rules-if-value.png)

Les cellules du tableau avec des valeurs comprises dans chaque plage apparaissent avec la couleur donnée. Trois règles sont présentes dans l’illustration suivante.

![Colorer selon des règles - Exemple](media/desktop-conditional-table-formatting/table-formatting-1-color-by-rules.png)

L’exemple de tableau se présente maintenant comme ceci :

![Exemple de tableau avec Colorer selon des règles](media/desktop-conditional-table-formatting/table-formatting-1-color-by-rules-table.png)


### <a name="color-minimum-to-maximum"></a>Colorer du minimum au maximum

Vous pouvez configurer les valeurs *Minimum* et *Maximum* et leurs couleurs. Si vous sélectionnez la zone **Divergent**, vous pouvez également configurer une valeur *Centrale* en option.

![Bouton Divergent](media/desktop-conditional-table-formatting/table-formatting-1-diverging.png)

L’exemple de tableau se présente maintenant comme ceci :

![Exemple de tableau avec des couleurs divergentes](media/desktop-conditional-table-formatting/table-formatting-1-diverging-table.png)

## <a name="font-color-scales"></a>Échelles de couleurs de la police

Le fait de sélectionner **Mise en forme conditionnelle**, puis **Échelles de couleurs de la police**, affiche la boîte de dialogue suivante. Cette boîte de dialogue est similaire à la boîte de dialogue **Échelles de couleurs de l’arrière-plan**, mais elle change la couleur de la police au lieu de la couleur d’arrière-plan de la cellule.

![Boîte de dialogue Échelles de couleurs de la police](media/desktop-conditional-table-formatting/table-formatting-2-diverging.png)

L’exemple de tableau se présente maintenant comme ceci :

![Exemple de table avec des échelles de couleurs de police](media/desktop-conditional-table-formatting/table-formatting-2-table.png)

## <a name="data-bars"></a>Barres de données

Le fait de sélectionner **Mise en forme conditionnelle**, puis **Barres de données**, affiche la boîte de dialogue suivante. 

![Boîte de dialogue Barres de données](media/desktop-conditional-table-formatting/table-formatting-3-default.png)

Par défaut, l’option **Afficher seulement la barre** est décochée : la cellule du tableau montre donc à la fois la barre et la valeur réelle.

![Exemple de tableau avec des barres de données et des valeurs](media/desktop-conditional-table-formatting/table-formatting-3-default-table.png)

Si l’option **Afficher seulement la barre** est cochée, la cellule du tableau montre seulement la barre.

![Exemple de tableau avec seulement des barres de données](media/desktop-conditional-table-formatting/table-formatting-3-default-table-bars.png)
