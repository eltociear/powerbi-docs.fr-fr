---
title: Nouveautés dans Power BI Report Server
description: Découvrez les nouveautés dans Power BI Report Server. Cet article aborde les principaux domaines de fonctionnalités et est mis à jour à mesure que de nouveaux éléments sont publiés.
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-report-server
ms.topic: conceptual
ms.date: 08/16/2018
ms.openlocfilehash: 648938006cd15e2bb92b305aa9a2af24d028cead
ms.sourcegitcommit: 67336b077668ab332e04fa670b0e9afd0a0c6489
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44726935"
---
# <a name="whats-new-in-power-bi-report-server"></a>Nouveautés dans Power BI Report Server

Découvrez les nouveautés dans Power BI Report Server. Cet article aborde les principaux domaines de fonctionnalités et est mis à jour à mesure que de nouveaux éléments sont publiés.

Pour télécharger Power BI Report Server et Power BI Desktop optimisé pour Power BI Report Server, accédez à la page [Rapports locaux avec Power BI Report Server](https://powerbi.microsoft.com/report-server/).

Consultez également les sources suivantes pour vous tenir au courant des nouvelles fonctionnalités de Power BI Report Server.

* [Blog Microsoft Power BI](https://powerbi.microsoft.com/blog/)
* [Blog de l’équipe SQL Server Reporting Services](https://blogs.msdn.microsoft.com/sqlrsteamblog/)
* [Chaîne YouTube Guy in a Cube](https://aka.ms/guyinacube)

Pour des informations connexes sur les nouveautés de Power BI, voir :

* [Nouveautés dans le service Power BI](../service-whats-new.md)
* [Nouveautés dans Power BI Desktop](../desktop-latest-update.md)
* [Nouveautés dans les applications mobiles pour Power BI](../consumer/mobile/mobile-whats-new-in-the-mobile-apps.md)

## <a name="august-2018"></a>Août 2018

De nombreuses fonctionnalités nouvelles ont été ajoutées à la version de Power BI Desktop d’août 2018, optimisée pour Power BI Report Server. Voici ces fonctionnalités, réparties par domaine :

- [Création de rapports](#reporting)
- [Analytique](#analytics)
- [Modélisation](#modeling)

### <a name="highlights-of-the-august-2018-release"></a>Principales nouveautés de la version d’août 2018

Parmi la longue liste des nouvelles fonctionnalités, celles-ci sont particulièrement intéressantes. Pour plus d’informations, consultez notre [billet de blog](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/).

#### <a name="report-theming"></a>Thèmes de rapport

Les thèmes de rapport ont été ajoutés à la version d’août 2018 de Power BI Report Server : ils vous permettent d’utiliser rapidement des couleurs dans tout votre rapport pour le faire correspondre à un thème ou à une personnalisation d’entreprise. Quand vous importez un thème, tous vos graphiques sont automatiquement mis à jour pour utiliser les couleurs du thème, et vous pouvez accéder aux couleurs du thème à partir de la palette de couleurs. Vous pouvez charger un fichier de thème en utilisant l’option **Importer un thème** sous le bouton **Changer de thème**.

Un fichier de thème est un fichier JSON qui inclut toutes les couleurs que vous voulez utiliser dans votre rapport, ainsi que les mises en forme par défaut à appliquer aux visuels.
Voici un exemple simple de thème JSON qui met simplement à jour les couleurs par défaut du rapport :

```json
{
"name": "waveform",
"dataColors": [ "#31B6FD", "#4584D3", "#5BD078", "#A5D028", "#F5C040", "#05E0DB", "#3153FD", "#4C45D3", "#5BD0B0", "#54D028", "#D0F540", "#057BE0" ],
"background":"#FFFFFF",
"foreground": "#F2F2F2",
"tableAccent":"#5BD078"
}
```

#### <a name="conditional-formatting-by-a-different-field"></a>Mise en forme conditionnelle en fonction d’un autre champ

La possibilité de mettre en forme une colonne en fonction d’un autre champ de votre modèle est une des améliorations significatives de la mise en forme conditionnelle.

#### <a name="conditional-formatting-by-values"></a>Mise en forme conditionnelle en fonction de valeurs

Un autre nouveau type de mise en forme conditionnelle est **Mettre en forme en fonction de la valeur d’un champ**. « Mettre en forme en fonction de la valeur d’un champ » vous permet d’utiliser une mesure ou une colonne qui spécifie une couleur, via un code hexadécimal ou un nom, et qui applique cette couleur à l’arrière-plan ou à la police.

#### <a name="report-page-tooltips"></a>Info-bulles de page de rapport

La fonctionnalité d’info-bulles de page de rapport est incluse dans la mise à jour d’août 2018 de Power BI Report Server. Cette fonctionnalité vous permet de concevoir l’utilisation d’une page de rapport comme info-bulle personnalisée pour d’autres visuels de votre rapport.

#### <a name="log-axis-improvements"></a>Améliorations des axes logarithmiques

Nous avons considérablement amélioré les axes logarithmiques dans vos graphiques cartésiens. Vous pouvez désormais sélectionner une échelle logarithmique pour l’axe numérique de n’importe quel graphique cartésien, notamment les graphiques combinés, quand vous avez des données entièrement positives ou entièrement négatives.

#### <a name="sap-hana-sso-direct-query"></a>DirectQuery avec authentification unique SAP HANA

La prise en charge de DirectQuery avec authentification unique SAP HANA avec Kerberos est désormais disponible pour les rapports Power BI.

>[!Note]
>Ce scénario est pris en charge seulement quand SAP HANA est traité comme source de données relationnelle avec les rapports que vous avez créés dans Power BI Desktop.  Pour activer cette possibilité dans Power BI Desktop, dans le menu DirectQuery sous Options, cochez « Traiter SAP HANA comme source relationnelle », puis cliquez sur OK.

#### <a name="custom-visuals"></a>Visuels personnalisés

- La version de l’API livrée avec cette version est 1.13.0.

- Désormais, les visuels personnalisés peuvent utiliser comme solution de repli une version antérieure compatible avec la version actuelle de l’API du serveur (si elle est disponible).

### <a name="reporting"></a>Création de rapports 

- [Thèmes de rapport](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#theming)
- [Boutons pour déclencher des actions](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#buttons)
- [Styles de ligne pour les graphiques combinés](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#comboLines)
- [Amélioration du tri par défaut des visuels](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#sort)
- [Sélecteur de plages numériques](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#numericSlicer)
- [Synchronisation avancée de sélecteurs](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#slicerSync)
- [Améliorations des axes logarithmiques](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#logAxis)
- [Options d’étiquette de données pour graphique en entonnoir](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#funnelChart)
- [Définir l’épaisseur du trait de ligne sur zéro](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#lineStroke)
- [Prise en charge du contraste élevé dans les rapports](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#highContrast)
- [Contrôle du rayon des graphiques en anneau](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#donutRadius)
- [Contrôle de la position des étiquettes de détail des graphiques à secteurs et en anneau](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#detailLabels)
- [Mise en forme séparée des étiquettes de données pour chaque mesure dans un graphique combiné](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#comboLabels)
- [Nouvel en-tête de visuel avec plus de flexibilité et de possibilités de mise en forme](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#visualHeader)
- [Mise en forme du papier peint](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#wallpaper)
- [Info-bulles pour les tables et les matrices](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#tableTooltips)
- [Désactiver les info-bulles pour les visuels](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#tooltips)
- [Accessibilité des sélecteurs](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#slicerAccessibility)
- [Améliorations de la mise en forme des volets](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#formattingPane)
- [Prise en charge des lignes en escalier pour les graphiques en courbes et combinés](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#steppedLine)
- [Amélioration de l’expérience du tri](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#sorting)
- [Imprimer des rapports via Exporter au format PDF (dans Power BI Desktop)](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#print)
- [Créer des groupes de signets](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#bookmarks)
- [Réitération pour le sélecteur](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#slicer)
- [Info-bulles de page de rapport](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#reportPageTooltips)

### <a name="analytics"></a>Analyse

- [Nouvelle fonction DAX : COMBINEVALUES()](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#combineValues)
- [Extraction de mesure](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#measureDrillthrough)
- [Mise en forme conditionnelle en fonction d’un autre champ](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#conditionalFormattingField)
- [Mise en forme conditionnelle en fonction de valeurs](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#conditionalFormattingValue)

### <a name="modeling"></a>Modélisation

- [Filtrage et tri dans la vue de données](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#filterAndSort)
- [Amélioration de la mise en forme des paramètres régionaux](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#locale)
- [Catégories de données pour les mesures](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#dataCategory)
- [Fonctions statistiques de DAX](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#dax)

## <a name="may-2018"></a>May 2018

### <a name="configure-power-bi-ios-mobile-apps-for-report-servers-remotely"></a>Configurer à distance des applications mobiles iOS Power BI pour les serveurs de rapports

En tant qu’administrateur informatique, vous pouvez désormais utiliser l’outil MDM de votre organisation pour configurer à distance l’accès de l’application mobile iOS Power BI à un serveur de rapports. Pour plus d’informations, consultez [Configurer à distance l’accès d’une application mobile iOS Power BI à un serveur de rapports](configure-powerbi-mobile-apps-remote.md).

## <a name="march-2018"></a>Mars 2018

De nombreuses fonctionnalités nouvelles ont été ajoutées à la version de Power BI Desktop de mars 2018, optimisée pour Power BI Report Server. Voici ces fonctionnalités, réparties par domaine :

- [Visuels](#visuals-updates)
- [Création de rapports](#reporting)
- [Analytique](#analytics)
- [Performances](#performance)
- [Serveur de rapports](#report-server)
- [Autres](#other-improvements)

### <a name="highlights-of-the-march-2018-release"></a>Principales nouveautés de la version de mars 2018

Parmi la longue liste des nouvelles fonctionnalités, celles-ci sont particulièrement intéressantes.

#### <a name="rule-based-conditional-formatting-for-table-and-matrixhttpspowerbimicrosoftcomblogpower-bi-desktop-november-2017-feature-summaryconditionalformatting"></a>[Mise en forme conditionnelle basée sur des règles pour les tables et les matrices](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#conditionalFormatting)

Créer des règles pour appliquer de façon conditionnelle une couleur à l’arrière-plan ou à la police d’une colonne, en fonction d’une logique métier spécifique dans votre table ou votre matrice.

#### <a name="show-and-hide-pageshttpspowerbimicrosoftcomblogpower-bi-desktop-january-2018-feature-summaryhidepages"></a>[Afficher et masquer des pages](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#hidePages)

Vous voulez que les lecteurs aient accès à votre rapport, mais certaines des pages ne sont pas encore terminées. Vous pouvez désormais les masquer jusqu’à ce qu’elles soient prêtes. Vous pouvez aussi masquer des pages pour la navigation normale ; les lecteurs peuvent obtenir la page par extraction ou via des signets.

#### <a name="bookmarkinghttpspowerbimicrosoftcomblogpower-bi-desktop-march-2018-feature-summarybookmarking"></a>[Signets](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#bookmarking)

Vous pouvez créer des signets pour raconter une histoire avec les données de votre rapport.

- [Mise en évidence croisée pour des signets](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#bookmarkCrossHighlighting) : les signets gèrent et affichent l’état de mise en évidence croisée de la page d’un rapport au moment où vous avez créé le signet.
- [Plus de flexibilité pour les signets](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#bookmarkFlexibility) : les signets reflètent les propriétés que vous définissez dans votre rapport et affectent seulement les visuels que vous choisissez.

#### <a name="multi-select-data-points-across-multiple-chartshttpspowerbimicrosoftcomblogpower-bi-desktop-february-2018-feature-summarycrosshighlight"></a>[Points de données à sélection multiple entre plusieurs graphiques](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#crosshighlight)

Sélectionnez plusieurs points de données dans plusieurs graphiques et appliquez le filtrage croisé à toute la page.

#### <a name="sync-slicers-across-multiple-pages-of-your-reporthttpspowerbimicrosoftcomblogpower-bi-desktop-february-2018-feature-summarysyncslicers"></a>[Synchronisation des segments sur plusieurs pages de votre rapport](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#syncSlicers)

Un segment peut s’appliquer à une ou plusieurs pages d’un rapport.

#### <a name="quick-measureshttpspowerbimicrosoftcomblogpower-bi-desktop-february-2018-feature-summaryquickmeasures"></a>[Mesures rapides](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#quickMeasures) 

Créez des mesures basées sur des mesures existantes et des colonnes numériques dans une table.

#### <a name="drilling-down-filters-other-visualshttpspowerbimicrosoftcomblogpower-bi-desktop-december-feature-summarydrillfiltersothervisuals"></a>[L’exploration filtre d’autres visuels](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#drillFiltersOtherVisuals)

Quand vous descendez dans la hiérarchie d’une catégorie dans un visuel, vous pouvez faire en sorte qu’il filtre tous les visuels de la page selon la même catégorie.

### <a name="visuals-updates"></a>Mises à jour des visuels

- [Alignement des cellules pour les tables et les matrices](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#alignment)
- [Contrôle de l’affichage des unités et de la précision dans les colonnes des tables et des matrices](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#displayUnits)
- [Débordement des étiquettes de données pour les graphiques à barres et les histogrammes](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#overflow)
- [Contrôle de la couleur d’arrière-plan des étiquettes de données des visuels cartésiens et de carte](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#dataLabelBackground)
- [Contrôle du remplissage des barres/colonnes](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#padding)
- [Agrandissement de la zone utilisée pour les étiquettes d’axe dans les graphiques](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#axisSize)
- [Visuel Nuage de points à partir de regroupements des axes X et Y](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#scatterChart)
- [Échantillonnage à haute densité pour les cartes basé sur la latitude et la longitude](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#highDensityMaps)
- [Segments réactifs](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#responsive)
- [Ajout d’une date d’ancrage pour un segment de date relative](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#anchorDate)

### <a name="reporting"></a>Création de rapports

- [Désactivation de l’en-tête du visuel en mode Lecture dans un rapport](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#visualHeader)
- [Options de rapport pour les sources de données lentes](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#slowDataSource)
- [Amélioration du placement par défaut des visuels](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#visualPlacement)
- [Contrôle de l’ordre des visuels dans le volet Sélection](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#selectionPane)
- [Verrouillage des objets sur votre rapport](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#lock)
- [Recherche dans les volets Mise en forme et Analytique](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#search)
- [Volet Propriétés du champ et description de champs](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#fieldPropertiesPane)

### <a name="analytics"></a>Analyse

- [UTCNOW() et UTCTODAY()](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#utcDAX)
- [Marquage d’une table de dates personnalisée](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#customDateTable)
- [Filtres d’exploration d’autres visuels](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#drillFiltersOtherVisuals)
- [Mise en forme au niveau de la cellule pour les modèles AS multidimensionnels pour carte à plusieurs lignes](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#cellLevelFormatting)

### <a name="performance"></a>Performance

- [Améliorations des performances du filtrage](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#filtering)
- [Améliorations des performances de DirectQuery](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#dqPerf)
- [Amélioration des performances à l’ouverture et à l’enregistrement](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#savePerf)
- [Amélioration de l’option Afficher les éléments sans données](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#showItemsWithNoData)

### <a name="report-server"></a>Serveur de rapports

#### <a name="export-to-accessible-pdf"></a>Exporter au format PDF accessible

Quand vous exportez un rapport paginé (RDL) au format PDF, vous pouvez désormais obtenir un fichier PDF accessible/étiqueté. Sa taille est plus grande taille, mais la lecture et la navigation y sont plus faciles pour les lecteurs d’écran et les autres technologies d’assistance. Vous activez le format PDF accessible en définissant le paramètres d’informations de l’appareil **AccessiblePDF** sur **True**. Consultez [Paramètres d’informations de périphérique PDF](https://docs.microsoft.com/sql/reporting-services/pdf-device-information-settings) et [Modification des paramètres d’informations de périphérique](https://docs.microsoft.com/sql/reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config#changing-device-information-settings).

### <a name="other-improvements"></a>Autres améliorations

- [Amélioration de l’ajout d’une colonne à partir d’exemples](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#addColumnFromExamples)
- [Lien rapide Services de conseil](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#consultingServices)
- [Rapport d’erreurs amélioré](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#errors)
- [Affichage des erreurs précédemment rencontrées](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#viewErrors)

## <a name="october-2017"></a>Octobre 2017

### <a name="power-bi-report-data-sources"></a>Sources de données de rapport Power BI

Les rapports Power BI dans Power BI Report Server peuvent se connecter à diverses sources de données. Vous pouvez importer des données et planifier une actualisation des données, ou les interroger directement à l’aide de DirectQuery ou d’une connexion active à SQL Server Analysis Services. Consultez la liste des sources de données qui prennent en charge l’actualisation planifiée et de celles qui prennent en charge DirectQuery dans « Sources de données de rapport Power BI dans Power BI Report Server ».

### <a name="scheduled-data-refresh-for-imported-data"></a>Actualisation des données planifiée pour des données importées

Dans Power BI Report Server, vous pouvez configurer une actualisation des données planifiée pour tenir les données à jour dans les rapports Power BI avec un modèle incorporé, au lieu d’une connexion active ou de DirectQuery. Avec un modèle incorporé, vous importez les données de sorte qu’elles sont déconnectées de la source de données d’origine. Une mise à jour est nécessaire pour maintenir les données actualisées, et l’actualisation planifiée est la méthode appropriée pour cela. Pour en savoir plus, lisez « Actualisation planifiée pour les rapports Power BI dans Power BI Report Server ».

### <a name="editing-power-bi-reports-from-the-server"></a>Modification des rapports Power BI à partir du serveur

Vous pouvez ouvrir et modifier des fichiers de rapport Power BI (.pbix) à partir du serveur, mais que vous récupérez le fichier d’origine que vous avez chargé.  Cela signifie que **si les données ont été actualisées par le serveur, elles ne sont pas actualisées lorsque vous ouvrez le fichier pour la première fois**. Pour voir la modification, vous devez actualiser le fichier manuellement localement.

### <a name="large-file-uploaddownload"></a>Chargement/téléchargement de fichier volumineux

Vous pouvez charger des fichiers jusqu’à une taille de 2 Go, bien que, par défaut, cette limite soit fixée à 1 Go dans les paramètres du serveur de rapports dans SQL Server Management Studio (SSMS).  Ces fichiers sont stockés dans la base de données, comme ils le sont sur SharePoint, et aucune configuration particulière du catalogue SQL Server d’est requise.  

### <a name="accessing-shared-datasets-as-odata-feeds"></a>Accès à des Jeux de données partagés en tant que flux OData

Vous pouvez accéder à des jeux de données partagés à partir de Power BI Desktop avec un flux OData. Pour plus d’informations, voir [Accès à des jeux de données partagés en tant que flux OData dans Power BI Report Server](access-dataset-odata.md).

### <a name="scale-out"></a>Montée en puissance parallèle

Cette version prend en charge la montée en puissance parallèle. Pour une expérience optimale, utilisez un équilibreur de charge et définissez l’affinité du serveur. Notez que, le scénario n’étant pas encore optimisé pour la montée en puissance parallèle, vous allez voir des modèles potentiellement répliqués sur plusieurs nœuds. Le scénario fonctionne sans équilibreur de charge réseau et sessions rémanentes. Toutefois, outre une surutilisation de la mémoire sur les nœuds résultant du fait que le modèle est chargé plusieurs fois, vous allez constater que les performances ralentissent entre les connexions pendant la diffusion en continu du modèle, quand celui-ci atteint un nouveau nœud entre des demandes.  

### <a name="administrator-settings"></a>Paramètres administrateur

Les administrateurs peuvent définir les propriétés suivantes dans les propriétés avancées de SSMS pour la batterie de serveurs :

* EnableCustomVisuals : True/False
* EnablePowerBIReportEmbeddedModels : True/False
* EnablePowerBIReportExportData : True/False
* MaxFileSizeMb : la valeur par défaut est désormais 1000
* ModelCleanupCycleMinutes : fréquence de vérification pour la suppression de modèles de la mémoire
* ModelExpirationMinutes : durée avant que le modèle expire et soit supprimé, en fonction de l’heure de la dernière utilisation
* ScheduleRefreshTimeoutMinutes : temps que l’actualisation de données peut prendre pour un modèle Par défaut, il s’agit de deux heures.  Il n’existe aucune limite supérieure.

**Fichier de configuration rsreportserver.config**

```
<Configuration>
  <Service>
    <PollingInterval>10</PollingInterval>
    <IsDataModelRefreshService>false</IsDataModelRefreshService>
    <MaxQueueThreads>0</MaxQueueThreads>
  </Service>
</Configuration>
```

### <a name="developer-api"></a>API Développeur

L’API développeur (API REST) introduite pour SSRS 2017 a été étendue pour que Power BI Report Server puisse travailler avec des fichiers Excel et .pbix. Un cas d’usage potentiel consiste à télécharger par programme des fichiers à partir du serveur, à les actualiser, puis à les republier. Il s’agit de la seule façon d’actualiser des classeurs Excel, par exemple, avec des modèles PowerPivot.

Notez qu’il existe une nouvelle API distincte pour les fichiers volumineux, qui sera mise à jour dans la version Power BI Report Server de Swagger. 

### <a name="sql-server-analysis-services-ssas-and-the-power-bi-report-server-memory-footprint"></a>SQL Server Analysis Services (SSAS) et l’encombrement mémoire de Power BI Report Server

Power BI Report Server héberge désormais en interne SQL Server Analysis Services (SSAS). Cela n’est pas spécifique à une actualisation planifiée. Un hébergement SSAS peut étendre considérablement l’encombrement de mémoire du serveur de rapports. Le fichier de configuration AS.ini étant disponible sur les nœuds de serveur, si vous êtes familiarisé avec SSAS, vous pouvez mettre à jour les paramètres, dont la limite maximale de mémoire et la mise en cache sur disque, etc. Pour plus de détails, voir [Propriétés du serveur dans Analysis Services](https://docs.microsoft.com/sql/analysis-services/server-properties/server-properties-in-analysis-services).

### <a name="viewing-and-interacting-with-excel-workbooks"></a>Affichage de classeurs Excel et interaction avec ceux-ci

Excel et Power BI contiennent une panoplie d’outils unique dans ce secteur d’activité. Ensemble, ils permettent aux analystes de collecter, de mettre en forme, d’analyser et d’explorer visuellement leurs données avec beaucoup plus de facilité. Outre l’affichage de rapports Power BI sur le portail web, les utilisateurs professionnels peuvent désormais faire de même avec des classeurs Excel dans Power BI Report Server. Ils disposent ainsi d’un emplacement unique pour publier et consulter leur contenu Microsoft BI en libre-service.

Nous avons publié une [procédure pas à pas montrant comment ajouter Office Online Server (OOS) à votre environnement en préversion Power BI Report Server](excel-oos.md). Les clients titulaires d’un compte de licence en volume peuvent télécharger OOS gratuitement à partir du Centre MVLS et accéder aux fonctionnalités en lecture seule. Une fois configurés, les utilisateurs peuvent interagir avec des classeurs Excel qui :

* n’ont aucune dépendance de source de données externe ;
* disposent d’une connexion active à une source de données SQL Server Analysis Services externe ;
* disposent d’un modèle de données PowerPivot.

### <a name="support-for-new-table-and-matrix-visuals"></a>Prendre en charge des nouveaux visuels de table et de matrice

Power BI Report Server prend désormais en charge les nouveaux visuels de table et de matrice Power BI. Pour créer des rapports avec ces visuels, vous devez disposer d’une version mise à jour de Power BI Desktop pour la préversion d’octobre 2017. Une installation côte à côte avec la version de juin 2017 de Power BI Desktop n’est pas possible. Pour obtenir la dernière version de Power BI Desktop, dans la [page de téléchargement de Power BI Report Server](https://powerbi.microsoft.com/report-server/), sélectionnez **Options de téléchargement avancées**.

## <a name="june-2017"></a>Juin 2017

* Disponibilité générale (GA) de Power BI Report Server.

## <a name="may-2017"></a>Mai 2017

* Disponibilité de Power BI Report Server en version préliminaire
* Possibilité de publier des rapports Power BI localement
  * Prise en charge des visuels personnalisés
  * Prise en charge prochaine des **connexions directes Analysis Services** uniquement, avec plus de sources de données.
  * Application mobile Power BI mise à jour pour afficher des rapports Power BI hébergés dans Power BI Report Server
* Collaboration améliorée dans les rapports avec des commentaires

## <a name="next-steps"></a>Étapes suivantes

[Présentation de Power BI Report Server](get-started.md) 
[Manuel de l’administrateur](admin-handbook-overview.md)  
[Installer Power BI Report Server](install-report-server.md)  
[Installer le Générateur de rapports](https://docs.microsoft.com/sql/reporting-services/install-windows/install-report-builder)  
[Télécharger SQL Server Data Tools (SSDT)](http://go.microsoft.com/fwlink/?LinkID=616714)

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)