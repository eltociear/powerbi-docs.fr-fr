---
title: Résolution des problèmes de votre application incorporée
description: Cet article décrit certains problèmes courants que vous pouvez rencontrer lors de l’incorporation de contenu à partir de Power BI.
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-developer
ms.topic: conceptual
ms.date: 07/03/2018
ms.author: maghan
ms.openlocfilehash: b3c9599ea3ce01094bb75d9b036fb25b1ca7109a
ms.sourcegitcommit: 627918a704da793a45fed00cc57feced4a760395
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37926556"
---
# <a name="troubleshooting-your-embedded-application"></a>Résolution des problèmes de votre application incorporée

Cet article décrit certains problèmes courants que vous pouvez rencontrer lors de l’incorporation de contenu à partir de Power BI.

## <a name="tools-for-troubleshooting"></a>Outils de résolution des problèmes

### <a name="fiddler-trace"></a>Trace Fiddler

[Fiddler](http://www.telerik.com/fiddler) est un outil gratuit de Telerik qui surveille le trafic HTTP.  Vous pouvez voir les allers et retours au niveau des API Power BI à partir de l’ordinateur client. Vous pouvez ainsi repérer les erreurs et d’autres informations connexes.

![Trace Fiddler](../includes/media/gateway-onprem-tshoot-tools-include/fiddler.png)

### <a name="f12-in-browser-for-front-end-debugging"></a>F12 dans le navigateur pour le débogage frontal

F12 lance la fenêtre de développeur dans votre navigateur. Cela vous permet d’examiner le trafic réseau et d’autres informations.

![Débogage de navigateur F12](media/embedded-troubleshoot/browser-f12.png)

### <a name="extracting-error-details-from-power-bi-response"></a>Extraction des détails de l’erreur à partir de la réponse de Power BI

Cet extrait de code montre comment extraire les détails de l’erreur d’une exception HTTP :

```
public static string GetExceptionText(this HttpOperationException exc)
{
    var errorText = string.Format("Request: {0}\r\nStatus: {1} ({2})\r\nResponse: {3}",
    exc.Request.Content, exc.Response.StatusCode, (int)exc.Response.StatusCode, exc.Response.Content);
    if (exc.Response.Headers.ContainsKey("RequestId"))
    {
        var requestId = exc.Response.Headers["RequestId"].FirstOrDefault();
        errorText += string.Format("\r\nRequestId: {0}", requestId);
    }

    return errorText;
}
```
Nous vous recommandons de journaliser les ID de demande (et les détails de l’erreur à des fins de dépannage).
Indiquez l’ID de la demande lorsque vous contactez le support Microsoft.

## <a name="app-registration"></a>Inscriptions des applications

**Échec de l’inscription des applications**

Les messages d’erreur dans le portail Azure ou la page d’inscription des applications Power BI indiquent des privilèges insuffisants. Pour inscrire une application, vous devez être administrateur du locataire Azure AD ou des inscriptions d’applications doivent être activées pour les utilisateurs non-administrateurs.

**Le service Power BI n’apparaît pas dans le portail Azure lors de l’inscription d’une nouvelle application**

Au moins un utilisateur doit être inscrit à Power BI. Si vous ne voyez pas **Service Power BI** dans la liste des API, aucun utilisateur n’est inscrit à Power BI.

## <a name="rest-api"></a>API REST

**Appel d’API retournant l’erreur 401**

Une capture Fiddler peut être nécessaire pour approfondir vos recherches. L’étendue d’autorisation requise est peut-être manquante pour l’application inscrite dans Azure AD. Vérifiez que l’étendue requise est présente au sein de l’inscription de l’application pour Azure AD dans le portail Azure.

**Appel d’API retournant l’erreur 403**

Une capture Fiddler peut être nécessaire pour approfondir vos recherches. Plusieurs raisons peuvent expliquer une erreur 403.

* L’utilisateur a dépassé la quantité de jetons incorporés pouvant être générés sur une capacité partagée. Vous devez acheter des capacités Azure pour générer des jetons incorporés et attribuer l’espace de travail à cette capacité. Consultez [Créer une capacité Power BI Embedded dans le portail Azure](https://docs.microsoft.com/azure/power-bi-embedded/create-capacity).
* Le jeton d’authentification Azure AD a expiré.
* L’utilisateur authentifié n’est pas membre du groupe (espace de travail d’application).
* L’utilisateur authentifié n’est pas administrateur du groupe (espace de travail d’application).
* L’en-tête d’autorisation n’est peut-être pas répertorié correctement. Vérifiez l’absence de fautes de frappe.

Le backend de l’application doit peut-être actualiser le jeton d’authentification avant d’appeler GenerateToken.

```
    GET https://wabi-us-north-central-redirect.analysis.windows.net/metadata/cluster HTTP/1.1
    Host: wabi-us-north-central-redirect.analysis.windows.net
    ...
    Authorization: Bearer eyJ0eXAiOi...
    ...
 
    HTTP/1.1 403 Forbidden
    ...
     
    {"error":{"code":"TokenExpired","message":"Access token has expired, resubmit with a new access token"}}
```

## <a name="authentication"></a>Authentification

### <a name="authentication-failed-with-aadsts70002-or-aadsts50053"></a>Échec de l’authentification avec AADSTS70002 ou AADSTS50053

**(AADSTS70002 : Erreur de validation des informations d’identification. AADSTS50053 : Vous avez essayé de vous connecter un trop grand nombre de fois avec un ID d’utilisateur ou un mot de passe incorrect)**

Si vous utilisez à la fois Power BI Embedded et l’authentification directe Azure AD et que vous obtenez des messages au moment de vous connecter, tels que ***error: unauthorized_client,error_description:AADSTS70002 : Erreur de validation des informations d’identification. AADSTS50053 : Vous avez essayé de vous connecter un trop grand nombre de fois avec un ID d’utilisateur ou un mot de passe incorrect***, cela est dû au fait que l’authentification directe est désactivée depuis le 14/06/2018.

Nous vous recommandons d’utiliser la prise en charge de l’[accès conditionnel Azure AD](https://cloudblogs.microsoft.com/enterprisemobility/2018/06/07/azure-ad-conditional-access-support-for-blocking-legacy-auth-is-in-public-preview/) pour bloquer l’authentification héritée ou d’utiliser l’[authentification directe Azure AD Directory](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnect-pass-through-authentication).

Cependant, il existe un moyen de la réactiver en utilisant une [stratégie Azure AD](https://docs.microsoft.com/en-us/azure/active-directory/manage-apps/configure-authentication-for-federated-users-portal#enable-direct-authentication-for-legacy-applications) dont la portée peut être limitée à l’organisation ou à un [principal du service](https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-application-objects#service-principal-object).

**_Nous vous recommandons de recourir à cette option qu’au cas par cas, selon l’application, et uniquement si vous avez besoin d’une solution de contournement._**

Pour créer cette stratégie, vous devez être **administrateur général** de l’annuaire dans lequel vous créez et affectez la stratégie. Voici un exemple de script qui vous montre comment créer la stratégie et l’affecter au principal du service de l’application :

1. Installez le [module PowerShell Azure AD (Préversion)](https://docs.microsoft.com/en-us/powershell/azure/active-directory/install-adv2?view=azureadps-2.0).

2. Exécutez les commandes PowerShell ci-dessous ligne par ligne (en veillant à ce que la variable $sp n’ait pas plus de 1 application en résultat).

```powershell
Connect-AzureAD
```

```powershell
$sp = Get-AzureADServicePrincipal -SearchString "Name_Of_Application"
```

```powershell
$policy = New-AzureADPolicy -Definition @("{`"HomeRealmDiscoveryPolicy`":{`"AllowCloudPasswordValidation`":true}}") -DisplayName EnableDirectAuth -Type HomeRealmDiscoveryPolicy -IsOrganizationDefault $false
```

```powershell
Add-AzureADServicePrincipalPolicy -Id $sp.ObjectId -RefObjectId $policy.Id 
```

Après avoir affecté la stratégie et avant d’effectuer un test, attendez environ 15 à 20 secondes, le temps qu’elle se propage.

**La génération du jeton échoue lors de la fourniture de l’identité effective**

GenerateToken peut échouer, quand une identité effective est fournie, pour différentes raisons.

* Le jeu de données ne prend pas en charge les identités effectives.
* Le nom d’utilisateur n’a pas été fourni.
* Le rôle n’a pas été fourni.
* L’ID du jeu de données n’a pas été fourni.
* L’utilisateur ne dispose des autorisations appropriées

Pour vérifier le motif de l’erreur, essayez ce qui suit.

* Exécutez [get dataset](https://docs.microsoft.com/rest/api/power-bi/datasets). La propriété IsEffectiveIdentityRequired est-elle définie sur True ?
* Le nom d’utilisateur est obligatoire pour les identités effectives.
* Si IsEffectiveIdentityRolesRequired est défini sur True, le rôle est requis.
* L’ID du jeu de données est obligatoire pour les identités effectives.
* Pour Analysis Services, l’utilisateur principal doit être un administrateur de passerelle.

### <a name="aadsts90094-the-grant-requires-admin-permission"></a>AADSTS90094 : L’octroi nécessite une autorisation de l’administrateur

**_Symptômes :_**</br>
Quand un utilisateur non-administrateur tente de se connecter à une application pour la première fois et octroie un consentement, il obtient l’erreur suivante :
* Le test de consentement nécessite une autorisation d’accès aux ressources de votre organisation que seul un administrateur peut accorder. Demandez à un administrateur de vous accorder une autorisation d’accès à cette application avant de l’utiliser.
* AADSTS90094 : L’octroi nécessite une autorisation de l’administrateur.

    ![Test de consentement](media/embedded-troubleshoot/consent-test-01.png)

Un utilisateur administrateur peut se connecter et octroyer un consentement.

**_Cause racine :_**</br>
Le consentement de l’utilisateur est désactivé pour le locataire.

**_Plusieurs solutions sont possibles :_**

*Activez le consentement de l’utilisateur pour l’ensemble du locataire (tous les utilisateurs, toutes les applications)*
1. Dans le portail Azure, accédez à « Azure Active Directory » => « Utilisateurs et groupes » => « Paramètres utilisateur »
2. Activez « Les utilisateurs peuvent autoriser les applications à accéder aux données de l’entreprise en leur nom », puis enregistrez les modifications.

    ![Correctif du test de consentement](media/embedded-troubleshoot/consent-test-02.png)

*Octroyer des autorisations par un administrateur* Octroyer des autorisations d’accès à l’application par un administrateur (soit pour l’ensemble du locataire, soit pour un utilisateur spécifique).

## <a name="data-sources"></a>Sources de données

**L’éditeur de logiciels indépendant souhaite disposer d’informations d’identification différentes pour la même source de données**

Une source de données peut avoir un ensemble unique d’informations d’identification pour un même utilisateur principal. Si vous avez besoin d’utiliser des informations d’identification différentes, créez des utilisateurs principaux supplémentaires. Ensuite, affectez différentes informations d’identification dans chaque contexte d’utilisateur principal à gérer, et effectuez l’incorporation à l’aide du jeton Azure AD de cet utilisateur.

## <a name="content-rendering"></a>Restitution du contenu

**Le rendu (ou la consommation) du contenu incorporé échoue ou expire**

Vérifiez que le jeton d’incorporation n’a pas expiré. Vérifiez que vous cochez le jeton d’incorporation et que vous l’actualisez. Pour plus d’informations, consultez [Actualiser le jeton à l’aide du SDK JavaScript](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Refresh-token-using-JavaScript-SDK-example).

**Le tableau de bord ou rapport n’est pas chargé**

Si l’utilisateur ne peut pas voir le rapport ou le tableau de bord, vérifiez que ce dernier se charge correctement dans powerbi.com. Le rapport ou tableau de bord ne fonctionne pas dans votre application s’il n’est pas chargé dans powerbi.com.

**Un tableau de bord ou rapport s’exécute lentement**

Ouvrez le fichier à partir de Power BI Desktop ou dans powerbi.com, puis vérifiez que les performances sont acceptables pour écarter des problèmes avec votre application ou les API d’incorporation.

## <a name="onboarding-experience-tool-for-embedding"></a>Outil d’expérience d’intégration pour l’incorporation

Vous pouvez passer par [l’outil d’expérience d’intégration](https://aka.ms/embedsetup) pour télécharger rapidement un exemple d’application. Vous pouvez ensuite comparer votre application à l’exemple.

### <a name="prerequisites"></a>Conditions préalables

Vérifiez que vous disposez de tous les prérequis appropriés avant d’utiliser l’outil d’expérience d’intégration. Vous avez besoin d’un compte **Power BI Pro** et d’un abonnement **Microsoft Azure**.

* Si vous n’avez pas d’abonnement à **Power BI Pro**, [inscrivez-vous à un essai gratuit](https://powerbi.microsoft.com/en-us/pricing/) avant de commencer.
* Si vous n’avez pas d’abonnement Azure, créez un [compte gratuit](https://azure.microsoft.com/free/?WT.mc_id=A261C142F) avant de commencer.
* Vous aurez besoin de votre propre installation de [client Azure Active Directory ](create-an-azure-active-directory-tenant.md).
* [Visual Studio](https://www.visualstudio.com/) doit être installé (version 2013 ou ultérieure).

### <a name="common-issues"></a>Problèmes courants

Voici quelques problèmes courants que vous pouvez rencontrer lors du test avec l’outil d’expérience d’intégration :

#### <a name="using-the-embed-for-your-customers-sample-application"></a>Utilisation de l’exemple d’application Embed for your customers (Incorporer pour vos clients)

Si vous travaillez avec l’expérience **Incorporer pour vos clients**, enregistrez et décompressez le fichier *PowerBI-Developer-Samples.zip*. Ensuite, ouvrez le dossier *PowerBI-Developer-Samples-master\App Owns Data* et exécutez le fichier *PowerBIEmbedded_AppOwnsData.sln*.

Quand vous sélectionnez **Accorder des autorisations** (à l’étape Accorder des autorisations), vous obtenez l’erreur suivante :

    AADSTS70001: Application with identifier <client ID> was not found in the directory <directory ID>

La solution consiste à fermer la fenêtre contextuelle, à attendre quelques secondes et à recommencer l’opération. Il peut être nécessaire de répéter cette opération quelques fois. Un intervalle de temps provoque ce problème : le processus d’inscription de l’application ne se termine pas quand il est disponible pour des API externes.

Le message d’erreur suivant s’affiche lors de l’exécution de l’exemple d’application :

    Password is empty. Please fill password of Power BI username in web.config.

Cette erreur se produit, car la seule valeur qui n’est pas injectée dans l’exemple d’application est votre mot de passe utilisateur. Ouvrez le fichier Web.config dans la solution et renseignez le champ pbiPassword avec votre mot de passe utilisateur.

#### <a name="using-the-embed-for-your-organization-sample-application"></a>Utilisation de l’exemple d’application Embed for your organization (Incorporer pour votre organisation)

Si vous travaillez avec l’expérience **Incorporer pour votre organisation**, enregistrez et décompressez le fichier *PowerBI-Developer-Samples.zip*. Ensuite, ouvrez le dossier *PowerBI-Developer-Samples-master\User Owns Data\integrate-report-web-app* et exécutez le fichier *pbi-saas-embed-report.sln*.

Quand vous exécutez l’exemple d’application **Embed for your organization**, vous obtenez l’erreur suivante :

    AADSTS50011: The reply URL specified in the request does not match the reply URLs configured for the application: <client ID>

La raison en est que l’URL de redirection spécifiée pour l’application de serveur web est différente de l’URL de l’exemple. Si vous voulez inscrire l’exemple d’application, utilisez `http://localhost:13526/` comme URL de redirection.

Si vous voulez modifier l’application inscrite, découvrez comment modifier [l’application inscrite auprès d’AAD](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications#updating-an-application), pour que l’application puisse fournir l’accès aux API web.

Si vous voulez modifier votre profil ou vos données utilisateur Power BI, découvrez comment modifier vos [données Power BI](https://docs.microsoft.com/en-us/power-bi/service-basic-concepts).

Pour plus d’informations, consultez le [FAQ sur Power BI Embedded](embedded-faq.md).

D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)