---
title: 'DAX : Fonction DIVIDE ou opérateur de division (/)'
description: Conseils sur l’utilisation de la fonction DIVIDE DAX.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: v-pemyer
ms.openlocfilehash: c20a366ef657e851ef77a9649dbcc8b66b67dac0
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74695194"
---
# <a name="dax-divide-function-vs-divide-operator-"></a>DAX : Fonction DIVIDE ou opérateur de division (/)

En tant que modeleur de données, quand vous écrivez une expression DAX pour diviser un numérateur par un dénominateur, vous pouvez choisir d’utiliser la fonction [DIVIDE](/dax/divide-function-dax) ou l’opérateur de division (/, barre oblique).

Lorsque vous utilisez la fonction DIVIDE, vous devez passer les expressions de numérateur et dénominateur. Si vous le souhaitez, vous pouvez passer une valeur qui représente un _autre résultat_.

```dax
DIVIDE(<numerator>, <denominator> [,<alternateresult>])
```

La fonction DIVIDE a été conçue pour gérer automatiquement les cas de division par zéro. Si aucun autre résultat n’est passé et que le dénominateur a la valeur zéro ou BLANK, la fonction retourne BLANK. Quand un autre résultat est passé, il est retourné à la place de BLANK.

La fonction DIVIDE est pratique, car elle évite à votre expression d’avoir à commencer par tester la valeur du dénominateur. La fonction est également mieux optimisée pour tester la valeur de dénominateur que la fonction [IF](/dax/if-function-dax). Le gain de performance est significatif, car la vérification de division par zéro est coûteuse. L’utilisation poussée de DIVIDE produit une expression plus concise et plus fluide.

## <a name="example"></a>Exemple

L’expression de mesure suivante produit une division sans risque, mais elle implique l’utilisation de quatre fonctions DAX.

```dax
Profit Margin =
IF(
    OR(
        ISBLANK([Sales]),
        [Sales] == 0
    ),
    BLANK(),
    [Profit] / [Sales]
)
```

Cette expression de mesure aboutit au même résultat, mais de façon plus efficace et fluide.

```dax
Profit Margin =
DIVIDE([Profit], [Sales])
```

## <a name="recommendations"></a>Recommandations

Nous vous recommandons d’utiliser la fonction DIVIDE chaque fois que le dénominateur est une expression qui _peut_ retourner zéro ou BLANK.

Dans le cas où le dénominateur est une valeur constante, nous vous recommandons d’utiliser l’opérateur de division. Dans ce cas, la réussite de la division est garantie et votre expression est plus performante, car elle évite les tests inutiles.

Déterminez avec soin si la fonction DIVIDE doit retourner une autre valeur. Pour les mesures, il convient généralement mieux de retourner BLANK quand un résultat significatif ne peut pas être évalué. Pour plus d’informations, consultez [Éviter de convertir des blancs (BLANK) en valeurs](dax-avoid-converting-blank.md).

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur cet article, consultez les ressources suivantes :

- [Informations de référence sur DAX (Data Analysis Expressions)](/dax/)
- Vous avez des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
