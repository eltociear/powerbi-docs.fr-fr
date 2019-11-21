---
title: Créer un visuel avec Questions et réponses Power BI
description: Découvrez comment créer un visuel avec Questions et réponses dans le service Power BI en utilisant l’exemple Analyse de la vente au détail
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/13/2019
ms.author: maggies
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: 817ce82b94817530854d85c7dbcca17a313fc438
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73874466"
---
# <a name="create-a-visual-with-power-bi-qa"></a>Créer un visuel avec Questions et réponses Power BI

Il est parfois plus rapide d’obtenir des informations à partir de vos données en posant une question dans un langage naturel.  Dans cet article, nous examinons deux façons de créer la même visualisation : d’abord en posant une question avec Questions et réponses et ensuite en la créant dans un rapport. Nous utilisons le service Power BI, pour créer le visuel dans le rapport, mais le processus est presque identique si vous utilisez Power BI Desktop.

![Graphique Power BI rempli](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna-create-visual.png)

Pour effectuer la procédure, vous devez utiliser un rapport que vous pouvez modifier. Nous allons donc utiliser un des exemples disponibles avec Power BI.

## <a name="create-a-visual-with-qa"></a>Créer un visuel avec les Questions et réponses

Comment créer ce graphique en courbes avec Questions et réponses ?

1. Dans votre espace de travail Power BI, sélectionnez **Obtenir des données** \> **Exemples** \> **Retail Analysis Sample (Exemple Analyse de la vente au détail)**  > **Connexion**.

1. Ouvrez le tableau de bord de l’exemple Analyse de la vente au détail et placez votre curseur dans la zone Questions et réponses, sur **Poser une question sur vos données**.

    ![Placer le curseur dans la zone Questions et réponses](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna-cursor-in-qna-box.png)

2. Dans la zone Questions et réponses, tapez quelque chose de similaire à cette question :
   
    **this year sales and last year sales by month as area chart**
   
    Quand vous tapez votre question, Q&R sélectionne la meilleure visualisation pour répondre à la question, et change la visualisation de manière dynamique à mesure que vous complétez la question. De plus, Q&R vous aide à formuler votre question en proposant des suggestions, des correspondances de saisie semi-automatique et des corrections orthographiques. Questions et réponses recommande une petite modification de la formulation : « this year sales and last year sales by *time month* as area chart ».  

    ![Formulation corrigée par Questions et réponses](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna-corrected-create-filled-chart.png)

4. Sélectionnez la phrase pour accepter la suggestion. 
   
   Quand vous avez fini de taper votre question, le résultat est identique au graphique que vous voyez dans le rapport.
   
   ![Graphique en aires rempli par Questions et réponses](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna-create-filled-chart.png)

4. Pour épingler le graphique à votre tableau de bord, sélectionnez l’icône d’épingle. ![Icône Épingler](media/power-bi-visualization-introduction-to-q-and-a/pinnooutline.png) dans le coin supérieur droit.

## <a name="create-a-visual-in-the-report-editor"></a>Créer un visuel dans l’éditeur de rapport

1. Revenez au tableau de bord Exemple Analyse de la vente au détail.
   
2. Le tableau de bord contient la même vignette de graphique en aires pour « Last Year Sales and This Year Sales ».  Sélectionnez cette vignette. Ne sélectionnez pas la vignette que vous avez créée avec Questions et réponses. Cette sélection ouvre Questions et réponses. La vignette du graphique en aires d’origine a été créée dans un rapport : le rapport s’ouvre donc sur la page qui contient cette visualisation.

    ![Tableau de bord Exemple Analyse de la vente au détail](media/power-bi-visualization-introduction-to-q-and-a/power-bi-dashboard.png)

1. Ouvrez le rapport en Mode Edition en sélectionnant **Modifier le rapport**.  Si vous n’êtes pas propriétaire d’un rapport, vous ne pouvez pas ouvrir le rapport en mode Édition.
   
    ![Bouton Modifier le rapport](media/power-bi-visualization-introduction-to-q-and-a/power-bi-edit-report.png)
4. Sélectionnez le graphique en aires et vérifiez les paramètres dans le volet **Champs** .  Pour générer ce graphique, le créateur du rapport a sélectionné ces trois valeurs (**Last Year Sales** et **This Year Sales > Valeur** dans la table **Sales**, et **FiscalMonth** dans la table **Time**) et les a organisées dans **Axes** et dans **Valeurs**.
   
    ![volet Visualisations](media/power-bi-visualization-introduction-to-q-and-a/gnatutorial_3-new.png)

    Vous voyez qu’elles ont abouti au même visuel. La création avec cette méthode n’était pas trop compliquée. Mais sa création avec Questions et réponses a été plus facile !

## <a name="next-steps"></a>Étapes suivantes

- [Utiliser Q&R dans des tableaux de bord et des rapports](power-bi-tutorial-q-and-a.md)  
- [Q&R pour les consommateurs](consumer/end-user-q-and-a.md)
- [Optimiser vos données avec Q&R dans Power BI](service-prepare-data-for-q-and-a.md)

D’autres questions ? [Posez vos questions à la communauté Power BI](https://community.powerbi.com/)

