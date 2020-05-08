---
title: Ajouter une page de destination aux visuels Power BI
description: Cet article explique comment ajouter une page de destination aux visuels Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 06/18/2019
ms.openlocfilehash: 6f1590d5635ed6e55833350027c52379e5d7cf51
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "79379954"
---
# <a name="add-a-landing-page-to-your-power-bi-visuals"></a>Ajouter une page de destination aux visuels Power BI

Avec l’API 2.3.0, vous pouvez ajouter une page de destination à vos visuels Power BI. Pour cela, ajoutez `supportsLandingPage` aux fonctionnalités et affectez-lui la valeur true. Cette action initialise et met à jour votre visuel avant que vous y ajoutiez des données. Du fait que le visuel n’affiche plus de filigrane, vous pouvez concevoir votre propre page de destination à afficher dans le visuel quand celui-ci ne contient pas de données.

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

L’image suivante illustre un exemple de page de destination :

![capture d’écran de la page d’accueil](media/landing-page/app-landing-page.png)
