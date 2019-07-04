---
title: Visuels d’indicateur de performance clé (KPI)
description: Créer des visuels d’indicateur de performance clé (KPI) dans Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: xmja6EpqaO0
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 06/24/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 8fa39c7cc57e24f0c19e1a484c0e925bfeec94f7
ms.sourcegitcommit: 1c96b65a03ec0a0612e851dd58c363f4d56bca38
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2019
ms.locfileid: "67389712"
---
# <a name="key-performance-indicator-kpi-visuals"></a>Visuels d’indicateur de performance clé (KPI)

Un indicateur de performance clé (KPI) est un indice visuel qui représente la marge de progression réalisée en vue d’atteindre un objectif mesurable. Pour plus d’informations sur les indicateurs de performance clé (KPI), consultez [Indicateurs de performance clés (KPI) dans PowerPivot](/previous-versions/sql/sql-server-2012/hh272050(v=sql.110)).

Vous pouvez écouter Will qui vous montre comment créer des éléments visuels de métrique uniques : jauges, cartes et indicateurs de performance clés.

<iframe width="560" height="315" src="https://www.youtube.com/embed/xmja6EpqaO0?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

## <a name="when-to-use-a-kpi"></a>Quand utiliser un indicateur de performance clé ?

Les indicateurs de performances clés sont recommandés :

* Pour mesurer la progression. Répond à la question : dans quel domaine suis-je en avance ou en retard ?

* Pour mesurer ce qu’il vous reste à faire pour atteindre un objectif. Répond à la question : suis-je en avance ou en retard ?

## <a name="kpi-requirements"></a>Conditions requises pour les indicateurs de performance clés

Un concepteur base le visuel d’un indicateur de performance clé (KPI) sur une mesure spécifique. L’objectif du KPI est de vous aider à évaluer le statut et la valeur actuelle d’une mesure par rapport à un objectif défini. Un visuel d’indicateur de performance clé requiert une mesure de *base* qui renvoie une valeur, une mesure ou une valeur *cible* et un *seuil* ou un *objectif*.

Un jeu de données d’indicateurs de performances clés doit contenir des valeurs cibles pour un indicateur de performance clé. Si votre jeu de données n’en contient pas, vous pouvez créer des objectifs en ajoutant une feuille Excel contenant des objectifs à votre modèle de données ou fichier PBIX.

## <a name="prerequisites"></a>Conditions préalables

Si vous n’êtes pas inscrit à Power BI, [inscrivez-vous à un essai gratuit](https://app.powerbi.com/signupredirect?pbi_source=web) avant de commencer.

* [Power BI Desktop](https://powerbi.microsoft.com/get-started/) (gratuit)

* [Fichier PBIX Exemple Analyse de la vente au détail](http://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix)

## <a name="how-to-create-a-kpi"></a>Création d’un indicateur de performance clé

Ouvrez le [fichier .PBIX Analyse de la vente au détail](http://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix) dans Power BI Desktop. Vous allez créer un indicateur de performance clé qui mesure votre progression réalisée en vue d’atteindre un objectif de vente.

1. Ouvrez l’**Exemple Analyse de la vente au détail** dans la vue Rapport ![Capture d’écran de l’icône Vue Rapport.](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Sélectionner ![Capture d’écran de l’onglet jaune.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) pour ajouter une nouvelle page.

1. Dans le volet **Champs**, sélectionnez **Sales > This Year Sales (Ventes > Ventes de cette année)** .  Cette valeur servira d’indicateur.

1. Ajoutez **Heure > MoisFiscal**.  Cette valeur représentera la tendance.

1. Dans le coin supérieur droit du visuel, sélectionnez les points de suspension et vérifiez que Power BI a trié les colonnes par ordre croissant selon le champ **MoisFiscal**.

    > [!IMPORTANT]
    > Une fois que vous convertissez la visualisation en indicateur de performance clé, il n’existe **aucune** option de tri. Vous devez désormais trier correctement le visuel.

    ![Capture d’écran du menu Points de suspension développé avec tri croissant et champ MoisFiscal sélectionné.](media/power-bi-visualization-kpi/power-bi-ascending-by-fiscal-month.png)

    Une fois correctement trié, votre visuel ressemblera à ceci :

    ![Capture d’écran du visuel correctement trié.](media/power-bi-visualization-kpi/power-bi-chart.png)

1. Convertissez le visuel en indicateur de performance clé en sélectionnant l’icône **KPI** dans le volet **Visualisation**.

    ![Capture d’écran du volet Visualisation avec l’icône d’indicateur de performance clé (KPI).](media/power-bi-visualization-kpi/power-bi-kpi-template.png)

1. Pour ajouter un objectif, faites glisser **Nombre total d’unités l’année dernière** dans le champ **Objectifs cibles**.

    ![Capture d’écran du visuel KPI terminé et du volet Champs avec les valeurs mentionnées.](media/power-bi-visualization-kpi/power-bi-kpi-done.png)

1. Vous pouvez aussi formater l’indicateur de performance clé en sélectionnant l’icône représentant un rouleau qui ouvre le volet de Mise en forme.

    * **Indicateur** : contrôle les unités d’affichage de l’indicateur et les décimales.

    * **Axe de tendance** : quand il est **activé**, le visuel affiche l’axe de tendance en arrière-plan du visuel de l’indicateur de performance clé.  

    * **Objectifs** : quand il est **activé**, le visuel affiche l’objectif et la distance restante pour atteindre l’objectif, sous forme de pourcentage.

    * **Code couleur > Direction** : certains indicateurs de performances clés sont considérés comme meilleurs pour des valeurs *plus élevées* et d’autres sont considérés comme meilleurs pour des valeurs *plus faibles*. Par exemple, les bénéfices par rapport au temps d’attente. De manière générale, une valeur plus élevée pour les bénéfices est mieux considérée qu’une valeur de temps d’attente élevée. Sélectionnez **Correct vers le haut** et modifiez éventuellement les paramètres de couleur.

Les indicateurs de performance clés sont également faciles à trouver et à installer dans le service Power BI et sur vos appareils mobiles. Vous pouvez ainsi garder à tout moment le contact avec votre entreprise.

## <a name="considerations-and-troubleshooting"></a>Considérations et résolution des problèmes

Si votre indicateur de performance clé ne ressemble pas à celui ci-dessus, peut-être n’avez pas effectué un tri par **MoisFiscal**. Les indicateurs de performance clés ne proposent aucune option de tri. Vous devrez recommencer et trier par **MoisFiscal** *avant* de convertir votre visualisation en indicateur de performance clé.

## <a name="next-steps"></a>Étapes suivantes

* [Trucs et astuces pour les visualisations de carte Power BI](power-bi-map-tips-and-tricks.md)

* [Types de visualisation dans Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)

D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)
