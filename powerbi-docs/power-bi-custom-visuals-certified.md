---
title: "Certifier des visualisations Power BI personnalisées"
description: "Découvrez la configuration requise et la procédure à suivre pour soumettre un visuel personnalisé pour certification. Cet article présente également une liste de visuels personnalisés déjà certifiés."
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 11/20/2017
ms.author: mihart
ms.openlocfilehash: 3d51475b300fadc55f33960b03c3adc0031a39b8
ms.sourcegitcommit: 12236d08c27c7ee3fabb7ef9d767e9dee693f8aa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="getting-a-custom-visual-certified"></a>Obtention d’un visuel personnalisé *certifié*
## <a name="what-is-meant-by-certified"></a>Qu’entend-on par *certifié* ?
Un *visuel personnalisé certifié* est un visuel qui satisfait à un ensemble d’exigences de code et qui a passé avec succès des tests de sécurité stricts.  Une fois certifié, un visuel personnalisé peut être [exporté vers PowerPoint](service-publish-to-powerpoint.md) et il apparaît dans les courriers reçus lorsqu’un utilisateur [s’inscrit à des pages de rapport](service-report-subscribe.md).

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
| [Traçage Aster](https://appsource.microsoft.com/product/power-bi-visuals/WA104380759?src=office&tab=Overview) | |
| [Graphique en nœud papillon par MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380838?src=office&tab=Overview) |[Vidéo](https://youtu.be/So5xKMSpVJI) |
| [BciCalendar (Beyondsoft Calendar)](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381096?src=office&tab=Overview)  | |
| [Graphique en boîte à moustaches](https://appsource.microsoft.com/product/power-bi-visuals/WA104380831?src=office&tab=Overview) | |
| [Bullet Chart](https://store.office.com/app.aspx?assetid=WA104380755) |[Vidéo 1](https://youtu.be/AOlsFYkfkcw)   [Vidéo 2](https://youtu.be/AQvd2FhRyCI) |
| [Graphique à puces par OKViz](https://store.office.com/bullet-chart-by-okviz-WA104380953.aspx) |[Vidéo](https://youtu.be/mtvUNl9bMjA) |
| [Calendar par Tallan](https://appsource.microsoft.com/product/power-bi-visuals/WA104381146?src=office&tab=Overview) | |
| [Segment Chiclet](https://store.office.com/chiclet-slicer-WA104380756.aspx) |[Vidéo](https://youtu.be/iYOkJ1APueY) |
| [Graphique de grille harmonique](https://appsource.microsoft.com/product/power-bi-visuals/WA104380761?src=office&tab=Overview) |[Vidéo](https://youtu.be/AQvd2FhRyCI) |
| [Jauge circulaire par MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380837?tab=Overview) | |
| [Jauge cylindrique](https://appsource.microsoft.com/product/power-bi-visuals/WA104380874) | |
| [Jauge radiale](https://appsource.microsoft.com/product/power-bi-visuals/WA104381184) |[Vidéo](https://youtu.be/AOlsFYkfkcw) |
| [Graphique en anneau par MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380824?tab=Overview) |[Vidéo](https://youtu.be/pDToHDFHnq8) |
| [Traçage de points par OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104381101?src=office&tab=Overview) |[Vidéo](https://youtu.be/4lskRgcpFJY) |
| [Exploration dans le graphique en anneau par ZoomCharts](https://appsource.microsoft.com/product/power-bi-visuals/WA104380858) | |
| [Dual KPI](https://store.office.com/dual-kpi-WA104380774.aspx) |[Vidéo](https://youtu.be/821o0-eVBXo?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x) |
| [Enlighten Aquarium](https://appsource.microsoft.com/product/power-bi-visuals/WA104381112?src=office&tab=Overview) | |
| Enlighten World Flags - bientôt disponible | |
| Enlighten Stack Shuffle - bientôt disponible | |
| [Diagramme de Gantt](https://store.office.com/gantt-WA104380765.aspx) |[Vidéo](https://youtu.be/qJ7s_KrGiUU) |
| [Histogramme](https://store.office.com/histogram-chart-WA104380776.aspx) | |
| [Entonnoir horizontal](https://appsource.microsoft.com/product/power-bi-visuals/WA104380846) |[Vidéo](https://youtu.be/SudZei68PPo) |
| [Indicateur d’indicateur de performance clé](https://store.office.com/kpi-indicator-WA104380832.aspx) | |
| [Jauge linéaire par MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380821?src=office&tab=Overview) |[Vidéo](https://youtu.be/AOlsFYkfkcw) |
| [Graphique Mekko](https://appsource.microsoft.com/product/power-bi-visuals/WA104380785?src=office&tab=Overview)  | [Vidéo](https://youtu.be/90FLCKpgicA)|
| [Axe de lecture (segment dynamique)](https://store.office.com/play-axis-dynamic-slicer-WA104380981.aspx) | |
| [Power KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104381083) |[Vidéo](https://youtu.be/IvfIP3E6-1Q) |
| [Graphique en radar](https://store.office.com/radar-chart-WA104380771.aspx) | |
| [Graphique en anneau par MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380824?src=office&tab=Overview) | [Vidéo](https://youtu.be/pDToHDFHnq8)|
| [Graphique de Sankey](https://store.office.com/app.aspx?assetid=WA104380777.aspx) |[Vidéo](https://youtu.be/WWP9wVUHGaA) |
| [Barre de défilement](https://store.office.com/scroller-WA104381018.aspx) |[Vidéo](https://youtu.be/uhRFQF2cGSY) |
| [Filtre dynamique par SQLBI](https://store.office.com/smart-filter-by-okviz-WA104380859.aspx) |[Vidéo](https://youtu.be/gcJsDDRQq28) |
| [Graphique sparkline par OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380910?src=office&tab=Overview) |[Vidéo](https://youtu.be/0m3Vnvso9tY) |
| [Graphique en rayons de soleil](https://appsource.microsoft.com/product/power-bi-visuals/WA104380767?src=office&tab=Overview) | |
| [Tachymètre](https://store.office.com/tachometer-WA104380937.aspx?) |[Vidéo](https://www.youtube.com/watch?v=C3OXdETbS9o) |
| [Thermomètre](https://appsource.microsoft.com/product/power-bi-visuals/WA104380847?src=office&tab=Overview) | [Vidéo](https://youtu.be/SPX9mgrAdBc)|
| [Décomposition de série temporelle](https://appsource.microsoft.com/product/power-bi-visuals/WA104380897) | |
| [Carte thermique Table](https://store.office.com/table-heatmap-WA104380818.aspx) | |
| [Wrapper de texte](https://appsource.microsoft.com/product/power-bi-visuals/WA104380826) | |
| [Timeline slicer](https://store.office.com/timeline-slicer-WA104380786.aspx) |[Vidéo](https://youtu.be/ozMtZ4_NZ10) |
| [Graphique en tornade](https://store.office.com/tornado-chart-WA104380768.aspx) |[Vidéo](https://youtu.be/AQvd2FhRyCI) |
| [Graphique en gaufre](https://appsource.microsoft.com/product/power-bi-visuals/WA104381049?src=office&tab=Overview) |[Vidéo](https://youtu.be/1vRqYUsm3Vk) |
| [Nuage de mots](https://store.office.com/word-cloud-WA104380752.aspx?) |[Vidéo](https://www.youtube.com/watch?v=AblTenl9fqo) |

## <a name="next-steps"></a>Étapes suivantes
[Prise en main des outils de développement de visuels personnalisés (version préliminaire)](service-custom-visuals-getting-started-with-developer-tools.md)      
[Sélection de visuels personnalisés de Microsoft sur YouTube](https://www.youtube.com/playlist?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x)  
[Visualisations dans Power BI](power-bi-report-visualizations.md)  
[Visualisations personnalisées dans Power BI](power-bi-custom-visuals.md)  
[Publier des visuels personnalisés dans Microsoft AppSource](developer/office-store.md)  
D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)

