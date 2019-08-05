---
title: Page d’accueil
description: Comment ajouter une page d’accueil aux visuels Power BI
author: sranins
ms.author: rasala
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 44cc9314b31803c97d3203d4aab846685d8f88fa
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424881"
---
# <a name="landing-page"></a>Page d’accueil

Avec l’API 2.3.0, vous pouvez ajouter une page d’accueil à votre visuel. Pour ce faire, ajoutez `supportsLandingPage` aux fonctionnalités et affectez-lui la valeur true. Cela vous permet d’initialiser et de mettre à jour votre visuel avant d’y ajouter des données (ce qui signifie qu’il n’affichera plus de filigrane) afin que vous puissiez concevoir votre propre page d’accueil à afficher dans le visuel tant qu’il n’a pas de données.

```typescript
export class BarChart implements IVisual {
    //...
    private element: HTMLElement;
    private isLandingPageOn: boolean;
    private LandingPageRemoved: boolean;
    private LandingPage: d3.Selection<any>;

    constructor(options: VisualConstructorOptions) {
            //...
            this.element = options.element;
            //...
    }

    public update(options: VisualUpdateOptions) {
    //...
        this.HandleLandingPage(options);
    }

    private HandleLandingPage(options: VisualUpdateOptions) {
        if(!options.dataViews || !options.dataViews.length) {
            if(!this.isLandingPageOn) {
                this.isLandingPageOn = true;
                const SampleLandingPage: Element = this.createSampleLandingPage(); //create a landing page
                this.element.appendChild(SampleLandingPage);
                this.LandingPage = d3.select(SampleLandingPage);
            }

        } else {
                if(this.isLandingPageOn && !this.LandingPageRemoved){
                    this.LandingPageRemoved = true;
                    this.LandingPage.remove();
                }
        }
    }
```

Exemple

![capture d’écran de la page d’accueil](./media/landing-page.png)
