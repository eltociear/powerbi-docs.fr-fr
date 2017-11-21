---
title: "Utiliser des informations dans Power BI Desktop (préversion)"
description: Obtenir facilement des informations sur des augmentations ou des diminutions dans Power BI Desktop
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 09/25/2017
ms.author: davidi
ms.openlocfilehash: d4b1d1866fc56d48960539a420819d99afc13eb1
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2017
---
# <a name="use-insights-in-power-bi-desktop-preview"></a>Utiliser des informations dans Power BI Desktop (préversion)
Vous pouvez demander à **Power BI Desktop** d’expliquer des hausses ou des baisses observées dans des graphiques, et obtenir une analyse automatique, rapide et révélatrice de vos données. Cliquez simplement avec le bouton droit sur un point de données, puis sélectionnez **Analyser > Expliquer la baisse** (ou la hausse si la barre précédente était plus basse). Vous obtenez ainsi une information dans une fenêtre facile à utiliser.

![](media/desktop-insights/insights_01.png)

Cette fonctionnalité est contextuelle et basée sur le point de données immédiatement précédent, par exemple, la barre ou la colonne précédentes.

> [!NOTE]
> Cette fonctionnalité étant en préversion, elle est sujette à modification. La fonctionnalité permettant d’obtenir des informations est activée par défaut (vous n’avez pas besoin de cliquer sur une zone d’aperçu pour l’activer) à partir de la version de septembre 2017 de **Power BI Desktop**.
> 
> 

## <a name="using-insights"></a>Utilisation des informations
Pour utiliser les informations, cliquez simplement avec le bouton droit sur un point de données quelconque dans un visuel de barre ou de ligne, puis sélectionnez **Analyser > Expliquer la hausse** (ou *Expliquer la baisse*, puisque toutes les informations fournies sont basées sur le changement par rapport au point de données précédent).

![](media/desktop-insights/insights_02.png)

**Power BI Desktop** exécute alors ses algorithmes d’apprentissage sur les données, puis insère dans une fenêtre un visuel et une description des catégories qui ont le plus influencé la hausse ou la baisse. Par défaut, ces informations sont fournies sous la forme d’un visuel *en cascade*, comme illustré dans l’image suivante.

![](media/desktop-insights/insights_03.png)

En sélectionnant les petites icônes au bas du visuel en cascade, vous pouvez choisir d’afficher les informations dans un nuage de points, un histogramme empilé ou un graphique de ruban.

![](media/desktop-insights/insights_04.png)

Les icônes de *pouce levé* et de *pouce baissé* en haut de la page vous permettent de commenter le visuel et la fonctionnalité.

Et surtout, le bouton **+** en haut d’un visuel vous permet d’ajouter le visuel sélectionné à votre rapport, exactement comme si vous créiez le visuel manuellement. Vous pouvez ensuite mettre en forme ou ajuster autrement le visuel ajouté, comme vous le feriez pour tout autre visuel figurant sur votre rapport. Lorsque vous modifiez un rapport dans **Power BI Desktop**, vous ne pouvez ajouter qu’un seul visuel d’information sélectionné.

Vous pouvez utiliser cette fonctionnalité d’affichage d’informations lorsque votre rapport est en mode de lecture ou de modification. La fonctionnalité est donc polyvalente pour l’analyse de données et la création de visuels que vous pouvez aisément ajouter à vos rapports.

## <a name="considerations-and-limitations"></a>Considérations et limitations
Étant donné que les insights sont basés sur la modification du précédent point de données, ils ne sont pas disponibles lorsque vous sélectionnez le premier point de données d’un visuel. 

La liste suivante répertorie les scénarios actuellement non pris en charge pour la fonctionnalités d’affichage d’**informations** :

* Filtres TopN
* Filtres Inclure/Exclure
* Filtres de mesures
* Mesures et agrégats non additifs
* Afficher la valeur comme
* Mesures filtrées (nouvelle ressource que nous utilisons pour les nuages de points dans les informations)
* Colonnes de catégorie sur l’axe X, sauf si celui-ci définit un tri par colonne de type scalaire. Si vous utilisez une hiérarchie, chaque colonne dans la hiérarchie active doit remplir cette condition.
* Mesures non numériques

De plus, les sources de données et les types de modèles suivants ne sont actuellement pas pris en charge pour la fonctionnalité d’affichage d’informations :

* DirectQuery
* Live Connect
* Reporting Services en local
* Incorporation

## <a name="next-steps"></a>Étapes suivantes
Pour plus d’informations sur **Power BI Desktop** et la prise en main de cette solution, voir les articles suivants.

* [Prise en main de Power BI Desktop](desktop-getting-started.md)
* [Présentation des requêtes dans Power BI Desktop](desktop-query-overview.md)
* [Sources de données dans Power BI Desktop](desktop-data-sources.md)
* [Se connecter aux données dans Power BI Desktop](desktop-connect-to-data.md)
* [Mettre en forme et combiner des données dans Power BI Desktop](desktop-shape-and-combine-data.md)
* [Tâches courantes relatives aux requêtes dans Power BI Desktop](desktop-common-query-tasks.md)   

