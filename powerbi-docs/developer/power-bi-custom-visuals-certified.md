---
title: Visuels Power BI certifiés
description: Exigences à respecter et procédure à suivre pour faire une demande de certification d’un visuel personnalisé, et liste des visuels Power BI certifiés.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 03/01/2020
ms.openlocfilehash: 8aea9041665de69b2c5be954dc8f13a6402a06e0
ms.sourcegitcommit: d55d3089fcb3e78930326975957c9940becf2e76
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78260758"
---
# <a name="get-a-power-bi-visual-certified"></a>Obtenir un visuel Power BI certifié

Les visuels Power BI certifiés sont des visuels Power BI [d’AppSource](https://appsource.microsoft.com/en-us/marketplace/apps?page=1&product=power-bi-visuals) conformes aux [exigences de code](#certification-requirements) de l’équipe Microsoft Power BI. Ces visuels sont testés pour vérifier qu’ils n’accèdent pas à des services ou ressources externes, et qu’ils suivent les modèles et instructions de codage sécurisé.

Un visuel Power BI certifié offre davantage de fonctionnalités. Par exemple, vous pouvez [exporter vers PowerPoint](../consumer/end-user-powerpoint.md) ou afficher le visuel dans les e-mails reçus quand un utilisateur [s’abonne aux pages du rapport](../consumer/end-user-subscribe.md).

Le processus de certification est facultatif. Les visuels Power BI non certifiés ne sont pas nécessairement des visuels Power BI non sécurisés. Certains visuels Power BI ne sont pas certifiés parce qu’ils ne sont pas conformes à un ou plusieurs [exigences de certification](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements), par exemple un visuel Power BI de type carte se connectant à un service externe ou un visuel Power BI utilisant des bibliothèques commerciales.

> [!NOTE]
> Microsoft n’est pas l’auteur des visuels Power BI de tiers. Pour vérifier le fonctionnement des visuels de tiers, contactez directement leur auteur.

## <a name="certification-requirements"></a>Critères de certification

Votre visuel Power BI doit être conforme aux exigences listées dans cette section pour que vous puissiez le faire [certifier](#get-a-power-bi-visual-certified). 

### <a name="general-requirements"></a>Conditions générales

Votre visuel Power BI doit être approuvé par le tableau de bord vendeur ou l’Espace partenaires. Il est recommandé que le visuel Power BI se trouve déjà dans [AppSource](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals). Pour savoir comment publier un visuel Power BI sur AppSource, consultez [Publier des visuels Power BI sur l’Espace partenaires](office-store.md).

Avant de faire une demande de certification pour votre visuel Power BI, vérifiez qu’il est conforme aux [instructions sur les visuels Power BI](./guidelines-powerbi-visuals.md).

Lorsque vous envoyez votre visuel Power BI, vérifiez que le package compilé correspond exactement au package envoyé.

### <a name="code-repository-requirements"></a>Exigences relatives au référentiel de code

Bien qu’il ne soit pas nécessaire de partager publiquement le code dans GitHub, l’équipe Power BI doit avoir accès au référentiel de code pour pouvoir l’examiner. La meilleure solution consiste à fournir le code source (JavaScript ou TypeScript) dans GitHub.

Le référentiel doit contenir les éléments suivants :
* Code pour un seul élément visuel Power BI. Il ne peut pas contenir le code de plusieurs visuels Power BI ou du code sans rapport.
* Une branche nommée **certification** (obligatoirement en minuscules). Le code source de cette branche doit correspondre au package soumis. Ce code ne peut être mis à jour que lors du processus d’envoi suivant, si vous envoyez à nouveau votre visuel Power BI.

Si votre visuel Power BI utilise des packages npm privés ou des sous-modules GIT, vous devez fournir l’accès aux référentiels supplémentaires contenant ce code.

Pour comprendre l’aspect d’un référentiel visuel Power BI, examinez le référentiel GitHub sur le [Graphique à barres exemple des éléments visuels Power BI](https://github.com/microsoft/PowerBI-visuals-sampleBarChartgi).

### <a name="file-requirements"></a>Exigences relatives aux fichiers

Utilisez la dernière version de l’API pour écrire le visuel Power BI.

Le référentiel doit comporter les fichiers suivants :
* **.gitignore** : ajoutez `node_modules`, `.tmp`, `dist` à ce fichier. Le code ne peut pas inclure les dossiers *node_modules*, *.tmp* or *dist*.
* **capabilities.json** : si vous soumettez une version plus récente de votre visuel Power BI dont les propriétés ont été modifiées dans ce fichier, vérifiez qu’elles ne bloquent pas les rapports pour les utilisateurs existants.
* **pbiviz.json** 
* **package.json**. Le package suivant doit être installé dans le visuel :
   * [« tslint »](https://www.npmjs.com/package/tslint) : « 5.18.0 » ou ultérieure
   * [« typescript » ](https://www.npmjs.com/package/typescript) : « 3.0.0 » ou ultérieure
   * [« tslint-microsoftcontrib »](https://www.npmjs.com/package/tslint-microsoft-contrib) : « 6.2.0 » ou ultérieure
   * Le fichier doit contenir la commande d’exécution de linter : « lint » : « tslint -c tslint.json -p tsconfig.json »
* **package-lock.json**
* **tsconfig.json**

### <a name="command-requirements"></a>Exigences relatives aux commandes

Vérifiez que les commandes suivantes ne retournent aucune erreur.

* `npm install`
* `pbiviz package`
* `npm audit` : ne doit retourner aucun avertissement de niveau élevé ou modéré.
* [TSlint de Microsoft](https://www.npmjs.com/package/tslint-microsoft-contrib) avec [la configuration requise](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/master/tslint.json). Cette commande ne doit retourner aucune erreur Lint.

### <a name="compiling-requirements"></a>Exigences relatives à la compilation

Utilisez la dernière version de [powerbi-visuals-tools](https://www.npmjs.com/package/powerbi-visuals-tools) pour écrire le visuel Power BI.

Vous devez compiler votre visuel Power BI avec `pbiviz package`. Si vous utilisez vos propres scripts de build, fournissez une commande de build personnalisée `npm run package`.



### <a name="source-code-requirements"></a>Exigences relatives au code source

Vérifiez que vous suivez la liste des stratégies de [certification supplémentaires des visuels Power BI](https://docs.microsoft.com/legal/marketplace/certification-policies#1200-power-bi-visuals-additional-certification). Si votre envoi ne suit pas ces instructions, l’e-mail de rejet de l’Espace partenaires comportera les numéros de stratégie indiqués dans ce lien.

Suivez les exigences relatives au code ci-dessous pour vérifier que votre code est conforme aux stratégies de certification Power BI.  

**Obligatoire**
* N’utilisez que des composants OSS consultables par le public, comme des bibliothèques publiques JavaScript ou TypeScript.
* Le code doit prendre en charge [l’API d’événements de rendu](./visuals/event-service.md).
* Vérifiez que le DOM est correctement manipulé. Utilisez l’assainissement pour la saisie ou les données utilisateur avant de les ajouter au DOM.
* Utilisez [l’exemple de rapport](https://github.com/Microsoft/PowerBI-visuals/raw/gh-pages/assets/reports/large_data.pbix) comme jeu de données de test.

**Non autorisé**
* Accès à des services ou ressources externes. Par exemple, aucune requête HTTP/S ou WebSocket ne peut accéder à des services à l’extérieur de Power BI.
* Usage de `innerHTML` ou de `D3.html(user data or user input)`.
* Erreurs ou exceptions JavaScript dans la console du navigateur pour les données d’entrée.
* Code arbitraire ou dynamique, comme `eval()`, utilisation non sécurisée de `settimeout()`, de `requestAnimationFrame()`, de `setinterval(user input function)` et de la saisie ou des données utilisateur.
* Fichiers ou projets JavaScript minifiés.

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

### <a name="private-repository-submission-process"></a>Processus d’envoi du référentiel privé

Si vous utilisez un référentiel privé tel que GitHub pour envoyer votre élément visuel Power BI pour certification, suivez les instructions de cette section.
1. Créez un nouveau compte pour l’équipe de validation.
2. Configurez [l’authentification à deux facteurs](https://help.github.com/github/authenticating-to-github/securing-your-account-with-two-factor-authentication-2fa) pour votre compte.
3. [Générez un nouvel ensemble de codes de récupération](https://help.github.com/github/authenticating-to-github/configuring-two-factor-authentication-recovery-methods#generating-a-new-set-of-recovery-codes).
4. Lorsque vous envoyez votre élément visuel Power BI, fournissez les éléments suivants :
    * un lien web vers le référentiel
    * des informations d'identification pour la connexion (y compris le mot de passe)
    * des codes de récupération
    * des autorisations en lecture seule sur notre compte ([pbicvsupport](https://github.com/pbicvsupport))

## <a name="certified-power-bi-visuals"></a>Visuels Power BI certifiés

Les visuels Power BI certifiés sont listés ci-dessous. Cliquez sur le lien pour ouvrir le visuel Power BI dans AppSource. Si une vidéo est disponible, vous pouvez cliquer sur son lien pour la regarder.

* [Systèmes 3AG – graphique à barres avec écart absolu](https://appsource.microsoft.com/product/power-bi-visuals/WA104381802)
*  [Systèmes 3AG – graphique à barres avec écart relatif](https://appsource.microsoft.com/product/power-bi-visuals/WA104381912)
*  [Systèmes 3AG - histogramme avec écart relatif](https://appsource.microsoft.com/product/power-bi-visuals/WA104381803)
*  [Systèmes 3AG - histogramme avec écart](https://appsource.microsoft.com/product/power-bi-visuals/WA104381724)
* [Advanced Donut Visual (Full Edition)](https://appsource.microsoft.com/product/power-bi-visuals/WA104381941)
*  [Advanced Donut Visual (Light Edition)](https://appsource.microsoft.com/product/power-bi-visuals/WA104380858)
*  [Advanced Graph Visual](https://appsource.microsoft.com/product/power-bi-visuals/WA104382086)
*  [Advanced Network Visualization](https://appsource.microsoft.com/product/power-bi-visuals/WA104381942)
*  [Advanced TimeSeries Visual (Full Edition)](https://appsource.microsoft.com/product/power-bi-visuals/WA104381943)
*  [Traçage Aster](https://appsource.microsoft.com/product/power-bi-visuals/WA104380759)
*  [Calendrier Beyondsoft](https://appsource.microsoft.com/product/power-bi-visuals/WA104381096)
*  [Bowtie Chart par MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380838)
*  [Graphique en boîte à moustaches](https://appsource.microsoft.com/product/power-bi-visuals/WA104380831)
* [Graphique en boîte à moustaches par MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381351)
*  [Brick Chart par MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380836)
*  [Bubble Chart par Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381340)
*  [Bullet Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380755),  **[lien vers la vidéo](https://youtu.be/AOlsFYkfkcw)**
* [Bullet Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380755)
*  [Bullet Chart par OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380953), **[lien vers la vidéo](https://youtu.be/mtvUNl9bMjA)**
* [Calendar par MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381844)
*  [Calendar par Tallan](https://appsource.microsoft.com/product/power-bi-visuals/WA104381146)
*  [Candlestick par OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380952), **[lien vers la vidéo](https://youtu.be/nT_18gyRxPo)**
*  [Carte avec états par OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380967)
*  [Segment Chiclet](https://appsource.microsoft.com/product/power-bi-visuals/WA104380756)
*  [Chord](https://appsource.microsoft.com/product/power-bi-visuals/WA104380761), **[lien vers la vidéo](https://youtu.be/AQvd2FhRyCI)**
*  [Circular Gauge par MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380837)
*  [Carte du cluster](https://appsource.microsoft.com/product/power-bi-visuals/WA104380806)
* [Custom Calendar par Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381179)
* [Cylindrical Gauge par MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380874)
*  [Dial Gauge](https://appsource.microsoft.com/product/power-bi-visuals/WA104381184)
[Dot Plot](https://appsource.microsoft.com/product/power-bi-visuals/WA104380760)
*  [Dot Plot par OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380949), **[lien vers la vidéo](https://youtu.be/By16pX9KT40)**
*  [Drilldown Cartogram](https://appsource.microsoft.com/product/power-bi-visuals/WA104381045)
*  [Drilldown Choropleth](https://appsource.microsoft.com/product/power-bi-visuals/WA104381044)
*  [Histogramme d’exploration](https://appsource.microsoft.com/product/power-bi-visuals/WA104380857), **[lien vers la vidéo](https://youtu.be/lBy2gQQ5YsQ)**
*  [Histogramme d’exploration pour les données temporelles](https://appsource.microsoft.com/product/power-bi-visuals/WA104380881), **[lien vers la vidéo](https://youtu.be/T_mRou18vx0)**
*  [Graphique en anneau d’exploration](https://appsource.microsoft.com/product/power-bi-visuals/WA104380858), **[lien vers la vidéo](https://youtu.be/AUVFrSHmPeo)**
*  [Dual KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104380774)
*  [Dynamic Tooltip par MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380983)
*  [Nuage de points amélioré](https://appsource.microsoft.com/product/power-bi-visuals/WA104380762), **[lien vers la vidéo](https://youtu.be/xCfM0cjM4do)**
*  [Enlighten Aquarium](https://appsource.microsoft.com/product/power-bi-visuals/WA104381112)
*  [Enlighten Slicer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380960)
*  [Enlighten Stack Shuffle](https://appsource.microsoft.com/product/power-bi-visuals/WA104380849)
*  [Enlighten Waffle Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380850)
*  [Filter by List par Devscope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381413), **[lien vers la vidéo](https://youtu.be/RetEWGwBu0I)**
*  [Force-Directed Graph](https://appsource.microsoft.com/product/power-bi-visuals/WA104380764), **[lien vers la vidéo](https://youtu.be/YsTa7uyJ4sg)**
*  [Funnel with Source par MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381334)
*  [Gantt](https://appsource.microsoft.com/product/power-bi-visuals/WA104380765), **[lien vers la vidéo](https://youtu.be/qJ7s_KrGiUU)**
* [Diagramme de Gantt par MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381364)
*  [Globe Data Bars](https://appsource.microsoft.com/product/power-bi-visuals/WA104381344)
*  [Grid par MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380825)
*  [Hierarchy Chart par Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381333), **[lien vers la vidéo](https://youtu.be/0ZGzJaq_KT4)**
*  [Histogramme](https://appsource.microsoft.com/product/power-bi-visuals/WA104380776)
*  [Histogramme avec points par MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381032)
* [Histogramme horizontal](https://appsource.microsoft.com/product/power-bi-visuals/WA104381230)
*  [Horizontal Funnel par MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380846)
*  [Image par CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381297)
*  [Image Grid](https://appsource.microsoft.com/product/power-bi-visuals/WA104381355)
*  [Infographic Designer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380898)
*  [Graphique KPI par Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381432)
*  [Colonne KPI par MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380996)
*  [Grille KPI par MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380947)
*  [Indicateur d’indicateur de performance clé](https://appsource.microsoft.com/product/power-bi-visuals/WA104380832)
*  [KPI Ticker par MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380946)
* [Linear Gauge par MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380821)
*  [LineDot Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380766)
*  [Mekko Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380785), **[lien vers la vidéo](https://youtu.be/90FLCKpgicA)**
*  [Multi KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104381763)
*  [Vue d’ensemble par CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381477)
*  [Axe de lecture (segment dynamique)](https://appsource.microsoft.com/product/power-bi-visuals/WA104380981)
*  [Indicateur de performance clé Power BI](https://appsource.microsoft.com/product/power-bi-visuals/WA104381083), [lien vers la vidéo](https://youtu.be/IvfIP3E6-1Q)
*  [Matrice des indicateurs de performance clé Power](https://appsource.microsoft.com/product/power-bi-visuals/WA104381299), **[lien vers la vidéo](https://youtu.be/1enze8pcGzY)**
*  [Pulse Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104381006), **[lien vers la vidéo](https://youtu.be/DQWdcQtjDVw)**
*  [Quadrant Chart par MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381011)
*  [Graphique en radar](https://appsource.microsoft.com/product/power-bi-visuals/WA104380771)
*  [Ring Chart par MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380824)
*  [Rotating Chart par MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381007)
*  [Sankey Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380777), **[lien vers la vidéo](https://youtu.be/WWP9wVUHGaA)**
*  [Graphique à nuages de points par Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381703)
*  [Barre de défilement](https://appsource.microsoft.com/product/power-bi-visuals/WA104381018)
*  [Smart Filter par OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380859), **[lien vers la vidéo](https://youtu.be/gcJsDDRQq28)**
*  [Sparkline par OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380910), **[lien vers la vidéo](https://youtu.be/0m3Vnvso9tY)**
*  [Stream Graph](https://appsource.microsoft.com/product/power-bi-visuals/WA104380772)
*  [Graphique en rayons de soleil](https://appsource.microsoft.com/product/power-bi-visuals/WA104380767)
*  [Tableau synoptique par OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380873)
*  [Carte thermique Table](https://appsource.microsoft.com/product/power-bi-visuals/WA104380818)
*  [Tachymètre](https://appsource.microsoft.com/product/power-bi-visuals/WA104380937), **[lien vers la vidéo](https://youtu.be/C3OXdETbS9o)**
*  [Filtre de texte](https://appsource.microsoft.com/product/power-bi-visuals/WA104381309)
*  [Text Wrapper par MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380826)
*  [Thermometer by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380847)
*  [Time Brush Slicer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380798)
*  [Timeline Slicer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380786), **[lien vers la vidéo](https://youtu.be/ozMtZ4_NZ10)**
*  [Timeline par CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381427), [lien vers la vidéo](https://youtu.be/szNi9YgXFJc)
*  [Tornado Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380768), **[lien vers la vidéo](https://www.youtube.com/watch?v=AQvd2FhRyCI)**
*  [Trading Chart par MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380823)
* [Ultimate KPI Card](https://appsource.microsoft.com/product/power-bi-visuals/WA104381977)
*  [Ultimate Variance](https://appsource.microsoft.com/product/power-bi-visuals/WA104381140), **[lien vers la vidéo](https://youtu.be/pDYF8iZxERs)**
*  [Ultimate Waterfall](https://appsource.microsoft.com/product/power-bi-visuals/WA104380956), **[lien vers la vidéo](https://youtu.be/0BZsVCQdEkc)**
*  [User List par CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381426)
*  [Venn Diagram par MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381231)
*  [Violin Plot](https://appsource.microsoft.com/product/power-bi-visuals/WA104381947)
*  [Visuel Visio](https://appsource.microsoft.com/product/power-bi-visuals/WA104381132)
*  [Graphique en gaufre](https://appsource.microsoft.com/product/power-bi-visuals/WA104381049), **[lien vers la vidéo](https://youtu.be/1vRqYUsm3Vk)**
*  [Nuage de mots](https://appsource.microsoft.com/product/power-bi-visuals/WA104380752), **[lien vers la vidéo](https://youtu.be/AblTenl9fqo)**

## <a name="faq"></a>FORUM AUX QUESTIONS

Pour plus d’informations sur les visuels, consultez [Questions fréquentes sur les visuels certifiés](power-bi-custom-visuals-faq.md#certified-power-bi-visuals).

## <a name="next-steps"></a>Étapes suivantes

* [Développement d’un visuel personnalisé Power BI](../developer/custom-visual-develop-tutorial.md)
* [Sélection de visuels personnalisés de Microsoft sur YouTube](https://www.youtube.com/playlist?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x)  
* [Visualisations dans Power BI](../visuals/power-bi-report-visualizations.md)  
* [Visualisations personnalisées dans Power BI](power-bi-custom-visuals.md)  
* [Publier des visuels Power BI dans Microsoft AppSource](../developer/office-store.md) 
* Si vous êtes un développeur web qui souhaite créer ses propres visuels Power BI et les ajouter à  [Microsoft AppSource](https://appsource.microsoft.com), commencez par le tutoriel  [Développement d'un visuel Power BI](visuals/custom-visual-develop-tutorial.md). 

D’autres questions ? [Posez vos questions à la communauté Power BI](https://community.powerbi.com/)
