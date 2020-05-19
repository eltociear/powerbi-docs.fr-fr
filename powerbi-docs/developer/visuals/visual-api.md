---
title: API de visuel
description: Cet article explique comment utiliser l’API IVisual pour les visuels Power BI
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 03/19/2020
ms.openlocfilehash: 6ec30fdd4812427ae855ff9a167d946d2a415c28
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83302963"
---
# <a name="visual-api"></a>API de visuel
Tous les éléments visuels commencent par une classe qui implémente l’interface `IVisual`. Vous pouvez nommer la classe comme vous le souhaitez, tant qu’il existe exactement une classe qui implémente l’interface `IVisual`.

> [!NOTE]
> Le nom de la classe de visuel doit correspondre à ce qui est défini dans le fichier *pbiviz.json*.

Consultez l’exemple de classe de visuel avec les méthodes suivantes qui doivent être implémentées :

* `constructor`, un constructeur standard pour initialiser l’état du visuel
* `update`, pour mettre à jour les données du visuel
* `enumerateObjectInstances`, pour retourner des objets afin de remplir le volet de propriétés (options de mise en forme), où vous pouvez les modifier en fonction de vos besoins
* `destroy`, destructeur standard pour le nettoyage

```typescript
class MyVisual implements IVisual {
    
    constructor(options: VisualConstructorOptions) {
        //one time setup code goes here (called once)
    }
    
    public update(options: VisualUpdateOptions): void {
        //code to update your visual goes here (called on all view or data changes)
    }

    public enumerateObjectInstances(options: EnumerateVisualObjectInstancesOptions): VisualObjectInstanceEnumeration {
        //returns objects to populate the property pane (called for each object defined in capabilities)
    }
    
    public destroy(): void {
        //one time cleanup code goes here (called once)
    }
}
```

## <a name="constructor"></a>constructor

Le constructeur de la classe de visuel est appelé lorsque le visuel est instancié. Il peut être utilisé pour toutes les opérations de configuration requises par le visuel.

```typescript
constructor(options: VisualConstructorOptions)
```

**VisualConstructorOptions**

* `element: HTMLElement`, une référence à l’élément DOM qui contiendra votre visuel
* `host: IVisualHost`, une collection de propriétés et de services qui peuvent être utilisés pour interagir avec l’hôte visuel (Power BI)

   `IVisualHost` contient les services suivants :

   ```typescript
   export interface IVisualHost extends extensibility.IVisualHost {
       createSelectionIdBuilder: () => visuals.ISelectionIdBuilder;
       : () => ISelectionManager;
       colorPalette: ISandboxExtendedColorPalette;
       persistProperties: (changes: VisualObjectInstancesToPersist) => void;
       applyJsonFilter: (filter: IFilter[] | IFilter, objectName: string, propertyName: string, action: FilterAction) => void;
       tooltipService: ITooltipService;
       telemetry: ITelemetryService;
       authenticationService: IAuthenticationService;
       locale: string;
       allowInteractions: boolean;
       launchUrl: (url: string) => void;
       fetchMoreData: () => boolean;
       instanceId: string;
       refreshHostData: () => void;
       createLocalizationManager: () => ILocalizationManager;
       storageService: ILocalVisualStorageService;
       eventService: IVisualEventService;
       switchFocusModeState: (on: boolean) => void;
   }
   ```
   * `createSelectionIdBuilder`, génère et stocke des métadonnées pour les éléments sélectionnables dans votre visuel
   * `createSelectionManager`, crée le pont de communication utilisé pour notifier l’hôte du visuel des modifications de l’état de sélection, consultez [API de sélection](./selection-api.md).
   * `createLocalizationManager`, génère un gestionnaire pour faciliter la [Localisation](./localization.md)
   * `allowInteractions: boolean`, indicateur booléen qui indique si le visuel doit être interactif
   * `applyJsonFilter`, applique des types de filtres spécifiques, consultez [API de filtre](./filter-api.md)
   * `persistProperties`, permet aux utilisateurs de conserver les propriétés et de les enregistrer avec la définition du visuel, afin qu’elles soient disponibles lors du rechargement suivant
   * `eventService`, retourne un [service d’événements](./event-service.md) pour prendre en charge les événements de **Rendu**
   * `storageService`, retourne un service pour utiliser le [stockage local](./local-storage.md) dans le visuel
   * `authenticationService`, génère un service pour faciliter l’authentification de l’utilisateur
   * `tooltipService`, retourne un [service d’info-bulles](./add-tooltips.md) pour aider à utiliser des info-bulles dans le visuel
   * `launchUrl`, permet [d’ouvrir une URL](./launch-url.md) dans l’onglet suivant
   * `locale`, retourne une chaîne de paramètres régionaux, consultez [Localisation](./localization.md)
   * `instanceId`, retourne une chaîne pour identifier l’instance de visuel en cours
   * `colorPalette`, retourne la colorPalette requise pour appliquer des couleurs à vos données
   * `fetchMoreData`, prend en charge plus de données que la limite standard (1 000 lignes)
   * `switchFocusModeState`, permet de modifier l’état du mode focus

## <a name="update"></a>update

Tous les visuels doivent implémenter une méthode de mise à jour publique qui est appelée chaque fois qu’une modification est apportée à l’environnement de données ou d’hôte.

```typescript
public update(options: VisualUpdateOptions): void
```

**VisualUpdateOptions**

* `viewport: IViewport`, dimensions de la fenêtre d’affichage dans laquelle le visuel doit être rendu
* `dataViews: DataView[]`, l’objet DataView qui contient toutes les données nécessaires pour afficher votre visuel (votre visuel utilise généralement la propriété catégorique sous DataView)
* `type: VisualUpdateType`, indicateurs pour indiquer le ou les types de cette mise à jour (**Données** | **Redimensionner** | **ViewMode** | **Style** | **ResizeEnd**)
* `viewMode: ViewMode`, indicateurs pour indiquer le mode d’affichage du visuel (**Affichage** | **Modifier** | **InFocusEdit**)
* `editMode: EditMode`, indicateur qui spécifie le mode d’édition du visuel (**Par défaut** | **Avancé**) (si le visuel prend en charge **AdvancedEditMode**, il ne doit restituer ses contrôles d’interface utilisateur avancés que lorsque **editMode** est défini sur **Avancé**, voir [AdvancedEditMode](./advanced-edit-mode.md))
* `operationKind?: VisualDataChangeOperationKind`, indicateur pour indiquer le type de modification de données (**Créer** | **Ajouter**)
* `jsonFilters?: IFilter[]`, collection de filtres JSON appliqués
* `isInFocus?: boolean`, indicateur pour indiquer si le visuel est en mode focus ou non
    
## <a name="enumerateobjectinstances-optional"></a>enumerateObjectInstances `optional`

Cette méthode est appelée pour chaque objet répertorié dans les fonctionnalités. À l’aide des options (uniquement le nom actuellement), vous retournez une `VisualObjectInstanceEnumeration` avec des informations sur la façon d’afficher cette propriété.

```typescript
enumerateObjectInstances(options:EnumerateVisualObjectInstancesOptions):VisualObjectInstanceEnumeration
```

**EnumerateVisualObjectInstancesOptions**

* `objectName: string`, nom de l'objet

## <a name="destroy-optional"></a>destroy `optional`

La fonction de destruction est appelée lorsque votre visuel est déchargé et peut être utilisée pour les tâches de nettoyage, comme la suppression d’écouteurs d’événements.

``` typescript
public destroy(): void
```

> [!Note]
> Power BI n’appelle généralement pas `destroy`, car il est plus rapide de supprimer l’IFrame entier qui contient le visuel.
