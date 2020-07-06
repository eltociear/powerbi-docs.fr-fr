---
title: Activer la fonctionnalité Synchroniser les segments dans les visuels Power BI
description: Cet article explique comment ajouter la fonctionnalité Synchroniser les segments aux visuels Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 06/18/2019
ms.openlocfilehash: 5c364713ec7e0328e8278694985950266734c91d
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85238396"
---
# <a name="sync-slicers-in-power-bi-visuals"></a>Synchroniser les segments dans les visuels Power BI

Pour que la fonctionnalité [Synchroniser les segments](https://docs.microsoft.com/power-bi/desktop-slicers) soit prise en charge, il faut que votre visuel de segment personnalisé utilise la version 1.13.0 ou une version ultérieure de l’API.

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

![Le volet « Synchroniser les segments »](media/enable-sync-slicers/sync-slicers-panel.png)

Dans le panneau **Synchroniser les segments**, vous pouvez voir que les options de visibilité et de filtrage de votre segment sont applicables à plusieurs pages de rapport.
