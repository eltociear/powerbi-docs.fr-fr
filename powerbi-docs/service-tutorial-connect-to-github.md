---
title: 'Tutoriel : Se connecter à un référentiel GitHub avec Power BI'
description: Dans ce tutoriel, vous vous connectez à de vraies données disponibles dans le service GitHub à l’aide de Power BI, qui crée automatiquement des rapports et des tableaux de bord.
author: maggiesMSFT
manager: kfile
ms.reviewer: SarinaJoan
ms.service: powerbi
ms.subservice: powerbi-service
ms.custom: connect-to-services
ms.topic: tutorial
ms.date: 04/19/2019
ms.author: maggies
LocalizationGroup: Connect to services
ms.openlocfilehash: 3aeb1fc16ae200399125a2366a8993d45aad34c4
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "64578615"
---
# <a name="tutorial-connect-to-a-github-repo-with-power-bi"></a>Tutoriel : Se connecter à un référentiel GitHub avec Power BI
Dans ce tutoriel, vous vous connectez à de vraies données disponibles dans le service GitHub à l’aide de Power BI, qui crée automatiquement des rapports et des tableaux de bord. Vous vous connectez à Power BI content public repository (également appelé un *référentiel*) et consulter les réponses aux questions telles que : Combien de personnes contribuent au contenu public Power BI ? Qui y contribue le plus ? Quel jour de la semaine enregistre le plus de contributions ? Et d’autres questions. 

![Rapport GitHub dans Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-punch-card.png)

Ce tutoriel vous montre comment effectuer les étapes suivantes :

> [!div class="checklist"]
> * Demander un compte GitHub, si vous n’en avez pas encore 
> * Vous connecter au service avec votre compte Power BI, ou en demander un si vous n’en avez pas
> * Ouvrir le service Power BI
> * Rechercher l’application GitHub
> * Entrer les informations relatives au dépôt GitHub public dans Power BI
> * Afficher le tableau de bord et le rapport avec les données GitHub
> * Nettoyer les ressources en supprimant l’application

Si vous n’êtes pas inscrit à Power BI, [inscrivez-vous à un essai gratuit](https://app.powerbi.com/signupredirect?pbi_source=web) avant de commencer.

## <a name="prerequisites"></a>Conditions préalables

Pour suivre ce tutoriel, vous avez besoin d’un compte GitHub (demandez-en un si vous n’en avez pas). 

- Inscrivez-vous pour un [compte GitHub](https://docs.microsoft.com/contribute/get-started-setup-github).


## <a name="how-to-connect"></a>Comment se connecter
1. Connectez-vous au service Power BI (https://app.powerbi.com). 
2. Dans le volet de navigation de gauche, sélectionnez **Applications**, puis **Obtenir des applications**.
   
   ![Obtenir des applications - Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial.png) 

3. Sélectionnez **applications**, type **GitHub** dans la zone de recherche > **obtenez-le maintenant**.
   
   ![Obtenir GitHub - Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-app-source.png) 

4. Dans **installer cette application Power BI ?** sélectionnez **installer**.
5. Dans **votre nouvelle application est prête**, sélectionnez **accéder à l’application**.
6. Dans **prise en main votre nouvelle application**, sélectionnez **se connecter aux données**.

    ![Démarrer avec votre nouvelle application](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-connect-data.png)

7. Entrez le nom et le propriétaire du dépôt. L’URL de ce dépôt étant https://github.com/MicrosoftDocs/powerbi-docs, le **Propriétaire du dépôt** est **MicrosoftDocs** et le **Dépôt** est **powerbi-docs**. 
   
    ![Nom du dépôt GitHub - Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-connect.png)

5. Entrez les informations d’identification GitHub que vous avez créées. Power BI ignore cette étape si vous êtes déjà connecté à GitHub dans votre navigateur. 

6. Pour **méthode d’authentification**, conserver **oAuth2** sélectionné \> **Sign In**.

7. Suivez les écrans d’authentification GitHub. Accordez l’autorisation d’accès Power BI aux données GitHub.
   
   Power BI peut maintenant se connecter à GitHub et aux données.  Les données sont actualisées une fois par jour.

8. Une fois que Power BI importe les données, vous consultez le contenu de votre nouvel espace de travail de GitHub. 
9. Dans la barre de navigation de gauche, sélectionnez la flèche en regard du nom de l’espace de travail. Vous consultez que l’espace de travail contient un tableau de bord et un rapport. 

    ![Application dans le volet de navigation gauche](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-left-nav-expanded.png)

10. Sélectionnez les points de suspension (...) en regard du nom de tableau de bord > **renommer** > type **tableau de bord GitHub**.
 
    ![Vignette GitHub - Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-left-nav.png) 

8. Sélectionnez l’icône de navigation globale pour réduire le volet de navigation de gauche et afficher la fenêtre en plus grand.

    ![Icône de navigation globale](media/service-tutorial-connect-to-github/power-bi-global-navigation-icon.png)

10. Sélectionnez votre tableau de bord GitHub.
    
    Le tableau de bord GitHub contient des données actives, les valeurs que vous voyez peuvent différer.

    ![Tableau de bord GitHub dans Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-new-dashboard.png)

    

## <a name="ask-a-question"></a>Poser une question

1. Placez votre curseur dans **poser une question sur vos données**. Power BI offre **Questions pour obtenir votre prise en main**. 

1. Sélectionnez **combien d’utilisateurs existe-t-il**.
 
    ![Existe-t-il des combien d’utilisateurs](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-qna-how-many-users.png)

13. Entre les deux **combien** et **existe-t-il des utilisateurs**, type **par les demandes de tirage**. 

     Power BI crée un graphique à barres montrant le nombre de demandes de tirage par personne.

    ![Existe-t-il des combien de demandes de tirage par utilisateur](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-qna-how-many-prs.png)


13. Sélectionnez le code confidentiel pour l’épingler à votre tableau de bord, puis **fermer la zone Q & r**.

## <a name="view-the-github-report"></a>Afficher le rapport GitHub 

1. Dans le tableau de bord GitHub, sélectionnez l’histogramme **requêtes d’extraction par mois** pour ouvrir le rapport.

    ![Demandes de tirage en histogramme mois](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-column-chart.png)

2. Sélectionnez un nom d’utilisateur dans le **les demandes de tirage Total par utilisateur** graphique. Dans cet exemple, nous voyons la plupart de leurs heures étaient en février.

    ![Sélection dans un rapport GitHub - Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-cross-filter-total-prs.png)

3. Sélectionnez l’onglet **Punch Card** (Carte perforée) pour afficher la page suivante du rapport. 
 
    ![Punch Card (Carte perforée) dans un rapport GitHub - Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-tues-3pm.png)

    Apparemment mardi à 15 : 00 est le plus de temps commun et jour de la semaine pour *valide*, lorsqu’un utilisateur archive dans leur travail.

## <a name="clean-up-resources"></a>Nettoyer les ressources

Maintenant que vous avez terminé le tutoriel, vous pouvez supprimer l’application GitHub. 

1. Dans le volet de navigation de gauche, sélectionnez **Applications**.
2. Placez le curseur sur la vignette GitHub et sélectionnez la poubelle **Supprimer**.

    ![Supprimer l’application GitHub](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-delete.png)

## <a name="next-steps"></a>Étapes suivantes

Dans ce tutoriel, vous vous êtes connecté à un dépôt public GitHub et vous avez obtenu des données, que Power BI a mises en forme dans un tableau de bord et un rapport. Vous avez répondu à certaines questions en explorant les données du tableau de bord et du rapport. Vous pouvez maintenant découvrir comment vous connecter à d’autres services, tels que Salesforce, Microsoft Dynamics et Google Analytics. 
 
> [!div class="nextstepaction"]
> [Se connecter aux services en ligne que vous utilisez](service-connect-to-services.md)


