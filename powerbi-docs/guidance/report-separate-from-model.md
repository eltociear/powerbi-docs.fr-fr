---
title: Séparer les rapports des modèles dans Power BI Desktop
description: Conseils pour séparer les rapports des modèles dans Power BI Desktop.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/11/2020
ms.author: v-pemyer
ms.openlocfilehash: dad451da460abed65a69990394522f268d7f21cd
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "81525250"
---
# <a name="separate-reports-from-models-in-power-bi-desktop"></a>Séparer les rapports des modèles dans Power BI Desktop

Lors de la création d’une solution Power BI Desktop, l’une des premières tâches à effectuer consiste à « obtenir des données ». L’obtention de données peut aboutir à deux résultats distincts. Cette opération peut :

- Créer une [connexion active](../desktop-report-lifecycle-datasets.md) à un modèle déjà publié, par exemple un jeu de données Power BI ou un modèle Analysis Services hébergé à distance.
- Initier le développement d’un nouveau modèle, par exemple un modèle d’importation, DirectQuery ou composite.

Cet article s’intéresse au deuxième scénario. Il fournit des conseils sur la combinaison d’un rapport et d’un modèle dans un fichier Power BI Desktop unique.

## <a name="single-file-solution"></a>Solution à fichier unique

Une _solution à fichier unique_ fonctionne bien lorsqu’il n’existe qu’un seul rapport basé sur le modèle. Dans ce cas, il est probable que le modèle et le rapport aient été créés par la même personne. Nous définissons un tel projet comme une solution _BI personnelle_, bien que le rapport puisse être partagé avec d’autres utilisateurs. Ces solutions peuvent représenter des rapports basés sur un rôle ou des évaluations à usage unique d’un défi commercial, et sont souvent appelées _rapports ad hoc_.

:::image type="content" source="media/report-separate-from-model/single-file-solution.png" alt-text="Un fichier unique contient un modèle et un rapport, développés par la même personne." border="true":::

## <a name="separate-report-files"></a>Fichiers de rapports distincts

Il est logique de séparer le développement du modèle et du rapport dans des fichiers Power BI Desktop distincts dans les cas suivants :

- Les modélisateurs des données et les auteurs des rapports sont des personnes différentes.
- Il est entendu qu’un modèle sera la source de plusieurs rapports, maintenant ou ultérieurement.

:::image type="content" source="media/report-separate-from-model/separate-report-files.png" alt-text="Il existe trois fichiers PBIX. Le premier contient uniquement un modèle. Les deux autres contiennent uniquement des rapports, qui se connectent en direct au modèle hébergé dans le service Power BI. Les rapports sont développés par différentes personnes." border="true":::

Les modélisateurs de données peuvent toujours utiliser la solution de création de rapports Power BI Desktop pour tester et valider leurs conceptions de modèles. Toutefois, juste après la publication de leur fichier dans le service Power BI, ils doivent supprimer le rapport de l’espace de travail. Ils doivent veiller à supprimer le rapport chaque fois qu’ils republient et remplacent le jeu de données.

### <a name="preserve-the-model-interface"></a>Conserver l’interface du modèle

Parfois, les modifications de modèle sont inévitables. Les modélisateurs de données doivent donc veiller à ne pas interrompre l’interface du modèle. Si c’est le cas, cela risquerait d’interrompre les visuels de rapport ou les vignettes de tableau de bord connexes. Les visuels interrompus apparaissent comme des erreurs et peuvent entraîner une certaine frustration chez les auteurs de rapports et les consommateurs. Et pire encore, ces derniers risquent de ne plus avoir confiance dans les données.

Par conséquent, gérez avec précaution les modifications de modèle. Évitez si possible les modifications suivantes :

- Renommer des tables, des colonnes, des hiérarchies, des niveaux de hiérarchie ou des mesures.
- Modification des types de données de colonnes.
- Modification d’expressions de mesure afin qu’elles retournent un type de données différent.
- Déplacement de mesures vers une autre table principale. Cela est dû au fait que le déplacement d’une mesure risque de rompre les mesures basées sur un rapport qui qualifient entièrement des mesures avec le nom de leur table principale. Nous vous déconseillons d’écrire des expressions DAX à l’aide de noms de mesures qualifiés complets. Pour plus d'informations, consultez [DAX : Références de colonne et de mesure](dax-column-measure-references.md).

L’ajout de tables, de colonnes, de hiérarchies, de niveaux de hiérarchie ou de mesures est une opération sécurisée, à une exception près : Il est possible qu’un nouveau nom de mesure puisse entrer en conflit avec le nom d’une mesure basée sur un rapport. Pour éviter tout conflit, nous recommandons aux auteurs de rapports d’adopter une convention d’affectation de noms lors de la définition de mesures dans leurs rapports. Ils peuvent préfixer les noms de mesures basées sur un rapport avec un trait de soulignement voire un ou plusieurs autres caractères.

Si vous devez apporter des modifications importantes à vos modèles, nous vous recommandons d’effectuer l’une des opérations suivantes :

- [Afficher un contenu associé pour le jeu de données](../consumer/end-user-related.md#view-related-content-for-a-dataset) dans le service Power BI.
- Explorez la vue [Traçabilité des données](../collaborate-share/service-data-lineage.md) dans le service Power BI.

Ces deux options vous permettent d’identifier rapidement tous les rapports et tableaux de bord associés. La vue Traçabilité des données est probablement la meilleure option car elle permet d’identifier facilement le contact pour chaque artefact associé. En fait, il s’agit d’un lien hypertexte qui ouvre un message électronique adressé au contact.

Nous vous recommandons de contacter le propriétaire de chaque artefact associé pour lui signaler les modifications importantes planifiées. De cette façon, cette personne peut se préparer à résoudre les éventuels problèmes et à republier ses rapports, réduisant ainsi les temps d’arrêt et la frustration.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations en rapport avec cet article, consultez les ressources suivantes :

- [Se connecter à des jeux de données dans le service Power BI à partir de Power BI Desktop](../desktop-report-lifecycle-datasets.md)
- [Afficher un contenu associé dans le service Power BI](../consumer/end-user-related.md)
- [Lignage des données](../collaborate-share/service-data-lineage.md)
- Vous avez des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
- Vous avez des suggestions ? [Envoyez-nous vos idées pour améliorer Power BI](https://ideas.powerbi.com/)
