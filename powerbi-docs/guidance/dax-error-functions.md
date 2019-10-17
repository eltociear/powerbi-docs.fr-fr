---
title: 'DAX : Utilisation appropriée des fonctions d’erreur'
description: Conseils sur l’utilisation des fonctions d’erreur DAX.
author: peter-myers
manager: asaxton
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/26/2019
ms.author: v-pemyer
ms.openlocfilehash: 0855a9ee4c699c4a3b65e4331b5af2fa68a5610c
ms.sourcegitcommit: 5e277dae93832d10033defb2a9e85ecaa8ffb8ec
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72021065"
---
# <a name="dax-appropriate-use-of-error-functions"></a>DAX : Utilisation appropriée des fonctions d’erreur

Cet article cible les modélisateurs de données qui définissent des expressions DAX.

## <a name="background"></a>Arrière-plan

Lors de l'écriture d'une expression DAX qui pourrait entraîner une erreur de temps d'évaluation, vous pouvez utiliser deux fonctions DAX pratiques.

- La fonction [ISERROR](/dax/iserror-function-dax), qui prend une seule expression et retourne la valeur TRUE si cette expression entraîne une erreur.
- La fonction [IFERROR](/dax/iferror-function-dax), qui prend deux expressions. Si la première expression entraîne une erreur, la valeur de la seconde expression est retournée. Il s’agit en fait d’une meilleure implémentation de l'imbrication de la fonction ISERROR dans une fonction [IF](/dax/if-function-dax).

Cependant, même si ces fonctions peuvent être utiles et faciliter la compréhension des expressions, elles peuvent aussi dégrader considérablement les performances des calculs. Cela s'explique par le fait que ces fonctions augmentent le nombre d'analyses requises par le moteur de stockage.

Notez que la plupart des erreurs de temps d’évaluation sont dues à des valeurs vides (BLANK) inattendues ou à des valeurs nulles, ou à une conversion de type de données non valide.

## <a name="recommendations"></a>Recommandations

Il vaut mieux éviter d'utiliser les fonctions ISERROR et IFERROR. Appliquez plutôt des stratégies défensives lors de la conception du modèle et de l'écriture des expressions. Ces stratégies peuvent inclure :

- **S'assurer que des données de qualité sont chargées dans le modèle :** Utilisez les transformations Power Query pour supprimer ou substituer des valeurs non valides ou manquantes, et pour définir des types de données corrects. Une transformation Power Query peut également être utilisée pour filtrer les lignes lorsque des erreurs, notamment une conversion de données non valide, surviennent.

    La qualité des données peut également être contrôlée en désactivant la propriété **Is Nullable** de la colonne du modèle, ce qui entraînera l’échec de l’actualisation des données si des valeurs vides (BLANK) sont détectées. Notez que si cet échec se produit, les données chargées à la suite d'une actualisation réussie resteront dans les tables.
- **Utilisation de la fonction IF :** L'expression de test logique de la fonction IF peut être utilisée pour déterminer si un résultat d'erreur se produirait. Remarque : comme les fonctions ISERROR et IFERROR, cette fonction peut entraîner des analyses supplémentaires du moteur de stockage, mais elle sera probablement plus performante car aucune erreur ne doit être déclenchée.
- **Utilisation de fonctions à tolérance d’erreur :** Certaines fonctions DAX testent et compensent les conditions d'erreur. Ces fonctions vous permettent de saisir un autre résultat qui serait renvoyé à la place. La fonction [DIVIDE](/dax/divide-function-dax) en est un exemple. Pour plus d'informations sur cette fonction, lisez l’article [DAX : fonction DIVIDE ou opérateur de division (/)](dax-divide-function-operator.md).

## <a name="example"></a>Example

L'expression de mesure suivante teste si une erreur s’affichera. Elle retourne une valeur BLANK dans ce cas (ce qui est le cas lorsque vous ne fournissez pas à la fonction IF une expression value-if-false).
```dax
= IF(ISERROR([Profit] / [Sales]))
```
Cette prochaine version de l'expression de mesure a été améliorée en utilisant la fonction IFERROR à la place des fonctions IF et ISERROR.
```dax
= IFERROR([Profit] / [Sales], BLANK())
```
Mais cette version finale de l’expression de mesure aboutit au même résultat, mais de façon plus efficace et fluide.
```dax
= DIVIDE([Profit], [Sales])
```