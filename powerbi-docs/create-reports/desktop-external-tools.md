---
title: Utilisation d’outils externes dans Power BI (préversion)
description: Étendre l’utilisation de Power BI Desktop à l’aide d’outils externes
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 07/15/2020
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 4d752a49587e611c3f42de3f40c68437f36fe3a9
ms.sourcegitcommit: 11deeccf596e9bb8f22615276a152614f7579f35
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2020
ms.locfileid: "86411854"
---
# <a name="using-external-tools-in-power-bi-desktop-preview"></a>Utilisation d’outils externes dans Power BI Desktop (préversion)

À partir de la version de juillet 2020 de Power BI Desktop, vous pouvez utiliser des outils externes afin de fournir des fonctionnalités supplémentaires à Power BI Desktop. La prise en charge des outils externes vous permet de tirer parti de la multitude d’outils de la communauté Analysis Services pour professionnels du décisionnel, tels que l’optimisation et la création de requêtes et d’expressions DAX, ainsi que la Gestion du cycle de vie des applications.

Dans Power BI Desktop, le ruban **Outils externes** contient des boutons correspondant aux outils externes qui sont installés sur l’ordinateur et qui sont inscrits auprès de Power BI Desktop. Les outils externes lancés à partir de Power BI Desktop sont automatiquement connectés au moteur Analysis Services qui fonctionne dans le cadre de Power BI Desktop, ce qui permet aux utilisateurs de bénéficier d’une expérience fluide.

![Le ruban Outils externes dans Power BI Desktop](media/desktop-external-tools/desktop-external-tools-01.png)

Les sections suivantes indiquent les opérations qui sont prises en charge par les outils externes, la liste des outils qui sont proposés dans Power BI Desktop, ainsi que la procédure à suivre pour inscrire des outils supplémentaires.

## <a name="supported-write-operations"></a>Opérations d'écriture prise en charge

Les outils externes peuvent se connecter au jeu de données Power BI Desktop (modèle Analysis Services) pour modifier les objets suivants. La modification d’un fichier de modèle Power BI Desktop (PBIT) n’est pas prise en charge.

* Les [mesures](https://docs.microsoft.com/analysis-services/tabular-models/measures-ssas-tabular) utilisées pour les calculs
* Les [groupes de calcul](https://docs.microsoft.com/analysis-services/tabular-models/calculation-groups) pour la réutilisation des calculs dans les modèles complexes
* Les [perspectives](https://docs.microsoft.com/analysis-services/tabular-models/perspectives-ssas-tabular) permettant de définir des vues des métadonnées du jeu de données qui soient ciblées et propres à un domaine d’entreprise

La gestion des traductions de métadonnées à l’aide d’outils externes est possible, mais elle n’est pas prise en charge dans cette préversion. Si les paramètres régionaux de l’utilisateur actuel sont des paramètres régionaux traduits, la modification d’objets dans la liste de champs ne fonctionnera pas correctement avec la version actuelle de Power BI Desktop. 

Il existe un problème connu qui se produit lorsque vous générez des rapports à partir de modèles pour lesquels des groupes de calculs sont définis. Si le groupe de calcul définit la mise en forme dynamique selon le calcul ou la mesure sélectionnés, cette mise en forme sera disponible uniquement dans les visuels de table, de matrice et de carte.

Toutes les métadonnées du jeu de données [Modèle d’objet tabulaire](https://docs.microsoft.com/analysis-services/tom/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo) sont accessibles en lecture seule. En outre, les objets qui ne figurent pas dans la liste de l’article [Modèle d’objet tabulaire](https://docs.microsoft.com/analysis-services/tom/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo) ne peuvent pas encore faire l’objet de modifications dans l’instance Power BI Desktop Analysis Services.


## <a name="featured-external-tools"></a>Outils externes proposés

Les outils de la communauté open source suivants fonctionnent avec Power BI Desktop. Le programme d’installation de chaque outil inscrit celui-ci auprès de Power BI Desktop lors de son l’installation :

* Éditeur tabulaire
* DAX Studio
* ALM Toolkit

Nous allons nous intéresser à chacun de ces outils.

### <a name="tabular-editor"></a>Éditeur tabulaire

Vous pouvez installer l’[éditeur tabulaire](https://tabulareditor.com/) à partir du lien suivant : [Site web de l’éditeur tabulaire](https://tabulareditor.com/)

L’éditeur tabulaire permet aux professionnels du décisionnel de créer et de gérer facilement des modèles tabulaires à l’aide d’un éditeur simplifié et intuitif. Une vue hiérarchisée montre tous les objets de votre modèle tabulaire, organisés par dossiers d’affichage, avec prise en charge de la modification de plusieurs propriétés et de la coloration syntaxique DAX.

![Capture d’écran de l’éditeur tabulaire](media/desktop-external-tools/desktop-external-tools-02.png)

Le code source de l’éditeur tabulaire se trouve dans le dépôt GitHub suivant : [Éditeur tabulaire sur GitHub](https://github.com/otykier/TabularEditor)

L’auteur principal de l’éditeur tabulaire est [Daniel Otykier](https://www.linkedin.com/in/daniel-otykier-2231876).


### <a name="dax-studio"></a>DAX Studio

Vous pouvez installer [DAX Studio](https://daxstudio.org) à partir du lien suivant : [Site web DAX Studio](https://daxstudio.org)

DAX Studio est un outil complet conçu pour la création, le diagnostic, le réglage des performances et l’analyse DAX. Ses fonctionnalités incluent l’exploration des objets, le traçage intégré, l’analyse de l’exécution des requêtes avec des statistiques détaillées, ainsi que la coloration syntaxique DAX et la mise en forme. L’image suivante montre un écran Dax Studio. 

![Capture d’écran de DAX Studio](media/desktop-external-tools/desktop-external-tools-03.png)

Le code source de DAX Studio se trouve dans le dépôt GitHub suivant : [DAX Studio sur GitHub](https://github.com/DaxStudio/DaxStudio)

L’auteur principal de DAX Studio est [Darren Gosbell](https://www.linkedin.com/in/darrengosbell).

### <a name="alm-toolkit"></a>ALM Toolkit

Vous pouvez installer [ALM Toolkit](http://alm-toolkit.com) à partir du lien suivant : [Site web d’ALM Toolkit](http://alm-toolkit.com)

ALM Toolkit est un outil de comparaison de schémas pour les jeux de données Power BI, qui est utilisé pour les scénarios de gestion du cycle de vie des applications. Celui-ci vous permet d’effectuer facilement un déploiement dans plusieurs environnements et de conserver les données historiques de l’actualisation incrémentielle. ALM Toolkit vous permet de comparer et de fusionner des fichiers de métadonnées, des branches et des dépôts. Vous pouvez également réutiliser les définitions communes entre les jeux de données.

![Capture d’écran d’ALM Toolkit](media/desktop-external-tools/desktop-external-tools-04.png)

Le code source d’ALM Toolkit se trouve dans le dépôt GitHub suivant : [ALM Toolkit sur GitHub](https://github.com/microsoft/analysis-services)

L’auteur principal d’ALM Toolkit est [Christian Wade](https://www.linkedin.com/in/christianwade1).


## <a name="how-to-register-external-tools"></a>Inscrire des outils externes

Pour inscrire des outils externes auprès de Power BI Desktop, créez un fichier JSON avec le contenu suivant :

```json
{
    "name": "<tool name>",
    "description": "<tool description>",
    "path": "<tool executable path>",
    "arguments": "<optional command line arguments>",
    "iconData": "image/png;base64,<encoded png icon data>"
}
```

La liste suivante comprend les éléments du fichier JSON :
 
* **name:** donnez un nom à l’outil. Ce nom s’affichera sous la forme d’une légende de bouton dans le ruban Outils externes de Power BI Desktop.
* **description :** (facultatif) fournissez une description, qui s’affichera sous la forme d’une info-bulle sur le bouton du ruban Outils externes dans Power BI Desktop.
* **path :** indiquez le chemin complet du fichier exécutable de l’outil.
* **arguments :** (facultatif) indiquez la chaîne d’arguments de ligne de commande avec laquelle le fichier exécutable de l’outil doit être lancé. Vous pouvez utiliser l’un des espaces réservés suivants :
    * **%server% :** à remplacer par le nom du serveur et le numéro de port de l’instance locale d’Analysis Services Tabular pour les modèles de données importés ou DirectQuery.
    * **%database% :** à remplacer par le nom de la base de données du modèle hébergé sur l’instance locale d’Analysis Services Tabular pour les modèles de données importés ou DirectQuery.
* **iconData :** fournissez des données d’image qui seront affichées sous forme d’icône de bouton dans le ruban Outils externes de Power BI Desktop. La chaîne doit être mise en forme selon la syntaxe des URI de données, sans le préfixe « data: ».
 
Nommez le fichier `"<tool name>.pbitool.json"`, puis placez-le dans le dossier suivant :

* `%commonprogramfiles%\Microsoft Shared\Power BI Desktop\External Tools`

Dans les environnements 64 bits, placez les fichiers dans le dossier suivant :

* **Program Files (x86)\Common Files\Microsoft Shared\Power BI Desktop\External Tools**

Les fichiers de cet emplacement spécifié avec l’extension **.pbitool.json** sont chargés par Power BI Desktop lors du démarrage.


## <a name="next-steps"></a>Étapes suivantes

Les articles suivants pourraient également vous intéresser :

* [Utiliser une extraction interrapport dans les rapports Power BI](desktop-cross-report-drill-through.md)
* [Utilisation de segments Power BI Desktop](../visuals/power-bi-visualization-slicers.md)


