---
title: Bonnes pratiques relatives aux performances de Power BI Embedded
description: Cet article fournit des conseils relatifs aux bonnes pratiques de l’analytique incorporée
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-embedded
ms.topic: conceptual
ms.date: 12/12/2018
ms.openlocfilehash: d0f4ca29e30e5f6e6176f036dc535601eb580471
ms.sourcegitcommit: 298db44200b78b1281b3ae6dfe7cce7a89865ec9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53329875"
---
# <a name="power-bi-embedded-performance-best-practices"></a>Bonnes pratiques relatives aux performances de Power BI Embedded

Cet article fournit des recommandations pour un rendu plus rapide des rapports, des tableaux de bord et des vignettes dans votre application

## <a name="embed-parameters"></a>Paramètres incorporés

La méthode Powerbi.embed() reçoit peu de paramètres pour incorporer un rapport, un tableau de bord ou une vignette. Ces paramètres ont un impact sur les performances.

### <a name="embed-url"></a>URL incorporé

Évitez de générer l’URL incorporé. Au lieu de cela, assurez-vous d’obtenir l’URL incorporé en appelant l’API [Obtenir des rapports](https://na01.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Frest%2Fapi%2Fpower-bi%2Freports%2Fgetreportsingroup&data=02%7C01%7CMark.Ghanayem%40microsoft.com%7C07ca68ceb37a48e3f3de08d64968707a%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636777110256168308&sdata=22lkqRM2w1MQfrM8dooedaPqqIU8PufTq9TT4VDzRo0%3D&reserved=0), [Obtenir des tableaux de bord](https://na01.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Frest%2Fapi%2Fpower-bi%2Fdashboards%2Fgetdashboardsingroup&data=02%7C01%7CMark.Ghanayem%40microsoft.com%7C07ca68ceb37a48e3f3de08d64968707a%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636777110256168308&sdata=nfWRgbSoXVF42Rg%2Ba9491u19uksXp%2FAyz%2Fa%2Ba7%2FCtdA%3D&reserved=0), ou [Obtenir des vignettes](https://na01.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Frest%2Fapi%2Fpower-bi%2Fdashboards%2Fgettilesingroup&data=02%7C01%7CMark.Ghanayem%40microsoft.com%7C07ca68ceb37a48e3f3de08d64968707a%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636777110256178318&sdata=LgZ27TynNpqQJDrb3aHWGQXIS%2FzichAO9De5M2uhF1Q%3D&reserved=0). Nous avons ajouté un nouveau paramètre à l’URL nommé **_config_**, utilisé pour l’amélioration des performances.

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

* Utilisez toujours la dernière version de [Power BI Desktop](https://powerbi.microsoft.com/en-us/desktop/).

* Installez la dernière version du [Kit de développement logiciel (SDK) client Power BI](https://github.com/Microsoft/PowerBI-JavaScript). Nous continuons de publier de nouvelles améliorations. Veillez donc à les suivre de temps à autre.

* Packages à installer :
    * Package npm : powerbi-client
    * Package NuGet : Microsoft.PowerBI.JavaScript

> [!Note]
> N’oubliez pas que le temps de chargement dépend principalement d’éléments relatifs au rapport et aux données, tels que le nombre de visuels, la taille des données, la complexité des requêtes et les mesures calculées. Veuillez suivre les [meilleures pratiques](../power-bi-reports-performance.md) afin d’améliorer le temps de chargement du rapport.

## <a name="next-steps"></a>Étapes suivantes

* [Performances du rapport](../power-bi-reports-performance.md)
* [Comment résoudre les problèmes de Power BI Embedded](embedded-troubleshoot.md)
* [FAQ sur Power BI Embedded](embedded-faq.md)
