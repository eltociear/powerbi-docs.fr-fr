---
title: Données multidimensionnelles Analysis Services dans Power BI Desktop
description: Données multidimensionnelles SQL Server Analysis Services (SSAS) dans Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 01/15/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 7b96e9707e9c91c6403047091bed00afbff3789d
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85222525"
---
# <a name="connect-to-ssas-multidimensional-models-in-power-bi-desktop"></a>Découvrez comment vous connecter aux modèles multidimensionnels SSAS dans Power BI Desktop

Power BI Desktop vous permet d’accéder aux *modèles multidimensionnels SSAS*, communément appelés *SSAS MD*.

Pour vous connecter à une base de données SSAS MD, sélectionnez **Obtenir des données**, choisissez **Base de données** > **Base de données SQL Server Analysis Services** et sélectionnez **Se connecter** :

![Base de données SQL Server Analysis Services (SSAS), boîte de dialogue Obtenir des données, Power BI Desktop](media/desktop-ssas-multidimensional/ssas-multidimensional-2.png)

À la fois le service Power BI et Power BI Desktop prennent en charge les modèles multidimensionnels SSAS en mode de connexion active. Vous pouvez publier et charger des rapports qui utilisent les **modèles multidimensionnels SSAS** en mode réel au service Power BI.

## <a name="capabilities-and-features-of-ssas-md"></a>Capacités et fonctionnalités de SSAS MD

Les sections suivantes décrivent les fonctionnalités et capacités des connexions Power BI et SSAS MD.

### <a name="tabular-metadata-of-multidimensional-models"></a>Métadonnées tabulaires des modèles multidimensionnels

Le tableau suivant illustre la correspondance entre les objets multidimensionnels et les métadonnées tabulaires qui sont renvoyés à Power BI Desktop. Power BI interroge le modèle pour obtenir les métadonnées tabulaires. En fonction des métadonnées retournées, Power BI Desktop exécute les requêtes DAX appropriées sur SSAS quand vous créez une visualisation (comme une table, une matrice, un graphique ou un segment).

| Objet BISM multidimensionnel | Métadonnées tabulaires |
| --- | --- |
| Cube |Modèle |
| Dimension de cube |Table |
| Attributs de dimension (clés), nom |Colonnes |
| Groupe de mesures |Table |
| Mesure |Mesure |
| Mesures sans groupe de mesures associé |Dans une table appelée *Mesures* |
| Relation groupe de mesures -> dimension de Cube |Relation |
| Perspective |Perspective |
| Indicateur de performance clé |KPI |
| Hiérarchies parent-enfant/utilisateur |Hiérarchies |

### <a name="measures-measure-groups-and-kpis"></a>Mesures, groupes de mesures et indicateurs de performance clés

Les groupes de mesures dans un cube multidimensionnel sont exposés sous forme de tables avec le signe ∑ à côté, dans le volet **Champs**. Les mesures calculées sans groupe de mesures associé sont regroupées dans une table spéciale appelée *Mesures* dans les métadonnées tabulaires.

Pour simplifier les modèles complexes dans un modèle multidimensionnel, vous pouvez définir un ensemble de mesures ou d’indicateurs de performance clés dans un cube à placer dans un *dossier d’affichage*. Power BI reconnaît les dossiers d’affichage dans les métadonnées tabulaires et affiche les mesures et indicateurs de performance clés dans les dossiers d’affichage. Les indicateurs de performance clés dans les bases de données multidimensionnelles prennent en charge *Valeur*, *Objectif*, *Graphique d’état* et *Graphique de tendance*.

### <a name="dimension-attribute-type"></a>Types d’attributs de dimension

Les modèles multidimensionnels prennent également en charge l’association d’attributs de dimension avec des types d’attributs de dimension spécifiques. Par exemple, une dimension **Géographie**, pour laquelle les attributs de dimension *Ville*, *État/région*, *Pays* et *Code postal* sont associés à des types géographiques appropriés, sont exposés dans les métadonnées tabulaires. Power BI reconnaît les métadonnées, ce qui vous permet de créer des visualisations de carte. Ces associations sont identifiables grâce à l’icône *carte* à côté de l’élément dans le volet **Champ** dans Power BI.

Power BI peut également restituer des images lorsque vous fournissez un champ qui contient des URL (uniform resource locators) des images. Vous pouvez spécifier ces champs comme types *ImageURL* dans SQL Server Data Tools (ou dans Power BI). Les informations de type sont alors fournies à Power BI dans les métadonnées tabulaires. Power BI peut ensuite récupérer ces images à partir de l’URL et les afficher dans des visuels.

### <a name="parent-child-hierarchies"></a>Hiérarchies parent-enfant

Les modèles multidimensionnels prennent en charge les hiérarchies parent-enfant, qui sont présentées comme *hiérarchie* dans les métadonnées tabulaires. Chaque niveau de la hiérarchie parent-enfant est exposé sous forme de colonne masquée dans les métadonnées tabulaires. L’attribut clé de la dimension parent-enfant n’est pas exposé dans les métadonnées tabulaires.

### <a name="dimension-calculated-members"></a>Membres calculés de dimension

Les modèles multidimensionnels prennent en charge la création de différents types de *membres calculés*. Les deux types de membres calculés les plus courants sont :

* Membres calculés sur les hiérarchies d’attributs qui ne sont pas frères de *Tous*
* membres calculés sur les hiérarchies d’utilisateur

Les modèles multidimensionnels exposent les *membres calculés sur les hiérarchies d’attributs* sous forme de valeurs d’une colonne. Vous avez quelques options et contraintes supplémentaires si vous exposez ce type de membre calculé :

* Un attribut de dimension peut avoir une propriété *UnknownMember* facultative.

* Un attribut contenant des membres calculés ne peut pas être l’attribut clé de la dimension, sauf s’il est le seul attribut de la dimension.

* Un attribut contenant des membres calculés ne peut pas être un attribut parent-enfant.

Les membres calculés des hiérarchies d’utilisateurs ne sont pas exposés dans Power BI. À la place, vous pouvez vous connecter à un cube qui contient des membres calculés sur des hiérarchies utilisateur. Toutefois, vous ne pourrez pas voir les membres calculés si ceux-ci ne respectent pas les contraintes que nous avons mentionnées dans la liste à puces précédente.

### <a name="security"></a>Sécurité

Les modèles multidimensionnels prennent en charge la sécurité au niveau des cellules et de la dimension au moyen de *rôles*. Lorsque vous vous connectez à un cube avec Power BI, vous êtes authentifié et évalué afin d’obtenir les autorisations appropriées. Si la *sécurité de dimension* est appliquée à un utilisateur, celui-ci ne peut pas voir les membres de la dimension respective dans Power BI. Toutefois, si l’utilisateur a défini une autorisation de *sécurité de cellule*, lorsque certaines cellules sont restreintes, il ne peut pas se connecter au cube à l’aide de Power BI.

## <a name="considerations-and-limitations"></a>Considérations et limitations

Il existe certaines limitations à l’utilisation de SSAS MD :

* Seules les éditions Enterprise et BI de SQL Server 2014 prennent en charge les connexions actives. Pour l’édition Standard de SQL Server, SQL Server 2016 ou ultérieur est requis pour les connexions actives.

* Les *actions* et les *jeux nommés* ne sont pas exposés à Power BI. Pour créer des visuels et des rapports, vous pouvez toujours vous connecter à des cubes qui contiennent également des actions ou des jeux nommés.

* Lorsque Power BI affiche des métadonnées pour un modèle SSAS, il peut vous arriver parfois de ne pas pouvoir récupérer les données du modèle. Ce scénario peut se produire si vous avez installé la version 32 bits du fournisseur MSOLAP, et non la version 64 bits. L’installation de la version 64 bits peut résoudre le problème.

* Vous ne pouvez pas créer des mesures *au niveau du rapport* lors de la création d’un rapport qui est connecté en direct à un modèle multidimensionnel SSAS. Les seules mesures disponibles sont les mesures définies dans le modèle MD.

## <a name="supported-features-of-ssas-md-in-power-bi-desktop"></a>Fonctionnalités prises en charge de SSAS MD dans Power BI Desktop

La consommation des éléments suivants est prise en charge dans cette version de SSAS MD. Pour plus d'informations sur ces fonctionnalités, consultez [Présentation de Power View pour les modèles multidimensionnels](/sql/analysis-services/multidimensional-models/understanding-power-view-for-multidimensional-models?view=sql-server-2014).

* Membres par défaut
* Attributs de dimensions
* Types d’attributs de dimension
* Membres calculés de dimension, qui :
  * Doivent être des membres réels uniques quand la dimension a plus d’un attribut.
  * Ne peuvent pas être l’attribut clé de la dimension, sauf si c’est le seul attribut.
  * Ne peuvent pas être un attribut parent-enfant.
* Sécurité de la dimension
* Dossiers d’affichage
* Hiérarchies
* ImageUrls
* Indicateurs de performance clés
* Tendances d’indicateur de performance clé
* Mesures (avec ou sans groupes de mesures)
* Mesures en tant que variantes

## <a name="troubleshooting"></a>Résolution des problèmes

La liste suivante décrit tous les problèmes connus lors de la connexion à SQL Server Analysis Services (SSAS).

* **Erreur : Impossible de charger le schéma de modèle** - Cette erreur se produit généralement quand l’utilisateur qui se connecte à Analysis Services n’a pas accès à la base de données/au cube.
