---
title: API de stockage local dans les visuels Power BI
description: L’article explique comment utiliser des API de visuels Power BI pour accéder au stockage local du navigateur
author: uve
ms.author: v-grniki
ms.reviewer: KesemSharabi
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 01/21/2019
ms.openlocfilehash: 85517fcd7ec773f947135614c94c0c4e4638ea48
ms.sourcegitcommit: 02342150eeab52b13a37b7725900eaf84de912bc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2020
ms.locfileid: "76539322"
---
# <a name="local-storage-api"></a>API de stockage local

L’API de stockage local est une API qu’un visuel personnalisé peut utiliser pour demander à l’hôte d’enregistrer ou de charger des données à partir du stockage de l’appareil. Elle est isolée dans le sens où il existe une séparation de l’accès de stockage entre les différents types de visuels.

## <a name="sample"></a>Exemple

Si le visuel personnalisé doit augmenter un compteur chaque fois que la méthode de mise à jour est appelée, mais que la valeur du compteur doit également être conservée et ne pas être réinitialisée à chaque démarrage du visuel :

```typescript
export class Visual implements IVisual {
        // ...
        private updateCountName: string = 'updateCount';
        private updateCount: number;
        private storage: ILocalVisualStorageService;
        // ...

        constructor(options: VisualConstructorOptions) {
            // ...
            this.storage = options.host.storageService;
            // ...

            this.storage.get(this.updateCountName).then(count =>
            {
                this.updateCount = +count;
            })
            .catch(() =>
            {
                this.updateCount = 0;
                this.storage.set(this.updateCountName, this.updateCount.toString());
            });
            // ...
        }

        public update(options: VisualUpdateOptions) {
            // ...
            this.updateCount++;
            this.storage.set(this.updateCountName, this.updateCount.toString());
            // ...
        }
}
```

## <a name="known-limitations-and-issues"></a>Limites et problèmes connus

L’API de stockage local n’est pas activée par défaut pour les visuels personnalisés. Si vous voulez l’activer pour votre visuel personnalisé, envoyez une demande au support technique des visuels personnalisés Power BI : `pbicvsupport@microsoft.com`  
**Notez que votre visuel doit être disponible dans [AppSource](https://appsource.microsoft.com/en-us/marketplace/apps?product=power-bi-visuals) et être [certifié](https://powerbi.microsoft.com/en-us/documentation/powerbi-custom-visuals-certified/).**
