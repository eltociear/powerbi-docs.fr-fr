---
title: Mode d’édition avancé dans les visuels Power BI
description: Cet article explique comment définir des contrôles d’interface utilisateur avancés dans les visuels Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 97242883fe90c8f5e115818a24e4bb1c49f69b77
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79380552"
---
# <a name="advanced-edit-mode-in-power-bi-visuals"></a>Mode d’édition avancé dans les visuels Power BI

Si vous souhaitez inclure des contrôles d’interface utilisateur avancés dans votre visuel Power BI, vous pouvez utiliser le mode d’édition avancé. Quand vous êtes en mode d’édition de rapport, vous sélectionnez un bouton **Modifier** pour définir le mode d’édition sur **Avancé**. Le visuel peut utiliser l’indicateur `EditMode`pour déterminer s’il doit afficher ce contrôle d’interface utilisateur.

Par défaut, le visuel ne prend pas en charge le mode d’édition avancé. Si un comportement différent est requis, vous pouvez le spécifier explicitement dans le fichier *capabilities.json* du visuel, en définissant la propriété `advancedEditModeSupport`.

Valeurs possibles :

- `0` - NotSupported

- `1` - SupportedNoAction

- `2` - SupportedInFocus

## <a name="enter-advanced-edit-mode"></a>Entrer le mode d’édition avancé

Un bouton **Modifier** s’affiche dans les cas suivants :

* La propriété `advancedEditModeSupport` est définie dans le fichier *capabilities.json* sur `SupportedNoAction` ou `SupportedInFocus`.

* Le visuel est affiché en mode d’édition de rapport.

Si la propriété `advancedEditModeSupport` n’est pas spécifiée dans le fichier *capabilities.json*, ou si elle y est définie sur `NotSupported`, le bouton **Modifier** n’est pas affiché.

![Passer au mode Édition](media/advanced-edit-mode/edit-mode.png)

Quand vous sélectionnez **Modifier**, le visuel obtient un appel update() où EditMode est défini sur `Advanced`. Selon la valeur qui est définie dans le fichier *capabilities.json*, les actions suivantes se produisent :

* `SupportedNoAction` : aucune action supplémentaire n’est requise par l’hôte.
* `SupportedInFocus` : l’hôte affiche le visuel en mode Focus.

## <a name="exit-advanced-edit-mode"></a>Quitter le mode d’édition avancé

Le bouton **Retour au rapport** est affiché dans le cas suivant :

* La propriété `advancedEditModeSupport` est définie dans le fichier *capabilities.json* sur `SupportedInFocus`.
