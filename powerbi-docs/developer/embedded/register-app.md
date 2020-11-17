---
title: Inscrire une application pour incorporer du contenu Power BI
description: Découvrez comment inscrire une application dans Azure Active Directory afin de l’utiliser avec l’incorporation de contenu Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: nishalit
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.date: 04/02/2019
ms.openlocfilehash: 52e835f4ff0d3dc4cad13c2e3ecc77d254f3be9d
ms.sourcegitcommit: 5ccab484cf3532ae3a16acd5fc954b7947bd543a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/06/2020
ms.locfileid: "93412224"
---
# <a name="register-an-azure-ad-application-to-use-with-power-bi"></a>Inscrire une application Azure AD à utiliser avec Power BI

Pour utiliser l’analytique incorporée Power BI, vous devez inscrire une application Azure Active Directory (Azure AD) dans Azure. L’application Azure AD établit des autorisations pour les ressources REST Power BI et autorise l’accès aux [API REST Power BI](/rest/api/power-bi/).

## <a name="determine-your-embedding-solution"></a>Déterminer votre solution d’incorporation

Avant d’inscrire votre application, choisissez parmi les solutions suivantes celle qui vous convient le mieux :

* Incorporer pour vos clients
* Incorporer pour votre organisation

### <a name="embed-for-your-customers"></a>Incorporer pour vos clients

Utilisez la solution [Incorporer pour vos clients](embed-sample-for-customers.md), également appelée *app owns data* (application propriétaire des données), si vous envisagez de créer une application pensée pour vos clients. Les utilisateurs n’auront pas besoin de se connecter à Power BI ni de disposer d’une licence Power BI pour utiliser votre application. Votre application utilisera l’une des méthodes suivantes pour s’authentifier auprès de Power BI :

* Un compte **Utilisateur maître** (licence Power BI Pro utilisée pour la connexion à Power BI)

*  [Principal du service](embed-service-principal.md)

La solution Incorporer pour vos clients est généralement utilisée par les éditeurs de logiciels indépendants (ISV) et les développeurs qui créent des applications pour un tiers.

### <a name="embed-for-your-organization"></a>Incorporer pour votre organisation

Utilisez la solution [Incorporer pour votre organisation](embed-sample-for-your-organization.md), également appelée *user owns data* (utilisateur propriétaire des données), si vous envisagez de créer une application qui impose aux utilisateurs d’utiliser leurs informations d’identification pour s’authentifier auprès de Power BI.

La solution Incorporer pour votre organisation est généralement utilisée par les grandes entreprises et organisations et s’adresse aux utilisateurs internes.

## <a name="register-an-azure-ad-app"></a>Inscrire une application Azure AD

La façon la plus simple d’inscrire une application Azure AD est d’utiliser l’[outil de configuration de l’incorporation Power BI](https://app.powerbi.com/embedsetup). Cet outil propose un processus d’inscription rapide pour les deux solutions d’incorporation via une interface graphique simple.

Si vous créez une application de type *Incorporer pour votre organisation* et que vous souhaitez mieux contrôler votre application Azure AD, vous pouvez l’inscrire manuellement sur le portail Azure.

> [!IMPORTANT]
> Pour pouvoir inscrire une application Power BI, vous devez disposer d’un [locataire Azure Active Directory et d’un utilisateur d’organisation](create-an-azure-active-directory-tenant.md).

# <a name="embed-for-your-customers"></a>[Incorporer pour vos clients](#tab/customers)

Ces étapes décrivent la procédure d’inscription d’une application Azure AD pour la solution Power BI [Incorporer pour vos clients](embed-sample-for-customers.md).

[!INCLUDE[registration tool step 1](../../includes/register-tool-step-1.md)]

2. Dans la section *Choisir une solution d’incorporation*, sélectionnez **Incorporer pour vos clients**.

[!INCLUDE[registration tool step 3](../../includes/register-tool-step-3.md)]

4. À l’*Étape 2 – Inscrire votre application*, renseignez les champs suivants :

    * **Nom de l’application** – Donnez un nom à votre application.

    * **Accès aux API** – Sélectionnez les API Power BI (également appelées « étendues ») dont votre application a besoin. Vous pouvez utiliser *Sélectionner tout* pour sélectionner toutes les API. Pour plus d’informations sur les autorisations d’accès de Power BI, consultez [Autorisations et consentement dans le point de terminaison de la plateforme d’identités Microsoft](/azure/active-directory/develop/v2-permissions-and-consent).

5. Sélectionnez **Inscription**.

    L’**ID d’application** de votre application Azure AD s’affiche dans la zone *Résumé*. Copiez cette valeur en vue d’une utilisation ultérieure.

[!INCLUDE[registration tool steps 6-7](../../includes/register-tool-steps-6-7.md)]

8. À l’*Étape 5 – Accorder des autorisations*, sélectionnez **Accorder des autorisations** puis, dans la fenêtre contextuelle, sélectionnez **accepter**. Cela permet à votre application Azure AD d’accéder aux API que vous avez sélectionnées (également appelées « étendues ») avec votre utilisateur connecté. Cet utilisateur est aussi appelé **utilisateur maître**.

9. (Facultatif) Si vous avez créé un espace de travail Power BI et que vous y avez chargé du contenu à l’aide de l’outil, vous pouvez maintenant sélectionner **Télécharger l’exemple d’application**. Veillez à copier toutes les informations contenues dans la zone *Résumé*.

[!INCLUDE[registration tool note](../../includes/register-tool-note.md)]

# <a name="embed-for-your-organization"></a>[Incorporer pour votre organisation](#tab/organization)

Ces étapes décrivent la procédure d’inscription d’une application Azure AD pour la solution Power BI [Incorporer pour votre organisation](embed-sample-for-your-organization.md).

[!INCLUDE[registration tool step 1](../../includes/register-tool-step-1.md)]

2. Dans la section *Choisir une solution d’incorporation*, sélectionnez **Incorporer pour votre organisation**.

[!INCLUDE[registration tool step 3](../../includes/register-tool-step-3.md)]

4. À l’*Étape 2 – Inscrire votre application*, renseignez les champs suivants :

    * **Nom de l’application** – Donnez un nom à votre application.

    * **URL de la page d’accueil** – Entrez une URL pour votre page d’accueil.

    * **URL de redirection** – Une fois inscrits, les utilisateurs de votre application sont redirigés vers cette adresse pendant que votre application reçoit un code d’authentification d’Azure. Sélectionnez une de ces options :

        * **Utiliser une URL par défaut**– Cette option permet de créer et de télécharger automatiquement un exemple d’application d’analytique incorporée. L’URL par défaut est http://localhost:13526/.

        * **Utiliser une URL personnalisée** – Sélectionnez cette option si vous disposez déjà d’une application d’analytique incorporée et que vous savez quelle URL de redirection utiliser.

    * **Accès aux API** – Sélectionnez les API Power BI (également appelées « étendues ») dont votre application a besoin. Vous pouvez utiliser *Sélectionner tout* pour sélectionner toutes les API. Pour plus d’informations sur les autorisations d’accès de Power BI, consultez [Autorisations et consentement dans le point de terminaison de la plateforme d’identités Microsoft](/azure/active-directory/develop/v2-permissions-and-consent).

5. Sélectionnez **Inscription**.

    Les valeurs **ID d’application** et **Secret de l’application** de votre application Azure AD sont affichées dans la zone *Résumé*. Copiez ces valeurs pour les utiliser ultérieurement.

[!INCLUDE[registration tool steps 6-7](../../includes/register-tool-steps-6-7.md)]

8. (Facultatif) Si vous avez créé un espace de travail Power BI et que vous y avez chargé du contenu à l’aide de l’outil, vous pouvez maintenant sélectionner **Télécharger l’exemple d’application**. Veillez à copier toutes les informations contenues dans la zone *Résumé*.

[!INCLUDE[registration tool note](../../includes/register-tool-note.md)]

# <a name="manual-registration"></a>[Inscription manuelle](#tab/manual)

Utilisez l’inscription d’application manuelle Azure AD uniquement si vous créez une solution *Incorporer pour votre organisation*. Pour plus d’informations sur la façon d’inscrire les applications dans Azure Active Directory, consultez [Inscrire une application avec Azure Active Directory](/azure/active-directory/develop/quickstart-v2-register-an-app).

1. Connectez-vous au [portail Azure](https://portal.azure.com).

2. Sélectionnez votre locataire Azure AD en sélectionnant votre compte dans l’angle supérieur droit de la page.

3. Sélectionnez **Inscriptions d’applications**. Si vous ne voyez pas cette option, recherchez-la.
 
4. Dans *Inscriptions d’applications*, sélectionnez **Nouvelle inscription**.

5. Remplissez les champs suivants :

    * **Nom** – Donnez un nom à votre application.

    * **Type de compte pris en charge** – Sélectionnez qui peut utiliser l’application.

6. (Facultatif) Dans **URI de redirection**, ajoutez une URL de redirection.

7. Sélectionnez **Inscription**. Une fois votre application inscrite, vous êtes dirigé vers la page Vue d’ensemble de votre application, où vous pouvez obtenir l’*ID d’application*.

---

## <a name="change-your-azure-ad-apps-permissions"></a>Modifier les autorisations de votre application Azure AD

Après avoir inscrit votre application, vous pouvez apporter des modifications à ses autorisations. Il est possible de modifier les autorisations par programmation ou sur le portail Azure.

# <a name="azure"></a>[Microsoft Azure](#tab/Azure)

Sur le portail Azure, vous pouvez afficher votre application et apporter des modifications à ses autorisations.

1. Connectez-vous au [portail Azure](https://portal.azure.com).

2. Sélectionnez votre locataire Azure AD en sélectionnant votre compte dans l’angle supérieur droit de la page.

3. Sélectionnez **Inscriptions d’applications**. Si vous ne voyez pas cette option, recherchez-la.

4. À partir de l’onglet **Applications détenues**, sélectionnez votre application. L’application s’ouvre sous l’onglet *Vue d’ensemble*, où vous pouvez examiner l’*ID d’application*.

5. Sélectionnez l’onglet **Autorisations de l’API**.

6. Pour ajouter des autorisations, suivez ces étapes :

    1. Sélectionnez **Ajouter une autorisation**, puis **Service Power BI**.

    2. Sélectionnez **Autorisations déléguées** et ajoutez ou supprimez les autorisations de votre choix.

    3. Quand vous avez terminé, sélectionnez **Ajouter des autorisations** pour enregistrer vos modifications.

7. Pour supprimer une autorisation, suivez ces étapes :

    1. Sélectionnez les points de suspension (...) à droite de l’autorisation.
    
    2. Sélectionnez **Supprimer l’autorisation**.
    
    3. Dans la fenêtre contextuelle *Supprimer l’autorisation*, sélectionnez **Oui, supprimer**.

# <a name="http"></a>[HTTP](#tab/HTTP)

Pour modifier les autorisations de votre application Azure AD par programmation, vous devez obtenir les principaux de service (utilisateurs) existants au sein de votre locataire. Pour plus d’informations sur la procédure à suivre, voir [servicePrincipal](/graph/api/resources/serviceprincipal).

1. Pour obtenir tous les principaux de service au sein de votre locataire, appelez l’API `Get servicePrincipal` sans `{ID}`.

2. Recherchez un principal de service en utilisant l’*ID d’application* de votre application pour la propriété `appId`.

    ```json
    Post https://graph.microsoft.com/v1.0/servicePrincipals HTTP/1.1
    Authorization: Bearer ey..qw
    Content-Type: application/json
    {
    "accountEnabled" : true,
    "appId" : "{App_Client_ID}",
    "displayName" : "{App_DisplayName}"
    }
    ```

    >[!NOTE]
    >`displayName` est facultatif.

3. Accordez des autorisations Power BI à votre application en affectant une de ces valeurs à `consentType` :

    * `AllPrincipals` – Peut être utilisé uniquement par un administrateur Power BI pour accorder des autorisations au nom de tous les utilisateurs du locataire.

    * `Principal` – Utilisé pour accorder des autorisations au nom d’un utilisateur spécifique. Si vous utilisez cette option, ajoutez la propriété `principalId={User_ObjectId}` au corps de la demande.

     ```json
     Post https://graph.microsoft.com/v1.0/OAuth2PermissionGrants HTTP/1.1
     Authorization: Bearer ey..qw
     Content-Type: application/json
     {
     "clientId":"{Service_Plan_ID}",
     "consentType":"AllPrincipals",
     "resourceId":"c78a3685-1ce7-52cd-95f7-dc5aea8ec98e",
     "scope":"Dataset.ReadWrite.All Dashboard.Read.All Report.Read.All Group.Read Group.Read.All Content.Create Metadata.View_Any Dataset.Read.All Data.Alter_Any",
     "expiryTime":"2018-03-29T14:35:32.4943409+03:00",
     "startTime":"2017-03-29T14:35:32.4933413+03:00"
     }
     ```

    >[!NOTE]
    >* Si vous utilisez un **utilisateur maître**, pour éviter d’être invité à donner votre consentement par Azure AD, vous devez accorder des autorisations au compte principal.
    >* Le `resourceId` *c78a3685-1ce7-52cd-95f7-dc5aea8ec98e* est dépendant du locataire et non universel. Cette valeur est l’*objectId* de l’application *Service Power BI* dans Azure AD. Pour obtenir cette valeur à partir du portail Azure, accédez à [Applications d’entreprise > Toutes les applications](https://portal.azure.com/#blade/Microsoft_AAD_IAM/StartboardApplicationsMenuBlade/AllApps), puis recherchez *Service Power BI*.

4. Accordez des autorisations d’application à Azure AD en affectant une valeur à `consentType`.

    ```json
    Post https://graph.microsoft.com/v1.0/OAuth2PermissionGrants HTTP/1.1
    Authorization: Bearer ey..qw
    Content-Type: application/json
    {
    "clientId":"{Service_Plan_ID}",
    "consentType":"AllPrincipals",
    "resourceId":"61e57743-d5cf-41ba-bd1a-2b381390a3f1",
    "scope":"User.Read Directory.AccessAsUser.All",
    "expiryTime":"2018-03-29T14:35:32.4943409+03:00",
    "startTime":"2017-03-29T14:35:32.4933413+03:00"
    }
    ```

# <a name="c"></a>[C#](#tab/CSharp)

Vous pouvez aussi modifier les autorisations de votre application Azure AD en utilisant C#. Cette méthode peut être utile si vous envisagez d’automatiser certains de vos processus.

Pour plus d’informations sur les requêtes HTTP, consultez l’[onglet HTTP](register-app.md?tabs=customers%2CHTTP#change-your-azure-ad-apps-permissions).

```csharp
var graphClient = GetGraphClient();

currentState.createdApp = await graphClient.Applications
    .Request()
    .AddAsync(application);

System.Threading.Thread.Sleep(2000);

var passwordCredential = new PasswordCredential
{
    DisplayName = "Client Secret Created in C#"
};

currentState.createdSecret = await graphClient.Applications[currentState.createdApp.Id]
    .AddPassword(passwordCredential)
    .Request()
    .PostAsync();

var servicePrincipal = new ServicePrincipal
{
    AppId = currentState.createdApp.AppId
};

currentState.createdServicePrincipal = await graphClient.ServicePrincipals
    .Request()
    .AddAsync(servicePrincipal);

```

---

## <a name="next-steps"></a>Étapes suivantes

>[!div class="nextstepaction"]
>[Obtenir un jeton d’accès Azure AD pour votre application Power BI](get-azuread-access-token.md)

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)