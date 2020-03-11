---
title: Quand utiliser des rapports paginés dans Power BI
description: Guide sur l’utilisation des rapports paginés Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 01/04/2020
ms.author: v-pemyer
ms.openlocfilehash: 049b6ac14c6d35d68815eac32520a4eaa654ad42
ms.sourcegitcommit: ced8c9d6c365cab6f63fbe8367fb33e6d827cb97
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/07/2020
ms.locfileid: "78920734"
---
# <a name="when-to-use-paginated-reports-in-power-bi"></a>Quand utiliser des rapports paginés dans Power BI

Cet article s’adresse à vous en tant qu’auteur de rapports Power BI. Il a pour but de vous aider à choisir quand développer des [rapports paginés Power BI](../paginated-reports/paginated-reports-report-builder-power-bi.md).

> [!NOTE]
> La publication des rapports paginés Power BI nécessite un abonnement Power BI Premium. Les rapports s’affichent uniquement lorsqu’ils se trouvent dans un espace de travail situé dans une capacité dédiée où la [charge de travail Rapports paginés est activée](../service-admin-premium-workloads.md#paginated-reports).

Les rapports paginés Power BI sont optimisés pour l’**impression** et la **génération de PDF**. Ils vous permettent également de créer des dispositions impeccables et sophistiquées. Les rapports paginés sont donc parfaits pour les rapports opérationnels, tels que les factures.

Les rapports Power BI, quant à eux, sont optimisés pour l’**exploration et l’interactivité**. En outre, ils vous permettent d’utiliser une gamme complète de visuels ultramodernes pour la présentation de vos données. Par conséquent, les rapports Power BI sont parfaits pour les rapports d’analytique, qui permettent aux utilisateurs de vos rapports d’explorer les données et de découvrir des relations et des modèles.

Nous vous recommandons d’utiliser un rapport paginé Power BI dans les cas suivants :

- Lorsque vous savez que le rapport doit être imprimé ou affiché sous la forme d’un document PDF.
- Lorsque les dispositions de grille de données sont susceptibles d’être développées et de déborder. Notez qu’une table (ou matrice) d’un rapport Power BI ne peut pas être redimensionnée dynamiquement pour afficher toutes les données. Des barres de défilement sont donc prévues à cet effet. Toutefois, si vous l’imprimez, vous ne pourrez pas utiliser le défilement pour afficher les données qui sont en dehors de la vue.
- Les fonctionnalités paginées Power BI vous seront très utiles. De nombreux cas d’utilisation de ces rapports seront abordés plus loin dans cet article.

## <a name="legacy-reports"></a>Rapports hérités

Si vous disposez déjà de rapports [RDL](/sql/reporting-services/reports/report-definition-language-ssrs) SQL Server Reporting Services (SSRS), vous pouvez choisir de les redévelopper sous la forme de [rapports Power BI](../consumer/end-user-reports.md) ou d’effectuer leur migration vers Power BI en tant que rapports paginés. Pour plus d’informations, consultez [Effectuer la migration de rapports SQL Server Reporting Services vers Power BI](migrate-ssrs-reports-to-power-bi.md).

Une fois publiés dans un espace de travail Power BI, les rapports paginés s’affichent en regard des rapports Power BI. Ils peuvent ensuite être facilement distribués à l’aide d’[applications Power BI](../service-create-distribute-apps.md).

Si vous le souhaitez, vous pouvez redévelopper des rapports SSRS, plutôt que d’effectuer leur migration. Ceci est particulièrement vrai pour les rapports à visée analytique. Dans ce cas, les rapports Power BI offriront probablement la meilleure expérience utilisateur.

## <a name="paginated-report-scenarios"></a>Scénarios impliquant des rapports paginés

Les rapports paginés Power BI offrent de nombreuses possibilités. Celles-ci correspondent à des fonctionnalités qui ne sont pas prises en charge par les rapports Power BI.

- **Prêt pour l’impression** : Les rapports paginés sont optimisés pour l’impression et la génération de PDF. Si nécessaire, les régions de données peuvent être développées en vue de déborder sur plusieurs pages de manière contrôlée. Dans vos mises en page de rapport, vous pouvez définir des marges, ainsi que des en-têtes et des pieds de page.
- **Formats du rendu** : Power BI peut afficher des rapports paginés dans différents formats. Ces formats incluent notamment Microsoft Excel, Microsoft Word, Microsoft PowerPoint, PDF, CSV, XML et MHTML (le format MHTML est utilisé par le service Power BI pour afficher les rapports). Les utilisateurs de votre rapport peuvent décider de l’exporter au format qui leur convient.
- **Disposition précise** : vous pouvez concevoir des dispositions impeccables et très sophistiquées, à la même taille et au même emplacement que ceux qui ont été configurés en fractions de pouce ou en centimètres.
- **Disposition dynamique** : vous pouvez produire des dispositions hautement réactives en définissant de nombreuses propriétés de rapport qui utilisent des expressions VB.NET. Les expressions ont accès à un grand nombre de bibliothèques .NET Framework principales.
- **Disposition en fonction du rendu** : vous pouvez utiliser des expressions pour modifier la mise en page du rapport en fonction du format de rendu appliqué. Par exemple, vous pouvez concevoir le rapport de manière à désactiver le basculement de la visibilité (pour monter ou descendre dans la hiérarchie) lorsqu’il est affiché dans un format non interactif, tel que le format PDF.
- **Requêtes natives** : il n’est pas nécessaire de développer d’abord un jeu de données Power BI. Il est possible de créer des requêtes natives (ou d’utiliser des procédures stockées) pour toutes les [sources de données prises en charge](../paginated-reports/paginated-reports-data-sources.md). Les requêtes peuvent inclure un paramétrage.
- **Concepteurs de requêtes graphiques** : Power BI Report Builder proposent des concepteurs de requêtes graphiques qui peuvent vous aider à écrire et à tester vos requêtes de jeux de données.
- **Jeux de données statiques** : vous pouvez définir un jeu de données et entrer les données directement dans la définition de votre rapport. Cette fonctionnalité est particulièrement utile pour une démonstration ou la fourniture d’une preuve de concept (POC).
- **Intégration des données** : Vous pouvez combiner des données provenant de différentes sources de données, ou les combiner avec des jeux de données statiques. Pour cela, vous devez créer des champs personnalisés à l’aide d’expressions VB.NET.
- **Paramétrage** : vous pouvez concevoir des expériences de paramétrage hautement personnalisées, comprenant notamment des paramètres en cascade et des paramètres basés sur les données. Il est également possible de définir des paramètres par défaut. Ces expériences peuvent être conçues pour aider les utilisateurs de vos rapports à appliquer rapidement les filtres nécessaires. En outre, les paramètres n’ont pas besoin de filtrer les données du rapport. Ils peuvent être utilisés pour l’évaluation des scénarios, ou pour prendre en charge le filtrage et l’application de style dynamiques.
- **Données image** : votre rapport peut afficher des images lorsqu’elles sont stockées au format binaire dans une source de données.
- **Code personnalisé** : vous pouvez développer des blocs de code de fonctions VB.NET dans votre rapport et les utiliser dans n’importe quelle expression de rapport.
- **Sous-rapports** : vous pouvez incorporer d’autres rapports paginés Power BI (à partir du même espace de travail) dans votre rapport.
- **Grilles de données flexibles** : vous disposez d’un contrôle affiné sur les dispositions de grille grâce à la région de données de tableau matriciel. Celle-ci prend également en charge les dispositions complexes, notamment celles qui comprennent des groupes imbriqués et adjacents. Elle peut être configurée pour répliquer des en-têtes lors d’une impression sur plusieurs pages. En outre, elle peut incorporer un sous-rapport ou d’autres visualisations, y compris des barres de données, des graphiques sparkline et des indicateurs.
- **Types de données spatiales** : la région de données de carte permet de visualiser des [types de données spatiales SQL Server](/sql/relational-databases/spatial/spatial-data-sql-server). Les types de données GEOGRAPHY et GEOMETRY peuvent donc être utilisés pour visualiser des points, des lignes ou des polygones. Vous pouvez aussi visualiser les polygones définis dans des fichiers de forme ESRI.
- **Jauges modernes** : les jauges radiales et linéaires peuvent être utilisées pour afficher les valeurs et l’état des indicateurs de performance clés. Elles peuvent même être incorporées dans les régions de données de grille, ce qui permet leur réplication au sein des groupes.
- **Rendu HTML** : vous pouvez afficher un texte enrichi au format RTF lorsqu’il est stocké au format HTML.
- **Publipostage** : vous pouvez utiliser des espaces réservés de zone de texte pour injecter des valeurs de données dans du texte. De cette façon, vous pouvez créer un rapport de publipostage.
- **Fonctionnalités d’interactivité** : les fonctionnalités interactives incluent le basculement de la visibilité (pour descendre et monter dans la hiérarchie), les liens, le tri interactif et les info-bulles. Vous pouvez également ajouter des liens permettant d’explorer les données des rapports Power BI ou des rapports paginés Power BI. Les liens permettent même d’atteindre un autre emplacement du même rapport.
- **Abonnements** : Power BI peut envoyer, selon un calendrier, des rapports paginés sous forme d’e-mails comprenant des pièces jointes aux formats pris en charge.
- **Mise en page par utilisateur** : vous pouvez créer des mises en page de rapport qui changent en fonction de l’utilisateur authentifié qui ouvre le rapport. Vous pouvez concevoir le rapport de manière à filtrer les données différemment, masquer les régions de données ou les visualisations, appliquer des formats différents ou définir des valeurs par défaut pour chaque utilisateur.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations en rapport avec cet article, consultez les ressources suivantes :

- [Présentation des rapports paginés dans Power BI Premium](../paginated-reports/paginated-reports-report-builder-power-bi.md)
- [Effectuer la migration des rapports SQL Server Reporting Services vers Power BI](migrate-ssrs-reports-to-power-bi.md)
- Vous avez des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
- Vous avez des suggestions ? [Envoyez-nous vos idées pour améliorer Power BI](https://ideas.powerbi.com/)
