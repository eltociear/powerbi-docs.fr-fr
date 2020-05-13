---
title: Créer un bouton d’extraction dans Power BI
description: Vous pouvez ajouter des boutons d’extraction dans les rapports Power BI pour que vos rapports se comportent comme des applications et pour approfondir l’engagement avec les utilisateurs.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/12/2020
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: d3cb3c8093446d4417a59c5f64ab6b85a765e3c8
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83301514"
---
# <a name="create-a-drill-through-button-in-power-bi-preview"></a>Créer un bouton d’extraction dans Power BI (préversion)

Lorsque vous créez un bouton dans Power BI, vous pouvez sélectionner l’action **Extraire (préversion)** . Ce type d’action crée un bouton qui permet d’accéder à une page prioritaire pour obtenir des détails filtrés par rapport à un contexte spécifique.

Un bouton d’extraction peut être utile si vous souhaitez augmenter la détectabilité de scénarios d’extraction importants dans vos rapports.

Dans cet exemple, une fois que l’utilisateur a sélectionné la barre Word dans le graphique, le bouton **Voir les détails** est activé.

![Bouton Voir les détails](media/desktop-drill-through-buttons/power-bi-drill-through-visual-button.png)

Lorsqu’un utilisateur sélectionne le bouton **Voir les détails**, il accède à la page d’analyse du panier d’achat. Comme vous pouvez le voir dans le visuel de gauche, la page d’extraction est désormais filtrée pour Word.

![Visuel filtré](media/desktop-drill-through-buttons/power-bi-drill-through-destination.png)

## <a name="set-up-a-drill-through-button"></a>Configurer un bouton d’extraction

Pour configurer un bouton d’extraction, vous devez d’abord [configurer une page d’extraction valide](desktop-drillthrough.md) au sein de votre rapport. Ensuite, vous devez créer un bouton avec **Extraire** comme type d’action et sélectionner la page d’extraction comme **Destination**.

Le bouton d’extraction a deux états (extraction activée ou désactivée) et il existe donc deux options d’info-bulle.

![Configurer le bouton d’extraction](media/desktop-drill-through-buttons/power-bi-create-drill-through-button.png)

Si vous laissez les zones d’info-bulle vides, Power BI génère automatiquement les info-bulles. Ces info-bulles sont basées sur le ou les champs de destination et d’extraction.

Voici un exemple de l’info-bulle générée automatiquement lorsque le bouton est désactivé :

« Pour extraire jusqu’à Analyse du panier d’achat (la page de destination), sélectionnez un seul point de données dans Produit (le champ d’extraction). »

![Info-bulle générée automatiquement désactivée](media/desktop-drill-through-buttons/power-bi-drill-through-tooltip-disabled.png)

Et voici un exemple de l’info-bulle générée automatiquement lorsque le bouton est désactivé :

« Cliquez pour extraire jusqu’à Analyse du panier d’achat (la page de destination). »

![Info-bulle générée automatiquement activée](media/desktop-drill-through-buttons/power-bi-drill-through-visual-button.png)

Toutefois, si vous souhaitez fournir des info-bulles personnalisées, vous pouvez toujours entrer une chaîne statique. Nous ne prenons pas encore en charge la mise en forme conditionnelle pour les info-bulles.

Vous pouvez utiliser la mise en forme conditionnelle pour modifier le texte du bouton en fonction de la valeur sélectionnée d’un champ. Pour ce faire, vous devez créer une mesure qui renvoie la chaîne souhaitée en fonction de la fonction DAX SELECTEDVALUE.

Voici un exemple de mesure qui génère la sortie « See product details » si une valeur Product unique n’est PAS sélectionnée. Dans le cas contraire, elle génère « See details for [le produit sélectionné] » :

```
String_for_button = If(SELECTEDVALUE('Product'[Product], 0) == 0), "See product details", "See details for " & SELECTEDVALUE('Product'[Product]))
```

Une fois que vous avez créé cette mesure, vous sélectionnez l’option **Mise en forme conditionnelle** pour le texte du bouton :

![Sélectionner Mise en forme conditionnelle](media/desktop-drill-through-buttons/power-bi-button-conditional-tooltip.png)

Ensuite, vous sélectionnez la mesure que vous avez créée pour le texte du bouton :

![Valeur basée sur le champ](media/desktop-drill-through-buttons/power-bi-conditional-measure.png)

Quand un produit unique est sélectionné, le texte du bouton indique :

« See details for Word »

![Quand une valeur unique est sélectionnée](media/desktop-drill-through-buttons/power-bi-conditional-button-text.png)

Si aucun produit n’est sélectionné ou si plusieurs produits sont sélectionnés, le bouton est désactivé et le texte du bouton est le suivant :

« See product details »

![Quand plusieurs valeurs sont sélectionnées](media/desktop-drill-through-buttons/power-bi-button-conditional-text-2.png)

## <a name="pass-filter-context"></a>Passer le contexte du filtre

Le bouton fonctionne comme une extraction normale et vous pouvez donc passer aussi des filtres sur des champs supplémentaires en filtrant de façon croisée les visuels qui contiennent le champ d’extraction. Par exemple, en utilisant **Ctrl** + **clic** et le filtrage croisé, vous pouvez passer plusieurs filtres sur le magasin à la page d’extraction, car vos sélections effectuent un filtrage croisé du visuel qui contient Product, le champ d’extraction :

![Passage du contexte de filtre](media/desktop-drill-through-buttons/power-bi-cross-filter-drill-through-button.png)

Lorsque vous sélectionnez le bouton d’extraction, vous voyez les filtres sur le magasin et le produit transmis à la page de destination :

![Filtres dans cette page](media/desktop-drill-through-buttons/power-bi-button-filters-passed-through.png)

### <a name="ambiguous-filter-context"></a>Contexte de filtre ambigu

Comme le bouton d’extraction n’est pas lié à un seul visuel, si votre sélection est ambiguë, le bouton est désactivé.

Dans cet exemple, le bouton est désactivé, car deux visuels contiennent chacun une sélection unique sur Product. Il y a une ambiguïté concernant le point de données de visuel auquel lier l’action d’extraction :

![Contexte de filtre ambigu](media/desktop-drill-through-buttons/power-bi-button-disabled-ambiguity.png)

## <a name="limitations"></a>Limites

- Ce bouton n’autorise pas les destinations multiples à l’aide d’un seul bouton.
- Ce bouton prend en charge uniquement les extractions dans le même rapport ; en d’autres termes, il ne prend pas en charge l’extraction interrapport.
- La mise en forme de l’état désactivé pour le bouton est liée aux classes de couleur dans votre thème de rapport. Apprenez-en davantage sur les [classes de couleur](desktop-report-themes.md#setting-structural-colors).
- L’action d’extraction fonctionne pour tous les visuels intégrés et fonctionne avec *certains* visuels importés à partir d’AppSource. Toutefois, il n’est pas garanti qu’elle fonctionnera avec *tous* les visuels importés depuis AppSource.

## <a name="next-steps"></a>Étapes suivantes
Pour plus d’informations sur les fonctionnalités qui sont similaires ou pour interagir avec des boutons, consultez les articles suivants :

* [Créer des boutons](desktop-buttons.md)
* [Utiliser l’extraction dans les rapports Power BI](desktop-drillthrough.md)
* [Utiliser des signets pour partager des insights et créer des récits dans Power BI](desktop-bookmarks.md)

