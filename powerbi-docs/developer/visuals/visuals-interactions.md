---
title: Interactions entre les visuels dans les visuels Power BI
description: Cet article explique comment vérifier si les visuels Power BI doivent autoriser les interactions entre les visuels.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: b8b1a1a59ee9fae5a1c248548a14c5f91438edc9
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73875512"
---
# <a name="visual-interactions-in-power-bi-visuals"></a>Interactions entre les visuels dans les visuels Power BI

Les visuels peuvent interroger la valeur de l’indicateur `allowInteractions`, qui spécifie si le visuel doit autoriser les interactions entre les visuels. Par exemple, les visuels sont interactifs pendant l’affichage ou la modification d’un rapport, mais pas quand ils sont affichés dans un tableau de bord. Les interactions possibles sont le *clic*, le *panoramique*, le *zoom* et la *sélection*, entre autres. 

> [!NOTE]
> Vous devez activer les info-bulles dans tous les scénarios, quel que soit l’indicateur utilisé.

L’indicateur `allowInteractions` est passé en tant que valeur booléenne durant l’initialisation du visuel, comme membre de l’interface IVisualHost.

Dans les scénarios Power BI où les visuels ne doivent pas être interactifs (par exemple, les vignettes de tableau de bord), l’indicateur `allowInteractions` est défini sur `false`. Dans tous les autres scénarios (par exemple, les rapports), `allowInteractions` est défini sur `true`.

Pour plus d’informations, consultez [Référentiel visuel SampleBarChart](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/59a47935d8f5272ce145fe804193599ddb7e2001).

```typescript
   ...
   let allowInteractions = options.host.allowInteractions;
   bars.on('click', function(d) {
       if (allowInteractions) {
           selectionManager.select(d.selectionId);
           ...
       }
   });
```
