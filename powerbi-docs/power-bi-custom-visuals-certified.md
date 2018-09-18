---
title: Certifier des visualisations Power BI personnalisées
description: Découvrez la configuration requise et la procédure à suivre pour soumettre un visuel personnalisé pour certification. Cet article présente également une liste de visuels personnalisés déjà certifiés.
author: mihart
manager: kfile
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.component: powerbi-developer
ms.topic: conceptual
ms.date: 02/13/2018
ms.author: mihart
ms.openlocfilehash: 4676b31a117573d1d69b5947ec2380c4abf29405
ms.sourcegitcommit: 67336b077668ab332e04fa670b0e9afd0a0c6489
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44726866"
---
# <a name="getting-a-custom-visual-certified"></a>Obtention d’un visuel personnalisé *certifié*
## <a name="what-is-meant-by-certified"></a>Qu’entend-on par *certifié* ?
Un *visuel personnalisé certifié* est un visuel qui satisfait à un ensemble d’exigences de code et qui a passé avec succès des tests de sécurité stricts.  Une fois certifié, un visuel personnalisé peut être [exporté vers PowerPoint](service-publish-to-powerpoint.md) et il apparaît dans les courriers reçus lorsqu’un utilisateur [s’inscrit à des pages de rapport](service-report-subscribe.md). Bien entendu, vous pouvez aussi l’utiliser comme [visuel personnalisé standard](power-bi-custom-visuals.md), l’ajouter au service Power BI et aux rapports Power BI Desktop, et l’afficher dans Power BI Mobile et Embedded.

Vous êtes un développeur web et souhaitez créer vos propres visualisations et les ajouter à [Microsoft AppSource](https://appsource.microsoft.com) ? Pour savoir comment procéder, consultez [Prise en main des outils de développement](service-custom-visuals-getting-started-with-developer-tools.md).


## <a name="certification-requirements"></a>Critères de certification
* Approuvé(s) par Microsoft AppSource    
* Le visuel personnalisé est écrit avec une API version 1.2 ou supérieure.    
* Un référentiel de code est disponible pour examen (par exemple, code de l’élément visuel accessible via GitHub).    
* Le visuel utilise uniquement des composants OSS publics consultables.    
* Le visuel n’accède pas à des services ou ressources externes.    

> **CONSEIL** : nous vous recommandons d’utiliser EsLint avec un ensemble des règles de sécurité par défaut afin de pré-valider votre code avant de le soumettre.
> 
> 

## <a name="process-for-submitting-a-custom-visual-for-certification"></a>Processus de soumission d’un visuel personnalisé en vue de sa certification
Pour soumettre un visuel personnalisé en vue de sa certification :

1. Envoyez un e-mail au support technique des visuels personnalisés de Power BI (pbicvsupport@microsoft.com). Dans l’e-mail, incluez les informations suivantes :    

   * Titre : Demande de certification de visuel    
   * Lien vers le dépôt GitHub où est hébergé le code source du visuel    
   * Respect de la configuration requise (voir ci-dessus)    
   * Révision réussie du code et de la sécurité    

2. L’équipe de Microsoft en charge des visuels personnalisés vous avertit après que votre visuel personnalisé a été certifié et ajouté à la liste certifiée (voir ci-dessous) ou rejeté avec un rapport des problèmes à résoudre. Il incombe au développeur d’ouvrir et de maintenir ouverte une ligne de communication avec Microsoft, ainsi que de mettre à jour ses visuels certifiés au besoin.

## <a name="removal-of-power-bi-certified-custom-visuals"></a>Suppression de visuels personnalisés certifiés Power BI
Microsoft peut, à sa discrétion, supprimer un visuel de la liste certifiée.  

## <a name="list-of-custom-visuals-that-have-been-certified"></a>Liste de visuels personnalisés certifiés

| Lien vers AppSource | Lien vers la vidéo |
| --- | --- |
| [Traçage Aster](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380759) | |
| [Calendrier Beyondsoft](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381096) | |
| [Bowtie Chart par MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380838) | [Vidéo](https://youtu.be/So5xKMSpVJI) |
| [Graphique en boîte à moustaches](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380831) | |
| [Graphique en boîte à moustaches par MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381351) | [Vidéo](https://youtu.be/JoHaFLfhXdo) |
| [Brick Chart par MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380836) | [Vidéo](https://youtu.be/hA3DOsvn2xY) |
| [Bubble Chart par Akvelon](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381340) | |
| [Bullet Chart](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380755) | [Vidéo](https://youtu.be/AOlsFYkfkcw) |
| [Graphique à puces par OKViz](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380953) | [Vidéo](https://youtu.be/mtvUNl9bMjA) |
| [Calendar par Tallan](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381146) | |
| [Candlestick par OKViz](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380952) | [Vidéo](https://youtu.be/nT_18gyRxPo) |
| [Carte avec états par OKViz](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380967) | |
| [Segment Chiclet](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380756) | |
| [Chord](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380761) | [Vidéo](https://youtu.be/AQvd2FhRyCI) |
| [Circular Gauge par MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380837) | [Vidéo](https://youtu.be/9NHXALkBXuY) |
| [Carte du cluster](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380806) | |
| [Cylindrical Gauge par MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380874) | [Vidéo](https://youtu.be/DgdoWi7Gcxo) |
| [Jauge radiale](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381184) | |
| [Graphique à points](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380760) | |
| [Traçage de points par OKViz](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380949) | [Vidéo](https://youtu.be/By16pX9KT40) |
| [Drilldown Cartogram](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381045) | |
| [Drilldown Choropleth](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381044) | |
| [Graphique d’analyse en colonnes](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380857) | [Vidéo](https://youtu.be/lBy2gQQ5YsQ) |
| [Graphique d’analyse en colonnes pour les données temporelles](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380881) | [Vidéo](https://youtu.be/T_mRou18vx0) |
| [Graphique d’analyse en anneau](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380858) | [Vidéo](https://youtu.be/AUVFrSHmPeo) |
| [Dual KPI](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380774) | |
| [Dynamic Tooltip par MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380983) | [Vidéo](https://youtu.be/Z-tl97BpEr0) |
| [Enhanced Scatter](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380762) | [Vidéo](https://youtu.be/xCfM0cjM4do) |
| [Enlighten Aquarium](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381112) | |
| [Enlighten Slicer](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380960) | |
| [Enlighten Stack Shuffle](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380849) | |
| [Enlighten Waffle Chart](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380850) | |
| [Graphique Force-Directed](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380764) | [Vidéo](https://youtu.be/YsTa7uyJ4sg) |
| [Funnel with Source par MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381334) | [Vidéo](https://youtu.be/R_EcimsLI8U) |
| [Diagramme de Gantt](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380765) | [Vidéo](https://youtu.be/qJ7s_KrGiUU) |
| [Diagramme de Gantt par MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381364) | [Vidéo](https://youtu.be/vJLV9JRCpI8) |
| [Globe Data Bars](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381344) | |
| [Grid par MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380825) | [Vidéo](https://youtu.be/VOPoDJgZfOY) |
| [Hierarchy Chart par Akvelon](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381333) | [Vidéo](https://youtu.be/0ZGzJaq_KT4) |
| [Histogramme](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380776) | |
| [Histogramme avec points par MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381032) | [Vidéo](https://youtu.be/-ILF--wExrw) |
| [Horizontal Funnel par MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380846) | [Vidéo](https://youtu.be/SudZei68PPo) |
| [Image par CloudScope](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381297) | |
| [Image Grid](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381355) | |
| [Infographic Designer](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380898) | |
| [Graphique KPI par Akvelon](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381432) | |
| [Colonne KPI par MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380996) | [Vidéo](https://youtu.be/rU0xoOlIq1U) |
| [Grille KPI par MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380947) | [Vidéo](https://youtu.be/dM4PvZh71V0) |
| [Indicateur d’indicateur de performance clé](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380832) | |
| [KPI Ticker par MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380946) | [Vidéo](https://youtu.be/cudG4gsZ2V8) |
| [Linear Gauge par MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380821) | [Vidéo](https://youtu.be/7_jFaM30dkc) |
| [LineDot Chart](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380766) | |
| [Graphique Mekko](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380785) | [Vidéo](https://youtu.be/90FLCKpgicA) |
| [Vue d’ensemble par CloudScope](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381477) | |
| [Axe de lecture (segment dynamique)](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380981) | |
| [Power KPI](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381083) | [Vidéo](https://youtu.be/IvfIP3E6-1Q) |
| [Matrice des indicateurs de performance clé Power](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381299) | [Vidéo](https://youtu.be/1enze8pcGzY) |
| [Graphique de pulsations](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381006) | [Vidéo](https://youtu.be/DQWdcQtjDVw) |
| [Quadrant Chart par MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381011) | [Vidéo](https://youtu.be/ppBnyhqWNC0) |
| [Graphique en radar](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380771) | |
| [Ring Chart par MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380824) | [Vidéo](https://youtu.be/pDToHDFHnq8) |
| [Rotating Chart par MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381007) | [Vidéo](https://youtu.be/d5xBCMmb3hU) |
| [Graphique de Sankey](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380777) | [Vidéo](https://youtu.be/WWP9wVUHGaA) |
| [Barre de défilement](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381018) | |
| [Filtre dynamique par OKViz](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380859) | [Vidéo](https://youtu.be/gcJsDDRQq28) |
| [Graphique sparkline par OKViz](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380910) | [Vidéo](https://youtu.be/0m3Vnvso9tY) |
| [Stream Graph](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380772) | |
| [Graphique en rayons de soleil](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380767) | |
| [Tableau synoptique par OKViz](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380873) | |
| [Carte thermique Table](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380818) | |
| [Tachymètre](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380937) | [Vidéo](https://youtu.be/C3OXdETbS9o) |
| [Filtre de texte](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381309) | |
| [Text Wrapper par MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380826) | |
| [Thermometer by MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380847) | [Vidéo](https://youtu.be/SPX9mgrAdBc) |
| [Time Brush Slicer](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380798) | |
| [Timeline Slicer](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380786) | [Vidéo](https://youtu.be/ozMtZ4_NZ10) |
| [Timeline par CloudScope](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381427) | [Vidéo](https://youtu.be/szNi9YgXFJc) |
| [Graphique en tornade](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380768) | [Vidéo](https://www.youtube.com/watch?v=AQvd2FhRyCI) |
| [Trading Chart par MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380823) | [Vidéo](https://youtu.be/xhTR6y6J9Ko) |
| [Ultimate Variance](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381140) | [Vidéo](https://youtu.be/pDYF8iZxERs) |
| [Ultimate Waterfall](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380956) | [Vidéo](https://youtu.be/0BZsVCQdEkc) |
| [User List par CloudScope](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381426) | |
| [Graphique en gaufre](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381049) | [Vidéo](https://youtu.be/1vRqYUsm3Vk) |
| [Nuage de mots](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380752) | [Vidéo](https://youtu.be/AblTenl9fqo) |

## <a name="next-steps"></a>Étapes suivantes
[Prise en main des outils de développement de visuels personnalisés (version préliminaire)](service-custom-visuals-getting-started-with-developer-tools.md)      
[Sélection de visuels personnalisés de Microsoft sur YouTube](https://www.youtube.com/playlist?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x)  
[Visualisations dans Power BI](visuals/power-bi-report-visualizations.md)  
[Visualisations personnalisées dans Power BI](power-bi-custom-visuals.md)  
[Publier des visuels personnalisés dans Microsoft AppSource](developer/office-store.md)  
D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)

