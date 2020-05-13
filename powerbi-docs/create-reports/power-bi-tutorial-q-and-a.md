---
title: Utiliser la fonctionnalité Questions et réponses Power BI pour explorer vos données et créer des visuels
description: Découvrez comment utiliser la fonctionnalité Questions et réponses Power BI pour créer des visualisations dans des tableaux de bord et des rapports.
author: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/13/2019
ms.author: maggies
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: b98d3b154d779a9b9ae04dfa00a6033d59c45c9c
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83309587"
---
# <a name="use-power-bi-qa-to-explore-your-data-and-create-visuals"></a>Utiliser la fonctionnalité Questions et réponses Power BI pour explorer vos données et créer des visuels

Il est parfois plus rapide d’obtenir des informations à partir de vos données en posant une question dans un langage naturel. La fonctionnalité Questions et réponses de Power BI vous permet d’explorer vos données avec vos propres mots.  La première partie de cet article explique comment utiliser la fonctionnalité Questions et réponses avec des tableaux de bord dans le service Power BI. La deuxième partie montre ce que Questions et réponses vous permet de faire lorsque vous créez des rapports dans le service Power BI ou dans Power BI Desktop. Pour plus d’informations, consultez l’article [Questions et réponses pour les consommateurs](../consumer/end-user-q-and-a.md). 

[Questions et réponses dans les apps mobiles Power BI](../consumer/mobile/mobile-apps-ios-qna.md) et [Questions et réponses avec Power BI Embedded](../developer/embedded/qanda.md) sont traités dans différents articles. 

La fonctionnalité Questions et réponses est interactive, voire divertissante. Souvent, une question mène à d’autres questions, car les visualisations révèlent des chemins intéressants à suivre. Regardez Amanda illustrer l’utilisation de Questions et réponses pour créer des visualisations, les explorer et les épingler à des tableaux de bord.

<iframe width="560" height="315" src="https://www.youtube.com/embed/qMf7OLJfCz8?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

## <a name="part-1-use-qa-on-a-dashboard-in-the-power-bi-service"></a>Partie 1 : Utiliser Questions et réponses sur un tableau de bord dans le service Power BI

Dans le service Power BI (app.powerbi.com), un tableau de bord contient des vignettes épinglées à partir d’un ou plusieurs jeux de données. Vous pouvez donc poser des questions sur les données contenues dans un de ces jeux de données. Pour afficher les rapports et jeux de données utilisées pour créer le tableau de bord, sélectionnez **Afficher les éléments associés** à partir de la barre de menus.

![Afficher les rapports et les jeux de données associés](media/power-bi-tutorial-q-and-a/power-bi-view-related.png)

La zone de question Questions et réponses située en haut à gauche de votre tableau de bord vous permet de taper votre question dans un langage naturel. Vous ne voyez pas la zone de question ? Consultez [Considérations et résolution des problèmes](../consumer/end-user-q-and-a.md#considerations-and-troubleshooting) dans l’article **Questions et réponses pour les consommateurs**.  La fonctionnalité Questions et réponses reconnaît les mots que vous tapez et déduit l’emplacement (le jeu de données) où se trouve la réponse. Q&R vous aide également à formuler votre question grâce à la saisie semi-automatique, à la reformulation, ainsi qu’à d’autres aides textuelles et visuelles.

![Zone de question de Questions et réponses](media/power-bi-tutorial-q-and-a/powerbi-qna.png)

La réponse à votre question s’affiche comme une visualisation interactive et change quand vous modifiez votre question.

1. Ouvrez un tableau de bord et placez votre curseur dans la zone de questions. En haut à droite, sélectionnez **Nouvelle expérience Questions et réponses activée**.

    ![Power BI - Nouvelle expérience Questions et réponses activée](media/power-bi-tutorial-q-and-a/power-bi-qna-new-experience.png)

1. Avant même que vous commenciez à taper votre question, Q&R affiche dans un nouvel écran des suggestions de formulation de votre question. Vous voyez des groupes de mots et des questions complètes contenant le nom des tables des jeux de données sous-jacents, et vous pouvez même voir des questions complètes si le propriétaire du jeu de données a créé des [questions proposées](service-q-and-a-create-featured-questions.md).

   ![Questions proposées dans Questions et réponses](media/power-bi-tutorial-q-and-a/power-bi-qna-suggested-questions.png)

   Vous pouvez choisir l’une de ces questions comme point de départ et continuer à affiner la question pour trouver la réponse que vous recherchez. Sinon, vous pouvez aussi utiliser un nom de table pour formuler une nouvelle question.

2. Sélectionnez une question dans la liste, ou commencez à taper votre propre question et sélectionnez une suggestion dans la liste déroulante.

   ![Sélectionner une connexion dans la liste](media/power-bi-tutorial-q-and-a/power-bi-qna-select-a-question-how-many-stores.png)

3. Lorsque vous tapez une question, Questions et réponses choisit la meilleure visualisation à afficher comme réponse.

   ![Questions et réponses : nombre de magasins par état](media/power-bi-tutorial-q-and-a/power-bi-qna-how-many-stores-by-state.png)

4. La visualisation change de manière dynamique lorsque vous modifiez la question.

   ![Questions et réponses : nombre de magasins par état sous forme de graphique à barres](media/power-bi-tutorial-q-and-a/power-bi-qna-stores-by-state-bar-chart.png)

1. Quand vous tapez une question, Power BI recherche la meilleure réponse dans les jeux de données ayant une vignette sur ce tableau de bord.  Si toutes les vignettes proviennent du *jeu_de_données_A*, votre réponse proviendra du *jeu_de_données_A*.  S’il existe des vignettes provenant du *jeu_de_données_A* et du *jeu_de_données_B*, Questions et réponses recherche la meilleure réponse dans ces deux jeux de données.

   > [!TIP]
   > Attention : si vous disposez d’une seule vignette provenant du *jeu_de_données_A* et que vous la supprimez de votre tableau de bord, Questions et réponses n’a plus accès au *jeu_de_données_A*.
   >

5. Quand vous êtes satisfait du résultat, épinglez la visualisation à un tableau de bord en sélectionnant l’icône d’épingle dans l’angle supérieur droit. Si le tableau de bord a été partagé avec vous, ou fait partie d’une application, vous ne pouvez pas l’épingler.

   ![Questions et réponses : Épingler le visuel](media/power-bi-tutorial-q-and-a/power-bi-qna-pin-visual.png)

## <a name="part-2-use-qa-in-a-report-in-power-bi-service-or-power-bi-desktop"></a>Partie 2 : Utiliser Questions et réponses dans un rapport dans le service Power BI ou dans Power BI Desktop

Utilisez Questions et réponses pour explorer votre jeu de données et pour ajouter des visualisations au rapport et aux tableaux de bord. Un rapport est basé sur un seul jeu de données et peut être entièrement vide ou contenir des pages avec nombreuses visualisations. Toutefois, ce n’est pas parce qu’un rapport est vide que vous n’avez pas de données à explorer : le jeu de données est lié au rapport et vous n’avez plus qu’à explorer et créer des visualisations.  Pour afficher le jeu de données utilisé pour créer un rapport, ouvrez le rapport en mode Lecture dans le service Power BI et sélectionnez **Afficher les éléments associés** à partir de la barre de menus.

![Afficher les jeux de données associés](media/power-bi-tutorial-q-and-a/power-bi-view-related.png)

Pour utiliser Questions et réponses dans des rapports, vous devez disposer d’autorisations de modification pour le rapport et le jeu de données sous-jacent. Dans l’article [Questions et réponses pour les consommateurs](../consumer/end-user-q-and-a.md), nous appelons cela un scénario de *créateur*. Si vous *consommez* un rapport qui a été partagé avec vous, Questions et réponses ne sera pas disponible.

1. Ouvrez un rapport en mode Édition (service Power BI) ou Rapport (Power BI Desktop) et sélectionnez **Poser une question** dans la barre de menus.

    **Power BI Desktop**    
    ![Sélectionner Poser une question dans Power BI Desktop](media/power-bi-tutorial-q-and-a/power-bi-desktop-question.png)

    **Service**    
    ![Sélectionner Poser une question dans le service Power BI](media/power-bi-tutorial-q-and-a/power-bi-service.png)

2. Une zone de question Questions et réponses s’affiche sur le canevas de rapport. Dans l’exemple ci-dessous, la zone de question s’affiche sur une autre visualisation. C’est un fonctionnement correct, mais il peut être préférable d’ajouter une page vierge au rapport avant de poser une question.

    ![Zone de question de Questions et réponses](media/power-bi-tutorial-q-and-a/power-bi-ask-question.png)

3. Placez votre curseur dans la zone de question. À mesure que vous tapez, Questions et réponses affiche des suggestions de formulation de votre question.

   ![Taper une question dans la zone de question Questions et réponses](media/power-bi-tutorial-q-and-a/power-bi-q-and-a-suggestions.png)

4. Quand vous tapez votre question, Questions et réponses sélectionne la meilleure [visualisation](../visuals/power-bi-visualization-types-for-reports-and-q-and-a.md) pour répondre à la question, et change la visualisation de manière dynamique à mesure que vous modifiez la question.

   ![Questions et réponses crée une visualisation](media/power-bi-tutorial-q-and-a/power-bi-q-and-a-visual.png)

5. Lorsque vous disposez de la visualisation voulue, appuyez sur Entrée. Pour enregistrer la visualisation avec le rapport, sélectionnez **Fichier > Enregistrer**.

6. Interagissez avec la nouvelle visualisation. Peu importe la façon dont vous avez créé la visualisation, les mêmes fonctionnalités de mise en forme et d’interactivité sont disponibles.

   ![Interagir avec la nouvelle visualisation](media/power-bi-tutorial-q-and-a/power-bi-q-and-a-ellipses.png)

   Si vous avez créé la visualisation dans le service Power BI, vous pouvez même [l’épingler à un tableau de bord](service-dashboard-pin-tile-from-q-and-a.md).

## <a name="tell-qa-which-visualization-to-use"></a>Indiquer dans Questions et réponses la visualisation à utiliser
Grâce à Questions et réponses, non seulement vous pouvez demander à vos données de parler d’elles-mêmes, mais vous pouvez également indiquer à Power BI comment afficher la réponse. Il suffit d’ajouter « sous forme de <visualization type> » à la fin de votre question.  Par exemple, « afficher le volume du stock par site sous la forme d’une carte » et « afficher le stock total sous la forme d’une carte ».  Essayez ces requêtes.

## <a name="considerations-and-troubleshooting"></a>Considérations et résolution des problèmes
- Si vous vous êtes connecté à un jeu de données à l’aide d’une connexion active ou d’une passerelle, Questions et réponses doit être [activé pour ce jeu de données](service-q-and-a-direct-query.md).

- Vous avez ouvert un rapport et vous ne voyez pas l’option Questions et réponses. Si vous utilisez le service Power BI, veillez à ouvrir le rapport en mode Édition. Si vous ne pouvez pas ouvrir le mode Édition, cela signifie que vous n’avez pas les autorisations de modification pour ce rapport et que vous ne pouvez pas utiliser Questions et réponses avec celui-ci.

## <a name="next-steps"></a>Étapes suivantes

- [Q&R pour les consommateurs](../consumer/end-user-q-and-a.md)   
- [Conseils de formulation des questions dans Q&R](../consumer/end-user-q-and-a-tips.md)   
- [Préparer un classeur pour Q&R](service-prepare-data-for-q-and-a.md)  
- [Préparer des jeux de données locaux pour Questions et réponses](service-q-and-a-direct-query.md)   
- [Épingler une vignette au tableau de bord à partir de Questions et réponses](service-dashboard-pin-tile-from-q-and-a.md)
