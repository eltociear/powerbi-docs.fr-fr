---
title: Machine Learning automatisé dans Power BI (préversion)
description: Découvrez comment utiliser l’apprentissage automatique (AutoML) dans Power BI
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
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "61236447"
---
# <a name="automated-machine-learning-in-power-bi-preview"></a>Machine Learning automatisé dans Power BI (préversion)

Automatisés apprentissage automatique (AutoML) pour les flux de données permet des analystes d’entreprise former, valider et appeler des modèles de Machine Learning directement dans Power BI. Il inclut une expérience simple pour la création d’un modèle ML où les analystes peuvent utiliser leurs flux de données pour spécifier les données d’apprentissage du modèle d’entrée. Le service extrait automatiquement les fonctionnalités les plus pertinents, sélectionne un algorithme approprié et ajuste et valide le modèle ML. Une fois un modèle est formé, Power BI génère automatiquement un rapport qui inclut les résultats de validation qui explique les performances et résultats pour les analystes. Le modèle peut ensuite être appelé sur n’importe quel nouveau ou mis à jour les données dans le flux de données.

![Écran machine learning](media/service-machine-learning-automated/automated-machine-learning-power-bi-01.png)

Apprentissage automatique est disponible pour les flux de données qui sont hébergés sur les capacités Power BI Premium et incorporé uniquement. Dans cette version préliminaire, AutoML vous permet de former des modèles d’apprentissage automatique pour les modèles de régression, la Classification et prédiction binaire.

## <a name="working-with-automl"></a>Utilisation de AutoML

[Power BI de flux de données](service-dataflows-overview.md) offrent la préparation des données en libre-service pour les données volumineuses. AutoML vous permet de tirer parti de votre effort de préparation des données pour la création de modèles d’apprentissage automatique, directement dans Power BI.

AutoML dans Power BI permet à des analystes de données à utiliser des flux de données pour créer des modèles d’apprentissage automatique avec une expérience simplifiée, en utilisant simplement les compétences de Power BI. La majeure partie de la science des données derrière la création des modèles ML est automatisé par Power BI, avec guardrails pour vous assurer que le modèle généré a bonne qualité et la visibilité de vous fournir un aperçu complet du processus utilisé pour créer votre modèle ML.

AutoML prend en charge la création de **prédiction binaire**, **Classification**, et **régression** modèles de flux de données. Il s’agit des types de modèles d’apprentissage automatique supervisé, ce qui signifie qu’ils apprennent à partir des résultats connus d’observations passées pour prévoir les résultats d’autres observations. Le jeu de données d’entrée pour l’apprentissage d’un modèle AutoML est un jeu d’enregistrements qui sont **intitulé** avec les résultats connus.

AutoML dans Power BI s’intègre [automatisée ML](https://docs.microsoft.com/azure/machine-learning/service/concept-automated-ml) à partir de la [service Azure Machine Learning](https://docs.microsoft.com/azure/machine-learning/service/overview-what-is-azure-ml) pour créer vos modèles ML. Toutefois, vous n’avez pas besoin d’abonnement Azure à utiliser AutoML dans Power BI. Le processus de formation et les modèles ML d’hébergement est géré entièrement par le service Power BI.

Une fois un modèle ML est formé, AutoML génère automatiquement un rapport Power BI qui explique la performance probable de votre modèle ML. AutoML met l’accent sur explainability, mettez en surbrillance les facteurs d’influence clés parmi vos entrées qui influencent les prédictions retournées par votre modèle. Le rapport inclut également des mesures clés pour le modèle, en fonction du type de modèle ML.

Autres pages du rapport généré affichent le résumé statistique du modèle et les détails de la formation. Le résumé statistique présente un intérêt pour les utilisateurs qui souhaitent voir les mesures de science des données standard des performances pour le modèle. Les détails de la formation synthétiser toutes les itérations qui ont été exécutées pour créer votre modèle, avec les paramètres de modélisation associé. Elle décrit également comment chaque entrée a été utilisée pour créer le modèle ML.

Vous pouvez ensuite appliquer votre modèle ML à vos données pour calculer les scores. Lorsque le flux de données est actualisée, les prédictions à partir de votre modèle ML sont automatiquement appliquées à vos données. Power BI inclut également une explication individualisée pour chaque score de prédiction spécifique qui génère le modèle ML.

## <a name="creating-a-machine-learning-model"></a>Création d’un modèle d’apprentissage automatique

Cette section décrit comment créer un modèle d’apprentissage automatique AutoML. 

### <a name="data-prep-for-creating-an-ml-model"></a>Préparation des données pour la création d’un modèle ML

Pour créer un modèle d’apprentissage automatique dans Power BI, vous devez d’abord créer un flux de données pour les données avec les informations d’historique de résultat, qui sont utilisées pour l’apprentissage du modèle ML. Pour plus d’informations sur la configuration de votre flux de données, consultez [de préparation des données en libre-service dans Power BI](service-dataflows-overview.md).

Dans la version actuelle, Power BI utilise des données à partir d’une seule entité pour former le modèle ML. Par conséquent, si vos données d’historique se composent de plusieurs entités, vous devez joindre manuellement les données dans une entité de flux de données unique. Vous devez également ajouter des colonnes calculées pour les métriques d’entreprise qui peuvent être PRÉDICTEURS forts pour le résultat que vous tentez de prédire.

AutoML a des exigences de données spécifiques pour l’apprentissage d’un modèle d’apprentissage. Ces exigences sont décrites dans les sections ci-dessous, selon les types de modèle en question.

### <a name="configuring-the-ml-model-inputs"></a>Configurer les entrées de modèle ML

Pour créer un modèle AutoML, sélectionnez l’icône de ML dans le **Actions** colonne de l’entité de flux de données avec les données d’historique, puis sélectionnez **ajouter un modèle machine learning**.

![Ajouter un modèle d’apprentissage automatique](media/service-machine-learning-automated/automated-machine-learning-power-bi-02.png)

Une expérience simplifiée est lancée, consistant en un Assistant qui vous guide à travers le processus de création du modèle ML. L’Assistant inclut les étapes suivantes.

1. Sélectionnez l’entité avec les données d’historique de résultat et le champ pour lequel vous souhaitez une prédiction
2. Choisissez un type de modèle en fonction du type de prédiction que vous aimeriez voir
3. Sélectionnez les entrées que vous souhaitez que le modèle à utiliser comme signaux prédictives
4. Nommez votre modèle et enregistrer votre configuration

Le champ de résultat historiques identifie l’attribut label d’apprentissage du modèle ML, illustré dans l’image suivante.

![Sélectionnez les données d’historique de résultat](media/service-machine-learning-automated/automated-machine-learning-power-bi-03.png)

Lorsque vous spécifiez le champ de résultat historiques, AutoML analyse les données d’étiquette pour identifier les types de modèles ML qui peuvent être formés pour ces données et suggère le type de modèle ML probablement qui permettre être formé. 

> [!NOTE]
> Certains types de modèle ne peuvent pas pris en charge pour les données que vous avez sélectionné.

AutoML analyse également tous les champs dans l’entité sélectionnée pour suggérer des entrées qui peuvent être utilisées pour l’apprentissage du modèle ML. Ce processus est approximatif et repose sur l’analyse statistique, donc vous devez examiner les entrées utilisées. Toutes les entrées qui sont dépendantes sur le champ Historique de résultat (ou le champ d’étiquette) ne doivent pas servir pour l’apprentissage du modèle ML, dans la mesure où ils affectent les performances.

![Personnaliser les champs d’entrée](media/service-machine-learning-automated/automated-machine-learning-power-bi-04.png)

Dans la dernière étape, vous pouvez nommer le modèle et enregistrer ses paramètres.

À ce stade, vous êtes invité à actualiser le flux de données, qui commence le processus d’apprentissage pour le modèle ML.

### <a name="ml-model-training"></a>Apprentissage du modèle ML

Apprentissage des modèles de AutoML fait partie de l’actualisation de flux de données. AutoML commence par préparer vos données pour l’apprentissage.

AutoML fractionne les données historiques que vous fournissez en une formation et de jeux de données de test. Le jeu de données de test est un jeu d’exclusion qui est utilisé pour valider les performances du modèle après la formation. Ceux-ci sont réalisés en tant que **apprentissage et de test** entités dans le flux de données. AutoML utilise la validation croisée pour la validation du modèle.

Ensuite, chaque champ d’entrée est analysé et imputation est appliquée, ce qui remplace des valeurs manquantes par des valeurs substituées. Deux stratégies d’imputation différentes sont utilisées par AutoML. Ensuite, n’importe quel échantillonnage requis et la normalisation sont appliquées à vos données.

AutoML s’applique à plusieurs transformations sont chaque champ d’entrée sélectionné en fonction de son type de données et ses propriétés de statistiques. AutoML utilise ces transformations pour extraire des fonctionnalités pour une utilisation dans l’apprentissage votre modèle ML.

Le processus d’apprentissage pour les modèles AutoML se compose d’itérations jusqu'à 50 avec modélisation différents algorithmes et les paramètres d’hyperparamètres pour découvrir le modèle avec les meilleures performances. Les performances de chacun de ces modèles sont évalué par la validation avec le jeu de données de test d’exclusion. Pendant cette étape de la formation, AutoML crée plusieurs pipelines pour l’apprentissage et de validation de ces itérations. Le processus consistant à évaluer les performances des modèles peut prendre le temps, en tout lieu de plusieurs minutes à quelques heures, selon la taille de votre jeu de données et les ressources de capacité dédiée disponibles.

Dans certains cas, le modèle final généré peut utiliser ensemble d’apprentissage, où plusieurs modèles sont utilisés pour fournir des performances de prédiction mieux.

### <a name="automl-model-explainability"></a>Explainability de modèle AutoML

Une fois que le modèle a été formé, AutoML analyse la relation entre les fonctionnalités d’entrée et la sortie du modèle. Il évalue la magnitude et le sens de modification à la sortie de modèle pour le jeu de données de test d’exclusion pour chaque fonctionnalité d’entrée. Il s’agit du *feature importance*.

![Importance de fonctionnalité](media/service-machine-learning-automated/automated-machine-learning-power-bi-05.png)

### <a name="automl-model-report"></a>Rapport de modèle AutoML

AutoML génère un rapport Power BI qui résume les performances du modèle pendant la validation, ainsi que l’importance de fonctionnalité globale. Le rapport récapitule les résultats à partir d’appliquer le modèle ML pour les données de test d’exclusion et en comparant les prédictions avec les valeurs de résultat connus.

Vous pouvez consulter le rapport de modèle pour comprendre ses performances. Vous pouvez également valider que les facteurs d’influence clés du modèle s’aligner avec les informations d’entreprise sur les résultats connus.

Les graphiques et les mesures utilisées pour décrire les performances du modèle dans le rapport dépendent du type de modèle. Ces graphiques de performances et les mesures sont décrits dans les sections suivantes.

Les pages supplémentaires dans le rapport peuvent décrire des mesures statistiques relatives au modèle à partir d’une perspective de science des données. Par exemple, le **prédiction binaire** rapport inclut un graphique de gain et de la courbe ROC pour le modèle.

Ces rapports incluent également un **détails de la formation** page qui inclut une description de la façon dont le modèle a été formé et inclut un graphique décrivant les performances du modèle sur chacune des itérations s’exécute.

![Détails de l’entraînement](media/service-machine-learning-automated/automated-machine-learning-power-bi-06.png)

Une autre section de cette page décrit comment la méthode d’imputation utilisé pour remplir les valeurs manquantes pour les champs d’entrée, ainsi que la manière dont chaque champ d’entrée a été transformé pour extraire les fonctionnalités utilisées dans le modèle. Il inclut également les paramètres utilisés par le modèle final.

![Plus d’informations pour le modèle](media/service-machine-learning-automated/automated-machine-learning-power-bi-07.png)

Si le modèle de produit utilise l’apprentissage d’ensemble, puis le **détails de la formation** page inclut également une section décrivant le poids de chaque modèle constitutif dans l’ensemble, ainsi que ses paramètres.

![Dans l’ensemble de poids](media/service-machine-learning-automated/automated-machine-learning-power-bi-08.png)

## <a name="applying-the-automl-model"></a>Appliquer le modèle AutoML

Si vous êtes satisfait des performances du modèle ML créé, vous pouvez l’appliquer aux données nouvelle ou mise à jour lorsque votre flux de données est actualisé. Faire cela dans le rapport de modèle, en sélectionnant le **appliquer** bouton dans l’angle supérieur droit.

Pour appliquer le modèle ML, vous devez spécifier le nom de l’entité à laquelle il doit être appliqué et un préfixe pour les colonnes qui seront ajoutés à cette entité pour la sortie du modèle. Le préfixe par défaut pour les noms de colonne est le nom du modèle. Le *appliquer* fonction peut inclure des paramètres supplémentaires spécifiques au type de modèle.

Appliquer le modèle ML crée une nouvelle entité de flux de données avec le suffixe **enrichi < model_name >** . Par exemple, si vous appliquez le _PurchaseIntent_ modèle pour le _OnlineShoppers_ entité, génère la sortie le **OnlineShoppers enrichi PurchaseIntent**.

Actuellement, l’entité de sortie ne peut pas être utilisée pour afficher un aperçu les résultats du modèle ML dans l’éditeur Power Query. Les colonnes de sortie affichent toujours null comme résultat. Pour afficher les résultats, une seconde sortie entité avec le suffixe **enrichi < model_name > Aperçu** est créé lorsque le modèle est appliqué.

Vous devez actualiser le flux de données, pour afficher un aperçu des résultats dans l’éditeur de requête.

![Éditeur de requête](media/service-machine-learning-automated/automated-machine-learning-power-bi-09.png)

Lorsque vous appliquez le modèle, AutoML conserve toujours les prévisions à jour lorsque le flux de données est actualisé.

AutoML inclut également une explication individualisée pour chaque ligne qui il évalue dans l’entité de sortie.

Pour utiliser les informations et les prédictions du modèle ML dans un rapport Power BI, vous pouvez vous connecter à l’entité de sortie à partir de Power BI Desktop à l’aide de la **flux de données** connecteur.

## <a name="binary-prediction-models"></a>Modèles de prédiction binaire

Modèles de prédiction binaire, plus communément appelé **modèles de classification binaire**, sont utilisés pour classer un jeu de données en deux groupes. Elles sont utilisées pour prédire les événements qui peuvent avoir un résultat binaire, tels que si une opportunité de vente convertira, si un compte sera d’activité, si une facture sur la durée ; Indique si une transaction est frauduleux et ainsi de suite.

Étant donné que le résultat est binaire, Power BI attend l’étiquette pour un modèle de prédiction binaire soit un booléen, avec les résultats connus en cours intitulé **true** ou **false**. Par exemple, dans un modèle de conversion opportunité de vente, les opportunités de ventes conclues sont étiquetées trues, ceux qui ont été perdus sont false, et les opportunités de ventes ouvertes sont étiquetées null.

La sortie d’un modèle de prédiction binaire est un score de probabilité, qui identifie la probabilité que le résultat correspondant à la valeur d’étiquette ayant pour valeur true sera obtenu.

### <a name="training-a-binary-prediction-model"></a>Apprentissage d’un modèle de prédiction binaire

Pour créer un modèle de prédiction binaire, l’entité d’entrée qui contient vos données d’apprentissage doit avoir un champ booléen en tant que le champ de résultat historiques pour identifier les derniers résultats connus.

Conditions préalables :

* Un champ booléen doit être utilisé en tant que le champ de résultat historiques
* Un minimum de 50 lignes de données historiques sont nécessaires pour chaque classe de résultats

En règle générale, si les derniers résultats sont identifiés par les champs d’un type de données différent, vous pouvez ajouter une colonne calculée pour la transformer en une valeur booléenne à l’aide de Power Query.

Le processus de création pour un modèle de prédiction binaire suit les mêmes étapes que les autres modèles AutoML, décrits dans la section **configurer les entrées de modèle ML** ci-dessus.

### <a name="binary-prediction-model-report"></a>Rapport de modèle de prédiction binaire

Le modèle de prédiction binaire produit en tant que sortie une probabilité qu’un enregistrement permettent d’obtenir le résultat défini par la valeur d’étiquette booléenne comme True. Le rapport inclut un segment pour le seuil de probabilité, ce qui influence la façon dont les scores au-dessus et au-dessous du seuil de probabilité sont interprétés.

Le rapport décrit les performances du modèle en termes de *vrais positifs*, *faux positifs*, *vrais négatifs* et *faux négatifs*. True positifs et négatifs True sont des résultats prédits correctement pour les deux classes dans les données de résultat. Faux positifs sont les résultats qui avaient l’étiquette booléenne réelle de la valeur False, mais ont été prédite en tant que la valeur True. À l’inverse, faux négatifs sont des résultats où la valeur réelle de l’étiquette Boolean a la valeur True, mais qui ont été prédit comme False.

Mesures, telles que la précision et le rappel, décrivent l’effet du seuil de probabilité sur les résultats prédits. Vous pouvez utiliser le segment de seuil de probabilité pour sélectionner un seuil qui permet d’obtenir un bon compromis entre précision et le rappel.

![Aperçu de l’analyse de précision](media/service-machine-learning-automated/automated-machine-learning-power-bi-10.png)

Le **rapport d’analyse de précision** page du rapport du modèle inclut la *Gains cumulés* graphique et la valeur ROC de courbe pour le modèle. Il s’agit de mesures statistiques des performances du modèle. Ces rapports incluent des descriptions des tableaux de caractères indiqué.

![Écran de rapport d’analyse de précision](media/service-machine-learning-automated/automated-machine-learning-power-bi-11.png)

### <a name="applying-a-binary-prediction-model"></a>Appliquer un modèle de prédiction binaire

Pour appliquer un modèle de prédiction binaire, vous devez spécifier l’entité avec les données à laquelle vous souhaitez appliquer les prédictions à partir du modèle ML. Autres paramètres incluent le préfixe de nom de colonne de sortie et le seuil de probabilité pour classer le résultat prédit.

![Entrées de prédiction](media/service-machine-learning-automated/automated-machine-learning-power-bi-12.png)

Lorsqu’un modèle de prédiction binaire est appliqué, il ajoute trois colonnes de sortie à l’entité de sortie enrichie. Il s’agit de la **PredictionScore**, **PredictionOutcome** et **PredictionExplanation**. Les noms de colonnes dans l’entité ont le préfixe spécifié lorsque le modèle est appliqué.

Le **PredictionOutcome** colonne contient l’étiquette de résultat prédit. Enregistrements avec des probabilités de dépassement du seuil prédits comme susceptible d’obtenir le résultat, et celles ci-dessous sont a prédit que peu de chances d’obtenir le résultat.

Le **PredictionExplanation** colonne contient une explication avec l’influence spécifique présentant les fonctionnalités d’entrée sur le **PredictionScore**. Il s’agit d’une collection au format JSON de poids des fonctionnalités d’entrée pour la prédiction.

## <a name="classification-models"></a>Modèles de classification

Modèles de classification sont utilisés pour classer un jeu de données en plusieurs groupes ou classes.  Elles sont utilisées pour prédire les événements qui peuvent avoir un ou plusieurs résultats possibles, par exemple si un client est susceptible d’avoir une très haute, haute, moyenne ou faible valeur de durée de vie ; Si le risque pour la valeur par défaut est élevé, modéré, faible ou très faible ; et ainsi de suite.

La sortie d’un modèle de Classification est un score de probabilité, qui identifie la probabilité qu’un enregistrement sera atteindre les critères pour une classe donnée.

### <a name="training-a-classification-model"></a>Apprentissage d’un modèle de Classification

L’entité d’entrée qui contient vos données d’apprentissage pour un modèle de Classification doit avoir une chaîne ou un champ numérique en tant que le champ Historique de résultat, qui identifie les derniers résultats connus.

Conditions préalables :

* Un minimum de 50 lignes de données historiques sont nécessaires pour chaque classe de résultats

Le processus de création pour un modèle de Classification suit les mêmes étapes que les autres modèles AutoML, décrits dans la section **configurer les entrées de modèle ML** ci-dessus.

### <a name="classification-model-report"></a>Rapport de modèle de classification

La Classification des rapports de modèle sont généré en appliquant le modèle ML à l’exclusion de test de données et de comparaison de la classe prévue pour un enregistrement avec la classe réelle connue.

Le rapport de modèle comprend un graphique qui inclut la répartition des enregistrements pour chaque classe connu classifications correctes et incorrectes.

![Rapport de modèle](media/service-machine-learning-automated/automated-machine-learning-power-bi-13.png)

Une exploration spécifique à la classe supplémentaire permet une analyse de la façon dont les prédictions pour une classe connue sont distribuées. Cela inclut les autres classes dans laquelle les enregistrements de connues de classe sont susceptibles d’être mal classées.

![Rapport d’analyse](media/service-machine-learning-automated/automated-machine-learning-power-bi-14.png)

L’explication de modèle dans le rapport inclut également les PRÉDICTEURS supérieurs pour chaque classe.

Le rapport de modèle de Classification inclut également une page de détails de la formation similaire aux pages pour les autres types de modèles, comme décrit dans la section **rapport de modèle AutoML** plus haut dans cet article.

### <a name="applying-a-classification-model"></a>Appliquer un modèle de classification

Pour appliquer un modèle de Classification ML, vous devez spécifier l’entité avec les données d’entrée et le préfixe de nom de colonne de sortie.

Lorsqu’un modèle de Classification est appliqué, il ajoute que trois colonnes à l’entité de sortie enrichie de sortie. Il s’agit de la **PredictionScore**, **PredictionClass** et **PredictionExplanation**. Les noms de colonnes dans l’entité ont le préfixe spécifié lorsque le modèle est appliqué.

Le **PredictionClass** colonne contient la classe très probablement prévue pour l’enregistrement. Le **PredictionScore** colonne contient la liste des scores de probabilité pour l’enregistrement pour chaque classe possible.

Le **PredictionExplanation** colonne contient une explication avec l’influence spécifique présentant les fonctionnalités d’entrée sur le **PredictionScore**. Il s’agit d’une collection au format JSON de poids des fonctionnalités d’entrée pour la prédiction.

## <a name="regression-models"></a>Modèles de régression

Les modèles de régression sont utilisés pour prédire une valeur, comme le chiffre d’affaires susceptible d’être réalisés à partir d’une quantité de ventes, la valeur de durée de vie d’un compte, le montant d’une facture client est susceptible d’être payé, la date à laquelle une facture peut être payée , et ainsi de suite.

La sortie d’un modèle de régression est la valeur prédite.

### <a name="training-a-regression-model"></a>Apprentissage d’un modèle de régression

L’entité d’entrée contenant les données d’apprentissage d’un modèle de régression doit avoir un champ numérique que le champ Historique de résultat, qui identifie les dernières valeurs de résultat connus.

Conditions préalables :

* Un minimum de 100 lignes de données historiques sont nécessaires pour un modèle de régression

Le processus de création pour un modèle de régression suit les mêmes étapes que les autres modèles AutoML, décrits dans la section **configurer les entrées de modèle ML** ci-dessus.

### <a name="regression-model-report"></a>Rapport de modèle de régression

Comme les autres rapports de modèle AutoML, le rapport de régression est basé sur les résultats de l’application du modèle aux données de test d’exclusion.

Le rapport de modèle comprend un graphique qui compare les valeurs prédites à la valeur réelle. Dans ce graphique, la distance à partir de la diagonale indique l’erreur dans la prédiction.

Le graphique de l’erreur qui sont restées montre la distribution du pourcentage de l’erreur moyenne pour des valeurs différentes dans le jeu de données de test d’exclusion. L’axe horizontal représente la moyenne de la valeur réelle pour le groupe, avec la taille de la bulle indiquant la fréquence ou le nombre de valeurs dans cette plage. L’axe vertical est l’erreur résiduelle moyenne.

![Graphique de l’erreur résiduel](media/service-machine-learning-automated/automated-machine-learning-power-bi-15.png)

Le rapport de modèle de régression inclut également une page de détails de la formation comme les rapports pour les autres types de modèles, comme décrit dans la section **rapport de modèle AutoML** ci-dessus.

### <a name="applying-a-regression-model"></a>Appliquer un modèle de régression

Pour appliquer un modèle de régression ML, vous devez spécifier l’entité avec les données d’entrée et le préfixe de nom de colonne de sortie.

![Appliquer une régression](media/service-machine-learning-automated/automated-machine-learning-power-bi-16.png)

Lorsqu’un modèle de régression est appliqué, il ajoute deux colonnes de sortie à l’entité de sortie enrichie. Il s’agit de la **PredictionValue**, et **PredictionExplanation**. Les noms de colonnes dans l’entité ont le préfixe spécifié lorsque le modèle est appliqué.

Le **PredictionValue** colonne contient la valeur prévue pour l’enregistrement basé sur les champs d’entrée. Le **PredictionExplanation** colonne contient une explication avec l’influence spécifique présentant les fonctionnalités d’entrée sur le **PredictionValue**. Il s’agit d’une collection au format JSON de poids des fonctionnalités d’entrée.

## <a name="next-steps"></a>Étapes suivantes

Cet article fourni une vue d’ensemble de l’apprentissage d’automatisée pour les flux de données dans le service Power BI. Les articles suivants peuvent également être utiles.

* [Tutoriel : Générer un modèle de Machine Learning dans Power BI (version préliminaire)](service-tutorial-build-machine-learning-model.md)
* [Tutoriel : Utilisation de Cognitive Services dans Power BI](service-tutorial-use-cognitive-services.md)
* [Tutoriel : Appeler un modèle Machine Learning Studio dans Power BI (préversion)](service-tutorial-invoke-machine-learning-model.md)
* [Cognitive Services dans Power BI (préversion)](service-cognitive-services.md)
* [Intégration d’Azure Machine Learning dans Power BI (préversion)](service-machine-learning-integration.md)

Pour plus d’informations sur les flux de données, lisez les articles suivants :
* [Créer et utiliser des flux de données dans Power BI](service-dataflows-create-use.md)
* [À l’aide d’entités calculées sur Power BI Premium](service-dataflows-computed-entities-premium.md)
* [À l’aide de flux de données avec des sources de données locales](service-dataflows-on-premises-gateways.md)
* [Ressources du développeur pour les flux de données Power BI](service-dataflows-developer-resources.md)
* [Flux de données et intégration à Azure Data Lake (préversion)](service-dataflows-azure-data-lake-integration.md)


