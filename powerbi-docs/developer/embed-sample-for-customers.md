---
title: Incorporer du contenu Power BI dans une application pour vos clients
description: Découvrez comment intégrer ou incorporer un rapport, un tableau de bord ou une vignette dans une application web avec les API Power BI pour vos clients.
author: markingmyname
ms.author: maghan
ms.date: 06/20/2018
ms.topic: tutorial
ms.service: powerbi
ms.component: powerbi-developer
ms.custom: mvc
manager: kfile
ms.openlocfilehash: 3cb33180c24022c1e328691ce3a776875d4c87a9
ms.sourcegitcommit: b45134887a452f816a97e384f4333db9e1d8b798
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47238120"
---
# <a name="tutorial-embed-a-power-bi-report-dashboard-or-tile-into-an-application-for-your-customers"></a>Tutoriel : Incorporer un rapport, un tableau de bord ou une vignette Power BI dans une application pour vos clients

Avec **Power BI Embedded dans Azure**, vous pouvez incorporer des rapports, des tableaux de bord et des vignettes dans une application à l’aide de l’exemple **App Owns Data (L’application possède les données)**. **Application possède des données** vise à permettre d’avoir une application qui utilise Power BI comme sa plateforme d’analyse incorporée. L’utilisation de **App Owns Data (L’application possède les données)** est généralement un scénario des **développeurs chez des éditeurs de logiciels indépendants**. En tant que **développeur chez un éditeur de logiciels indépendant**, vous pouvez créer du contenu **Power BI** qui affiche des rapports, des tableaux de bord ou des vignettes dans une application qui est entièrement intégrée et interactive, sans exiger des utilisateurs de l’application qu’ils disposent d’une licence Power BI. Ce tutoriel montre comment intégrer un rapport dans une application avec le Kit de développement logiciel (SDK) **Power BI** .NET ainsi que l’API JavaScript **Power BI** en utilisant **Power BI Embedded dans Azure**  pour vos clients suivant un modèle **L’application possède les données**.

Dans ce tutoriel, vous allez découvrir comment :
>[!div class="checklist"]
>* inscrire une application dans Azure ;
>* incorporer un rapport Power BI dans une application.

## <a name="prerequisites"></a>Conditions préalables

Pour commencer, vous avez besoin d’un compte **Power BI Pro** (ce compte est votre **compte principal**) et d’un abonnement **Microsoft Azure**.

* Si vous n’avez pas d’abonnement à **Power BI Pro**, [inscrivez-vous à un essai gratuit](https://powerbi.microsoft.com/en-us/pricing/) avant de commencer.
* Si vous n’avez pas d’abonnement Azure, créez un [compte gratuit](https://azure.microsoft.com/free/?WT.mc_id=A261C142F) avant de commencer.
* Vous aurez besoin de votre propre installation de [client Azure Active Directory ](create-an-azure-active-directory-tenant.md).
* [Visual Studio](https://www.visualstudio.com/) doit être installé (version 2013 ou ultérieure).

## <a name="set-up-your-embedded-analytics-development-environment"></a>Configurer votre environnement de développement d’analytique incorporée

Avant de commencer à incorporer des rapports, des tableaux de bord ou des vignettes dans votre application, vérifiez que votre environnement est configuré de façon à autoriser l’incorporation. Dans le cadre de la configuration, vous devez effectuer les opérations suivantes.

Vous pouvez accéder à [l’outil de configuration de l’incorporation](https://aka.ms/embedsetup/AppOwnsData) pour démarrer rapidement et télécharger un exemple d’application qui vous permet de créer un environnement et d’incorporer un rapport.

Cependant, si vous choisissez de configurer l’environnement manuellement, vous pouvez continuer et suivre les instructions ci-dessous.

### <a name="register-an-application-in-azure-active-directory-azure-ad"></a>Inscrire une application dans Azure Active Directory (Azure AD)

Inscrivez votre application sur Azure Active Directory pour l’autoriser à accéder aux API REST Power BI. Vous pourrez ainsi établir une identité pour votre application et spécifier des autorisations sur les ressources REST de Power BI.

1. Acceptez les [conditions d’utilisation de l’API Microsoft Power BI](https://powerbi.microsoft.com/api-terms).

2. Connectez-vous au [portail Azure](https://portal.azure.com).

    ![Page principale du Portail Azure](media/embed-sample-for-customers/embed-sample-for-customers-002.png)

3. Dans le volet de navigation de gauche, choisissez **Tous les services** et sélectionnez **Inscriptions d’applications**, puis **Nouvelle inscription d’application**.

    ![Recherche d’inscription d’application](media/embed-sample-for-customers/embed-sample-for-customers-003.png)</br>
    ![Nouvelle inscription d’application](media/embed-sample-for-customers/embed-sample-for-customers-004.png)

4. Suivez les invites pour créer une application. Dans le cas où les applications possèdent les données, il est nécessaire d’utiliser le type d’application **Natif**. Vous devez également indiquer un **URI de redirection**, qui sera utilisé par **Azure AD** pour retourner des réponses de jeton. Entrez une valeur propre à votre application (par exemple, `http://localhost:13526/Redirect`).

    ![Créer une application](media/embed-sample-for-customers/embed-sample-for-customers-005.png)

### <a name="apply-permissions-to-your-application-within-azure-active-directory"></a>Appliquer des autorisations à une application dans Azure Active Directory

Il est nécessaire d’activer des autorisations supplémentaires pour l’application en plus de celles qui ont été spécifiées dans la page d’inscription de l’application. Vous devrez utiliser le compte *principal* servant à l’incorporation, et il devra s’agir d’un compte Administrateur général.

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

7. Sous **Autorisations déléguées**, sélectionnez toutes les autorisations. Vous devez les sélectionner une par une pour enregistrer les sélections. Lorsque vous avez terminé, sélectionnez **Enregistrer**.
   
    ![Sélectionner les autorisations déléguées](media/embed-sample-for-customers/embed-sample-for-customers-015.png)

8. Dans **Autorisations requises**, sélectionnez **Accorder des autorisations**.
   
    L’action **Accorder des autorisations** a besoin du *compte principal* pour éviter d’être invitée à obtenir le consentement d’Azure AD. Si le compte qui effectue cette action est celui d’un administrateur général, vous devez accorder des autorisations à tous les utilisateurs de votre organisation pour cette application. Si le compte qui effectue cette action est le *compte principal* et pas celui d’un administrateur général, vous devez uniquement accorder des autorisations au *compte principal* pour cette application.
   
    ![Accorder des autorisations dans la boîte de dialogue Autorisations requises](media/embed-sample-for-customers/embed-sample-for-customers-016.png)

## <a name="set-up-your-power-bi-environment"></a>Configurer votre environnement Power BI

### <a name="create-an-app-workspace"></a>Créer un espace de travail d'application

Si vous incorporez des rapports, des tableaux de bord ou des vignettes pour vos clients, vous devez placer votre contenu au sein d’un espace de travail d’application. Le compte *principal* doit être administrateur de cet espace de travail d’application.

1. Commencez par créer l’espace de travail. Sélectionnez **Espaces de travail** > **Créer un espace de travail d’application**. C’est à cet endroit que vous placez le contenu auquel votre application doit accéder.

    ![Créer un espace de travail](media/embed-sample-for-customers/embed-sample-for-customers-020.png)

2. Nommez l’espace de travail. Si l’**ID d’espace de travail** correspondant n’est pas disponible, modifiez-le de façon à obtenir un ID unique. Celui-ci doit aussi correspondre au nom de l’application.

    ![Nommer un espace de travail](media/embed-sample-for-customers/embed-sample-for-customers-021.png)

3. Vous devez définir quelques options. Si vous choisissez **Public**, toute personne au sein de votre organisation peut voir le contenu de l’espace de travail. En revanche, **Privé** signifie que seuls les membres de l’espace de travail peuvent en voir le contenu.

    ![Privé/public](media/embed-sample-for-customers/embed-sample-for-customers-022.png)

    Vous ne pouvez pas modifier le paramètre Public/Privé après avoir créé le groupe.

4. Vous pouvez également spécifier si les membres peuvent **apporter des modifications** ou consulter en **lecture seule**.

    ![Ajouter des membres](media/embed-sample-for-customers/embed-sample-for-customers-023.png)

5. Ajouter les adresses e-mail des personnes qui doivent avoir accès à l’espace de travail, puis sélectionnez **Ajouter**. Vous ne pouvez ajouter d’alias de groupe, uniquement des individus.

6. Décidez pour chaque personne si celle-ci est membre ou administrateur. Les administrateurs peuvent modifier l’espace de travail, y compris y ajouter des membres. Les membres peuvent modifier le contenu de l’espace de travail, sauf s’ils disposent d’un accès en affichage seul. Les administrateurs et les membres peuvent publier l’application.

    Vous pouvez à présent voir le nouvel espace de travail. Power BI crée l’espace de travail et l’ouvre. Celui-ci figure dans la liste des espaces de travail dont vous êtes membre. Étant donné que vous êtes administrateur, vous pouvez sélectionner les points de suspension (…) pour revenir en arrière afin d’apporter des modifications, d’ajouter des membres ou de modifier leurs autorisations.

    ![Nouvel espace de travail](media/embed-sample-for-customers/embed-sample-for-customers-025.png)

### <a name="create-and-publish-your-reports"></a>Créer et publier des rapports

Vous pouvez créer vos rapports et jeux de données à l’aide de Power BI Desktop, puis publier ces rapports dans un espace de travail d’applications. Pour publier les rapports dans un espace de travail d’application, l’utilisateur final doit disposer d’une licence Power BI Pro.

1. Téléchargez l’exemple [Blog Demo](https://github.com/Microsoft/powerbi-desktop-samples) (Démonstration blog) sur GitHub.

    ![Exemple de rapport](media/embed-sample-for-customers/embed-sample-for-customers-026-1.png)

2. Ouvrez l’exemple de rapport PBIX dans **Power BI Desktop**.

   ![Rapport PBI Desktop](media/embed-sample-for-customers/embed-sample-for-customers-027.png)

3. Publiez-le sur **l’espace de travail d’application**.

   ![Publier un rapport Desktop](media/embed-sample-for-customers/embed-sample-for-customers-028.png)

    Vous pouvez à présent afficher le rapport dans le service Power BI en ligne.

   ![Affichage du rapport PBI Desktop dans le service](media/embed-sample-for-customers/embed-sample-for-customers-029.png)

## <a name="embed-your-content-using-the-sample-application"></a>Incorporer votre contenu en utilisant l’exemple d’application

Suivez ces étapes pour commencer l’incorporation de votre contenu à l’aide d’un exemple d’application.

1. Téléchargez [l’exemple App Owns Data](https://github.com/Microsoft/PowerBI-Developer-Samples) (L’application possède les données) sur GitHub pour commencer.

    ![Exemple d’application App Owns Data (L’application possède les données)](media/embed-sample-for-customers/embed-sample-for-customers-026.png)

2. Ouvrez le fichier Web.config dans l’exemple d’application. Pour pouvoir exécuter l’application, vous devez renseigner 5 champs : **clientId**, **groupId**, **reportId**, **pbiUsername** et **pbiPassword**.

    ![Fichier Web.config](media/embed-sample-for-customers/embed-sample-for-customers-030.png)

    Renseignez l’information **clientId** avec **l’ID d’application** provenant **d’Azure**. **L’ID client** permet à l’application de s’identifier auprès des utilisateurs auxquels vous demandez des autorisations. Pour obtenir la valeur **clientId**, suivez ces étapes :

    Connectez-vous au [portail Azure](https://portal.azure.com).

    ![Page principale du Portail Azure](media/embed-sample-for-customers/embed-sample-for-customers-002.png)

    Dans le volet de navigation de gauche, choisissez **Tous les services**, puis sélectionnez **Inscriptions d’applications**.

    ![Recherche d’inscription d’application](media/embed-sample-for-customers/embed-sample-for-customers-003.png)

    Sélectionnez l’application pour laquelle vous souhaitez récupérer la valeur **clientId**.

    ![Choisir l’application](media/embed-sample-for-customers/embed-sample-for-customers-006.png)

    Un **ID d’application** devrait être listé au format GUID. Utilisez cet **ID d’application** comme **clientId** de l’application.

    ![clientId](media/embed-sample-for-customers/embed-sample-for-customers-007.png)

    Renseignez l’information **groupId** avec le **GUID d’espace de travail d’application** provenant de Power BI.

    ![groupId](media/embed-sample-for-customers/embed-sample-for-customers-031.png)

    Renseignez l’information **reportId** avec le **GUID de rapport** provenant de Power BI.

    ![reportId](media/embed-sample-for-customers/embed-sample-for-customers-032.png)

    * Renseignez le champ **pbiUsername** avec le compte d’utilisateur principal Power BI.
    * Renseignez le champ **pbiPassword** avec le mot de passe du compte d’utilisateur principal Power BI.

3. Exécutez l’application !

    Tout d’abord, sélectionnez **Exécuter** dans **Visual Studio**.

    ![Exécuter l’application](media/embed-sample-for-customers/embed-sample-for-customers-033.png)

    Ensuite, sélectionnez **Incorporer un rapport**. Sélectionnez l’option correspondant au contenu choisi pour le test (rapports, tableaux de bord ou vignettes) dans l’application.

    ![Sélectionner un contenu](media/embed-sample-for-customers/embed-sample-for-customers-034.png)

    Vous pouvez à présent voir le rapport dans l’exemple d’application.

    ![Voir l’application](media/embed-sample-for-customers/embed-sample-for-customers-035.png)

## <a name="embed-your-content-within-your-application"></a>Incorporer votre contenu dans l’application

Même si les étapes permettant d’incorporer votre contenu peuvent être effectuées avec les [API REST Power BI](https://docs.microsoft.com/rest/api/power-bi/), les exemples de code décrits dans cet article utilisent le **kit SDK .NET**.

L’incorporation pour vos clients dans votre application exige que vous obteniez un **jeton d’accès** pour votre compte principal à partir d’**Azure AD**. Vous devez obligatoirement [obtenir un jeton d’accès Azure AD](get-azuread-access-token.md#access-token-for-non-power-bi-users-app-owns-data) pour votre application Power BI en utilisant le modèle **L’application possède les données** avant de faire appel aux [API REST Power BI](https://docs.microsoft.com/rest/api/power-bi/).

Pour créer le client Power BI avec votre **jeton d’accès**, vous devez créer votre objet client Power BI pour interagir avec les [API REST Power BI](https://docs.microsoft.com/rest/api/power-bi/). Pour cela, encapsulez l’élément **AccessToken** avec un objet ***Microsoft.Rest.TokenCredentials***.

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using Microsoft.Rest;
using Microsoft.PowerBI.Api.V2;

var tokenCredentials = new TokenCredentials(authenticationResult.AccessToken, "Bearer");

// Create a Power BI Client object. It is used to call Power BI APIs.
using (var client = new PowerBIClient(new Uri(ApiUrl), tokenCredentials))
{
    // Your code to embed items.
}
```

### <a name="get-the-content-item-you-want-to-embed"></a>Obtenir l’élément de contenu que vous souhaitez incorporer

Vous pouvez utiliser l’objet client Power BI pour récupérer une référence à l’élément que vous souhaitez incorporer.

Voici un exemple de code montrant comment récupérer le premier rapport à partir d’un espace de travail donné.

*Un exemple d’obtention d’un élément de contenu, qu’il s’agisse d’un rapport, d’un tableau de bord ou d’une vignette à incorporer, est disponible dans le fichier Controllers\HomeController.cs dans l’[exemple d’application](#embed-your-content-within-a-sample-application).*

```csharp
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

// You need to provide the GroupID where the dashboard resides.
ODataResponseListReport reports = client.Reports.GetReportsInGroupAsync(GroupId);

// Get the first report in the group.
Report report = reports.Value.FirstOrDefault();
```

### <a name="create-the-embed-token"></a>Créer le jeton incorporé

Un jeton d’incorporation doit être généré pour être utilisé à partir de l’API JavaScript. Le jeton d’incorporation est spécifique à l’élément que vous incorporez. De ce fait, chaque fois que vous incorporez un élément de contenu Power BI, vous devez lui créer un jeton d’incorporation. Pour en savoir plus, notamment sur les niveaux d’accès (**accessLevel**) à utiliser, consultez [API GenerateToken](https://msdn.microsoft.com/library/mt784614.aspx).

Voici un exemple d’ajout d’un jeton d’incorporation de rapport à votre application.

*Un exemple de création de jeton d’incorporation de rapport, de tableau de bord ou de vignette est disponible dans le fichier Controllers\HomeController.cs dans l’[exemple d’application](#embed-your-content-within-a-sample-application).*

```csharp
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

// Generate Embed Token.
var generateTokenRequestParameters = new GenerateTokenRequest(accessLevel: "view");
EmbedToken tokenResponse = client.Reports.GenerateTokenInGroup(GroupId, report.Id, generateTokenRequestParameters);

// Generate Embed Configuration.
var embedConfig = new EmbedConfig()
{
    EmbedToken = tokenResponse,
    EmbedUrl = report.EmbedUrl,
    Id = report.Id
};
```

Cela suppose la création d’une classe pour **EmbedConfig** et **TileEmbedConfig**. Un exemple de ces éléments est disponible dans le fichier **Models\EmbedConfig.cs** et le fichier **Models\TileEmbedConfig.cs**.

### <a name="load-an-item-using-javascript"></a>Charger un élément en utilisant JavaScript
JavaScript permet de charger un rapport dans un élément div sur votre page web.

Pour obtenir un exemple complet d’utilisation de l’API JavaScript, vous pouvez utiliser [l’outil Playground](https://microsoft.github.io/PowerBI-JavaScript/demo). C’est un moyen rapide de jouer avec différents types d’exemples Power BI Embedded. Pour plus d’informations sur l’API JavaScript, vous pouvez consulter la page du [wiki PowerBI-JavaScript](https://github.com/Microsoft/powerbi-javascript/wiki).

Voici un exemple qui utilise un modèle **EmbedConfig** et un modèle **TileEmbedConfig** avec les vues d’un rapport.

*Un exemple d’ajout de rapport, de tableau de bord ou de vignette est disponible dans les fichiers Views\Home\EmbedReport.cshtml, Views\Home\EmbedDashboard.cshtml ou Views\Home\Embedtile.cshtml dans l’[exemple d’application](#embed-your-content-within-a-sample-application).*

```javascript
<script src="~/scripts/powerbi.js"></script>
<div id="reportContainer"></div>
<script>
    // Read embed application token from Model
    var accessToken = "@Model.EmbedToken.Token";

    // Read embed URL from Model
    var embedUrl = "@Html.Raw(Model.EmbedUrl)";

    // Read report Id from Model
    var embedReportId = "@Model.Id";

    // Get models. models contains enums that can be used.
    var models = window['powerbi-client'].models;

    // Embed configuration used to describe the what and how to embed.
    // This object is used when calling powerbi.embed.
    // This also includes settings and options such as filters.
    // You can find more information at https://github.com/Microsoft/PowerBI-JavaScript/wiki/Embed-Configuration-Details.
    var config = {
        type: 'report',
        tokenType: models.TokenType.Embed,
        accessToken: accessToken,
        embedUrl: embedUrl,
        id: embedReportId,
        permissions: models.Permissions.All,
        settings: {
            filterPaneEnabled: true,
            navContentPaneEnabled: true
        }
    };

    // Get a reference to the embedded report HTML element
    var reportContainer = $('#reportContainer')[0];

    // Embed the report and display it within the div container.
    var report = powerbi.embed(reportContainer, config);
</script>
```

## <a name="move-to-production"></a>Passer à la production

Maintenant que votre application est développée, il est temps de sauvegarder votre espace de travail d’application avec une capacité dédiée. Une capacité dédiée est nécessaire de passer à la production.

### <a name="create-a-dedicated-capacity"></a>Créer une capacité dédiée

En créant une capacité dédiée, vous pouvez profiter du fait que vous disposez d’une ressource dédiée pour votre client. Vous pouvez acheter une capacité dédiée dans le [Portail Microsoft Azure](https://portal.azure.com). Pour en savoir plus sur la création d’une capacité Power BI Embedded, consultez [Créer une capacité Power BI Embedded dans le Portail Microsoft Azure](azure-pbie-create-capacity.md).

Examinez le tableau ci-dessous pour déterminer la capacité Power BI Embedded qui répond le mieux à vos besoins.

| Nœud de capacité | Nombre total de cœurs<br/>*(Serveur principal + serveur frontal)* | Cœurs du serveur principal | Cœurs du serveur frontal | Limites de connexions actives/DirectQuery | Rendus de pages au maximum aux heures de pointe |
| --- | --- | --- | --- | --- | --- |
| A1 |1 v-core(s) |.5 cœur(s), 3 Go de RAM |.5 cœurs | 5 par seconde |1-300 |
| A2 |2 v-core(s) |1 cœur(s), 5 Go de RAM |1 cœur(s) | 10 par seconde |301-600 |
| A3 |4 v-core(s) |2 cœur(s), 10 Go de RAM |2 cœur(s) | 15 par seconde |601-1 200 |
| A4 |8 v-core(s) |4 cœur(s), 25 Go de RAM |4 cœur(s) |30 par seconde |1 201-2 400 |
| A5 |16 v-core(s) |8 cœur(s), 50 Go de RAM |8 cœur(s) |60 par seconde |2 401-4 800 |
| A6 |32 v-core(s) |16 cœur(s), 100 Go de RAM |16 cœur(s) |120 par seconde |4 801-9 600 |

**_Les références SKU A ne vous permettent pas d’accéder à du contenu Power BI avec une licence Power BI GRATUITE._**

L’utilisation de jetons d’incorporation avec des licences PRO étant destinée aux tests de développement, le nombre de jetons d’incorporation qu’un compte principal Power BI peut générer est limité. Vous devez acheter une capacité dédiée pour l’incorporation dans un environnement de production. Avec une capacité dédiée, le nombre de jetons incorporés que vous pouvez générer n’est pas limité. Accédez à [Fonctionnalités disponibles](https://docs.microsoft.com/rest/api/power-bi/availablefeatures/getavailablefeatures) pour vérifier la valeur qui indique l’utilisation actuelle de jetons incorporés en pourcentage. Le volume d’utilisation varie en fonction du compte principal.

Pour plus d’informations, consultez le [livre blanc Planification d’une capacité d’analytique incorporée](https://aka.ms/pbiewhitepaper).

### <a name="assign-an-app-workspace-to-a-dedicated-capacity"></a>Affecter un espace de travail d’application à une capacité dédiée

Une fois que vous avez créé une capacité dédiée, vous pouvez lui affecter votre espace de travail d’application. Pour ce faire, effectuez les étapes suivantes.

1. Dans le **service Power BI**, développez les espaces de travail, puis sélectionnez les points de suspension en regard de l’espace de travail que vous utilisez pour incorporer votre contenu. Sélectionnez ensuite **Modifier l’espace de travail**.

    ![Modifier l’espace de travail](media/embed-sample-for-customers/embed-sample-for-customers-036.png)

2. Développez **Avancé**, activez **Capacité dédiée**, puis sélectionnez la capacité dédiée que vous avez créée. Ensuite, sélectionnez **Enregistrer**.

    ![Affecter une capacité dédiée](media/embed-sample-for-customers/embed-sample-for-customers-024.png)

3. Après avoir sélectionné **Enregistrer**, vous devez voir un **losange** en regard du nom de l’espace de travail d’application.

    ![espace de travail lié à une capacité](media/embed-sample-for-customers/embed-sample-for-customers-037.png)

## <a name="next-steps"></a>Étapes suivantes

Dans ce tutoriel, vous avez appris à incorporer du contenu Power BI dans une application pour vos clients. Vous pouvez aussi essayer d’incorporer du contenu Power BI pour votre organisation.

> [!div class="nextstepaction"]
>[Incorporer pour votre organisation](embed-sample-for-your-organization.md)

D’autres questions ? [Essayez d’interroger la communauté Power BI](http://community.powerbi.com/)
