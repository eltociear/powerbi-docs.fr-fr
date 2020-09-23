---
title: 'DAX : Références de colonne et de mesure'
description: Aide sur les références de colonne et de mesure dans vos expressions DAX.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/18/2019
ms.author: v-pemyer
ms.openlocfilehash: d3a7c39d659dacb8a44728518e239cd481ba951d
ms.sourcegitcommit: cff93e604e2c5f24e0f03d6dbdcd10c2332aa487
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90965228"
---
# <a name="dax-column-and-measure-references"></a>DAX : Références de colonne et de mesure

Parce qu’elles modélisent les données, vos expressions DAX référencent des colonnes et des mesures de modèle. Les colonnes et les mesures sont toujours associées à des tables de modèle, mais le type d’association est différent. Nous avons donc des recommandations différentes sur la façon dont vous les référencez dans vos expressions.

## <a name="columns"></a>Colonnes

Une colonne est un objet de niveau table et son nom doit être unique dans une table. Vous pouvez donc avoir le même nom de colonne plusieurs fois dans votre modèle, à condition que ces colonnes appartiennent à des tables différentes. Il existe une autre règle : un nom de colonne ne peut pas être identique à un nom de mesure ou un nom de hiérarchie qui existe dans la même table.

En général, DAX n’impose pas de référence _complète_ à une colonne. Une référence complète signifie que le nom de table précède le nom de colonne.

Voici un exemple de définition de colonne calculée qui utilise uniquement des références de nom de colonne. Les colonnes **Sales** et **Cost** appartiennent toutes deux à une table nommée **Orders**.

```dax
Profit = [Sales] - [Cost]
```

La même définition peut être réécrite avec des références de colonne complètes.

```dax
Profit = Orders[Sales] - Orders[Cost]
```

Vous devez parfois utiliser des références de colonne complètes quand Power BI détecte une ambiguïté. Quand vous entrez une formule, un message d’erreur et un trait ondulé rouge vous avertissent. Par ailleurs, certaines fonctions DAX, comme [LOOKUPVALUE](/dax/lookupvalue-function-dax), nécessitent l’utilisation de références de colonne complètes.

Nous vous recommandons de toujours utiliser des références de colonne complètes. Les raisons sont fournies dans la section [Recommandations](#recommendations).

## <a name="measures"></a>Mesures

Une mesure est un objet de niveau modèle. Pour cette raison, les noms de mesure doivent être uniques dans le modèle. Toutefois, dans le volet **Champs**, les auteurs de rapports voient chaque mesure associée à une seule table de modèle. Cette association est définie pour des raisons esthétiques, et vous pouvez la configurer en définissant la propriété **Table principale** de la mesure. Pour plus d’informations, consultez [Mesures dans Power BI Desktop (Organisation de vos mesures)](../transform-model/desktop-measures.md#organizing-your-measures).

Vous pouvez utiliser une référence de mesure complète dans vos expressions. La fonctionnalité IntelliSense de DAX vous offre même la suggestion. Toutefois, ce n’est pas nécessaire et ce n’est pas une pratique recommandée. Si vous changez la table principale d’une mesure, toute expression qui utilise une référence de mesure complète s’arrête. Vous devez ensuite modifier chaque formule rompue pour supprimer (ou mettre à jour) la référence de mesure.

Nous vous recommandons de ne jamais utiliser de références complètes de mesure. Les raisons sont fournies dans la section [Recommandations](#recommendations).

## <a name="recommendations"></a>Recommandations

Nos recommandations sont simples et faciles à mémoriser :

- Toujours utiliser des références de colonne complètes
- Ne jamais utiliser de références de mesure complètes

Voici pourquoi :

- **Entrée de formule** : Les expressions sont acceptées, car il n’y a pas de référence ambiguë à résoudre. Par ailleurs, vous respectez les exigences de ces fonctions DAX qui demandent des références de colonne complètes.
- **Robustesse** : Les expressions continuent de fonctionner, même quand vous changez la propriété de table principale d’une mesure.
- **Lisibilité** : Les expressions sont rapides et faciles à comprendre : vous déterminez rapidement s’il s’agit d’une colonne ou d’une mesure, selon que sa référence est complète ou non.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur cet article, consultez les ressources suivantes :

- [Informations de référence sur DAX (Data Analysis Expressions)](/dax/)
- Parcours d’apprentissage : [Utiliser DAX dans Power BI Desktop](/learn/paths/dax-power-bi/)
- Des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
- Vous avez des suggestions ? [Envoyez-nous vos idées pour améliorer Power BI](https://ideas.powerbi.com)