---
title: 'Tutoriel : Créer un modèle Machine Learning dans Power BI (préversion)'
description: Dans ce didacticiel, vous allez créer un modèle Machine Learning dans Power BI.
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.custom: connect-to-services
ms.topic: tutorial
ms.date: 03/29/2019
ms.author: davidi
LocalizationGroup: Connect to services
ms.openlocfilehash: 611d6f6c923e6cb68af94840c4266a0b6dee7651
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "61406747"
---
# <a name="tutorial-build-a-machine-learning-model-in-power-bi-preview"></a>Tutoriel : Créer un modèle Machine Learning dans Power BI (préversion)

Dans cet article de didacticiel, vous utilisez le **Machine Learning automatisé** pour créer et appliquer un modèle de prédiction binaire dans Power BI. Ce didacticiel fournit des instructions pour créer un dataflow Power BI et utiliser les entités définies dans le dataflow pour former et valider un modèle Machine Learning directement dans Power BI. Nous utilisons ensuite ce modèle pour le scoring afin de générer des prédictions.

Tout d’abord, vous allez créer un modèle Machine Learning de prédiction binaire afin de prédire l’intention d’achat des acheteurs en ligne selon un ensemble d’attributs de session en ligne. Un jeu de données de référence Machine Learning est utilisé pour cet exercice. Une fois qu’un modèle est formé, Power BI génère automatiquement un rapport de validation expliquant les résultats du modèle. Vous pouvez ensuite passer en revue le rapport de validation et appliquer le modèle à vos données pour le scoring.

Ce didacticiel se compose des étapes suivantes :

> [!div class="checklist"]
> * Créer un dataflow avec les données d’entrée
> * Créer et effectuer l’apprentissage d’un modèle Machine Learning
> * Examiner le rapport de validation de modèle
> * Appliquer le modèle à une entité de dataflow
> * Utilisation de la sortie notée du modèle dans un rapport Power BI

## <a name="create-a-dataflow-with-the-input-data"></a>Créer un dataflow avec les données d’entrée

La première partie de ce didacticiel consiste à créer un dataflow avec des données d’entrée. Ce processus prend quelques étapes, comme indiqué dans les sections suivantes, en commençant par l’obtention des données.

### <a name="get-data"></a>Obtenir les données

La première étape de la création d’un dataflow consiste à préparer vos sources de données. Dans notre cas, nous utilisons un jeu de données Machine Learning à partir d’un ensemble de sessions en ligne, dont certaines ont abouti à un achat. Le jeu de données contient un ensemble d’attributs concernant ces sessions, que nous utiliserons pour la formation de notre modèle.

Vous pouvez télécharger le jeu de données à partir du site web d’UC Irvine.  Nous le proposons également, pour les besoins de ce didacticiel, au lien suivant : [online_shoppers_intention.csv](https://raw.githubusercontent.com/santoshc1/PowerBI-AI-samples/master/Tutorial_AutomatedML/online_shoppers_intention.csv).

### <a name="create-the-entities"></a>Créer les entités

Pour créer les entités dans votre flux de données, connectez-vous au service Power BI et accédez à un espace de travail sur votre capacité dédiée où la préversion IA est activée.

Si vous ne disposez pas déjà d’un espace de travail, vous pouvez en créer un en sélectionnant **Espaces de travail** dans le menu de navigation gauche du service Power BI, puis en sélectionnant **Créer un espace de travail d’application** en bas du panneau qui s’affiche. Cette opération ouvre un panneau sur la droite pour entrer les détails de l’espace de travail. Entrez un nom d’espace de travail et sélectionnez **Avancé**. Confirmez que l’espace de travail utilise une capacité dédiée à l’aide du bouton radio, et qu’il est affecté à une instance de capacité dédiée pour laquelle la préversion de l’intelligence artificielle est activée. Ensuite, sélectionnez **Enregistrer**.

![Créer un espace de travail](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-01.png)

Une fois que l’espace de travail a été créé, vous pouvez sélectionner **Ignorer** dans la partie inférieure droite de l’écran d’accueil, comme sur l’image suivante.

![Ignorez si vous disposez d’un espace de travail](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-02.png)

Sélectionnez l'onglet **Dataflows (préversion)** . Sélectionnez le bouton **Créer** en haut à droit de l’espace de travail, puis **Dataflow**.

![Créer un dataflow](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-03.png)

Sélectionnez **Ajouter de nouvelles entités**. Un éditeur **Power Query** est lancé dans le navigateur.

![Ajouter une nouvelle entité](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-04.png)

Sélectionnez **Fichier texte/CSV** comme source de données, comme indiqué dans l’image suivante.

![Fichier texte/CSV sélectionné](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-05.png)

Dans la zone **Connexion à une source de données** qui s’affiche ensuite, collez le lien suivant vers le fichier *online_shoppers_intention.csv* dans la zone **Chemin ou URL du fichier**, puis sélectionnez **Suivant**.

`https://raw.githubusercontent.com/santoshc1/PowerBI-AI-samples/master/Tutorial_AutomatedML/online_shoppers_intention.csv`

![Chemin de fichier](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-06.png)

L’éditeur Power Query affiche un aperçu des données à partir du fichier CSV. Sélectionnez **Transformer une table** dans le ruban des commandes, puis sélectionnez **Utiliser les premières lignes comme en-têtes** dans le menu qui s’affiche. Cette opération ajoute l’étape de requête _En-têtes promus_ à la section **Étapes appliquées** sur la droite de l’écran. Vous pouvez renommer la requête en un nom plus convivial en modifiant la valeur dans la zone **Nom** dans le volet droit. Par exemple, vous pouvez remplacer le nom de la requête par _Visiteur en ligne_.

![Remplacer par un nom convivial](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-07.png)

Certains des types de données d’attribut dans ce jeu de données sont _numériques_ ou _booléens_, bien qu’ils puissent être interprétés comme des chaînes par **Power Query**. Sélectionnez l’icône de type d’attribut en haut de chaque en-tête de colonne pour modifier les colonnes répertoriées ci-dessous pour les types suivants :

* **Nombre décimal :** Administrative_Duration; Informational_Duration; ProductRelated_Duration; BounceRates; ExitRates; PageValues; SpecialDay
* **True/False :** Weekend; Revenue

![Modifier le type de données](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-08.png)

Le modèle de **prédiction binaire** que nous allons former requiert un champ booléen comme étiquette identifiant les résultats des observations passées. Dans ce jeu de données, l’attribut _Revenue_ indique l’achat, et cet attribut est déjà disponible en tant que valeur booléenne. Nous n’avons donc pas besoin d’ajouter une colonne calculée pour l’étiquette. Dans d’autres jeux de données, vous devrez peut-être transformer des attributs d’étiquette existants en une colonne booléenne.

Cliquez sur le bouton **Terminé** pour fermer l’éditeur Power Query. La liste des entités s’affiche avec les données des _Visiteurs en ligne_ que nous avons ajoutées. Sélectionnez **Enregistrer** dans le coin supérieur droit, fournissez un nom pour le dataflow, puis sélectionnez **Enregistrer** dans la boîte de dialogue, comme illustré dans l’image suivante.

![Enregistrer le dataflow](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-09.png)

### <a name="refresh-the-dataflow"></a>Actualiser le flux de données

L’enregistrement du dataflow entraîne l’affichage d’une notification indiquant que votre dataflow a été enregistré. Sélectionnez **Actualiser maintenant** pour ingérer des données provenant de la source dans le dataflow.

![Actualiser maintenant](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-10.png)

Sélectionnez **Fermer** dans le coin supérieur droit et attendez que l’actualisation du flux de données soit terminée.

Vous pouvez également actualiser votre dataflow avec les commandes **Actions**. Le dataflow affiche l’horodateur lorsque l’actualisation est terminée.

![Horodateur de l’actualisation](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-11.png)

## <a name="create-and-train-a-machine-learning-model"></a>Créer et effectuer l’apprentissage d’un modèle Machine Learning

Sélectionnez le dataflow une fois l’actualisation terminée. Pour ajouter un modèle Machine Learning, sélectionnez le bouton **Appliquer le modèle Machine Learning** dans la liste **Actions** de l’entité de base qui contient vos données d’apprentissage et informations d’étiquette, puis sélectionnez **Ajouter un modèle Machine Learning**.

![Ajouter un modèle Machine Learning](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-12.png)

La première étape pour créer notre modèle Machine Learning consiste à identifier les données historiques, y compris le champ d’étiquette que vous souhaitez prédire. Le modèle sera créé en apprenant à partir de ces données.

Dans le cas du jeu de données que nous utilisons, il s’agit du champ **Revenue**. Sélectionnez **Revenue** comme valeur du champ de résultat historique, puis sélectionnez **Suivant**.

![Sélectionner des données historiques](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-13.png)

Ensuite, vous devez sélectionner le type de modèle Machine Learning à créer. Power BI analyse les valeurs du champ de résultat historique que vous avez identifié et suggère les types de modèles Machine Learning qui peuvent être créés pour prédire ce champ.

Dans ce cas, étant donné que nous prévoyons un résultat binaire indiquant si un utilisateur effectue un achat ou non, sélectionnez **Prédiction binaire** pour le type de modèle, puis sélectionnez Suivant.

![Prédiction binaire sélectionnée](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-14.png)

Ensuite, Power BI effectue une analyse préliminaire des données et suggère les entrées que le modèle peut utiliser. Vous avez la possibilité de personnaliser les champs d’entrée utilisés pour le modèle. Dans notre jeu de données organisé, pour sélectionner tous les champs, activez la case à cocher en regard du nom de l’entité. Sélectionnez **Suivant** pour accepter les entrées.

![Cochez la case Suivant](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-15.png)

Pour la dernière étape, nous devons fournir un nom pour notre modèle, ainsi que les étiquettes conviviales pour les résultats à utiliser dans le rapport généré automatiquement qui synthétise les résultats de la validation du modèle. Ensuite, nous devons nommer le modèle _Prédiction d’intention d’achat_ et les étiquettes true et false _Achat_ et _Pas d’achat_. Ensuite, sélectionnez **Enregistrer**.

![Enregistrer le modèle](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-16.png)

Notre modèle Machine Learning est maintenant prêt pour la formation. Sélectionnez **Actualiser maintenant** pour commencer la formation du modèle.

![Actualiser maintenant](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-17.png)

Le processus d’apprentissage commence par échantillonner et normaliser vos données historiques et fractionner votre jeu de données en deux nouvelles entités, *Données d'apprentissage de prédiction d’intention d’achat* et *Données de test de prédiction d’intention d’achat*.

Selon la taille du jeu de données, le processus d’apprentissage peut durer de quelques minutes à plusieurs heures. À ce stade, vous pouvez voir le modèle sous l'onglet **Modèles Machine Learning** du dataflow. L’état _Prêt_ indique que le modèle a été mis en file d’attente pour l’apprentissage ou est en cours d’apprentissage.

![Prêt pour l’apprentissage](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-18.png)

Pendant la formation du modèle, vous ne pouvez pas afficher ou modifier le dataflow. Vous pouvez vérifier que le modèle est en cours de formation et de validation par le biais de l’état du dataflow. Il s’agit d’une actualisation des données en cours sous l’onglet **Dataflows** de l’espace de travail.

![In-process](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-19.png)

Une fois l’apprentissage du modèle terminé, le dataflow affiche une date d’actualisation mise à jour. Vous pouvez vérifier que le modèle est formé en accédant à l’onglet **Modèles Machine Learning** dans le dataflow. Le modèle que vous avez créé doit afficher l'état **Formé** et la date de **Dernier entraînement** doit être mise à jour.

![Dernier entraînement le](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-20.png)

## <a name="review-the-model-validation-report"></a>Examiner le rapport de validation de modèle

Pour consulter le rapport de validation de modèle, dans les **Modèles Machine Learning**, choisissez le bouton **Afficher le rapport de performances et appliquer le modèle** dans la colonne **Actions du modèle**. Ce rapport décrit les performances attendues de votre modèle Machine Learning.

Dans la page **Performances du modèle** du rapport , sélectionnez **Influenceurs clés** pour afficher les meilleures prédictions de votre modèle. Vous pouvez sélectionner une des prédictions pour voir comment la distribution des résultats est associée à cette prédiction.

![Performances du modèle](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-21.png)

Vous pouvez utiliser le segment **Seuil de probabilité** sur la page Performances du modèle pour examiner son influence sur la précision et le rappel pour le modèle.

![Seuil de probabilité](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-22.png)

Les autres pages du rapport décrivent les métriques de performance statistiques pour le modèle.

Le rapport comprend également une page de détails de formation qui décrit les différentes itérations exécutées, la façon dont les fonctionnalités ont été extraites des entrées et les hyperparamètres pour le modèle final utilisé.

## <a name="apply-the-model-to-a-dataflow-entity"></a>Appliquer le modèle à une entité de dataflow

Sélectionnez le bouton **Appliquer le modèle** en haut du rapport pour appeler ce modèle lorsque le dataflow est actualisé. Dans la boîte de dialogue **Appliquer**, vous pouvez spécifier l’entité cible qui contient les données source auxquelles le modèle doit être appliqué.

![Appliquer le modèle](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-23.png)

Quand vous y êtes invité, vous devez **Actualiser** le dataflow pour afficher un aperçu des résultats de votre modèle.

L’application du modèle créera une nouvelle entité, avec le suffixe **enriched <nom_modèle>** ajouté à l’entité à laquelle vous avez appliqué le modèle. Dans le cas présent, l’application du modèle à l’entité **OnlineShoppers** crée l’entité **OnlineShoppers enriched Prédiction d’intention d’achat**, qui comprend la sortie prédite du modèle.

L’application d’un modèle de prédiction binaire ajoute trois colonnes avec les résultats prédits, les scores de probabilité et les meilleurs influenceurs spécifiques aux enregistrements pour la prédiction, chacune avec le nom de colonne spécifié en préfixe.

![Trois colonnes de résultats](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-24.png)

En raison d’un problème connu, les colonnes de sortie notées dans l’entité enrichie sont uniquement accessibles à partir de Power BI Desktop. Pour afficher un aperçu de celles-ci dans le service, vous devez utiliser une entité d’aperçu spéciale.

Une fois l’actualisation du dataflow terminée, vous pouvez sélectionner l'entité **OnlineShoppers enriched Prédiction d’intention d’achat Preview** pour afficher les résultats.

![Afficher les résultats](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-25.png)

## <a name="using-the-scored-output-from-the-model-in-a-power-bi-report"></a>Utilisation de la sortie notée du modèle dans un rapport Power BI

Pour utiliser la sortie notée de votre modèle Machine Learning, vous pouvez vous connecter à votre dataflow à partir de Power BI Desktop avec le connecteur de dataflows. L'entité **OnlineShoppers enriched Prédiction d’intention d’achat** peut maintenant être utilisée pour incorporer les prédictions de votre modèle dans les rapports Power BI.

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez créé et appliqué un modèle de prédiction binaire dans Power BI à l’aide des étapes suivantes :

* Créer un dataflow avec les données d’entrée
* Créer et effectuer l’apprentissage d’un modèle Machine Learning
* Examiner le rapport de validation de modèle
* Appliquer le modèle à une entité de dataflow
* Utilisation de la sortie notée du modèle dans un rapport Power BI

Pour plus d’informations sur l’automatisation du Machine Learning dans Power BI, consultez [Machine Learning automatisé dans Power BI (préversion)](service-machine-learning-automated.md).
