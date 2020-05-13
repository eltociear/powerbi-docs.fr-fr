---
author: davidiseminger
ms.service: powerbi
ms.topic: include
ms.date: 01/31/2020
ms.author: davidi
ms.openlocfilehash: 912b0213c328c623e7881f7f30fe7d67f6d889b3
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83274631"
---
## <a name="limitations"></a>Limites

Les limitations actuelles pour la sécurité au niveau des lignes sur les modèles cloud sont les suivantes :

* Si vous avez précédemment défini des rôles et des règles dans le service Power BI, vous devez les recréer dans Power BI Desktop.

* Vous pouvez définir la sécurité au niveau des lignes (SNL) uniquement sur les jeux de données créés à l’aide de Power BI Desktop. Pour activer la sécurité au niveau des lignes pour les jeux de données créés avec Excel, vous devez d’abord convertir vos fichiers au format PBIX (Power BI Desktop). [En savoir plus](../connect-data/desktop-import-excel-workbooks.md).

* Seules les connexions Import et DirectQuery sont prises en charge. Les connexions actives à Analysis Services sont gérées dans le modèle local.

## <a name="known-issues"></a>Problèmes connus

Il existe un problème connu : vous obtenez un message d’erreur quand vous tentez de publier un rapport déjà publié à partir de Power BI Desktop. Le scénario est le suivant :

1. Anna possède un jeu de données publié sur le service Power BI et a configuré la sécurité au niveau des lignes.

1. Anna met à jour le rapport dans Power BI Desktop et le republie.

1. Anna reçoit une erreur.

**Solution de contournement :** republiez le fichier Power BI Desktop à partir du service Power BI jusqu’à ce que ce problème soit résolu. Pour cela, sélectionnez **Obtenir des données** > **Fichiers**.

