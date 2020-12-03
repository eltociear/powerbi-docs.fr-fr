---
title: Utilisation de la liste de champs dans Power BI Desktop (préversion)
description: Utiliser la liste de champs pour modéliser des données et créer des rapports dans Power BI Desktop
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-transform-model
ms.topic: conceptual
ms.date: 11/11/2020
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 834df274d4cc75af1087ab4fa7d24c2fd7dd4fec
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96415999"
---
# <a name="using-the-field-list-in-power-bi-desktop-preview"></a>Utilisation de la liste de champs dans Power BI Desktop (préversion)

À partir de la mise à jour de novembre 2020, nous centralisons les listes de **champs** dans la vue Modèle, la vue Données et la vue Rapport de Power BI Desktop. La centralisation de ces vues crée une cohérence en termes de fonctionnement et d’interface utilisateur, en réponse aux commentaires reçus des clients.

Les changements que vous noterez dans les vues sont les suivants :

* Iconographie
* Fonctionnalité de recherche
* Éléments de menu contextuel
* Comportement de glisser-déplacer similaire
* Info-bulles
* Améliorations de l’accessibilité

L’objectif est d’améliorer la facilité d’utilisation de Power BI Desktop. Les changements devraient avoir un impact minimal sur votre workflow de données classique.

## <a name="enabling-the-new-field-list-preview"></a>Activation de la nouvelle liste de champs (préversion)

La liste de champs centralisée va commencer par la vue **Modèle**, puis sera appliquée aux autres vues par la suite. Pour activer la vue Champ centralisée, dans Power BI Desktop, accédez à **Fichier > Options et paramètres > Options**, puis sélectionnez **Fonctionnalités en préversion** dans le volet gauche. Dans la section Fonctionnalités en préversion, cochez la case à côté de **Nouvelle liste de champs**.

![Activer la nouvelle liste de champs](media/desktop-field-list/field-list-01.png)

Vous êtes invité à redémarrer Power BI Desktop pour que la sélection prenne effet.

## <a name="field-list-changes"></a>Changements dans la liste de champs

Les tableaux suivants indiquent les mises à jour apportées à la liste de champs. 


|**Liste de champs d’origine (vue Modèle)**  | **Nouvelle liste de champs (vue Modèle)**  |
|:---------:|:---------:|
|**Ressource d’origine** |**Nouveau** |
|**Icônes et interface utilisateur**       ||
|![Liste de champs d’origine](media/desktop-field-list/field-list-01a.png)     |![Nouvelle liste de champs](media/desktop-field-list/field-list-01b.png)    |
|**Menu contextuel - Champ**       ||
|![Menu contextuel d’origine pour Champ](media/desktop-field-list/field-list-02a.png)     |![Nouveau menu contextuel pour Champ](media/desktop-field-list/field-list-02b.png)    |
|**Menu contextuel - Table**       ||
|![Menu contextuel d’origine pour la table](media/desktop-field-list/field-list-03a.png)     |![Nouveau menu contextuel pour la table](media/desktop-field-list/field-list-03b.png)    |
|**Info-bulles**       ||
|![Info-bulle d’origine](media/desktop-field-list/field-list-04a.png)     |![Nouvelle info-bulle](media/desktop-field-list/field-list-04b.png)    |

Il existe également de nouvelles icônes de liste de champs. Le tableau suivant présente les icônes d’origine et leur nouvel équivalent, puis fournit une brève description de chacune d’elles. 


|Icône d’origine  |Icône Nouveau  |Description  |
|:---------:|:---------:|:---------|
|![Icône de dossier d’origine](media/desktop-field-list/field-list-05a.png)     |![Nouvelle icône de dossier](media/desktop-field-list/field-list-05b.png)           |Dossier dans la liste Champs         |
|![Icône de champ numérique d’origine](media/desktop-field-list/field-list-06a.png)     |![Nouvelle icône de champ numérique](media/desktop-field-list/field-list-06b.png)         |Champ numérique : Les champs numériques sont des agrégats qui sont utilisés dans le cadre d’additions ou de calculs de moyenne, par exemple. Les agrégats sont importés avec les données et sont définis dans le modèle de données sur lequel votre rapport est basé. Pour plus d’informations, consultez [Agrégats dans des rapports Power BI](../create-reports/service-aggregates.md).         |
|![Icône de colonne calculée d’origine](media/desktop-field-list/field-list-07a.png)     |![Nouvelle icône de colonne calculée](media/desktop-field-list/field-list-07b.png)         |Colonne calculée avec type de données non numérique : Nouvelle colonne non numérique que vous créez avec une formule DAX (Data Analysis Expressions) qui définit les valeurs de la colonne. En savoir plus sur les [colonnes calculées](desktop-calculated-columns.md)        |
|![Icône de colonne calculée numérique d’origine](media/desktop-field-list/field-list-08a.png)     |![Nouvelle icône de colonne calculée numérique](media/desktop-field-list/field-list-08b.png)          |Colonne calculée numérique : Nouvelle colonne que vous créez avec une formule DAX (Data Analysis Expressions) qui définit les valeurs de la colonne. En savoir plus sur les [colonnes calculées](desktop-calculated-columns.md)         |
|![Icône de mesure d’origine](media/desktop-field-list/field-list-09a.png)     |![Nouvelle icône de mesure](media/desktop-field-list/field-list-09b.png)          |Mesure : Chaque mesure a sa propre formule codée en dur. Les visionneuses de rapports ne peuvent pas changer le calcul ; par exemple, s’il s’agit d’une somme, il peut uniquement s’agir d’une somme. Les valeurs ne sont pas stockées dans une colonne. Elles sont calculées à la volée, en fonction uniquement de leur emplacement dans le visuel. Pour plus d’informations, lisez [Présentation des mesures](desktop-measures.md).         |
|![Icône de groupe de mesures d’origine](media/desktop-field-list/field-list-10a.png)     |![Nouvelle icône de groupe de mesures](media/desktop-field-list/field-list-10b.png)         |Groupe de mesures.         |
|![Icône d’indicateur de performance clé d’origine](media/desktop-field-list/field-list-11a.png)     |![Nouvelle icône d’indicateur de performance clé](media/desktop-field-list/field-list-11b.png)         |KPI : Indice visuel qui permet de voir la progression réalisée vers un objectif mesurable. Découvrez-en plus sur les visuels d’[indicateur de performance clé (KPI)](../visuals/power-bi-visualization-kpi.md).         |
|![Icône de hiérarchie des champs d’origine](media/desktop-field-list/field-list-12a.png)     |![Nouvelle icône de hiérarchie des champs](media/desktop-field-list/field-list-12b.png)           |Hiérarchie des champs : Sélectionnez la flèche pour afficher les champs qui composent la hiérarchie. Pour plus d’informations, regardez cette vidéo Power BI sur YouTube concernant la [création et l’utilisation des hiérarchies](https://www.youtube.com/watch?v=q8WDUAiTGeU).         |
|![Icône de données géographiques d’origine](media/desktop-field-list/field-list-13a.png)     |![Nouvelle icône de données géographiques](media/desktop-field-list/field-list-13b.png)         |Données géographiques : Ces champs d’emplacement peuvent être utilisés pour créer des visualisations de cartes.         |
|![Icône de champ Identité d’origine](media/desktop-field-list/field-list-14a.png)     |![Nouvelle icône de champ Identité](media/desktop-field-list/field-list-14b.png)          |Champ Identité : Les champs portant cette icône sont des champs uniques, configurés pour afficher toutes les valeurs, y compris les doublons. Par exemple, vos données peuvent comprendre des enregistrements pour deux personnes nommées « Robin Smith », et chaque enregistrement sera traité comme étant unique. Ils ne seront pas additionnés.         |
|![Icône de paramètre d’origine](media/desktop-field-list/field-list-15a.png)     |![Nouvelle icône de paramètre](media/desktop-field-list/field-list-15b.png)          |Paramètre : Configurez les paramètres pour que certaines parties de vos rapports et modèles de données (filtre de requête, référence à une source de données, définition de mesure, etc.) dépendent d’une ou de plusieurs valeurs de paramètres. Pour plus d’informations, consultez ce billet de blog Power BI sur les [paramètres de requête](https://powerbi.microsoft.com/blog/deep-dive-into-query-parameters-and-power-bi-templates/).         |
|![Icône de champ de date de calendrier d’origine](media/desktop-field-list/field-list-16a.png)     |![Nouvelle icône de champ de date de calendrier](media/desktop-field-list/field-list-16b.png)         |Champ de date de calendrier avec une table de dates intégrée.         |
|![Icône de table calculée d’origine](media/desktop-field-list/field-list-17a.png)     |![Nouvelle icône de table calculée](media/desktop-field-list/field-list-17b.png)          |Table calculée : Table créée à l’aide d’une formule DAX (Data Analysis Expressions) basée sur les données déjà chargées dans le modèle. Ces tables conviennent mieux aux calculs intermédiaires que vous voulez stocker dans le cadre du modèle.         |
|![Icône d’avertissement d’origine](media/desktop-field-list/field-list-18a.png)     |![Nouvelle icône d’avertissement](media/desktop-field-list/field-list-18b.png)         |Avertissement : Champ calculé avec une erreur. Par exemple, la syntaxe de l’expression DAX peut être incorrecte.         |
|![Icône de groupe d’origine](media/desktop-field-list/field-list-19a.png)     |![Nouvelle icône de groupe](media/desktop-field-list/field-list-19b.png)         |Groupe : Les valeurs de cette colonne sont basées sur des valeurs de regroupement d’une autre colonne, déterminées à l’aide de la fonctionnalité des groupes et classes. Vous pouvez apprendre à [utiliser le regroupement et le binning](../create-reports/desktop-grouping-and-binning.md).         |
| Aucune icône d’origine    |![Nouvelle icône de mesure de détection des changements](media/desktop-field-list/field-list-20b.png)          |Mesure de détection des changements : Quand vous configurez une page pour qu’elle s’actualise automatiquement, vous pouvez configurer une [mesure de détection des changements](../create-reports/desktop-grouping-and-binning.md) qui est interrogée pour déterminer si le reste des visuels de la page doit être mis à jour.         |


## <a name="next-steps"></a>Étapes suivantes

Les articles suivants pourraient également vous intéresser :

* [Créer des colonnes calculées dans Power BI Desktop](desktop-calculated-columns.md)
* [Utiliser le regroupement et le compartimentage dans Power BI Desktop](../create-reports/desktop-grouping-and-binning.md)
* [Utiliser le quadrillage et l’alignement sur la grille dans les rapports Power BI Desktop](../create-reports/desktop-gridlines-snap-to-grid.md)

