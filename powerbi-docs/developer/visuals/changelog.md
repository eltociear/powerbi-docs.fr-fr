---
title: Journal des modifications de l’API de visuels Power BI
description: Cet article décrit les principales modifications apportées aux différentes versions de l’API de visuels Power BI
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 03/13/2019
ms.openlocfilehash: c43542bc6c2bb0699403062f68024f9718bbbb60
ms.sourcegitcommit: 54e571a10b0fdde5cd6036017eac9ef228de5116
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501946"
---
# <a name="power-bi-visuals-api-changelog"></a>Journal des modifications de l’API de visuels Power BI
Cette page contient un récapitulatif rapide des versions de l’API. Les versions répertoriées ici sont considérées comme stables et ne changeront pas.


## <a name="api-v340"></a>API v3.4.0
  * `fetchMoreData` : nouveau paramètre `aggregateSegments` (valeur par défaut true), pour la prise en charge de fetchMoreData sans agrégation

## <a name="api-v320"></a>API v3.2.0
  * Prend en charge **[supportsMultiVisualSelection](./supportsmultivisualselection-feature.md)**

## <a name="api-v260"></a>API v2.6.0
  * Ajoute **isInFocus** pour mettre à jour l’option et la méthode **switchFocusModeState** à l’hôte du visuel
  * Prend en charge la personnalisation **sous-totaux**

## <a name="api-v250"></a>API v2.5.0
  * Prend en charge le **[Volet Analyse](./analytics-pane.md)**
  * Prend en charge les méthodes `SelectionIdBuilder` **withMatrixNode** et **withTable**
  * Ne prend plus en charge l’interface `DataRepetitionSelector`, remplacée par l’interface `data.CustomVisualOpaqueIdentity`

## <a name="api-v230"></a>API v2.3.0
  * **[API de page d’accueil](./landing-page.md)**
  * **[API de stockage local](./local-storage.md)**
  * **[API Filtre de tuple (filtre à plusieurs colonnes)](./filter-api.md#the-tuple-filter-api-multi-column-filter)**
  * **[API d’événements de rendu](./event-service.md#render-events-in-power-bi-visuals)**

## <a name="api-v220"></a>API v2.2.0
  * Prend en charge la **[Restauration du filtre JSON à partir de DataView](./filter-api.md#restore-the-json-filter-from-the-data-view)**
  * **[API ContextMenu](./context-menu.md)**

## <a name="api-v210"></a>API v2.1.0
  * Amélioration des performances :
    * Temps de chargement plus rapides
    * Encombrement mémoire plus faible
    * Données et transactions d’événement optimisées  

**Notes de publication**
* Les API de filtrage refactorisées sont disponibles dans l’API 2.2 et ne sont pas prises en charge dans l’API 2.1.
* Les visuels recevront uniquement le type de dataView qui a été déclaré dans leurs fonctionnalités. Les visuels qui utilisaient plusieurs types de dataView cesseront de fonctionner à la suite de cette mise à jour.
* Ne prend plus en charge l’interface `DataViewScopeIdentity`, remplacée par l’interface `data.DataRepetitionSelector`. Si vous utilisiez la propriété de clé de l’interface `DataViewScopeIdentity`, vous pouvez la remplacer par `JSON.stringify(identity)`
* `undefined` est remplacé par `null` à l’intérieur de la dataView. Lors d’une itération sur un tableau avec `var item in myArray`, il ignore `undefined` mais pas `null`. Les visuels qui utilisent ce modèle peuvent cesser de fonctionner après cette mise à jour. Veillez à vérifier la présence de `null` dans les tableaux :
   ```typescript
   for (var item in myArray) {
     if (!item) {
       continue;
     }
     console.log(item);
   }
   ```
* La propriété `proto` ne stocke plus les métadonnées/données cachées dans la dataView. Les visuels qui accèdent aux propriétés via `proto` peuvent cesser de fonctionner après cette mise à jour.

## <a name="api-v1130"></a>API v1.13.0
* Prend en charge **[Synchroniser les segments](./enable-sync-slicers.md)** . Notez que cela ne fonctionne que pour les segments à champ unique en raison de l’état actuel du code PBI. [En savoir plus](../../visuals/power-bi-visualization-slicers.md).
* Accessibilité : [Prise en charge du contraste élevé](./high-contrast-support.md) 
* Accessibilité : Autoriser l’indicateur de focus clavier

## <a name="api-v1120"></a>API v1.12.0
* Prise en charge des thèmes
* Prend en charge **[fetchMoreData](./fetch-more-data.md)** . Notez que **l’API Récupérer d’autres données** dépasse la limite ferme de 30 000 points de données
* **[API d’info-bulles de canevas](./add-tooltips.md#add-report-page-tooltips)**

## <a name="api-v1110"></a>API v1.11.0
* **[API FilterManager](./filter-api.md)**
* Prend en charge les **[signets](./bookmarks-support.md)** 

## <a name="api-v1100"></a>API v1.10.0
* Ajoute `ILocalizationManager`
* **API d’authentification**

## <a name="api-v190"></a>API v1.9.0
* **[API launchUrl](./launch-url.md)**

## <a name="api-v180"></a>API v1.8.0
* Prend en charge le nouveau type **fillRule** (gradient) dans le schéma des fonctionnalités
* Prend en charge la propriété **rule** dans le schéma des fonctionnalités pour les propriétés d’objet

## <a name="api-v170"></a>API v1.7.0
* Prend en charge **[RESJSON](./localization.md#resource-file)**

## <a name="api-v162"></a>API v1.6.2
* Prend en charge le **[mode d’édition](./advanced-edit-mode.md)** pour l’entrée en mode d’édition dans le visuel
* Prend en charge les **[visuels Power BI R interactifs (HTML)](https://github.com/Microsoft/PowerBI-visuals/blob/master/RVisualTutorial/CreateRHTML.md)** , sur la base du code HTML

## <a name="api-v150"></a>API v1.5.0
* Prend en charge **[Autoriser les interactions](./visuals-interactions.md)** pour l’interactivité visuelle

## <a name="api-v140"></a>API v1.4.0
* Prend en charge la **[localisation](./localization.md)**

## <a name="api-v130"></a>API v1.3.0
* Prend en charge les **[info-bulles](./add-tooltips.md)**

## <a name="api-v120"></a>API v1.2.0
* Ajoute **colorPalette** pour gérer les couleurs utilisées sur votre visuel.
* Prend en charge la **sélection multiple** : selectionManager peut accepter un tableau de `SelectionId`.
* Prend en charge les **[visuels R](https://github.com/Microsoft/PowerBI-visuals/blob/master/RVisualTutorial/CreateRHTML.md)** à l’aide de scripts R

## <a name="api-v110"></a>API v1.1.0
* Prend en charge le visuel de débogage dans un iFrame
* Ajoute un bac à sable (sandbox) léger et une initialisation plus rapide de l’iFrame
* Résout le problème [Capabilities.objects does not support "text" type](https://github.com/Microsoft/PowerBI-visuals-tools/issues/12)
* Prend en charge `pbiviz update` pour mettre à jour les définitions de type et le schéma des API de visuel
* Prend en charge l’indicateur `--api-version` dans `pbiviz new` pour créer des visuels avec une version d’API spécifique
* Prend en charge la version alpha de l’API v1.2.0

**Hôte de visuel**
* Ajoute **createSelectionIdBuilder** pour créer des identificateurs uniques utilisés pour la sélection des données
* Ajoute **createSelectionManager** pour gérer l’état de sélection du visuel et communiquer les modifications à l’hôte du visuel
* Ajoute un tableau de **couleurs** par défaut à utiliser dans les visuels

## <a name="api-v100"></a>API v1.0.0
* Version initiale de l’API
