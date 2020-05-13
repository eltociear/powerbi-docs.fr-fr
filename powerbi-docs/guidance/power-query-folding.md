---
title: Aide sur le Query Folding dans Power BI Desktop
description: Aide sur le Query Folding de Power Query dans Power BI Desktop.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/09/2019
ms.author: v-pemyer
ms.openlocfilehash: 271ccd9abcba8fe75f0ad66a88cb970584855a35
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83149174"
---
# <a name="query-folding-guidance-in-power-bi-desktop"></a>Aide sur le Query Folding dans Power BI Desktop

Cet article s’adresse aux modélisateurs de données développant des modèles dans Power BI Desktop. Il fournit des conseils sur les bonnes pratiques pour savoir quand et comment utiliser le Query Folding de Power Query.

Le _Query Folding_ permet à une requête Power Query de générer une seule instruction de requête afin de récupérer et transformer des données sources. Pour plus d’informations, consultez [Query Folding de Power Query](/power-query/power-query-folding).

## <a name="guidance"></a>Instructions

L’aide sur le Query Folding diffère selon le mode du modèle.

Pour une table avec un mode de stockage **DirectQuery** ou **Double**, la requête Power Query doit utiliser le Query Folding.

Pour une table d’**importation**, vous pouvez peut-être utiliser le Query Folding. Quand une requête est basée sur une source relationnelle, et dans l’hypothèse où une seule instruction SELECT peut être construite, vous obtenez les _meilleures performances d’actualisation des données_ en garantissant le Query Folding. Si le moteur mashup Power Query est toujours nécessaire pour traiter les transformations, vous devez réduire au minimum le travail qu’il doit effectuer, en particulier pour les grands jeux de données.

La liste à puces suivante fournit une aide spécifique.

- **Déléguer la plus grande partie possible du traitement à la source de données** : Quand toutes les étapes d’une requête Power Query ne peuvent pas être pliées, découvrez l’étape qui empêche le Query Folding. Dans la mesure du possible, avancez les étapes ultérieures dans la séquence pour qu’elles puissent être prises en compte dans le Query Folding. Notez que le moteur mashup Power Query peut être suffisamment intelligent pour réorganiser vos étapes de requête quand il génère la requête source.

    Pour une source de données relationnelle, si l’étape qui empêche le Query Folding peut être obtenue dans une seule instruction SELECT (ou dans la logique procédurale d’une procédure stockée), utilisez une requête SQL native, comme décrit ci-après.

- **Utiliser une requête SQL native** : Quand une requête Power Query récupère des données d’une source relationnelle, certaines sources peuvent utiliser une requête SQL native. La requête peut en fait être toute instruction valide, y compris l’exécution d’une procédure stockée. Si l’instruction génère plusieurs jeux de résultats, seul le premier est retourné. Les paramètres peuvent être déclarés dans l’instruction et nous vous recommandons d’utiliser la fonction M [Value.NativeQuery](/powerquery-m/value-nativequery). Cette fonction a été conçue pour passer des valeurs de paramètre de manière sécurisée et pratique. Comprenez bien que le moteur mashup Power Query ne peut pas plier les étapes de requête ultérieures. Vous devez donc inclure toute la logique de transformation (dans la mesure du possible) dans l’instruction de requête native.

    Quand vous utilisez des requêtes SQL natives, gardez à l’esprit deux points importants :

    - Pour une table de modèle DirectQuery, la requête doit être une instruction SELECT et ne peut pas utiliser d’expressions de table communes (CTE) ou de procédure stockée.
    - L’actualisation incrémentielle ne peut pas utiliser de requête SQL native. Elle force donc le moteur mashup Power Query à récupérer toutes les lignes sources, puis à appliquer des filtres pour déterminer les changements incrémentiels.

    > [!IMPORTANT]
    > Une requête SQL native ne se limite pas forcément à récupérer des données. Toute instruction valide peut être exécutée (éventuellement plusieurs fois), y compris pour modifier ou supprimer des données. Appliquez bien le principe du moindre privilège pour veiller à ce que le compte utilisé pour accéder à la base de données ait uniquement une autorisation de lecture sur les données demandées.

- **Préparer et transformer les données dans la source** : Quand vous déterminez que certaines étapes de requête Power Query ne peuvent pas être pliées, vous pouvez parfois appliquer les transformations dans la source de données. Pour obtenir les transformations, vous écrivez une vue de base de données qui transforme logiquement les données sources. Vous pouvez aussi préparer physiquement les données et les matérialiser avant que Power BI ne les interroge. Généralement composé de sources pré-intégrées de données organisationnelles, un entrepôt de données relationnelles est un excellent exemple de données préparées.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur cet article, consultez les ressources suivantes :

- Article sur le concept du [Query Folding](/power-query/power-query-folding) de Power Query
- [Actualisation incrémentielle dans Power BI Premium](../admin/service-premium-incremental-refresh.md)
- Vous avez des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
