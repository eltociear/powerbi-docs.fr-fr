---
title: Questions fréquentes sur Power BI Embedded
description: Parcourir une liste de questions fréquentes et de réponses sur Power BI Embedded.
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 05/27/2019
ms.openlocfilehash: af3c22197e4d6783787bd72c9cf010bf6db64bc1
ms.sourcegitcommit: 277fadf523e2555004f074ec36054bbddec407f8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68270970"
---
# <a name="frequently-asked-questions-about-power-bi-embedded"></a>Questions fréquentes sur Power BI Embedded

* Si vous avez des questions, [essayez d’interroger la communauté Power BI](http://community.powerbi.com/).
* Le problème persiste ? Visitez la [page de support Power BI](https://powerbi.microsoft.com/support/).

## <a name="general"></a>Général

### <a name="what-is-power-bi-embedded"></a>Qu'est-ce que Power BI Embedded ?

[Microsoft Power BI Embedded (PBIE)](azure-pbie-what-is-power-bi-embedded.md) permet aux développeurs d’applications d’incorporer dans des applications des rapports attrayants et totalement interactifs, sans avoir à créer leurs propres visualisations et contrôles de données.

### <a name="who-is-the-target-audience-for-power-bi-embedded"></a>Qui est le public cible de Power BI Embedded ?

Les développeurs et les éditeurs de logiciels (ISV) qui développent des applications.

### <a name="how-is-power-bi-embedded-different-from-power-bi-the-service"></a>En quoi Power BI Embedded est différent du service Power BI ?

Power BI est une solution d’analytique en tant que service qui offre aux organisations une vue unique de leurs données les plus critiques.

Microsoft a développé Power BI Embedded pour les éditeurs de logiciels indépendants (ISV) qui souhaitent incorporer des visuels dans leurs applications afin d’aider leurs clients à prendre des décisions d’ordre analytique. De cette façon, les éditeurs n’ont pas à créer leurs propres solutions d’analytique. L’[analytique incorporée](embedding.md) permet aux utilisateurs métier d’accéder aux données de l’entreprise et d’exécuter des requêtes afin de générer des insights au sein de l’application.


### <a name="what-is-the-difference-between-power-bi-premium-and-power-bi-embedded"></a>Quelle est la différence entre Power BI Premium et Power BI Embedded ?

Power BI Premium s’adresse aux entreprises qui souhaitent une solution d’informatique décisionnelle complète, leur permettant de visualiser au même emplacement les informations concernant leur organisation, leurs partenaires, leurs clients et leurs fournisseurs. Power BI Premium aide votre organisation à prendre des décisions. Power BI Premium est un produit SaaS qui permet aux utilisateurs de consommer du contenu par le biais d’applications mobiles, d’applications développées en interne ou du portail Power BI.

Power BI Embedded s’adresse aux éditeurs de logiciels indépendants qui souhaitent incorporer des visuels dans leurs applications. Power BI Embedded aide vos clients à prendre des décisions. Comme Power BI Embedded est conçu pour les développeurs d’applications, les clients de ces applications peuvent utiliser du contenu stocké sur la capacité Power BI Embedded, y compris toute personne à l’intérieur ou à l’extérieur de l’organisation. Vous ne pouvez pas partager le contenu Power BI Embedded via les fonctionnalités Publier sur le web en un clic et Publier sur SharePoint en un clic.

### <a name="what-is-the-microsoft-recommendation-for-when-a-customer-should-buy-power-bi-premium-vs-power-bi-embedded"></a>Que recommande Microsoft à un client qui doit choisir entre Power BI Premium et Power BI Embedded ?

Microsoft recommande Power BI Premium aux entreprises, car il s’agit d’une solution d’informatique décisionnel cloud libre-service conçue pour l’entreprise. Nous recommandons aux éditeurs de logiciels indépendants d’acheter Power BI Embedded pour ses composants d’analytique incorporée générée par le cloud. Toutefois, le client est libre d’acheter le produit de son choix.

Dans certains cas, un éditeur de logiciels indépendant (généralement de grande taille), en plus de l’incorporation aux applications, voudra utiliser une référence SKU P afin de bénéficier des avantages du service Power BI prépackagé au sein de son organisation. Certaines entreprises peuvent décider d’utiliser des références SKU A dans Azure si elles ne sont intéressées que par la création d’applications métier et par l’incorporation d’une analytique dans ces dernières, mais pas par l’utilisation du service Power BI complet.

### <a name="how-many-embed-tokens-can-i-create"></a>Combien de jetons incorporés puis-je créer ?

Les jetons d’incorporation des licences PRO sont destinés aux tests de développement. Par conséquent, un compte principal ou un [principal du service](embed-service-principal.md) Power BI ne peuvent donc générer qu’un nombre limité de jetons. [Achetez une capacité](#technical) pour l’incorporation dans un environnement de production. Lorsque vous achetez une capacité, le nombre de jetons incorporés que vous pouvez générer est illimité. Accédez à [Fonctionnalités disponibles](https://docs.microsoft.com/rest/api/power-bi/availablefeatures) pour vérifier la valeur qui indique l’utilisation actuelle de jetons incorporés en pourcentage.

## <a name="technical"></a>Technique

### <a name="what-is-the-difference-between-the-a-skus-in-azure-and-the-em-skus-in-office-365"></a>Quelle est la différence entre les références SKU A dans Azure et les références SKU EM dans Office 365 ?

PowerBI.com est une solution SaaS qui comprend de nombreuses fonctionnalités telles que la collaboration sociale ou l’abonnement aux e-mails. PowerBI.com aide les éditeurs de logiciels indépendants à gérer le contenu des solutions d’analytique incorporée et les paramètres au niveau du locataire.

Power BI Embedded est un ensemble d’API PaaS que les développeurs peuvent utiliser pour créer une solution d’analytique incorporée.

Voici une liste non exhaustive des différences de fonctionnalités qui existent entre ces solutions.

| Caractéristique | Power BI Embedded | Capacité Power BI Premium | Capacité Power BI Premium |
|----------------------------------------------------------------------------------|-------------------|---------------------------|---------------------------|
|   | (Références SKU A) | (Références SKU EM) | (Références SKU P) |
| Incorporer des artefacts provenant d’un espace de travail d’application Power BI | Capacité Azure | Capacité Office 365 | Capacité Office 365 |
| Utiliser des rapports Power BI dans une application incorporée | Oui | Oui | Oui |
| Utiliser des rapports Power BI dans SharePoint | Non | Oui | Oui |
| Utiliser des rapports Power BI dans Dynamics | Non | Oui | Oui |
| Utiliser des rapports Power BI dans Teams (à l’exception de l’application mobile) | Non | Oui | Oui |
| Accéder à du contenu avec une licence Power BI gratuite dans Powerbi.com et Power BI Mobile | Non | Non | Oui |
| Accéder à du contenu incorporé dans des applications MS Office avec une licence Power BI GRATUITE | Non | Oui | Oui |

### <a name="power-bi-now-offers-three-skus-for-embedding-a-skus-em-skus-and-p-skus-which-one-should-i-purchase-for-my-scenario"></a>Power BI propose maintenant trois références SKU pour l’incorporation : A, EM et P. Laquelle dois-je acheter pour mon scénario ?

|  |Référence SKU A (Power BI Embedded)  |Référence SKU EM (Power BI Premium)  |Référence SKU P (Power BI Premium)  |
|---------|---------|---------|---------|
|Achat  |Portail Azure |Office |Office |
|Cas d’usage | Incorporer du contenu dans votre application | <li> Incorporer du contenu dans votre application <br><br><br> <li> Incorporer du contenu dans les applications MS Office : <br> - [SharePoint](https://powerbi.microsoft.com/blog/integrate-power-bi-reports-in-sharepoint-online/) <br> - [Teams (à l’exception de l’application mobile)](https://powerbi.microsoft.com/blog/power-bi-teams-up-with-microsoft-teams/) <br> - [Dynamics 365](https://docs.microsoft.com/dynamics365/customer-engagement/basics/add-edit-power-bi-visualizations-dashboard) | <li> Incorporer du contenu dans votre application <br><br><br> <li> Incorporer du contenu dans les applications MS Office : <br> - [SharePoint](https://powerbi.microsoft.com/blog/integrate-power-bi-reports-in-sharepoint-online/) <br> - [Teams (à l’exception de l’application mobile)](https://powerbi.microsoft.com/blog/power-bi-teams-up-with-microsoft-teams/) <br> - [Dynamics 365](https://docs.microsoft.com/dynamics365/customer-engagement/basics/add-edit-power-bi-visualizations-dashboard) <br><br><br> <li> Partager du contenu avec des utilisateurs de Power BI par le biais du [service Power BI](https://powerbi.microsoft.com/)  |
|Facturation |Toutes les heures |Mensuelle |Mensuelle |
|Avec engagement  |Sans engagement |Annuel  |Mensuelle/Annuelle |
|Différenciation |Élasticité complète : augmenter/réduire la taille, interrompre/reprendre des ressources dans le portail Azure ou via l’API  |Peut être utilisée pour incorporer du contenu dans SharePoint Online et Microsoft Teams (à l’exception de l’application mobile) |Combiner l’incorporation dans les applications et utiliser le service Power BI dans la même capacité |

### <a name="what-are-the-prerequisites-to-create-a-pbie-capacity-in-azure"></a>Quelles sont les prérequis à la création d’une capacité PBIE dans Azure ?

* Connectez-vous à l’annuaire de votre organisation (les comptes Microsoft ne sont pas pris en charge).
* Vous devez avoir un locataire Power BI (c’est-à-dire qu’au moins un utilisateur de votre annuaire doit être inscrit auprès de Power BI). 
* Vous devez disposer d’un abonnement Azure dans votre annuaire d’organisation.

### <a name="how-can-i-monitor-power-bi-embedded-capacity-consumption"></a>Comment superviser la consommation des capacités Power BI Embedded ?

* Utilisez [le portail d’administration de Power BI](../service-admin-portal.md#power-bi-embedded).

* Téléchargez l’[application de métriques](https://docs.microsoft.com/power-bi/service-admin-premium-monitor-capacity) dans Power BI.

* Utilisez la [Journalisation des diagnostics Azure](azure-pbie-diag-logs.md).

### <a name="can-my-capacity-scale-automatically-to-adjust-to-my-app-consumption"></a>Ma capacité peut-elle évoluer automatiquement pour s’ajuster à la consommation de mon application ?

La mise à l’échelle automatique n’est pas disponible. Toutefois, toutes les API peuvent être mises à l’échelle à tout moment.

### <a name="why-creatingscalingresuming-a-capacity-results-in-putting-the-capacity-into-a-suspended-state"></a>Pourquoi les opérations de création, mise à l’échelle et reprise d’une capacité la font-elles basculer dans un état interrompu ?

Le provisionnement d’une capacité (mise à l’échelle/reprise/création) peut échouer. Vous pouvez utiliser l’API Get Details pour vérifier l’état de provisionnement (ProvisioningState) d’une capacité : [Capacités - Obtenir les détails](https://docs.microsoft.com/rest/api/power-bi-embedded/capacities/getdetails).

### <a name="can-i-only-create-power-bi-embedded-capacities-in-a-specific-region"></a>Puis-je uniquement créer des capacités Power BI Embedded dans une région spécifique ?

La fonctionnalité [Multi-Geo (préversion)](embedded-multi-geo.md) vous permet d’acheter une [capacité Power BI Embedded](azure-pbie-create-capacity.md) dans une région autre que celle de l’emplacement d’origine du locataire Power BI.

### <a name="why-cant-i-see-a-workspace-although-i-have-permissions"></a>Pourquoi m’est-il impossible de voir un espace de travail pour lequel je dispose d’autorisations ?

Les espaces de travail, applications ou artefacts pour lesquels un utilisateur reçoit des autorisations ne sont pas toujours immédiatement disponibles via les appels d’API.
Dans ce cas, il peut recevoir une réponse de l’API 'GET' l’informant qu’un artefact est manquant, ou une erreur peut se produire lorsque vous tentez d’utiliser l’artefact en question.
L’utilisateur peut résoudre ce problème en appelant [l’API refreshUserPermissions](https://docs.microsoft.com/rest/api/power-bi/users/refreshuserpermissions), qui met à jour les autorisations de l’utilisateur.


### <a name="how-can-i-find-my-pbi-tenant-region"></a>Comment déterminer la région de mon locataire PBI ?

La région de votre locataire PBI est accessible sur le portail PBI.

[https://app.powerbi.com/](https://app.powerbi.com/ ) > ? > À propos de Power BI

![À propos de Power BI](media/embedded-faq/about-01.png)
![Région du locataire](media/embedded-faq/tenant-location-01.png)

### <a name="what-does-the-cloud-solution-provider-csp-channel-support"></a>Que permet le canal Fournisseur de solutions Cloud (CSP) ?

* Le type d’abonnement CSP vous permet de créer des capacités PBIE pour votre locataire.
* Le compte partenaire permet de se connecter au locataire d’un client et d’acheter des capacités PBIE pour ce dernier, en spécifiant l’utilisateur du locataire du client comme administrateur de capacité Power BI.

### <a name="why-do-i-get-an-unsupported-account-message"></a>Pourquoi j’obtiens un message de compte non pris en charge ?

Power BI vous impose de vous inscrire avec un compte professionnel. Vous ne pouvez pas vous inscrire à Power BI avec un compte Microsoft.

### <a name="can-i-use-apis-to-create-and-manage-azure-capacities"></a>Puis-je utiliser des API pour créer et gérer des capacités Azure ?

Oui, les applets de commande PowerShell et les API REST Azure Resource Manager vous permettent de créer et de gérer des ressources PBIE.

* [API REST](https://docs.microsoft.com/rest/api/power-bi-embedded/) 
* [Applets de commande PowerShell](https://docs.microsoft.com/powershell/module/azurerm.powerbiembedded/)

### <a name="what-is-the-pbi-embedded-dedicated-capacity-role-in-a-pbi-embedded-solution"></a>Quel est le rôle d’une capacité dédiée PBI Embedded dans une solution PBI Embedded ?

Pour [promouvoir votre solution en production](embed-sample-for-customers.md#move-to-production), vous devez affecter le contenu Power BI (espace de travail d’application) que votre application utilise à une capacité Power BI Embedded (référence SKU A).

### <a name="in-what-azure-regions-is-pbi-embedded-available"></a>Dans quelles régions Azure PBI Embedded est-il disponible ?

[PAM](https://ecosystemmanager.azurewebsites.net/home) (EcoManager) - voir le responsable de la disponibilité produit

Régions disponibles (16 - mêmes régions que Power BI)

* États-Unis (6) - USA Est, USA Est 2, USA Centre Nord, USA Centre Sud, USA Ouest, USA Ouest 2
* Europe (2) - Europe Nord, Europe Ouest
* Asie-Pacifique (2) - Asie Sud-Est, Asie Est
* Brésil (1) - Brésil Sud
* Japon (1) - Japon Est
* Australie (1) - Australie Sud-Est
* Inde (1) - Inde Ouest
* Canada (1) - Canada Centre
* Royaume-Uni (1) - Royaume-Uni Sud

### <a name="what-is-power-bi-embeddeds-authentication-model"></a>Quel est le modèle d’authentification de Power BI Embedded ?

Power BI Embedded continue à utiliser Azure AD pour l’authentification de l’utilisateur maître (utilisateur désigné sous licence Power BI Pro), ou un [principal du service](embed-service-principal.md) pour l’authentification de l’application au sein de Power BI.  

 Un éditeur de logiciels indépendant peut implémenter ses propres méthodes d’authentification et ses propres autorisations pour ses applications.

Vous pouvez utiliser un annuaire existant si vous disposez déjà d’un locataire Azure AD. Vous pouvez également créer un nouveau locataire Azure AD pour la sécurité du contenu de votre application incorporée.

Pour obtenir un jeton AAD, vous pouvez utiliser une des [bibliothèques d’authentification Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries). Des bibliothèques clientes sont disponibles pour plusieurs plateformes.

### <a name="my-application-already-uses-aad-for-user-authentication-how-can-we-use-this-identity-when-authenticating-to-power-bi-in-a-user-owns-data-scenario"></a>My Application utilise déjà AAD pour l’authentification utilisateur. Comment utiliser cette identité pour s’authentifier auprès de Power BI dans un scénario où l’utilisateur possède les données ?

Il s’agit d’un flux OAuth On-Behalf-Of standard (<https://docs.microsoft.com/azure/active-directory/develop/web-api>). Vous devez configurer votre application afin qu’elle exige des autorisations pour le service Power BI (avec les étendues nécessaires). Une fois que vous avez un jeton d’utilisateur pour votre application, il vous suffit d’appeler l’API ADAL AcquireTokenAsync à l’aide du jeton d’accès d’utilisateur, et de spécifier l’URL des ressources Power BI en tant qu’ID de ressource.

```csharp
var context = new AD.AuthenticationContext(authorityUrl);
var userAssertion = new AD.UserAssertion(userAccessToken);
var clientAssertion = new AD.ClientAssertionCertificate(MyAppId, MyAppCertificate)
var authenticationResult = await context.AcquireTokenAsync(resourceId, clientAssertion, userAssertion);
```

### <a name="what-object-id-is-the-service-principal-object-id"></a>À quoi correspond l’ID d’objet du principal de service ?

L’*ID d’objet* qui s’affiche sur l’écran principal d’une application inscrite est l’ID d’objet de l’application.

L’ID d’objet qui se trouve dans la section *Application managée dans l’annuaire local > Propriétés* correspond à l’ID d’objet du principal de service que vous devez utiliser. Cet ID d’objet permet de référencer un principal de service pour les opérations, ou d’apporter des modifications à l’ID d’objet du principal de service (par exemple, utiliser un principal de service comme l’administrateur d’un espace de travail).

### <a name="how-is-power-bi-embedded-different-from-other-azure-services"></a>En quoi Power BI Embedded est différent des autres services Azure ?

Vous devez déjà disposer d’un compte Power BI pour acheter Power BI Embedded dans Azure. Votre région de déploiement Power BI Embedded détermine votre compte Power BI. Gérez votre ressource Power BI Embedded dans Azure aux fins suivantes :

* Augmenter/réduire la taille
* Ajouter des administrateurs de capacité
* Interrompre ou reprendre le service

Utilisez PowerBI.com pour attribuer/désattribuer des espaces de travail à votre capacité Power BI Embedded.

### <a name="what-content-pack-data-types-can-you-embed"></a>Quels types de données de pack de contenu est-il possible d’incorporer ?

Vous *ne pouvez pas* incorporer des **tableaux de bord** et des **vignettes** créés à partir de jeux de données de pack de contenu. Toutefois, vous *pouvez* incorporer des **rapports** créés à partir d’un jeu de données de pack de contenu.

### <a name="what-is-the-difference-between-using-row-level-security-rls-vs-javascript-filters"></a>Quelle est la différence entre la sécurité au niveau des lignes et les filtres JavaScript ?

On confond souvent ces deux méthodes, car l’une permet de contrôler ce qu’un utilisateur peut voir, tandis que l’autre permet d’optimiser ce que l’utilisateur voit.

Pour la sécurité au niveau des lignes, le développeur ISV contrôle le filtrage des données dans le cadre de la création du modèle et de la génération de jeton d’incorporation. L’utilisateur final voit uniquement ce que l’ISV l’autorise à voir. Dans ce cas, l’utilisateur peut choisir d’en voir moins que ce qui est filtré, mais il ne pourra pas contourner la configuration de sécurité au niveau des lignes et voir plus que ce qui est autorisé.

Pour le filtrage côté client (JavaScript), l’ISV peut décider de ce que l’utilisateur final voit dans la vue initiale, mais il ne peut pas contrôler les changements que l’utilisateur est susceptible d’appliquer à la vue proprement dite. Étant donné que le code client Javascript de l’utilisateur peut déclencher le filtrage des données sur le back-end, il n’est pas considéré comme sécurisé.

Pour plus d’informations, consultez [Sécurité au niveau des lignes ou filtres JavaScript](embedded-row-level-security.md#using-rls-vs-javascript-filters).

### <a name="how-do-i-manage-permissions-for-service-principals-with-power-bi"></a>Comment gérer les autorisations pour les principaux de service avec Power BI ?

Une fois que vous activez l’utilisation du [principal du service](embed-service-principal.md) avec Power BI, les autorisations AD de l’application n’ont plus d’effet. Les autorisations de l’application sont ensuite gérées par le biais du portail d’administration Power BI.

Les principaux de service héritent des autorisations de leur groupe de sécurité pour tous les paramètres du locataire Power BI. Pour limiter les autorisations, créez un groupe de sécurité dédié pour les principaux de service et ajoutez-le à la liste **À l’exception des groupes de sécurité spécifiques** pour les paramètres Power BI pertinents et activés.

Ce cas de figure a son importance quand vous ajoutez le principal du service comme **administrateur** au nouvel espace de travail. Vous pouvez gérer cette tâche via des [API](https://docs.microsoft.com/rest/api/power-bi/groups/addgroupuser) ou avec le service Power BI.

### <a name="when-to-use-an-application-id-vs-a-service-principal-object-id"></a>Quand utiliser un ID d’application ou un ID d’objet de principal du service ?

L’ **[ID d’application](embed-sample-for-customers.md#application-id)**  est utilisé pour créer le jeton d’accès lors du passage de l’ID d’application pour l’authentification.

Pour référencer un principal du service pour des opérations ou pour faire des changements, par exemple pour appliquer un principal du service en tant qu’administrateur à un espace de travail, vous utilisez l’ **[ID d’objet de principal du service](embed-service-principal.md#how-to-get-the-service-principal-object-id)** .

### <a name="can-you-manage-an-on-premises-data-gateway-with-service-principal"></a>Est-il possible de gérer une passerelle de données locale avec un principal du service ?

Vous ne pouvez pas gérer une passerelle de données locale avec un [principal du service](embed-service-principal.md) comme vous pouvez le faire avec un compte principal.

Avec un compte principal, vous pouvez installer une passerelle de données, ajouter des utilisateurs à la passerelle, vous connecter à des sources de données et effectuer d’autres tâches d’administration.

Avec le principal du service, vous pouvez configurer [une sécurité au niveau des lignes](embedded-row-level-security.md#on-premises-data-gateway-with-service-principal) en utilisant une source de données avec une connexion active locale SQL Server Analysis Services (SSAS). De cette façon, vous pouvez gérer les utilisateurs et leur accès aux données dans SSAS lors de l’intégration à **Power BI Embedded** avec un principal du service.

### <a name="can-you-sign-into-the-power-bi-service-with-service-principal"></a>Pouvez-vous vous connecter au service Power BI avec un principal du service ?

Non, vous ne pouvez pas vous connecter à Power BI avec un principal du service.

De plus, vous ne pouvez pas utiliser du contenu en tant qu’utilisateur dans des applications externes (incorporation SaaS), seulement quand vous générez un jeton d’incorporation.

### <a name="what-are-the-best-practices-to-improve-performance"></a>Quelles sont les bonnes pratiques pour améliorer les performances ?

[Performances de Power BI Embedded](embedded-performance-best-practices.md)

## <a name="licensing"></a>Licensing

### <a name="how-do-i-purchase-power-bi-embedded"></a>Comment acheter Power BI Embedded ?

Power BI Embedded est disponible via Azure.

### <a name="what-happens-if-i-already-purchased-power-bi-premium-and-now-i-want-some-power-bi-embedded-in-azure-benefits"></a>Que se passe-t-il si j’ai déjà acheté Power BI Premium et que je veux maintenant profiter de certains des avantages de Power BI Embedded dans Azure ?

Les clients continuent de payer les achats Power BI Premium existants jusqu’à la fin de leur contrat actuel et peuvent ensuite basculer leurs achats Power BI si nécessaire.

### <a name="do-i-still-have-to-buy-power-bi-premium-to-get-access-to-power-bi-embedded"></a>Dois-je toujours acheter Power BI Premium pour accéder à Power BI Embedded ?

Non. Power BI Embedded inclut la capacité basée sur Azure dont vous avez besoin pour déployer et distribuer votre solution aux clients.

### <a name="whats-the-purchase-commitment-for-power-bi-embedded"></a>Quel est la durée d’engagement pour Power BI Embedded ?

Les clients peuvent modifier leur utilisation sur une base horaire. Il n’existe aucun engagement mensuel ou annuel pour le service Power BI Embedded.

### <a name="how-does-the-usage-of-power-bi-embedded-show-up-on-my-bill"></a>Comment s’affiche l’utilisation de Power BI Embedded sur ma facture ?

Power BI Embedded est facturé à un tarif horaire prévisible basé sur le type de nœuds déployé. Tant qu’elle est active, votre ressource vous est facturée, même si aucune utilisation n’est enregistrée. Vous devez suspendre l’exécution de votre ressource pour arrêter la facturation.

### <a name="who-needs-a-power-bi-pro-license-for-power-bi-embedded-and-why"></a>Qui a besoin d’une licence Power BI Pro pour Power BI Embedded et pourquoi ?

Pour utiliser l’API REST, vous avez besoin d’une licence Power BI Pro ou d’un [principal de service](embed-service-principal.md). Pour ajouter des rapports à un espace de travail Power BI, les analystes doivent avoir une licence Power BI Pro ou utiliser un principal de service. Pour gérer les locataires et les capacités Power BI, les administrateurs doivent avoir une licence Power BI Pro.

Comme Power BI Embedded autorise l’utilisation du portail Power BI pour la gestion et la validation du contenu incorporé, une licence Power BI Pro est nécessaire pour authentifier l’application à l’intérieur de PowerBI.com, afin d’accéder aux rapports qui se trouvent dans les dépôts appropriés.

Cependant, pour [créer/modifier des rapports incorporés](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Create-Report-in-Embed-View) au sein de votre application, l’utilisateur final n’a pas besoin d’une licence Pro, car il n’a pas besoin d’être un utilisateur Power BI.

### <a name="can-i-get-started-for-free"></a>Puis-je commencer gratuitement ?

Oui, vous pouvez utiliser vos [crédits Azure](https://azure.microsoft.com/free/) pour Power BI Embedded.

### <a name="can-i-get-a-trial-experience-for-power-bi-embedded-in-azure"></a>Puis-je me procurer un essai de Power BI Embedded dans Azure ?

Étant donné que Power BI Embedded fait partie d’Azure, il est possible d’utiliser le service avec le [crédit de 200 $ reçu lors de l’inscription à Azure](https://azure.microsoft.com/free/).

### <a name="is-power-bi-embedded-available-for-national-clouds-us-government-germany-china"></a>Power BI Embedded est-il disponible pour les clouds nationaux (gouvernement américain, Allemagne, Chine) ?

Power BI Embedded est également disponible pour les [clouds nationaux](embed-sample-for-customers-national-clouds.md).

### <a name="is-power-bi-embedded-available-for-non-profits-and-educational"></a>Power BI Embedded est-il disponible pour les organisations à but non lucratif et les établissements d’enseignement ?

Il n’existe pas de tarifs Azure spéciaux pour les associations à but non lucratif et les établissements d’enseignement.

## <a name="power-bi-workspace-collection"></a>Collection d’espaces de travail Power BI

### <a name="what-is-power-bi-workspace-collection"></a>Présentation de la collection d’espaces de travail Power BI

La **collection d’espaces de travail Power BI** (**Power BI Embedded** version 1) est une solution basée sur la ressource Azure **Collection d’espaces de travail Power BI**. Cette solution permet de créer des applications **Power BI Embedded** pour les clients avec du contenu Power BI sous la solution **Collection d’espaces de travail Power BI**, des API dédiées et des clés de collection d’espaces de travail permettant d’authentifier l’application sur Power BI.

### <a name="can-i-migrate-from-power-bi-workspace-collection-to-power-bi-embedded"></a>Peut-on migrer d’une collection d’espaces de travail Power BI vers Power BI Embedded ?

1. Vous pouvez utiliser l’outil de migration pour cloner le contenu de la **collection d’espaces de travail Power BI** dans Power BI : https://docs.microsoft.com/power-bi/developer/migrate-from-powerbi-embedded#content-migration.

2. Commencez par la preuve de concept d’application **Power BI Embedded** qui utilise le contenu Power BI.

3. Au moment de passer en production, achetez une capacité dédiée **Power BI Embedded** et affectez-y votre contenu Power BI (espace de travail).

    > [!Note]
    > Vous pouvez continuer à utiliser la **collection d’espaces de travail Power BI** tout en travaillant en parallèle avec une solution **Power BI Embedded**. Quand vous êtes prêt, vous pouvez déplacer votre client vers la nouvelle solution **Power BI Embedded** et mettre hors service la solution **Collection d’espaces de travail Power BI**.

Pour plus d’informations, voir [Guide pratique pour migrer le contenu d’une collection d’espaces de travail Power BI Embedded vers Power BI Embedded](https://docs.microsoft.com/power-bi/developer/migrate-from-powerbi-embedded).

### <a name="is-power-bi-workspace-collection-on-a-deprecation-path"></a>La collection d’espaces de travail Power BI est-elle en voie d’être dépréciée ?

Oui, mais les clients qui utilisent déjà la **collection d’espaces de travail Power BI** pourront continuer à s’en servir jusqu’à sa dépréciation. Ils peuvent également créer de nouvelles collections d’espaces de travail et des applications **Power BI Embedded** qui utilisent encore la solution **Collection d’espaces de travail Power BI**.

Toutefois, cela signifie aussi que les nouvelles fonctionnalités ne sont pas ajoutées aux solutions **Collection d’espaces de travail Power BI**. Nous encourageons les clients à planifier leur migration vers la nouvelle **Power BI Embedded**.

### <a name="when-is-power-bi-workspace-collection-support-discontinued"></a>Quand se termine la prise en charge de la collection d’espaces de travail Power BI ?

Les clients qui utilisent déjà la solution **Collection d’espaces de travail Power BI** pourront continuer à s’en servir jusqu’à la fin du mois de juin 2018 ou de leur contrat de support.

### <a name="in-what-regions-can-i-create-a-pbi-workspace-collection"></a>Dans quelles régions peut-on créer des collections d’espaces de travail PBI ?

Les régions disponibles sont les suivantes : Canada Centre, États-Unis de l’Ouest, États-Unis de l’Est 2, Europe de l’Ouest, Europe du Nord, Inde de l’Ouest, Japon de l’Est, Nord du centre des États-Unis, Royaume-Uni Sud, Sud du Brésil, Sud du centre des États-Unis, Sud-Est asiatique et Sud-Est de l’Australie.

### <a name="why-should-i-migrate-from-pbi-workspace-collection-to-power-bi-embedded"></a>Pourquoi migrer d’une collection d’espaces de travail PBI vers Power BI Embedded ?

Certaines des nouvelles fonctionnalités de **Power BI Embedded** ne sont pas disponibles dans la **collection d’espaces de travail Power BI**.

En voici quelques exemples :
* Toutes les sources de données PBI sont prises en charge. Seules deux sources de données de la **collection d’espaces de travail Power BI** sont prises en charge. 
* De nouvelles fonctionnalités, comme les Questions et réponses, l’actualisation, les favoris, l’incorporation de tableaux de bord et de vignettes et les menus personnalisés, ne sont prises en charge que dans la solution **Power BI Embedded**.
* Modèle de facturation de la capacité.

## <a name="embedding-setup-tool"></a>Outil de configuration de l’incorporation

### <a name="what-is-the-embedding-setup-tool"></a>Qu’est-ce que l’outil de configuration de l’incorporation ?

[L’outil de configuration de l’incorporation](https://aka.ms/embedsetup) vous permet de démarrer rapidement et de télécharger un exemple d’application pour commencer l’incorporation avec Power BI.

### <a name="which-solution-should-i-choose"></a>Quelle solution dois-je choisir ?

* [L’incorporation pour vos clients](embedding.md#embedding-for-your-customers) permet d’incorporer des tableaux de bord et des rapports pour les utilisateurs qui n’ont pas de compte Power BI. Exécutez la solution [Incorporer pour vos clients](https://aka.ms/embedsetup/AppOwnsData).
* [L’incorporation pour votre organisation](embedding.md#embedding-for-your-organization) vous permet d’étendre le service Power BI. Exécutez la solution [Incorporer pour votre organisation](https://aka.ms/embedsetup/UserOwnsData).

### <a name="ive-downloaded-the-sample-app-which-solution-do-i-choose"></a>J’ai téléchargé l’exemple d’application : quelle solution choisir ?

Si vous travaillez avec l’expérience **Incorporer pour vos clients**, enregistrez et décompressez le fichier *PowerBI-Developer-Samples.zip*. Ensuite, ouvrez le dossier *PowerBI-Developer-Samples-master\App Owns Data* et exécutez le fichier *PowerBIEmbedded_AppOwnsData.sln*.

Si vous travaillez avec l’expérience **Incorporer pour votre organisation**, enregistrez et décompressez le fichier *PowerBI-Developer-Samples.zip*. Ensuite, ouvrez le dossier *PowerBI-Developer-Samples-master\User Owns Data\integrate-report-web-app* et exécutez le fichier *pbi-saas-embed-report.sln*.

### <a name="how-can-i-edit-my-registered-application"></a>Comment puis-je modifier mon application inscrite ?

Pour découvrir comment modifier des applications inscrites auprès d’Azure AD, consultez [Démarrage rapide : mettre à jour une application dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/quickstart-v1-update-azure-ad-app).

### <a name="how-can-i-edit-my-power-bi-user-profile-or-data"></a>Comment puis-je modifier mon profil ou mes données utilisateur Power BI ?

Vous pouvez découvrir comment modifier vos données Power BI [ici](https://docs.microsoft.com/power-bi/service-basic-concepts).

Pour plus d’informations, consultez [Résolution des problèmes de votre application incorporée](embedded-troubleshoot.md).

D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)
