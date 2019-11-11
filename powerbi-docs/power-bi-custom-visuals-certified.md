---
title: Visuels Power BI de Power BI certifiés
description: Découvrez la configuration requise et la procédure à suivre pour soumettre un visuel personnalisé pour certification. Cet article présente également une liste de visuels Power BI déjà certifiés.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 05/9/2019
ms.openlocfilehash: 8b119f0f3b0dfb67dc2f9cb1dfd6f19d72593d66
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73874578"
---
# <a name="get-a-power-bi-visual-certified"></a>Obtenir un visuel Power BI certifié

## <a name="what-are-_certified_-power-bi-visuals"></a>Qu’est-ce que les visuels Power BI **_certifiés_**  ?

Les visuels Power BI certifiés sont des visuels de la **Place de marché** qui respectent certaines conditions de **code spécifié**, celles-ci ayant été testées et approuvées par l’**équipe Microsoft Power BI**. Un visuel personnalisé certifié offre davantage de fonctionnalités. Vous pouvez, par exemple, [exporter vers PowerPoint](consumer/end-user-powerpoint.md) et afficher le visuel dans les e-mails reçus quand un utilisateur [s’abonne aux pages du rapport](consumer/end-user-subscribe.md).

Les **visuels Power BI certifiés** sont utilisés comme des [visuels Power BI standard](power-bi-custom-visuals.md). Vous pouvez ajouter des visuels Power BI certifiés au **service Power BI** ou à un **rapport Power BI Desktop**, et les afficher avec **Power BI Mobile** et **Power BI Embedded**.

Les tests effectués sont conçus pour vérifier que le visuel n’a pas accès à des services ni à des ressources externes. **Microsoft** n’étant *pas* l’auteur des visuels Power BI de tiers, nous conseillons aux clients de contacter directement leur auteur pour vérifier leur fonctionnement.

Le processus de certification est un processus facultatif, et il appartient aux développeurs de décider s’ils souhaitent que leur visuel soit certifié dans la Place de marché.  

Un **visuel Power BI non certifié** ne présente pas nécessairement des risques pour la sécurité. Certains visuels ne sont pas certifiés car ils ne sont pas conformes à un ou plusieurs [critères de certification](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements). Citons par exemple les visuels de carte qui se connectent à un service externe ou ceux qui utilisent des bibliothèques commerciales.

Vous êtes développeur web et souhaitez créer vos propres visualisations à ajouter à  **[Microsoft AppSource](https://appsource.microsoft.com)**  ? Pour la marche à suivre, consultez  **[Développer un visuel personnalisé Power BI](developer/visuals/custom-visual-develop-tutorial.md)** .

## <a name="removal-of-power-bi-certified-power-bi-visuals"></a>Suppression de visuels Power BI certifiés de Power BI

Microsoft peut supprimer un visuel de la [liste certifiée](#list-of-power-bi-visuals-that-have-been-certified) à sa discrétion.

## <a name="getting-a-custom-visualcertified"></a>Certification d’un visuel personnalisé

### <a name="certification-requirements"></a>Critères de certification

Pour faire [certifier](#get-a-power-bi-visual-certified) un visuel personnalisé, vérifiez qu’il respecte les critères ci-dessous :  

* Approuvé par Microsoft AppSource. Votre visuel personnalisé doit figurer dans notre [Place de marché](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals).
* Le visuel personnalisé est écrit avec une **API v2.5** ou ultérieure.
* Dépôt de code disponible pour revue par l’équipe Power BI (par exemple, code source en JavaScript ou TypeScript accessible dans un format lisible par le biais de GitHub).

    >[!Note]
    > Vous n’êtes pas obligé de partager publiquement votre code dans Github.
* Configuration requise pour le référentiel de code :
   * Doit inclure le jeu de fichiers minimal requis :
      * .gitignore
      * capabilities.json
      * pbiviz.json
      * package.json
      * package-lock.json
      * tsconfig.json
   * Ne doit pas inclure le dossier node_modules (ajoutez node_modules au fichier .gitingore)
   * La commande **npm install** ne doit retourner aucune erreur.
   * la commande **npm audit** ne doit retourner aucun avertissement avec un niveau élevé ou modéré.
   * La commande **pbiviz package** ne doit retourner aucune erreur.
   * Doit inclure [TSlint de Microsoft](https://www.npmjs.com/package/tslint-microsoft-contrib) sans configuration remplacée, et cette commande ne doit pas retourner d’erreurs Lint.
   * Le package compilé du visuel personnalisé doit correspondre au package envoyé (le hachage MD5 des deux fichiers doit être le même).
* Spécifications du code source :
   * Le visuel doit prendre en charge [l’API d’événements de rendu](https://microsoft.github.io/PowerBI-visuals/docs/how-to-guide/rendering-events/).
   * Assurez-vous qu’aucun code arbitraire/dynamique n’est exécuté (éviter : eval(), utilisation non sécurisée de setTimeout(), requestAnimationFrame(), setinterval(fonction avec entrée utilisateur), exécution d’entrées/données utilisateur).
   * Assurez-vous que le DOM est manipulé de façon sûre (éviter : innerHTML, D3.html(<entrée de données utilisateur>), utilisez l’assainissement pour les entrées/données utilisateur avant de les ajouter au modèle DOM.
   * Assurez-vous qu’il n’existe aucune erreur/exception JavaScript dans la console du navigateur pour les données d’entrée. Les utilisateurs pourraient utiliser votre visuel avec une plage différente de données inattendue, le visuel ne doit donc pas échouer. Vous pouvez utiliser [cet exemple de rapport](https://github.com/Microsoft/PowerBI-visuals/raw/gh-pages/assets/reports/large_data.pbix) comme jeu de données de test.

* Si des propriétés dans capabilities.json sont modifiées, assurez-vous qu’elles n’interrompent pas les rapports de l’utilisateur existant.

* Assurez-vous que le visuel est conforme à la [Marche à suivre pour les visuels Power BI](./developer/guidelines-powerbi-visuals.md#guidelines-for-power-bi-visuals-with-additional-purchases). **Aucun filigrane n’est autorisé**.

* Utilise uniquement des composants OSS publics consultables (bibliothèques JS ou code TypeScript publics. Le code source est disponible pour revue et ne présente pas de vulnérabilités connues). Nous ne pouvons pas vérifier un visuel personnalisé à l’aide d’un composant commercial.

* N’accède pas à des services ni à des ressources externes. Citons notamment, mais pas exclusivement, les requêtes HTTP/S ou WebSocket qui accèdent à des services à l’extérieur de Power BI. 

> [!TIP]
> Nous vous recommandons d’utiliser EsLint avec un ensemble de règles de sécurité par défaut pour prévalider votre code avant de le soumettre.

## <a name="process-for-submitting-a-custom-visual-for-certification"></a>Processus de soumission d’un visuel personnalisé en vue de sa certification

Pour soumettre un visuel personnalisé en vue de sa certification :

1. Envoyez un e-mail à l’équipe de support technique des visuels Power BI de Power BI (pbicvsupport@microsoft.com). Dans l’e-mail, incluez les informations suivantes :
    * Titre : Demande de certification de visuel
    * Lien vers le dépôt GitHub où est hébergé le code source contrôlable de visu
    * [Respect des exigences](#certification-requirements)
    * Revue du code réussie

2. L’équipe de Microsoft en charge des visuels Power BI vous avertit quand votre visuel Power BI est certifié et ajouté à la [liste certifiée](#list-of-power-bi-visuals-that-have-been-certified). S’il est rejeté, un rapport des problèmes à résoudre vous est envoyé. Il incombe au développeur d’ouvrir et de maintenir ouverte une ligne de communication avec Microsoft, ainsi que de mettre à jour ses visuels certifiés au besoin.

## <a name="list-of-power-bi-visuals-that-have-been-certified"></a>Liste des visuels Power BI qui ont été certifiés

| Lien vers AppSource | Lien vers la vidéo |
| --- | --- |
| [Systèmes 3AG – graphique à barres avec écart relatif](https://appsource.microsoft.com/en/product/power-bi-visuals/WA104381912) | |
| [Systèmes 3AG - histogramme avec écart relatif](https://appsource.microsoft.com/product/power-bi-visuals/WA104381803) | |
| [Advanced Donut Visual](https://appsource.microsoft.com/product/power-bi-visuals/WA104381941) | |
| [Advanced Network Visualization](https://appsource.microsoft.com/product/power-bi-visuals/WA104381942) | |
| [Advanced TimeSeries Visual](https://appsource.microsoft.com/product/power-bi-visuals/WA104381943) | |
| [Advanced Combo Visual](https://appsource.microsoft.com/product/power-bi-visuals/WA104381944) | |
| [Traçage Aster](https://appsource.microsoft.com/product/power-bi-visuals/WA104380759) | |
| [Calendrier Beyondsoft](https://appsource.microsoft.com/product/power-bi-visuals/WA104381096) | |
| [Bowtie Chart par MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380838) | [Vidéo](https://youtu.be/So5xKMSpVJI) |
| [Graphique en boîte à moustaches](https://appsource.microsoft.com/product/power-bi-visuals/WA104380831) | |
| [Graphique en boîte à moustaches par MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381351) | [Vidéo](https://youtu.be/JoHaFLfhXdo) |
| [Brick Chart par MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380836) | [Vidéo](https://youtu.be/hA3DOsvn2xY) |
| [Bubble Chart par Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381340) | |
| [Bullet Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380755) | [Vidéo](https://youtu.be/AOlsFYkfkcw) |
| [Graphique à puces par OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380953) | [Vidéo](https://youtu.be/mtvUNl9bMjA) |
| [Calendar par Tallan](https://appsource.microsoft.com/product/power-bi-visuals/WA104381146) | |
| [Candlestick par OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380952) | [Vidéo](https://youtu.be/nT_18gyRxPo) |
| [Carte avec états par OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380967) | |
| [Segment Chiclet](https://appsource.microsoft.com/product/power-bi-visuals/WA104380756) | |
| [Chord](https://appsource.microsoft.com/product/power-bi-visuals/WA104380761) | [Vidéo](https://youtu.be/AQvd2FhRyCI) |
| [Circular Gauge par MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380837) | [Vidéo](https://youtu.be/9NHXALkBXuY) |
| [Carte du cluster](https://appsource.microsoft.com/product/power-bi-visuals/WA104380806) | |
| [Cylindrical Gauge par MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380874) | [Vidéo](https://youtu.be/DgdoWi7Gcxo) |
| [Jauge radiale](https://appsource.microsoft.com/product/power-bi-visuals/WA104381184) | |
| [Graphique à points](https://appsource.microsoft.com/product/power-bi-visuals/WA104380760) | |
| [Traçage de points par OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380949) | [Vidéo](https://youtu.be/By16pX9KT40) |
| [Drilldown Cartogram](https://appsource.microsoft.com/product/power-bi-visuals/WA104381045) | |
| [Drilldown Choropleth](https://appsource.microsoft.com/product/power-bi-visuals/WA104381044) | |
| [Graphique d’analyse en colonnes](https://appsource.microsoft.com/product/power-bi-visuals/WA104380857) | [Vidéo](https://youtu.be/lBy2gQQ5YsQ) |
| [Graphique d’analyse en colonnes pour les données temporelles](https://appsource.microsoft.com/product/power-bi-visuals/WA104380881) | [Vidéo](https://youtu.be/T_mRou18vx0) |
| [Graphique d’analyse en anneau](https://appsource.microsoft.com/product/power-bi-visuals/WA104380858) | [Vidéo](https://youtu.be/AUVFrSHmPeo) |
| [Dual KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104380774) | |
| [Dynamic Tooltip par MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380983) | [Vidéo](https://youtu.be/Z-tl97BpEr0) |
| [Enhanced Scatter](https://appsource.microsoft.com/product/power-bi-visuals/WA104380762) | [Vidéo](https://youtu.be/xCfM0cjM4do) |
| [Enlighten Aquarium](https://appsource.microsoft.com/product/power-bi-visuals/WA104381112) | |
| [Enlighten Slicer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380960) | |
| [Enlighten Stack Shuffle](https://appsource.microsoft.com/product/power-bi-visuals/WA104380849) | |
| [Enlighten Waffle Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380850) | |
| [Filter by List par Devscope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381413) | [Vidéo](https://youtu.be/RetEWGwBu0I) |
| [Graphique Force-Directed](https://appsource.microsoft.com/product/power-bi-visuals/WA104380764) | [Vidéo](https://youtu.be/YsTa7uyJ4sg) |
| [Funnel with Source par MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381334) | [Vidéo](https://youtu.be/R_EcimsLI8U) |
| [Diagramme de Gantt](https://appsource.microsoft.com/product/power-bi-visuals/WA104380765) | [Vidéo](https://youtu.be/qJ7s_KrGiUU) |
| [Diagramme de Gantt par MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381364) | [Vidéo](https://youtu.be/vJLV9JRCpI8) |
| [Globe Data Bars](https://appsource.microsoft.com/product/power-bi-visuals/WA104381344) | |
| [Grid par MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380825) | [Vidéo](https://youtu.be/VOPoDJgZfOY) |
| [Hierarchy Chart par Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381333) | [Vidéo](https://youtu.be/0ZGzJaq_KT4) |
| [Histogramme](https://appsource.microsoft.com/product/power-bi-visuals/WA104380776) | |
| [Histogramme avec points par MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381032) | [Vidéo](https://youtu.be/-ILF--wExrw) |
| [Horizontal Funnel par MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380846) | [Vidéo](https://youtu.be/SudZei68PPo) |
| [Image par CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381297) | |
| [Image Grid](https://appsource.microsoft.com/product/power-bi-visuals/WA104381355) | |
| [Infographic Designer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380898) | |
| [Graphique KPI par Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381432) | |
| [Colonne KPI par MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380996) | [Vidéo](https://youtu.be/rU0xoOlIq1U) |
| [Grille KPI par MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380947) | [Vidéo](https://youtu.be/dM4PvZh71V0) |
| [Indicateur d’indicateur de performance clé](https://appsource.microsoft.com/product/power-bi-visuals/WA104380832) | |
| [KPI Ticker par MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380946) | [Vidéo](https://youtu.be/cudG4gsZ2V8) |
| [Linear Gauge par MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380821) | [Vidéo](https://youtu.be/7_jFaM30dkc) |
| [LineDot Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380766) | |
| [Graphique Mekko](https://appsource.microsoft.com/product/power-bi-visuals/WA104380785) | [Vidéo](https://youtu.be/90FLCKpgicA) |
| [Multi KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104381763) | |
| [Vue d’ensemble par CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381477) | |
| [Axe de lecture (segment dynamique)](https://appsource.microsoft.com/product/power-bi-visuals/WA104380981) | |
| [Power KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104381083) | [Vidéo](https://youtu.be/IvfIP3E6-1Q) |
| [Matrice des indicateurs de performance clé Power](https://appsource.microsoft.com/product/power-bi-visuals/WA104381299) | [Vidéo](https://youtu.be/1enze8pcGzY) |
| [Graphique de pulsations](https://appsource.microsoft.com/product/power-bi-visuals/WA104381006) | [Vidéo](https://youtu.be/DQWdcQtjDVw) |
| [Quadrant Chart par MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381011) | [Vidéo](https://youtu.be/ppBnyhqWNC0) |
| [Graphique en radar](https://appsource.microsoft.com/product/power-bi-visuals/WA104380771) | |
| [Ring Chart par MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380824) | [Vidéo](https://youtu.be/pDToHDFHnq8) |
| [Rotating Chart par MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381007) | [Vidéo](https://youtu.be/d5xBCMmb3hU) |
| [Graphique de Sankey](https://appsource.microsoft.com/product/power-bi-visuals/WA104380777) | [Vidéo](https://youtu.be/WWP9wVUHGaA) |
| [Graphique à nuages de points par Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381703) | |
| [Barre de défilement](https://appsource.microsoft.com/product/power-bi-visuals/WA104381018) | |
| [Filtre dynamique par OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380859) | [Vidéo](https://youtu.be/gcJsDDRQq28) |
| [Graphique sparkline par OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380910) | [Vidéo](https://youtu.be/0m3Vnvso9tY) |
| [Stream Graph](https://appsource.microsoft.com/product/power-bi-visuals/WA104380772) | |
| [Graphique en rayons de soleil](https://appsource.microsoft.com/product/power-bi-visuals/WA104380767) | |
| [Tableau synoptique par OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380873) | |
| [Carte thermique Table](https://appsource.microsoft.com/product/power-bi-visuals/WA104380818) | |
| [Tachymètre](https://appsource.microsoft.com/product/power-bi-visuals/WA104380937) | [Vidéo](https://youtu.be/C3OXdETbS9o) |
| [Filtre de texte](https://appsource.microsoft.com/product/power-bi-visuals/WA104381309) | |
| [Text Wrapper par MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380826) | |
| [Thermometer by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380847) | [Vidéo](https://youtu.be/SPX9mgrAdBc) |
| [Time Brush Slicer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380798) | |
| [Timeline Slicer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380786) | [Vidéo](https://youtu.be/ozMtZ4_NZ10) |
| [Timeline par CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381427) | [Vidéo](https://youtu.be/szNi9YgXFJc) |
| [Graphique en tornade](https://appsource.microsoft.com/product/power-bi-visuals/WA104380768) | [Vidéo](https://www.youtube.com/watch?v=AQvd2FhRyCI) |
| [Trading Chart par MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380823) | [Vidéo](https://youtu.be/xhTR6y6J9Ko) |
| [Ultimate Variance](https://appsource.microsoft.com/product/power-bi-visuals/WA104381140) | [Vidéo](https://youtu.be/pDYF8iZxERs) |
| [Ultimate Waterfall](https://appsource.microsoft.com/product/power-bi-visuals/WA104380956) | [Vidéo](https://youtu.be/0BZsVCQdEkc) |
| [User List par CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381426) | |
| [Graphique en gaufre](https://appsource.microsoft.com/product/power-bi-visuals/WA104381049) | [Vidéo](https://youtu.be/1vRqYUsm3Vk) |
| [Nuage de mots](https://appsource.microsoft.com/product/power-bi-visuals/WA104380752) | [Vidéo](https://youtu.be/AblTenl9fqo) |

## <a name="faq"></a>FORUM AUX QUESTIONS

Pour plus d’informations sur les visuels, consultez [Questions fréquentes sur les visuels certifiés](power-bi-custom-visuals-faq.md#certified-power-bi-visuals).

## <a name="next-steps"></a>Étapes suivantes

* [Développement d’un visuel personnalisé Power BI](developer/visuals/custom-visual-develop-tutorial.md)
* [Sélection de visuels personnalisés de Microsoft sur YouTube](https://www.youtube.com/playlist?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x)  
* [Visualisations dans Power BI](visuals/power-bi-report-visualizations.md)  
* [Visualisations personnalisées dans Power BI](power-bi-custom-visuals.md)  
* [Publier des visuels Power BI dans Microsoft AppSource](developer/office-store.md)  

D’autres questions ? [Posez vos questions à la communauté Power BI](https://community.powerbi.com/)
