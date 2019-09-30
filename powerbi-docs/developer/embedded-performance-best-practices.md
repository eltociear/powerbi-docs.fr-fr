---
title: Bonnes pratiques relatives aux performances de Power BI Embedded
description: Cet article fournit des conseils relatifs aux bonnes pratiques de l’analytique incorporée
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 12/12/2018
ms.openlocfilehash: 93c26d64193346b9b2db52bb2d0a0bbe32a4e97b
ms.sourcegitcommit: 57e45f291714ac99390996a163436fa1f76db427
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/26/2019
ms.locfileid: "71305707"
---
# <a name="power-bi-embedded-performance-best-practices"></a>Bonnes pratiques relatives aux performances de Power BI Embedded

Cet article fournit des recommandations pour un rendu plus rapide des rapports, des tableaux de bord et des vignettes dans votre application.

> [!Note]
> N’oubliez pas que le temps de chargement dépend principalement des éléments pertinents pour le rapport et des données elles-mêmes, y compris des visuels, la taille des données et la complexité des requêtes et des mesures calculées. Pour plus d’informations, consultez [Bonnes pratiques relatives aux performances de Power BI](../power-bi-reports-performance.md).

## <a name="update-tools-and-sdk-packages"></a>Mettre à jour les outils et les packages du SDK

Maintenez les outils et les packages du SDK à jour.

* Utilisez toujours la dernière version de [Power BI Desktop](https://powerbi.microsoft.com/desktop/).

* Installez la dernière version du [Kit de développement logiciel (SDK) client Power BI](https://github.com/Microsoft/PowerBI-JavaScript). Nous continuons de publier de nouvelles améliorations. Veillez donc à les suivre de temps à autre.

## <a name="embed-parameters"></a>Paramètres incorporés

La méthode `powerbi.embed(element, config)` reçoit un élément et une configuration. Le paramètre de configuration comprend des champs qui ont des implications en termes de performances.

### <a name="embed-url"></a>URL incorporé

Évitez de générer l’URL incorporé. Au lieu de cela, assurez-vous d’obtenir l’URL incorporée en appelant l’API [Obtenir des rapports](/rest/api/power-bi/reports/getreportsingroup), [Obtenir des tableaux de bord](/rest/api/power-bi/dashboards/getdashboardsingroup), ou [Obtenir des vignettes](/rest/api/power-bi/dashboards/gettilesingroup). Nous avons ajouté un nouveau paramètre à l’URL nommé **_config_** , qui sert pour l’amélioration des performances.

### <a name="permissions"></a>Autorisations

Fournissez des autorisations d’**affichage** si vous ne souhaitez pas incorporer un rapport en mode édition. De cette façon, le code incorporé n’initialise pas les composants qui sont utilisés pour le mode Édition.

### <a name="filters-bookmarks-and-slicers"></a>Filtres, signets et segments

En règle générale, les visuels d’un rapport sont enregistrés avec les données en cache. Les données en cache sont utilisées pour fournir des performances perçues. Les rapports affichent des données en cache tandis que les requêtes sont exécutées. Si des filtres, des signets ou des segments sont fournis, les données mises en cache ne sont pas pertinentes et les visuels sont rendus uniquement après la fin de la requête visuelle.

Si vous incorporez des rapports avec les mêmes filtres, signets et segments pour améliorer vos performances, enregistrez le rapport avec les filtres, signets et segments déjà appliqués. Cela affiche le rapport avec les données mises en cache, ce qui comprend les filtres, les signets et les segments.

## <a name="switching-between-reports"></a>Basculement entre rapports

Lorsque vous incorporez plusieurs rapports au même iframe, ne générez pas de nouvel iframe pour chaque rapport. Utilisez plutôt `powerbi.embed(element, config)` avec une autre configuration pour incorporer le nouveau rapport.

> [!NOTE]
> Le basculement entre rapports pour un scénario de type « l’application possède les données » peut ne pas être très efficace en raison de la nécessité de générer un nouveau jeton incorporé.

## <a name="query-caching"></a>Mise en cache des requêtes

Les organisations avec une capacité Power BI Premium ou Power BI Embedded peuvent tirer parti de la mise en cache des requêtes pour accélérer l’exécution de rapports associés à un jeu de données.

[En savoir plus sur la mise en cache des requêtes dans Power BI](../power-bi-query-caching.md).

## <a name="preload"></a>Préchargement

Utilisez `powerbi.preload()` afin d’améliorer les performances pour l’utilisateur final. La méthode `powerbi.preload()` télécharge des fichiers JavaScript, CSS et d’autres artefacts, qui seront utilisés ultérieurement pour être incorporés dans un rapport.

Appelez `powerbi.preload()` si vous n’incorporez pas immédiatement le rapport. Par exemple, si le contenu Power BI intégré n'apparaît pas sur la page d'accueil, utilisez `powerbi.preload()` pour télécharger et mettre en cache les artefacts utilisés pour intégrer le contenu.

## <a name="bootstrapping-the-iframe"></a>Amorçage de l’iframe

> [!NOTE]
> [Power BI client SDK](https://github.com/Microsoft/PowerBI-JavaScript) version 2.9 est requis pour amorcer l’iframe.

`powerbi.bootstrap(element, config)` vous permet de commencer l'intégration avant que tous les paramètres requis ne soient disponibles. L’API d’amorçage prépare et initialise l’iframe.
Lors de l'utilisation de l'API d’amorçage, il est toujours nécessaire d'appeler `powerbi.embed(element, config)` sur le même élément HTML.

Par exemple, vous pouvez utiliser cette fonctionnalité pour effectuer l’amorçage d’iframe et les appels au principal pour l'incorporation, en parallèle.
> [!TIP]
> Utilisez si possible l'API d’amorçage pour générer l'iframe avant qu'il ne soit visible pour l'utilisateur final.

[En savoir plus sur l’amorçage d’iframe](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Bootstrap-For-Better-Performance).

## <a name="measure-performance"></a>Mesurer les performances

### <a name="performance-events"></a>Événements de performances

Pour mesurer les performances incorporées, vous pouvez utiliser deux événements :

1. Événement chargé : Délai avant que le rapport soit initialisé (le logo de Power BI disparaît une fois la charge terminée).
2. Événement rendu : Délai avant que le rapport complet soit rendu à l’aide de données réelles. L’événement rendu est déclenché chaque fois que le rapport est rendu à nouveau (par exemple après l’application des filtres). Pour mesurer un rapport, assurez-vous d’effectuer les calculs dans le premier événement déclenché.

Les données mises en cache sont rendues quand elles sont disponibles, mais aucun événement supplémentaire n’est généré.

[En savoir plus sur la gestion des événements](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Handling-Events).

### <a name="performance-analyzer"></a>Analyseur de performances

Pour examiner les performances des éléments de rapport, vous pouvez utiliser l’analyseur de performances dans Power BI Desktop.
L’analyseur de performances vous permet de voir et d’enregistrer les journaux qui mesurent la façon dont chacun de vos éléments de rapport s’exécute.

[En savoir plus sur l’Analyseur de performances](../desktop-performance-analyzer.md).

> [!NOTE]
> N’oubliez pas de comparer les performances du rapport incorporé aux performances sur powerbi.com. Cela peut vous aider à comprendre l’origine de vos problèmes de performances

## <a name="next-steps"></a>Étapes suivantes

* [Bonnes pratiques relatives aux performances des rapports Power BI](../power-bi-reports-performance.md)
* [Comment résoudre les problèmes de Power BI Embedded](embedded-troubleshoot.md)
* [FAQ sur Power BI Embedded](embedded-faq.md)
