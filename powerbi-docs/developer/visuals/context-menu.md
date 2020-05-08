---
title: Fonctionnalités et propriétés des visuels Power BI
description: Cet article décrit les fonctionnalités et propriétés des visuels Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 7d24ea77fd73ca6a83176d1b8560c88fa98a8d6b
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "79380752"
---
# <a name="add-context-menu-to-power-bi-visual"></a>Ajouter un menu contextuel à un visuel Power BI

Vous pouvez utiliser `selectionManager.showContextMenu()` avec les paramètres `selectionId` et une position (comme objet `{x:, y:}`) afin que Power BI affiche un menu contextuel pour votre visuel.

> [!IMPORTANT]
> `selectionManager.showContextMenu()` a été introduit dans Visuals API 2.2.0.

Généralement, cet élément est ajouté en tant qu'événement de clic droit (ou d’appui prolongé sur les appareils tactiles). Le menu contextuel a été ajouté à l’exemple BarChart pour référence :

```typescript
    public update(options: VisualUpdateOptions) {
        //...
        //handle context menu
        this.svg.on('contextmenu', () => {
            const mouseEvent: MouseEvent = d3.event as MouseEvent;
            const eventTarget: EventTarget = mouseEvent.target;
            let dataPoint = d3.select(eventTarget).datum();
            this.selectionManager.showContextMenu(dataPoint? dataPoint.selectionId : {}, {
                x: mouseEvent.clientX,
                y: mouseEvent.clientY
            });
            mouseEvent.preventDefault();
        });
```
