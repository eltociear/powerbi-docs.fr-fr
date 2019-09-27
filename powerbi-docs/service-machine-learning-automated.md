---
title: Machine Learning automatisé dans Power BI (préversion)
description: Découvrez comment utiliser le Machine Learning automatisé (AutoML) dans Power BI
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/02/2019
ms.author: davidi
LocalizationGroup: conceptual
ms.openlocfilehash: 894e92687a6283ce71b253bd4dc635aca0c4673f
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "61236447"
---
# <a name="automated-machine-learning-in-power-bi-preview"></a>Machine Learning automatisé dans Power BI (préversion)

Le Machine Learning automatisé (AutoML) pour les dataflows permet aux analystes d’entreprise de former, valider et appeler des modèles Machine Learning directement dans Power BI. Il offre une expérience simple pour la création d’un nouveau modèle Machine Learning dans lequel les analystes peuvent utiliser leurs dataflows pour spécifier les données d’entrée pour effectuer l’apprentissage du modèle. Le service extrait automatiquement les fonctionnalités les plus pertinentes, sélectionne un algorithme approprié et règle et valide le modèle Machine Learning. Après l’apprentissage d’un modèle, Power BI génère automatiquement un rapport qui comprend les résultats de la validation et explique les performances et résultats aux analystes. Le modèle peut ensuite être appelé sur toutes les données nouvelles ou mises à jour dans le dataflow.

![Écran de Machine Learning](media/service-machine-learning-automated/automated-machine-learning-power-bi-01.png)

Le Machine Learning automatisé est disponible pour les dataflows hébergés sur les capacités Power BI Premium et Embedded uniquement. Dans cette préversion, AutoML vous permet d’effectuer l’apprentissage des modèles Machine Learning pour les modèles de prédiction binaire, de classification et de régression.

## <a name="working-with-automl"></a>Utilisation d’AutoML

Les [dataflows de Power BI](service-dataflows-overview.md) offrent une préparation des données en libre-service pour le Big Data. AutoML vous permet de tirer parti de votre effort de préparation des données pour créer des modèles Machine Learning directement dans Power BI.

AutoML dans Power BI permet aux analystes de données d’utiliser les dataflows pour créer des modèles Machine Learning avec une expérience simplifiée, en utilisant uniquement des compétences Power BI. La majeure partie de la science des données derrière la création des modèles Machine Learning est automatisée par Power BI, avec des contrôles pour s’assurer que le modèle produit présente une bonne qualité et une visibilité suffisante pour vous fournir une vue d’ensemble du processus utilisé pour créer votre modèle Machine Learning.

AutoML prend en charge la création de modèles de **Prédiction binaire**, de **Classification** et de **Régression** pour les dataflows. Il s’agit de types de modèles Machine Learning supervisés, ce qui signifie qu’ils apprennent des résultats connus à partir d’observations passées pour prédire les résultats d’autres observations. Le jeu de données d’entrée pour effectuer l'apprentissage d’un modèle AutoML est un ensemble d’enregistrements **étiquetés** avec les résultats connus.

AutoML dans Power BI intègre le [Machine Learning automatisé](https://docs.microsoft.com/azure/machine-learning/service/concept-automated-ml) du [service Azure Machine Learning](https://docs.microsoft.com/azure/machine-learning/service/overview-what-is-azure-ml) pour créer vos modèles Machine Learning. Toutefois, vous n’avez pas besoin d’un abonnement Azure pour utiliser AutoML dans Power BI. Le processus de formation et d’hébergement des modèles Machine Learning est géré entièrement par le service Power BI.

Après l’apprentissage d’un modèle Machine Learning, AutoML génère automatiquement un rapport Power BI qui explique les performances probables de votre modèle Machine Learning. AutoML met l’accent sur la facilité d’explication, en mettant en évidence les facteurs d’influence clés parmi les entrées qui influencent les prédictions renvoyées par votre modèle. Le rapport comprend également des métriques clés pour le modèle, en fonction du type de modèle Machine Learning.

D’autres pages du rapport généré affichent le résumé statistique du modèle et les détails de la formation. Le résumé statistique présente un intérêt pour les utilisateurs qui souhaitent voir les mesures de performance de la science des données standard pour le modèle. Les détails de la formation résument toutes les itérations exécutées pour créer votre modèle, avec les paramètres de modélisation associés. Ils décrivent également comment chaque entrée a été utilisée pour créer le modèle Machine Learning.

Vous pouvez ensuite appliquer votre modèle Machine Learning à vos données pour scoring. Lorsque le dataflow est actualisé, les prédictions de votre modèle Machine Learning sont automatiquement appliquées à vos données. Power BI comprend également une explication individualisée pour chaque score de prédiction spécifique produit par le modèle Machine Learning.

## <a name="creating-a-machine-learning-model"></a>Créer un modèle Machine Learning

Cette section décrit comment créer un modèle d’apprentissage AutoML. 

### <a name="data-prep-for-creating-an-ml-model"></a>Préparation des données pour la création d’un modèle Machine Learning

Pour créer un modèle Machine Learning dans Power BI, vous devez d’abord créer un dataflow pour les données avec les informations d’historique des résultats, qui sont utilisées pour effectuer l'apprentissage du modèle ML. Pour plus d’informations sur la configuration de vos dataflows, consultez [Préparation des données en libre-service dans Power BI](service-dataflows-overview.md).

Dans la version actuelle, Power BI utilise les données d’une seule entité pour effectuer l'apprentissage du modèle ML. Par conséquent, si vos données d’historique se composent de plusieurs entités, vous devez joindre manuellement les données dans une entité de dataflow unique. Vous devez également ajouter des colonnes calculées pour toutes les métriques commerciales qui peuvent être des éléments de prédiction forts pour les résultats que vous essayez de prédire.

AutoML a des exigences spécifiques en matière de données pour la formation d’un modèle Machine Learning. Ces exigences sont décrites dans les sections ci-dessous, en fonction des types de modèle respectifs.

### <a name="configuring-the-ml-model-inputs"></a>Configuration des entrées du modèle Machine Learning

Pour créer un modèle AutoML, sélectionnez l’icône ML dans la colonne **Actions** de l’entité de dataflow avec les données historiques, puis sélectionnez **Ajouter un modèle Machine Learning**.

![Ajouter un modèle Machine Learning](media/service-machine-learning-automated/automated-machine-learning-power-bi-02.png)

Une expérience simplifiée est lancée, composée d’un assistant qui vous guide tout au long du processus de création du modèle Machine Learning. L’assistant comprend les étapes simples suivantes.

1. Sélectionnez l’entité avec les données de résultat historiques et le champ pour lequel vous souhaitez une prédiction
2. Choisissez un type de modèle en fonction du type de prédiction que vous souhaitez afficher
3. Sélectionnez les entrées que vous souhaitez que le modèle utilise comme signaux prédictifs
4. Nommez votre modèle et enregistrez votre configuration

Le champ de résultats historiques identifie l’attribut d’étiquette pour la formation du modèle Machine Learning, comme illustré dans l’image suivante.

![Sélectionner les données de résultat historiques](media/service-machine-learning-automated/automated-machine-learning-power-bi-03.png)

Lorsque vous spécifiez le champ de résultats historiques, AutoML analyse les données d’étiquette pour identifier les types de modèles Machine Learning qui peuvent être formés pour ces données, et suggère le type de modèle Machine Learning le plus probable qui peut être formé. 

> [!NOTE]
> Certains types de modèles peuvent ne pas être pris en charge pour les données que vous avez sélectionnées.

AutoML analyse également tous les champs de l’entité sélectionnée pour suggérer les entrées qui peuvent être utilisées pour effectuer l'apprentissage du modèle Machine Learning. Ce processus est approximatif et repose sur une analyse statistique. Vous devez donc passer en revue les entrées utilisées. Toutes les entrées dépendantes du champ de résultats historiques (ou du champ d’étiquette) ne doivent pas être utilisées pour effectuer l'apprentissage du modèle Machine Learning, car elles affectent les performances.

![Personnaliser les champs d’entrée](media/service-machine-learning-automated/automated-machine-learning-power-bi-04.png)

Dans la dernière étape, vous pouvez nommer le modèle et enregistrer ses paramètres.

À ce stade, vous êtes invité à actualiser le dataflow, qui commence le processus d’apprentissage pour le modèle ML.

### <a name="ml-model-training"></a>Formation du modèle Machine Learning

La formation des modèles AutoML fait partie de l’actualisation du dataflow. AutoML prépare tout d’abord vos données pour l’apprentissage.

AutoML fractionne les données historiques que vous fournissez dans les jeux de données d’apprentissage et de test. Le jeu de données de test est un ensemble de données d’exclusion utilisé pour valider les performances du modèle après l’apprentissage. Il se présente sous la forme d’entités **Apprentissage et test** dans le dataflow. AutoML utilise la validation croisée pour la validation du modèle.

Ensuite, chaque champ d’entrée est analysé et l’imputation est appliquée, ce qui remplace toutes les valeurs manquantes par des valeurs substituées. Plusieurs stratégies d’imputation sont utilisées par AutoML. Ensuite, l’échantillonnage et la normalisation requis sont appliqués à vos données.

AutoML applique plusieurs transformations. Chaque champ d’entrée est sélectionné en fonction de son type de données et de ses propriétés statistiques. AutoML utilise ces transformations pour extraire les fonctionnalités à utiliser lors de la formation de votre modèle Machine Learning.

Le processus d’apprentissage pour les modèles AutoML se compose de jusqu’à 50 itérations avec différents algorithmes de modélisation et des paramètres d’hyperparamètre pour trouver le modèle avec les meilleures performances. Les performances de chacun de ces modèles sont évaluées par la validation avec le jeu de données d’exclusion de test. Au cours de cette étape de formation, AutoML crée plusieurs pipelines pour effectuer l'apprentissage et la validation de ces itérations. Le processus d’évaluation des performances des modèles peut prendre du temps, entre quelques minutes et quelques heures, en fonction de la taille de votre jeu de données et des ressources de capacité dédiées disponibles.

Dans certains cas, le modèle final généré peut utiliser l’apprentissage conjoint, où plusieurs modèles sont utilisés pour fournir de meilleures performances prédictives.

### <a name="automl-model-explainability"></a>Facilité d’explication du modèle AutoML

Une fois le modèle formé, AutoML analyse la relation entre les fonctionnalités d’entrée et la sortie du modèle. Elle évalue l’amplitude et la direction de la modification apportée à la sortie du modèle pour le jeu de données d’exclusion de test pour chaque fonctionnalité d’entrée. C’est ce que l’on appelle *l’Importance de la fonctionnalité*.

![Importance de la fonctionnalité](media/service-machine-learning-automated/automated-machine-learning-power-bi-05.png)

### <a name="automl-model-report"></a>Rapport sur le modèle AutoML

AutoML génère un rapport Power BI qui résume les performances du modèle pendant la validation, ainsi que l’importance globale des fonctionnalités. Le rapport résume les résultats de l’application du modèle Machine Learning aux données d’exclusion de test et de la comparaison des prédictions avec les valeurs de résultat connues.

Vous pouvez consulter le rapport de modèle pour comprendre ses performances. Vous pouvez également vérifier que les influenceurs clés du modèle s’alignent sur les insights métier sur les résultats connus.

Les graphiques et mesures utilisés pour décrire les performances du modèle dans le rapport varient selon le type de modèle. Ces graphiques et mesures de performance sont décrits dans les sections suivantes.

Des pages supplémentaires dans le rapport peuvent décrire des mesures statistiques sur le modèle du point de vue de la science des données. Par exemple, le rapport **Prédiction binaire** comprend un graphique de gain et la courbe ROC pour le modèle.

Les rapports incluent également une page **Détails de l’entraînement** qui inclut une description de la façon dont le modèle a été formé et inclut un graphique décrivant les performances du modèle sur chacune des itérations exécutées.

![Détails de l’entraînement](media/service-machine-learning-automated/automated-machine-learning-power-bi-06.png)

Une autre section de cette page décrit comment la méthode d’imputation a été utilisée pour remplir les valeurs manquantes pour les champs d’entrée, ainsi que la façon dont chaque champ d’entrée a été transformé pour extraire les fonctionnalités utilisées dans le modèle. Elle comprend également les paramètres utilisés par le modèle final.

![Plus d’informations sur le modèle](media/service-machine-learning-automated/automated-machine-learning-power-bi-07.png)

Si le modèle produit utilise l’apprentissage conjoint, la page **Détails de formation** comprend également une section décrivant le poids de chaque modèle constitutif dans l’ensemble, ainsi que ses paramètres.

![Poids dans l’ensemble](media/service-machine-learning-automated/automated-machine-learning-power-bi-08.png)

## <a name="applying-the-automl-model"></a>Application du modèle AutoML

Si vous êtes satisfait des performances du modèle Machine Learning créé, vous pouvez l’appliquer à des données nouvelles ou mises à jour lorsque votre dataflow est actualisé. Vous pouvez le faire à partir du rapport de modèle, en sélectionnant le bouton **Appliquer** dans le coin supérieur droit.

Pour appliquer le modèle Machine Learning, vous devez spécifier le nom de l’entité à laquelle il doit être appliqué et un préfixe pour les colonnes qui seront ajoutées à cette entité pour la sortie du modèle. Le préfixe par défaut des noms de colonne est le nom du modèle. La fonction *Appliquer* peut inclure des paramètres supplémentaires spécifiques au type de modèle.

L’application du modèle Machine Learning crée une entité de dataflow avec le suffixe **enriched <nom_modèle>** . Par exemple, si vous appliquez le modèle _PurchaseIntent_ à l’entité _OnlineShoppers_, la sortie génère **PurchaseIntent enriched OnlineShoppers**.

Actuellement, l’entité de sortie ne peut pas être utilisée pour afficher un aperçu des résultats du modèle Machine Learning dans l’éditeur Power Query. Les colonnes de sortie affichent toujours la valeur null comme résultat. Pour afficher les résultats, une deuxième entité de sortie avec le suffixe **<nom_modèle> Preview** est créée lorsque le modèle est appliqué.

Vous devez actualiser le dataflow pour afficher un aperçu des résultats dans l’éditeur de requête.

![Éditeur de requête](media/service-machine-learning-automated/automated-machine-learning-power-bi-09.png)

Lorsque vous appliquez le modèle, AutoML garde toujours vos prédictions à jour lorsque le dataflow est actualisé.

AutoML comprend également une explication individualisée pour chaque ligne qu’il note dans l’entité de sortie.

Pour utiliser les insights et prédictions du modèle Machine Learning dans un rapport Power BI, vous pouvez vous connecter à l’entité de sortie à partir de Power BI Desktop avec le connecteur de **dataflows**.

## <a name="binary-prediction-models"></a>Modèles de prédiction binaire

Les modèles de prédiction binaire, plus connus sous le nom de **modèles de classification binaire**, sont utilisés pour classer un jeu de données en deux groupes. Ils sont utilisés pour prédire les événements qui peuvent avoir un résultat binaire, par exemple si une opportunité de vente sera convertie, si un client ne renouvellera pas, si une facture sera payée à temps, si une transaction sera frauduleuse, et ainsi de suite.

Étant donné que le résultat est binaire, Power BI s’attend à ce que l’étiquette d’un modèle de prédiction binaire soit une valeur booléenne, avec des résultats connus étiquetés **true** ou **false**. Par exemple, dans un modèle de conversion d’opportunité de vente, les opportunités de vente qui ont été remportées sont étiquetées true, celles qui ont été perdues false, et celles qui sont encore ouvertes null.

La sortie d’un modèle de prédiction binaire est un score de probabilité, qui identifie la probabilité que le résultat correspondant à la valeur de l’étiquette soit vrai.

### <a name="training-a-binary-prediction-model"></a>Apprentissage d’un modèle de prédiction binaire

Pour créer un modèle de prédiction binaire, l’entité d’entrée contenant vos données d’apprentissage doit avoir un champ booléen comme champ de résultat historique pour identifier les résultats connus passés.

Conditions préalables :

* Un champ booléen doit être utilisé comme champ de résultat historique
* Au moins 50 lignes de données d’historique sont requises pour chaque classe de résultats

En général, si les résultats passés sont identifiés par des champs d’un type de données différent, vous pouvez ajouter une colonne calculée pour les transformer en valeur booléenne à l’aide de Power Query.

Le processus de création d’un modèle de prédiction binaire suit les mêmes étapes que les autres modèles AutoML, décrits dans la section **Configuration des entrées du modèle Machine Learning** ci-dessus.

### <a name="binary-prediction-model-report"></a>Rapport de modèle de prédiction binaire

Le modèle de prédiction binaire produit comme résultat une probabilité qu’un enregistrement atteigne le résultat défini par la valeur de l’étiquette booléenne true. Le rapport comprend un segment pour le seuil de probabilité, qui détermine la façon dont les scores au-dessus et en dessous du seuil de probabilité sont interprétés.

Le rapport décrit les performances du modèle en termes de *Vrais positifs*, *Faux positifs*, *Vrais négatifs* et *Faux négatifs*. Les vrais positifs et vrais négatifs sont des résultats prédits correctement pour les deux classes dans les données de résultat. Les faux positifs sont des résultats qui ont reçu l’étiquette booléenne false, mais qui avaient été prédits comme true. À l’inverse, les faux négatifs sont des résultats où la valeur réelle d’étiquette booléenne était true, mais qui avaient été prédits comme false.

Les mesures, telles que la précision et le rappel, décrivent l’effet du seuil de probabilité sur les résultats prédits. Vous pouvez utiliser le segment de seuil de probabilité pour sélectionner un seuil qui atteint un compromis équilibré entre précision et rappel.

![Aperçu de la précision](media/service-machine-learning-automated/automated-machine-learning-power-bi-10.png)

La page **Rapport de précision** du rapport de modèle comprend le graphique *Gains cumulés* et la courbe ROC pour le modèle. Il s’agit des mesures statistiques des performances du modèle. Les rapports incluent des descriptions des graphiques affichés.

![Écran de rapport de précision](media/service-machine-learning-automated/automated-machine-learning-power-bi-11.png)

### <a name="applying-a-binary-prediction-model"></a>Application d’un modèle de prédiction binaire

Pour appliquer un modèle de prédiction binaire, vous devez spécifier l’entité avec les données auxquelles vous souhaitez appliquer les prédictions à partir du modèle Machine Learning. Les autres paramètres incluent le préfixe du nom de la colonne de sortie et le seuil de probabilité pour la classification des résultats prédits.

![Entrées de prédiction](media/service-machine-learning-automated/automated-machine-learning-power-bi-12.png)

Lorsqu’un modèle de prédiction binaire est appliqué, il ajoute trois colonnes de sortie à l’entité de sortie enrichie. Ce sont les colonnes **PredictionScore**, **PredictionOutcome** et **PredictionExplanation**. Le préfixe est spécifié pour les noms de colonnes de l’entité lorsque le modèle est appliqué.

La colonne **PredictionOutcome** contient l’étiquette de résultat prédite. Les enregistrements avec des probabilités dépassant le seuil sont prédits comme susceptibles d’obtenir le résultat, et ceux en dessous du seuil sont prédits comme peu susceptibles d’obtenir le résultat.

La colonne **PredictionExplanation** contient une explication de l’influence spécifique que les fonctionnalités d’entrée avaient sur le **PredictionScore**. Il s’agit d’une collection au format JSON de poids des fonctionnalités d’entrée pour la prédiction.

## <a name="classification-models"></a>Modèles de classification

Les modèles de classification sont utilisés pour classer un jeu de données en plusieurs groupes ou classes.  Ils sont utilisés pour prédire des événements qui peuvent avoir plusieurs résultats possibles, par exemple si un client est susceptible d’avoir une valeur de durée de vie très élevée, élevée, moyenne ou faible, ou si le risque de défaut est élevé, modéré, faible ou très faible, et ainsi de suite.

La sortie d’un modèle de classification est un score de probabilité qui identifie la probabilité qu’un enregistrement atteigne les critères d’une classe donnée.

### <a name="training-a-classification-model"></a>Formation d’un modèle de classification

L’entité d’entrée contenant les données d’apprentissage d’un modèle de classification doit avoir un champ chaîne ou numérique comme champ de résultat historique, qui identifie les résultats passés connus.

Conditions préalables :

* Au moins 50 lignes de données d’historique sont requises pour chaque classe de résultats

Le processus de création d’un modèle de classification suit les mêmes étapes que les autres modèles AutoML, décrits dans la section **Configuration des entrées du modèle Machine Learning** ci-dessus.

### <a name="classification-model-report"></a>Rapport de modèle de classification

Le rapport de modèle de classification est généré en appliquant le modèle Machine Learning aux données d’exclusion de test et en comparant la classe prédite pour un enregistrement à la classe connue réelle.

Le rapport de modèle contient un graphique qui comprend la répartition des enregistrements correctement et incorrectement classés pour chaque classe connue.

![Rapport de modèle](media/service-machine-learning-automated/automated-machine-learning-power-bi-13.png)

Un autre détail spécifique à la classe permet d’analyser la manière dont les prédictions d’une classe connue sont distribuées. Cela comprend les autres classes dans lesquelles les enregistrements de cette classe connue sont susceptibles d’être mal classés.

![Rapport d’analyse](media/service-machine-learning-automated/automated-machine-learning-power-bi-14.png)

L’explication du modèle dans le rapport comprend également les meilleures prédictions de chaque classe.

Le rapport de modèle de classification comprend également une page de détails de l’entraînement similaire aux pages pour les autres types de modèles, comme décrit dans la section **Rapport sur le modèle AutoML** plus haut dans cet article.

### <a name="applying-a-classification-model"></a>Application d’un modèle de classification

Pour appliquer un modèle de classification Machine Learning, vous devez spécifier l’entité avec les données d’entrée et le préfixe du nom de la colonne de sortie.

Lorsqu’un modèle de classification est appliqué, il ajoute trois colonnes de sortie à l’entité de sortie enrichie. Ce sont les colonnes **PredictionScore**, **PredictionClass** et **PredictionExplanation**. Le préfixe est spécifié pour les noms de colonnes de l’entité lorsque le modèle est appliqué.

La colonne **PredictionClass** contient la classe prédite la plus probable pour l’enregistrement. La colonne **PredictionScore** contient la liste des scores de probabilité pour l’enregistrement pour chaque classe possible.

La colonne **PredictionExplanation** contient une explication de l’influence spécifique que les fonctionnalités d’entrée avaient sur le **PredictionScore**. Il s’agit d’une collection au format JSON de poids des fonctionnalités d’entrée pour la prédiction.

## <a name="regression-models"></a>Modèles de régression

Les modèles de régression sont utilisés pour prédire une valeur, par exemple le chiffre d’affaires susceptible d’être réalisé pour un contrat de vente, la valeur de durée de vie d’un client, le montant d’une facture client susceptible d’être payé, la date à laquelle une facture peut être payée, et ainsi de suite.

La sortie d’un modèle de régression est la valeur prédite.

### <a name="training-a-regression-model"></a>Formation d’un modèle de régression

L’entité d’entrée contenant les données d’apprentissage d’un modèle de régression doit avoir un champ numérique comme champ de résultat historique, qui identifie les valeurs des résultats passés connus.

Conditions préalables :

* Un modèle de régression nécessite au minimum 100 lignes de données historiques

Le processus de création d’un modèle de régression suit les mêmes étapes que les autres modèles AutoML, décrits dans la section **Configuration des entrées du modèle Machine Learning** ci-dessus.

### <a name="regression-model-report"></a>Rapport sur le modèle de régression

Comme les autres rapports de modèle AutoML, le rapport de régression est basé sur les résultats de l’application du modèle aux données d’exclusion de test.

Le rapport de modèle comprend un graphique qui compare les valeurs prédites à la valeur réelle. Dans ce graphique, la distance par rapport à la diagonale indique l’erreur dans la prédiction.

Le tableau d’erreurs résiduelles affiche la répartition du pourcentage moyen d’erreur pour les différentes valeurs dans le jeu de données d’exclusion de test. L’axe horizontal représente la moyenne de la valeur réelle pour le groupe, la taille de la bulle indiquant la fréquence ou le nombre de valeurs de cette plage. L’axe vertical est l’erreur résiduelle moyenne.

![Graphique des erreurs résiduelles](media/service-machine-learning-automated/automated-machine-learning-power-bi-15.png)

Le rapport de modèle de régression comprend également une page de détails de l’entraînement, comme les rapports pour les autres types de modèles, comme décrit dans la section **Rapport sur le modèle AutoML** ci-dessus.

### <a name="applying-a-regression-model"></a>Application d’un modèle de régression

Pour appliquer un modèle de régression Machine Learning, vous devez spécifier l’entité avec les données d’entrée et le préfixe du nom de la colonne de sortie.

![Appliquer une régression](media/service-machine-learning-automated/automated-machine-learning-power-bi-16.png)

Lorsqu’un modèle de régression est appliqué, il ajoute deux colonnes de sortie à l’entité de sortie enrichie. Ce sont les colonnes **PredictionValue** et **PredictionExplanation**. Le préfixe est spécifié pour les noms de colonnes de l’entité lorsque le modèle est appliqué.

La colonne **PredictionValue** contient la valeur prédite de l’enregistrement en fonction des champs d’entrée. La colonne **PredictionExplanation** contient une explication de l’influence spécifique que les fonctionnalités d’entrée avaient sur le **PredictionValue**. Il s’agit d’une collection au format JSON de poids des fonctionnalités d’entrée.

## <a name="next-steps"></a>Étapes suivantes

Cet article donne une vue d’ensemble du Machine Learning automatisé pour les dataflows dans le service Power BI. Les articles suivants peuvent également vous être utiles.

* [Tutoriel : Créer un modèle Machine Learning dans Power BI (préversion)](service-tutorial-build-machine-learning-model.md)
* [Tutoriel : Utilisation de Cognitive Services dans Power BI](service-tutorial-use-cognitive-services.md)
* [Tutoriel : Appeler un modèle Machine Learning Studio dans Power BI (préversion)](service-tutorial-invoke-machine-learning-model.md)
* [Cognitive Services dans Power BI (préversion)](service-cognitive-services.md)
* [Intégration d’Azure Machine Learning dans Power BI (préversion)](service-machine-learning-integration.md)

Pour plus d’informations sur les flux de données, lisez les articles suivants :
* [Créer et utiliser des flux de données dans Power BI](service-dataflows-create-use.md)
* [Utilisation d’entités calculées sur Power BI Premium](service-dataflows-computed-entities-premium.md)
* [Utilisation de flux de données avec des sources de données locales](service-dataflows-on-premises-gateways.md)
* [Ressources du développeur pour les flux de données Power BI](service-dataflows-developer-resources.md)
* [Flux de données et intégration à Azure Data Lake (préversion)](service-dataflows-azure-data-lake-integration.md)


