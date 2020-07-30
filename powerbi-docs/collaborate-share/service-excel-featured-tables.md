---
title: Accéder aux tables recommandées Power BI dans Excel (préversion)
description: Dans Excel, vous pouvez rechercher des données à partir des tables recommandées dans les jeux de données Power BI dans la galerie Types de données.
author: maggiesMSFT
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 07/24/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 00fba391a6ad92f1e3edaf0e2af9691452724f6e
ms.sourcegitcommit: 65025ab7ae57e338bdbd94be795886e5affd45b4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87251479"
---
# <a name="access-power-bi-featured-tables-in-excel-preview"></a>Accéder aux tables recommandées Power BI dans Excel (préversion)

Dans la galerie Types de données d’Excel, vous pouvez rechercher des données à partir des *tables recommandées* dans les jeux de données Power BI. Les tables recommandées facilitent l’ajout de données d’entreprise à vos feuilles Excel. Voici les étapes à suivre pour récupérer de Power BI des données dans des feuilles Excel.

- Un modéliseur de données Power BI [promeut ou certifie un jeu de données dans Power BI](../connect-data/service-datasets-promote.md).
- Le modéliseur de données [identifie les tables recommandées](service-create-excel-featured-tables.md) dans le jeu de données et enregistre ce dernier dans le service Power BI.
- Le reste de l’organisation peut se connecter à ces tables recommandées dans Excel pour disposer de données pertinentes et actualisables. Excel fait référence à ces tables en tant que *types de données* et les liste dans la galerie Types de données.

> [!NOTE]
> Dans Excel, vous pouvez également obtenir des données de n’importe quel jeu de données auquel vous pouvez accéder dans Power BI. Dans le ruban **Données**, sélectionnez **Obtenir des données** > **À partir de Power BI (Microsoft)** .
> :::image type="content" source="media/service-excel-featured-tables/excel-get-data-power-bi.png" alt-text="Capture d’écran de l’option Obtenir des données à partir de Power BI sur le ruban Données.":::

## <a name="the-excel-data-types-gallery"></a>Galerie Types de données d’Excel
Les tables recommandées dans les jeux de données Power BI s’affichent en tant que *types de données* sur le ruban **Données** dans la galerie **Types de données** d’Excel.

:::image type="content" source="media/service-excel-featured-tables/excel-data-ribbon.png" alt-text="Capture d’écran de la galerie Types de données dans le ruban Données d’Excel":::

Une fois développée, la galerie affiche les types de données génériques, tels que **Données boursières** et **Données géographiques**, ainsi que les 10 principaux types de données **Organisation** mis à votre disposition, qui sont les tables recommandées issues des jeux de données Power BI.

:::image type="content" source="media/service-excel-featured-tables/excel-data-types-gallery.png" alt-text="Capture d’écran de la galerie Types de données d’Excel":::

## <a name="format-a-range-of-cells-as-a-table-optional"></a>Mettre en forme une plage de cellules en tant que tableau (facultatif)

 Avant toute chose, nous vous recommandons de mettre en forme vos données sous forme de tableau Excel. Ainsi, les modifications que vous apportez à une ligne s’appliquent aux autres lignes du tableau. 

1. Ajoutez un en-tête de colonne. 
2. Sélectionnez ensuite une cellule dans vos données et appuyez sur Ctrl+L. 
3. Cochez la case **Mon tableau comporte des en-têtes** > **OK**.

    :::image type="content" source="media/service-excel-featured-tables/excel-format-table.png" alt-text="Capture d’écran de la conversion d’une plage en tableau":::

## <a name="search-for-power-bi-data-in-the-excel-data-types-gallery"></a>Rechercher des données Power BI dans la galerie Types de données d’Excel

Pour rechercher des données dans une table recommandée Power BI, sélectionnez une cellule ou une plage dans votre feuille Excel contenant une valeur qui correspond à la valeur dans la table recommandée. Sélectionnez **Organisation**. Excel explore toutes les tables recommandées auxquelles vous avez accès, en recherchant une correspondance.

:::image type="content" source="media/service-excel-featured-tables/excel-table-organization.png" alt-text="Capture d’écran de la sélection d’une cellule ou d’une plage de cellules":::
 
Si vous savez quelle table recommandée vous recherchez, sélectionnez **$$$À partir de votre organisation (préversion)** dans la galerie, puis sélectionnez-la.

:::image type="content" source="media/service-excel-featured-tables/excel-organizational-data-table.png" alt-text="Capture d’écran des données organisationnelles dans Excel - Tableau avec le type de données Fournisseurs.":::
 
Quand vous effectuez une recherche, si Excel trouve des lignes correspondantes avec un niveau de confiance élevé, les cellules sont immédiatement liées à ces lignes. L’icône d’élément lié indique que les cellules sont liées aux lignes dans Power BI.

:::image type="content" source="media/service-excel-featured-tables/excel-linked-card-icon.png" alt-text="Capture d’écran de l’icône d’élément lié":::

Si une cellule contient plusieurs lignes possibles correspondantes, la cellule affiche une icône de point d’interrogation et le volet **Sélecteur de données** s’ouvre. Dans l’exemple suivant, l’utilisateur a sélectionné la plage B2:B10 et recherché une table recommandée Power BI. Toutes les lignes ont des correspondances, à l’exception de la cellule B5, « Ma Maison ». Le **Sélecteur de données** affiche deux correspondances possibles.

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-pane.png" alt-text="Capture d’écran du volet Sélecteur de données d’Excel":::
 
L’option Données organisationnelles peut retourner des lignes de plusieurs tables recommandées. Excel regroupe les lignes potentiellement correspondantes selon le type de données à partir duquel elles proviennent. Excel trie les types de données en fonction de leur ligne de correspondance la plus probable. Utilisez les flèches pour réduire et développer les types de données pour les lignes correspondantes.

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-multiple.png" alt-text="Capture d’écran du volet Sélecteur de données d’Excel avec plusieurs possibilités":::
 
Pour chaque ligne, sélectionnez le nom de la ligne pour afficher plus de détails au sein de cette ligne pour vous aider à choisir la bonne ligne. Une fois que vous l’avez trouvée, appuyez sur **Sélectionner** pour lier la ligne à la cellule dans Excel. 

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-details.png" alt-text="Capture d’écran des détails du sélecteur de données":::
 
La sélection de l’icône **Fiche** dans la cellule affiche une fiche contenant les données des champs et des champs calculés dans la table recommandée. Le titre de la fiche affiche la valeur du champ d’étiquette de ligne dans la table recommandée.
 
:::image type="content" source="media/service-excel-featured-tables/excel-linked-item-details.png" alt-text="Capture d’écran des détails de l’élément lié":::

Sélectionnez l’icône **Insérer des données**, puis sélectionnez un nom de champ dans la liste des champs pour ajouter sa valeur à la grille.  

:::image type="content" source="media/service-excel-featured-tables/excel-select-field.png" alt-text="Capture d’écran de la sélection d’un nom de champ":::

La ou les valeurs du champ sont placées dans les cellules adjacentes. La formule de la cellule fait référence à la cellule liée et au nom du champ, ce qui vous permet d’utiliser les données dans des fonctions Excel.

:::image type="content" source="media/service-excel-featured-tables/excel-cell-formula.png" alt-text="Capture d’écran de la formule de la cellule Excel":::

## <a name="cell-formulas"></a>Formules de cellule

Lorsque vous utilisez un tableau Excel, vous pouvez faire référence à la colonne de la table liée, puis ajouter des champs de données à l’aide de la référence `.` (point).

:::image type="content" source="media/service-excel-featured-tables/excel-dot-reference.png" alt-text="Capture d’écran de la référence (point) Excel":::

De même, lorsque vous utilisez une cellule, vous pouvez vous référer à la cellule et utiliser la référence `.` (point) pour extraire des champs.

:::image type="content" source="media/service-excel-featured-tables/excel-cell-dot-reference.png" alt-text="Capture d’écran de la référence (point) pour une cellule":::
 
## <a name="data-caching-and-refresh"></a>Mise en cache et actualisation des données

Quand Excel lie une cellule à une ligne dans une table Power BI recommandée, il récupère et enregistre toutes les valeurs de champ dans le fichier Excel. Toute personne avec laquelle vous partagez le fichier peut faire référence à n’importe quel champ, sans demander de données de Power BI.  

Utilisez le bouton **Actualiser tout** dans le ruban **Données** pour actualiser les données des cellules liées. 

:::image type="content" source="media/service-excel-featured-tables/excel-refresh-all.png" alt-text="Capture d’écran de l’option Actualiser tout":::
 
Vous pouvez également actualiser les cellules une par une. Cliquez avec le bouton droit sur la cellule, puis sélectionnez **Types de données** > **Actualiser**.

## <a name="show-a-card-change-or-convert-to-text"></a>Afficher une carte, modifier ou convertir en texte

Les cellules liées ont des options de menu contextuel supplémentaires. Cliquez avec le bouton droit sur une cellule. Avec les options habituelles, vous pouvez également voir les éléments suivants :

- **Montrer la fiche du type de données**
- **Actualiser**.
- **Modifier**.
- **Convertir en texte**.

:::image type="content" source="media/service-excel-featured-tables/excel-right-click-data-type.png" alt-text="Capture d’écran de l’option Convertir en texte, accessible via un clic droit.":::
 
**Convertir en texte** supprime le lien vers la ligne dans la table Power BI recommandée. Il convient de noter que le texte de la cellule sera la valeur de l’étiquette de ligne de la cellule liée. Si vous avez lié une cellule à une ligne par inadvertance, sélectionnez **Annuler** dans Excel pour restaurer les valeurs de cellule initiales.

## <a name="licensing"></a>Licences

La galerie Types de données Excel et les expériences connectées aux tables Power BI recommandées sont uniquement disponibles pour les clients Excel E5 et G5. 

## <a name="security"></a>Sécurité

Vous voyez uniquement les tables recommandées des jeux de données pour lesquels vous disposez de l’autorisation dans Power BI. Lors de l’actualisation des données, vous devez avoir l’autorisation d’accéder au jeu de données dans Power BI pour récupérer les lignes. Cela nécessite l’autorisation Générer ou Écrire sur le jeu de données. Excel met en cache les données retournées pour l’intégralité de la ligne. Toute personne avec laquelle vous partagez le fichier Excel peut voir les données de tous les champs de toutes les cellules liées.

Si un jeu de données Power BI possède une sécurité au niveau des lignes ou une étiquette de sensibilité Microsoft Information Protection appliquée, les tables recommandées de ce jeu de données ne sont pas incluses dans la galerie Types de données Excel. Il s’agit d’une limitation de la préversion initiale.

## <a name="administrative-control"></a>Contrôle administratif

Les administrateurs Power BI peuvent contrôler les utilisateurs de l’organisation qui peuvent utiliser les tables recommandées dans la galerie Types de données Excel. Pour plus d’informations, consultez [Paramètres des tables recommandées](../admin/service-admin-portal.md#featured-tables-settings) dans l’article du portail d’administration. 
 
### <a name="auditing"></a>Audit

Les journaux d’audit d’administration affichent ces événements pour les tables recommandées :

- **AnalyzedByExternalApplication** : Donne aux administrateurs la visibilité sur les utilisateurs qui accèdent aux tables recommandées.
- **UpdateFeaturedTables** : Donne aux administrateurs la visibilité sur les utilisateurs qui publient et mettent à jour les tables recommandées.

Pour obtenir la liste complète des événements du journal d’audit, consultez [Suivre les activités utilisateur dans Power BI](../admin/service-admin-auditing.md).

## <a name="considerations-and-limitations"></a>Considérations et limitations

Voici les limitations de la préversion initiale :

- L’intégration est disponible dans les builds Excel Insiders.
- La galerie Types de données Excel comprend des tables recommandées pour les utilisateurs avec la licence appropriée dans Power BI Desktop et le service Power BI. La prise en charge du service Power BI pourrait ne pas être disponible au lancement de la préversion, mais elle sera ajoutée.
- Les tables recommandées dans les jeux de données Power BI qui utilisent les fonctionnalités suivantes ne sont pas affichées dans Excel : 

    - Jeux de données de sécurité au niveau des lignes.
    - Jeux de données Microsoft Information Protection activés.
    - Jeux de données DirectQuery.
    - Jeux de données avec une connexion active.

- Excel affiche uniquement les données dans les colonnes et les colonnes calculées dans la table recommandée. Les éléments suivants ne sont pas fournis dans la préversion initiale :

    - Mesures définies sur la table recommandée.
    - Mesures définies sur les tables associées, et mesures implicites calculées à partir des relations.

- Excel affiche uniquement les tables recommandées (*types de données*) qui sont stockées dans les nouveaux espaces de travail Power BI. Les tables recommandées stockées dans les espaces de travail classiques, ou dans Mon espace de travail, ne sont pas affichées comme types de données dans Excel. Vous pouvez [Mettre à niveau les espaces de travail classiques vers de nouveaux espaces de travail](service-upgrade-workspaces.md) dans Power BI.

L’expérience Types de données dans Excel est semblable à celle d’une fonction de recherche. Elle prend une valeur de cellule fournie par la feuille Excel et recherche les lignes correspondantes dans les tables Power BI recommandées. L’expérience Recherche présente les comportements suivants :

- Lorsque vous utilisez le bouton **Données organisationnelles** pour effectuer des recherches, Excel recherche uniquement les tables recommandées dans les jeux de données certifiés.
- La correspondance des lignes est basée sur les colonnes de texte dans la table recommandée. Elle utilise la même indexation que Power BI Q&A, qui est optimisée pour la recherche en langue anglaise. La recherche dans d’autres langues peut ne pas aboutir à des correspondances précises. Les colonnes numériques ne sont pas prises en compte pour la correspondance.
- La correspondance est basée sur les correspondances Préfixe et Exacte pour les termes de recherche individuels. La valeur d’une cellule est fractionnée en fonction des espaces ou d’autres caractères d’espacement, comme les tabulations. Chaque mot est alors considéré comme un terme de recherche. Les valeurs de champ de texte d’une ligne sont comparées à chaque terme de recherche pour les correspondances de type Exacte et Préfixe. Une correspondance de préfixe est retournée si le champ de texte de la ligne commence par le terme de recherche. Par exemple, si une cellule contient « Orange County », « orange » et « County » sont des termes de recherche distincts. 

    - Les lignes avec des colonnes de texte dont la valeur correspond exactement à « orange » ou « county » sont retournées. 
    - Les lignes avec une colonne de texte dont la valeur commence par « orange » ou « county » sont retournées. 
    - Il convient de noter que les lignes qui contiennent « orange » ou « county » mais ne commencent pas par ces termes ne sont pas retournées.

- Power BI retourne au maximum 100 suggestions de ligne pour chaque cellule.
- La définition ou la mise à jour de la table recommandée n’est pas prise en charge dans le point de terminaison XMLA
- Les fichiers Excel avec un modèle de données peuvent être utilisés pour publier des tables recommandées. Chargez les données dans Power BI Desktop, puis publiez la table recommandée.
- La modification du nom de la table, d’une étiquette de ligne ou d’une colonne clé de la table recommandée peut avoir un impact sur les utilisateurs Excel avec des cellules liées sur les lignes de la table. 
- Excel affiche le moment où les données ont été récupérées à partir du jeu de données Power BI. Ce n’est pas nécessairement l’heure à laquelle les données ont été actualisées dans Power BI, ou l’heure du point de données le plus récent dans un jeu de données. Par exemple, imaginons qu’un jeu de données Power BI a été actualisé il y a une semaine, mais que les données sources sous-jacentes dataient d’une semaine quand l’actualisation s’est produite. Les données sont en réalité âgées de 2 semaines, mais Excel affiche les données comme ayant été récupérées à la date et à l’heure de leur extraction dans Excel.

## <a name="next-steps"></a>Étapes suivantes

- [Définir des tables recommandées dans Power BI Desktop](service-create-excel-featured-tables.md)
- Vous trouverez des informations sur l’utilisation des [types de données Excel depuis Power BI](https://support.office.com/article/use-excel-data-types-from-power-bi-preview-cd8938ce-f963-444d-b82a-7140848241e9) dans la documentation Excel.
- Vous avez des questions ? [Essayez la communauté Power BI](https://community.powerbi.com/)

