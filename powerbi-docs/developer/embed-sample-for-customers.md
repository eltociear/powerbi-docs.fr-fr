---
title: Incorporer du contenu Power BI dans une application pour vos clients
description: Découvrez comment intégrer ou incorporer un rapport, un tableau de bord ou une vignette dans une application web avec les API Power BI pour vos clients.
services: powerbi
author: markingmyname
ms.author: maghan
ms.date: 05/07/2018
ms.topic: tutorial
ms.service: powerbi
ms.custom: mvc
manager: kfile
ms.openlocfilehash: 2d4fdee8d3e4cca60294acd0a9167da1f048afa5
ms.sourcegitcommit: 9fa954608e78dcdb8d8a503c3c9b01c43ca728ab
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/11/2018
ms.locfileid: "34051930"
---
# <a name="tutorial-embed-a-power-bi-report-dashboard-or-tile-into-an-application-for-your-customers"></a>Tutoriel : Incorporer un rapport, un tableau de bord ou une vignette Power BI dans une application pour les clients
Avec **Power BI Embedded dans Azure**, vous pouvez incorporer des rapports, des tableaux de bord et des vignettes dans une application afin de permettre à vos clients de partager des données. Ce scénario concerne généralement les **développeurs des éditeurs de logiciels indépendants** suivant une structure selon laquelle **l’application possède les données**. Le modèle **L’application possède les données** implique d’incorporer du contenu Power BI pour vos propres clients. L’utilisateur du contenu Power BI peut par exemple afficher des rapports, des tableaux de bord et des vignettes sans avoir besoin de se connecter à **Power BI**. Ce tutoriel montre comment intégrer ou incorporer un rapport dans une application avec le Kit de développement logiciel (SDK) .NET **Power BI** ainsi que l’API JavaScript **Power BI** en utilisant **Power BI Embedded dans Azure**  pour les clients suivant un modèle **l’application possède les données**.

Dans ce tutoriel, vous allez découvrir comment :
>[!div class="checklist"]
>* inscrire une application dans Azure ;
>* incorporer un rapport, un tableau de bord ou une vignette dans une application avec Power BI Embedded dans Azure.

## <a name="prerequisites"></a>Conditions préalables
Pour commencer, vous aurez besoin d’un compte **Power BI Pro** et d’un compte **Microsoft Azure**.

* Si vous n’avez pas d’abonnement à **Power BI Pro**, [inscrivez-vous à un essai gratuit](https://powerbi.microsoft.com/en-us/pricing/) avant de commencer.
* Si vous n’avez pas d’abonnement Azure, créez un [compte gratuit](https://azure.microsoft.com/free/?WT.mc_id=A261C142F) avant de commencer.
* Vous aurez besoin de votre propre installation de [client Azure Active Directory ](create-an-azure-active-directory-tenant.md).
* [Visual Studio](https://www.visualstudio.com/) doit être installé (version 2013 ou ultérieure).

## <a name="setup-your-embedded-analytics-development-environment"></a>Configurer l’environnement de développement d’analytique incorporée

Avant de commencer à incorporer des rapports, des tableaux de bord ou des vignettes dans votre application, vérifiez que votre environnement est configuré de façon à autoriser l’incorporation. Dans le cadre de la configuration, vous devez effectuer les opérations suivantes.

### <a name="register-an-application-in-azure-active-directory-azure-ad"></a>Inscrire une application dans Azure Active Directory (Azure AD)

Inscrivez votre application sur Azure Active Directory pour l’autoriser à accéder aux API REST Power BI. Vous pourrez ainsi établir une identité pour votre application et spécifier des autorisations sur les ressources REST de Power BI.

1. Acceptez les [conditions d’utilisation de l’API Microsoft Power BI](https://powerbi.microsoft.com/api-terms).

2. Connectez-vous au [portail Azure](https://portal.azure.com).
 
    ![Page principale du Portail Azure](media/embed-sample-for-customers/embed-sample-for-customers-002.png)

3. Dans le volet de navigation de gauche, choisissez **Tous les services** et sélectionnez **Inscriptions d’applications**, puis **Nouvelle inscription d’application**.
   
    ![Recherche d’inscription d’application](media/embed-sample-for-customers/embed-sample-for-customers-003.png)</br>
    ![Nouvelle inscription d’application](media/embed-sample-for-customers/embed-sample-for-customers-004.png)

4. Suivez les invites pour créer une application. Dans le cas où les applications possèdent les données, il est nécessaire d’utiliser le type d’application **Natif**. Vous devez également indiquer un **URI de redirection**, qui sera utilisé par **Azure AD** pour retourner des réponses de jeton. Entrez une valeur propre à votre application (par exemple, http://localhost:13526/redirect).

    ![Créer une application](media/embed-sample-for-customers/embed-sample-for-customers-005.png)

### <a name="apply-permissions-to-your-application-within-azure-active-directory"></a>Appliquer des autorisations à une application dans Azure Active Directory

Il est nécessaire d’activer des autorisations supplémentaires pour l’application en plus de celles qui ont été spécifiées sur la page d’inscription de l’application. Vous devrez utiliser le compte *principal* servant à l’incorporation, et il devra s’agir d’un compte Administrateur général.

### <a name="use-the-azure-active-directory-portal"></a>Utiliser le portail Azure Active Directory

1. Accédez à [Inscriptions des applications](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ApplicationsListBlade) dans le portail Azure, puis sélectionnez l’application que vous utilisez pour l’incorporation.
   
    ![Choisir l’application](media/embed-sample-for-customers/embed-sample-for-customers-006.png)

2. Sélectionnez **Paramètres** ; ensuite, sous **Accès aux API**, sélectionnez **Autorisations requises**.
   
    ![Autorisations requises](media/embed-sample-for-customers/embed-sample-for-customers-008.png)

3. Sélectionnez **Windows Azure Active Directory** puis vérifiez que l’option **Accéder au répertoire en tant qu’utilisateur actuellement connecté** est sélectionnée. Sélectionnez **Enregistrer**.
   
    ![Autorisations Windows Azure AD](media/embed-sample-for-customers/embed-sample-for-customers-011.png)

4. Sélectionnez **Ajouter**.

    ![Ajouter des autorisations](media/embed-sample-for-customers/embed-sample-for-customers-012.png)

5. Sélectionnez **Sélectionner une API**.

    ![Ajouter un accès aux API](media/embed-sample-for-customers/embed-sample-for-customers-013.png)

6. Sélectionnez **Service Power BI**, puis **Sélectionner**.

    ![Sélectionner PBI Services](media/embed-sample-for-customers/embed-sample-for-customers-014.png)

7. Sous **Autorisations déléguées**, sélectionnez toutes les autorisations. Vous devez les sélectionner une par une afin d’enregistrer les sélections. Lorsque vous avez terminé, sélectionnez **Enregistrer**.
   
    ![Sélectionner les autorisations déléguées](media/embed-sample-for-customers/embed-sample-for-customers-015.png)

8. Dans **Autorisations requises**, sélectionnez **Accorder des autorisations**.
   
    L’action **Accorder des autorisations** est nécessaire pour éviter qu’Azure AD exige une confirmation du *compte principal*. Si le compte qui effectue cette action est celui d’un administrateur global, vous pouvez accorder des autorisations pour tous les utilisateurs de votre organisation pour cette application. Si le compte qui effectue cette action est le *compte principal* et pas celui d’un administrateur global, vous pouvez uniquement accorder des autorisations au *compte principal* pour cette application.
   
    ![Accorder des autorisations dans la boîte de dialogue Autorisations requises](media/embed-sample-for-customers/embed-sample-for-customers-016.png)

### <a name="create-your-power-bi-embedded-dedicated-capacity-in-azure"></a>Créer une capacité dédiée Power BI Embedded dans Azure

1. Connectez-vous au [portail Azure](https://portal.azure.com).

    ![Page principale du Portail Azure](media/embed-sample-for-customers/embed-sample-for-customers-002.png)

2. Dans le volet de navigation de gauche, choisissez **Tous les services**, puis sélectionnez **Power BI Embedded**.

    ![Recherche PBIE](media/embed-sample-for-customers/embed-sample-for-customers-017.png)

3. Suivez les invites et renseignez les informations nécessaires pour créer une nouvelle capacité dédiée **Power BI Embedded**, puis sélectionnez **Créer**. Au moment de choisir le **Niveau tarifaire**, consultez le tableau ci-dessous pour déterminer le plus adapté à vos besoins. Ensuite, sélectionnez **Créer** et attendez que la ressource soit créée.

    ![Configuration PBIE](media/embed-sample-for-customers/embed-sample-for-customers-018.png)

| Nœud de capacité | Nombre total de cœurs<br/>*(Serveur principal + serveur frontal)* | Cœurs du serveur principal | Cœurs du serveur frontal | Limites de connexions actives/DirectQuery | Rendus de pages au maximum aux heures de pointe |
| --- | --- | --- | --- | --- | --- |
| A1 |1 cœur virtuel |.5 cœurs, 3 Go de RAM |.5 cœurs | 5 par seconde |1-300 |
| A2 |2 cœurs virtuels |1 cœur, 5 Go de RAM |1 cœur | 10 par seconde |301-600 |
| A3 |4 cœurs virtuels |2 cœurs, 10 Go de RAM |2 cœurs | 15 par seconde |601-1 200 |
| A4 |8 cœurs virtuels |4 cœurs, 25 Go de RAM |4 cœurs |30 par seconde |1 201-2 400 |
| A5 |16 cœurs virtuels |8 cœurs, 50 Go de RAM |8 cœurs |60 par seconde |2 401-4 800 |
| A6 |32 cœurs virtuels |16 cœurs, 100 Go de RAM |16 cœurs |120 par seconde |4 801-9 600 |

Vous pouvez maintenant voir la nouvelle **capacité dédiée Power BI Embedded**.

   ![Capacité dédiée PBIE](media/embed-sample-for-customers/embed-sample-for-customers-019.png)

## <a name="setup-your-power-bi-environment"></a>Configurer un environnement Power BI

### <a name="create-an-app-workspace"></a>Créer un espace de travail d’application

Si vous incorporez des rapports, des tableaux de bord ou des vignettes pour vos clients, vous devez placer votre contenu au sein d’un espace de travail d’application. Le compte *principal* doit être administrateur de cet espace de travail d’application.

1. Commencez par créer l’espace de travail. Sélectionnez **Espaces de travail** > **Créer un espace de travail d’application**. C’est à cet endroit que sera placé le contenu auquel votre application devra avoir accès.

    ![Créer un espace de travail](media/embed-sample-for-customers/embed-sample-for-customers-020.png)

2. Nommez l’espace de travail. Si l’**ID d’espace de travail** correspondant n’est pas disponible, modifiez-le de façon à obtenir un ID unique. Ce sera aussi le nom de l’application.

    ![Nommer un espace de travail](media/embed-sample-for-customers/embed-sample-for-customers-021.png)

3. Vous devez définir quelques options. Si vous choisissez **Public**, toute personne au sein de votre organisation peut voir le contenu de l’espace de travail. En revanche, **Privé** signifie que seuls les membres de l’espace de travail peuvent en voir le contenu.

    ![Privé/public](media/embed-sample-for-customers/embed-sample-for-customers-022.png)

    Vous ne pouvez pas modifier le paramètre Public/Privé après avoir créé le groupe.

4. Vous pouvez également spécifier si les membres peuvent **apporter des modifications** ou consulter en **lecture seule**.

    ![Ajouter des membres](media/embed-sample-for-customers/embed-sample-for-customers-023.png)

5. Ajouter les adresses e-mail des personnes qui doivent avoir accès à l’espace de travail, puis sélectionnez **Ajouter**. Vous ne pouvez ajouter d’alias de groupe, uniquement des individus.

6. Décidez pour chaque personne si celle-ci est membre ou administrateur. Les administrateurs peuvent modifier l’espace de travail, y compris y ajouter des membres. Les membres peuvent modifier le contenu de l’espace de travail, sauf s’ils disposent d’un accès en affichage seul. Les administrateurs et les membres peuvent publier l’application.

7. Développez **Avancé**, puis activez **Capacité dédiée** et sélectionnez la **capacité dédiée Power BI Embedded** que vous avez créée. Ensuite, sélectionnez **Enregistrer**.

    ![Ajouter des membres](media/embed-sample-for-customers/embed-sample-for-customers-024.png)

Vous pouvez à présent voir le nouvel espace de travail. Power BI crée l’espace de travail et l’ouvre. Celui-ci figure dans la liste des espaces de travail dont vous êtes membre. Étant donné que vous êtes administrateur, vous pouvez sélectionner les points de suspension (…) pour revenir en arrière afin d’apporter des modifications, d’ajouter des membres ou de modifier leurs autorisations.

   ![Nouvel espace de travail](media/embed-sample-for-customers/embed-sample-for-customers-025.png)

### <a name="create-and-publish-your-reports"></a>Créer et publier des rapports

Vous pouvez créer vos rapports et jeux de données à l’aide de Power BI Desktop, puis publier ces rapports dans un espace de travail d’applications. Pour publier les rapports dans un espace de travail d’applications, l’utilisateur final doit disposer d’une licence Power BI Pro.

1. Téléchargez l’exemple [Blog Demo](https://github.com/Microsoft/powerbi-desktop-samples) (Démonstration blog) sur GitHub.

    ![Exemple de rapport](media/embed-sample-for-customers/embed-sample-for-customers-026-1.png)

2. Ouvrez l’exemple de rapport PBIX dans **Power BI Desktop**.

   ![Rapport PBI Desktop](media/embed-sample-for-customers/embed-sample-for-customers-027.png)

3. Publiez-le sur **l’espace de travail d’application**.

   ![Rapport PBI Desktop](media/embed-sample-for-customers/embed-sample-for-customers-028.png)

    Vous pouvez à présent voir le rapport dans le service Power BI en ligne.

   ![Rapport PBI Desktop](media/embed-sample-for-customers/embed-sample-for-customers-029.png)

## <a name="embed-your-content"></a>Incorporer du contenu

1. Téléchargez [l’exemple App Owns Data](https://github.com/Microsoft/PowerBI-Developer-Samples) (L’application possède les données) sur GitHub pour commencer.

    ![Exemple d’application App Owns Data (L’application possède les données)](media/embed-sample-for-customers/embed-sample-for-customers-026.png)

2. Ouvrez le fichier Web.config dans l’exemple d’application. Il y a cinq champs à renseigner pour pouvoir exécuter l’application : **clientID**, **groupId**, **reportId**, **pbiUsername** et **pbiPassword**.

      ![Fichier Web.config](media/embed-sample-for-customers/embed-sample-for-customers-030.png)

    * Renseignez l’information **clientId** avec **l’ID d’application** provenant **d’Azure**. **L’ID client** permet à l’application de s’identifier auprès des utilisateurs auxquels vous demandez des autorisations. Pour obtenir la valeur **clientId**, suivez les étapes ci-dessous :

        1. Connectez-vous au [portail Azure](https://portal.azure.com).

        ![Page principale du Portail Azure](media/embed-sample-for-customers/embed-sample-for-customers-002.png)

        2. Dans le volet de navigation de gauche, choisissez **Tous les services**, puis sélectionnez **Inscriptions d’applications**.

        ![Recherche d’inscription d’application](media/embed-sample-for-customers/embed-sample-for-customers-003.png)
        3. Sélectionnez l’application pour laquelle vous souhaitez récupérer la valeur **clientId**.

        ![Choisir l’application](media/embed-sample-for-customers/embed-sample-for-customers-006.png)

      4. Un **ID d’application** devrait être listé au format GUID. Utilisez cet **ID d’application** comme **clientId** de l’application.

        ![clientId](media/embed-sample-for-customers/embed-sample-for-customers-007.png)     

    * Renseignez l’information **groupId** avec le **GUID d’espace de travail d’application** provenant de Power BI.

        ![groupId](media/embed-sample-for-customers/embed-sample-for-customers-031.png)

    * Renseignez l’information **reportId** avec le **GUID de rapport** provenant de Power BI.

        ![reportId](media/embed-sample-for-customers/embed-sample-for-customers-032.png)    

    * Renseignez le champ **pbiUsername** avec le compte Power BI d’utilisateur principal.
    * Renseignez le champ **pbiPassword** avec le mot de passe du compte Power BI d’utilisateur principal.

3. Exécutez l’application !

    Tout d’abord, sélectionnez **Exécuter** dans **Visual Studio**.

    ![Exécuter l’application](media/embed-sample-for-customers/embed-sample-for-customers-033.png)

    Ensuite, sélectionnez **Incorporer un rapport**. Sélectionnez l’option correspondant au contenu choisi pour le test (rapports, tableaux de bord ou vignettes) dans l’application.

    ![Sélectionner un contenu](media/embed-sample-for-customers/embed-sample-for-customers-034.png)
 
    Vous pouvez à présent voir le rapport dans l’exemple d’application.

    ![Voir l’application](media/embed-sample-for-customers/embed-sample-for-customers-035.png)

Pour obtenir un exemple complet d’utilisation de l’API JavaScript, vous pouvez utiliser [l’outil Playground](https://microsoft.github.io/PowerBI-JavaScript/demo). C’est un moyen rapide de jouer avec différents types d’exemples Power BI Embedded. Vous trouverez également d’autres informations sur l’API JavaScript sur la page [Wiki PowerBI-JavaScript](https://github.com/Microsoft/powerbi-javascript/wiki).

Pour toute question sur Power BI Embedded, consultez la page [FAQ](embedded-faq.md).  Si vous rencontrez des problèmes liés à Power Bi Embedded au sein de votre application, consultez la page [Résolution des problèmes](embedded-troubleshoot.md).

D’autres questions ? [Essayez d’interroger la communauté Power BI](http://community.powerbi.com/) 