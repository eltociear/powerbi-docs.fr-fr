---
title: "Conseils pour la conception d’un tableau de bord Power BI"
description: "Conseils pour la conception d’un tableau de bord Power BI"
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
ms.date: 03/02/2018
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: 769d669f00c87e6139d8ff2cb8640739d09edf7a
ms.sourcegitcommit: ab5192675729949d89de212acae48dd51294ad78
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2018
---
# <a name="tips-for-designing-a-great-power-bi-dashboard"></a>Conseils pour la conception d’un tableau de bord Power BI
Maintenant que vous avez créé un tableau de bord et ajouté des vignettes, pensez comment vous pourriez rendre votre tableau de bord aussi élégant que fonctionnel. En général, cela consiste à mettre en évidence les informations les plus importantes et à faire en sorte que votre tableau de bord soit clair et non encombré.

Voici quelques astuces.

> [!TIP]
> De nombreux principes de conception de rapports s’appliquent aussi aux tableaux de bord.  Lisez notre livre blanc [Bonnes pratiques de conception de rapports et de visualisations](power-bi-visualization-best-practices.md).
> 
> 

### <a name="consider-your-audience"></a>Prenez en compte votre public
Quelles sont les métriques clés qui les aideront à prendre des décisions ? De quelle façon le tableau de bord sera-t-il utilisé ? Quelles hypothèses culturelles peuvent affecter vos choix en matière de conception ? De quelles informations votre public a-t-il besoin pour réussir ?

N’oubliez pas qu’un tableau de bord fournit une vue d’ensemble, un emplacement unique duquel surveiller l’état actuel des données. Le tableau de bord est basé sur des rapports et des jeux de données sous-jacents qui peuvent contenir de très nombreux détails. Vos lecteurs peuvent explorer vos rapports depuis votre tableau de bord. Par conséquent, ne placez pas de détails sur le tableau de bord, sauf s’il s’agit des informations que vos lecteurs doivent surveiller.

Sur quel type d’appareil le tableau de bord sera-t-il affiché ? S’il s’agit d’un grand écran, vous pouvez ajouter davantage de contenu. S’il doit être lu depuis une tablette, un nombre limité de vignettes le rendra plus lisible.

### <a name="tell-a-story-and-keep-it-to-one-screen"></a>Racontez une histoire et contentez-vous d’un seul écran
Étant donné que les tableaux de bord permettent de lire des informations importantes en un seul coup d’œil, il est préférable que toutes les vignettes se trouvent sur un seul écran. Pouvez-vous éviter l’utilisation d’une barre de défilement dans votre tableau de bord ?

Le tableau de bord est-il encombré ?  Ne gardez que les informations importantes qui peuvent être facilement lues et interprétées.

### <a name="make-use-of-full-screen-mode"></a>Utiliser le mode plein écran
Affichez votre tableau de bord en mode [plein écran](service-fullscreen-mode.md) sans distractions.

### <a name="make-the-most-important-information-biggest"></a>Affichez les informations les plus importantes en grand format
Si le texte et les visualisations de votre tableau de bord ont la même taille, vos lecteurs auront du mal à se concentrer sur ce qui est le plus important. Par exemple, les visualisations de carte sont un bon moyen de mettre en évidence un nombre important :  
![Visualisation de carte](media/service-dashboards-design-tips/pbi_card.png)

N’oubliez pas de préciser le contexte.  

En savoir plus sur la [création d’une vignette avec un seul numéro](power-bi-visualization-card.md).

### <a name="put-the-most-important-information-in-the-upper-corner"></a>Placez les informations les plus importantes au-dessus des autres
La plupart des gens lisent de haut en bas. Placez donc les informations de haut niveau en haut et les informations détaillées en dessous pour suivre le mouvement de lecture de vos utilisateurs (de gauche à droite, de droite à gauche).

### <a name="use-the-right-visualization-for-the-data-and-format-it-for-easy-reading"></a>Utiliser la visualisation qui convient à vos données et la mettre en forme pour en faciliter la lecture
Évitez d’utiliser trop de types de visualisations différents.  Les visualisations doivent représenter une image et être faciles à lire et à interpréter.  Pour certaines données et visualisations, une simple visualisation graphique est suffisante. Toutefois, certaines données peuvent nécessiter une visualisation plus complexe : utilisez des titres, des étiquettes et d’autres personnalisations pour aider le lecteur.  

* [Choisissez des visualisations qui conviennent à vos données](http://blogs.msdn.com/b/microsoft_business_intelligence1/archive/2012/10/08/best-practices-in-data-visualization.aspx). Soyez prudent quand vous utilisez des graphiques qui déforment la réalité, tels que les graphiques 3D. N’oubliez pas qu’il est difficile pour le cerveau humain d’interpréter les formes circulaires. Les graphiques à secteurs, les graphiques en anneau, les jauges et autres types de graphiques circulaires, aussi élégants qu’ils puissent être, ne sont pas recommandés pour les visualisations de données.
* Soyez cohérent avec les échelles des axes, l’ordre des dimensions et les couleurs utilisées pour les valeurs des dimensions dans les graphiques.
* Encodez soigneusement les données quantitatives. Ne dépassez pas trois ou quatre chiffres pour les nombres. Affichez les mesures avec un ou deux chiffres à gauche de la décimale et procédez à une mise à l’échelle pour les milliers et les millions (c’est-à-dire 3,4 millions et non 3 400 000).
* Ne mélangez pas les niveaux de précision et les unités de temps. Assurez-vous que les périodes sont bien comprises.  Ne mettez pas côte à côte un graphique concernant le mois dernier et des graphiques filtrés concernant un certain mois de l’année.
* Ne mélangez pas les grandes et les petites unités de mesures sur une même échelle, telle qu’une ligne ou un graphique à barres.  Par exemple, une mesure en millions et une autre en milliers.  Avec une telle échelle, il serait difficile de voir les différences de la mesure en milliers.  Si vous devez les combiner, choisissez une visualisation qui permet d’utiliser un deuxième axe.
* N’encombrez pas vos graphiques avec des étiquettes de données qui ne sont pas nécessaires. Les valeurs exprimées sous la forme de graphiques à barres sont généralement bien comprises et ne nécessitent pas l’affichage du nombre réel.
* Faites attention à la manière dont les [graphiques sont organisés](power-bi-report-change-sort.md).  Si vous voulez attirer l’attention sur le nombre le plus élevé ou le plus bas, effectuez un tri par mesure.  Si vous voulez que les utilisateurs puissent trouver rapidement une catégorie parmi de nombreuses autres catégories, effectuez un tri par axe.  
* Si vous avez moins de huit catégories, les graphiques en secteurs conviendront le mieux. Étant donné que vous ne pouvez pas comparer des valeurs côte à côte, il est plus difficile de comparer des valeurs dans un graphique à secteurs que dans un graphique à barres ou dans un histogramme. Les graphiques en secteurs conviennent mieux à l’affichage des relations partie-tout qu’à la comparaison de différentes parties. Les graphiques en jauge conviennent parfaitement à l’affichage de l’état actuel dans le contexte d’un objectif.

Pour plus d’informations sur les visualisations, consultez [Types de visualisations dans Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md).  

## <a name="learning-more-about-best-practice-dashboard-design"></a>En savoir plus sur les bonnes pratiques relatives à la création de tableaux de bord
Pour maîtriser l’art de la conception des tableaux de bord, découvrez les principes de base de la Gestalt concernant la perception visuelle et comment communiquer clairement des informations pratiques en contexte. Heureusement, il existe une multitude de ressources qui sont disséminées dans nos blogs. Voici quelques-uns de nos livres préférés :

* *Information Dashboard Design* par Stephen Few  
* *Show Me the Numbers* par Stephen Few  
* *Now You See It* par Stephen Few  
* *Envisioning Information* par Edward Tufte  
* *Advanced Presentations* par Andrew Abela   

## <a name="next-steps"></a>Étapes suivantes
[Tableaux de bord dans Power BI](service-dashboards.md)  
[Power BI – Concepts de base](service-basic-concepts.md)  
D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)

