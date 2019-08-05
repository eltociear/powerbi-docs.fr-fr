---
title: Événements de rendu
description: Les visuels Power BI peuvent notifier Power BI qu’ils sont prêts à être exportés vers Power point/PDF
author: Yarovinsky
ms.author: alexyar
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 46166b3503a770e033b98474fcf9240235296cc2
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425088"
---
# <a name="event-service"></a>Service d’événements

La nouvelle API est constituée de trois méthodes (démarrée, terminée ou en échec) qui doivent être appelées pendant le rendu.

Lorsque le rendu démarre, le code visuel personnalisé appelle la méthode renderingStarted pour indiquer le démarrage du processus de rendu.

Si le rendu s’est terminé avec succès, le code visuel personnalisé appellera immédiatement la méthode `renderingFinished` pour notifier les écouteurs **(principalement « Exporter au format PDF » et « Exporter vers PowerPoint** ») que l’image du visuel est prête.

Dans le cas où un problème se produit pendant le processus de rendu, le visuel personnalisé ne se termine pas correctement. Le code visuel personnalisé doit appeler la méthode `renderingFailed` pour signaler à l’écouteur que le processus de rendu n’a pas été terminé. Cette méthode fournit également une chaîne facultative pour la cause de l’échec.

## <a name="usage"></a>Utilisation

```typescript
export interface IVisualHost extends extensibility.IVisualHost {
    eventService: IVisualEventService ;
}

/**
 * An interface for reporting rendering events
 */
export interface IVisualEventService {
    /**
     * Should be called just before the actual rendering was started. 
     * Usually at the very start of the update method.
     *
     * @param options - the visual update options received as update parameter
     */
    renderingStarted(options: VisualUpdateOptions): void;

    /**
     * Shoudl be called immediately after finishing successfull rendering.
     * 
     * @param options - the visual update options received as update parameter
     */
    renderingFinished(options: VisualUpdateOptions): void;

    /**
     * Called when rendering failed with optional reason string
     * 
     * @param options - the visual update options received as update parameter
     * @param reason - the option failure reason string
     */
    renderingFailed(options: VisualUpdateOptions, reason?: string): void;
}
```

### <a name="simple-sample-the-visual-hasnt-any-animations-on-rendering"></a>Exemple simple. Le visuel n’a pas d’animation sur le rendu

```typescript
    export class Visual implements IVisual {
        ...
        private events: IVisualEventService;
        ...

        constructor(options: VisualConstructorOptions) {
            ...
            this.events = options.host.eventService;
            ...
        }

        public update(options: VisualUpdateOptions) {
            this.events.renderingStarted(options);
            ...
            this.events.renderingFinished(options);
        }
```

### <a name="sample-the-visual-with-animation"></a>Échantillon. Le visuel avec animation

Si le visuel possède des animations ou des fonctions asynchrones pour le rendu, la méthode `renderingFinished` doit être appelée après l’animation ou au sein de la fonction asynchrone.

```typescript
    export class Visual implements IVisual {
        ...
        private events: IVisualEventService;
        private element: HTMLElement;
        ...

        constructor(options: VisualConstructorOptions) {
            ...
            this.events = options.host.eventService;
            this.element = options.element;
            ...
        }

        public update(options: VisualUpdateOptions) {
            this.events.renderingStarted(options);
            ...
            // read more https://github.com/d3/d3-transition/blob/master/README.md#transition_end
            d3.select(this.element).transition().duration(100).style("opacity","0").end().then(() => {
                // renderingFinished called after transition end
                this.events.renderingFinished(options);
            });
        }
```

## <a name="rendering-events-for-visual-certification"></a>Rendu des événements pour la certification visuelle

La prise en charge du rendu des événements par le visuel est l’une des exigences de la certification des visuels. En savoir plus sur [Critères de certification](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements)
