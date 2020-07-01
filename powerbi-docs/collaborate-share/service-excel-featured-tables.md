---
title: Accéder aux tables recommandées Power BI dans Excel (préversion)
description: Dans Excel, vous pouvez rechercher des données à partir des tables recommandées dans les jeux de données Power BI dans la galerie Types de données.
author: maggiesMSFT
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 05/20/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: a872c0ada80a7168ebc6bb545de1ad474c4561b7
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85226351"
---
# <a name="access-power-bi-featured-tables-in-excel-preview"></a>Accéder aux tables recommandées Power BI dans Excel (préversion)

Dans Excel, vous pouvez rechercher des données à partir des tables recommandées dans les jeux de données Power BI dans la galerie Types de données. Les tables recommandées facilitent l’ajout de données d’entreprise à vos feuilles Excel. En utilisant des fonctionnalités de jeu de données Power BI certifiées et promues, les organisations permettent à davantage d’utilisateurs de trouver et d’utiliser des données pertinentes et actualisables pour prendre de meilleures décisions. Vous trouverez plus d’informations sur l’utilisation des [types de données Excel depuis Power BI](https://support.office.com/article/use-excel-data-types-from-power-bi-preview-cd8938ce-f963-444d-b82a-7140848241e9) dans la documentation Excel.

La galerie Types de données affiche uniquement les tables recommandées qu’un modeleur a organisées dans des jeux de données Power BI. Vous pouvez également parcourir dans Excel n’importe quel jeu de données auquel vous pouvez accéder dans Power BI. Dans Excel, sélectionnez l’option **Jeux de données Power BI** sous l’option **Obtenir des données** sur le ruban **Données**.

## <a name="access-power-bi-data-through-the-excel-data-types-gallery"></a>Accéder aux données Power BI par le biais de la galerie Types de données Excel
Les tables recommandées dans les jeux de données Power BI s’affichent dans la galerie Types de données Excel du ruban Données.

:::image type="content" source="media/service-excel-featured-tables/excel-data-ribbon.png" alt-text="Ruban Données Excel":::

Une fois développée, la galerie affiche les principaux types de données disponibles.

:::image type="content" source="media/service-excel-featured-tables/excel-data-types-gallery.png" alt-text="Galerie Types de données Excel":::
 
Pour rechercher des données dans une table Power BI recommandée, sélectionnez une cellule ou une plage dans votre feuille Excel.

:::image type="content" source="media/service-excel-featured-tables/excel-select-cell.png" alt-text="Sélectionner une cellule":::
 
Sélectionnez l’option **Données organisationnelles** dans la galerie pour rechercher des données dans les tables recommandées dans les jeux de données certifiés auxquels vous avez accès.

:::image type="content" source="media/service-excel-featured-tables/excel-organizational-data.png" alt-text="Données organisationnelles Excel":::
 
Sélectionnez un type de données spécifique si vous connaissez le type de données que vous recherchez ou si vous ne trouvez pas les lignes correspondantes à l’aide de l’option Données organisationnelles.

:::image type="content" source="media/service-excel-featured-tables/excel-select-data-type.png" alt-text="Sélectionner un type de données":::
 
Lorsque vous recherchez, si une ligne correspondante est trouvée avec un niveau de confiance élevé, la cellule est immédiatement liée à cette ligne. L’icône d’élément lié indique que la cellule est liée à la ligne dans Power BI.

:::image type="content" source="media/service-excel-featured-tables/excel-linked-item-icon.png" alt-text="Icône d’élément lié":::

Si une cellule contient plusieurs lignes correspondantes potentielles, un volet de sélection de données s’affiche. La cellule affiche l’icône de point d’interrogation, qui ouvre le volet de sélection de données sur cette ligne. Voici un exemple après que l’utilisateur a sélectionné une plage A2:A7 et effectué une recherche dans une table Power BI recommandée.

:::image type="content" source="media/service-excel-featured-tables/excel-multiple-matches.png" alt-text="Plusieurs lignes correspondantes possibles":::

Le volet **Sélecteur de données** affiche les lignes potentiellement correspondantes.

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-pane.png" alt-text="Volet Sélecteur de données Excel":::
 
L’option Données organisationnelles peut retourner des lignes de plusieurs types de données. Excel regroupe les lignes potentiellement correspondantes selon le type de données à partir duquel elles proviennent. Excel trie les types de données en fonction de leur ligne de correspondance la plus probable. Utilisez les flèches pour réduire et développer les types de données pour les lignes correspondantes.

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-multiple.png" alt-text="Volet Sélecteur de données Excel":::
 
Pour chaque ligne, sélectionnez le nom de la ligne pour afficher plus de détails au sein de cette ligne pour vous aider à choisir la bonne ligne. Une fois que vous avez trouvé une ligne, appuyez sur **Sélectionner** pour lier la ligne à la cellule dans Excel. 

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-select.png" alt-text="Détails du sélecteur de données":::
 
Lorsqu’une ligne est sélectionnée, la cellule est liée à la ligne et sa valeur l’est avec la valeur du champ **Étiquette de ligne** dans la table Power BI recommandée. 

:::image type="content" source="media/service-excel-featured-tables/excel-linked-item-icon.png" alt-text="Élément lié Excel":::
 
La sélection de l’icône **Cellule liée** affiche une carte contenant les données des champs et des champs calculés dans la table recommandée. Le titre de la carte affiche la valeur du champ d’étiquette de ligne dans la table recommandée.
 
:::image type="content" source="media/service-excel-featured-tables/excel-linked-item-details.png" alt-text="Détails de l’élément lié":::

Sélectionnez l’icône **Insérer des données** pour ajouter des valeurs de champ à la grille.

:::image type="content" source="media/service-excel-featured-tables/excel-insert-data.png" alt-text="Insérer des données"::: 

Sélectionnez un nom de champ dans la liste de champs pour ajouter sa valeur à la grille.  

:::image type="content" source="media/service-excel-featured-tables/excel-select-field.png" alt-text="Sélectionner un nom de champ":::

La valeur du champ est placée dans la cellule adjacente. La formule de la cellule fait référence à la cellule liée et au nom du champ, ce qui vous permet d’utiliser les données dans des fonctions Excel.

:::image type="content" source="media/service-excel-featured-tables/excel-cell-formula.png" alt-text="Formule de cellule Excel":::
 
Lorsque vous mettez en forme vos données sous forme de tableau Excel, l’ajout de champs développe le tableau et définit l’en-tête de colonne pour qu’il corresponde au nom du champ. Les lignes liées aux mêmes types de données sont également remplies avec leurs valeurs respectives.

:::image type="content" source="media/service-excel-featured-tables/excel-field-column-name.png" alt-text="Le champ est le nom de la colonne"::: 

## <a name="cell-formulas"></a>Formules de cellule

Lorsque vous utilisez un tableau Excel, vous pouvez faire référence à la colonne de la table liée, puis ajouter des champs de données à l’aide de la référence `.` (point).

:::image type="content" source="media/service-excel-featured-tables/excel-dot-reference.png" alt-text="Référence point Excel":::

De même, lorsque vous utilisez une cellule, vous pouvez vous référer à la cellule et utiliser la référence `.` (point) pour extraire des champs.

:::image type="content" source="media/service-excel-featured-tables/excel-cell-dot-reference.png" alt-text="Référence point de cellule":::
 
## <a name="data-caching-and-refresh"></a>Mise en cache et actualisation des données

Quand Excel lie une cellule à une ligne dans une table Power BI recommandée, il récupère et enregistre toutes les valeurs de champ dans le fichier Excel. Toute personne avec laquelle vous partagez le fichier peut faire référence à n’importe quel champ, sans demander de données de Power BI.  

Utilisez le bouton **Actualiser tout** dans le ruban **Données** pour actualiser les données des cellules liées. 

:::image type="content" source="media/service-excel-featured-tables/excel-refresh-all.png" alt-text="Actualiser tout":::
 
Vous pouvez également actualiser les cellules une par une. Cliquez avec le bouton droit sur la cellule, puis sélectionnez **Types de données** > **Actualiser**.

## <a name="show-a-card-change-or-convert-to-text"></a>Afficher une carte, modifier ou convertir en texte

Les cellules liées ont des options de menu contextuel supplémentaires. Cliquez avec le bouton droit sur une cellule > sélectionnez **Type de données** >  

- **Afficher une carte**
- **Actualisation**
- **Modification** 
- **Convertir en texte**.

:::image type="content" source="media/service-excel-featured-tables/excel-right-click-data-type.png" alt-text="Cliquer avec le bouton droit, Convertir en texte":::
 
**Convertir en texte** supprime le lien vers la ligne dans la table Power BI recommandée. Il convient de noter que le texte de la cellule sera la valeur de l’étiquette de ligne de la cellule liée. Si vous avez lié une cellule à une ligne par inadvertance, sélectionnez **Annuler** dans Excel pour restaurer les valeurs de cellule initiales.

## <a name="licensing"></a>Licences
La galerie Types de données Excel et les expériences connectées aux tables Power BI recommandées sont uniquement disponibles pour les clients Excel E5 et G5. 

## <a name="security"></a>Sécurité

Vous voyez uniquement les tables recommandées des jeux de données pour lesquels vous disposez de l’autorisation dans Power BI. Lors de l’actualisation des données, vous devez avoir l’autorisation d’accéder au jeu de données dans Power BI pour récupérer les lignes. Cela nécessite l’autorisation Générer ou Écrire sur le jeu de données. Excel met en cache les données retournées pour l’intégralité de la ligne. Toute personne avec laquelle vous partagez le fichier Excel peut voir les données de tous les champs de toutes les cellules liées.

Si un jeu de données Power BI possède une sécurité au niveau des lignes ou une étiquette de sensibilité Microsoft Information Protection appliquée, les tables recommandées de ce jeu de données ne sont pas incluses dans la galerie Types de données Excel. Il s’agit d’une limitation de la préversion initiale.

## <a name="curate-a-featured-table-in-power-bi-desktop"></a>Organiser une table recommandée dans Power BI Desktop
La galerie Types de données Excel affiche les tables recommandées dans les jeux de données chargés dans le service Power BI. Utilisez Power BI Desktop pour organiser les tables recommandées dans le modèle de données, puis téléchargez-les dans le service Power BI.

### <a name="turn-on-the-featured-table-preview"></a>Activer l’aperçu de la table recommandée

1. Dans Power BI Desktop, sélectionnez **Fichier** > **Options et paramètres** > **Options** > **Fonctionnalités en préversion**.
2. Activez la case à cocher **Tables recommandées**.

    :::image type="content" source="media/service-excel-featured-tables/power-bi-preview-featured-tables.png" alt-text="Option Aperçu des tables recommandées":::

### <a name="select-a-table"></a>Sélectionner une table

1. Dans Power BI Desktop, accédez à la vue Modèle.

    :::image type="content" source="media/service-excel-featured-tables/power-bi-model-view.png" alt-text="Vue Modèle":::
 
2. Sélectionnez une table et définissez **Est une table proposée** sur **Oui**.

    :::image type="content" source="media/service-excel-featured-tables/power-bi-featured-table-yes.png" alt-text="Définissez Est une table proposée sur Oui":::

4. Dans **Configurer cette table recommandée**, renseignez les champs requis :

    - Une **Description**.
    - La valeur du champ **Étiquette de ligne** est utilisée dans Excel afin que les utilisateurs puissent facilement identifier la ligne. Elle apparaît en tant que valeur de cellule pour une cellule liée, dans le volet **Sélecteur de données** et dans la carte **Informations**. 
    - La valeur du champ **Colonne clé** fournit l’ID unique de la ligne. Cette valeur permet à Excel de lier une cellule à une ligne spécifique de la table.

    :::image type="content" source="media/service-excel-featured-tables/power-bi-set-up-featured-table.png" alt-text="Configurer la table recommandée":::

Une fois que vous avez publié ou importé le jeu de données dans le service Power BI, la table recommandée s’affiche dans la galerie Types de données Excel.

- Excel met en cache la liste de types de données, ce qui vous permet de redémarrer Excel pour voir les tables recommandées qui viennent d’être publiées.
- Certains jeux de données ne sont pas pris en charge dans la préversion, et les tables recommandées définies dans ces jeux de données n’apparaissent pas dans Excel. Consultez Considérations et limitations pour plus de détails.

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

- Excel affiche uniquement les tables recommandées qui sont stockées dans les nouveaux espaces de travail Power BI. Les tables recommandées stockées dans les espaces de travail classiques, ou dans Mon espace de travail, ne sont pas affichées comme types de données dans Excel. Vous pouvez [Mettre à niveau les espaces de travail classiques vers de nouveaux espaces de travail](service-upgrade-workspaces.md) dans Power BI.

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

- Vous avez des questions ? [Essayez la communauté Power BI](https://community.powerbi.com/)

