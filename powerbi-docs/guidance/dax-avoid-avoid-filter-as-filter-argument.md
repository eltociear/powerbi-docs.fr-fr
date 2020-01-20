---
title: 'DAX : Évitez d’utiliser FILTER comme argument de filtre'
description: Conseils sur l’utilisation de la fonction FILTER comme un argument de filtre.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/30/2019
ms.author: v-pemyer
ms.openlocfilehash: 935b453dabeaa731a218175526ddddeb980a2b92
ms.sourcegitcommit: b09de56e971b8844a3771413d1f56d49b31baaaf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75692456"
---
# <a name="dax-avoid-using-filter-as-a-filter-argument"></a>DAX : Évitez d’utiliser FILTER comme argument de filtre

En tant que modeleur de données, vous êtes fréquemment amené à écrire des expressions DAX qui doivent être évaluées dans un contexte de filtre modifié. Par exemple, vous pouvez écrire une définition de mesure pour calculer les ventes de « produits à marge élevée ». Nous décrirons ce calcul plus loin dans cet article.

> [!NOTE]
> Cet article est particulièrement utile pour les calculs de modèle qui appliquent des filtres aux tables d’importation.

Les fonctions DAX [CALCULATE](/dax/calculate-function-dax) et [CALCULATETABLE](/dax/calculatetable-function-dax) sont des fonctions importantes et très utiles. Elles vous permettent d’écrire des calculs qui suppriment ou ajoutent des filtres, et de modifier des chemins de relation. Pour cela, vous devez passer des arguments de filtre (expressions booléennes, expressions de table ou fonctions de filtre spécial). Dans cet article, nous aborderons uniquement les expressions booléennes et les expressions de table.

Intéressons-nous maintenant à la définition de mesure suivante, qui calcule les ventes de produits de couleur rouge à l’aide d’une expression de table. Celle-ci va remplacer tous les filtres qui sont appliqués à la table **Product**.

```dax
Red Sales =
CALCULATE(
    [Sales],
    FILTER('Product', 'Product'[Color] = "Red")
)
```

La fonction CALCULATE accepte une expression de table retournée par la fonction DAX [FILTER](/dax/filter-function-dax), qui évalue son expression de filtre pour chaque ligne de la table **Product**. Elle obtient le bon résultat, c’est-à-dire le résultat des ventes des produits de couleur rouge. Toutefois, le résultat peut être obtenu plus efficacement à l’aide d’une expression booléenne.

Voici une définition de mesure améliorée, qui utilise une expression booléenne au lieu d’une expression de table.

```dax
Red Sales =
CALCULATE(
    [Sales],
    'Product'[Color] = "Red"
)
```

Dans la mesure du possible, nous vous recommandons de passer des arguments de filtre en tant qu’expressions booléennes. Ceci est recommandé car les tables de modèle d’importation sont des magasins de colonnes en mémoire. Ils sont optimisés de manière explicite pour filtrer efficacement les colonnes ainsi.

Toutefois, des restrictions s’appliquent aux expressions booléennes lorsqu’elles sont utilisées en tant qu’arguments de filtre. Voici ces restrictions :

- Elles ne permettent pas de comparer des colonnes à d’autres colonnes.
- Elles ne peuvent pas référencer une mesure.
- Elles ne peuvent pas utiliser des fonctions CALCULATE imbriquées.
- Elles ne peuvent pas utiliser des fonctions qui analysent ou retournent une table.

Cela signifie que vous devez utiliser des expressions de table lorsque les exigences de filtre sont complexes.

Voyons maintenant une autre définition de mesure.

```dax
High Margin Product Sales =
CALCULATE(
    [Sales],
    FILTER(
        'Product',
        'Product'[ListPrice] > 'Product'[StandardCost] * 2
    )
)
```

Un _produit à marge élevée_ est un produit dont le prix dépasse le double de son coût standard. Dans cet exemple, vous pouvez utiliser une fonction FILTER. Ceci est dû au fait que l’expression de filtre est trop complexe pour une expression booléenne.

Voici un autre exemple. L’exigence suivante consiste à calculer les ventes, mais uniquement pour les mois où l’entreprise a réalisé des bénéfices.

```dax
Sales for Profitable Months =
CALCULATE(
    [Sales],
    FILTER(
        VALUES('Date'[Month]),
        [Profit] > 0)
    )
)
```

Dans cet exemple, vous pouvez également utiliser une fonction FILTER. Ceci est dû au fait qu’il est nécessaire d’évaluer la mesure **Profit** pour éliminer les mois où aucun bénéfice n’est réalisé. Vous ne pouvez pas utiliser de mesure dans une expression booléenne quand celle-ci est utilisée comme un argument de filtre.

## <a name="recommendations"></a>Recommandations

Pour des performances optimales, nous vous recommandons d’utiliser des expressions booléennes comme arguments de filtre chaque fois que cela vous est possible.

Par conséquent, vous ne devez utiliser les fonctions de filtre que lorsque cela est nécessaire. Vous pouvez les utiliser pour effectuer des comparaisons de colonnes à filtre complexe. Ces comparaisons de colonnes peuvent impliquer :

- Mesures
- D’autres colonnes
- L’utilisation de la fonction DAX [ ou ](/dax/or-function-dax), ou de l’opérateur logique OR (||)

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur cet article, consultez les ressources suivantes :

- [Informations de référence sur DAX (Data Analysis Expressions)](/dax/)
- [Fonctions de filtrage (DAX)](/dax/filter-function-dax)
- Vous avez des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
