---
title: Bonnes pratiques relatives aux performances de Power BI Embedded
description: Cet article fournit des conseils relatifs aux bonnes pratiques de l’analytique incorporée
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-embedded
ms.topic: conceptual
ms.date: 12/12/2018
ms.openlocfilehash: 50fbb175640e38431db62df34276417f1080e42a
ms.sourcegitcommit: a36f82224e68fdd3489944c9c3c03a93e4068cc5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2019
ms.locfileid: "55430347"
---
# <a name="power-bi-embedded-performance-best-practices"></a>Bonnes pratiques relatives aux performances de Power BI Embedded

Cet article fournit des recommandations pour un rendu plus rapide des rapports, des tableaux de bord et des vignettes dans votre application

## <a name="embed-parameters"></a>Paramètres incorporés

La méthode Powerbi.embed() reçoit peu de paramètres pour incorporer un rapport, un tableau de bord ou une vignette. Ces paramètres ont un impact sur les performances.

### <a name="embed-url"></a>URL incorporé

Évitez de générer l’URL incorporé. Au lieu de cela, assurez-vous d’obtenir l’URL incorporé en appelant l’API [Obtenir des rapports](/rest/api/power-bi/reports/getreportsingroup), [Obtenir des tableaux de bord](/rest/api/power-bi/dashboards/getdashboardsingroup), ou [Obtenir des vignettes](/rest/api/power-bi/dashboards/gettilesingroup). Nous avons ajouté un nouveau paramètre à l’URL nommé **_config_**, utilisé pour l’amélioration des performances.

### <a name="permissions"></a>Autorisations

Fournissez des autorisations d’**affichage** si vous ne souhaitez pas incorporer un rapport en **mode Édition**. De cette façon, le code incorporé n’initialise pas les composants qui sont utilisés pour le mode Édition.

### <a name="filters-bookmarks-and-slicers"></a>Filtres, signets et segments

En règle générale, les visuels d’un rapport sont enregistrés avec les données en cache. Les données en cache sont utilisées pour fournir des performances perçues. Les rapports affichent des données en cache tandis que les requêtes sont exécutées. Si des filtres, signets ou segments sont fournis, les données en cache ne sont pas applicables. Ensuite, les visuels sont rendus uniquement après l’exécution de la requête visuelle.

Si vous incorporez des rapports avec les mêmes filtres, enregistrez le rapport avec des filtres déjà appliqués pour éviter de transmettre une liste de filtres dans la configuration de la charge.

## <a name="preload"></a>Préchargement

Utilisez l’API JavaScript *Préchargement* pour améliorer les performances de l’utilisateur final.
Powerbi.preload() télécharge des fichiers JavaScript, CSS et d’autres artefacts, qui seront utilisés ultérieurement pour être incorporés dans un rapport.

Appelez le préchargement si vous n’incorporez pas immédiatement le rapport. Par exemple, si vous incorporez un rapport sur un bouton, il est préférable d’appeler le préchargement lors du chargement de la page précédente. Ainsi, lorsque l’utilisateur de l’application clique sur le bouton, le rendu est plus rapide.

## <a name="measure-performance"></a>Mesurer les performances

Pour mesurer les performances, utilisez :

1. Chargé : délai jusqu’à ce que le rapport soit initialisé (l’utilisateur ne voit aucun effet).
2. Rendu : délai jusqu’à ce que le rapport complet soit rendu à l’aide de données réelles. L’événement rendu est déclenché chaque fois que le rapport est rendu à nouveau (autrement dit, après l’application des filtres). Pour d’abord mesurer un rapport, assurez-vous d’effectuer les calculs dans le premier événement déclenché.

Les données en cache sont rendues quand elles sont disponibles, mais nous n’avons pas encore d’événement pour ces données.

## <a name="update-tools-and-sdk-packages"></a>Mettre à jour les outils et les packages du SDK

Maintenez les outils et les packages du SDK à jour.

* Utilisez toujours la dernière version de [Power BI Desktop](https://powerbi.microsoft.com/desktop/).

* Installez la dernière version du [Kit de développement logiciel (SDK) client Power BI](https://github.com/Microsoft/PowerBI-JavaScript). Nous continuons de publier de nouvelles améliorations. Veillez donc à les suivre de temps à autre.

* Packages à installer :
    * Package npm : powerbi-client
    * Package NuGet : Microsoft.PowerBI.JavaScript

> [!Note]
> N’oubliez pas que le temps de chargement dépend principalement d’éléments relatifs au rapport et aux données, tels que le nombre de visuels, la taille des données, la complexité des requêtes et les mesures calculées. Veuillez suivre les [meilleures pratiques](../power-bi-reports-performance.md) afin d’améliorer le temps de chargement du rapport.

## <a name="next-steps"></a>Étapes suivantes

* [Bonnes pratiques relatives aux performances des rapports Power BI](../power-bi-reports-performance.md)
* [Comment résoudre les problèmes de Power BI Embedded](embedded-troubleshoot.md)
* [FAQ sur Power BI Embedded](embedded-faq.md)
