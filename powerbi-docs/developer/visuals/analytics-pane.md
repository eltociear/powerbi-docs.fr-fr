---
title: Volet Analytique des visuels Power BI
description: Cet article décrit comment créer des lignes de référence dynamiques dans les visuels Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.topic: how-to
ms.subservice: powerbi-custom-visuals
ms.date: 06/18/2019
ms.openlocfilehash: e9d1479b596f563edc37f0c7a72b29c3343fed1e
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85239909"
---
# <a name="the-analytics-pane-in-power-bi-visuals"></a>Volet Analytique des visuels Power BI

Le volet **Analytique** a été introduit pour les [visuels natifs](https://docs.microsoft.com/power-bi/desktop-analytics-pane) en novembre 2018.
Cet article explique comment les visuels Power BI avec l’API v2.5.0 peuvent présenter et gérer leurs propriétés dans le volet **Analytique**.

![Le volet Analytique](media/analytics-pane/visualization-pane-analytics-tab.png)

## <a name="manage-the-analytics-pane"></a>Gérer le volet Analytique

De la même façon que vous gérez les propriétés dans le [volet **Format**](https://docs.microsoft.com/power-bi/developer/visuals/custom-visual-develop-tutorial-format-options), vous gérez le volet **Analytique** en définissant un objet dans le fichier *capabilities.json* du visuel.

Pour le volet **Analytique**, les différences sont les suivantes :

* Dans la définition de l’objet, vous ajoutez un champ **objectCategory** avec la valeur 2.

    > [!NOTE]
    > Le champ `objectCategory` facultatif a été introduit dans l’API 2.5.0. Il définit l’aspect du visuel que l’objet contrôle (1 = mise en forme, 2 = analytique). `Formatting` est utilisé pour des éléments tels que l’apparence, les couleurs, les axes et les étiquettes. `Analytics` est utilisé pour des éléments tels que les prévisions, les courbes de tendance, les lignes de référence et les formes.
    >
    > Si la valeur n’est pas spécifiée, `objectCategory` prend par défaut la valeur « Formatting ».

* L’objet doit avoir les deux propriétés suivantes :
    * `show` de type `bool`, avec la valeur par défaut `false`.
    * `displayName` de type `text`. La valeur par défaut que vous choisissez devient le nom d’affichage initial de l’instance.

```json
{
  "objects": {
    "YourAnalyticsPropertiesCard": {
      "displayName": "Your analytics properties card's name",
      "objectCategory": 2,
      "properties": {
        "show": {
          "type": {
            "bool": true
          }
        },
        "displayName": {
          "type": {
            "text": true
          }
        },
      ... //any other properties for your Analytics card
      }
    }
  ...
  }
}
```

Vous pouvez définir d’autres propriétés de la même façon que vous le feriez pour des objets **Format**. Et vous pouvez énumérer des objets comme vous le feriez dans le volet **Format**.

## <a name="known-limitations-and-issues-of-the-analytics-pane"></a>Limitations et problèmes connus du volet Analytique

* Le volet **Analytique** n’offre pas encore la prise en charge de plusieurs instances. Les objets ne peuvent pas avoir un [sélecteur](https://microsoft.github.io/PowerBI-visuals/docs/concepts/objects-and-properties/#selector) autre que statique (autrement dit, « sélecteur » : null), et les visuels Power BI ne peuvent pas avoir plusieurs instances d’une carte définies par l’utilisateur.
* Les propriétés de type `integer` ne sont pas affichées correctement. Pour résoudre ce problème, il est conseillé d’utiliser plutôt le type `numeric`.

> [!NOTE]
> * Utilisez le volet **Analytique** uniquement pour les objets qui ajoutent de nouvelles informations ou qui donnent un nouvel éclairage aux informations présentées (par exemple, des lignes de référence dynamiques qui illustrent des tendances importantes).
> * Les options qui contrôlent l’apparence du visuel (c’est-à-dire sa mise en forme) doivent être limitées au volet **Mise en forme**.
