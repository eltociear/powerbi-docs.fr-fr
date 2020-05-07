---
title: 'DAX : Éviter de convertir des blancs (BLANK) en valeurs'
description: Conseils de conversion des blancs (BLANK) en valeurs.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/24/2019
ms.author: v-pemyer
ms.openlocfilehash: 2f70b98ed540a2e5b87e5a949e30b0c1c02069d1
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "74700383"
---
# <a name="dax-avoid-converting-blanks-to-values"></a>DAX : Éviter de convertir des blancs (BLANK) en valeurs

En tant que modeleur de données, quand vous écrivez des expressions de mesure, vous pouvez rencontrer des cas où une valeur significative ne peut pas être retournée. Dès lors, vous pouvez être tenté de retourner une valeur (comme zéro) à la place. Nous vous suggérons de déterminer soigneusement si cette conception est efficace et pratique.

Considérez la définition de mesure suivante qui convertit explicitement les résultats BLANK en zéro.

```dax
Sales (No Blank) =
IF(
    ISBLANK([Sales]),
    0,
    [Sales]
)
```

Prenons une autre définition de mesure qui convertit également les résultats BLANK en zéro.

```dax
Profit Margin =
DIVIDE([Profit], [Sales], 0)
```

La fonction [DIVIDE](/dax/divide-function-dax) divise la mesure **Profit** par la mesure **Sales**. Si le résultat est zéro ou BLANK, le troisième argument (le résultat alternatif facultatif) est retourné. Dans cet exemple, étant donné que zéro est passé comme résultat alternatif, la mesure est certaine de toujours retourner une valeur.

Ces conceptions de mesures sont inefficaces et entraînent des conceptions de rapports médiocres.

Quand elles sont ajoutées à un visuel de rapport, Power BI tente de récupérer tous les regroupements dans le contexte de filtre. L’évaluation et la récupération de résultats de requête volumineux entraînent souvent un ralentissement du rendu des rapports. Chaque exemple de mesure convertit efficacement un calcul fragmenté en calcul dense, ce qui oblige Power BI à utiliser plus de mémoire que nécessaire.

De plus, un trop grand nombre de regroupements accable souvent les utilisateurs de vos rapports.

Voyons ce qui se passe lorsque la mesure **Profit Margin** est ajoutée à un visuel de table, avec un regroupement par client.

![Un visuel de table comporte trois colonnes : Customer, Sales et Profit Margin. La table présente environ 10 lignes de données, pourtant la barre de défilement verticale indique qu’il y a beaucoup plus de lignes affichables. La colonne Sales n’affiche aucune valeur. La colonne Profit Margin affiche uniquement zéro.](media/dax-avoid-converting-blank/table-visual-poor.png)

Le visuel de table affiche un nombre décourageant de lignes. (Il existe en fait 18 484 clients dans le modèle et la table essaie donc de tous les afficher.) Remarquez que les clients en vue n’ont réalisé aucune vente. Toutefois, puisque la mesure **Profit Margin** retourne toujours une valeur, ils sont affichés.

> [!NOTE]
> Lorsqu’il y a trop de points de données à afficher dans un visuel, Power BI peut utiliser des stratégies de réduction des données pour supprimer ou synthétiser des résultats de requêtes volumineux. Pour plus d’informations, consultez [Limites et stratégies par type de visuel du point de données](../visuals/power-bi-data-points.md).

Voyons ce qui se passe lorsque la mesure **Profit Margin** est améliorée. Elle retourne désormais une seule valeur quand la mesure **Sales** n’est pas BLANK (ou zéro).

```dax
Profit Margin =
DIVIDE([Profit], [Sales])
```

Le visuel de table présente maintenant uniquement les clients qui ont effectué des ventes dans le contexte de filtre actuel. La mesure ainsi améliorée engendre une expérience plus efficace et plus pratique pour les utilisateurs de vos rapports.

![Le même visuel de table présente maintenant quatre lignes de données. Chaque ligne concerne un client pour lequel il existe une valeur de vente et pour lequel les valeurs de marge bénéficiaire sont différentes de zéro.](media/dax-avoid-converting-blank/table-visual-good.png)

> [!TIP]
> Si nécessaire, vous pouvez configurer un visuel pour afficher tous les groupes (qui retournent des valeurs ou BLANK) dans le contexte de filtre en activant l’option [Afficher les éléments sans données](../desktop-show-items-no-data.md).

## <a name="recommendation"></a>Recommandation

Nous recommandons que vos mesures retournent BLANK quand aucune valeur significative ne peut être retournée.

Cette approche de conception est efficace, car elle permet à Power BI d’afficher les rapports plus rapidement. De plus, il est préférable de retourner BLANK parce que les visuels de rapport éliminent par défaut les regroupements quand les totalisations ont la valeur BLANK.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur cet article, consultez les ressources suivantes :

- [Informations de référence sur DAX (Data Analysis Expressions)](/dax/)
- Vous avez des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
