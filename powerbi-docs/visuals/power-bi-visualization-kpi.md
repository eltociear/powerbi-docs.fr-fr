---
title: Éléments visuels des indicateurs de performance clés
description: Créer des visuels des indicateurs de performance clés dans Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: xmja6EpqaO0
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: tutorial
ms.date: 09/24/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 0492390ae47c8d5aa0930a063370712c80d61de2
ms.sourcegitcommit: e17fc3816d6ae403414cf5357afbf6a492822ab8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2018
ms.locfileid: "52829639"
---
# <a name="kpi-visuals"></a>Éléments visuels des indicateurs de performance clés
Un indicateur de performance clé (KPI) est un indice visuel qui représente la marge de progression réalisée en vue d’atteindre un objectif mesurable. Pour plus d’informations sur les indicateurs de performances clés, consultez [Microsoft Developer Network](https://msdn.microsoft.com/library/hh272050).

Si vous n’êtes pas inscrit à Power BI, [inscrivez-vous à un essai gratuit](https://app.powerbi.com/signupredirect?pbi_source=web) avant de commencer.

## <a name="prerequisites"></a>Conditions préalables
* [Power BI Desktop (gratuit)](https://powerbi.microsoft.com/en-us/get-started/)
* [Fichier PBIX Exemple Analyse de la vente au détail](http://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix)

## <a name="when-to-use-a-kpi"></a>Quand utiliser un indicateur de performance clé ?
Les indicateurs de performances clés sont recommandés :

* pour mesurer la progression (dans quel domaine suis-je en avance ou en retard ?)
* pour mesurer ce qu’il vous reste à faire pour atteindre un objectif (suis-je en avance ou en retard ?)   

## <a name="kpi-requirements"></a>Conditions requises pour les indicateurs de performance clés
Un indicateur de performance clé (KPI) se base sur une mesure spécifique et est conçu pour vous aider à évaluer le statut et la valeur actuelle d’une mesure par rapport à un objectif défini. Ainsi, un visuel d’indicateur de performance clé requiert une mesure de *base* qui renvoie une valeur, une mesure ou une valeur *cible* et un *seuil* ou un *objectif*.

Actuellement, un jeu de données d’indicateurs de performances clés doit contenir des valeurs cibles pour un indicateur de performance clé. Si votre jeu de données n’en contient pas, vous pouvez créer des objectifs en ajoutant une feuille Excel contenant des objectifs à votre modèle de données ou fichier PBIX.


## <a name="how-to-create-a-kpi"></a>Création d’un indicateur de performance clé
Ouvrez le [fichier .PBIX Analyse de la vente au détail](http://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix) dans Power BI Desktop. Nous allons créer un indicateur de performance clé qui mesure la progression réalisée en vue d’atteindre un objectif de vente.

Vous pouvez également écouter Will qui vous montre comment créer des éléments visuels de métrique uniques : jauges, cartes et indicateurs de performance clés.

<iframe width="560" height="315" src="https://www.youtube.com/embed/xmja6EpqaO0?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

1. Ouvrez le rapport en mode Rapport et sélectionnez l’onglet jaune pour ajouter une nouvelle page.    
2. Dans le volet Champs, sélectionnez **Sales > This Year Sales** (Ventes > Ventes de cette année).  Il s’agit de l’indicateur.
3. Ajoutez **Heure > MoisFiscal**.  Ceci représente la tendance.
4. IMPORTANT : triez le graphique par **MoisFiscal**. Une fois que vous convertissez la visualisation en indicateur de performance clé, il n’existe aucune option de tri.

    ![](media/power-bi-visualization-kpi/power-bi-chart.png)
5. Convertissez l’élément visuel en indicateur de performance clé en sélectionnant l’icône correspondante dans le volet de visualisation.
   
    ![](media/power-bi-visualization-kpi/power-bi-kpi-template.png)
6. Ajoutez un objectif. Ajoutez les ventes de l’année précédente comme objectif. Faites glisser **Nombre total d’unités l’année dernière** dans le champ **Objectifs cibles**.
   
    ![](media/power-bi-visualization-kpi/power-bi-kpi-done.png)
7. Vous pouvez aussi formater l’indicateur de performance clé en sélectionnant l’icône représentant un rouleau qui ouvre le volet de Mise en forme.
   
   * **Indicateur** : contrôle les unités d’affichage de l’indicateur et les décimales.
   * **Axe de tendance** : quand il est **activé**, l’axe de tendance est affiché en arrière-plan de l’élément visuel de l’indicateur de performance clé.  
   * **Objectifs** : quand il est **activé**, l’élément visuel affiche l’objectif et la distance restante pour atteindre l’objectif, sous forme de pourcentage.
   * **Code couleur > Direction** : certains indicateurs de performances clés sont considérés comme *meilleurs* pour des valeurs plus élevées et d’autres sont considérés comme *meilleurs* pour des valeurs plus faibles. Par exemple, les bénéfices par rapport au temps d’attente. De manière générale, une valeur plus élevée pour les bénéfices est mieux considérée qu’une valeur de temps d’attente élevée. Sélectionnez **une valeur élevée est meilleure** et modifiez éventuellement les paramètres de couleur.


Les indicateurs de performance clés sont également disponibles dans le service Power BI et sur vos appareils mobiles, ce qui vous permet de toujours rester connecté.

## <a name="considerations-and-troubleshooting"></a>Considérations et résolution des problèmes
* Si votre indicateur de performance clé ne ressemble pas à celui ci-dessus, vous devez peut-être effectuer un tri par MoisFiscal. Étant donné que les indicateurs de performance clés n’ont pas d’option de tri, vous devez trier par MoisFiscal *avant* de convertir votre visualisation en indicateur de performance clé.

## <a name="next-steps"></a>Étapes suivantes

[Cartes de base dans Power BI](power-bi-map-tips-and-tricks.md)

[Types de visualisation dans Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)