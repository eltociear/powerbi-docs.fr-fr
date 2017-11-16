---
title: "Exemple Rentabilité des clients pour Power BI : visite guidée"
description: "Exemple Rentabilité des clients pour Power BI : visite guidée"
services: powerbi
documentationcenter: 
author: amandacofsky
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
ms.date: 10/29/2017
ms.author: mihart
ms.openlocfilehash: 9a100b7d13c11a8bd066b72a570f45d0c2bc08be
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2017
---
# <a name="customer-profitability-sample-for-power-bi-take-a-tour"></a>Exemple Rentabilité des clients pour Power BI : visite guidée
Le pack de contenu « Exemple Rentabilité des clients » contient un tableau de bord, un rapport et un jeu de données qui concernent une société qui fabrique des supports marketing. Ce tableau de bord a été créé par une directrice financière désireuse d’afficher des métriques clés sur les 5 responsables de division (encadrement), les produits, les clients et les marges brutes (GM). D’un simple coup d’œil, elle peut identifier les facteurs qui ont un impact sur la rentabilité.

Cet exemple fait partie d’une série d’exemples qui illustre la façon dont vous pouvez utiliser Power BI avec des données, des rapports et des tableaux de bord orientés métier. Il s’agit de données réelles provenant d’obviEnce ([www.obvience.com](http://www.obvience.com/)), présentées de façon anonyme.

Vous pouvez également [télécharger uniquement le jeu de données (classeur Excel) de cet exemple](http://go.microsoft.com/fwlink/?LinkId=529781).  
![](media/sample-customer-profitability/power-bi-dash.png)

## <a name="what-is-our-dashboard-telling-us"></a>Que nous révèle ce tableau de bord ?
### <a name="company-wide-dashboard-tiles"></a>Vignettes de tableau de bord à l’échelle de l’entreprise
Ces vignettes offrent à notre directrice financière une vue d’ensemble des métriques globales de l’entreprise qu’elle juge importantes.  Quand quelque chose l’interpelle, elle peut sélectionner une vignette pour explorer les données.

1. La marge brute de notre société est de 42,5 %.
2. Nous avons 80 clients.
3. Nous vendons 5 produits différents.
4. Nous avons enregistré notre plus faible écart de chiffre d’affaires par rapport aux prévisions en février, suivi de notre plus haut en mars.
5. Notre chiffre d’affaires est réalisé principalement dans les régions Est (« East » et Nord (« North »). La marge brute n’a jamais dépassé les prévisions ; quelques recherches complémentaires devront être entreprises en ce qui concerne 0-ER et MA-0.
6. Le chiffre d’affaires total de l’année est proche des prévisions.

### <a name="manager-specific-dashboard-tiles"></a>Vignettes de tableau de bord des responsables
Ces vignettes fournissent une carte de performance d’équipe. La directrice financière a besoin d’effectuer le suivi des responsables et ces vignettes lui offrent une vision globale des bénéfices, via GM% (ratio de la marge brute). Si la tendance du ratio de marge brute est inattendue pour l’un des responsables, elle peut étudier la question de plus près.

Le ratio de marge brute d’Annelie est le plus bas, mais nous constatons cependant qu’il augmente de façon régulière depuis le mois de mars. Valery, quant à elle, a vu le sien baisser de manière significative. Et Andrew a eu une année en dents de scie. Cliquez sur l’une des vignettes de responsable pour ouvrir le rapport sous-jacent. Le rapport contient 3 pages et s’ouvre à la page « Industry Margin Analysis » (Analyse de la marge sectorielle).

## <a name="explore-the-pages-in-the-report"></a>Exploration des pages du rapport
Notre rapport contient 3 pages :

* La page « Team Scorecard » (Carte de performance de l’équipe) se concentre sur les performances de 5 responsables et sur leur « activité ».
* La page « Industry Margin Analysis » (Analyse de la marge sectorielle) permet d’analyser notre rentabilité par rapport au secteur.
* La page « Executive Scorecard » (Carte de performance de l’exécutif) affiche chacun de nos responsables, selon une mise en page définie pour Cortana.

### <a name="team-scorecard-page"></a>Page « Team Scorecard » (Carte de performance de l’équipe)
![](media/sample-customer-profitability/customer2.png)

Étudions le cas de deux membres de l’équipe et voyons les enseignements que l’on peut en tirer. Dans le segment situé à gauche, sélectionnez « Andrew » pour filtrer la page de rapport uniquement sur les données le concernant.

* Pour un indicateur de performance clé rapide, regardez **l’état du chiffre d’affaires** (Revenue Status) d’Andrew : il est vert. Cela veut dire qu’il est performant.
* Le graphique en aires « Revenue Var % to Budget by Month » (Écart en % du chiffre d’affaires par rapport aux prévisions par mois) montre que si l’on fait abstraction d’une baisse en février, Andrew obtient dans l’ensemble de bons résultats. La région prédominante pour lui est la région Est (« East »). Il a un portefeuille de 49 clients et il vend 5 produits (sur 7). Son ratio de marge brute (« % GM ») n’est ni le plus élevé ni le plus faible.
* Le graphique « RevenueTY and Revenue Var % to Budget by Month » (Chiffre d’affaires annuel et Écart en % du chiffre d’affaires par rapport aux prévisions par mois) fait état d’un bénéficie régulier. Mais si l’on filtre en cliquant sur le carré de la région **Central** (Centre) dans le treemap des régions, on constate qu’Andrew n’a généré du chiffre d’affaires qu’en mars et seulement dans l’Indiana. Est-ce intentionnel ou y a-t-il une autre raison à découvrir ?

Passons maintenant au cas de Valery. Dans le segment, sélectionnez Valery pour filtrer la page de rapport uniquement sur les données qui l’intéressent.  
![](media/sample-customer-profitability/customer3.png)

* Notez que l’indicateur de performance clé **RevenueTY Status**(État du chiffre d’affaires annuel) est au rouge. Une analyse plus fine s’impose.
* De même, l’écart de son chiffre d’affaires dresse un tableau inquiétant. Elle n’a pas atteint ses objectifs de marge.
* Valery a seulement 9 clients, vend seulement 2 produits et travaille presque exclusivement avec des clients de la région Nord (« North »). Cette spécialisation pourrait expliquer les fluctuations importantes observées dans ses métriques.
* En sélectionnant le carré **North** (Nord) dans le treemap, on constate que la marge brute de Valery pour la région Nord cadre est en phase avec sa marge globale.
* En sélectionnant les carrés des autres **régions** , on découvre quelque chose d’intéressant : son ratio de marge brute (GM%) varie de 23 % à 79 % et son chiffre d’affaires, dans toutes les régions à l’exception du Nord, est extrêmement saisonnier.

Poursuivez l’analyse pour découvrir les raisons qui expliquent les mauvais résultats enregistrés dans la zone de Valery. Examinez les régions, les autres divisions et la page suivante du rapport : « Industry Margin Analysis » (Analyse de la marge sectorielle).

### <a name="industry-margin-analysis"></a>Analyse de la marge sectorielle
La page du rapport intitulée « Industry Margin Analysis » propose une autre découpe des données. Elle s’intéresse à la marge brute de l’ensemble des secteurs, ventilée par segment. La directrice financière se sert de cette page pour comparer les métriques de l’entreprise et des divisions à celles des secteurs d’activité afin d’analyser les tendances et la rentabilité. Vous vous demandez peut-être se que fait le graphique en aires « Gross Margin by Month and Executive Name » (Marge brute par mois et par cadre » dans cette page, puisque celle-ci est censée concerner l’équipe. En fait, il permet de filtrer la page par responsable de division.  
![](media/sample-customer-profitability/customer6.png)

Dans quelle mesure la rentabilité varie-t-elle en fonction du secteur d’activité ? Quelle est la répartition des produits et des clients par secteur d’activité ? Sélectionnez un ou plusieurs secteurs d’activité en haut à gauche. (Le premier est CPG, c’est-à-dire le secteur des biens emballés pour la vente au détail) Pour effacer le filtre, sélectionnez l’icône de gomme.

Dans le graphique en bulles, la directrice financière recherche les bulles les plus grandes, car ce sont celles qui contribuent le plus au chiffre d’affaires. Si l’on filtre la page par responsable en cliquant sur leurs noms dans le graphique en aires, il est facile de déterminer l’impact de chacun d’eux par secteur d’activité.

* La zone d’influence d’Andrew s’étend sur plusieurs secteurs d’activité bien différents avec un ratio de marge brute (le plus souvent positif) et un pourcentage d’écart très variables. 
* Le graphique d’Annelie est assez similaire, sauf qu’elle se concentre uniquement sur quelques secteurs d’activités, avec une priorité donnée au secteur Federal et au produit Gladius. 
* Carlos met clairement l’accent sur le segment Services, ce qui lui réussit. Il a fortement amélioré son pourcentage d’écart sur les secteurs High Tech (Hautes technologies) et Industrial (Industrie), qui est nouveau pour lui et où il a nettement dépassé les prévisions. 
* Tina se concentre sur quelques secteurs et c’est elle qui affiche le meilleur ratio de marge brute, mais la petite taille de ses bulles indique que sa contribution au résultat de l’entreprise est minime. 
* Valery, qui a un seul produit dans son portefeuille, travaille seulement dans 5 secteurs d’activité. Bien que son activité soit saisonnière, elle produit toujours une bulle de grande taille, ce qui est le signe qu’elle contribue de manière importante au résultat de l’entreprise. Est-ce le secteur qui explique ses performances négatives ?

### <a name="executive-scorecard"></a>Tableau de bord exécutif
Cette page est mise en forme comme une carte de réponse pour Cortana. Pour plus d’informations, voir [Créer des cartes de réponses pour Cortana](service-cortana-answer-cards.md).

## <a name="dig-into-the-data-by-asking-questions-with-qa"></a>Explorer les données en posant des questions dans Q&R
Pour notre analyse, il serait intéressant d’identifier le secteur d’activité qui profite le plus à Valery en termes de chiffre d’affaires. Utilisons Q&R.

1. Sélectionnez **Power BI** dans la barre de navigation supérieure pour retourner au tableau de bord.
2. Sélectionnez la zone de questions de Q&R en haut du tableau de bord.
   
    ![](media/sample-customer-profitability/customer4.png)
3. Tapez **total revenue by industry for Valery**(chiffre d’affaires total par secteur pour Valery). Comme vous pouvez le constater, la visualisation se met à jour à mesure que vous tapez la question.
   
    ![](media/sample-customer-profitability/customer5.png)
   
   Le secteur le plus porteur pour Valery est celui de la distribution.

### <a name="dig-deeper-by-adding-filters"></a>Aller plus loin en ajoutant des filtres
Penchons-nous sur le secteur *Distribution* .  

1. Revenez au tableau de bord et sélectionnez le graphique en aires qui indique la tendance de marge brute d’Andrew. Le rapport s’ouvre à la page « Industry Margin Analysis » (Analyse de la marge sectorielle).
2. Sans sélectionner aucune visualisation sur la page de rapport, développez le volet Filtres à droite. Le volet Filtres doit afficher uniquement les filtres au niveau page.  
   
   ![](media/sample-customer-profitability/power-bi-filters.png)
3. Recherchez le filtre pour **Industry** ( secteur), puis cliquez sur la flèche pour développer la liste. Ajoutons un filtre de page pour le secteur Distribution. Tout d’abord, annulez toutes les sélections en désactivant la case à cocher **Sélectionner tout**. Ensuite, sélectionnez **Distribution**.  
   
   ![](media/sample-customer-profitability/customer7.png)
4. Le graphique en aires « Gross margin by Month and Executive Name » (Marge brute par mois et par cadre) nous apprend que seules Valery et Tina ont des clients dans ce secteur d’activité et que Valery ne travaille dans ce secteur que de juin à novembre.   
5. Sélectionnez **Tina**, puis **Valery** dans la légende du graphique en aires « Gross margin by Month and Executive » (Marge brute par mois et Exécutif). Remarquez que la contribution de Tina au chiffre d’affaires total par produit (« Total Revenue by Product ») est très faible par rapport à celle de Valery. 
6. Pour afficher le chiffre d’affaires réel, retournez dans le tableau de bord et utilisez la fonctionnalité Q&R pour poser la question : **total revenue for distribution by scenario by executive** (chiffre d’affaires total distribution par scénario par cadre).  
   
   ![](media/sample-customer-profitability/customer8.png)

Nous pouvons procéder de la même manière pour explorer d’autres secteurs, voire ajouter des clients à nos éléments visuels pour comprendre les performances de Valery.

Il s’agit d’un environnement sécurisé à explorer. Vous pouvez toujours choisir de ne pas enregistrer les modifications apportées. Mais si vous les enregistrez, vous pouvez toujours accéder à **Obtenir des données** pour avoir une nouvelle copie de cet exemple.

## <a name="next-steps-connect-to-your-data"></a>Étapes suivantes : Connexion à vos données
Nous espérons qu’à travers cette visite guidée, vous aurez cerné tout l’intérêt des tableaux de bord Power BI, de Q&R et des rapports pour tirer des informations des données client. À présent, c’est votre tour : connectez-vous à vos propres données. Avec Power BI, vous pouvez vous connecter à une grande variété de sources de données. En savoir plus sur [la prise en main de Power BI](service-get-started.md).

[Revenir aux exemples Power BI](sample-datasets.md)  

