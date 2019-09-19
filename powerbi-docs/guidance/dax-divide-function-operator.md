---
title: 'DAX : Fonction DIVIDE ou opérateur de division (/)'
description: Conseils sur l’utilisation de la fonction DIVIDE DAX.
author: peter-myers
manager: asaxton
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: v-pemyer
ms.openlocfilehash: 7516aaedb886e7b9e0f57ed76f0a7c5e40efbd6d
ms.sourcegitcommit: 6a44cb5b0328b60ebe7710378287f1e20bc55a25
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70877862"
---
# <a name="dax-divide-function-vs-divide-operator-"></a>DAX : Fonction DIVIDE ou opérateur de division (/)

Cet article cible les modélisateurs de données qui définissent des expressions DAX.

## <a name="background"></a>Arrière-plan

Quand vous écrivez une expression DAX pour diviser un numérateur par un dénominateur, vous pouvez choisir d’utiliser la fonction [DIVIDE](/dax/divide-function-dax) ou l’opérateur de division (/, barre oblique).

Lorsque vous utilisez la fonction DIVIDE, vous devez passer les expressions de numérateur et dénominateur. Si vous le souhaitez, vous pouvez passer une valeur qui représente un autre résultat.

```dax

DIVIDE(<numerator>, <denominator> [,<alternateresult>])

```

La fonction DIVIDE a été conçue pour gérer automatiquement les cas de division par zéro. Si aucun autre résultat n’est passé et que le dénominateur a la valeur zéro ou BLANK, la fonction retourne BLANK. Si un autre résultat est passé, il est retourné à la place de BLANK.

La fonction DIVIDE est pratique, car elle évite à votre expression d’avoir à commencer par tester la valeur du dénominateur. La fonction est également mieux optimisée pour tester la valeur de dénominateur que la fonction [IF](/dax/if-function-dax). Le gain de performance est significatif, car la vérification de division par zéro est coûteuse. L’utilisation de DIVIDE produit également une expression plus concise et plus fluide.

## <a name="example"></a>Example

L’expression de mesure suivante produit une division sans risque, mais elle implique l’utilisation de quatre fonctions DAX.

```dax

=IF(OR(ISBLANK([Sales]), [Sales] == 0), BLANK(), [Profit] / [Sales])

```

Cette expression de mesure aboutit au même résultat, mais de façon plus efficace et fluide.

```dax

=DIVIDE([Profit], [Sales])

```

## <a name="recommendations"></a>Recommandations

Nous vous recommandons d’utiliser la fonction DIVIDE chaque fois que le dénominateur est une expression qui _peut_ retourner zéro ou BLANK.

Dans le cas où le dénominateur est une valeur constante, nous vous recommandons d’utiliser l’opérateur de division. Dans ce cas, la réussite de la division est garantie et votre expression est plus performante, car elle évite les tests inutiles.

Vous devez déterminer avec soin si la fonction DIVIDE doit retourner une autre valeur. Pour les mesures, il est généralement préférable qu’elles retournent BLANK. Ceci est dû au fait que les visuels de rapport éliminent par défaut les regroupements lorsque les résumés ont la valeur BLANK. Cela permet au visuel de se concentrer sur les groupes où il existe des données. Si nécessaire, vous pouvez configurer le visuel pour afficher tous les groupes (qui retournent des valeurs ou BLANK) dans le contexte de filtre en activant l’option « Afficher les éléments sans données ».
