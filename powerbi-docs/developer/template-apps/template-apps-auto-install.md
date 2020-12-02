---
title: Automatiser la configuration de l’installation des applications modèles pour vos clients
description: Découvrez l’automatisation de la configuration de l’installation des applications modèles.
author: paulinbar
ms.author: painbar
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 11/23/2020
ms.openlocfilehash: ca5db6ed7a07d5a6fb10133285378e8318527464
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96386089"
---
# <a name="automated-configuration-of-a-template-app-installation"></a>Configuration automatisée d’une installation d’application modèle

Les applications modèles sont un excellent moyen pour les clients de commencer à obtenir des insights à partir de leurs données. Les applications modèles leur permettent d’être opérationnels rapidement en les connectant à leurs données et en leur fournissant des rapports prédéfinis qu’ils peuvent ensuite personnaliser s’ils le souhaitent.

Les clients ne connaissent pas toujours les détails nécessaires pour se connecter à leurs données et devoir fournir ces détails lors de l’installation d’une application modèle peut être compliqué pour eux.

Si vous êtes fournisseur de services de données et que vous avez créé une application modèle pour aider vos clients à commencer à utiliser leurs données sur votre service, vous pouvez leur faciliter la tâche d’installation de votre application modèle en automatisant la configuration des paramètres de cette application. Quand le client se connecte à votre portail, il clique sur un lien spécial que vous avez préparé. Ceci lance l’automatisation, qui collecte les informations nécessaires, préconfigure les paramètres de l’application modèle et redirige le client vers son compte Power BI où il peut installer l’application. Tout ce qu’ils doivent faire ici est de cliquer pour installer, puis de se connecter à leur source de données ; ensuite, ils sont prêts à continuer ! 

Cette expérience client est illustrée ci-dessous.

![Illustration de l’expérience utilisateur avec l’installation automatique de l’application.](media/template-apps-auto-install/high-level-flow.png)

Cet article décrit le flux de base, les prérequis, les principales étapes et les API dont vous avez besoin pour automatiser la configuration de l’installation d’une application modèle. Cependant, si vous préférez simplement vous lancer directement, vous pouvez passer au [tutoriel](template-apps-auto-install-tutorial.md) où vous automatisez la configuration de l’installation de l’application modèle en utilisant un exemple d’application simple que nous avons préparé et qui utilise une fonction Azure.

## <a name="basic-flow"></a>Flux de base

Le flux de base de l’automatisation de la configuration de l’installation d’une application modèle est le suivant :

1. L’utilisateur se connecte au portail de l’ISV et clique sur le lien fourni. Ceci lance le flux automatisé. À ce stade, le portail de l’ISV prépare la configuration spécifique à l’utilisateur.

2. L’ISV acquiert un jeton d’**application uniquement** basé sur un [principal de service (jeton d’application uniquement)](../embedded/embed-service-principal.md), qui est inscrit dans le locataire de l’ISV.

3. En utilisant les [API REST de Power BI](https://docs.microsoft.com/rest/api/power-bi/), l’ISV crée un **ticket d’installation** qui contient la configuration de paramètre spécifique à l’utilisateur telle qu’elle est préparée par l’ISV.

4. L’ISV redirige l’utilisateur vers Power BI en utilisant une méthode de redirection ```POST``` contenant le ticket d’installation.

5. L’utilisateur est redirigé vers son compte Power BI avec le ticket d’installation et est invité à installer l’application modèle. Quand l’utilisateur clique sur Installer, l’application modèle est installée pour lui.

>[!Note]
>Les valeurs des paramètres sont configurées par l’ISV lors de la création du ticket d’installation, mais les informations d’identification liées à la source de données sont fournies par l’utilisateur seulement dans les étapes finales de l’installation. Ceci les empêche d’être exposées à un tiers, garantissant ainsi une connexion sécurisée entre l’utilisateur et les sources de données de l’application modèle.

## <a name="prerequisites"></a>Prérequis

Pour fournir une expérience d’installation préconfigurée pour votre application modèle, vous devez répondre aux prérequis suivants :

* Une **licence Power BI Pro**. Si vous n’êtes pas inscrit pour Power BI Pro, [inscrivez-vous pour un essai gratuit](https://powerbi.microsoft.com/pricing/) avant de commencer.

* La **configuration de votre propre locataire Azure Active Directory**. Pour obtenir des instructions sur la façon d’en configurer un, consultez [Créer un locataire Azure Active Directory](https://docs.microsoft.com/power-bi/developer/embedded/create-an-azure-active-directory-tenant).

* Un **principal de service (jeton d’application uniquement)** inscrit dans le locataire ci-dessus. Pour plus d’informations, consultez [Incorporer du contenu Power BI avec un principal de service et un secret d’application](https://docs.microsoft.com/power-bi/developer/embedded/embed-service-principal). Veillez à inscrire l’application en tant qu’**application web côté serveur**. Vous inscrivez une application web côté serveur pour créer un secret d’application. Dans ce processus, vous devez enregistrer l’*ID d’application* (ID de client) et le *Secret de l’application* (secret du client), car vous en aurez besoin pour les étapes ultérieures.

* Une **application modèle paramétrable** prête pour l’installation. L’application modèle doit être créée dans le même locataire que celui où vous inscrivez votre application dans Azure Active Directory (Azure AD). Pour plus d’informations, consultez [Conseils pour les applications modèles](https://docs.microsoft.com/power-bi/connect-data/service-template-apps-tips.md) ou [Créer une application modèle dans Power BI](https://docs.microsoft.com/power-bi/connect-data/service-template-apps-create). Vous devez noter les informations suivantes de l’application modèle pour les étapes suivantes :
     * *ID d’application*, *Clé de package* et *ID de propriétaire* tels qu’ils apparaissent dans l’URL d’installation à la fin du processus [Définir les propriétés de l’application modèle](../../connect-data/service-template-apps-create.md#define-the-properties-of-the-template-app) quand l’application a été créée. Vous pouvez également accéder au même lien en cliquant sur **Obtenir un lien** dans la [Gestion de la publication](../../connect-data/service-template-apps-create.md#manage-the-template-app-release) de l’application modèle.

    * Les *noms des paramètres* tels qu’ils sont définis dans le jeu de données de l’application modèle. Les noms des paramètres sont des chaînes qui sont sensibles à la casse, et qui peuvent également être récupérés sous l’onglet **Valeurs des paramètres** quand vous [définissez les propriétés de l’application modèle](../../connect-data/service-template-apps-create.md#define-the-properties-of-the-template-app) ou à partir des paramètres du jeux de données dans Power BI.

    >[!NOTE]
    >Vous pouvez tester votre application d’installation préconfigurée sur votre application modèle si celle-ci est prête pour l’installation, même si elle n’est pas encore publiquement disponible sur AppSource. Cependant, pour que les utilisateurs en dehors de votre locataire puissent utiliser l’application d’installation automatisée pour installer votre application modèle, celle-ci doit être publiquement disponible dans la [Place de marché des applications Power BI](https://app.powerbi.com/getdata/services). Avant de distribuer votre application modèle en utilisant l’application d’installation automatisée que vous créez, veillez à la publier sur l’[Espace partenaires](https://docs.microsoft.com/azure/marketplace/partner-center-portal/create-power-bi-app-offer).

## <a name="main-steps-and-apis"></a>Étapes principales et API

Les étapes principales de l’automatisation de la configuration de l’installation d’une application modèle et les API dont vous avez besoin sont décrites dans les sections ci-dessous. Si la plupart des étapes sont effectuées avec les [API REST de Power BI](https://docs.microsoft.com/rest/api/power-bi/), les exemples de code décrits ci-dessous sont produits avec le **SDK .NET**.

## <a name="step-1-create-a-power-bi-client-object"></a>Étape 1 : Créer un objet client Power BI 

L’utilisation des API REST de Power BI nécessite d’obtenir un **jeton d’accès** pour votre [principal de service](../embedded/embed-service-principal.md) auprès d’**Azure AD**. Vous devez obligatoirement [obtenir un jeton d’accès Azure AD](../embedded/get-azuread-access-token.md#access-token-for-non-power-bi-users-app-owns-data) pour votre application Power BI avant d’effectuer des appels aux [API REST Power BI](https://docs.microsoft.com/rest/api/power-bi/).
Pour créer le client Power BI avec votre **jeton d’accès**, vous devez créer votre objet client Power BI, qui vous permet d’interagir avec les [API REST de Power BI](https://docs.microsoft.com/rest/api/power-bi/). Pour cela, wrappez l’élément **AccessToken** avec un objet client Power BI **_Microsoft.Rest.TokenCredentials_* _.

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using Microsoft.Rest;
using Microsoft.PowerBI.Api.V2;

var tokenCredentials = new TokenCredentials(authenticationResult.AccessToken, "Bearer");

// Create a Power BI Client object. it's used to call Power BI APIs.
using (var client = new PowerBIClient(new Uri(ApiUrl), tokenCredentials))
{
    // Your code to goes here.
}
```

## <a name="step-2-create-an-install-ticket"></a>Étape 2 : Créer un ticket d’installation

Créez un ticket d’installation, qui est utilisé lors de la redirection de vos utilisateurs vers Power BI. L’API utilisée pour cette opération est _ *CreateInstallTicket**.
* [Modèles d’applications - CreateInstallTicket](https://docs.microsoft.com/rest/api/power-bi/templateapps/createinstallticket)

Un exemple de création d’un ticket d’installation pour l’installation et la configuration d’une application modèle est disponible dans le fichier [InstallTemplateApp/InstallAppFunction.cs](https://github.com/microsoft/Template-apps-examples/blob/master/Developer%20Samples/Automated%20Install%20Azure%20Function/InstallTemplateAppSample/InstallTemplateApp/InstallAppFunction.cs) de l’[exemple d’application](https://github.com/microsoft/Template-apps-examples/tree/master/Developer%20Samples/Automated%20Install%20Azure%20Function/InstallTemplateAppSample).


Voici un exemple de code montrant l’utilisation de l’API REST *CreateInstallTicket* pour une application modèle.
```csharp
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

// Create Install Ticket Request.
InstallTicket ticketResponse = null;
var request = new CreateInstallTicketRequest()
{
    InstallDetails = new List<TemplateAppInstallDetails>()
    {
        new TemplateAppInstallDetails()
        {
            AppId = Guid.Parse(AppId),
            PackageKey = PackageKey,
            OwnerTenantId = Guid.Parse(OwnerId),
            Config = new TemplateAppConfigurationRequest()
            {
                Configuration = Parameters
                                    .GroupBy(p => p.Name)
                                    .ToDictionary(k => k.Key, k => k.Select(p => p.Value).Single())
            }
        }
    }
};

// Issue the request to the REST API using .NET SDK
InstallTicket ticketResponse = await client.TemplateApps.CreateInstallTicketAsync(request);
```

## <a name="step-3-redirect-users-to-power-bi-with-the-ticket"></a>Étape 3 : Rediriger les utilisateurs vers Power BI avec le ticket

Une fois que vous avez créé un ticket d’installation, vous l’utilisez pour rediriger vos utilisateurs vers Power BI pour continuer l’installation et la configuration de l’application modèle. Pour ce faire, utilisez une redirection de méthode ```POST``` vers l’URL d’installation de l’application modèle, avec le ticket d’installation dans le corps de la requête.

Il existe plusieurs méthodes documentées pour émettre une redirection en utilisant des requêtes ```POST```. Le choix de l’une ou de l’autre dépend du scénario et de la façon dont vos utilisateurs interagissent avec votre portail ou votre service.

Un exemple simple, principalement utilisé à des fins de test, s’appuie sur un formulaire avec un champ masqué, qui s’envoie automatiquement lui-même lors du chargement.

```javascript
<html>
    <body onload='document.forms["form"].submit()'>
        <!-- form method is POST and action is the app install URL -->
        <form name='form' action='https://app.powerbi.com/....' method='post' enctype='application/json'>
            <!-- value should be the new install ticket -->
            <input type='hidden' name='ticket' value='H4sI....AAA='>
        </form>
    </body>
</html>
```

Voici un exemple de la réponse de l’[exemple d’application](https://github.com/microsoft/Template-apps-examples/tree/master/Developer%20Samples/Automated%20Install%20Azure%20Function/InstallTemplateAppSample), qui contient le ticket d’installation et redirige automatiquement les utilisateurs vers Power BI. La réponse pour cette fonction Azure est en fait le même formulaire qui s’envoie automatiquement lui-même que celui que nous voyons dans l’exemple HTML ci-dessus.

```csharp
...
    return new ContentResult() { Content = RedirectWithData(redirectUrl, ticket.Ticket), ContentType = "text/html" };
}

...

public static string RedirectWithData(string url, string ticket)
{
    StringBuilder s = new StringBuilder();
    s.Append("<html>");
    s.AppendFormat("<body onload='document.forms[\"form\"].submit()'>");
    s.AppendFormat("<form name='form' action='{0}' method='post' enctype='application/json'>", url);
    s.AppendFormat("<input type='hidden' name='ticket' value='{0}' />", ticket);
    s.Append("</form></body></html>");
    return s.ToString();
}
```

>[!Note]
>S’il existe différentes méthodes d’utilisation des redirections de navigateur ```POST```, vous devez toujours utiliser la méthode la plus sécurisée, qui dépend des besoins et des limitations de votre service. Rappelez-vous que certains formulaires de redirection non sécurisée peuvent entraîner l’exposition de vos utilisateurs ou de votre service à des problèmes de sécurité.

## <a name="step-4-move-your-automation-to-production"></a>Étape 4 : Passer votre automatisation en production

Quand l’automatisation que vous avez conçue est prête, pensez à la passer en production.

## <a name="next-steps"></a>Étapes suivantes

* Essayez notre [tutoriel](template-apps-auto-install-tutorial.md) qui utilise une fonction Azure simple pour automatiser la configuration de l’installation d’une application modèle.

* D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
