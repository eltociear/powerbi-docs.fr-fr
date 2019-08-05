---
title: Activer Synchroniser les segments
description: Comment ajouter la fonctionnalité de synchronisation des segments pour des visuels Power BI
author: EugeneElkin
ms.author: v-evelk
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 9966475e8bcaccad2090451b47ef09ef0a9af125
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425019"
---
# <a name="sync-slicers"></a>Synchroniser les segments

Pour prendre en charge la [synchronisation des segments](https://docs.microsoft.com/power-bi/desktop-slicers), votre visuel de segment personnalisé doit utiliser l’API 1.13 ou une version ultérieure.

Le deuxième aspect nécessaire est l’option activée dans `capabilities.json` (voir un exemple ci-dessous).

```json
{
    ...
    "supportsHighlight": true,
    "suppressDefaultTitle": true,
    "supportsSynchronizingFilterState": true,
    "sorting": {
        "default": {}
    }
}
```

Après les modifications dans `capabilities.json`, vous pouvez voir le panneau des options de synchronisation des segments lorsque vous cliquez sur votre visuel de segment personnalisé.

> [!NOTE]
> Si votre segment contient plus d’un champ (catégorie ou mesure), la fonctionnalité est désactivée, car la synchronisation des segments ne prend pas en charge plusieurs champs.

![Volet Synchroniser les segments](./media/sync-slicers-panel.png)

Dans le panneau, vous pouvez voir que la visibilité de votre segment et son filtrage peuvent être appliqués à plusieurs pages de rapport.
