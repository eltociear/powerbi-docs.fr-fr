---
author: mgblythe
ms.service: powerbi
ms.topic: include
ms.date: 09/13/2019
ms.author: mblythe
ms.openlocfilehash: b2be085c48b303304d46ea93c272e6a860143c51
ms.sourcegitcommit: a97c0c34f888e44abf4c9aa657ec9463a32be06f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71074825"
---
## <a name="limitations"></a>Limites

Voici une liste des limites actuelles pour la sécurité au niveau des lignes sur les modèles cloud.

* Si vous avez précédemment défini des rôles et des règles dans le service Power BI, vous devez les recréer dans Power BI Desktop.

* Vous pouvez définir la sécurité au niveau des lignes (SNL) uniquement sur les jeux de données créés à l’aide de Power BI Desktop. Pour activer la sécurité au niveau des lignes pour les jeux de données créés avec Excel, vous devez d’abord convertir vos fichiers au format PBIX (Power BI Desktop). [En savoir plus](../desktop-import-excel-workbooks.md)

* Seules les connexions ETL et DirectQuery sont prises en charge. Les connexions actives à Analysis Services sont gérées dans le modèle local.

* Cortana n’est pas actuellement pris en charge avec la sécurité au niveau des lignes (SNL).

## <a name="known-issues"></a>Problèmes connus

Il existe un problème connu : vous obtenez un message d’erreur quand vous tentez de publier un rapport déjà publié à partir de Power BI Desktop. Le scénario est le suivant.

1. Anna possède un jeu de données publié sur le service Power BI et a configuré la sécurité au niveau des lignes.

1. Anna met à jour le rapport dans Power BI Desktop et le republie.

1. Anna reçoit une erreur.

**Solution de contournement** : republiez le fichier Power BI Desktop à partir du service Power BI jusqu’à ce que ce problème soit résolu. Pour cela, sélectionnez **Obtenir des données** > **Fichiers**.
