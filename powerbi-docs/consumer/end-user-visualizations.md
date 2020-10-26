---
title: Utilisation des visualisations (visuels) en tant qu’utilisateur professionnel
description: Concepts et terminologie de Power BI - visualisations, éléments visuels. Qu’est-ce qu’une visualisation, un élément visuel Power BI.
author: mihart
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: how-to
ms.date: 10/7/2020
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: f463e9a065ddfa550cdab6929393cfb71ce30158
ms.sourcegitcommit: d2f633b4bfa271051ba1d2ef0e6e8da7dcf42818
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2020
ms.locfileid: "91830294"
---
# <a name="interact-with-visuals-in-reports-dashboards-and-apps"></a>Interagir avec les visuels dans les rapports, les tableaux de bord et les applications

[!INCLUDE[consumer-appliesto-ynny](../includes/consumer-appliesto-ynny.md)]

Dans sa version la plus basique, une ***visualisation*** (ou *élément visuel*), est un type de graphique créé par les *concepteurs* Power BI à l’aide des données dans les rapports et les jeux de données. 

Vous pouvez utiliser les visuels disponibles dans les tableaux de bord et les rapports, ou en créer instantanément à l’aide de la fonctionnalité Questions et réponses de Power BI. Quand un concepteur crée un visuel dans un rapport, il peut *épingler* ce nouveau visuel à un tableau de bord. [Un visuel sur un tableau de bord est appelé *vignette*](end-user-tiles.md). Ce tableau de bord comporte huit vignettes. 

![Tableau de bord avec des vignettes](media/end-user-visualizations/power-bi-dashboard.png)

> [!TIP]
> Nous vous recommandons de lire tout d’abord la rubrique de présentation [Concepts de base de Power BI pour les *utilisateurs professionnels*](end-user-basic-concepts.md) avant de lire ce contenu plus détaillé.

## <a name="what-can-i-do-with-visuals"></a>Que puis-je faire avec les visuels ?

Les visuels sont créés par des *concepteurs* de rapport et de tableau de bord, et partagés avec les collègues. Le concepteur affecte différentes autorisations à ses collègues, en fonction de la façon dont le collègue va utiliser le rapport ou tableau de bord. Par exemple, un *développeur* peut se voir attribuer des autorisations différentes de celles d’un *utilisateur professionnel*. 

Les tâches les plus courantes pour un *utilisateur professionnel* sont répertoriées dans le tableau ci-dessous, avec des liens vers des instructions pas à pas. Les *utilisateurs professionnels* disposent de nombreuses options pour interagir avec des visuels pour découvrir des insights et prendre des décisions métier pilotées par les données.  

Pour la plupart de ces options, votre administrateur ou le *concepteur* peut désactiver les fonctionnalités associées afin que vous ne puissiez pas les voir ni les utiliser. Par ailleurs, certaines de ces fonctionnalités sont uniquement utilisables dans des types de visuels particuliers.  Si vous avez des questions, contactez votre administrateur ou bien le propriétaire du rapport ou du tableau de bord. Pour savoir qui est le propriétaire, ouvrez la liste déroulante du rapport ou du tableau de bord. 

![Liste déroulante du titre indiquant le propriétaire](media/end-user-visualizations/power-bi-designer.png)


> [!IMPORTANT]
> Mais tout d’abord, parlons de Q&A. Q&A est l’outil de recherche en langage naturel de Power BI. Vous tapez une question à l’aide du langage naturel et Q&A répond à la question sous la forme d’un visuel. Questions et réponses permet aux utilisateurs professionnels de créer leurs propres visuels à la volée. Toutefois, les visuels que vous créez avec Q&A ne peuvent pas être enregistrés. Mais Q&A constitue une excellente option si vous voulez apprendre quelque chose de spécifique sur les données et que le concepteur n’a pas inclus cet élément dans un rapport ou un tableau de bord. Pour en savoir plus sur Q&A, consultez [Q&A pour les utilisateurs professionnels](end-user-q-and-a.md).



|Tâche  |Sur un tableau de bord  |Dans un rapport  | Dans Q&A
|---------|---------|---------|--------|
|[Ajouter des commentaires à un visuel pour vous-même ou démarrer une conversation sur le visuel avec des collègues](end-user-comment.md).     |  Oui       |   Oui      |  non  |
|[Ouvrir et explorer le rapport où le visuel a été créé](end-user-tiles.md).     |    Oui     |   na      |  non |
|[Afficher la liste des filtres et des segments qui impactent le visuel](end-user-report-filter.md).     |    oui, en mode Focus     |   Oui      |  non |
|[Ouvrir et explorer un visuel dans Questions et réponses (si le *concepteur* a utilisé Questions et réponses pour créer le visuel)](end-user-q-and-a.md).     |   Oui      |   na      |  na  |
|[Créer un visuel dans Questions et réponses (pour l’exploration, vous ne pourrez pas l’enregistrer)](end-user-q-and-a.md).     |   Oui      |   si le concepteur a ajouté Questions et réponses au rapport      |  Oui  |
|[Demander à Power BI de rechercher pour vous des faits intéressants ou des tendances](end-user-insights.md) dans les données du visuel.  Ces visuels générés automatiquement sont appelés *insights*.     |    oui, pour les vignettes    |  non       | non   |
|[Afficher un seule visuel à la fois avec le mode *Focus*](end-user-focus.md).     | oui, pour les vignettes        |   oui, pour les visuels      | na  |
|[Rechercher la dernière actualisation du visuel](end-user-fresh.md).     |  Oui       |    Oui     | na  |
|[Afficher un seul visuel à la fois, sans bordures ni volets de navigation, en mode *plein écran*](end-user-focus.md).     |   Oui      |  Oui       | par défaut  |
|[Imprimer](end-user-print.md).     |  Oui       |   Oui      | non  |
|[Explorer le visuel en ajoutant et en modifiant les filtres du visuel.](end-user-report-filter.md)     |    non     |   Oui      | non  |
|Pointer sur un visuel pour afficher des info-bulles et des détails supplémentaires.     |    Oui     |   Oui      | Oui  |
|[Filtrer en croisé et mettre en surbrillance croisée d’autres visuels sur la page.](end-user-interactions.md)    |   non      |   Oui      | na  |
|[Afficher les données utilisées pour créer le visuel](end-user-show-data.md).     |  non       |   Oui      | non  |
| [Modifier l’ordre de tri du visuel](end-user-change-sort.md). | non  | Oui  | peut modifier le tri en reformulant la question  |
| [Ajoutez un projecteur à un visuel](end-user-spotlight.md). | non  | Oui  |  non |
| [Exporter vers Excel.](end-user-export.md) | Oui | Oui | non|
| [Créer une alerte](end-user-alerts.md) pour vous avertir lorsqu’une valeur dépasse un seuil que vous avez défini.  | Oui  | non  | non |
| [Appliquer un filtrage croisé et une sélection croisée aux autres visuels de la page](end-user-report-filter.md).  | non      | Oui  | na |
| [Explorer un visuel qui a une hiérarchie](end-user-drill.md).  | non  | Oui   | non |

## <a name="next-steps"></a>Étapes suivantes
Retour aux [Concepts de base pour les utilisateurs professionnels](end-user-basic-concepts.md)    
[Sélectionner un visuel pour ouvrir un rapport](end-user-report-open.md)    
[Types de visuels disponibles dans Power BI](end-user-visual-type.md)