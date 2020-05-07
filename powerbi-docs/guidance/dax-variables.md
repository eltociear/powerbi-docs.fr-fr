---
title: 'DAX : Utiliser des variables pour améliorer vos formules'
description: Conseils d’utilisation des variables dans des expressions DAX.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/23/2019
ms.author: v-pemyer
ms.openlocfilehash: f352cbbd7c42aa54ae876e73c0ed821eccda59c8
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "74700705"
---
# <a name="dax-use-variables-to-improve-your-formulas"></a>DAX : Utiliser des variables pour améliorer vos formules

En tant que modeleur de données, l’écriture et le débogage de certains calculs DAX peuvent s’avérer difficiles. Les exigences de calcul complexes impliquent souvent d’écrire des expressions composées ou complexes. Les expressions composées peuvent impliquer l’utilisation de nombreuses fonctions imbriquées, et éventuellement la réutilisation de la logique d’expression.

L’utilisation de variables dans vos formules DAX vous aide à écrire des calculs complexes et efficaces. Les variables peuvent :

- [Améliorer les performances](#improve-performance)
- [Améliorer la lisibilité](#improve-readability)
- [Simplifier le débogage](#simplify-debugging)
- [Réduire la complexité](#reduce-complexity)

Dans cet article, nous allons démontrer les trois premiers avantages en utilisant un exemple de mesure de la croissance des ventes année par année. (La formule de croissance des ventes année par année est : période de vente _ventes inférieures pendant la même période de l’année précédente, _divisée par_ ventes pendant la même période de l’année précédente.)

Commençons par la définition de mesure suivante.

```dax
Sales YoY Growth % =
DIVIDE(
    ([Sales] - CALCULATE([Sales], PARALLELPERIOD('Date'[Date], -12, MONTH))),
    CALCULATE([Sales], PARALLELPERIOD('Date'[Date], -12, MONTH))
)
```

La mesure produit le résultat correct, mais intéressons-nous maintenant à la manière de l’améliorer.

## <a name="improve-performance"></a>Améliorer les performances

Notez que la formule répète l’expression qui calcule « même période de l’année précédente ». Cette formule est inefficace, car elle demande que Power BI évalue deux fois la même expression. La définition de mesure peut être rendue plus efficace à l’aide d’une variable.

La définition de mesure suivante représente une amélioration. Elle utilise une expression pour affecter le résultat « même période de l’année précédente » à une variable nommée **SalesPriorYear**. La variable est ensuite utilisée deux fois dans l’expression RETURN.

```dax
Sales YoY Growth % =
VAR SalesPriorYear =
    CALCULATE([Sales], PARALLELPERIOD('Date'[Date], -12, MONTH))
RETURN
    DIVIDE(([Sales] - SalesPriorYear), SalesPriorYear)
```

La mesure continue à produire le résultat correct et le fait environ deux fois plus vite.

## <a name="improve-readability"></a>Améliorer la lisibilité

Dans la définition de mesure précédente, remarquez comme le choix du nom de la variable rend l’expression RETURN plus simple à comprendre. L’expression est courte et auto-descriptive.

## <a name="simplify-debugging"></a>Simplifier le débogage

Les variables peuvent également vous aider à déboguer une formule. Pour tester une expression affectée à une variable, vous réécrivez provisoirement l’expression RETURN pour générer la variable.

La définition de mesure suivante retourne uniquement la variable **SalesPriorYear**. Remarquez comme elle commente l’expression RETURN prévue. Cette technique vous permet de la rétablir facilement une fois que le débogage est terminé.

```dax
Sales YoY Growth % =
VAR SalesPriorYear =
    CALCULATE([Sales], PARALLELPERIOD('Date'[Date], -12, MONTH))
RETURN
    --DIVIDE(([Sales] - SalesPriorYear), SalesPriorYear)
    SalesPriorYear
```

## <a name="reduce-complexity"></a>Réduire la complexité

Dans les versions antérieures de DAX, les variables n’étaient pas encore prises en charge. Les expressions complexes qui ont introduit de nouveaux contextes de filtre devaient utiliser les fonctions DAX [EARLIER](/dax/earlier-function-dax) ou [EARLIEST](/dax/earliest-function-dax) pour faire référence à des contextes de filtre externes. Malheureusement, les modeleurs de données ont trouvé ces fonctions difficiles à comprendre et à utiliser.

Les variables sont toujours évaluées en dehors des filtres que votre expression RETURN applique. C’est pourquoi, lorsque vous utilisez une variable dans un contexte de filtre modifié, elle obtient le même résultat que la fonction EARLIEST. L’utilisation des fonctions EARLIER ou EARLIEST peut donc être évitée. Cela signifie que vous pouvez désormais écrire des formules qui sont moins complexes et plus faciles à comprendre.

Considérez la définition de colonne calculée suivante ajoutée à la table **Subcategory**. Elle évalue un classement pour chaque sous-catégorie de produit en fonction des valeurs de la colonne **Subcategory Sales**.

```dax
Subcategory Sales Rank =
COUNTROWS(
    FILTER(
        Subcategory,
        EARLIER(Subcategory[Subcategory Sales]) < Subcategory[Subcategory Sales]
    )
) + 1
```

La fonction EARLIER est utilisée pour faire référence à la valeur de la colonne **Subcategory Sales**_dans le contexte de ligne actuel_.

La définition de colonne calculée peut être améliorée à l’aide d’une variable au lieu de la fonction EARLIER. La variable **CurrentSubcategorySales** stocke la valeur de la colonne **Subcategory Sales**_dans le contexte de ligne actuel_, puis l’expression RETURN l’utilise dans un contexte de filtre modifié.

```dax
Subcategory Sales Rank =
VAR CurrentSubcategorySales = Subcategory[Subcategory Sales]
RETURN
    COUNTROWS(
        FILTER(
            Subcategory,
            CurrentSubcategorySales < Subcategory[Subcategory Sales]
        )
    ) + 1
```

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur cet article, consultez les ressources suivantes :

- Article DAX [VAR](/dax/var-dax)
- Vous avez des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
