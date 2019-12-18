---
title: Visuels Power BI certifiés
description: Découvrez la configuration requise et la procédure à suivre pour soumettre un visuel personnalisé pour certification. Cet article présente également une liste de visuels Power BI déjà certifiés.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 12/02/2019
ms.openlocfilehash: 0a39496ade27cd45fae116eea92ef4b472e04582
ms.sourcegitcommit: 5bb62c630e592af561173e449fc113efd7f84808
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2019
ms.locfileid: "74999741"
---
# <a name="get-a-power-bi-visual-certified"></a>Obtenir un visuel Power BI certifié

Les visuels Power BI certifiés sont des visuels de la *Place de marché* qui respectent certaines conditions de *code spécifié*, celles-ci ayant été testées et approuvées par l’*équipe Microsoft Power BI*. Les tests sont conçus pour vérifier que le visuel n’a pas accès à des services ni à des ressources externes.

Les visuels Power BI certifiés et les [visuels Power BI standard](power-bi-custom-visuals.md) sont utilisés de la même manière. Ils peuvent être ajoutés à [Power BI Desktop](../desktop-what-is-desktop.md) et à un [service Power BI](../power-bi-service-overview.md), et affichés avec [Power BI Mobile](../consumer/mobile/mobile-apps-for-mobile-devices.md) et [Power BI Embedded](embedding.md).

Le processus de certification est un processus facultatif. Il appartient aux développeurs de décider s’ils souhaitent que leur visuel Power BI soit certifié dans la Place de marché. Un visuel Power BI certifié offre davantage de fonctionnalités. Par exemple, vous pouvez [exporter vers PowerPoint](../consumer/end-user-powerpoint.md) ou afficher le visuel dans les e-mails reçus quand un utilisateur [s’abonne aux pages du rapport](../consumer/end-user-subscribe.md).

Un visuel Power BI non certifié ne présente pas nécessairement des risques pour la sécurité. Certains visuels ne sont pas certifiés car ils ne sont pas conformes à un ou plusieurs [critères de certification](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements). Citons par exemple les visuels de carte qui se connectent à un service externe ou ceux qui utilisent des bibliothèques commerciales.

Si vous êtes un développeur web qui souhaite créer ses propres visuels Power BI et les ajouter à  [Microsoft AppSource](https://appsource.microsoft.com), commencez par le tutoriel  [Développement d'un visuel Power BI](visuals/custom-visual-develop-tutorial.md).

> [!NOTE]
> **Microsoft** n’est *pas* l’auteur des visuels Power BI de tiers. Pour vérifier le fonctionnement des visuels de tiers, nous conseillons aux clients de contacter directement leur auteur.

> [!IMPORTANT]
> Microsoft peut supprimer un visuel Power BI de la [liste certifiée](#list-of-power-bi-visuals-that-have-been-certified) à sa discrétion.

## <a name="certification-requirements"></a>Critères de certification

Pour faire [certifier](#get-a-power-bi-visual-certified) votre visuel Power BI, assurez-vous que votre visuel Power BI est conforme aux exigences énumérées dans cette section. 

> [!TIP]
> Nous vous recommandons d’utiliser EsLint avec l’ensemble de règles de sécurité par défaut pour prévalider votre code avant de le soumettre.

* Tableau de bord vendeur Microsoft ou Espace partenaires approuvé. Votre visuel Power BI doit figurer dans notre [Place de marché](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals).
* Le visuel Power BI est écrit avec une *API v2.5* ou ultérieure.
* Le référentiel de code est disponible pour examen par l'équipe Power BI. Par exemple, nous disposons d’un format lisible du code source (JavaScript ou TypeScript) via GitHub.

    >[!NOTE]
    > Vous n’êtes pas obligé de partager publiquement votre code dans Github.

* Configuration requise pour le référentiel de code :
  * Doit inclure les fichiers suivants :
    * .gitignore
    * capabilities.json
    * pbiviz.json
    * package.json
    * package-lock.json
    * tsconfig.json
  * Ne doit pas inclure le dossier *node_modules* (ajoutez *node_modules* au fichier .gitingore*).
  * La commande *npm install* ne doit retourner aucune erreur.
  * La commande *npm audit* ne doit retourner aucun avertissement avec un niveau élevé ou modéré.
  * La commande *pbiviz package* ne doit retourner aucune erreur.
  * Doit inclure [TSlint de Microsoft](https://www.npmjs.com/package/tslint-microsoft-contrib) sans configuration remplacée. Cette commande ne doit retourner aucune erreur Lint.
   * Le package compilé du visuel Power BI doit correspondre au package envoyé (le hachage MD5 des deux fichiers doit être le même).
* Spécifications du code source :
   * Le visuel Power BI doit prendre en charge [l’API d’événements de rendu](https://microsoft.github.io/PowerBI-visuals/docs/how-to-guide/rendering-events/).
   * Assurez-vous qu’aucun code arbitraire/dynamique n’est exécuté (éviter : eval(), utilisation non sécurisée de setTimeout(), requestAnimationFrame(), setinterval(fonction avec entrée utilisateur), exécution d’entrées/données utilisateur).
   * Assurez-vous que le DOM est manipulé de façon sûre (éviter : innerHTML, D3.html(<entrée de données utilisateur>), utilisez l’assainissement pour les entrées/données utilisateur avant de les ajouter au modèle DOM.
   * Assurez-vous qu’il n’existe aucune erreur ou exception JavaScript dans la console du navigateur pour les données d’entrée. Les utilisateurs pourraient utiliser votre visuel Power BI avec une plage différente de données inattendue, le visuel ne doit donc pas échouer. Vous pouvez utiliser [cet exemple de rapport](https://github.com/Microsoft/PowerBI-visuals/raw/gh-pages/assets/reports/large_data.pbix) comme jeu de données de test.

* Si des propriétés dans le fichier *capabilities.json* sont modifiées, assurez-vous qu’elles n’interrompent pas les rapports de l’utilisateur existant.

* Assurez-vous que le visuel Power BI est conforme à la [Marche à suivre pour les visuels Power BI](./guidelines-powerbi-visuals.md).
    
* Votre code ne peut utiliser que des composants OSS consultables par le public tels que des bibliothèques publiques JavaScript ou TypeScript. Le code source doit être disponible pour examen et ne pas présenter de vulnérabilités connues. Nous ne pouvons pas vérifier un visuel personnalisé à l’aide d’un composant commercial.

* Le visuel Power BI ne doit pas accéder à des services ou ressources externes. Par exemple, aucune requête HTTP/S ou WebSocket ne peut accéder à des services à l’extérieur de Power BI. 

## <a name="submitting-a-power-bi-visual-for-certification"></a>Soumission d'un visuel Power BI pour certification

Vous pouvez demander à l'équipe Power BI de certifier votre visuel Power BI via l’Espace partenaires.

>[!TIP]
>Le processus de certification Power BI peut prendre du temps. Si vous créez un nouveau visuel Power BI, nous vous recommandons de publier votre visuel Power BI via l’Espace partenaires avant de demander une certification Power BI. Cela évite ainsi tout retard dans la publication de votre visuel.

Pour demander la certification Power BI :

1. Connectez-vous à l’Espace partenaires.
2. Sur la **page Vue d’ensemble**, choisissez votre visuel Power BI, puis accédez à la page de configuration du **produit**.
3. Cochez la case **Demander la certification Power BI**.
4. Sur la page **Vérifier et publier**, dans la zone de texte **Remarques pour la certification**, fournissez un lien vers le code source et les informations d'identification requises pour y accéder.

>[!NOTE]
> Si un processus de soumission d’un visuel Power BI est en cours et que vous devez utiliser le [tableau de bord du vendeur](https://docs.microsoft.com/office/dev/store/use-the-seller-dashboard-to-submit-to-the-office-store) (l’ancien outil de gestion), passez en revue les instructions du [processus de soumission d’une certification du tableau de bord vendeur](seller-dashboard.md#seller-dashboard-certification-submission-process).

## <a name="list-of-power-bi-visuals-that-have-been-certified"></a>Liste des visuels Power BI qui ont été certifiés

| Lien | Video |
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

* [Développement d’un visuel personnalisé Power BI](../developer/custom-visual-develop-tutorial.md)
* [Sélection de visuels personnalisés de Microsoft sur YouTube](https://www.youtube.com/playlist?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x)  
* [Visualisations dans Power BI](../visuals/power-bi-report-visualizations.md)  
* [Visualisations personnalisées dans Power BI](power-bi-custom-visuals.md)  
* [Publier des visuels Power BI dans Microsoft AppSource](../developer/office-store.md)  

D’autres questions ? [Posez vos questions à la communauté Power BI](https://community.powerbi.com/)
