---
title: Mise en surbrillance
description: Mise en surbrillance des sélections des points de données dans les visuels Power BI
author: sranins
ms.author: rasala
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 1ee45781ddc29eee9eeab23a5d748fb7752fe907
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424812"
---
# <a name="highlight-data-points-in-power-bi-visuals"></a>Mettre en surbrillance des points de données dans les visuels Power BI

Par défaut, chaque fois qu’un élément est sélectionné, le tableau `values` de l’objet `dataView` est filtré sur les valeurs sélectionnées uniquement. Il s’ensuit que tous les autres visuels de la page affichent uniquement les données sélectionnées.

![Comportement par défaut de la mise en surbrillance de la vue de données](./media/highlight-dataview.png)

Si vous définissez la propriété `supportsHighlight` du fichier `capabilities.json` sur `true`, vous recevez le tableau `values` complet non filtré avec un tableau `highlights`. Le tableau `highlights` a la même longueur que le tableau de valeurs, et toutes les valeurs non sélectionnées sont définies sur `null`. Lorsque cette propriété est activée, il est de la responsabilité du visuel de mettre en surbrillance les données appropriées en comparant le tableau `values` au tableau `highlights`.

![Mise en surbrillance prise en charge dans la vue de données](./media/highlight-dataview-supports.png)

Dans l’exemple, vous remarquerez la barre 1 qui est sélectionnée. Il s’agit de la seule valeur du tableau des mises en surbrillance. Il est également important de noter qu’il peut y avoir plusieurs sélections et une mise en surbrillance partielle. La valeur numérique correspondante comprise dans les tableaux de valeurs et de mises en surbrillance est alors différente.
