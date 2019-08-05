---
title: Interactions entre les visuels
description: Comment vérifier qu’un visuel Power BI autorise les interactions visuelles
author: shaym83
ms.author: shaym
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 739e59c6da3c1e464e0462a928bc4f33ea0d01f8
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424490"
---
# <a name="visuals-interactions"></a>Interactions entre les visuels

Les visuels peuvent interroger la valeur de l’indicateur « allowInteractions », indiquant si le visuel doit autoriser les interactions visuelles.
Par exemple, les visuels sont interactifs lors de l’affichage ou de la modification d’un rapport, mais pas dans le cas d’un affichage au sein d’un tableau de bord.
Ces interactions sont le clic, le panoramique, le zoom, la sélection et d’autres.
Notez que les info-bulles doivent être activées dans tous les scénarios, quel que soit l’indicateur.

L’indicateur « allowInteractions » est passé en tant que valeur booléenne pendant l’initialisation du visuel, en tant que membre de l’interface IVisualHost.

Dans tout scénario Power BI nécessitant que les visuels ne soient pas interactifs (par exemple, des vignettes de tableau de bord), l’indicateur « allowInteractions » est défini sur false.
Dans le cas contraire (par exemple, un rapport), « allowInteractions » aura la valeur true.

Pour plus d’informations, consultez [Référentiel visuel SampleBarChart](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/59a47935d8f5272ce145fe804193599ddb7e2001)

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
