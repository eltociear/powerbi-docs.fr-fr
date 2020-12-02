---
title: Exemple de modèle DAX
description: Exemple de modèle DAX pour la prise en charge des articles de référence.
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 06/25/2020
ms.openlocfilehash: b2930003da1593ef5d5888c611af6700e00d3d07
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96394057"
---
# <a name="dax-sample-model"></a>Exemple de modèle DAX

L’exemple de modèle **Adventure Works DW 2020** Power BI Desktop est conçu pour prendre en charge votre apprentissage DAX. Le modèle est basé sur [l’exemple d’entrepôt de données Adventure Works](/sql/samples/adventureworks-install-configure#data-warehouse-downloads) pour AdventureWorksDW2017. Toutefois, les données ont été modifiées pour s’adapter aux objectifs de l’exemple de modèle.

## <a name="scenario"></a>Scénario

:::image type="content" source="media/dax-sample-model/adventure-works-logo-150x150.png" alt-text="Une image du logo de la société Adventure Works s’affiche.":::

La société Adventure Works représente un fabricant de vélos qui vend des vélos et des accessoires à l’échelle internationale. Les données de l’entrepôt de données de la société sont stockées dans Azure SQL Database.

## <a name="model-structure"></a>Structure du modèle

Le modèle comporte sept tables :

|Table|Description|
|-----|-------|
|**Client**|Décrit les clients et leur emplacement géographique. Les clients achètent des produits en ligne (Internet Sales, Ventes sur Internet).|
|**Date**|Il existe trois relations entre les tables **Date** et **Sales** (Ventes), pour la date de commande, la date d’expédition et la date d’échéance. La relation de la date de commande est active. La société génère des rapports sur les ventes à l’aide d’un exercice qui commence le 1er juillet de chaque année. La table est marquée en tant que table de dates à l’aide de la colonne **Date**.|
|**Produit**|Stocke uniquement les produits finis.|
|**Reseller**|Décrit les revendeurs et leur emplacement géographique. Revendeurs et la vente des produits à leurs clients.|
|**Sales**|Stocke les lignes sur le grain de la ligne de commande client. Toutes les valeurs financières sont en dollars américains (USD). La première date de commande est le 1er juillet 2017 et la dernière date de commande est le 15 juin 2020.|
|**Sales Order** (Commande client)|Décrit les numéros de commande client et de ligne de commande, ainsi que le canal de vente, **Reseller** (Revendeur) ou **Internet**. Cette table a une relation un-à-un avec la table **Sales** (Ventes).|
|**Sales Territory** (Secteur de vente)|Les secteurs de vente sont organisés en groupes (Amérique du Nord, Europe et Pacifique), pays et régions. Seuls les États-Unis vendent des produits au niveau de la région.|

Le modèle ne contient aucun calcul DAX.

## <a name="download-sample"></a>Charger l’exemple

Vous pouvez télécharger le fichier de l’exemple de modèle Power BI Desktop [ici](https://aka.ms/dax-docs-sample-file).

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur cet article, consultez les ressources suivantes :

- [Informations de référence sur DAX (Data Analysis Expressions)](/dax/)
- Parcours d’apprentissage : [Utiliser DAX dans Power BI Desktop](/learn/paths/dax-power-bi/)
- Des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
- Vous avez des suggestions ? [Envoyez-nous vos idées pour améliorer Power BI](https://ideas.powerbi.com)