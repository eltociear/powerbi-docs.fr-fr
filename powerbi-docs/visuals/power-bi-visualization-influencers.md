---
title: Tutoriel sur les visualisations d’influenceurs clés
description: 'Tutoriel : Créer une visualisation d’influenceurs clés dans Power BI'
author: mihart
manager: kvivek
ms.reviewer: juluczni
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: tutorial
ms.date: 05/22/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: d41fc5991a95b51f71d0db522d4de84454de4ca2
ms.sourcegitcommit: 0332efe8f83cb55a9b8ea011db7c99e9b4568118
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2019
ms.locfileid: "68590599"
---
# <a name="key-influencers-visualization"></a>Visualisation des influenceurs clés
Le visuel d’influenceurs clés vous aide à comprendre les facteurs affectant une métrique qui vous intéresse. Il analyse vos données, classe les facteurs qui sont importants et les affiche sous forme d’influenceurs clés. Par exemple, supposons que vous souhaitez déterminer ce qui influence le renouvellement du personnel. L’un des facteurs peut être la longueur du contrat d’emploi et un autre l’âge de l’employé. 
 
## <a name="when-to-use-key-influencers"></a>Quand utiliser des influenceurs clés 
Le visuel d’influenceurs clés constitue un excellent choix quand vous souhaitez : 
- Voir quels facteurs affectent la métrique en cours d’analyse.
- Comparer l’importance relative de ces facteurs. Par exemple, les contrats à court terme ont-ils plus d’impact sur le renouvellement du personnel que les contrats à long terme ? 

## <a name="key-influencer-requirements"></a>Exigences relatives aux influenceurs clés 
La métrique que vous analysez doit être un champ de catégorie ou numérique (les agrégats et les mesures ne sont pas encore pris en charge).

## <a name="features-of-the-key-influencers-visual"></a>Fonctionnalités du visuel d’influenceurs clés

![Fonctionnalités numérotées](media/power-bi-visualization-influencers/power-bi-ki-numbers-new.png)

1. **Onglets** : sélectionnez un onglet pour changer de vue. **Influenceurs clés** montre les principaux contributeurs à la valeur de métrique sélectionnée. **Top des segments** montre les principaux segments qui contribuent à la valeur de métrique sélectionnée. Un *segment* est composé d’une combinaison de valeurs. Par exemple, un segment peut représenter les consommateurs qui sont clients depuis au moins 20 ans et qui habitent dans la région Ouest. 

2. **Zone de liste déroulante** : valeur de la métrique étudiée. Dans cet exemple, examinez la métrique **Évaluation**. La valeur sélectionnée est **Faible**.

3. **Répétition** : permet d’interpréter le visuel dans le volet gauche.

4. **Volet gauche** : le volet gauche contient un visuel. Ici, le volet gauche montre une liste des principaux influenceurs clés.

5. **Répétition** : permet d’interpréter le visuel dans le volet droit.

6. **Volet droit** : le volet droit contient un visuel. Ici, l’histogramme affiche toutes les valeurs pour l’influenceur clé **Thème** qui est sélectionné dans le volet gauche. La valeur spécifique (**usage**) dans le volet gauche est indiquée en vert. Toutes les autres valeurs pour **Thème** sont en noir.

7. **Ligne moyenne** : la moyenne est calculée pour toutes les autres valeurs possibles pour **Thème** sauf **usage**. Le calcul s’applique donc à toutes les valeurs en noir. Cela indique quel pourcentage des autres **Thèmes** a donné une évaluation faible. Autrement dit, quand une évaluation est donnée par un client, celui-ci décrit également la raison ou le thème de l’évaluation. Les thèmes possibles sont l’usage, la vitesse et la sécurité. 

   **Thème est usage** est le deuxième influenceur clé le plus important pour une évaluation faible, d’après le visuel dans le volet gauche. Si vous faites la moyenne de tous les autres thèmes et de leur contribution à une évaluation **faible**, vous obtenez le résultat apparaissant en rouge. De tous les autres thèmes donnés, seuls 11,35 % sont supérieurs à **usage**.

8. **Case à cocher** : **Afficher uniquement les valeurs qui sont des influenceurs**.

## <a name="create-a-key-influencers-visual"></a>Créer un visuel d’influenceurs clés 
 
Regardez cette vidéo pour apprendre à créer un visuel d’influenceurs clés. Effectuez ensuite ces étapes pour en créer un. 

<iframe width="560" height="315" src="https://www.youtube.com/embed/fDb5zZ3xmxU" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Votre responsable produit vous demande d’identifier les facteurs qui poussent les clients à laisser des avis négatifs sur votre service cloud. Pour suivre la procédure, ouvrez le [fichier PBIX de commentaires client](https://github.com/Microsoft/powerbi-desktop-samples/blob/master/2019/customerfeedback.pbix) dans Power BI Desktop. Vous pouvez également télécharger le [fichier Excel de commentaires client pour le service Power BI ou Power BI Desktop](https://github.com/Microsoft/powerbi-desktop-samples/blob/master/2019/customerfeedback.xlsx). 

> [!NOTE]
> Le jeu de données de commentaires clients est basé sur [Moro et al., 2014] S. Moro, P. Cortez et P. Rita. « A Data-Driven Approach to Predict the Success of Bank Telemarketing. » *Decision Support Systems*, Elsevier, 62:22-31, juin 2014. 

1. Ouvrez le rapport et sélectionnez l’icône **Influenceurs clés**. 

    ![Dans le volet Visualisations, sélectionnez le modèle Influenceurs clés.](media/power-bi-visualization-influencers/power-bi-template-new.png)

2. Déplacez la métrique que vous voulez examiner dans le champ **Analyser**. Le champ **Analyser** prend uniquement en charge les variables catégorielles (ou discontinues). Pour voir les facteurs qui incitent les clients à laisser une évaluation faible, sélectionnez **Table des clients** > **Évaluation**. 
3. Déplacez les champs qui selon vous pourraient influencer **Évaluation** dans le champ **Expliquer par**. Vous pouvez déplacer autant de champs que vous le souhaitez. Dans ce cas, démarrez avec :
    - Pays-Région 
    - Rôle dans l’org 
    - Type d’abonnement 
    - Taille de l’entreprise 
    - Thème 
1. Pour vous concentrer sur les évaluations négatives, sélectionnez **Faible** dans la zone de liste déroulante **Ce qui influence l’évaluation**.  

    ![Sélectionner Faible dans la zone de liste déroulante](media/power-bi-visualization-influencers/power-bi-key-influencers.png)

L’analyse s’exécute au niveau table du champ en cours d’analyse. Dans ce cas, il s’agit de la métrique **Évaluation**. Cette métrique est définie au niveau client. Chaque client a donné un score élevé ou un score faible. Tous les facteurs explicatifs doivent être définis au niveau client pour que le visuel puisse les utiliser. 

Dans l’exemple précédent, tous les facteurs explicatifs ont une relation un-à-un ou plusieurs-à-un avec la métrique. Dans ce cas, chaque score est associé à un thème. Ce thème correspond au thème principal de l’évaluation du client. De même, les clients proviennent d’un pays, ont un type d’appartenance et jouent un rôle dans leur organisation. Les facteurs explicatifs sont déjà des attributs d’un client et aucune transformation n’est nécessaire. Le visuel peut les utiliser immédiatement. 

Plus loin dans le tutoriel, vous examinerez des exemples plus complexes avec des relations un-à-plusieurs. Dans ces cas-là, vous devrez d’abord agréger les colonnes au niveau client avant de pouvoir exécuter l’analyse. 

Les métriques et agrégats utilisés comme facteurs explicatifs sont également évalués au niveau table de la métrique **Analyse**. Vous verrez quelques exemples plus loin dans cet article. 

## <a name="interpret-categorical-key-influencers"></a>Interpréter les influenceurs clés catégoriels 
Jetons un œil aux influenceurs clés pour les évaluations faibles. 

### <a name="top-single-factor-that-influences-the-likelihood-of-a-low-rating"></a>Principal facteur influençant la probabilité d’une évaluation faible

Dans cet exemple, l’organisation a trois rôles : consommateur, administrateur et éditeur. Le fait d’être un consommateur est le principal facteur contribuant à une évaluation faible. 

![Sélectionner Rôle dans l’org est consommateur](media/power-bi-visualization-influencers/power-bi-role-consumer.png)


Plus précisément, vos consommateurs sont 2,57 fois plus susceptibles d’attribuer à votre service un score négatif. Le graphique d’influenceurs clés mentionne **Rôle dans l’org est consommateur** en premier dans la liste sur la gauche. En sélectionnant **Rôle dans l’org est consommateur**, Power BI affiche des détails supplémentaires dans le volet droit. L’effet comparatif de chaque rôle sur la probabilité d’une évaluation faible est indiqué.
  
- 14,93 % des consommateurs attribuent un score faible. 
- En moyenne, tous les autres rôles attribuent un score faible 5,78 % du temps.
- Les consommateurs sont 2,57 fois plus susceptibles d’attribuer un score faible par rapport à tous les autres rôles. Vous pouvez déterminer cela en divisant la barre verte par la ligne rouge en pointillés. 

### <a name="second-single-factor-that-influences-the-likelihood-of-a-low-rating"></a>Deuxième facteur influençant la probabilité d’une évaluation faible

Le visuel d’influenceurs clés compare et classe les facteurs à partir de nombreuses variables différentes. Le deuxième influenceur n’a rien à voir avec **Rôle dans l’org**. Sélectionnez le deuxième influenceur dans la liste, à savoir **Thème est usage**. 

![Sélectionner Thème est usage](media/power-bi-visualization-influencers/power-bi-theme.png)

Le deuxième facteur le plus important est lié au thème de l’évaluation du client. Les clients qui ont commenté l’usage du produit étaient 2,55 fois plus susceptibles d’attribuer un score faible par rapport aux clients ayant commenté d’autres thèmes tels que la fiabilité, la conception ou la vitesse. 

Entre les visuels, la moyenne (ligne rouge en pointillés) est passé de 5,78 % à 11,34 %. La moyenne est dynamique, car elle est basée sur la moyenne de toutes les autres valeurs. Pour le premier influenceur, la moyenne exclut le rôle client. Pour le deuxième influenceur, elle exclut le thème de l’usage. 
 
Cochez la case **Afficher uniquement les valeurs qui sont des influenceurs** pour filtrer en utilisant uniquement les valeurs influentes. Dans ce cas, ils s’agit des rôles qui génèrent un score faible. Sur les douze thèmes, Power BI en retient quatre générant des évaluations faibles. 

![Cocher la case](media/power-bi-visualization-influencers/power-bi-only-show.png)

## <a name="interact-with-other-visuals"></a>Interagir avec d’autres visuels 
 
Chaque fois que vous sélectionnez un segment, un filtre ou un autre visuel sur le canevas, le visuel d’influenceurs clés réexécute son analyse sur la nouvelle portion de données. Par exemple, vous pouvez déplacer **Taille de l’entreprise** dans le rapport et l’utiliser comme segment. Utilisez-le pour voir si les influenceurs clés pour nos clients en entreprise diffèrent de ceux de la population générale. Une grande entreprise est une organisation qui compte plus de 50 000 employés.
 
Sélectionnez **> 50 000** pour réexécuter l’analyse. Vous pouvez alors voir que les influenceurs ont changé. Pour les clients des grandes entreprises, le principal influenceur pour les évaluations faibles a un thème lié à la sécurité. Vous souhaiterez peut-être approfondir vos recherches afin de déterminer s’il existe des fonctionnalités de sécurité spécifiques dont vos clients de grandes entreprises ne sont pas satisfaits. 

![Segment par taille d’entreprise](media/power-bi-visualization-influencers/power-bi-filter.png)

## <a name="interpret-continuous-key-influencers"></a>Interpréter les influenceurs clés continus 
 
Jusqu’à présent, vous avez vu comment utiliser le visuel pour explorer la manière dont différents champs de catégorie influencent les évaluations faibles. Il est également possible d’avoir des facteurs continus tels que l’âge, la hauteur et le prix dans le champ **Expliquer par**. Examinons à présent ce qui se passe si nous déplaçons **Ancienneté** de la table des clients dans **Expliquer par**. L’ancienneté représente depuis combien de temps le client utilise le service. 
 
À mesure que l’ancienneté augmente, la probabilité de recevoir une évaluation plus faible augmente également. Cette tendance suggère que les clients à long terme sont plus susceptibles d’attribuer un score négatif. Cet insight est intéressant et peut faire l’objet d’un suivi par la suite. 
 
La visualisation montre que chaque fois que l’ancienneté augmente de 13,44 mois, en moyenne la probabilité d’une évaluation faible est multipliée par 1,23. Ici, 13,44 mois représente l’écart type pour Ancienneté. Ainsi, l’insight que vous obtenez examine comment le fait d’augmenter l’ancienneté d’une certaine valeur (c’est-à-dire l’écart type pour l’ancienneté) affecte la probabilité de recevoir une évaluation faible. 
 
Le nuage de points dans le volet droit trace le pourcentage moyen d’évaluations faibles pour chaque valeur d’ancienneté. Il met en évidence la pente avec une courbe de tendance.

![Nuage de points pour Ancienneté](media/power-bi-visualization-influencers/power-bi-tenure.png)

## <a name="binned-continuous-key-influencers"></a>Influenceurs clés continus compartimentés

Dans certains cas, vous pouvez constater que vos facteurs continus ont été automatiquement convertis en catégories. Cela est dû au fait que nous avons découvert que la relation entre les variables n’est pas linéaire et que nous ne pouvons pas décrire la relation comme une simple augmentation ou une diminution (comme nous l’avons fait dans l’exemple ci-dessus).

Nous exécutons des tests de corrélation pour déterminer la linéarité de l’influenceur par rapport à la cible. Si la cible est continue, nous exécutons la corrélation Perasons et, si la cible est catégorique, nous exécutons des tests de corrélation du point bisériel. Si nous détectons que la relation n’est pas suffisamment linéaire, nous traitons des compartimentages supervisés et générons un maximum de 5 emplacements. Pour déterminer les emplacements les plus significatifs, nous utilisons une méthode de compartimentage supervisée qui examine la relation entre le facteur explicatif et la cible analysée.

## <a name="interpret-measures-and-aggregates-as-key-influencers"></a>Interpréter les mesures et agrégats comme influenceurs clés 
 
Vous pouvez utiliser des mesures et des agrégats comme facteurs explicatifs dans votre analyse. Par exemple, vous pouvez souhaiter connaître l’impact du nombre de tickets de support client ou de la durée moyenne d’un ticket ouvert sur le score que vous recevez. 
 
Ici, vous voulez voir si le nombre de tickets de support d’un client a un impact sur le score qu’il attribue. Importez à présent l’**ID de ticket de support** à partir de la table de ticket de support. Un client pouvant avoir plusieurs tickets de support, vous agrégez l’ID au niveau client. L’agrégation est importante car l’analyse s’exécute au niveau client, et tous les facteurs doivent donc être définis à ce niveau de granularité. 
 
Examinons le nombre d’ID. Chaque ligne de client est donc associée à un nombre de tickets de support. Ici, à mesure que le nombre de tickets de support augmente, la probabilité de recevoir une évaluation faible est multipliée par 5,51. Le visuel de droite indique le nombre moyen de tickets de support en fonction de différentes valeurs **Évaluation** au niveau client. 

![Influence du nombre d’ID de ticket de support](media/power-bi-visualization-influencers/power-bi-support-ticket.png)


## <a name="interpret-the-results-top-segments"></a>Interprétez les résultats : Top des segments 
 
Vous pouvez utiliser l’onglet **Influenceurs clés** pour évaluer chaque facteur individuellement. Vous pouvez également utiliser l’onglet **Top des segments** pour voir comment une combinaison de facteurs affecte la métrique que vous analysez. 
 
Top des segments montre initialement une vue d’ensemble de tous les segments découverts par Power BI. L’exemple suivant montre que six segments ont été trouvés. Ces segments sont classés en fonction du pourcentage d’évaluations faibles dans le segment. Le segment 1, par exemple, a 74,3 % d’évaluations de client qui sont faibles. Plus la bulle est haute, plus la proportion d’évaluations faibles est élevée. La taille de la bulle représente le nombre de clients inclus dans le segment. 

![Sélectionner l’onglet Top des segments](media/power-bi-visualization-influencers/power-bi-top-segments-tab.png)

La sélection d’une bulle permet d’explorer les détails de ce segment. Si vous sélectionnez par exemple le segment 1, vous observez qu’il est constitué de clients relativement anciens. Ils sont clients depuis plus de 29 mois et ont plus de quatre tickets de support. Pour finir, il ne s’agit pas d’éditeurs (ils sont donc consommateurs ou administrateurs). 
 
Dans ce groupe, 74,3 % des clients ont attribué une évaluation faible. Le client moyen attribue une évaluation faible 11,7 % du temps. Ce segment a donc une proportion nettement plus élevée d’évaluations faibles (63 points de pourcentage en plus). Le segment 1 contient également environ 2,2 % des données. Il représente donc une partie de la population pouvant être identifiée et ciblée. 

![Sélectionner le premier segment principal](media/power-bi-visualization-influencers/power-bi-top-segments2.png)

## <a name="working-with-numerical-data"></a>Utilisation des données numériques

Si vous déplacez un champ numérique dans le champ **Analyser**, vous pouvez choisir comment gérer ce scénario. Pour changer le comportement du visuel, accédez au **volet de mise en forme** et basculez entre le type d’analyse **Catégorie** et le type d’analyse **Continu**.

![Remplacer Catégorie par Continu](media/power-bi-visualization-influencers/power-bi-ki-formatting.png)

Un type d’analyse **Catégorie** se comporte comme dans la description ci-dessus. Par exemple, si vous passez en revue les scores d’une enquête allant de 1 à 10, vous pouvez vous poser la question suivante : « Quels sont les facteurs qui contribuent à l’obtention d’un score d’enquête de 1 ? ».

Un type d’analyse **Continu** change la question en question continue. Dans l’exemple ci-dessus, notre nouvelle question serait la suivante : « Quels sont les facteurs qui influent sur l’augmentation ou la diminution des scores d’enquête ? ».

Cette distinction est très utile quand vous avez un grand nombre de valeurs uniques dans le champ que vous analysez. Dans l’exemple ci-dessous, nous allons examiner le prix d’une maison. La question « Quels sont les facteurs qui contribuent à l’obtention d’un prix de 156 214 $ ? » n’a guère d’utilité. Elle est en effet très spécifique, et nous risquons de ne pas avoir suffisamment de données pour en déduire une tendance.

Au lieu de cela, nous pouvons nous poser la question suivante : « Quels sont les facteurs qui influencent l’augmentation du prix d’une maison ? ». Nous pouvons ainsi traiter le prix de la maison comme une plage et non comme une valeur distincte.

![Question numérique](media/power-bi-visualization-influencers/power-bi-ki-numeric-question.png)

## <a name="interpret-the-results-key-influencers"></a>Interprétez les résultats : Influenceurs clés 

Dans ce scénario, nous examinons les facteurs qui influent sur l’augmentation du prix d’une maison. Nous nous intéressons à plusieurs facteurs explicatifs susceptibles d’impacter le prix d’une maison, notamment **Year Built** (année de construction), **KitchenQual** (qualité de la cuisine) et **YearRemodAdd** (année de rénovation). 

Dans l’exemple ci-dessous, nous examinons notre influenceur principal, à savoir une cuisine d’excellente qualité. Les résultats sont très similaires à ceux que nous avons vu quand nous analysions les métriques catégorielles, avec toutefois quelques différences importantes :

- L’histogramme sur la droite s’intéresse aux moyennes plutôt qu’aux pourcentages. Il nous montre donc le prix moyen d’une maison équipée d’une cuisine d’excellente qualité (barre verte) par rapport au prix moyen d’une maison sans une telle cuisine (ligne en pointillés).
- Le chiffre dans la bulle est la différence entre la ligne en pointillés rouge et la barre verte, mais elle est exprimée sous forme d’un nombre (158 490 $) et non d’une probabilité (1,93 fois). Ainsi, en moyenne, les maisons équipées d’une cuisine d’excellente qualité sont presque 160 000 $ plus chères que les maisons sans une telle cuisine.

![Influenceurs de catégorie d’une cible numérique](media/power-bi-visualization-influencers/power-bi-ki-numeric-categorical.png)

Dans l’exemple ci-dessous, nous nous intéressons à l’impact d’un facteur continu (année de rénovation) sur le prix d’une maison. Les différences par rapport à la façon dont nous analysons les influenceurs continus pour les métriques de catégorie sont les suivantes :

-   Le nuage de points dans le volet droit indique le prix moyen d’une maison pour chaque année de rénovation. 
-   La valeur dans la bulle indique dans quelle mesure le prix moyen d’une maison augmente (ici, de 2 870 $) quand l’année de rénovation de la maison augmente de son écart type (dans ce cas, 20 ans).

![Influenceurs continus d’une cible numérique](media/power-bi-visualization-influencers/power-bi-ki-numeric-continuous.png)

Enfin, dans le cas des mesures, nous examinons l’année moyenne de la construction d’une maison. L’analyse ici est la suivante :

-   Le nuage de points dans le volet droit indique le prix moyen d’une maison pour chaque valeur distincte dans la table.
-   La valeur dans la bulle indique dans quelle mesure le prix moyen d’une maison augmente (ici, de 1 350 $) quand l’année moyenne augmente de son écart type (dans ce cas, 30 ans).

![Influenceurs de mesure d’une cible numérique](media/power-bi-visualization-influencers/power-bi-ki-numeric-measures.png)

## <a name="interpret-the-results-top-segments"></a>Interprétez les résultats : Top des segments

Le top des segments pour les cibles numériques montre les groupes pour lesquels le prix de la maison est en moyenne supérieur à celui du jeu de données d’ensemble. Par exemple, nous pouvons voir ci-dessous que le **Segment 1** se compose de maisons où **GarageCars** (capacité du garage en nombre de voitures) est supérieur à 2 et où **RoofStyle** est Hip. Les maisons présentant ces caractéristiques ont un prix moyen de 355 000 $, tandis que la moyenne globale dans les données est de 180 000 $.

![Influenceurs de mesure pour des cibles numériques](media/power-bi-visualization-influencers/power-bi-ki-numeric-segments.png)

## <a name="considerations-and-troubleshooting"></a>Considérations et résolution des problèmes 
 
**Quelles sont les limitations du visuel ?** 
 
Le visuel Influenceur clés présente certaines limitations :

- La requête directe n’est pas prise en charge
- La connexion active à Azure Analysis Services et à SQL Server Analysis Services n’est pas prise en charge
- La publication sur le web n’est pas prise en charge
- .NET Framework 4.6 ou une version ultérieure est requis

![Question numérique](media/power-bi-visualization-influencers/power-bi-ki-numeric-question.png)

**Je reçois une erreur indiquant qu’aucun influenceur ou segment n’a été trouvé. Pourquoi ?** 

![Erreur : aucun influenceur trouvé](media/power-bi-visualization-influencers/power-bi-error1.png)


Cette erreur se produit quand vous avez inclus des champs dans **Expliquer par**, mais qu’aucun influenceur n’a été trouvé. 
- Vous avez inclus la métrique que vous analysiez à la fois dans **Analyser** et dans **Expliquer par**. Supprimez-la de **Expliquer par**. 
- Vos champs explicatifs ont trop de catégories avec peu d’observations. La visualisation a donc plus de difficulté à déterminer quels facteurs sont des influenceurs. Il est difficile de généraliser d’après seulement quelques observations. Si vous analysez un champ numérique, vous pouvez passer de l’**analyse par catégorie** à l’**analyse en continu** dans le **volet de mise en forme** sous la carte  **Analyse**.
- Vos facteurs explicatifs ont assez d’observations pour effectuer des généralisations, mais la visualisation n’a trouvé aucune corrélation significative à signaler.
 
**Je reçois une erreur indiquant que la métrique que je suis en train d’analyser n’a pas suffisamment de données pour exécuter l’analyse. Pourquoi ?** 

![Erreur : données insuffisantes](media/power-bi-visualization-influencers/power-bi-not-enough-data.png)

La visualisation examine les tendances des données d’un groupe par rapport à celles d’autres groupes. Par exemple, elle recherche le nombre de clients ayant attribué des évaluations faibles par rapport au nombre de clients ayant attribué des évaluations élevées. Si les données dans votre modèle ont seulement quelques observations, il est difficile de trouver des tendances. Si la visualisation n’a pas suffisamment de données pour trouver des influenceurs significatifs, elle signale que davantage de données sont nécessaires pour exécuter l’analyse. 

Nous recommandons au moins 100 observations pour l’état sélectionné. Dans ce cas, l’état correspond aux clients qui renouvellent leur contrat. Vous avez également besoin d’au moins 10 observations pour les états que vous utilisez à des fins de comparaison. Dans ce cas, l’état de la comparaison correspond aux clients qui ne renouvellent pas leur contrat.

Si vous analysez un champ numérique, vous pouvez passer de l’**analyse par catégorie** à l’**analyse en continu** dans le **volet de mise en forme** sous la carte  **Analyse**.

**Je reçois une erreur indiquant qu’un champ dans *Expliquer par* n’est pas lié de manière unique à la table contenant la métrique que je suis en train d’analyser. Pourquoi ?**
 
L’analyse s’exécute au niveau table du champ en cours d’analyse. Par exemple, si vous analysez les commentaires des clients pour votre service, vous pouvez avoir une table qui indique si un client a donné une évaluation élevée ou faible. Dans ce cas, votre analyse s’exécute au niveau de la table des clients. 

Si vous avez une table associée qui est définie à un niveau plus précis que celle qui contient votre métrique, vous obtenez cette erreur. Voici un exemple : 
 
- Vous analysez ce qui incite les clients à attribuer des évaluations faibles à votre service.
- Vous souhaitez vérifier si l’appareil sur lequel le client consomme votre service influence son évaluation.
- Un client peut consommer le service de plusieurs façons.
- Dans l’exemple suivant, le client 10000000 utilise un navigateur et une tablette pour interagir avec le service.

![Table associée définie à un niveau plus granulaire que celle qui contient votre métrique](media/power-bi-visualization-influencers/power-bi-error2.png)

Si vous essayez d’utiliser la colonne de l’appareil en tant que facteur explicatif, vous recevez l’erreur suivante : 

![Erreur Colonne incorrecte](media/power-bi-visualization-influencers/power-bi-error3.png)

Cette erreur s’affiche parce que l’appareil n’est pas défini au niveau client. Un client peut consommer le service sur plusieurs appareils. Pour que la visualisation trouve des tendances, l’appareil doit être un attribut du client. Il existe plusieurs solutions qui dépendent de votre compréhension de l’entreprise : 
 
- Vous pouvez changer la synthèse des appareils à compter. Par exemple, utilisez le décompte si le nombre d’appareils peut affecter le score attribué par un client. 
- Vous pouvez faire pivoter la colonne de l’appareil pour voir si l’utilisation du service sur un appareil spécifique influence l’évaluation d’un client.
 
Dans cet exemple, les données ont été croisées pour créer de nouvelles colonnes pour les navigateurs, les appareils mobiles et les tablettes (veillez à supprimer et à recréer vos relations dans la vue de modélisation après avoir croisé vos données). Vous pouvez désormais utiliser ces appareils spécifiques dans **Expliquer par**. Tous les appareils sont des influenceurs, le navigateur ayant le plus grand impact sur le score attribué par le client.

Plus précisément, les clients qui n’utilisent pas le navigateur pour consommer le service sont 3,79 fois plus susceptibles d’attribuer un faible score que ceux qui en utilisent un. Plus bas dans la liste, pour « mobile », l’inverse est vrai. Les clients qui utilisent l’application mobile sont plus susceptibles d’attribuer un faible score que ceux qui ne l’utilisent pas. 

![Résolu](media/power-bi-visualization-influencers/power-bi-error3-solution.png)

**Je reçois un avertissement signalant que les mesures n’ont pas été incluses dans mon analyse. Pourquoi ?** 

![Erreur : mesures non incluses](media/power-bi-visualization-influencers/power-bi-measures-not-included.png)


L’analyse s’exécute au niveau table du champ en cours d’analyse. Si vous analysez le taux d’attrition des clients, vous pouvez avoir une table qui indique si un client a renouvelé son contrat ou non. Dans ce cas, votre analyse s’exécute au niveau de la table de clients.
 
Les mesures et agrégats sont par défaut analysés à ce niveau table. S’il y avait une mesure des dépenses mensuelles moyennes, elle serait analysée au niveau de la table des clients. 

Si la table des clients n’a pas d’identificateur unique, vous ne pouvez pas évaluer la mesure et elle est ignorée par l’analyse. Pour éviter cette situation, vérifiez que la table avec votre métrique a un identificateur unique. Dans ce cas, il s’agit de la table de clients et l’identificateur unique est l’ID du client. Vus pouvez également ajouter facilement une colonne d’index à l’aide de Power Query.
 
**Je reçois un avertissement signalant que la mesure que je suis en train d’analyser a plus de 10 valeurs uniques, et que cela peut avoir une incidence sur la qualité de mon analyse. Pourquoi ?** 

La visualisation d’intelligence artificielle peut analyser les champs de catégorie et les champs numériques. Dans le cas des champs de catégorie, vous pouvez avoir par exemple l’attrition (oui ou non) et la satisfaction du client (élevée, moyenne ou faible). L’augmentation du nombre de catégories à analyser signifie qu’il y a moins d’observations par catégorie. Dans cette situation, il est difficile pour la visualisation de trouver des tendances dans les données. 

Quand vous analysez des champs numériques, vous avez l’option de les traiter comme du texte, auquel cas vous exécutez la même analyse que pour des données de catégorie (**analyse par catégorie**). Si vous avez beaucoup de valeurs distinctes, nous vous recommandons de passer à l’**analyse continue**, ce qui signifie que nous pouvons déduire des tendances quand les nombres augmentent ou diminuent plutôt que de les traiter comme des valeurs distinctes. Vous pouvez passer de l’**analyse par catégorie** à l’**analyse en continu** dans le **volet de mise en forme** sous la carte  **Analyse**.

Pour trouver des influenceurs plus forts, nous vous recommandons de regrouper les valeurs similaires dans une même unité. Par exemple, si vous avez une métrique pour le prix, vous obtiendrez sans doute de meilleurs résultats en regroupant les prix similaires dans des catégories comme « Élevé », « Moyen » et « Faible » au lieu d’utiliser des niveaux de prix individuels. 

![Avertissement lié à la présence de plus de 10 facteurs uniques](media/power-bi-visualization-influencers/power-bi-error4.png)


**Il y a des facteurs dans mes données qui devraient visiblement être des influenceurs clés, mais qui ne le sont pas. À quoi cela peut-il être dû ?**

Dans l’exemple suivant, les clients qui sont des consommateurs attribuent des évaluations faibles (14,93 % des évaluations). Le rôle d’administrateur présente également une proportion élevée d’évaluations faibles (13,42 %), mais n’est pas considéré comme un influenceur. 

La raison de cette détermination est que la visualisation prend également en compte le nombre de points de données quand elle trouve des influenceurs. L’exemple suivant a plus de 29 000 consommateurs et 10 fois moins d’administrateurs, environ 2 900. Seuls 390 d’entre eux ont donné une évaluation faible. Le visuel n’a pas suffisamment de données pour déterminer s’il a détecté une tendance avec les évaluations des administrateurs ou s’il s’agit simplement d’une déduction hasardeuse. 

![Détermination des influenceurs](media/power-bi-visualization-influencers/power-bi-error5.png)

**Comment calculer les influenceurs clés pour l’analyse par catégorie ?**

En arrière-plan, la visualisation d’intelligence artificielle utilise [ML.NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) pour exécuter une régression logistique qui calcule les influenceurs clés. Une régression logistique est un modèle statistique qui compare différents groupes. 

Si vous voulez voir ce qui contribue à des évaluations faibles, la régression logistique examine en quoi les clients qui ont attribué un score faible diffèrent de ceux ayant attribué un score élevé. Si vous avez plusieurs catégories (scores élevés, neutres et faibles par exemple), vous examinez en quoi les clients qui ont attribué une évaluation faible diffèrent de ceux n’ayant pas attribué une telle évaluation. Dans ce cas, en quoi les clients qui ont attribué un score faible diffèrent de ceux ayant attribué une évaluation élevée ou neutre ? 
 
La régression logistique recherche des tendances dans les données, autrement dit des indices suggérant en quoi les clients qui ont donné une évaluation faible peuvent différer de ceux ayant donné une évaluation élevée. Elle peut ainsi détecter que les clients qui ont de nombreux tickets de support présentent un pourcentage beaucoup plus élevé d’évaluations faibles que ceux qui en ont peu ou aucun.
 
La régression logistique prend également en compte le nombre de points de données présents. Par exemple, si les clients qui jouent un rôle d’administrateur attribuent des scores proportionnellement plus négatifs, mais qu’il n’y a que quelques administrateurs, ce facteur n’est pas considéré comme influent. Cette détermination tient au fait qu’il n’y a pas assez de points de données disponibles pour déduire une tendance. Un test statistique (appelé test de Wald) est utilisé pour déterminer si un facteur est considéré comme un influenceur. Le visuel utilise une valeur p de 0,05 pour déterminer le seuil. 

**Comment calculer les influenceurs clés pour l’analyse numérique ?**

En arrière-plan, la visualisation d’intelligence artificielle utilise [ML.NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) pour exécuter une régression linéaire qui calcule les influenceurs clés. Une régression linéaire est un modèle statistique qui examine comment le résultat du champ que vous analysez change en fonction de vos facteurs explicatifs.

Par exemple, si nous analysons le prix des maisons, une régression linéaire examine l’impact d’une cuisine d’excellente qualité sur le prix. Les maisons équipées d’une cuisine d’excellente qualité sont-elles généralement plus chères ou moins chères que les maisons n’offrant pas une telle cuisine ?

La régression linéaire prend également en compte le nombre de points de données. Par exemple, si les maisons avec des courts de tennis ont des prix plus élevés mais que très peu de maisons ont un court de tennis, ce facteur n’est pas considéré comme influent. Cette détermination s’explique par le fait qu’il n’y a pas assez de points de données disponibles pour déduire une tendance. Un test statistique (appelé test de Wald) est utilisé pour déterminer si un facteur est considéré comme un influenceur. Le visuel utilise une valeur p de 0,05 pour déterminer le seuil. 

**Comment les segments sont calculés ?**

En arrière-plan, la visualisation d’intelligence artificielle utilise [ML.NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) pour exécuter un arbre de décision afin de trouver des sous-groupes intéressants. L’objectif de l’arbre de décision est d’obtenir un sous-groupe de points de données qui est relativement élevé dans la métrique qui vous intéresse. Il peut s’agir de clients ayant donné des évaluations faibles ou de maisons avec des prix élevés.

L’arbre de décision prend chaque facteur explicatif et tente d’identifier quel facteur lui donne la meilleure *division*. Par exemple, si vous filtrez les données pour inclure uniquement les grandes entreprises, cela permettra-il de séparer les clients qui nous ont donné une évaluation élevée de ceux qui ont donné une évaluation faible ? Ou peut-être est-il préférable de filtrer les données pour inclure uniquement les clients qui ont commenté la sécurité ? 

Une fois que l’arbre de décision effectue une division, il prend le sous-groupe de données et détermine quelle serait la meilleure division suivante pour ces données. Dans ce cas, le sous-groupe est constitué des clients qui ont commenté la sécurité. Après chaque division, il prend également en compte le nombre de points de données de ce groupe afin de déterminer s’il est suffisamment représentatif pour en déduire une tendance, ou s’il pourrait simplement s’agir d’une anomalie dans les données (et non d’un segment réel). Un autre test statistique est appliqué pour vérifier la signification statistique de la condition de division, avec une valeur p égale à 0,05. 

Une fois l’exécution de l’arbre de décision terminée, il prend toutes les divisions (commentaires sur la sécurité et grande entreprise par exemple) et crée des filtres Power BI. Cette combinaison de filtres est empaqueté en tant que segment dans le visuel. 
 
**Pourquoi certains facteurs deviennent des influenceurs ou cessent d’en être à mesure que je déplace davantage de champs dans le champ *Expliquer par* ?**

La visualisation évalue tous les facteurs explicatifs ensemble. Un facteur peut être un influenceur en soi, mais il peut ne pas l’être quand il est considéré avec d’autres facteurs. Supposons que vous souhaitiez analyser les facteurs contribuant au prix élevé d’une maison, avec le nombre de chambres et la taille de la maison comme facteurs explicatifs :

- En soi, un nombre de chambres plus élevé peut faire augmenter le prix de la maison.
- Le fait d’inclure la taille de la maison dans l’analyse signifie que nous pouvons désormais observer ce qui se passe au niveau des chambres en maintenant la taille de la maison constante.
- Si la taille de la maison est fixée à 140 mètres carrés, il est peu probable que le fait d’augmenter de manière continue le nombre de chambres augmentera sensiblement le prix de la maison. 
- Le nombre de chambres ne sera peut-être pas un facteur aussi important qu’il l’était avant la prise en compte de la taille de la maison. 




## <a name="next-steps"></a>Étapes suivantes
- [Graphiques en entonnoir dans Power BI](power-bi-visualization-combo-chart.md)
- [Types de visualisation dans Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)
