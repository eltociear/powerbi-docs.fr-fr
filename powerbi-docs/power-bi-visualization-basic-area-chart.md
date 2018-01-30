---
title: Graphique en aires simple (didacticiel)
description: "Didacticiel : Graphique en aires simple."
services: powerbi
documentationcenter: 
author: mihart
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
ms.date: 01/20/2018
ms.author: mihart
ms.openlocfilehash: c9512be1bcba67eb169a41e3f240fac8e9073a5d
ms.sourcegitcommit: 2ae323fbed440c75847dc55fb3e21e9c744cfba0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2018
---
# <a name="basic-area-chart-tutorial"></a>Graphique en aires simple (didacticiel)
Le graphique en aires simple (également appelé graphique en aires empilées) est basé sur le graphique en courbes. La zone entre l’axe et la ligne est remplie avec des couleurs indiquant le volume. 

Les graphiques en aires mettent en évidence l’ampleur du changement dans le temps et peuvent être utilisés pour attirer l’attention sur la tendance évolutive d’une valeur totale. Par exemple, les données qui représentent des profits dans le temps peuvent être tracées dans un graphique en aires pour mettre l’accent sur le profit total.

![](media/power-bi-visualization-basic-area-chart/powerbi-area-chartnew.png)

## <a name="when-to-use-a-basic-area-chart"></a>Utilisation d’un graphique en aires simple
Les graphiques en aires simples sont conseillés pour :

* afficher et comparer la tendance évolutive des volumes d’une série chronologique ; 
* des séries individuelles représentant un ensemble dénombrable physiquement.

### <a name="prerequisites"></a>Conditions préalables
 - Service Power BI
 - Exemple Analyse de la vente au détail

Pour effectuer la procédure, connectez-vous à Power BI et sélectionnez **Obtenir des données \> Exemples \> Exemple Analyse de la vente au détail > Se connecter**, puis choisissez **Accéder au tableau de bord**. 

## <a name="create-a-basic-area-chart"></a>Créer un graphique en aires simple
 

1. Dans le tableau de bord « Exemple Analyse de la vente au détail », sélectionnez la vignette **Total Stores** (Total magasins) pour ouvrir le rapport « Exemple Analyse de la vente au détail ».
2. Sélectionnez **Modifier le rapport** pour ouvrir le rapport en Mode Edition.
3. Ajoutez une nouvelle page de rapport en sélectionnant l’icône représentant un signe « + » de couleur jaune au bas du rapport.
4. Créez un graphique en aires qui affiche les ventes de l’année actuelle et celles de l’année dernière mois par mois.
   
   a. Dans le volet Champs, sélectionnez **Sales (Ventes) \> Last Year Sales (Ventes de l’année dernière)** et **This Year Sales > Value (Ventes de cette année > Valeur)**.

   ![](media/power-bi-visualization-basic-area-chart/power-bi-bar-chart.png)

   b.  Convertissez le graphique en graphique en aires de base en sélectionnant l’icône Graphique en aires dans le volet Visualisations.

   ![](media/power-bi-visualization-basic-area-chart/convertchart.png)
   
   c.  Sélectionnez **Time\> > Month** (Période > Mois) pour l’ajouter à la ligne **Axe**.   
   ![](media/power-bi-visualization-basic-area-chart/powerbi-area-chartnew.png)
   
   d.  Pour afficher le graphique par mois, sélectionnez les points de suspension (dans le coin supérieur droit de l’élément visuel) et choisissez **Trier par mois**.

## <a name="highlighting-and-cross-filtering"></a>Mise en surbrillance et filtrage croisé
Pour plus d’informations sur le volet Filtres, consultez [Ajouter un filtre à un rapport](power-bi-report-add-filter.md).

Pour mettre en surbrillance une zone particulière de votre graphique, sélectionnez cette zone ou sa bordure supérieure.  Contrairement à d’autres types de visualisation, s’il existe d’autres visualisations sur la même page, la mise en surbrillance d’un graphiques en aires de base n’effectue pas de filtrage croisé des autres visualisations de la page de rapport. Toutefois, les graphiques en aires sont une cible pour le filtrage croisé déclenché par d’autres visualisations sur la page du rapport. Pour plus d’informations, consultez [Interactions avec un élément visuel dans les rapports](service-reports-visual-interactions.md).

## <a name="considerations-and-troubleshooting"></a>Considérations et résolution des problèmes
* Les graphiques en aires simples ne sont pas adaptés pour comparer des valeurs en raison de l’occlusion sur les aires empilées. Power BI utilise la transparence pour indiquer le chevauchement des aires. Toutefois, il fonctionne bien uniquement avec deux ou trois aires différentes. Quand vous devez comparer la tendance de plus de trois valeurs, utilisez plutôt des graphiques en courbes. Pour comparer le volume de plus de trois valeurs, utilisez plutôt un graphique de compartimentage (treemap).

## <a name="next-steps"></a>Étapes suivantes
[Rapports dans Power BI](service-reports.md)  
[Visualisations dans des rapports Power BI](power-bi-report-visualizations.md)  
[Power BI – Concepts de base](service-basic-concepts.md)  
D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)

