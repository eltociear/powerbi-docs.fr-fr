---
title: Nouveautés dans Power BI Report Server
description: Découvrez les nouveautés dans Power BI Report Server. Cet article aborde les principaux domaines de fonctionnalités et est mis à jour à mesure que de nouveaux éléments sont publiés.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 02/27/2020
ms.openlocfilehash: 3ce1ae5207af6f4aaf844679bcd3ae52d2c13819
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83348157"
---
# <a name="whats-new-in-power-bi-report-server"></a>Nouveautés dans Power BI Report Server

Découvrez les nouveautés de Power BI Report Server et de Power BI Desktop optimisé pour Power BI Report Server. Cet article aborde les principaux domaines de fonctionnalités et est mis à jour avec chaque nouvelle version.

Téléchargez [Power BI Report Server et Power BI Desktop optimisé pour Power BI Report Server](https://powerbi.microsoft.com/report-server/).

Pour des informations connexes sur les nouveautés de Power BI, voir :

* [Nouveautés dans le service Power BI](../fundamentals/service-whats-new.md)
* [Nouveautés dans Power BI Desktop](../fundamentals/desktop-latest-update.md)
* [Nouveautés dans les applications mobiles pour Power BI](../consumer/mobile/mobile-whats-new-in-the-mobile-apps.md)

## <a name="january-2020"></a>Janvier 2020

Pour plus d’informations, consultez le billet de blog Power BI Report Server de janvier 2020.

### <a name="power-bi-desktop-optimized-for-power-bi-report-server"></a>Power BI Desktop optimisé pour Power BI Report Server

Cette version offre de nouvelles fonctionnalités, comme la mise en forme conditionnelle des boutons, l’amélioration du profilage des données et d’autres paramètres de mise en forme pour les visuels de type KPI et table. Voici la liste récapitulative des mises à jour :

**Création de rapports**

- Définition d’une colonne de table ou d’une valeur de matrice sous forme d’URL personnalisée
- Paramètres de mise en forme des visuels de type KPI
- Mise à jour de l’expérience du volet de filtrage

**Analytique**

- Boutons de mise en forme conditionnelle
- Chargement de davantage de données pour l’analyse des insights
- Nouvelle fonction DAX : Trimestre

**Préparation des données**

- Amélioration du profilage des données

**Autre**

- Nouveau format de fichier : .pbids
- Amélioration des performances des opérations de modélisation

**Création de rapports**

*Définir une colonne de table ou une valeur de matrice sous forme d’URL personnalisée*

Il est possible de définir une colonne de table ou une valeur de matrice sous forme d’URL personnalisée. Cette nouvelle option est disponible sous la carte Mise en forme conditionnelle dans le volet Mise en forme.

*Paramètres de mise en forme des visuels de type KPI*

Dans la version de ce mois-ci, les indicateurs de performance clés (KPI) ont de nouvelles options de mise en forme :

- Mise en forme du texte de l’indicateur (famille de polices, couleur et alignement)
- Transparence de l’axe de tendance
- Mise en forme du texte des objectifs et des distances (texte de l’étiquette, famille de polices, couleur et taille)
- Mise en forme du texte des distances (texte de l’étiquette, direction positive, famille de polices, couleur et taille)
- Ajout d’une étiquette de date avec mise en forme (famille de polices, couleur et taille)

Il est possible d’ajouter une mise en forme conditionnelle à certaines de ces nouvelles options :

- Couleur de police de l’indicateur
- Couleur de police de l’objectif et de la distance de l’objectif
- Couleurs d’état correct/incorrect/neutre
- Couleur de police de la date

*Mise à jour de l’expérience du volet de filtrage*

Dans le cadre de la disponibilité générale de la nouvelle expérience de filtrage dans la [dernière version](https://powerbi.microsoft.com/blog/power-bi-report-server-september-2019-feature-summary/#filterPane), nous avons simplifié le processus de transition des rapports actuels vers le nouveau volet. Lorsque vous ouvrez Power BI Report Server pour la première fois, une boîte de dialogue de mise à jour automatique du volet de filtrage s’affiche. Ces mises à jour incluent également des bannières dans le serveur de rapports lorsqu’il s’agit de migrer les rapports vers la nouvelle expérience.

**Analytique**

*Mise en forme conditionnelle des boutons*

Ces mises à jour de la mise en forme conditionnelle sont toutes liées aux boutons. Il est désormais possible de définir la mise en forme de manière dynamique pour les propriétés suivantes :

- Couleur de police de texte de bouton
- Texte du bouton
- Couleur de ligne de l’icône
- Couleur du contour
- Couleur de remplissage
- Info-bulle du bouton (sous la carte d’action)

*Chargement de davantage de données pour l’analyse des insights*

Lorsque vous exécutez la fonctionnalité Analyser pour rechercher des insights dans vos données, comme Expliquer l’augmentation, nous n’exécutons les modèles Machine Learning que pendant une période définie pour vous montrer les insights en temps voulu. S’il y a beaucoup de données à analyser, vous pouvez maintenant choisir de continuer à exécuter l’analyse après le délai d’expiration initial.

*Nouvelle fonction DAX : Quarter*

Ce mois-ci, nous proposons une nouvelle fonction DAX, Quarter, qui retourne le trimestre correspondant à une date spécifiée.

**Préparation des données**

*Amélioration du profilage des données*

Ce mois-ci, nous introduisons quelques améliorations significatives de nos fonctionnalités de profilage des données dans l’Éditeur Power Query :

- Plusieurs options de regroupement pour le visuel de répartition des valeurs du volet Profil des colonnes, propres au type de colonne, en plus des critères « par valeur » déjà présents.
- Texte : par longueur du texte (nombre de caractères).
- Numéro : par signe (positif/négatif) et parité (pair/impair).
- Date/DateHeure : par année, mois, jour, semaine de l’année, jour de la semaine, moment de la journée (matin/après-midi) et heure de la journée.
- Et plus encore pour d’autres types de données, par exemple true/false logique.

*Options de filtrage*

Plusieurs critères de regroupement dépendants du type étaient déjà disponibles dans le volet de distribution des profils de colonne. Il est à présent également possible de filtrer dans les légendes de chacune des valeurs du graphe de distribution lorsque des critères de regroupement sont appliqués. Par exemple, dans le volet Profils de données d’une colonne Date/DateHeure, vous pouvez exclure toutes les valeurs qui tombent dans un mois donné.

**Autre**

*Nouveau format de fichier : .pbids*

Ce mois-ci, nous lançons un nouveau format de fichier : .pbids, afin de simplifier l’expérience Obtenir des données pour les créateurs de rapports de votre organisation. Nous recommandons aux administrateurs de créer ces fichiers pour les connexions courantes.

Lorsqu’un créateur de rapport ouvre un fichier .pbids, Power BI Desktop invite à s’authentifier pour se connecter à la source de données spécifiée dans le fichier. L’utilisateur sélectionne ensuite les tables à charger dans le modèle, ainsi que la base de données si le fichier n’en spécifie aucune. Le créateur du rapport peut alors commencer à créer des visualisations.

Pour obtenir plus d’informations et des exemples, consultez la section [Utiliser des fichiers .pbids pour obtenir des données](../connect-data/desktop-data-sources.md#using-pbids-files-to-get-data) de l’article « Sources de données dans Power BI Desktop ».

*Amélioration des performances des opérations de modélisation*

Nous avons effectué une amélioration des performances du moteur Analysis Services pour accélérer les opérations de modélisation, par exemple l’ajout de mesures ou de colonnes calculées et la création de relations. L’ampleur de cette amélioration dépend du modèle, mais nous avons constaté des performances 20 fois meilleures pour certains clients sur des actions comme l’ouverture d’un fichier et l’ajout d’une mesure.

C’est tout pour la version de janvier 2020 de Power BI Report Server. Continuez à envoyer des commentaires et n’oubliez pas de [voter pour les fonctionnalités que vous aimeriez voir dans Power BI](https://ideas.powerbi.com/forums/265200-power-bi).

### <a name="power-bi-report-server"></a>Power BI Report Server

#### <a name="export-to-excel-from-power-bi-reports"></a>Exportation vers Excel à partir de rapports Power BI

L’exportation vers Excel à partir d’un rapport Power BI dans Power BI Report Server fonctionne désormais de la même façon que l’exportation vers Excel à partir d’un rapport Power BI dans le service Power BI. Vous pouvez exporter directement au format Excel. xlsx ; la limite d’exportation est de 150 000 lignes.

#### <a name="azure-sql-managed-instance-support"></a>Prise en charge d’Azure SQL Managed Instance

Il vous est maintenant possible d’héberger un catalogue de base de données utilisé pour Power BI Report Server dans une instance Azure SQL Managed Instance (MI) hébergée dans une machine virtuelle ou dans votre centre de données. La prise en charge est limitée à l’utilisation des informations d’identification de base de données pour la connexion à SQL MI.

#### <a name="power-bi-premium-dataset-support"></a>Prise en charge des jeux de données Power BI Premium

Vous pouvez vous connecter à des jeux de données Power BI à l’aide du Générateur de rapports Microsoft ou de SQL Server Data Tools (SSDT). Vous pouvez ensuite publier ces rapports sur Power BI Report Server à l’aide de la connectivité SQL Server Analysis Services. Les utilisateurs doivent utiliser un nom d’utilisateur et un mot de passe Windows stockés pour rendre possible le scénario.

#### <a name="alttext-alternative-text-support-for-report-elements"></a>Prise en charge d’AltText (texte de remplacement) pour les éléments de rapports

Lors de la création de rapports, vous pouvez vous servir des info-bulles afin de spécifier du texte pour chacun des éléments du rapport. Les technologies de lecteur d’écran utiliseront ces info-bulles.

#### <a name="azure-active-directory-application-proxy-support"></a>Prise en charge du proxy d'application Azure Active Directory

Avec le Proxy d’application Azure Active Directory, vous n’avez plus besoin de gérer votre propre proxy d’application web pour permettre un accès sécurisé via le web ou des applications mobiles. Pour plus d’informations, consultez [Accès à distance à des applications locales via le Proxy d’application Azure Active Directory](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy).

#### <a name="custom-headers"></a>En-têtes personnalisés

Définit des valeurs d’en-tête pour toutes les URL correspondant au modèle regex spécifié. Les utilisateurs peuvent mettre à jour la valeur d’en-tête personnalisé avec du code XML valide pour les URL de demande sélectionnées. Les administrateurs peuvent ajouter autant d’en-têtes qu’ils le souhaitent dans le code XML. Pour plus d’informations, consultez [CustomHeaders](/sql/reporting-services/tools/server-properties-advanced-page-reporting-services#customheaders) dans l’article **Page Propriétés de serveur avancées** de Reporting Services.

#### <a name="transparent-database-encryption"></a>Chiffrement transparent de base de données

Power BI Report Server prend désormais en charge le chiffrement transparent de la base de données du catalogue Power BI Report Server pour les éditions Enterprise et Standard.

#### <a name="power-bi-visuals-api"></a>API des éléments visuels Power BI

La version API expédiée avec cette mise en production est 2.6.

#### <a name="microsoft-report-builder-update"></a>Mise à jour du générateur de rapports Microsoft

La nouvelle version de Générateur de rapports est entièrement compatible avec les versions 2016, 2017 et 2019 de Reporting Services, ainsi qu’avec toutes les versions publiées et prises en charge de Power BI Report Server.

## <a name="september-2019"></a>Septembre 2019

Pour plus d’informations sur toutes les nouvelles fonctionnalités, consultez le billet de blog [Power BI Report Server September 2019](https://powerbi.microsoft.com/blog/power-bi-report-server-september-2019-feature-summary/).

La mise à jour de septembre 2019 de Power BI Report Server inclut un grand nombre de fonctionnalités pour les rapports Power BI. En voici les principales :

- **Filtres au niveau du visuel pour les sélecteurs** : Vous pouvez ajouter aux sélecteurs un filtre au niveau du visuel. Il fonctionne comme n’importe quel autre filtre au niveau du visuel, en filtrant simplement le sélecteur lui-même et aucun autre visuel. Ce filtre est utile pour éliminer les éléments vides ou si vous voulez utiliser des filtres de mesure.
- **Jeux d’icônes pour les tables et les matrices** : Avec les icônes d’indicateur de performance clé, vous pouvez configurer des règles pour montrer différents jeux d’icônes dans votre tableau et votre matrice, de façon similaire aux jeux d’icônes dans Excel.
- **Regroupement de visuels** : Vous pouvez désormais regrouper des visuels, des formes, des zones de texte, des images et des boutons sur une page de rapport, tout comme dans PowerPoint. Quand vous regroupez des objets, vous pouvez les déplacer et les redimensionner tous ensemble. Le regroupement facilite le travail dans un rapport comportant de nombreux objets superposés sur chaque page.
- **Nouveaux thèmes par défaut** : Pour poursuivre avec les nouvelles options JSON des thèmes, nous mettons à jour les thèmes disponibles pour les rapports et nous changeons le thème par défaut pour les nouveaux rapports. Le nouveau thème par défaut est mieux adapté au langage de conception de Microsoft et suit les bonnes pratiques de conception pour les visuels. 
- **Conception des volets mise à jour** : Nous avons rafraîchi une grande partie de notre interface. Nous avons mis à jour tous les volets, le pied de page et le sélecteur de vue avec une couleur plus claire et un espacement mis à jour, et nous avons introduit de nouvelles icônes. La nouvelle conception est la première étape du rafraîchissement de l’intégralité de l’interface.

Voici la liste complète des fonctionnalités. 

### <a name="reporting"></a>Création de rapports

- Conception des volets mise à jour
- Filtres au niveau du visuel pour les sélecteurs
- Tri pour le volet Analyseur de performances
- Info-bulles d’en-tête de visuel
- Personnalisation de l’étiquette du total des tableaux et des matrices
- Prise en charge de la synchronisation des sélecteurs pour le sélecteur de hiérarchie
- Tailles de police cohérentes entre les visuels
- Jeux d’icônes pour les tableaux et les matrices
- Prise en charge des pourcentages pour la mise en forme conditionnelle par des règles
- Nouveau volet Filtrer désormais en disponibilité générale
- Prise en charge des couleurs de données lors de l’utilisation d’un axe de lecture sur des graphiques à nuages de points
- Améliorations des performances lors de l’utilisation des dates relatives et des sélecteurs déroulants
- Regroupement de visuels
- Classes de couleurs et de texte dans les thèmes
- Nouveaux thèmes par défaut

### <a name="analytics"></a>Analytique

- Chaînes de format personnalisées
- Mises à jour de la mise en forme conditionnelle pour les options de mise en forme

    - Couleurs d’arrière-plan et de titre pour les visuels
    - Couleurs des cartes
    - Remplissage et couleurs des jauges
    - Texte de remplacement
    - Couleur de la bordure

- Avertissements concernant la mise en forme conditionnelle
- Amélioration de la découvrabilité de l’extraction
- Nouvelles expressions DAX : REMOVEFILTERS et CONVERT
- Nouvel opérateur de comparaison DAX : ==

### <a name="data-preparation"></a>Préparation des données

- Améliorations apportées à M Intellisense
- Nouvelle transformation : Fractionnement des colonnes par positions
- Copie dans le Presse-papiers à partir d’un profilage de données


## <a name="may-2019"></a>Mai 2019

### <a name="power-bi-desktop-for-power-bi-report-server"></a>Power BI Desktop optimisé pour Power BI Report Server

Pour plus d’informations sur toutes les nouvelles fonctionnalités, consultez le billet de blog [Power BI Report Server May 2019](https://powerbi.microsoft.com/blog/power-bi-report-server-update-may-2019/).

Voici les principales nouveautés de la version :

#### <a name="performance-analyzer"></a>Analyseur de performances 

Si votre rapport s’exécute plus lentement que prévu, essayez l’Analyseur de performances dans Power BI Desktop. Quand vous le démarrez, il crée un fichier journal avec des informations sur chaque action que vous effectuez dans le rapport. Découvrez plus d’informations sur l’[Analyseur de performances](../create-reports/desktop-performance-analyzer.md).

#### <a name="new-modeling-view"></a>Nouvelle vue Modélisation

Dans la nouvelle vue Modélisation de Power BI Desktop, vous pouvez afficher et utiliser des jeux de données complexes qui contiennent de nombreuses tables. Les principales nouveautés sont plusieurs dispositions de diagramme et la modification en bloc de colonnes, de mesures et de tables. Découvrez plus d’informations sur la [vue Modélisation](../transform-model/desktop-modeling-view.md).

#### <a name="accessible-visual-interaction"></a>Interaction visuelle accessible

Vous pouvez maintenant accéder aux points de données sur de nombreux visuels intégrés en utilisant la navigation au clavier. Découvrez plus d’informations sur l’[accessibilité dans les rapports Power BI](../desktop-accessibility.md).

#### <a name="conditional-formatting-titles-and-web-url-actions"></a>Mise en forme conditionnelle des titres et des actions d’URL web

Les rapports Power BI sont interactifs. Il est logique que les titres d’un rapport soient dynamiques, de façon à refléter l’état actuel du rapport. Vous pouvez utiliser la même mise en forme liée à une expression pour rendre dynamiques les URL de vos boutons, de vos formes et de vos images. Découvrez plus d’informations sur les [titres basés sur une expression](../create-reports/desktop-conditional-format-visual-titles.md).

#### <a name="cross-highlight-by-axis-labels"></a>Sélection par étiquettes d’axe

Sélectionnez les étiquettes de catégorie d’axe dans un visuel pour sélectionner les autres éléments d’une page, tout comme vous sélectionnez les points de données dans un visuel. Découvrez plus d’informations sur la [sélection](../create-reports/power-bi-reports-filters-and-highlighting.md#ad-hoc-highlighting).

#### <a name="all-the-new-features"></a>Toutes les nouvelles fonctionnalités

Voici la liste de toutes les nouvelles fonctionnalités :

#### <a name="reporting"></a>Création de rapports

- Sélection d’un point unique dans les graphiques en courbes 
- Retour automatique à la ligne dans les titres 
- Mise à jour de l’interaction avec le visuel par défaut pour le filtrage croisé
- Coins arrondis pour les bordures des visuels 
- Sélecteur avec une seule sélection  
- Prise en charge des cartes thermiques pour Bing Maps  
- Sélection par étiquettes d’axe  
- Mise en forme d’info-bulles par défaut  
- Prise en charge des URL web statiques pour les boutons, les formes et les images  
- Options d’alignement des pages   
- Améliorations du volet de sélection  
- Interaction visuelle accessible  
- Mise en forme conditionnelle pour les titres des visuels  
- Mise en forme conditionnelle pour les actions d’URL web pour les boutons, les formes et les images
- Volet Analyseur de performances
- Navigation avec le clavier dans les tableaux et les matrices
- Contrôle de la position des étiquettes de données sur les lignes
- Contrôle de la taille du texte des indicateurs visuels des KPI

#### <a name="analytics"></a>Analytique

- Affichage des dates sous forme de hiérarchie désormais en disponibilité générale  

#### <a name="modeling"></a>Modélisation

- Nouvelle vue Modélisation maintenant en disponibilité générale
- Nouvelles fonctions DAX
- Mise à jour de la fonction DAX ALLSELECTED
- Désactivation des tableaux de dates automatiques pour les nouveaux rapports

### <a name="power-bi-report-server"></a>Power BI Report Server

#### <a name="support-for-trusted-visuals"></a>Prise en charge des visuels approuvés

Nous avons ajouté la prise en charge des visuels approuvés pour Power BI Report Server. Actuellement, nous prenons en charge les visuels Mapbox et PowerOn. ESRI, Visio et PowerApps ne sont pas pris en charge pour cette version.)

#### <a name="improved-security-features"></a>Fonctionnalités de sécurité améliorées

**RestrictedResourceMimeTypeForUpload**, que les administrateurs peuvent utiliser pour spécifier une liste séparée par des virgules des types MIME interdits, par exemple text/html.

## <a name="january-2019"></a>Janvier 2019

Prise en charge de ces fonctionnalités dans les rapports Power BI :

[**Sécurité au niveau des lignes**](row-level-security-report-server.md) La configuration de la sécurité au niveau des lignes (SNL) avec Power BI Report Server peut restreindre l’accès aux données pour certains utilisateurs. Les filtres limitent l’accès aux données au niveau des lignes, et vous pouvez définir des filtres dans des rôles.

[**Développer et réduire les en-têtes de lignes d’une matrice**](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2018-feature-summary/#expandCollapse) Nous avons ajouté la possibilité de développer et de réduire les en-têtes de lignes d’une matrice, l’une des fonctionnalités les plus demandées pour ce visuel.

[**Faire des copier-coller d’un fichier .pbix à un autre**](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2018-feature-summary/#copyPaste) Vous pouvez copier des visuels d’un fichier .pbix à un autre. Pour cela, utilisez le menu contextuel du visuel ou le raccourci clavier Ctrl+C standard, puis collez le visuel dans un autre rapport avec Ctrl+V.

[**Guides d’alignement intelligents**](https://powerbi.microsoft.com/blog/power-bi-desktop-december-2018-feature-summary/#smartGuides) Comme dans PowerPoint, des guides d’alignement intelligents apparaissent quand vous déplacez des objets dans votre page de rapport pour vous aider à tout aligner. Ces guides s’affichent chaque fois que vous faites glisser ou redimensionnez un élément sur votre page. Quand vous déplacez un objet près d’un autre, il s’aligne avec celui-ci.

**Fonctionnalités d’accessibilité** Elles sont trop nombreuses pour toutes les énumérer ici. Citons par exemple la [prise en charge de fonctionnalités d’accessibilité dans le volet de liste de champs](https://powerbi.microsoft.com/blog/power-bi-desktop-december-2018-feature-summary/#fieldList). Le volet de liste de champs est entièrement accessible. Vous pouvez naviguer dans le volet en utilisant simplement votre clavier et un lecteur d’écran, puis utiliser le menu contextuel pour ajouter des champs à votre page de rapport.

#### <a name="power-bi-visuals"></a>Visuels Power BI

- La version de l’API livrée avec cette mise en production est 2.3.

### <a name="administrator-settings"></a>Paramètres administrateur

Les administrateurs peuvent définir les propriétés suivantes dans les propriétés avancées de SSMS pour la batterie de serveurs :

**AllowedResourceExtensionsForUpload** Définissez les extensions des ressources pouvant être chargées sur le serveur de rapports. Vous n’êtes pas obligé d’inclure des extensions pour les types de fichiers intégrés comme &ast;.rdl et &ast;.pbix. La valeur par défaut est « &ast;, &ast;.xml, &ast;.xsd, &ast;.xsl, &ast;.png, &ast;.gif, &ast;.jpg, &ast;.tif, &ast;.jpeg, &ast;.tiff, &ast;.bmp, &ast;.pdf, &ast;.svg, &ast;.rtf, &ast;.txt, &ast;.doc, &ast;.docx, &ast;.pps, &ast;.ppt, &ast;.pptx ». 

**SupportedHyperlinkSchemes** Définit une liste séparée par des virgules des schémas d’URI autorisés à être définis sur les actions de lien hypertexte dont l’affichage est permis ou « &ast; » pour activer tous les schémas de lien hypertexte. Par exemple, le fait de définir « http, https » autorise les liens hypertextes vers « https://www. contoso.com », mais supprime les liens hypertexte vers « mailto:bill@contoso.com » ou « javascript:window.open('www.contoso.com', '_blank') ». La valeur par défaut est « &ast; ».

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

#### <a name="power-bi-visuals"></a>Visuels Power BI

- La version de l’API livrée avec cette version est 1.13.0.

- Désormais, les visuels Power BI peuvent utiliser comme solution de repli une version antérieure compatible avec la version actuelle de l’API du serveur (si elle est disponible).

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

### <a name="analytics"></a>Analytique

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

#### <a name="rule-based-conditional-formatting-for-table-and-matrix"></a>[Mise en forme conditionnelle basée sur des règles pour les tables et les matrices](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#conditionalFormatting)

Créer des règles pour appliquer de façon conditionnelle une couleur à l’arrière-plan ou à la police d’une colonne, en fonction d’une logique métier spécifique dans votre table ou votre matrice.

#### <a name="show-and-hide-pages"></a>[Afficher et masquer des pages](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#hidePages)

Vous voulez que les lecteurs aient accès à votre rapport, mais certaines des pages ne sont pas encore terminées. Vous pouvez désormais les masquer jusqu’à ce qu’elles soient prêtes. Vous pouvez aussi masquer des pages pour la navigation normale ; les lecteurs peuvent obtenir la page par extraction ou via des signets.

#### <a name="bookmarking"></a>[Signets](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#bookmarking)

Vous pouvez créer des signets pour raconter une histoire avec les données de votre rapport.

- [Sélection croisée pour les signets](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#bookmarkCrossHighlighting) : les signets gèrent et affichent l’état de sélection croisée de la page d’un rapport au moment de la création du signet.
- [Amélioration de la flexibilité des signets](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#bookmarkFlexibility) : les signets reflètent les propriétés définies dans le rapport et affectent seulement les visuels choisis.

#### <a name="multi-select-data-points-across-multiple-charts"></a>[Points de données à sélection multiple entre plusieurs graphiques](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#crosshighlight)

Sélectionnez plusieurs points de données dans plusieurs graphiques et appliquez le filtrage croisé à toute la page.

#### <a name="sync-slicers-across-multiple-pages-of-your-report"></a>[Synchronisation des segments sur plusieurs pages de votre rapport](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#syncSlicers)

Un segment peut s’appliquer à une ou plusieurs pages d’un rapport.

#### <a name="quick-measures"></a>[Mesures rapides](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#quickMeasures) 

Créez des mesures basées sur des mesures existantes et des colonnes numériques dans une table.

#### <a name="drilling-down-filters-other-visuals"></a>[L’exploration filtre d’autres visuels](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#drillFiltersOtherVisuals)

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

### <a name="analytics"></a>Analytique

- [UTCNOW() et UTCTODAY()](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#utcDAX)
- [Marquage d’une table de dates personnalisée](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#customDateTable)
- [Filtres d’exploration d’autres visuels](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#drillFiltersOtherVisuals)
- [Mise en forme au niveau de la cellule pour les modèles AS multidimensionnels pour carte à plusieurs lignes](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#cellLevelFormatting)

### <a name="performance"></a>Performances

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

Vous pouvez ouvrir et modifier des fichiers de rapport Power BI (.pbix) à partir du serveur, mais que vous récupérez le fichier d’origine que vous avez chargé. **Si les données ont été actualisées par le serveur, elles ne seront pas actualisées la première fois que vous ouvrirez le fichier**. Pour voir la modification, vous devez actualiser le fichier manuellement localement.

### <a name="large-file-uploaddownload"></a>Chargement/téléchargement de fichier volumineux

Vous pouvez charger des fichiers jusqu’à une taille de 2 Go, bien que, par défaut, cette limite soit fixée à 1 Go dans les paramètres du serveur de rapports dans SQL Server Management Studio (SSMS).  Ces fichiers sont stockés dans la base de données, comme ils le sont sur SharePoint, et aucune configuration particulière du catalogue SQL Server d’est requise.  

### <a name="accessing-shared-datasets-as-odata-feeds"></a>Accès à des Jeux de données partagés en tant que flux OData

Vous pouvez accéder à des jeux de données partagés à partir de Power BI Desktop avec un flux OData. Pour plus d’informations, voir [Accès à des jeux de données partagés en tant que flux OData dans Power BI Report Server](access-dataset-odata.md).

### <a name="scale-out"></a>Montée en puissance parallèle

Cette version prend en charge la montée en puissance parallèle. Pour une expérience optimale, utilisez un équilibreur de charge et définissez l’affinité du serveur. Le scénario n’étant pas encore optimisé pour le scale-out, il peut y avoir des modèles répliqués sur plusieurs nœuds. Le scénario fonctionne sans équilibreur de charge réseau et sessions rémanentes. Toutefois, outre une surutilisation de la mémoire sur les nœuds résultant du fait que le modèle est chargé plusieurs fois, vous allez constater que les performances ralentissent entre les connexions pendant la diffusion en continu du modèle, quand celui-ci atteint un nouveau nœud entre des demandes.  

### <a name="administrator-settings"></a>Paramètres administrateur

Les administrateurs peuvent définir les propriétés suivantes dans les propriétés avancées de SSMS pour la batterie de serveurs :

* EnableCustomVisuals : Vrai/Faux
* EnablePowerBIReportEmbeddedModels : Vrai/Faux
* EnablePowerBIReportExportData : Vrai/Faux
* MaxFileSizeMb : la valeur par défaut est maintenant 1000
* ModelCleanupCycleMinutes : fréquence de vérification pour la suppression de modèles de la mémoire
* ModelExpirationMinutes : délai avant que le modèle expire et soit supprimé, en fonction de l’heure de la dernière utilisation
* ScheduleRefreshTimeoutMinutes : durée maximale de l’actualisation des données d’un modèle La valeur par défaut est deux heures.  Il n’existe aucune limite supérieure.

**Fichier de configuration rsreportserver.config**

```xml
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

Il existe une nouvelle API distincte pour les fichiers volumineux, qui sera mise à jour dans la version Power BI Report Server de Swagger. 

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
  * Prise en charge des visuels Power BI
  * Prise en charge prochaine des **connexions directes Analysis Services** uniquement, avec plus de sources de données.
  * Application mobile Power BI mise à jour pour afficher des rapports Power BI hébergés dans Power BI Report Server
* Collaboration améliorée dans les rapports avec des commentaires

## <a name="next-steps"></a>Étapes suivantes

Consultez les sources suivantes pour vous tenir au courant des nouvelles fonctionnalités de Power BI Report Server.

* [Blog Microsoft Power BI](https://powerbi.microsoft.com/blog/)
* [Chaîne YouTube Guy in a Cube](https://aka.ms/guyinacube)

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
