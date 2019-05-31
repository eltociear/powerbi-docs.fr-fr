---
title: 'Tutoriel : Générer un modèle de Machine Learning dans Power BI (version préliminaire)'
description: Dans ce didacticiel, vous générez un modèle d’apprentissage dans Power BI.
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
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "61406747"
---
# <a name="tutorial-build-a-machine-learning-model-in-power-bi-preview"></a>Tutoriel : Générer un modèle de Machine Learning dans Power BI (version préliminaire)

Dans cet article du didacticiel, vous allez utiliser **automatisé Machine Learning** pour créer et appliquer un modèle de prédiction binaire dans Power BI. Le didacticiel comprend des conseils pour la création d’un flux de données Power BI et utilisation des entités définies dans le flux de données pour former et de valider un modèle machine learning directement dans Power BI. Ensuite, nous utilisons ce modèle pour calculer les scores pour générer des prédictions.

Tout d’abord, vous allez créer une prédiction binaire modèle machine learning, afin de prédire l’intention d’achat des clients en ligne basé sur un ensemble de leurs attributs de la session en ligne. Un jeu de données de test d’évaluation machine learning est utilisé pour cet exercice. Une fois qu’un modèle est formé, Power BI génère automatiquement un rapport de validation expliquant les résultats du modèle. Vous pouvez ensuite consulter le rapport de validation et le modèle est appliqué à vos données pour calculer les scores.

Ce didacticiel comprend les étapes suivantes :

> [!div class="checklist"]
> * Créer un flux de données avec les données d’entrée
> * Créer et former un modèle d’apprentissage automatique
> * Passez en revue le rapport de validation de modèle
> * Le modèle est appliqué à une entité de flux de données
> * À l’aide de la sortie au score calculé à partir du modèle dans un rapport Power BI

## <a name="create-a-dataflow-with-the-input-data"></a>Créer un flux de données avec les données d’entrée

La première partie de ce didacticiel consiste à créer un flux de données avec des données d’entrée. Ce processus prend quelques étapes, comme indiqué dans les sections suivantes, à partir de l’obtention de données.

### <a name="get-data"></a>Obtenir les données

La première étape de création d’un flux de données est d’avoir vos sources de données prêts. Dans notre cas, nous utilisons un jeu de données d’apprentissage à partir d’un ensemble de sessions en ligne, certains d'entre eux débouché sur un achat. Le jeu de données contient un ensemble d’attributs relatives à ces sessions, nous allons utiliser pour la formation de notre modèle.

Vous pouvez télécharger le jeu de données depuis le site Web de UC Irvine.  Nous avons également ce disponibles pour les besoins de ce didacticiel, à partir du lien suivant : [online_shoppers_intention.csv](https://raw.githubusercontent.com/santoshc1/PowerBI-AI-samples/master/Tutorial_AutomatedML/online_shoppers_intention.csv).

### <a name="create-the-entities"></a>Créer les entités

Pour créer les entités dans votre flux de données, connectez-vous au service Power BI et accédez à un espace de travail sur votre capacité dédiée où la préversion IA est activée.

Si vous ne disposez pas d’un espace de travail, vous pouvez en créer un en sélectionnant **espaces de travail** dans le menu de navigation de gauche dans le service Power BI, puis sélectionnez **créer l’espace de travail application** en bas du panneau qui s’affiche. Cette opération ouvre un panneau sur la droite pour entrer les détails de l’espace de travail. Entrez un nom d’espace de travail et sélectionnez **avancé**. Vérifiez que l’espace de travail utilise une capacité dédiée à l’aide de la case d’option et qu’il est affecté à une instance de capacité dédiée qui a l’aperçu d’intelligence artificielle sous tension. Ensuite, sélectionnez **Enregistrer**.

![Créer un espace de travail](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-01.png)

Une fois l’espace de travail est créé, vous pouvez sélectionner **Skip** dans la partie inférieure droite de l’écran d’accueil, comme illustré dans l’image suivante.

![Ignorer si vous disposez d’un espace de travail](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-02.png)

Sélectionnez le **le flux de données (version préliminaire)** onglet. Sélectionnez le **créer** bouton en haut à droit de l’espace de travail et sélectionnez **flux de données**.

![Créer des flux de données](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-03.png)

Sélectionnez **Ajouter de nouvelles entités**. Cette action lance une **Power Query** éditeur dans le navigateur.

![Ajouter une nouvelle entité](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-04.png)

Sélectionnez **fichier texte/CSV** comme source de données, illustré dans l’image suivante.

![Fichier texte/CSF sélectionné](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-05.png)

Dans le **se connecter à une source de données** qui apparaît en regard, collez le lien suivant pour le *online_shoppers_intention.csv* dans le **chemin d’accès de fichier ou URL** zone, puis sélectionnez  **Suivant**.

`https://raw.githubusercontent.com/santoshc1/PowerBI-AI-samples/master/Tutorial_AutomatedML/online_shoppers_intention.csv`

![Chemin d’accès de fichier](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-06.png)

L’éditeur de requête Power affiche un aperçu des données à partir du fichier CSV. Sélectionnez **transformer une Table** dans le ruban de la commande, puis sélectionnez **utiliser la première ligne comme en-têtes** dans le menu qui s’affiche. Cette opération ajoute le _promues en-têtes_ étape de requête dans le **étapes appliquées** sur la droite de l’écran. Vous pouvez renommer la requête à un nom plus convivial en modifiant la valeur dans le **nom** zone trouvé dans le volet droit. Par exemple, vous pouvez changer le nom de requête à _visiteur en ligne_.

![Remplacez par un nom convivial](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-07.png)

Certains des types de données d’attribut dans ce jeu de données sont _numérique_ ou _booléenne_, bien que ceux-ci peuvent être interprétés en tant que chaînes par **Power Query**. Sélectionnez l’icône de type d’attribut en haut de chaque en-tête de colonne pour changer les colonnes répertoriées ci-dessous pour les types suivants :

* **Nombre décimal :** Administrative_Duration ; Informational_Duration ; ProductRelated_Duration ; BounceRates ; ExitRates ; PageValues ; SpecialDay
* **True/False :** Week-end ; Chiffre d’affaires

![Modifier le type de données](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-08.png)

Le **prédiction binaire** modèle que nous allons former requiert un champ booléen en tant qu’étiquette identifiant les résultats à partir des observations passées. Dans ce jeu de données, le _chiffre d’affaires_ attribut indique achat, et cet attribut est déjà disponible en tant que valeur booléenne. Par conséquent, nous n’avez pas besoin d’ajouter une colonne calculée pour l’étiquette. Dans les autres jeux de données, vous devrez transformer les attributs d’étiquette existant en une colonne de valeurs booléennes.

Sélectionnez le **fait** bouton pour fermer l’éditeur Power Query. Voici la liste des entités avec le _visiteurs Online_ nous avons ajouté des données. Sélectionnez **enregistrer** dans l’angle supérieur droit, fournissez un nom pour le flux de données, puis sélectionnez **enregistrer** dans la boîte de dialogue, comme illustré dans l’image suivante.

![Enregistrer le flux de données](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-09.png)

### <a name="refresh-the-dataflow"></a>Actualiser le flux de données

Enregistrer les résultats de flux de données dans une notification en cours s’affiche, indiquant que votre flux de données a été enregistré. Sélectionnez **Actualiser maintenant** pour recevoir les données à partir de la source dans le flux de données.

![Actualiser maintenant](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-10.png)

Sélectionnez **Fermer** dans le coin supérieur droit et attendez que l’actualisation du flux de données soit terminée.

Vous pouvez également actualiser votre flux de données à l’aide de la **Actions** commandes. Le flux de données affiche l’horodatage lorsque l’actualisation est terminée.

![Horodatage de l’actualisation](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-11.png)

## <a name="create-and-train-a-machine-learning-model"></a>Créer et former un modèle d’apprentissage automatique

Sélectionnez le flux de données une fois l’actualisation terminée. Pour ajouter un modèle d’apprentissage automatique, sélectionnez le **modèle ML appliquer** situé dans le **Actions** liste pour l’entité de base qui contient vos informations de données et l’étiquette de formation, puis sélectionnez **ajouter une modèle d’apprentissage automatique**.

![Ajouter un modèle Machine Learning](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-12.png)

La première étape pour la création de notre modèle d’apprentissage automatique consiste à identifier les données d’historique, y compris le champ d’étiquette que vous souhaitez prédire. Le modèle est créé par apprentissage à partir de ces données.

Dans le cas le jeu de données que nous utilisons, il s’agit du **chiffre d’affaires** champ. Sélectionnez **chiffre d’affaires** en tant que la valeur « historique de résultat field » puis **suivant**.

![Sélectionnez les données d’historique](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-13.png)

Ensuite, nous devons sélectionner le type de modèle pour créer d’apprentissage. Power BI analyse les valeurs dans le champ Historique de résultat que vous avez identifié et suggère les types de modèles d’apprentissage automatique qui peuvent être créés pour prédire ce champ.

Dans ce cas, étant donné que nous allons prédire un résultat binaire de si un utilisateur effectue un achat ou non, sélectionnez **prédiction binaire** pour le type de modèle, puis sélectionnez suivant.

![PRÉDICTION binaire sélectionnée](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-14.png)

Ensuite, Power BI procède à une analyse préliminaire des données et suggère les entrées que le modèle peut utiliser. Vous avez la possibilité de personnaliser les champs d’entrée utilisés pour le modèle. Dans notre jeu de données organisé pour sélectionner tous les champs, sélectionnez la case à cocher en regard du nom de l’entité. Sélectionnez **suivant** pour accepter les entrées.

![Activez la case à cocher suivante](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-15.png)

Dans la dernière étape, nous devons fournir un nom pour notre modèle, ainsi que les étiquettes conviviales pour les résultats à utiliser dans le rapport généré automatiquement qui résume les résultats de la validation du modèle. Ensuite, vous pouvez nommer le modèle _achat intention prédiction_et les étiquettes true et false comme _achat_ et _non-achat_. Ensuite, sélectionnez **Enregistrer**.

![Enregistrer le modèle](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-16.png)

Notre modèle d’apprentissage automatique est maintenant prêt pour l’apprentissage. Sélectionnez **Actualiser maintenant** pour démarrer l’apprentissage du modèle.

![Actualiser maintenant](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-17.png)

Commence le processus d’apprentissage via un échantillonnage et de normalisation de vos données historiques et de fractionnement de votre jeu de données en deux nouvelles entités *données d’apprentissage achat intention prédiction* et *achat intention prédiction test Données*.

Selon la taille du jeu de données, le processus d’apprentissage peut durer de quelques minutes à quelques heures. À ce stade, vous pouvez voir le modèle dans le **d’apprentissage des modèles** onglet du flux de données. Le _prêt_ état indique que le modèle en file d’attente pour l’apprentissage ou qu’il est couvert par la formation.

![Prêt pour l’apprentissage](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-18.png)

Lorsque le modèle est la formation, il se peut que vous ne pourrez pas afficher ou modifier le flux de données. Vous pouvez vérifier que le modèle a été formé et validés via l’état de flux de données. Il peut s’agit d’une actualisation des données en cours dans le **flux de données** onglet de l’espace de travail.

![Dans le processus](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-19.png)

Une fois que l’apprentissage du modèle est terminé, le flux de données affiche une heure d’actualisation mis à jour. Vous pouvez vérifier que le modèle est formé, en accédant à la **d’apprentissage des modèles** onglet dans le flux de données. Le modèle que vous avez créé doit afficher l’état en tant que **ajouté pour l’apprentissage** et **dernier formé** doit maintenant être mise à jour.

![Dernier formé sur](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-20.png)

## <a name="review-the-model-validation-report"></a>Passez en revue le rapport de validation de modèle

Pour passer en revue le rapport de validation de modèle, dans le **modèles d’apprentissage automatique, s** choisir le **afficher le rapport de performances et d’appliquer le modèle** situé dans le **Actions** colonne du modèle . Ce rapport décrit la façon dont votre modèle d’apprentissage automatique est susceptible de s’exécuter.

Dans le **performances d’un modèle** page du rapport, sélectionnez **facteurs d’influence clés** pour afficher les PRÉDICTEURS supérieurs pour votre modèle. Vous pouvez sélectionner parmi prédicateurs pour voir comment la distribution de résultat associé à cette prédiction.

![Performances du modèle](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-21.png)

Vous pouvez utiliser la **seuil de probabilité** segment dans la page de performances d’un modèle pour examiner son influence sur la précision et le rappel pour le modèle.

![Seuil de probabilité](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-22.png)

Les autres pages du rapport décrivent les mesures de performances de statistiques pour le modèle.

Le rapport inclut également une page de détails de la formation qui décrit les différentes itérations ont été exécutées, comment les fonctionnalités ont été extraits à partir des entrées et les hyperparamètres pour le modèle final utilisé.

## <a name="apply-the-model-to-a-dataflow-entity"></a>Le modèle est appliqué à une entité de flux de données

Sélectionnez le **Appliquer modèle** bouton en haut du rapport pour appeler ce modèle lorsque le flux de données est actualisé. Dans le **appliquer** boîte de dialogue, vous pouvez spécifier l’entité cible qui comporte les données sources à laquelle le modèle doit être appliqué.

![Appliquer le modèle](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-23.png)

Lorsque vous y êtes invité, vous devez **Actualiser** le flux de données à prévisualiser les résultats de votre modèle.

Appliquer le modèle créera une nouvelle entité, avec le suffixe **enrichi < model_name >** ajouté à l’entité à laquelle vous avez appliqué le modèle. Dans notre cas, applique le modèle pour le **OnlineShoppers** entité créera **OnlineShoppers enrichi achat intention prédiction**, qui inclut la sortie prévue à partir du modèle.

L’application d’un modèle de prédiction binaire ajoute trois colonnes avec le résultat prédit, un score de probabilité et les principaux facteurs d’influence spécifiques à l’enregistrement pour la prédiction, chacune préfixée par le nom de colonne spécifié.

![Trois colonnes de résultat](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-24.png)

En raison d’un problème connu, les colonnes de résultat évalué de l’entité enrichie sont uniquement accessibles à partir de Power BI Desktop. Pour afficher un aperçu dans le service, vous devez utiliser une entité aperçu spécial.

Une fois l’actualisation de flux de données est terminée, vous pouvez sélectionner le **OnlineShoppers enrichi achat intention prédiction aperçu** entité pour afficher les résultats.

![Afficher les résultats](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-25.png)

## <a name="using-the-scored-output-from-the-model-in-a-power-bi-report"></a>À l’aide de la sortie au score calculé à partir du modèle dans un rapport Power BI

Pour utiliser la sortie au score calculé à partir de votre modèle d’apprentissage, vous pouvez vous connecter à votre flux de données à partir du bureau de Power BI, à l’aide du connecteur de flux de données. Le **OnlineShoppers enrichi achat intention prédiction** entité peut maintenant être utilisée pour incorporer les prédictions à partir de votre modèle dans les rapports Power BI.

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous créé et appliqué un modèle de prédiction binaire dans Power BI en suivant ces étapes :

* Créer un flux de données avec les données d’entrée
* Créer et former un modèle d’apprentissage automatique
* Passez en revue le rapport de validation de modèle
* Le modèle est appliqué à une entité de flux de données
* À l’aide de la sortie au score calculé à partir du modèle dans un rapport Power BI

Pour plus d’informations sur l’automatisation dans Machine Learning dans Power BI, consultez [automatisée de Machine Learning dans Power BI (version préliminaire)](service-machine-learning-automated.md).
