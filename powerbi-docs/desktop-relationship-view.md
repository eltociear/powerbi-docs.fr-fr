---
title: Vue Relation dans Power BI Desktop
description: Vue Relation dans Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: cd9671b8c38cb2aa1502c3aa00a871d125f819b1
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75760477"
---
# <a name="work-with-relationship-view-in-power-bi-desktop"></a>Utiliser la vue Relation dans Power BI Desktop
La **vue Relation** affiche toutes les tables, colonnes et relations dans votre modèle. Cela peut être particulièrement utile quand votre modèle contient des relations complexes entre de nombreuses tables.

Jetons un œil !

![](media/desktop-relationship-view/relationshipview_fullscreen.png)

**A.**  Icône de vue Relation : cliquez dessus pour afficher votre modèle dans la vue Relation.

**B.** Relation : vous pouvez pointer votre curseur sur une relation pour voir les colonnes utilisées. Double-cliquez sur une relation pour l’ouvrir dans la boîte de dialogue **Modifier la relation**. 

Dans la figure ci-dessus, vous pouvez voir que la table *Stores (Magasins)* possède une colonne *StoreKey (Clé_Magasin)* qui est liée à la table *Sales (Ventes)* , qui possède également une colonne *StoreKey*. Nous constatons qu’il s’agit d’une relation de type *plusieurs à un* (\*:1), et l’icône au milieu de la ligne indique que la direction du filtrage croisé est *À double sens*. La flèche sur l’icône indique la direction du flux de contexte de filtre.

Pour en savoir plus sur les relations, consultez [Créer et gérer des relations dans Power BI Desktop](desktop-create-and-manage-relationships.md).

