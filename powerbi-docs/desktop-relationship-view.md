---
title: Vue du modèle dans Power BI Desktop
description: Vue du modèle dans Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/17/2020
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: ea568c061142e66e79351de8a6c0f0603a46f775
ms.sourcegitcommit: 08f65ea314b547b41b51afef6876e56182190266
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2020
ms.locfileid: "76753219"
---
# <a name="work-with-model-view-in-power-bi-desktop"></a>Utiliser la vue du modèle dans Power BI Desktop

La *vue du modèle* présente toutes les tables, colonnes et relations de votre modèle. Cette vue peut être particulièrement utile quand votre modèle contient des relations complexes entre de nombreuses tables.

Sélectionnez l’icône **Modèle** située sur le côté de la fenêtre pour voir une vue du modèle existant. Pointez votre curseur sur une ligne de relation pour afficher les colonnes qui sont utilisées.

![Vue du modèle, Power BI Desktop](media/desktop-relationship-view/model-view-full-screen.png)

Dans la figure, la table *Stores* (Magasins) possède une colonne *StoreKey* qui est liée à la table *Sales* (Ventes), qui possède également une colonne *StoreKey*. Les deux tables ont une relation *Plusieurs-à-un* (\*:1). Une flèche au milieu de la ligne indique la direction du flux de contexte de filtre. Les flèches doubles indiquent que la direction du filtre croisé est définie sur *À double sens*.

Vous pouvez double-cliquer sur une relation pour l’ouvrir dans la boîte de dialogue **Modifier la relation**. Pour en savoir plus sur les relations, consultez [Créer et gérer des relations dans Power BI Desktop](desktop-create-and-manage-relationships.md).
