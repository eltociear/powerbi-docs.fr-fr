---
title: Meilleures pratiques en matière de conception de visuels et de rapports
description: Un article sur les meilleures pratiques en matière de conception de rapports dans Power BI.
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/17/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 7d716c79146a0d53d261dba514aacb8787ca2fa3
ms.sourcegitcommit: 90aa7ea5fcc7cf0fd7f6c3c1efeff5f27e8ef0dd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/20/2019
ms.locfileid: "67299548"
---
# <a name="best-design-practices-for-reports-and-visuals"></a>Meilleures pratiques en matière de conception de visuels et de rapports

Cet article fournit les meilleures pratiques en matière de conception de rapports dans Power BI. Il présente les principes de conception que vous pouvez appliquer à vos rapports et aux pages et visuels qui composent ces rapports. Bon nombre de ces meilleures pratiques s’appliquent également à la conception de tableaux de bord.

> [!NOTE]
> Vous pouvez appliquer les recommandations formulées dans cet article quand et où cela est bénéfique. Pour chaque principe décrit ci-dessous, il existe des raisons généralement valables d’enfreindre les règles.

Nous espérons que cet article vous servira de point de départ, que vous allez appliquer les connaissances acquises à vos propres rapports et visualisations et que vous allez continuer la conversation en rejoignant la [Communauté Power BI Microsoft](http://community.powerbi.com/). La conception de rapports BI et la visualisation sont des sujets brûlants à l’heure actuelle. De nombreux leaders d’opinion, blogueurs et sites Web abordent de manière détaillée la conception de rapports BI. Nous en avons répertorié quelques-uns à la fin de cet article.

> *Nous sommes submergés d’informations, non pas parce qu’elles sont en trop grande quantité, mais parce que nous ne savons pas comment les maîtriser.*
-- Stephen Few

## <a name="a-look-at-the-landscape-and-terminology"></a>Présentation du contexte et de la terminologie

Dans Power BI, un rapport peut contenir une ou plusieurs pages. Toutes ces pages sont collectivement désignées par le terme « rapport ». Les éléments de base du rapport sont les visuels (également appelés visualisations), les images autonomes et les zones de texte. Des points de données individuels aux éléments de rapport et aux pages de rapport elles-mêmes, il existe un nombre illimité d’options de mise en forme.

Voici les points que nous allons aborder dans ce document : planification du rapport, principes de base liés à la conception de rapports, principes de conception visuelle et enfin description des meilleures pratiques en fonction des types de visuel.

Pour obtenir des conseils et des instructions complètes pour créer et utiliser les rapports Power BI, consultez la section [Découvrir Power BI](https://powerbi.microsoft.com/learning/).

## <a name="before-you-build-your-first-visualization-focus-on-requirements"></a>Avant de créer votre première visualisation, concentrez-vous sur la configuration requise

La création d’un rapport commence avant même de créer le premier visuel. Une planification est nécessaire à la production d’un rapport bien constitué. Déterminez avec quelles données vous devez travailler et écrivez les conditions requises associées au rapport. Posez-vous ces questions :

* Quels sont les besoins de mon entreprise ?

* Comment les lecteurs vont-ils utiliser ces données ?

* Qui va utiliser ces données ?

* Quelles décisions le lecteur voudra-t-il prendre en fonction de ce rapport ?

La réponse à ces questions va déterminer votre conception. Chaque rapport raconte une histoire. Assurez-vous que cette histoire correspond aux besoins de l’entreprise. Il peut être tentant d’ajouter des visuels qui montrent des insights spectaculaires, mais si ces insights ne correspondent pas aux besoins de l’entreprise, le rapport sera inutile. En fait, les utilisateurs risquent d’être distraits par ces visuels. En outre, il se peut que les informations nécessaires à la prise de décision ne puissent pas être extraites de ces données. Ce rapport vous servira-t-il à mesurer ce qu’il faut mesurer ?

Vous pouvez utiliser les rapports pour surveiller, découvrir, suivre, prévoir, mesurer, gérer, tester et bien plus encore. Par exemple, votre entreprise a besoin d’un rapport de ventes qui mesure les performances. Vous pouvez alors concevoir un rapport qui examine les ventes actuelles, les compare aux ventes précédentes, effectue une comparaison avec celles des concurrents et inclut des indicateurs de performance clés qui déclenchent des alertes. Les lecteurs peuvent peut-être explorer en détail les chiffres liés aux ventes pour voir les fermetures de magasin ou les problèmes de chaîne d’approvisionnement qui peuvent avoir un impact sur les ventes. Ou ils peuvent examiner en détail les ventes par magasin, région, produit, saison, etc.

Sachez à l’avance les clients auxquels le rapport est destiné. Concevez un rapport qui utilise une terminologie familière et fournit des données à un niveau de détail et de complexité correspondant au niveau de connaissance des clients. Vous avez plusieurs types de client ? Il n’existe pas de rapport « universel ». Concevez des pages de rapport distinctes basées sur votre expertise. Veillez à étiqueter chaque page clairement afin que les clients puissent facilement s’identifier. Une autre option consiste à utiliser des segments afin que les clients puissent adapter la page à leur convenance. Impliquez le client dans la phase de planification et évitez de générer un rapport en vous basant sur ce que vous pensez savoir de ses besoins. Si vous faites une erreur, soyez prêt à recommencer encore et encore.

Une fois que vous avez identifié les besoins de l’entreprise, les clients et les mesures que vous souhaitez inclure, l’étape suivante consiste à choisir les bons visuels permettant de raconter l’histoire. Trouvez une méthode permettant de les présenter de la manière la plus efficace possible. Commençons par quelques principes fondamentaux liés à la conception de rapports.

## <a name="principles-of-report-design"></a>Principes de la conception de rapports

Une page de rapport est un espace limité et le plus difficile est d’intégrer tous les éléments dans cet espace, tout en gardant ces informations compréhensibles. Ne sous-estimez pas non plus la valeur d’un rapport visuellement attrayant. La clé consiste à trouver un équilibre entre un rapport à la fois attrayant et utile.

Jetons un coup d’œil à la disposition, à la clarté et à l’esthétique.

### <a name="layout-of-the-report-canvas"></a>Disposition du canevas de rapport

Le canevas de rapport dispose d’une quantité limitée d’espace. Si tous les éléments ne tiennent pas sur une seule page, scindez le rapport en plusieurs pages. Vous pouvez adapter une page de rapport à un public spécifique (par exemple les ressources humaines, le service informatique, l’équipe commerciale). Si vous le souhaitez, adaptez le rapport à une question métier spécifique :

* « Quel est l’impact des défauts sur nos temps d’arrêt ? »

* « Quel est impact de notre campagne marketing sur le sentiment ? »

Il peut être préférable d’opter pour une histoire progressive. Peut-être avec une première page proposant une vue d'ensemble ou un titre accrocheur qui attire l'attention, une deuxième page qui poursuit l'histoire des données, une troisième page qui explore plus profondément l'histoire, et ainsi de suite. Si votre rapport entier tient sur une seule page, c’est parfait. Si ce n’est pas le cas, créez des pages de rapport distinctes qui segmentent le contenu de façon logique. N’oubliez pas de donner des noms pertinents et utiles aux pages.

Imaginez que vous deviez aménager une galerie d’art. Vous ne placeriez pas 50 œuvres dans un petit espace, rempli de chaises et dont chaque mur est peint d’une couleur différente. En tant que galeriste, choisissez uniquement les œuvres qui ont un thème commun. Vous devez les disposer autour de la pièce avec suffisamment d'espace pour que les visiteurs puissent se déplacer et observer les œuvres présentées. Vous pouvez même placer des fiches d'information qui décrivent ce qu’ils contemplent. Il y a bien une raison pour laquelle les galeries les plus modernes ont des murs nus !

Pour cet article, nous allons commencer par un exemple de rapport nécessitant beaucoup de travail. Nous allons ensuite améliorer ce rapport en appliquant nos meilleures pratiques et principes de conception.

![Une horrible page de rapport qui demande beaucoup de travail](media/power-bi-visualization-best-practices/power-bi-example1newa.png)

**Figure 1 : Une horrible page de rapport qui demande beaucoup de travail**

L’exemple ci-dessus présente plusieurs problèmes de conception (disposition) liés à l’espace dont nous allons discuter ci-dessous :

* alignement, ordre et utilisation de la proximité

* mauvaise utilisation de l’espace et du tri

* encombrement

### <a name="alignment-order-and-proximity"></a>Alignement, ordre et proximité

La disposition de vos éléments de rapport a un impact sur la compréhension du lecteur et le guide dans la lecture de la page de rapport. La façon dont vous placez et positionnez les éléments raconte une histoire, par exemple « Démarrez ici puis dirigez-vous ici » ou « ces trois éléments sont liés entre eux ».

* Dans de nombreuses cultures, les personnes lisent de gauche à droite et de haut en bas. Placez l’élément le plus important dans le coin supérieur gauche de votre rapport. Organisez le reste des visuels d’une manière qui aboutit à une navigation logique et à la compréhension des informations.

* Positionnez les éléments qui nécessitent un choix de la part du lecteur à gauche des visualisations sur lesquelles le choix aura un impact : par exemple les segments.

* Positionnez les éléments liés à proximité les uns des autres ; la proximité implique que les éléments sont associés.

* Un autre moyen de traduire les relations consiste à ajouter une bordure ou un arrière-plan en couleur autour des éléments liés. À l’inverse, ajoutez un séparateur pour distinguer les différentes sections d’un rapport.

* Utilisez un espace blanc pour segmenter visuellement des sections de la page de rapport.

* Remplissez la page de rapport. Si vous constatez que vous avez beaucoup trop d’espace blanc, agrandissez vos visualisations ou diminuez la taille du canevas.

* Suivez une intention précise lorsque vous redimensionnez vos éléments de rapport. Ne laissez pas l’espace disponible déterminer la taille d’une visualisation.

* Agrandissez les éléments importants ou ajoutez un visuel, par exemple une flèche, pour attirer l’attention.

* Alignez les éléments sur la page de rapport, soit de manière symétrique soit intentionnellement de façon asymétrique.

Examinons plus en détail l’alignement.

#### <a name="alignment"></a>Alignement

L’alignement ne signifie pas que les différents composants doivent être de la même taille, ou que vous devez disposer du même nombre de composants sur chaque ligne du rapport. Cela signifie simplement que la page a une structure qui facilite la navigation et la lisibilité.

Nous pouvons voir dans notre rapport mis à jour que nous avons aligné les composants du rapport sur les bords gauche et droit. Nous avons également aligné chaque ligne du rapport horizontalement et verticalement. Nos segments sont à gauche des visuels sur lesquels ils ont un impact.

![Notre horrible exemple de rapport amélioré grâce aux modifications apportées à la disposition.](media/power-bi-visualization-best-practices/power-bi-example2new.png)

**Figure 2 : Notre horrible exemple de rapport amélioré grâce aux modifications apportées à la disposition**

Power BI inclut des outils qui vous permettent d’aligner vos visuels. Dans Power BI Desktop, lorsque plusieurs visuels sont sélectionnés, vous pouvez utiliser les options **Aligner** et **Répartir** sous l’onglet du ruban **Outils pour les visuels** pour harmoniser la position des visuels.

![Aligner les visuels dans Power BI Desktop.](media/power-bi-visualization-best-practices/power-bi-visualization.png)

**Figure 3a : Aligner les outils pour les visuels dans Power BI Desktop**

![Aligner les visuels dans Power BI Desktop.](media/power-bi-visualization-best-practices/power-bi-visualization-pbi-service.png)

**Figure 3b : Aligner les outils pour les visuels dans le service Power BI**

Dans le service Power BI et Power BI Desktop, vous pouvez également contrôler avec précision la taille et la position des visuels. Vous trouverez ce contrôle dans l’onglet **Général** du volet **Mise en forme** pour tous les visuels :

![Définir la position exacte d’un visuel.](media/power-bi-visualization-best-practices/power-bi-align-vizs.png)

**Figure 4 : Définir la position exacte d’un visuel**

Dans notre exemple de page de rapport (Figure 2), Power BI aligne les deux cartes et la bordure épaisse sur la **Position X** à 200.

#### <a name="fit-to-the-space"></a>Ajuster à l’espace

Tirez le meilleur parti de l’espace dont vous disposez. Si vous savez de quelle manière les utilisateurs vont afficher et consulter le rapport, gardez cela à l’esprit. Réduisez l’espace vide pour remplir le canevas. Faites votre possible pour éliminer les barres de défilement sur des visuels spécifiques. Remplissez l’espace sans que les visuels semblent collés les uns aux autres.

##### <a name="adjust-the-page-size"></a>Ajuster la taille de la page

En réduisant la taille de la page, des éléments spécifiques deviennent plus volumineux par rapport à la page entière. Désélectionnez des visuels sur la page et utilisez l’onglet **Taille de la page** dans le volet **Mise en forme**.

Voici une page de rapport qui utilise la taille de page **4:3**, puis **16:9**. Notez à quel point la disposition est mieux adaptée au format 16:9. Il y a même suffisamment de place pour supprimer la barre de défilement du deuxième visuel.

![Rapport au format de page 4:3.](media/power-bi-visualization-best-practices/power-bi-page-view-before.png)

**Figure 5a : Rapport au format de page 4:3**

![Rapport au format de page 16:9.](media/power-bi-visualization-best-practices/power-bi-page-view-after.png)

**Figure 5b : Rapport au format de page 16:9**

Les utilisateurs afficheront-ils votre rapport au format 4:3, 16:9 ou autre ? Sur petit ou grand écran ? Sur toutes les tailles et proportions d’écran possibles ? Posez-vous ces questions lors de la conception.

Notre exemple de page de rapport semble quelque peu illisible. Avec aucun visuel sélectionné :

1. Sélectionnez ![Icône Rouleau de peinture du volet Mise en forme.](media/power-bi-visualization-best-practices/power-bi-paint-roller.png) pour ouvrir le volet **Mise en forme**.

1. Développez **Taille de la page**.

1. Pour **Type**, sélectionnez **Personnalisé**.

1. Définissez **Hauteur** sur **900**.

    ![Augmenter la hauteur de page.](media/power-bi-visualization-best-practices/power-bi-page-size.png)

**Figure 6 : Augmenter la hauteur de page**

#### <a name="reduce-clutter"></a>Réduire l’encombrement

Une page de rapport encombrée est difficile à comprendre en un clin d’œil et peut inciter les lecteurs à stopper leur lecture. Supprimez tous les éléments de rapport inutiles. N’ajoutez pas de fonctionnalités qui risquent de nuire à la compréhension ou à la navigation. La page de rapport doit transmettre les informations clairement et de façon aussi cohésive et rapide que possible.

Edward Tufte y fait référence sous le terme « data to ink ratio » (proportion entre la place utilisée par les visuels et l’espace total) dans son livre *The Visual Display of Quantitative Information*. Pour faire simple, supprimez tout ce qui n’est pas indispensable.

La suppression de ces éléments inutiles augmentera l’espace blanc sur la page de rapport. Vous avez ainsi davantage de place pour appliquer les meilleures pratiques abordées dans la section [Alignement, ordre et proximité](#alignment-order-and-proximity).

Notre exemple semble déjà mieux conçu. Nous avons supprimé l’encombrement et ajouté des formes pour regrouper les éléments. L’image d’arrière-plan a disparu, la flèche et la zone de texte inutiles ont disparu, un visuel a été déplacé sur une autre page du rapport, etc. Nous avons augmenté la taille de la page afin d’augmenter l’espace blanc.

![Notre horrible exemple de rapport moins encombré.](media/power-bi-visualization-best-practices/power-bi-example3newer.png)

**Figure 7 : Notre horrible exemple de rapport moins encombré**

### <a name="tell-a-story-at-a-glance"></a>Raconter une histoire en un clin d’œil

Comme preuve que cela fonctionne, une personne sans connaissances préalables doit pouvoir rapidement comprendre le rapport sans qu’une autre personne lui donne des explications. En un coup d’œil, les lecteurs peuvent voir le sujet traité dans chaque page, graphique ou tableau.

Lorsque les lecteurs consultent votre rapport, leurs yeux doivent être attirés par l’élément que vous souhaitez les voir regarder en premier, puis continuer de gauche à droite et de haut en bas. Pour modifier ce comportement, ajoutez des signaux visuels tels que des étiquettes de zone de texte, des formes, des bordures, différentes tailles et couleurs.

#### <a name="text-boxes"></a>Zones de texte

Parfois, les titres des visualisations ne suffisent pas à raconter l’histoire. Ajoutez des zones de texte pour communiquer avec les personnes qui consultent vos rapports. Utilisez des zones de texte pour décrire la page de rapport, un regroupement de visuels ou un visuel spécifique. Elles peuvent expliquer des résultats ou mieux définir un visuel, les composants du visuel ou les relations entre les visuels. Vous pouvez utiliser les zones de texte pour attirer l’attention selon différents critères appelés dans la zone de texte.

Dans la barre de menus supérieure du service Power BI, sélectionnez **Zone de texte**. Dans Power BI Desktop, sélectionnez **Zone de texte** à partir de la zone **Insérer** du ruban.

![Ajouter une zone de texte dans le service Power BI.](media/power-bi-visualization-best-practices/power-bi-text-boxes.png)

**Figure 8 : Ajouter une zone de texte dans le service Power BI**

Entrez le texte dans la zone vide. Puis utilisez les contrôles pour définir la police, la taille, l’alignement et bien plus encore. Utilisez les poignées pour redimensionner la zone.

![Mettre en forme la zone de texte.](media/power-bi-visualization-best-practices/power-bi-text-box-edit.png)

**Figure 9 : Mettre en forme la zone de texte**

N’en abusez pas ! Trop de texte sur un rapport risque de distraire l’attention des visuels. Si vous réalisez que votre page de rapport a besoin de beaucoup de texte pour être plus compréhensible, recommencez depuis le début. Pouvez-vous choisir un visuel différent qui présente par lui-même des informations plus pertinentes ? Pouvez-vous ajuster les titres natifs du visuel pour le rendre plus intelligible ?

#### <a name="text"></a>Texte

Créez un guide de style de texte et appliquez-le à toutes les pages de votre rapport. Choisissez un petit nombre de polices, tailles de texte et couleurs. Appliquez ce guide de style aux éléments textuels. Appliquez-le également aux options de police que vous utilisez dans vos visualisations. Consultez la section [Titres et étiquettes qui font partie des visualisations](#titles-and-labels-that-are-part-of-the-visualizations). Définissez des règles pour l’utilisation du gras, de l’italique, de grandes tailles de police, de couleurs spécifiques, etc. Évitez de tout mettre en majuscules ou souligner.

#### <a name="shapes"></a>Formes

Les formes peuvent également faciliter la navigation et la compréhension. Utilisez des formes pour regrouper des informations connexes, mettez en surbrillance les données importantes et utilisez les flèches pour guider le regard. Les formes permettent aux lecteurs de comprendre où commencer et comment interpréter vos rapports. En termes de conception, on parle souvent de *contraste*.

![Formes dans le service Power BI.](media/power-bi-visualization-best-practices/shapes.png)

**Figure 10a : Formes dans le service Power BI**

![Formes dans Power BI Desktop.](media/power-bi-visualization-best-practices/power-bi-desktop-shapes2new.png)

**Figure 10b : Formes dans Power BI Desktop**

À quoi ressemble notre exemple de page maintenant ? La figure 11 montre une page plus propre et moins encombrée avec une utilisation cohérente de la taille du texte, des polices et des couleurs. Notre titre de page dans le coin supérieur gauche indique de quoi parle la page.

![Notre exemple de rapport après application du guide de style de texte et ajout d’un titre.](media/power-bi-visualization-best-practices/power-bi-example4new.png)

**Figure 11 : Notre exemple de rapport après application du guide de style de texte et ajout d’un titre**

Dans notre exemple, nous avons ajouté un titre de page de rapport dans le coin supérieur gauche, là où le regard des lecteurs se pose en premier. Le texte utilise une taille de police de 28 points et la police Segoe Bold pour le faire ressortir du reste de la page. Notre guide de style de texte recommande de n’utiliser aucun arrière-plan, titre noir, ni aucune légende ou étiquette. Nous avons appliqué cette règle à tous les visuels de la page, dans la mesure du possible (les axes et les étiquettes des graphiques combinés ne sont pas modifiables). En outre, ces éléments ont été configurés selon les spécifications de guide de style :

* Cartes : **Étiquette de catégorie** définie sur **Désactivé**, **Titre** sur **Activé**, avec une police noire centrée de 12 points.

* Titres des visuels : si activés (**On**), ils sont définis sur 12 points et alignés à gauche.

* Segments : **En-tête** est défini sur **Désactivé**, **Titre** est défini sur **Activé**. Laissez **Éléments** > **Texte** en gris et à 10 points.

* Graphiques à nuages de points et histogrammes : police noire pour les axes X et Y, et leurs titres le cas échéant.

#### <a name="color"></a>Couleur

Utilisez la couleur à des fins de cohérence. Nous parlerons plus en détail des couleurs dans la section [Principes liés à la conception de visuels](#principles-of-visual-design). Ici, nous nous concentrons sur une sélection délibérée de couleur. La couleur ne doit pas empêcher vos lecteurs de comprendre rapidement votre rapport. Un trop grand nombre de couleurs vives fait barrage aux sens. Cette section vous présente plutôt ce qu’il est déconseillé de faire avec les couleurs.

#### <a name="backgrounds"></a>Arrière-plans

Lorsque vous définissez les arrière-plans des pages de rapport, choisissez des couleurs qui n’assombrissent pas le rapport, qui ne sont pas en conflit avec d’autres couleurs sur la page ou qui ont un impact négatif visuellement. Notez que certaines couleurs ont une signification intrinsèque. Par exemple, aux États-Unis, le rouge dans un rapport est généralement interprété comme quelque chose de « mauvais ».

![Définir l’arrière-plan du rapport.](media/power-bi-visualization-best-practices/power-bi-page-background.png)

**Figure 12 : Définir l’arrière-plan du rapport**

Vous ne créez pas une œuvre d’art, mais un rapport fonctionnel. Choisissez une couleur qui améliore la lisibilité et la visibilité des éléments du rapport. Une étude sur l'utilisation de la couleur et des visualisations dans les pages Web a révélé qu'un contraste plus élevé entre les couleurs augmente la vitesse de compréhension. Deux livres blancs abordent ce sujet :

* [The effect of text and background color on visual search of Web pages](https://www.sciencedirect.com/science/article/pii/S0141938202000410) (Effet de la couleur du texte et de l'arrière-plan sur la recherche visuelle de pages Web)

* [Determining Users’ Perception of Web Page Visual Complexity and Aesthetic Characteristics](https://www.researchgate.net/publication/301362579_Determining_Users'_Perception_of_Web_Page_Visual_Complexity_and_Aesthetic_Characteristics) (Déterminer la perception qu'ont les utilisateurs de la complexité visuelle et des caractéristiques esthétiques d’une page Web)

Nous avons appliqué quelques pratiques recommandées en matière de couleurs à notre exemple de rapport (Figures 20 et 21). Le plus évident, c’est que nous avons modifié la couleur d’arrière-plan qui est à présent le noir. Le jaune était trop clair et nous faisait mal aux yeux. En outre, sur le graphique **Count of athlete name by year and class** (Nombre d’athlètes par année et par classe), la partie jaune des barres se confond avec l’arrière-plan jaune. L’utilisation d’un arrière-plan noir (ou blanc) apporte un contraste maximal et permet de centrer l’attention sur les visuels.

Voici les étapes supplémentaires que nous avons effectuées pour améliorer l’exemple de rapport :

#### <a name="page-title"></a>Titre de la page

Lorsque nous avons configuré l’arrière-plan en noir, notre titre a disparu, car le champ de zone de texte permet uniquement une police noire. Pour résoudre ce problème, ajoutez un titre de zone de texte à la place :

1. Sélectionnez la zone de texte, puis effacez le texte.

1. Sous l’onglet **Visualisations**, sélectionnez l’option **Titre** et activez-la (**On**).

1. Sélectionnez la flèche pour développer les options **Titre** .

1. Entrez **Jeux olympiques d’été** dans le champ **Texte du titre**.

1. Sélectionnez le blanc dans le champ **Couleur de police**.

    ![Ajouter un titre de page.](media/power-bi-visualization-best-practices/power-bi-text-box-title.png)

    **Figure 13 : Ajouter un titre de page**

#### <a name="cards"></a>Cartes

Pour les visuels de carte :

1. Sélectionnez ![Icône Rouleau de peinture du volet Mise en forme.](media/power-bi-visualization-best-practices/power-bi-paint-roller.png) pour ouvrir le volet **Mise en forme**.

1. Définissez **Arrière-plan** sur **Activé**.

1. Sélectionnez le blanc avec une **transparence** de **0 %** .

    ![Couleurs d’arrière-plan des cartes.](media/power-bi-visualization-best-practices/power-bi-card-background.png)

1. Définissez ensuite **Titre** sur **Activé**.

1. Dans le champ **Couleur de police**, sélectionnez le blanc, et dans le champ **Couleur d’arrière-plan** , sélectionnez le noir.

    ![Couleurs du titre de la carte.](media/power-bi-visualization-best-practices/power-bi-card-title.png)

#### <a name="slicers"></a>Segments

Jusqu’à présent, les deux segments avaient une mise en forme différente, ce qui n’avait aucun sens. Pour les deux segments : 

1. Changez la couleur d’arrière-plan en cyan.

    ![Modifier la couleur d’arrière-plan des segments.](media/power-bi-visualization-best-practices/power-bi-slicer-background.png)

    **Figure 14 : Modifier la couleur d’arrière-plan des segments**

    La couleur Cyan est un bon choix, car elle fait partie de la palette de couleurs de la page : vous la retrouvez notamment dans la carte choroplèthe, le compartimentage et l’histogramme.

1. Ajoutez une fine bordure blanche.

    ![Ajouter une bordure au segment.](media/power-bi-visualization-best-practices/power-bi-slicer-outline.png)

    **Figure 15 : Ajouter une bordure au segment**

1. La police grise est difficile à voir à côté du cyan, par conséquent, utilisez du blanc pour la couleur des **éléments**.

    ![Modifier la couleur de police des segments.](media/power-bi-visualization-best-practices/power-bi-slicer-items.png)

    **Figure 16 : Modifier la couleur de police des segments**

1. Pour terminer, sous **Titre**, utilisez le blanc comme **couleur de police** et le noir comme **couleur d’arrière-plan**.

    ![Mettre en forme le titre du segment.](media/power-bi-visualization-best-practices/power-bi-card-formatting.png)

    **Figure 17 : Mettre en forme le titre du segment**

#### <a name="rectangle-shape"></a>Forme de rectangle

Le rectangle a également disparu dans le fond noir. Pour résoudre ce problème :

1. Sélectionnez la forme.

1. Dans le volet **Format de la forme**, définissez **Arrière-plan** sur **Activé**.

    ![Mettre en forme la forme](media/power-bi-visualization-best-practices/power-bi-shape-format.png)

    **Figure 18 : Mettre en forme la forme**

#### <a name="column-charts-bubble-chart-filled-map-and-treemap"></a>Histogrammes, graphique en bulles, carte choroplèthe et treemap

Ajoutez un arrière-plan blanc aux visuels restants sur la page de rapport. Dans le volet **Mise en forme** :

1. Développez l’option **Arrière-plan**.

1. Définissez la **couleur** sur blanc.

1. Définissez la **transparence** sur 0.

    ![Ajouter un arrière-plan blanc aux visualisations restantes.](media/power-bi-visualization-best-practices/power-bi-background.png)

    **Figure 19 : Ajouter un arrière-plan blanc aux visualisations restantes**

Voici à quoi ressemble le rapport une fois remis en forme :

![Notre exemple de rapport après application des meilleures pratiques en matière de couleurs (arrière-plan noir).](media/power-bi-visualization-best-practices/power-bi-example5a.png)

**Figure 20 : Notre exemple de rapport après application des meilleures pratiques en matière de couleurs (arrière-plan noir)**

![Notre exemple de rapport après application des meilleures pratiques en matière de couleurs (arrière-plan blanc)](media/power-bi-visualization-best-practices/power-bi-example5b.png)

**Figure 21 : Notre exemple de rapport après application des meilleures pratiques en matière de couleurs (arrière-plan blanc)**

### <a name="aesthetics"></a>Esthétique

Nous avons déjà évoqué les éléments jouant sur l’esthétique : l’alignement, les couleurs, les polices et l’encombrement. Il existe d’autres meilleures pratiques que nous souhaitons aborder concernant la conception d’un rapport : elles ont trait à l’apparence générale du rapport.

N’oubliez pas que la fonction de votre rapport est de répondre aux besoins de l’entreprise, pas d’être joli. Il est quand même nécessaire de proposer quelque chose de beau, surtout pour faire une première bonne impression. Le consultant Tony Bodoh de Nashville explique « L’émotion se déclenche une demi-seconde avant que la logique entre en action. » Les lecteurs réagissent d’abord au niveau émotionnel, avant de prendre le temps de mieux regarder votre page de rapport. Si votre page semble désorganisée, confuse, non professionnelle, votre lecteur risque de ne jamais découvrir la puissance des informations que vous présentez.

Le blogueur et analyste Wayne Eckerson utilise une excellente analogie. La conception d’un rapport est comme la décoration d’une pièce. Au fil du temps, vous achetez un vase, un canapé, une table et une peinture. Vous aimez chacun de ces éléments. Bien que chaque sélection individuelle fasse sens, collectivement, les objets sont en conflit ou attirent plus ou moins l’attention.

Concentrez-vous sur les éléments suivants :

* Créez une apparence ou un thème que vous appliquez à toutes les pages du rapport.

* Utilisez des images autonomes et d’autres graphiques pour soutenir l’histoire et non la distraire.

* Appliquez toutes les meilleures pratiques décrites jusqu’à présent dans cet article.

## <a name="principles-of-visual-design"></a>Principes liés à la conception de visuels

Nous avons examiné les principes en matière de conception de rapports, et comment organiser les éléments d’un rapport pour que ce dernier soit facile à comprendre. Nous allons maintenant examiner les principes de conception relatifs aux visuels eux-mêmes. Dans la section suivante, nous allons détailler des visuels spécifiques et présenter les meilleures pratiques pour certains types souvent utilisés.

Nous allons provisoirement laisser notre exemple de page de rapport de côté et voir d’autres exemples. Une fois que nous aurons vu les principes liés à la conception de visuels, nous reviendrons à notre exemple de page de rapport et vous appliquerez ce que vous aurez appris. Vous recevrez pour cela des instructions pas à pas.

### <a name="planning--choose-the-right-visual"></a>Planification - Choisir le bon visuel

Il est tout aussi important de planifier chaque visuel que de réfléchir à la conception du rapport avant même de commencer à le créer. Posez-vous la question : « Qu’est-ce que j'essaie de raconter avec ce visuel », puis déterminez le type de visuel qui présentera le mieux ces informations. Vous pouvez afficher la progression d’un cycle de vente sous forme d’histogramme, mais un graphique en entonnoir ou en cascade ne conviendrait-il pas mieux ? Pour faciliter ce processus, consultez la dernière section de cet article, [Types de visuels et meilleures pratiques](#visual-types-and-best-practices). Elle décrit les meilleures pratiques pour certains types de visuels courants. Ne soyez pas surpris si le premier type de visuel que vous choisissez n’est pas au final la meilleure option. Essayez plusieurs types de visuel pour voir lequel est le plus adapté à votre message.

Sachez reconnaître les différences entre les données quantitatives et catégorielles, et quels types de visuel fonctionnent le mieux avec un type de données spécifique. Les données quantitatives sont souvent appelées « mesures » et sont généralement au format numérique. Les données catégoriques sont souvent appelées « dimensions » et peuvent être classées. Ce sujet est traité plus en détail dans la section [Choisir la mesure adéquate](#choose-the-right-measure).

Évitez d’utiliser des types de visuel fantaisistes ou plus complexes sous prétexte que vous voulez rendre votre rapport plus impressionnant. Vous voulez l’option la plus simple pour transmettre votre message. Les graphiques à barres horizontales et les graphiques en courbes transmettent rapidement des informations. Ils sont familiers et pratiques et la plupart des lecteurs les interprètent facilement. Un autre avantage est que la plupart de vos utilisateurs lisent de gauche à droite et de haut en bas, et ils peuvent ainsi analyser et comprendre rapidement ces deux types de graphique.

Est-il nécessaire d’avoir un défilement dans votre visuel pour présenter les informations ? Évitez le défilement dans la mesure du possible. Essayez d’appliquer des filtres et d’utiliser les hiérarchies/explorations ci-dessous. Si ces éléments ne suppriment pas la barre de défilement, essayez avec un autre type de visuel. Si vous ne pouvez pas supprimer le défilement, vos lecteurs toléreront mieux le défilement horizontal que le défilement vertical.

Même si vous choisissez le meilleur visuel pour présenter les informations, vous aurez peut-être encore besoin d’aide pour faire passer le message. C’est là que les étiquettes, titres, menus, couleurs et tailles entrent en jeu. Nous aborderons ces éléments de conception ultérieurement dans la section [Éléments de conception](#design-elements).

### <a name="choose-the-right-measure"></a>Choisir la mesure adéquate

Les informations présentées par votre visuel sont-elles intéressantes ? Ont-elles de l’importance ? Ne créez pas de visuels pour le simple plaisir d’en créer. Peut-être avez-vous pensé que les données présenteraient les informations de façon intéressante, mais ce n’est pas le cas dans les faits. N’hésitez pas à recommencer et à chercher une histoire plus intéressante. Peut-être que l’histoire est la bonne, mais qu’elle doit être mesurée d’une façon différente.

Supposons que vous souhaitiez mesurer la réussite de vos responsables des ventes. Quelles mesures allez-vous utiliser pour cela ? Allez-vous examiner les ventes totales ou le bénéfice total, la croissance par rapport à l’année précédente ou les performances par rapport à un objectif cible ? La vendeuse Catherine a généré le bénéfice le plus élevé. Si vous avez affiché le bénéfice total par vendeur dans un histogramme, cette vendeuse semblera la meilleure par rapport aux autres vendeurs. Si Catherine a un coût des ventes élevé (frais de déplacement, frais d’expédition, coûts de fabrication, etc.), se contenter de regarder les ventes n’est pas la meilleure option.

#### <a name="reflect-reality-dont-distort-reality"></a>Reflétez la réalité/ne la faussez pas

Il est possible de créer un visuel qui déforme la vérité. Il existe un site web où les passionnés partagent les visuels qu’ils considèrent inefficaces. Le dénominateur commun des commentaires est la déception par rapport à la société qui a créé et distribué le visuel en question. Un visuel inefficace envoie le message que l'entreprise n’est pas digne de confiance.

Par conséquent, créez des visuels qui ne déforment pas la réalité de façon intentionnelle et qui ne sont pas manipulés afin de raconter l’histoire que vous aurez choisie. Voici un exemple :

![Graphique présentant une réalité déformée.](media/power-bi-visualization-best-practices/corp-success-distorted.png)

**Figure 22 : Graphique présentant une réalité déformée**

Dans cet exemple, il semble qu’il existe une grande différence entre les quatre sociétés et que CorpB est beaucoup plus efficace que les trois autres. Notez que l’axe X ne commence pas à zéro et que les différences entre les sociétés sont probablement dans la marge d’erreur. Voici les mêmes données avec un axe X qui commence à zéro.

![Graphique réaliste.](media/power-bi-visualization-best-practices/corp-success.png)

**Figure 23 : Graphique réaliste**

Les lecteurs supposent souvent que l’axe X commence à partir de zéro. Si vous décidez de ne pas commencer à partir de zéro, faites-le d’une manière qui ne fausse pas les résultats. Vous pouvez ajouter un repère visuel ou une zone de texte pour signaler l’écart par rapport à la norme.

### <a name="design-elements"></a>Éléments de conception

Une fois que vous avez sélectionné un type et une mesure et créé le visuel, il est temps d’affiner l’affichage pour une efficacité optimale. Cette section couvre les aspects suivants :

* Disposition, espace et taille

* Éléments de texte : étiquettes, annotations, menus, titres

* Tri

* Interaction avec le visuel

* Couleur

#### <a name="tweaking-visuals-for-best-use-of-space"></a>Ajustement des visuels pour une utilisation optimale de l’espace

Si vous tentez de faire tenir plusieurs graphiques dans un rapport, optimisez les proportions entre les graphiques et le contenu écrit pour faire ressortir l’histoire racontée par vos données. Comme mentionné plus haut, Edward Tufte a inventé le terme « data-ink ratio ». L’objectif est de supprimer autant de marques que possible dans un graphique sans altérer la capacité du lecteur à interpréter les données.

Dans le premier groupe de graphiques ci-dessous, il existe des étiquettes redondantes pour les axes : **janvier 2014**, **avril 2014**, et ainsi de suite. Dans les titres, **par date** est répété. Les titres de chaque graphique requièrent également un espace horizontal dédié sur chaque graphique. En supprimant les titres de graphique et en activant les étiquettes d’axes spécifiques, nous supprimons du contenu texte et utilisons l’espace global de façon optimale. Nous pouvons supprimer les étiquettes d’axe des deux graphiques du haut pour réduire le contenu texte et octroyer plus d’espace aux données.

S’il existe des périodes spécifiques que vous souhaitez faire ressortir, vous pouvez dessiner des lignes ou des rectangles derrière tous les graphiques. Cette méthode permet d’attirer l’attention en haut et en bas afin de faciliter la comparaison.

![Avant.](media/power-bi-visualization-best-practices/power-bi-multiples-before.png)

**Figure 24 : Avant**

![Après.](media/power-bi-visualization-best-practices/power-bi-multiples-after.png)

**Figure 25 : Après**

**Pour activer et désactiver les titres des axes**

1. Sélectionnez le visuel pour l’activer.

1. Sélectionnez ![Icône Rouleau de peinture du volet Mise en forme.](media/power-bi-visualization-best-practices/power-bi-paint-roller.png) pour ouvrir le volet **Mise en forme**.

1. Développez les options pour l’**axe X** ou l’**axe Y**.

1. Faites glisser le curseur de l’option **Titre** sur Activé ou Désactivé.

    ![Activer et désactiver les titres des axes.](media/power-bi-visualization-best-practices/power-bi-axis-titles.png)

    **Figure 26 : Activer et désactiver les titres des axes**

##### <a name="to-turn-axis-labels-on-and-off"></a>Pour activer et désactiver les étiquettes des axes

1. Sélectionnez le visuel pour l’activer.

1. Sélectionnez ![Icône Rouleau de peinture du volet Mise en forme.](media/power-bi-visualization-best-practices/power-bi-paint-roller.png) pour ouvrir le volet **Mise en forme**.

1. Des curseurs sont disponibles en regard de l’**axe X** et de l’**axe Y**.

1. Faites glisser le curseur pour activer ou désactiver les étiquettes des axes.

    ![Activer et désactiver les étiquettes des axes.](media/power-bi-visualization-best-practices/power-bi-axis-labels.png)

    **Figure 27 : Activer et désactiver les étiquettes des axes**

    > [!TIP]
    > Vous pouvez par exemple désactiver les étiquettes de l’axe Y si les **étiquettes de données** sont activées.

##### <a name="to-remove-visual-titles"></a>Pour supprimer les titres des visuels

1. Sélectionnez le visuel pour l’activer.

1. Sélectionnez ![Icône Rouleau de peinture du volet Mise en forme.](media/power-bi-visualization-best-practices/power-bi-paint-roller.png) pour ouvrir le volet **Mise en forme**.

1. Faites glisser le curseur de l’option **Titre** sur **Désactivé**.

    ![Supprimer les titres des visuels.](media/power-bi-visualization-best-practices/power-bi-title-off.png)

    **Figure 28 : Supprimer les titres des visuels**

Prenez en compte la façon dont vos lecteurs vont visualiser le rapport. Assurez-vous que vos visuels et le texte sont suffisamment grands et sombres pour être parfaitement lisibles. Si vous avez un visuel proportionnellement plus grand sur la page, les lecteurs peuvent supposer qu’il est le plus important. Placez suffisamment d’espace entre les visuels pour que votre rapport ne soit ni encombré ni déroutant. Alignez vos visuels de façon à diriger les yeux de vos lecteurs.

##### <a name="to-resize-a-visual"></a>Pour redimensionner un visuel

1. Sélectionnez le visuel pour l’activer.

1. Saisissez et faites glisser l’une des poignées pour ajuster la taille.

    ![Redimensionner un visuel.](media/power-bi-visualization-best-practices/power-bi-drag-handles.png)

    **Figure 29 : Redimensionner un visuel**

##### <a name="to-move-a-visual"></a>Pour déplacer un visuel

1. Sélectionnez le visuel pour l’activer.

1. Sélectionnez et maintenez la barre de redimensionnement en haut au centre du visuel

1. Faites glisser le visuel vers son nouvel emplacement.

    ![Déplacer un visuel.](media/power-bi-visualization-best-practices/power-bi-move.png)

    **Figure 30 : Déplacer un visuel**

#### <a name="titles-and-labels-that-are-part-of-the-visualizations"></a>Titres et étiquettes qui font partie des visualisations

Vérifiez que les titres et les étiquettes sont lisibles et explicites. Le texte des titres et des étiquettes doit avoir une taille optimale avec des couleurs qui ressortent. Vous vous souvenez de notre guide de style (voir [Texte](#text) plus haut dans cet article ) ? Limitez le nombre de couleurs et de tailles : des tailles et couleurs trop nombreuses encombrent la page et la rendent peu claire. Envisagez d’utiliser les mêmes couleur et taille de police pour tous les visuels d’une page de rapport. Choisissez également le même alignement pour tous les titres d’une page de rapport.

**Le volet Mise en forme**

Pour chacune des modifications de mise en forme répertoriées ci-dessous, sélectionnez l’icône en forme de rouleau de peinture ![icône de rouleau de peinture pour le volet Mise en forme.](media/power-bi-visualization-best-practices/power-bi-paint-roller.png) pour ouvrir le volet **Mise en forme**.

![Ouvrir le volet Mise en forme.](media/power-bi-visualization-best-practices/power-bi-paintbrush.png)

**Figure 31 : Ouvrir le volet Mise en forme**

Sélectionnez ensuite le visuel pour l’ajuster et vérifiez qu’il est **activé**. Exemples de visuels : **Axe X**, **Axe Y**, **Titre**, **Étiquettes de données** et **Légende**. L’exemple suivant montre l’élément **Titre**.

![Mettre en forme le titre d’un visuel.](media/power-bi-visualization-best-practices/power-bi-title-formatting.png)

**Figure 32 : Mettre en forme le titre d’un visuel**

##### <a name="set-the-text-size"></a>Définir la taille du texte

Vous pouvez ajuster la taille du texte pour les titres et les étiquettes de données, mais pas pour les axes X ou Y ni les légendes. Pour les étiquettes de données en particulier, jouez avec les **unités d’affichage** et le nombre de **décimales**. Vous finirez par trouver le niveau de détail optimal pour l’affichage de votre rapport.

##### <a name="set-the-text-alignment"></a>Définir l’alignement du texte

Vous pouvez choisir un alignement du titre à gauche, à droite ou au centre. Faites votre choix et appliquez ce même paramètre à tous les visuels de la page.

##### <a name="set-the-text-position"></a>Définir la position du texte

Vous pouvez ajuster la position du texte pour certains axes Y et la légende. Selon ce que vous choisissez, procédez de même pour les autres axes Y et légendes sur la page.

##### <a name="set-the-title-and-label-length"></a>Définir la longueur du titre et de l’étiquette

Ajustez la longueur des titres, des titres d’axe, des étiquettes de données et des légendes. Si vous décidez d’afficher un de ces éléments, ajustez la longueur (ainsi que la taille du texte) pour vous assurer que Power BI ne tronquera pas les valeurs :

* Pour **Titre** et **Légende**, le paramètre est **Texte du titre**. Entrez le titre qui apparaîtra sur le visuel.

* Pour **Axe X** et **Axe Y**, le paramètre est **Style**, que vous sélectionnez dans une liste déroulante.

* Pour **Étiquettes de données**, les paramètres sont **Affichage** et **Décimal**. Utilisez la liste déroulante **Affichage** pour sélectionner les unités de mesure : **millions**, **milliers**, **aucun**, **automatique**, etc. Utilisez le champ **Décimal** pour indiquer à Power BI le nombre de décimales à afficher.

##### <a name="set-the-text-color"></a>Définir la couleur du texte

Vous pouvez ajuster la couleur du texte pour les titres, les axes et les étiquettes de données.

#### <a name="titles-and-labels-that-arent-part-of-the-visualizations"></a>Titres et étiquettes qui ne font pas partie des visualisations

Plus haut dans cet article, nous avons évoqué l’ajout de zones de texte aux pages de rapport. Parfois, les titres des visualisations ne suffisent pas à raconter l’histoire. Ajoutez des zones de texte pour communiquer des informations supplémentaires aux lecteurs de vos rapports.

Pour éviter que la page de rapport soit trop encombrée ou peu claire, soyez cohérent dans l’utilisation de l’alignement, de la taille, de la couleur et de la police des zones de texte. Pour modifier le texte dans une zone de texte, sélectionnez celle-ci pour faire apparaître le menu de mise en forme.

![Mettre en forme la police utilisée dans une zone de texte.](media/power-bi-visualization-best-practices/power-bi-text-box-edit.png)

**Figure 33 : Mettre en forme la police utilisée dans une zone de texte**

#### <a name="sorting"></a>Tri

Pour présenter des informations plus rapidement, il est possible de définir l’ordre des visuels. Par exemple, le tri des graphiques à barres dans l’ordre croissant ou décroissant selon la valeur des barres vous permet d’afficher rapidement des informations importantes sans utiliser davantage de place.

Pour trier un graphique :

1. Sélectionnez les points de suspension dans l’angle supérieur droit du graphique.

1. Sélectionnez **Trier**.

1. Choisissez le champ de tri et la direction.

Pour plus d’informations, consultez [Modifier l’ordre de tri d’un visuel](../consumer/end-user-change-sort.md).

#### <a name="chart-interaction-and-interplay"></a>Interaction avec et entre les graphiques

Une des fonctions les plus remarquables de Power BI est la possibilité de modifier la façon dont les graphiques interagissent entre eux. Par défaut, les graphiques bénéficient de la sélection croisée : quand vous sélectionnez un point de données, les données associées des autres graphiques deviennent plus claires et les données non liées s’estompent. Vous pouvez modifier ce comportement et utiliser n’importe quel graphique comme filtre, ce qui vous fait gagner de la place sur votre page. Dans le service Power BI, sélectionnez **Interactions avec l'élément visuel** dans la barre de menus pour effectuer la modification.

![Interactions avec le visuel.](media/power-bi-visualization-best-practices/power-bi-visual-interactions.png)

**Figure 34 : Interactions avec le visuel**

Ensuite, pour chaque visuel de la page, décidez si vous souhaitez que le visuel sélectionné soit utilisé pour filtrer, mettre en surbrillance ou ne rien faire. Vous ne pouvez pas mettre en surbrillance tous les éléments visuels. Pour les visuels qui ne peuvent pas être mis en surbrillance, aucun contrôle de mise en surbrillance n’est disponible. Pour plus d’informations, consultez [Interactions avec un élément visuel dans Power BI](../consumer/end-user-interactions.md).

> [!TIP]
> Il se peut que les lecteurs qui ne connaissent pas Power BI ne se rendent pas compte immédiatement qu’il est possible de sélectionner les rapports et d’interagir avec eux. Ajoutez des zones de texte pour les aider à comprendre les éléments qu’ils peuvent sélectionner pour accéder à d’autres informations.

#### <a name="the-use-of-color-in-visuals"></a>Utilisation des couleurs dans les visuels

Plus haut dans cet article, nous avons vu qu’il est important de prévoir la façon dont vous allez utiliser les couleurs dans un rapport. Cette section aura pour principal sujet l’utilisation de couleurs dans des visuels spécifiques. Les mêmes principes s’appliquent : utilisez des couleurs pour unifier le rapport, accentuer les données importantes et améliorer la compréhension du visuel par le lecteur. L’utilisation d’un trop grand nombre de couleurs différentes peut être une source de distraction. Cela empêche le lecteur de savoir où regarder. Ne sacrifiez pas la compréhension à l’élégance. Ajoutez uniquement des couleurs qui facilitent la compréhension.

> [!TIP]
> Vous devez connaître votre audience et les règles de couleur suivies. Par exemple, aux États-Unis, le vert signifie généralement « bien » et le rouge généralement « mauvais ».

Les sections ci-après couvrent les thèmes suivants :

* Couleur des données

* Couleur des étiquettes de données

* Couleur des valeurs de catégorie

* Couleur des valeurs numériques

##### <a name="use-colors-to-highlight-interesting-data"></a>Utiliser des couleurs pour mettre en surbrillance les données intéressantes

Le plus simple consiste à modifier la couleur d’au moins un point de données pour attirer l’attention sur elle. Dans cet exemple, la couleur change lorsque les jeux Olympiques sont passés d’un cycle de 4 ans à un cycle de 2 ans lors de l’alternance entre les jeux d’été et d’hiver.

![Utiliser la couleur pour raconter une histoire.](media/power-bi-visualization-best-practices/power-bi-data-color.png)

**Figure 35 : Utiliser la couleur pour raconter une histoire**

Vous pouvez modifier les couleurs de point de données à partir de l’onglet **Couleurs des données** du volet **Mise en forme**. Pour personnaliser individuellement chaque point de données, vérifiez que **Afficher tout** est **activé**.

![Définir les couleurs des points de données.](media/power-bi-visualization-best-practices/power-bi-colors.png)

**Figure 36 : Définir les couleurs des points de données**

> [!NOTE]
> Power BI applique un thème par défaut aux visuels de votre rapport. Les concepteurs choisissent les couleurs de thème de façon à proposer diversité et contraste. Pour changer la palette de thèmes par défaut, sélectionnez **Couleur personnalisée**.
>
> ![Choisir une couleur personnalisée.](media/power-bi-visualization-best-practices/power-bi-custom-color.png)
>
> **Figure 37 : Choisir une couleur personnalisée**

Dans Power BI Desktop, vous pouvez même mettre en surbrillance les **valeurs hors norme** ou la section d’une ligne à l’aide d’une deuxième série :

![Utiliser Desktop pour tracer des valeurs hors norme.](media/power-bi-visualization-best-practices/power-bi-outliers.png)

**Figure 38 : Utiliser Power BI Desktop pour tracer des valeurs hors norme**

Ici, les valeurs de la série **Valeurs hors normes** existent uniquement où la température moyenne en août descend en dessous de 60. Pour cela, nous avons créé une colonne calculée DAX à l’aide de cette formule :

```
Outliers = if(Editions[Temp]<60, Editions[Temp], BLANK())
```

Notre exemple comportait trois valeurs hors norme : **1952**, **1956** et **2000**.

##### <a name="colors-for-labels-and-titles"></a>Couleurs des étiquettes et des titres

Parmi toutes les options de mise en forme disponibles, plusieurs endroits permettent d’ajouter une couleur aux titres et légendes. Par exemple, vous pouvez modifier la couleur des titres des axes et des étiquettes de données. Mais soyez prudent. Vous utilisez en général une même couleur pour tous les titres de visuel. Comme pour les autres directrices du présent article, il existe toujours des situations et des raisons d'enfreindre les règles. Si vous décidez d’enfreindre les règles, faites-le à bon escient.

##### <a name="colors-for-categorical-values"></a>Couleurs des valeurs de catégorie

Les graphiques avec une série ont généralement une valeur de catégorie dans la légende. Par exemple, chaque couleur de légende ci-dessous représente une catégorie différente de Pays/Région.

![Couleurs par défaut appliquées.](media/power-bi-visualization-best-practices/power-bi-bubble-color.png)

**Figure 39 : Couleurs par défaut appliquées**

Les concepteurs choisissent les couleurs par défaut que Power BI utilise pour différencier facilement les valeurs de catégorie. Certaines personnes modifient parfois ces couleurs en fonction de la charte de leur entreprise, mais cela peut entraîner des problèmes.

![Couleur appliquée comme teintes d’une même couleur.](media/power-bi-visualization-best-practices/power-bi-bubble-color2.png)

**Figure 40 : Couleur appliquée comme teintes d’une même couleur**

Comme une seule teinte a été utilisée et que l’intensité de la couleur varie, ce visuel donne un faux sentiment d’ordre entre les catégories. Il implique que les bulles plus sombres sont supérieures ou inférieures à une certaine échelle par rapport aux teintes plus claires. Pour ce type de valeur de catégorie, il n’existe normalement pas d’autre choix que l’application d’un ordre alphabétique.

Pour modifier les couleurs par défaut, sélectionnez ![icône Rouleau de peinture du volet Mise en forme.](media/power-bi-visualization-best-practices/power-bi-paint-roller.png) pour ouvrir le volet **Mise en forme**, puis sélectionnez **Couleurs des données**.

##### <a name="colors-for-numerical-values"></a>Couleurs des valeurs numériques

Pour les champs qui présentent un certain ordre inhérent et une valeur numérique, vous pouvez également donner une couleur aux points de données en fonction de la valeur. Colorer des points de données par valeur peut être utile pour afficher la répartition des valeurs sur les données et pour permettre à Power BI d’afficher deux variables sur un même graphique. Dans le graphique suivant, il est clair que, bien que la Chine ait gagné le plus grand nombre de médailles, le Japon et la Thaïlande ont participé à un plus grand nombre de Jeux Olympiques.

![Couleur des points de données en fonction de la valeur.](media/power-bi-visualization-best-practices/power-bi-saturation.png)

**Figure 41 : Couleur des points de données en fonction de la valeur**

Pour créer ce graphique :

1. Sélectionnez le visuel pour l’activer.

1. Sélectionnez ![Icône Rouleau de peinture du volet Mise en forme.](media/power-bi-visualization-best-practices/power-bi-paint-roller.png) pour ouvrir le volet **Mise en forme**.

1. Sélectionnez **Couleurs des données** > option > **Mise en forme conditionnelle** :

    ![Sélectionner la mise en forme conditionnelle.](media/power-bi-visualization-best-practices/power-bi-conditional-formatting.png)

    **Figure 42 : Sélectionner la mise en forme conditionnelle**

1. Ajustez les couleurs dans la boîte de dialogue **Couleur par défaut - *Couleurs des données*** .

    ![Ajuster les couleurs utilisées pour la saturation.](media/power-bi-visualization-best-practices/power-bi-color-controls.png)

    **Figure 43 : Ajuster les couleurs utilisées pour la saturation**

Vous pouvez également utiliser une couleur à mettre en évidence l’écart par rapport à une valeur centrale. Par exemple, mettre les valeurs positives en vert et les valeurs négatives en rouge. Tenez compte des différences culturelles lors de l’attribution de couleurs aux valeurs positives ou négatives. toutes les cultures n’utilisent pas le rouge pour ce qui est mauvais et le vert pour ce qui est bien.

![Couleur mettant en évidence l’écart par rapport à une valeur centrale.](media/power-bi-visualization-best-practices/power-bi-color.png)

**Figure 44 : Couleur mettant en évidence l’écart par rapport à une valeur centrale**

### <a name="principles-of-visual-design--applied-to-example-report-page"></a>Les principes de la conception de visuels appliqués à l’exemple de page de rapport

Nous allons maintenant reprendre les principes de conception des visuels décrits ci-dessus et les appliquer à notre exemple de rapport.

![Notre exemple de rapport (avant).](media/power-bi-visualization-best-practices/power-bi-example5a.png)

**Figure 45 : Notre exemple de rapport (avant)**

![Notre exemple de rapport (après).](media/power-bi-visualization-best-practices/power-bi-example6anew.png)

**Figure 46 : Notre exemple de rapport (après)**

#### <a name="what-did-we-do"></a>Qu’avons-nous fait ?

| Article | Description |
| ---- | ----------- |
| Segment | Nous avons supprimé les espaces des segments en ajoutant un filtre au niveau de la page et en sélectionnant uniquement **Or**, **Argent** et **Bronze**. <br> Nous avons défini **Contrôles de sélection** sur **désactivé** pour **Sélection simple** et **Sélectionner tout**. |
| Bulles | Il y a tellement d’éléments dans la légende qu’ils sortent de l’écran. Nous avons supprimé la légende et activé les **étiquettes de catégorie** à la place. Les clients peuvent survoler les bulles pour afficher les détails.<br> Nous avons raccourci le titre et supprimé « by country region », car cela semble aller de soi. <br> Nous avons **activé** les étiquettes des axes pour faciliter la compréhension du graphique. |
| Carte choroplèthe | Nous avons modifié les **couleurs des données** pour les faire ressortir davantage. <br> Nous avons activé **Divergent** et défini **Minimum** sur rose et **Maximum** sur rouge.
| Treemap | Nous avons supprimé le filtre qui était défini pour les ÉTATS-UNIS uniquement. <br> Nous avons défini les **étiquettes de données** sur une décimale. <br> Le visuel utilisait le champ **Classe** qui n’est pas utile puisqu’il est presque toujours à 33 % pour les 3 médailles : Or, Argent et Bronze. <br> Nous avons sélectionné un autre champ plus intéressant, à savoir le **sexe**. Nous avons défini la catégorie Aquatics sur du bleu et la catégorie Athlétisme sur du gris.
| Graphique à barres supérieur | Nous avons réduit le titre, supprimé les étiquettes de données et désactivé le titre des légendes. <br> Nous avons modifié l’ordre des mots du titre pour qu’il corresponde au graphique ci-dessous.
| Graphique à barres inférieur | Nous avons effectué un tri par année dans l’ordre croissant comme dans le graphique ci-dessus. <br> Nous avons modifié les couleurs pour qu’elles correspondent à la classe. <br> Nous avons modifié le titre. <br> Nous avons désactivé la légende pour donner davantage d’espace aux données. <br> Nous avons désactivé les étiquettes de données. Elles n’apparaîtront pas dans le rapport, car le visuel est trop petit pour que les étiquettes soient lisibles. Elles apparaîtront lorsque le lecteur ouvre le visuel en **Focus**. En savoir plus sur le [mode Focus](../consumer/end-user-focus.md). <br> Nous avons ajouté le **nombre d’événements (distincts)** à **Info-bulles**. Ainsi, quand vous survolez un histogramme empilé, les info-bulles vous indiquent également le nombre d’événements auxquels les personnes ont participé au cours de cette année. |
| Interactions avec l’élément visuel | Nous avons désactivé les interactions pour les deux cartes dans la mesure où nous voulons qu’elles affichent toujours le nombre total de jeux et de sports. |

## <a name="visual-types-and-best-practices"></a>Types de visuels et meilleures pratiques

Power BI fournit de nombreux types de visuels natifs. Ajoutez à cela les visuels personnalisés disponibles auprès de Microsoft et de la communauté Power BI et vous obtenez des options trop nombreuses pour être documentées ici. Examinons quelques-uns des types de visuels natifs les plus utilisés.

### <a name="line-charts"></a>Graphiques en courbes

![Graphique en courbes.](media/power-bi-visualization-best-practices/power-bi-line-chartb.png)

Les graphiques en courbes sont un moyen efficace d’examiner des données au fil du temps. Consulter des données dans les tables n’exploite pas pleinement la vitesse à laquelle nos yeux repèrent les pics, les creux, les cycles et les modèles. L’exemple ci-dessous montre les tendances dans le nombre de médailles distribuées et le nombre d’athlètes qui ont remporté des médailles.

![Graphiques en courbes.](media/power-bi-visualization-best-practices/power-bi-line-chart.png)

**Figure 47 : Graphiques en courbes**

#### <a name="best-practices"></a>Meilleures pratiques

* Lorsque les utilisateurs regardent les graphiques en courbes, la première chose qu’ils voient est la forme de la courbe. Vous avez donc besoin d’un axe X qui rend la courbe explicite, par exemple des catégories de temps et de distribution. Si vous placez des champs de catégorie comme un produit ou une zone géographique sur l’axe X, le graphique en courbes n’est pas intéressant. En effet, la forme de la courbe ne fournit aucune information pertinente.

* Si vous choisissez de placer plusieurs graphiques les uns au-dessous des autres pour faciliter la comparaison entre les séries, comme ceci, alignez l’axe X. Utilisez des filtres pour vous assurer que Power BI affiche la même plage de valeurs. Si vous examinez des plages de dates, vérifiez qu’elles sont identiques. Par exemple, de 1896 à 2012 sur les deux graphiques.

* Utilisez tout l’espace. Si cela est pertinent pour vos données, définissez les points de **début** et de **fin** de l’axe Y pour éliminer l’espace vide en haut et en bas de votre graphique. Cela permet également de mettre en évidence les points de données réels. Pour définir les points de **début** et de **fin** :

  1. Sélectionnez le visuel pour l’activer.

  1. Sélectionnez ![Icône Rouleau de peinture du volet Mise en forme.](media/power-bi-visualization-best-practices/power-bi-paint-roller.png) pour ouvrir le volet **Mise en forme**.
  
  1. Développez la zone **Axe Y** et définissez les points de **début** et de **fin**.
  
      ![Définir les points de début et de fin.](media/power-bi-visualization-best-practices/power-bi-start-end.png)
  
      **Figure 48 : Définir les points de début et de fin**

* L’autre raison pour laquelle vous devez définir explicitement les points de **début** et de **fin** est que vous comparez plusieurs graphiques sur la même page à l’aide du même champ d’axe Y. Par exemple, si vous examinez le nombre total d’événements, et que le nombre d’événements varie au Royaume-Uni de 1 à 70 et en Australie de 1 à 12, les deux graphiques en courbes affichent différents axes Y (Figure 49). Cela rend difficile la comparaison en un clin d’œil. À la place, définissez les graphiques pour qu’ils utilisent la même plage sur l’axe Y (Figure 50).
  
  ![Graphiques en courbes avec différents axes Y.](media/power-bi-visualization-best-practices/power-bi-line-chart2.png)
  
  **Figure 49 : Graphiques en courbes avec différents axes Y**
  
  ![Graphiques en courbes avec des axes Y identiques.](media/power-bi-visualization-best-practices/power-bi-line-chart3.png)
  
  **Figure 50 : Graphiques en courbes avec des axes Y identiques**

Pour plus d’informations, consultez :

* [Personnaliser les propriétés des axes X et Y](power-bi-visualization-customize-x-axis-and-y-axis.md)

* [Line Graphs and Irregular Intervals: An Incompatible Partnership](http://www.perceptualedge.com/articles/visual_business_intelligence/line_graphs_and_irregular_intervals.pdf)

* [Data Visualization 101: Line Charts](http://www.columnfivemedia.com/data-visualization-101-line-charts)

### <a name="bar-and-column-charts"></a>Graphiques à barres et histogrammes

![Graphiques à barres et histogrammes.](media/power-bi-visualization-best-practices/power-bi-bar-chart.png)

Si les graphiques en courbes sont la norme pour consulter les données sur une période écoulée, les graphiques à barres sont la norme pour la recherche d’une valeur spécifique dans différentes catégories. Si vous triez les barres en fonction du nombre, vous voyez immédiatement les premières valeurs et la distribution. Les graphiques à barres horizontales fonctionnent bien avec les étiquettes longues.

![Graphique à barres horizontales.](media/power-bi-visualization-best-practices/power-bi-horizontal-scroll.png)

**Figure 51 : Graphique à barres horizontales**

#### <a name="best-practices"></a>Meilleures pratiques

* Affichez les étiquettes de données pour les valeurs. Cela permet d’identifier plus facilement des valeurs spécifiques. Pour afficher les étiquettes de données : 

  1. Sélectionnez le visuel pour l’activer.

  1. Sélectionnez ![Icône Rouleau de peinture du volet Mise en forme.](media/power-bi-visualization-best-practices/power-bi-paint-roller.png) pour ouvrir le volet **Mise en forme**.
  
  1. Définissez **Étiquettes des données** sur **Activé**.

      ![Activer les étiquettes de données.](media/power-bi-visualization-best-practices/power-bi-data-labels.png)

      **Figure 52 : Activer les étiquettes de données**

* Le graphique à barres ci-dessus est utile pour comparer une mesure par rapport à d’autres mesures à un point unique dans le temps. Alors que le graphique en courbes affichait la tendance au fil du temps, le graphique à barres nous montre la tendance d’une catégorie à un moment précis dans le temps. En un clin d’œil, notre graphique à barres indique que l’Espagne a l’un des pires taux de chômage au monde, soit 24,70 %.

* Lorsqu’un graphique à barres ou un histogramme ne rentre pas dans l’espace alloué, Power BI ajoute des barres de défilement. Lorsque cela est possible, et si c’est judicieux, structurez le visuel et le rapport pour qu’ils affichent l’ensemble du graphique. Le lecteur bénéficiera ainsi une vue d’ensemble de la distribution tout entière. Malheureusement, cela n’est pas possible dans notre exemple, étant donné le nombre important de pays dans le monde.

  Pour limiter les valeurs incluses, il est possible d’utiliser un filtre. Par exemple, ajoutez un filtre **au niveau du visuel** qui indique le pays uniquement si le taux de chômage est supérieur à 20 %.

* Les graphiques à barres et les histogrammes peuvent faire l’objet d’une exploration détaillée (et sauvegardés à nouveau). C’est un excellent moyen de regrouper plus d’informations dans un visuel sans occuper davantage de place. L’exemple ci-dessous possède une hiérarchie Régions > Pays. Double-cliquez sur une barre représentant une région pour explorer en détail les pays qui la composent. Pour plus d’informations sur le mode Exploration, consultez [Mode Exploration pour une visualisation dans Power BI](../consumer/end-user-drill.md).
  
  ![Descendre dans la hiérarchie.](media/power-bi-visualization-best-practices/power-bi-drill.png)
  
  **Figure 53 : Descendre dans la hiérarchie**

Pour plus d’informations sur les graphiques à barres et les histogrammes :

* [Data Visualization 101: Bar Charts](http://blog.newscred.com/article/data-visualization-101-bar-charts)

* [Catalogue de visualisation des données : Graphique à barres](http://www.datavizcatalogue.com/methods/bar_chart.html#.VYV-hY3bLJw)

* [Catalogue de visualisation des données : Graphique à barres multijeu](http://www.datavizcatalogue.com/methods/multiset_barchart.html#.VYV_gI3bLJw)

### <a name="stacked-bar-and-column-charts"></a>Graphiques à barres empilées et histogrammes

![Graphiques à barres empilées.](media/power-bi-visualization-best-practices/power-bi-stacked.png)

Ajoutez une autre dimension à vos graphiques à barres et histogrammes en empilant différentes catégories dans la barre ou la colonne. Le graphique véhicule maintenant des informations sur une tendance générale (basée sur la hauteur et la longueur), et affiche également l’influence des catégories sur cette tendance. Le graphique suivant montre la croissance globale du chiffre d’affaires des meilleures équipes de football au-dessus de 6 milliards en 2014.

![Histogramme empilé](media/power-bi-visualization-best-practices/power-bi-deloite.png)

**Figure 54 : Histogramme empilé**

Cet histogramme empilé nous montre que le **chiffre d’affaires total** augmente au fil du temps et que les catégories **Commercial** et **Broadcasting** augmentent régulièrement au fil du temps, ce qui contribue à l’augmentation globale du chiffre d’affaires. Mais ce graphique ne permet pas de comparer facilement l’impact de chacune des trois catégories entre elles. Par exemple, en quoi la croissance de la catégorie Commercial est-elle comparable à la croissance de la catégorie Broadcasting ou Match Day ? Pour ces données, un graphique en courbes constitue un meilleur choix ou un visuel compagnon.

![Conversion en graphique en courbes.](media/power-bi-visualization-best-practices/power-bi-deloite2.png)

**Figure 55 : Conversion en graphique en courbes**

Dans ce graphique en courbes, il est plus facile de voir que le chiffre d’affaires de la catégorie Commercial a augmenté le plus, suivi par celui de Broadcast et Match Day.

#### <a name="best-practices"></a>Meilleures pratiques

* Comme avec les histogrammes et les à barres, vous avez la possibilité de choisir un affichage horizontal ou vertical. L’affichage horizontal est un meilleur choix si vous avez de longues étiquettes et l’affichage vertical est idéal pour les données de séries chronologiques.

* Évitez d’utiliser des graphiques à barres/histogrammes empilés si vous souhaitez afficher les tendances et d’autres modèles de changement au fil du temps. D’autres graphiques, tels que les graphiques en courbes, sont beaucoup plus efficaces.

* Vous pouvez également baser la distribution sur le volume total ou comme pourcentage d’un total.

* Comme l’a indiqué Stephen Few :

    > *il est difficile de comparer les segments d’un graphique à barres empilées. Si les segments sont organisés côte à côte et ont tous augmenté à partir de la même ligne de référence, il est facile de comparer leurs hauteurs, mais s’ils sont empilés les uns sur les autres, la tâche devient difficile. De plus, bien qu’il soit assez facile de voir comment (le chiffre d’affaires) a évolué d’un mois à l’autre, il est très difficile de voir comment (le chiffre d’affaires) d’autres (catégories) a changé*.

* Les graphiques empilés 100 % sont un bon choix lors de l’utilisation de pourcentages dont le total est égal à 100. Dans l’exemple ci-dessous, nous voyons la distribution de catégorie par équipe. Les pourcentages sont relatifs et nous permettent de visualiser en un clin d’œil les tendances. Le chiffre d’affaires d’Everton provient principalement de la catégorie Broadcasting (plus de 70 %) alors que celui de PSG tire seulement 20 % de son chiffre d’affaires de Broadcasting. Le choix d’un affichage horizontal permet de facilement ajuster les étiquettes d’équipes et de voir l’impact du type de chiffre d’affaires.

  ![Graphique empilé horizontal.](media/power-bi-visualization-best-practices/power-bi-deloite3.png)

  **Figure 56 : Graphique empilé horizontal**

Pour plus d’informations sur les graphiques à barres empilées :

* [Catalogue de visualisation des données : Histogrammes empilés](http://www.datavizcatalogue.com/methods/stacked_bar_graph.html#top)

* [Dans quels cas les graphiques à barres empilées 100 % sont-ils utiles ?](http://www.perceptualedge.com/blog/?p=2239)

### <a name="combo-bar-and-column-charts"></a>Graphiques combinés et histogrammes

![Graphiques combinés.](media/power-bi-visualization-best-practices/power-bi-combo.png)

Dans Power BI, vous pouvez combiner des graphiques en courbes et des histogrammes dans un graphique combiné. Les choix sont les suivants : 

* Graphique en courbes et histogramme empilé 

* Graphique en courbes et histogramme groupé

Gagnez de l’espace sur le canevas en combinant deux visuels en un seul.

Les deux captures d’écran suivantes montrent l’avant et l’après.

![Deux graphiques distincts.](media/power-bi-visualization-best-practices/power-bi-spain-line.png)

 **Figure 57 : Deux graphiques distincts**

Le premier a deux visuels distincts : un histogramme indiquant la population au fil du temps et un graphique en courbes affichant le PIB au fil du temps. Ces graphiques peuvent être regroupés en un graphique combiné, car ils ont un axe X (année) et des valeurs (de 2002 à 2012) identiques. Pourquoi ne pas les combiner afin de comparer ces deux tendances sur un seul visuel ? Combiner ces deux graphiques vous permet de comparer plus rapidement les données.

![Un seul graphique combiné.](media/power-bi-visualization-best-practices/power-bi-spain-combo.png)

 **Figure 58 : Un seul graphique combiné**

La nouvelle page de rapport a un seul visuel constitué d’un histogramme empilé et d’un graphique en courbes. Nous aurions pu facilement créer un visuel constitué d’un graphique en courbes et d’un histogramme groupé. Il est désormais plus facile de rechercher une relation entre les deux tendances. Nous pouvons voir que jusqu’en 2008, la population et le PIB ont suivi une tendance similaire. Mais à partir de 2009, comme la croissance de la population s’écrasait, le PIB était plus volatil.

#### <a name="best-practices"></a>Meilleures pratiques

* Le graphique combiné fonctionne mieux lorsque les deux visuels ont au moins un axe en commun.

* Faites attention aux axes ! Est-ce que votre graphique combiné est facile à lire et à interpréter ? Est-ce qu’il utilise différentes valeurs et plages ? Si l’échelle de l’axe X de l’histogramme est beaucoup plus petite que celle de l’axe Y du graphique en courbes, votre graphique combiné ne sera pas pertinent. Notez la troisième ligne (en cyan) tout en bas.

   ![Graphique en courbes non pertinent.](media/power-bi-visualization-best-practices/power-bi-dual-line.png)

   **Figure 59 : Graphique en courbes non pertinent**

  Par conséquent, votre graphique combiné n’est pas pertinent si votre histogramme et votre graphique en courbes utilisent deux mesures différentes et que vous ne créez pas deux axes. Par exemple, un pour les dollars et un pour les pourcentages. Veillez à inclure deux axes pour que le lecteur puisse comprendre le graphique et envisagez également d’ajouter des étiquettes d’axes.

  Pour créer deux axes :

    1. Sélectionnez le visuel pour l’activer.

    1. Sélectionnez ![Icône Rouleau de peinture du volet Mise en forme.](media/power-bi-visualization-best-practices/power-bi-paint-roller.png) pour ouvrir le volet **Mise en forme**.

    1. Développez **Axe Y** et définissez **Afficher l’élément secondaire** sur **Activé**.

          ![Afficher l’axe secondaire.](media/power-bi-visualization-best-practices/power-bi-show-secondary-new.png)

          **Figure 60 : Afficher l’axe secondaire**

    1. Définissez l’**axe y (colonne)**  > **Titre** sur **Activé**.

    1. Définissez l’**axe y (ligne)**  > **Titre** sur **Activé**.

  Voici à quoi ressemblera le graphique :

  ![Créer un graphique combiné.](media/power-bi-visualization-best-practices/power-bi-combo-chart.png)

  **Figure 61 : Créer un graphique combiné**

* Tirez parti des axes doubles. C’est un bon moyen de comparer plusieurs mesures avec des plages de valeurs différentes. Cela permet d’illustrer la corrélation entre deux mesures dans le même visuel.

Pour plus d’informations :

* [Graphique combiné dans Power BI](power-bi-visualization-combo-chart.md)

* [Double mise à l’échelle des axes dans des graphiques : Est-ce vraiment la meilleure Solution ? ](http://www.perceptualedge.com/articles/visual_business_intelligence/dual-scaled_axes.pdf)

### <a name="scatter-chart"></a>Nuage de points

![Nuage de points](media/power-bi-visualization-best-practices/power-bi-scatter.png)

Nous avons parfois de nombreuses variables à afficher ensemble et un graphique à nuages de points peut être un moyen utile d’obtenir une vue d’ensemble. Les graphiques en nuages de points affichent les relations entre 2 (nuages de point) ou 3 (bulles) mesures quantitatives. Un nuage de points a toujours deux axes de valeur pour afficher un jeu de données numériques sur l’axe horizontal et un autre jeu de valeurs numériques sur l’axe vertical. Le graphique affiche les points à l’intersection d’une valeur numérique x et y, en associant ces valeurs en points de données uniques. Power BI peut distribuer ces points de données uniformément ou non sur l’axe horizontal. Cela varie selon les données.

Un graphique en bulles remplace les points de données par des bulles, la taille de la bulle représentant une dimension supplémentaire des données.

Le graphique en bulles ci-dessous s’intéresse à l’Amérique du Sud et compare le PIB par habitant (axe Y), le PIB total (axe X) et la population par pays d’Amérique du Sud.

![PIB et population d’Amérique du Sud dans un graphique en bulles.](media/power-bi-visualization-best-practices/power-bi-bubble.png)

**Figure 62 : PIB et population d’Amérique du Sud dans un graphique en bulles**

La taille des bulles représente la population totale de ce pays. Le Brésil a la population la plus nombreuse (taille de bulle) et la plus grande portion du PIB de l’Amérique du Sud. Il est situé le plus loin le long de l’axe X. Mais notez que le PIB par habitant de l’Uruguay, du Chili et de l’Argentine est supérieur à celui du Brésil. Ils sont placés le plus haut sur l’axe Y.

Si vous ajoutez un axe de lecture, vous pouvez prétendre être Hans Rosling et raconter l’histoire au fil du temps : [From Data to Insight & Impact: Showing Africa's Progress with Power View and PPI by Microsoft](https://www.youtube.com/watch?v=PbaDBJWCeD4). Pour ajouter un axe de lecture, faites glisser un champ de date/heure dans la zone **Axe de lecture**.

#### <a name="best-practices"></a>Meilleures pratiques

* Les graphiques en nuages de points et les graphiques à bulles sont un excellent moyen de présenter des informations. Mais ils n’ont pas une grande utilité lorsque vous tentez d’explorer des données. C’est ce que Stephen Few souligne dans le paragraphe ci-dessous :

    > *cette approche est puissante lorsqu’elle sert à raconter une histoire. Quand Rosling raconte ce qui se passe dans le graphique lorsque les bulles changent de place et de valeur, en nous montrant ce qu’il veut que nous voyons, les informations prennent vie. Toutefois, les graphiques en bulles animés sont bien moins efficaces pour explorer et donner un sens aux données par soi-même. Je ne pense pas que Rosling utilise cette méthode pour découvrir des histoires, mais seulement pour les raconter une fois qu’elles sont connues. Nous ne pouvons pas regarder plusieurs bulles à la fois lorsqu’elles se déplacent. Nous devons donc exécuter l’animation plusieurs fois pour essayer de comprendre ce qui se passe. Nous pouvons ajouter des pistes aux bulles sélectionnées, ce qui permet de voir la trajectoire complète suivie par ces bulles, mais si vous utilisez les pistes pour plus que quelques bulles, le graphique devient rapidement trop encombré. Fondamentalement, ce que je dis, c’est que ce n’est pas la meilleure façon d’afficher ces informations à des fins d’analyse et d’exploration.*

* Ajoutez des étiquettes aux axes X et Y pour aider à raconter l’histoire. Avec les graphiques en bulles plus particulièrement, il existe de nombreux composants à lire et les étiquettes aident les lecteurs à comprendre le visuel.

* Ajoutez des étiquettes de données pour faciliter l’interprétation du visuel. Avec les graphiques en bulles plus particulièrement, lorsque vous avez plusieurs éléments dans la légende, il peut être difficile de différencier des couleurs similaires. Dans le visuel ci-dessus, les couleurs de légende pour Suriname, Columbia et Ecuador sont similaires.

* Votre nuage de points a-t-il uniquement un point de données qui regroupe toutes les valeurs sur les axes X et Y ? Regroupe-t-il toutes les valeurs le long d’une unique ligne horizontale ou verticale ? Pour résoudre l’agrégation, ajoutez un champ à la zone **Détails** pour indiquer à Power BI comment regrouper les valeurs. Le champ doit être unique pour chaque point à tracer. Pour obtenir de l’aide, reportez-vous au [didacticiel sur l’utilisation des graphiques en bulles et à nuages de points dans Power BI](power-bi-visualization-scatter.md).

### <a name="treemap-charts"></a>Graphiques treemap

![Graphiques treemap.](media/power-bi-visualization-best-practices/power-bi-treemap.png)

Les treemaps peuvent être utiles pour donner une vue d’ensemble de la taille relative de différents composants qui constituent un tout, en particulier lorsque vous pouvez les regrouper par catégories. Dès que vous essayez de comprendre une nouvelle entreprise, un treemap des composants principaux peut être utile pour connaître la distribution globale.

Dans le premier graphique ci-dessous, vous pouvez voir immédiatement que le Brésil génère environ la moitié du PIB de l’Amérique du Sud. Vous constatez également que la Colombie et le Chili ont à peu près la même taille.

Si vous souhaitez avoir un contexte plus large tout en ayant une idée de l’impact des pays qui contribuent le plus, créez des hiérarchies de visuels avec les membres de catégorie (pays) imbriqués au sein de régions. Essentiellement, le deuxième treemap nous donne une idée de la taille relative des régions. Ensuite, dans chaque région, nous pouvons voir quels pays contribuent le plus. Nous voyons qu’il existe trois grandes régions : Europe, Asie et Amérique du Nord. Dans ces régions, nous pouvons facilement voir les principaux pays/régions.

La principale limitation d’un treemap est qu’il est difficile de comparer les rectangles plus petits. Ce type de graphique est adapté aux vues d’ensemble, mais les histogrammes et les graphiques à barres sont probablement un meilleur choix pour avoir une idée plus précise de la taille relative des différents composants.

Le premier treemap donne une indication générale de l’ordre de grandeur du PIB. Mais il est difficile d’identifier les différences spécifiques entre les pays, en particulier les plus petites zones sans étiquette. Pour ces données, dans lesquelles vous comparez un regroupement unique, un histogramme ou graphique à barres peut être un meilleur choix.

![Comparaison du PIB en Amérique du Sud dans un treemap.](media/power-bi-visualization-best-practices/power-bi-treemap3.png)

**Figure 63 : Comparaison du PIB en Amérique du Sud dans un treemap**

Ensuite, nous avons ajouté la région sous la forme d’un autre niveau de données. Nous voyons la contribution globale au PIB par régions. Nous pouvons également voir l’impact relatif dans les régions. Attention : si vous effectuez ceci avec des mesures autres que des sommes (telles que des moyennes), la somme des détails peut ne pas représenter la valeur réelle du niveau d’agrégation.

![PIB par région et par pays dans un treemap.](media/power-bi-visualization-best-practices/power-bi-treemap2.png)

**Figure 64 : PIB par région et par pays dans un treemap**

Pour plus d’informations sur les treemaps :

* [Découverte de Business Intelligence à l’aide de visualisations treemap](http://www.perceptualedge.com/articles/b-eye/treemaps.pdf)

* [Catalogue de visualisation des données : Treemap](http://www.datavizcatalogue.com/methods/treemap.html#.VYhylI3bL7Y)

### <a name="other-charts"></a>Autres graphiques

#### <a name="pie-or-donut-charts"></a>Graphique en secteurs ou en anneau

![Graphique en secteurs ou en anneau](media/power-bi-visualization-best-practices/power-bi-donut.png)

Les graphiques en courbes, à barres et les histogrammes sont l’option idéale dans la plupart des cas. Il est évident que les graphiques en secteurs ou en anneau sont difficiles à interpréter correctement. En fait, ils peuvent souvent déformer les données. Évitez-les autant que possible. Stephen Few raconte très bien l’historique et les dangers dans son article [Save the Pies for Dessert](https://www.perceptualedge.com/articles/08-21-07.pdf).

Il explique le seul cas de figure où les graphiques en secteurs peuvent être utiles : lors de la comparaison de relations entre les parties et un tout. Il est rarement préférable à un graphique à barres empilées à 100 %.

Un autre article (animation) intéressant(e) sur les graphiques en secteurs est disponible sur le [site de Darkhorse Analytics](http://www.darkhorseanalytics.com/blog/salvaging-the-pie).

#### <a name="radial-gauges--kpis"></a>Jauges radiales et indicateurs de performance clés

![Jauges radiales et indicateurs de performance clés.](media/power-bi-visualization-best-practices/power-bi-gauge.png)

Les jauges radiales sont un bon choix de visuel pour indiquer les performances par rapport à une cible. Elles sont populaires dans les tableaux de bord des dirigeants. Elles rencontrent toutefois deux principaux inconvénients. Comme avec les graphiques en secteurs, il est difficile d’interpréter l’angle de la zone ombrée par rapport à la ligne cible ou à l’arc à 180 degrés. Elles utilisent également beaucoup d’espace pour afficher une seule mesure.

Comme alternative, nous vous conseillons d’utiliser un simple visuel montrant un indicateur de performance clé :

![Simple visuel d’indicateur de performance clé (KPI).](media/power-bi-visualization-best-practices/power-bi-kpi.png)

Les indicateurs de performance clés montrent la valeur, l’état, l’objectif, l’écart par rapport à l’objectif et les tendances dans le même espace. La couleur verte devient rouge si les données n’atteignent pas la cible, et peut être jaune si elles atteignent une cible intermédiaire. Ce type de visuel est beaucoup plus simple à lire et à interpréter que la jauge.

Pour plus d’informations, consultez :

* [Graphiques en jauge radiale dans Power BI](power-bi-visualization-radial-gauge-charts.md)

* [Visuels des indicateurs de performance clés](power-bi-visualization-kpi.md)

## <a name="conclusion"></a>Conclusion

Il est maintenant temps de tester ces meilleures pratiques. Gardez le contact et partagez les vôtres. Vous n’êtes pas d’accord avec nos recommandations ou vous avez trouvé une bonne raison d’enfreindre les règles ? Faites-nous part de votre expérience à ce sujet.

D’autres questions ? [Essayez la communauté Power BI](http://community.powerbi.com/)

### <a name="book-recommendations"></a>Recommandations de livres

Il existe plusieurs bons livres qui peuvent aider les équipes à rafraîchir leurs connaissances concernant les techniques de conception de visuels. Nous vous recommandons fortement de lire le livre *Information Dashboard Design* de Stephen Few. Il approfondit le sujet dans deux autres livres : *Show Me the Numbers* et *Now You See It*. Few et d’autres ont trouvé leur inspiration auprès de Edward R. Tufte, dont le livre *The Visual Display of Quantitative Information* est considéré comme un classique dans le secteur. Tufte a également écrit *Visual Explanations*, *Envisioning Information* et *Beautiful Evidence*. Nous vous recommandons également le nouvel ouvrage d’Andy Kirk, *Data Visualization: A Handbook for Data Driven Design*. Voici d’autres auteurs recommandés : Lachlan James, William McKnight et Boris Evelson (Forrester), Darkhorse Analytics.
