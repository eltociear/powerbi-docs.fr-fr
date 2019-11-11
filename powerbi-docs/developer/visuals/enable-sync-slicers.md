---
title: Activer la fonctionnalité Synchroniser les segments dans les visuels Power BI
description: Cet article explique comment ajouter la fonctionnalité Synchroniser les segments aux visuels Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 055878988a197b80a8e4842a6567966f75af2ce5
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73880141"
---
# <a name="sync-slicers-in-power-bi-visuals"></a>Synchroniser les segments dans les visuels Power BI

Pour prendre en charge la fonctionnalité [Synchroniser les segments](https://docs.microsoft.com/power-bi/desktop-slicers), votre visuel de segment personnalisé doit utiliser l’API version 1.13 ou ultérieure.

De plus, vous devez activer l’option dans le fichier *capabilities.json*, comme illustré dans le code suivant :

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

Une fois que vous avez mis à jour le fichier *capabilities.json*, vous voyez le volet d’options **Synchroniser les segments** quand vous sélectionnez votre visuel de segment personnalisé.

> [!NOTE]
> La fonctionnalité Synchroniser les segments peut s’utiliser pour un seul champ. Si votre segment comporte plusieurs champs (**Catégorie** ou **Mesure**), la fonctionnalité est désactivée.

![Le volet « Synchroniser les segments »](./media/sync-slicers-panel.png)

Dans le panneau **Synchroniser les segments**, vous pouvez voir que les options de visibilité et de filtrage de votre segment sont applicables à plusieurs pages de rapport.
