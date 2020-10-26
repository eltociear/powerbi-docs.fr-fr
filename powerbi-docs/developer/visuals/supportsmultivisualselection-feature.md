---
title: Fonctionnalité supportsMultiVisualSelection
description: Cet article explique comment utiliser la fonctionnalité supportsMultiVisualSelection dans les visuels Power BI, et ses exigences.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 04/30/2020
ms.openlocfilehash: 091bdeb4eeb4c979ccf0e79476eb081895fae2e1
ms.sourcegitcommit: 50b21718a167c2b131313b4135c8034c6f027597
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/14/2020
ms.locfileid: "92049404"
---
# <a name="use-the-supportsmultivisualselection-feature"></a>Utiliser la fonctionnalité supportsMultiVisualSelection

La fonctionnalité `supportsMultiVisualSelection` vous permet d’utiliser la sélection dans plusieurs visuels dans un rapport.

## <a name="example"></a>Exemple

Dans un rapport avec plusieurs visuels, sélectionnez deux valeurs pour que ces valeurs s’appliquent à d’autres visuels. Par exemple, dans [Exemple Analyse de la vente au détail](../../create-reports/sample-retail-analysis.md), sélectionnez **Fashions Direct** dans un visuel. Sélectionnez Ctrl et sélectionnez **Jan** dans un autre visuel. Dans le rapport, vos sélections s’appliquent aux autres visuels qui prennent en charge cette fonctionnalité. D’autres visuels s’étendent désormais à **Fashions Direct** et **Jan**.

## <a name="requirements"></a>Configuration requise

Cette fonctionnalité requiert l’API v3.2.0 ou une version ultérieure.

Vous ne pouvez pas appliquer cette fonctionnalité aux visuels d’image. Vous ne pouvez pas l’appliquer à certains éléments visuels avancés, comme les facteurs clés, les arborescences de décomposition, les visuels Questions et réponses, les zones de texte et les jauges.

## <a name="usage"></a>Utilisation

Pour utiliser la fonctionnalité `supportsMultiVisualSelection`, ajoutez le code suivant au fichier `capabilities.json` de votre visuel.

```json
    {   
            ...
        "supportsMultiVisualSelection": true
            ...
    }
```

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur les concepts de Power BI, consultez [Visuels dans Power BI](power-bi-visuals-concept.md).

Pour essayer le développement Power BI, consultez [Développement d’une carte ronde Power BI](develop-circle-card.md).
