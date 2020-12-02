---
title: 'DAX : Utiliser SELECTEDVALUE à la place de VALUES'
description: Conseils d’utilisation des fonctions SELECTEDVALUE.
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 11/20/2019
ms.openlocfilehash: 1925333b935209484855dff444542a20040a0f6a
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96394218"
---
# <a name="dax-use-selectedvalue-instead-of-values"></a>DAX : Utiliser SELECTEDVALUE à la place de VALUES

En tant que modeleur de données, vous pouvez parfois avoir besoin d’écrire une expression DAX qui teste si une colonne est filtrée par une valeur spécifique.

Dans les versions antérieures de DAX, cette condition a été remplie sans problème avec un modèle impliquant trois fonctions DAX. Ces fonctions sont [IF](/dax/if-function-dax), [HASONEVALUE](/dax/hasonevalue-function-dax) et [VALUES](/dax/values-function-dax). La définition de mesure suivante présente un exemple. Elle calcule le montant des taxes de vente, mais uniquement pour les ventes effectuées auprès de clients australiens.

```dax
Australian Sales Tax =
IF(
    HASONEVALUE(Customer[Country-Region]),
    IF(
        VALUES(Customer[Country-Region]) = "Australia",
        [Sales] * 0.10
    )
)
```

Dans l’exemple, la fonction HASONEVALUE retourne TRUE uniquement quand une seule valeur filtre la colonne **Country-Region**. Quand la valeur est TRUE, la fonction VALUES est comparée au texte littéral « Australia ». Lorsque la fonction VALUES retourne la valeur TRUE, la mesure **Sales** est multipliée par 0,10 (qui représente 10 %). Si la fonction HASONEVALUE retourne la valeur FALSE (car plusieurs valeurs filtrent la colonne), la première fonction IF retourne BLANK.

L’utilisation de HASONEVALUE est une technique défensive. Elle est nécessaire parce qu’il est possible que plusieurs valeurs filtrent la colonne **Country-Region**. Dans ce cas, la fonction VALUES retourne une table de plusieurs lignes. La comparaison d’une table de plusieurs lignes à une valeur scalaire génère une erreur.

## <a name="recommendation"></a>Recommandation

Nous vous recommandons d’utiliser la fonction [SELECTEDVALUE](/dax/selectedvalue-function). Elle permet d’obtenir le même résultat que le modèle décrit dans cet article, mais de manière plus efficace et plus élégante.

En utilisant la fonction SELECTEDVALUE, l’exemple de définition de mesure est maintenant réécrit.

```dax
Australian Sales Tax =
IF(
    SELECTEDVALUE(Customer[Country-Region]) = "Australia",
    [Sales] * 0.10
)
```

> [!TIP]
> Il est possible de passer une valeur de _résultat alternatif_ dans la fonction SELECTEDVALUE. La valeur de résultat alternatif est retournée quand aucun filtre n’est appliqué ou plusieurs filtres sont appliqués à la colonne.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur cet article, consultez les ressources suivantes :

- [Informations de référence sur DAX (Data Analysis Expressions)](/dax/)
- Parcours d’apprentissage : [Utiliser DAX dans Power BI Desktop](/learn/paths/dax-power-bi/)
- Des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
- Vous avez des suggestions ? [Envoyez-nous vos idées pour améliorer Power BI](https://ideas.powerbi.com)