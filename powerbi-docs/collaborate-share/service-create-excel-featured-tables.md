---
title: Définir des tables recommandées dans Power BI Desktop (préversion)
description: Créez des tables recommandées dans Power BI Desktop afin qu’elles s’affichent dans la galerie Types de données d’Excel.
author: maggiesMSFT
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 09/17/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: efddfbdb70b2c20ad650eda6a16a5d7defb758e8
ms.sourcegitcommit: fa0a1561aba2a392fb56e7030e1a0537806a9260
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90811848"
---
# <a name="set-featured-tables-in-power-bi-desktop-preview"></a>Définir des tables recommandées dans Power BI Desktop (préversion)

Dans la galerie Types de données d’Excel, vous pouvez rechercher des données à partir des *tables recommandées* dans vos jeux de données Power BI. Dans cet article, vous allez apprendre à définir des tables comme étant *recommandées* dans vos jeux de données. Ces étiquettes permettent aux utilisateurs d’ajouter plus facilement des données d’entreprise à leurs feuilles Excel. Voici les étapes de base de la définition et du partage de tables recommandées.

1. Vous identifiez les tables recommandées dans vos jeux de données dans Power BI Desktop (cet article)
1. Vous enregistrez ces jeux de données avec les tables recommandées dans l’un des nouveaux espaces de travail. Les créateurs de rapports peuvent créer des rapports avec ces tables recommandées. 
1. Le reste de l’organisation peut se connecter à ces tables recommandées, appelées *types de données* dans Excel, pour disposer de données pertinentes et actualisables. L’article [Accéder aux tables recommandées Power BI dans Excel (préversion)](service-excel-featured-tables.md) décrit la consommation de ces tables recommandées dans Excel.

> [!NOTE]
> Vous pouvez [promouvoir ou certifier des jeux de données dans Power BI](../connect-data/service-datasets-promote.md). Cela s’appelle l’*approbation*. Excel hiérarchise les tables des jeux de données approuvés dans la galerie Types de données. Excel liste d’abord les tableaux recommandés dans les jeux de données certifiés, puis les tables des jeux de données promus. Viennent ensuite les tables recommandées des jeux de données approuvés. 

## <a name="turn-on-the-featured-table-preview"></a>Activer l’aperçu de la table recommandée

1. Dans Power BI Desktop, sélectionnez **Fichier** > **Options et paramètres** > **Options** > **Fonctionnalités en préversion**.
2. Activez la case à cocher **Tables recommandées**.

    :::image type="content" source="media/service-excel-featured-tables/power-bi-preview-featured-tables.png" alt-text="Option Aperçu des tables recommandées":::

3. Redémarrez Power BI Desktop.

## <a name="select-a-table"></a>Sélectionner une table

1. Dans Power BI Desktop, accédez à la vue Modèle.

    :::image type="content" source="media/service-excel-featured-tables/power-bi-model-view.png" alt-text="Option Aperçu des tables recommandées":::
 
2. Sélectionnez une table et définissez **Est une table proposée** sur **Oui**.

    :::image type="content" source="media/service-excel-featured-tables/power-bi-featured-table-yes.png" alt-text="Option Aperçu des tables recommandées":::

4. Dans **Configurer cette table recommandée**, renseignez les champs requis :

    - Une **Description**. 
        > [!TIP]
        > Démarrez la description par « Table recommandée » pour aider les créateurs de rapports Power BI à identifier la table recommandée.
    - La valeur du champ **Étiquette de ligne** est utilisée dans Excel afin que les utilisateurs puissent facilement identifier la ligne. Elle apparaît en tant que valeur de cellule pour une cellule liée, dans le volet **Sélecteur de données** et dans la carte **Informations**. 
    - La valeur du champ **Colonne clé** fournit l’ID unique de la ligne. Cette valeur permet à Excel de lier une cellule à une ligne spécifique de la table.

    :::image type="content" source="media/service-excel-featured-tables/power-bi-set-up-featured-table.png" alt-text="Option Aperçu des tables recommandées":::

1. Une fois que vous avez publié ou importé le jeu de données dans le service Power BI, la table recommandée s’affiche dans la galerie Types de données d’Excel. Vous et d’autres créateurs de rapports pouvez également créer des rapports basés sur ce jeu de données.

1. Dans Excel : 
    - Excel met en cache la liste de types de données, ce qui vous permet de redémarrer Excel pour voir les tables recommandées qui viennent d’être publiées.
    - Certains jeux de données ne sont pas pris en charge dans la préversion, et les tables recommandées définies dans ces jeux de données n’apparaissent pas dans Excel. Pour plus d’informations, consultez la section suivante, Considérations et limitations.

## <a name="considerations-and-limitations"></a>Considérations et limitations

Voici les limitations de la préversion initiale.

- Les tables recommandées dans les jeux de données Power BI qui utilisent les fonctionnalités suivantes ne sont pas affichées dans Excel :

    - Jeux de données DirectQuery.
    - Jeux de données avec une connexion active.

- Excel affiche uniquement les données dans les colonnes et les colonnes calculées dans la table recommandée. Ni les mesures définies sur des tables associées, ni les mesures implicites calculées à partir de relations ne sont fournies dans la préversion initiale.
- Excel affiche uniquement les tables recommandées qui sont stockées dans les nouveaux espaces de travail Power BI. Les tables recommandées stockées dans les espaces de travail classiques n’apparaissent pas comme types de données dans Excel. Vous pouvez [Mettre à niveau les espaces de travail classiques vers de nouveaux espaces de travail](service-upgrade-workspaces.md) dans Power BI.
- Pour plus d’informations sur les autres considérations relatives à Excel, consultez [Considérations et limitations](service-excel-featured-tables.md#considerations-and-limitations) dans l’article « Accéder aux tables recommandées Power BI dans Excel ».

## <a name="next-steps"></a>Étapes suivantes

- [Accéder aux tables recommandées Power BI dans Excel](service-excel-featured-tables.md)
- Vous trouverez des informations sur l’utilisation des [types de données Excel depuis Power BI](https://support.office.com/article/use-excel-data-types-from-power-bi-preview-cd8938ce-f963-444d-b82a-7140848241e9) dans la documentation Excel.
- Vous avez des questions ? [Essayez la communauté Power BI](https://community.powerbi.com/)

