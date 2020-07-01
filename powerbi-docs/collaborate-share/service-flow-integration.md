---
title: Intégration de Power BI à Power Automate
description: Découvrez comment créer des flux Power Automate déclenchés par des alertes de données Power BI.
author: maggiesMSFT
ms.reviewer: ''
featuredvideoid: YhmNstC39Mw
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 02/25/2020
ms.author: maggies
LocalizationGroup: Get started
ms.openlocfilehash: 85d3ab05359094fbc0bd05b0fdb70fb73e4acec8
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85226176"
---
# <a name="power-automate-and-power-bi"></a>Power Automate et Power BI

[Power Automate](https://docs.microsoft.com/power-automate/getting-started) est une offre SaaS pour l’automatisation des workflows dans un nombre croissant d’applications et de services SaaS sur lesquels les utilisateurs professionnels s’appuient. Power Automate vous permet d’automatiser des tâches en intégrant vos applications et services favoris (y compris Power BI) pour obtenir des notifications, synchroniser des fichiers, collecter des données et bien plus encore. Les tâches répétitives sont simplifiées grâce à l’automatisation des flux de travail.

[Prise en main à l’aide de Power Automate maintenant.](https://docs.microsoft.com/power-automate/getting-started)

Effectuer le suivi de Sirui crée un flux Power Automate qui envoie un e-mail détaillé à des collègues quand une alerte Power BI est déclenchée. Suivez ensuite les instructions détaillées sous la vidéo pour essayer vous-même.

<iframe width="560" height="315" src="https://www.youtube.com/embed/YhmNstC39Mw" frameborder="0" allowfullscreen></iframe>

## <a name="create-a-flow-that-is-triggered-by-a-power-bi-data-alert"></a>Créer un flux déclenché par une alerte de données Power BI

### <a name="prerequisites"></a>Conditions préalables
Ce didacticiel vous montre comment créer deux flux différents : un à partir d’un modèle et l’autre à partir de zéro. Pour la suite, [créez une alerte de données dans Power BI](../create-reports/service-set-data-alerts.md), créez un compte Slack gratuit et [inscrivez-vous gratuitement à Power Automate](https://flow.microsoft.com/#home-signup).

## <a name="create-a-flow-that-uses-power-bi---from-a-template"></a>Créer un flux qui utilise Power BI - à partir d’un modèle
Dans cette tâche, nous utilisons un modèle pour créer un flux simple qui déclenche par un alerte de données Power BI (notification).

1. Connectez-vous à Power Automate (flow.microsoft.com).
2. Sélectionnez **Mes flux**.
   
   ![Barre de menus Power Automate](media/service-flow-integration/power-bi-my-flows.png)
3. Sélectionnez **Créer à partir d’un modèle**.
   
    ![Barre de menus Mes flux](media/service-flow-integration/power-bi-template.png)
4. Utilisez la zone de recherche pour trouver des modèles Power BI et sélectionnez **Envoyer un e-mail à n’importe quelle audience quand une alerte de données Power BI est déclenchée > Continuer**.
   
    ![résultats de la recherche](media/service-flow-integration/power-bi-flow-alert.png)


### <a name="build-the-flow"></a>Créer le flux
Ce modèle a un déclencheur (alerte de données Power BI en cas de nouvelles médailles olympiques pour l’Irlande) et une action (envoyer un e-mail). Lorsque vous sélectionnez un champ, Power Automate affiche un contenu dynamique que vous pouvez inclure.  Dans cet exemple, nous incluons la valeur et l’URL de la mosaïque dans le corps du message.

![modèle de flux](media/service-flow-integration/power-bi-template1.png)

1. Dans la liste déroulante des déclencheurs, sélectionnez une alerte de données Power BI. Sélectionnez **New medal for Ireland** (Nouvelle médaille pour l’Irlande). Pour savoir comment créer une alerte, voir [Alertes de données dans Power BI](../create-reports/service-set-data-alerts.md).
   
   ![liste déroulante des alertes](media/service-flow-integration/power-bi-trigger-flow.png)
2. Entrez une ou plusieurs adresses e-mail valides, puis sélectionnez **Modifier** (voir ci-dessous) ou **Ajouter du contenu dynamique**. 
   
   ![écran Envoyer un e-mail](media/service-flow-integration/power-bi-flow-email.png)

3. Power Automate crée un titre et un message que vous pouvez conserver ou modifier. Toutes les valeurs définies lors de la création de l’alerte dans Power BI sont utilisables : placez simplement votre curseur dessus et sélectionnez-les dans la zone grise en surbrillance. 

   ![écran Envoyer un e-mail](media/service-flow-integration/power-bi-flow-email-default.png)

1.  Par exemple, si vous avez créé le titre d’alerte **Nous avons gagné une autre médaille** dans Power BI, vous pouvez sélectionner **Titre de l’alerte** pour ajouter ce texte au champ Objet de votre adresse e-mail.

    ![créer le texte de l’e-mail](media/service-flow-integration/power-bi-flow-message.png)

    De même, vous pouvez accepter le corps de l’e-mail par défaut ou créer le vôtre. Dans l’exemple ci-dessus, quelques modifications ont été apportées au message.

1. Lorsque vous avez terminé, sélectionnez **Créer un flux** ou **Enregistrer le flux**.  Le flux est créé et évalué.  Power Automate vous indique s’il trouve des erreurs.
2. S’il en détecte, sélectionnez **Modifier le flux** pour les corriger ; sinon, sélectionnez **Terminé** pour exécuter le nouveau flux.
   
   ![message de réussite](media/service-flow-integration/power-bi-flow-running.png)
5. Lorsque l’alerte de données se déclenche, un e-mail est envoyé aux adresses que vous avez indiquées.  
   
   ![e-mail d’alerte](media/service-flow-integration/power-bi-flow-email2.png)

## <a name="create-a-power-automate-that-uses-power-bi---from-scratch-blank"></a>Créer un Power Automate qui utilise Power BI - à partir de zéro (vide)
Dans cette tâche, nous créons un flux simple à partir de zéro, déclenché par une alerte de données Power BI (notification).

1. Connectez-vous à Power Automate.
2. Sélectionnez **Mes flux** > **Créer entièrement**.
   
   ![Barre de menus supérieure Power Automate](media/service-flow-integration/power-bi-my-flows.png)
3. Utilisez la zone de recherche pour trouver un déclencheur Power BI et sélectionnez **Power BI - quand une alerte de données est déclenchée**.

### <a name="build-your-flow"></a>Créer votre flux
1. Dans la liste déroulante, sélectionnez le nom de l’alerte.  Pour savoir comment créer une alerte, voir [Alertes de données dans Power BI](../create-reports/service-set-data-alerts.md).
   
    ![sélectionner le nom de l’alerte](media/service-flow-integration/power-bi-totalstores2.png)
2. Sélectionnez **Nouvelle étape** > **Ajouter une action**.
   
   ![ajouter une nouvelle étape](media/service-flow-integration/power-bi-new-step.png)
3. Recherchez **Outlook** et sélectionnez **Créer un événement**.
   
   ![créer le flux](media/service-flow-integration/power-bi-create-event.png)
4. Complétez les champs de l’événement. Lorsque vous sélectionnez un champ, Power Automate affiche un contenu dynamique que vous pouvez inclure.
   
   ![continuer à créer le flux](media/service-flow-integration/power-bi-flow-event.png)
5. Quand vous avez terminé, sélectionnez **Créer un flux**.  Power Automate enregistre et évalue le flux. S’il n’y a pas d’erreurs, sélectionnez **Terminé** pour exécuter ce flux.  Le nouveau flux est ajouté à votre page **Mes flux**.
   
   ![terminer le flux](media/service-flow-integration/power-bi-flow-running.png)
6. Lorsque le flux est déclenché par l’alerte de données Power BI, vous recevez une notification d’événement Outlook semblable à celle-ci.
   
    ![Power Automate déclenche une notification Outlook](media/service-flow-integration/power-bi-flow-notice.png)

## <a name="next-steps"></a>Étapes suivantes
* [Bien démarrer avec Power Automate](https://docs.microsoft.com/power-automate/getting-started/)
* [Définir des alertes de données dans le service Power BI](../create-reports/service-set-data-alerts.md)
* [Définir des alertes de données sur votre iPhone](../consumer/mobile/mobile-set-data-alerts-in-the-mobile-apps.md)
* [Définir des alertes dans l’application mobile Power BI pour Windows 10](../consumer/mobile/mobile-set-data-alerts-in-the-mobile-apps.md)
* D’autres questions ? [Posez vos questions à la communauté Power BI](https://community.powerbi.com/)
