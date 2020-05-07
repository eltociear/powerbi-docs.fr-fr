---
title: Aide à la résolution des problèmes de relations
description: Aide à la résolution des problèmes liés aux relations de modèle.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 03/02/2020
ms.author: v-pemyer
ms.openlocfilehash: e2854d82d858bb1963b691d32d561c7b3bbfc11a
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "78263642"
---
# <a name="relationship-troubleshooting-guidance"></a>Aide à la résolution des problèmes de relations

Cet article s’adresse principalement aux modélisateurs de données qui utilisent Power BI Desktop. Il vous aide à résoudre les problèmes spécifiques que vous pouvez rencontrer lors du développement de modèles et de rapports.

[!INCLUDE [relationships-prerequisite-reading](includes/relationships-prerequisite-reading.md)]

## <a name="troubleshooting-checklist"></a>Liste de contrôle pour la résolution des problèmes

Quand un visuel de rapport est configuré pour utiliser des champs de deux tables (ou plus) et qu’il ne présente pas le résultat correct (ou pas de résultat du tout), il est possible que le problème soit lié à des relations de modèle.

Dans ce cas, voici une liste de contrôle de dépannage générale à suivre. Vous pouvez parcourir progressivement la liste de contrôle jusqu’à ce que vous ayez identifié le ou les problèmes.

1. Basculez le visuel sur une table ou une matrice, ou ouvrez le volet « Voir les données » : il est plus facile de résoudre les problèmes lorsque vous pouvez voir le résultat de la requête.
1. Si le résultat de la requête est vide, basculez vers Vue de données : vérifiez que les tables ont été chargées avec des lignes de données.
1. Basculez vers la Vue de modèle : il est facile de voir les relations et de déterminer rapidement leurs propriétés.
1. Vérifiez l’existence de relations entre les tables
1. Vérifiez que les propriétés de cardinalité sont correctement configurées. Elles peuvent être incorrectes si une colonne du côté « plusieurs » contient actuellement des valeurs uniques et si elle a été configurée de manière incorrecte en tant que côté « un »
1. Vérifiez que les relations sont actives (ligne pleine)
1. Vérifiez que les directions du filtre prennent en charge la propagation (interpréter les têtes des flèches)
1. Vérifiez que les colonnes appropriées sont associées : sélectionnez la relation ou placez le curseur dessus pour afficher les colonnes associées.
1. Vérifiez que les types de données de colonne associés sont identiques ou au moins compatibles : il est possible d’associer une colonne de texte à une colonne de nombres entiers, mais les filtres ne trouveront pas de correspondances à propager.
1. Basculez vers Vue de données et vérifiez que les valeurs correspondantes se trouvent dans des colonnes associées.

## <a name="troubleshooting-guide"></a>Guide de résolution des problèmes

Voici une liste des problèmes avec les solutions possibles.

|Problème|Raison(s) possible(s)|
|---------|---------|
|Le visuel n’affiche aucun résultat|- Le modèle n’est pas encore chargé avec les données<br />- Aucune donnée n’existe dans le contexte de filtre<br />- La sécurité au niveau des lignes est appliquée<br />- Les relations ne se propagent pas entre les tables : _suivre la liste de contrôle ci-dessus_<br />- La sécurité au niveau des lignes est appliquée, mais une relation bidirectionnelle n’est pas activée pour la propagation : consultez [Sécurité au niveau des lignes (RLS) avec Power BI Desktop](../desktop-rls.md)|
|Le visuel affiche la même valeur pour chaque regroupement |- Les relations n’existent pas<br />- Les relations ne se propagent pas entre les tables : _suivre la liste de contrôle ci-dessus_|
|Le visuel affiche des résultats, mais ils ne sont pas corrects|- Le visuel n’est pas configuré correctement.<br />- La logique de mesure est incorrecte<br />- Les données du modèle doivent être actualisées<br />- Les données sources sont incorrectes<br />- Les colonnes de relation ne sont pas liées correctement (par exemple, la colonne **ProductID** est mappée à **CustomerID**)<br />- Il s’agit d’une relation entre deux tables DirectQuery, et la colonne côté « un » d’une relation contient des valeurs dupliquées|
|Des regroupements VIDES ou des éléments de segment/filtre apparaissent, et les colonnes sources ne contiennent pas de valeurs VIDES|- Il s’agit d’une relation forte et la colonne côté « plusieurs » contient des valeurs qui ne sont pas stockées dans la colonne côté « un » : consultez [Relations de modèle dans Power BI Desktop (relations fortes)](../desktop-relationships-understand.md#strong-relationships)<br />- Il s’agit d’une relation un-à-un forte, et les colonnes associées contiennent des VIDES, consultez [Relations de modèle dans Power BI Desktop (relations fortes)](../desktop-relationships-understand.md#strong-relationships)<br />- Une colonne de relation inactive côté « plusieurs » stocke des VIDES ou contient des valeurs non stockées du côté « un »|
|Il manque des données de visuel|- Des filtres incorrects/inattendus sont appliqués<br />- La sécurité au niveau des lignes est appliquée<br />- Il s’agit d’une relation faible et il y a des VIDES dans les colonnes associées ou des problèmes d’intégrité des données : consultez [Relations de modèle dans Power BI Desktop (relations faibles)](../desktop-relationships-understand.md#weak-relationships)<br />- Il s’agit d’une relation entre deux tables DirectQuery, la relation est configurée pour [assumer l’intégrité référentielle](../desktop-relationships-understand.md#assume-referential-integrity), mais il y a des problèmes d’intégrité des données (valeurs incompatibles dans les colonnes associées)|
|La sécurité au niveau des lignes n’est pas appliquée correctement|- Les relations ne se propagent pas entre les tables : _suivre la liste de contrôle ci-dessus_<br />- La sécurité au niveau des lignes est appliquée, mais une relation bidirectionnelle n’est pas activée pour la propagation : consultez [Sécurité au niveau des lignes (RLS) avec Power BI Desktop](../desktop-rls.md)|
|||

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations en rapport avec cet article, consultez les ressources suivantes :

- [Relations de modèle dans Power BI Desktop](../desktop-relationships-understand.md)
- Des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
- Vous avez des suggestions ? [Envoyez-nous vos idées pour améliorer Power BI](https://ideas.powerbi.com/)
