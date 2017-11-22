---
title: "Didacticiel : Intégration de Power BI avec Microsoft Flow"
description: "Apprenez à créer des flux déclenchés par des alertes de données Power BI."
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: YhmNstC39Mw
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/30/2017
ms.author: mihart
ms.openlocfilehash: efab2e6be1d376a0da70c13bb66144ba34afa58c
ms.sourcegitcommit: f2b38777ca74c28f81b25e2f739e4835a0ffa75d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="microsoft-flow-and-power-bi"></a>Microsoft Flow et Power BI

[Microsoft Flow](https://flow.microsoft.com/en-us/documentation/getting-started) est une offre SaaS pour l’automatisation des flux de travail dans un nombre croissant d’applications et de services SaaS dont dépendent les utilisateurs professionnels. Flow vous permet d’automatiser des tâches en intégrant vos applications et services favoris (y compris Power BI) pour obtenir des notifications, synchroniser des fichiers, collecter des données et bien plus encore. Les tâches répétitives sont simplifiées grâce à l’automatisation des flux de travail.

[Prenez en main Flow dès maintenant.](https://flow.microsoft.com/documentation/getting-started)

Découvrez la façon dont Sirui crée un flux qui envoie un message détaillé à ses collègues quand une alerte Power BI est déclenchée. Suivez ensuite les instructions détaillées sous la vidéo pour essayer vous-même.

<iframe width="560" height="315" src="https://www.youtube.com/embed/YhmNstC39Mw" frameborder="0" allowfullscreen></iframe>

## <a name="create-a-flow-that-is-triggered-by-a-power-bi-data-alert"></a>Créer un flux déclenché par une alerte de données Power BI
Ce didacticiel vous montre comment créer deux flux différents : un à partir d’un modèle et l’autre à partir de zéro. Pour suivre la procédure, [créez une alerte de données dans Power BI](service-set-data-alerts.md) et [inscrivez-vous gratuitement à Microsoft Flow](https://flow.microsoft.com/en-us/#home-signup).

## <a name="create-a-flow-that-uses-power-bi---from-a-template"></a>Créer un flux qui utilise Power BI - à partir d’un modèle
Dans cette tâche, vous allez utiliser un modèle pour créer un simple flux qui est déclenché par une alerte de données Power BI (notification).

1. Connectez-vous à Microsoft Flow (flow.microsoft.com).
2. Sélectionnez **Mes flux**.
   
   ![](media/service-flow-integration/power-bi-my-flows.png)
3. Sélectionnez **Créer à partir d’un modèle**.
   
    ![](media/service-flow-integration/power-bi-template.png)
4. Utilisez la zone de recherche pour rechercher des modèles Power BI et sélectionnez **Post a message to a Slack channel when a Power BI data alert is triggered** (Envoyer un message à un canal Slack quand une alerte de données Power BI est déclenchée).
   
    ![](media/service-flow-integration/power-bi-template2.png)
5. Sélectionnez **Utiliser ce modèle**.
   
   ![](media/service-flow-integration/power-bi-use-template.png)
6. Si vous y êtes invité, connectez-vous à Slack et Power BI en sélectionnant **Se connecter**, puis suivez les invites. Une coche verte vous permet de savoir que vous êtes connecté.  Après avoir confirmé vos connexions, sélectionnez **Continuer**.
   
   ![](media/service-flow-integration/power-bi-flow-signin.png)

### <a name="build-the-flow"></a>Créer le flux
Ce modèle a un déclencheur (alerte de données Power BI en cas de nouvelles médailles Olympiques pour l’Irlande) et une action (publier un message dans Slack). Lorsque vous sélectionnez un champ, Flow affiche du contenu dynamique que vous pouvez inclure.  Dans cet exemple, nous avons inclus la valeur de vignette et l’URL de vignette dans le corps du message.

![](media/service-flow-integration/power-bi-flow-template.png)

1. Dans la liste déroulante des déclencheurs, sélectionnez une alerte de données Power BI. Sélectionnez **New medal for Ireland** (Nouvelle médaille pour l’Irlande). Pour savoir comment créer une alerte, voir [Alertes de données dans Power BI](service-set-data-alerts.md).
   
   ![](media/service-flow-integration/power-bi-trigger-flow.png)
2. Pour publier sur Slack, entrez un nom de canal et un texte message (vous pouvez également sélectionner le message par défaut que Flow crée). Notez le contenu dynamique que nous avons inclus dans le champ de texte du message.
   
   > [!NOTE]
   > Incluez « @ » au début du nom de votre canal.  Par exemple, si le canal Slack est nommé « channelA », dans Flow, entrez « @channelA ».
   > 
   > 
   
   ![](media/service-flow-integration/power-bi-flow-slacker.png)
3. Lorsque vous avez terminé, sélectionnez **Créer un flux** ou **Enregistrer le flux**.  Le flux est créé et évalué.  Flow vous indique s’il trouve des erreurs.
4. S’il en détecte, sélectionnez **Modifier le flux** pour les corriger ; sinon, sélectionnez **Terminé** pour exécuter le nouveau flux.
   
   ![](media/service-flow-integration/power-bi-flow-running.png)
5. Ouvrez votre compte Slack pour afficher le message.  
   
   ![](media/service-flow-integration/power-bi-slack-message.png)

## <a name="create-a-flow-that-uses-power-bi---from-scratch-blank"></a>Créer entièrement un flux qui utilise Power BI
Dans cette tâche, vous allez créer entièrement un simple flux qui est déclenché par une alerte de données Power BI (notification).

1. Connectez-vous à Microsoft Flow.
2. Sélectionnez **Mes flux** > **Créer entièrement**.
   
   ![](media/service-flow-integration/power-bi-my-flows.png)
3. Utilisez la zone de recherche pour trouver un déclencheur Power BI, puis sélectionnez **Déclencher un flux avec une alerte de données Power BI**.

### <a name="build-your-flow"></a>Créer votre flux
1. Dans la liste déroulante, sélectionnez le nom de l’alerte.  Pour savoir comment créer une alerte, voir [Alertes de données dans Power BI](service-set-data-alerts.md).
   
    ![](media/service-flow-integration/power-bi-totalstores.png)
2. Sélectionnez **Nouvelle étape** > **Ajouter une action**.
   
   ![](media/service-flow-integration/power-bi-new-step.png)
3. Recherchez **Outlook** et sélectionnez **Créer un événement**.
   
   ![](media/service-flow-integration/power-bi-create-event.png)
4. Complétez les champs de l’événement. Lorsque vous sélectionnez un champ, Flow affiche du contenu dynamique que vous pouvez inclure.
   
   ![](media/service-flow-integration/power-bi-flow-event.png)
5. Quand vous avez terminé, sélectionnez **Créer un flux**.  Flow enregistre et évalue le flux. S’il n’y a pas d’erreurs, sélectionnez **Terminé** pour exécuter ce flux.  Le nouveau flux est ajouté à votre page **Mes flux**.
   
   ![](media/service-flow-integration/power-bi-flow-running.png)
6. Lorsque le flux est déclenché par l’alerte de données Power BI, vous recevez une notification d’événement Outlook semblable à celle-ci.
   
    ![](media/service-flow-integration/power-bi-flow-notice.png)

## <a name="next-steps"></a>Étapes suivantes
* [Prise en main de Microsoft Flow](https://flow.microsoft.com/en-us/documentation/getting-started/)
* [Définir des alertes de données dans le service Power BI](service-set-data-alerts.md)
* [Définir des alertes de données sur votre iPhone](mobile-set-data-alerts-in-the-mobile-apps.md)
* [Définir des alertes dans l’application mobile Power BI pour Windows 10](mobile-set-data-alerts-in-the-mobile-apps.md)
* D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)

