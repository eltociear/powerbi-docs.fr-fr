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
ms.date: 05/22/2019
ms.openlocfilehash: 1bdc31d550573b926d45776307b8fcade95f0dc0
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66222173"
---
# <a name="frequently-asked-questions-about-power-bi-embedded"></a>Questions fréquentes sur Power BI Embedded

* Si vous avez des questions, [essayez d’interroger la communauté Power BI](http://community.powerbi.com/).
* Le problème persiste ? Visitez la [page de support Power BI](https://powerbi.microsoft.com/support/).

## <a name="general"></a>Général

### <a name="what-is-power-bi-embedded"></a>Qu'est-ce que Power BI Embedded ?

[Microsoft Power BI Embedded (PBIE)](azure-pbie-what-is-power-bi-embedded.md) permet aux développeurs d’application incorporer des rapports totalement interactifs exceptionnels dans leurs applications sans avoir à créer leurs propres visualisations de données et les contrôles à partir de zéro.

### <a name="who-is-the-target-audience-for-power-bi-embedded"></a>Qui est le public cible de Power BI Embedded ?

Les développeurs et éditeurs de logiciels, également appelé éditeurs indépendants (ISV), codent des applications.

### <a name="how-is-power-bi-embedded-different-from-power-bi-the-service"></a>En quoi Power BI Embedded est différent du service Power BI ?

Power BI est une solution d’analytique en tant que service qui offre aux organisations une vue unique de leurs données les plus critiques.

Microsoft a développé Power BI Embedded pour les éditeurs de logiciels souhaitant incorporer des éléments visuels dans leurs applications pour aider leurs clients à prendre des décisions d’analyse. Cela évite les éditeurs de logiciels d’avoir à créer des solutions des leurs propres analytique eux-mêmes. [Incorporé analytique](embedding.md) permet aux utilisateurs professionnels d’accéder aux données d’entreprise et d’exécuter des requêtes qu’il génère des informations au sein de l’application.


### <a name="what-is-the-difference-between-power-bi-premium-and-power-bi-embedded"></a>Quelle est la différence entre Power BI Premium et Power BI Embedded ?

Power BI Premium est la capacité destinée aux entreprises qui souhaitent une solution Décisionnelle complète qui fournit une vue unique de son organisation, les partenaires, les clients et les fournisseurs. Power BI Premium aide votre organisation à prendre des décisions. Power BI Premium est un produit SaaS qui permet aux utilisateurs de consommer du contenu par le biais des applications mobiles, des applications développées en interne ou sur le portail Power BI.

Power BI Embedded concerne les éditeurs de logiciels indépendants qui souhaitent incorporer des éléments visuels dans leurs applications. Power BI Embedded aide vos clients à prendre des décisions. Comme Power BI Embedded est conçu pour les développeurs d’applications, les clients de ces applications peuvent utiliser du contenu stocké sur la capacité Power BI Embedded, y compris toute personne à l’intérieur ou à l’extérieur de l’organisation. Vous ne pouvez pas partager de Power BI Embedded publication de contenu de la capacité via un clic sur le Web ou de publication en un clic sur SharePoint.

### <a name="what-is-the-microsoft-recommendation-for-when-a-customer-should-buy-power-bi-premium-vs-power-bi-embedded"></a>Que recommande Microsoft à un client qui doit choisir entre Power BI Premium et Power BI Embedded ?

Microsoft recommande que les entreprises achètent Power BI Premium, une entreprise, la solution de décisionnel libre-service de services cloud. Nous vous recommandons de que éditeurs de logiciels indépendants achètent Power BI Embedded pour ses composants d’analytique d’embedded sur le cloud. Toutefois, un client ne dispose d’aucune restriction sur le produit à acheter.

Il existe peut-être certains cas où un ISV (en général, grand), outre l’incorporation de l’application, souhaite utiliser une référence SKU P pour obtenir les avantages supplémentaires du service Power BI Prépackagé au sein de leur organisation. Certaines entreprises peuvent décider d’utiliser des références SKU A dans Azure si elles ne sont intéressées que par la création d’applications métier et par l’incorporation d’une analytique dans ces dernières, mais pas par l’utilisation du service Power BI complet.

### <a name="how-many-embed-tokens-can-i-create"></a>Combien de jetons incorporés puis-je créer ?

Incorporer des jetons avec une licence PRO sont destinées au test de développement, afin de compte principal de Power BI ou [principal du service](embed-service-principal.md) ne peut générer un nombre limité de jetons. [Achetez une capacité](#technical) pour l’incorporation dans un environnement de production. Il n’existe aucune limite quant au nombre de jetons, que vous pouvez générer lorsque vous achetez une capacité incorporés. Accédez à [Fonctionnalités disponibles](https://docs.microsoft.com/rest/api/power-bi/availablefeatures) pour vérifier la valeur qui indique l’utilisation actuelle de jetons incorporés en pourcentage.

## <a name="technical"></a>Technique

### <a name="what-is-the-difference-between-the-a-skus-in-azure-and-the-em-skus-in-office-365"></a>Quelle est la différence entre les références SKU A dans Azure et les références SKU EM dans Office 365 ?

PowerBI.com est un logiciel d’entreprise en tant que Service (SaaS) solution avec nombreuses fonctionnalités telles que la collaboration sociale, d’abonnement par courrier électronique et d’autres fonctionnalités. PowerBI.com aide les ISV à gérer leur solution d’analytique incorporée contenue et des paramètres au niveau du client.

Power BI Embedded est une plateforme comme un Service (PaaS) de développeurs d’API servant à créer une solution d’analytique incorporée.

Voici une liste partielle des différences de fonctionnalités.

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
|Différenciation |Élasticité complète : augmenter/réduire la taille, interrompre/reprendre des ressources dans le portail Azure ou via l’API  |Vous pouvez utiliser pour incorporer du contenu dans SharePoint Online et Microsoft Teams (excepté pour les applications mobiles) |Combiner l’incorporation dans les applications et utiliser le service Power BI dans la même capacité |

### <a name="what-are-the-prerequisites-to-create-a-pbie-capacity-in-azure"></a>Quelles sont les prérequis à la création d’une capacité PBIE dans Azure ?

* Connectez-vous à votre annuaire d’organisation (comptes ne sont pas pris en charge de Microsoft).
* Vous devez disposer d’un locataire Power BI, autrement dit, au moins un utilisateur dans votre annuaire s’est inscrit pour Power BI. 
* Vous devez disposer d’un abonnement Azure dans votre annuaire d’organisation.

### <a name="how-can-i-monitor-power-bi-embedded-capacity-consumption"></a>Comment superviser la consommation des capacités Power BI Embedded ?

* Utilisez [le portail d’administration de Power BI](../service-admin-portal.md#power-bi-embedded).

* Téléchargez l’[application de métriques](https://review.docs.microsoft.com/power-bi/service-admin-premium-monitor-capacity) dans Power BI.

* Utilisez la [Journalisation des diagnostics Azure](azure-pbie-diag-logs.md).

### <a name="can-my-capacity-scale-automatically-to-adjust-to-my-app-consumption"></a>Ma capacité peut évoluer automatiquement pour s’ajuster à la consommation de mon application ?

Il n’existe pas de mise à l’échelle maintenant automatique, toutes les API sont disponibles à l’échelle à tout moment.

### <a name="why-creatingscalingresuming-a-capacity-results-in-putting-the-capacity-into-a-suspended-state"></a>Pourquoi les opérations de création, mise à l’échelle et reprise d’une capacité la font-elles basculer dans un état interrompu ?

La capacité d’approvisionnement (mise à l’échelle/reprise/créer) peut échouer. Vous pouvez utiliser l’API Get de détails pour vérifier ProvisioningState d’une capacité : [Capacités - Obtenir les détails](https://docs.microsoft.com/rest/api/power-bi-embedded/capacities/getdetails).

### <a name="can-i-only-create-power-bi-embedded-capacities-in-a-specific-region"></a>Puis-je uniquement créer des capacités Power BI Embedded dans une région spécifique ?

La fonctionnalité [Multi-Geo (préversion)](embedded-multi-geo.md) vous permet d’acheter une [capacité Power BI Embedded](azure-pbie-create-capacity.md) dans une région autre que celle de l’emplacement d’origine du locataire Power BI.

### <a name="how-can-i-find-my-pbi-tenant-region"></a>Comment puis-je trouver ma région du locataire PBI ?

Vous pouvez utiliser le portail PBI pour rechercher votre région PBI locataire.

[https://app.powerbi.com/](https://app.powerbi.com/) > ? > À propos de Power BI

![À propos de Power BI](media/embedded-faq/about-01.png)
![Région du locataire](media/embedded-faq/tenant-location-01.png)

### <a name="what-does-the-cloud-solution-provider-csp-channel-support"></a>Ce que le canal de fournisseur de solutions Cloud (CSP) prend en charge ?

* Le type d’abonnement CSP vous permet de créer des capacités PBIE pour votre locataire.
* Le compte partenaire permet de se connecter au locataire d’un client et d’acheter des capacités PBIE pour ce dernier, en spécifiant l’utilisateur du locataire du client comme administrateur de capacité Power BI.

### <a name="why-do-i-get-an-unsupported-account-message"></a>Pourquoi j’obtiens un message de compte non pris en charge ?

Power BI vous impose de vous inscrire avec un compte professionnel. Tente de s’inscrire à Power BI à l’aide d’un compte Microsoft n’est pas pris en charge.

### <a name="can-i-use-apis-to-create-and-manage-azure-capacities"></a>Puis-je utiliser des API pour créer et gérer les capacités de Azure ?

Oui, il existe des applets de commande Powershell et API REST de Azure Resource Manager que vous pouvez utiliser pour créer et gérer des ressources PBIE.

* [API REST](https://docs.microsoft.com/rest/api/power-bi-embedded/)
* [Applets de commande PowerShell](https://docs.microsoft.com/powershell/module/azurerm.powerbiembedded/)

### <a name="what-is-the-pbi-embedded-dedicated-capacity-role-in-a-pbi-embedded-solution"></a>Quel est le rôle d’une capacité dédiée PBI Embedded dans une solution PBI Embedded ?

Pour [promouvoir votre solution en production](embed-sample-for-customers.md#move-to-production), vous devez affecter le contenu de Power BI (espace de travail) utilise votre application à une capacité Power BI Embedded (une référence (SKU)).

### <a name="in-what-azure-regions-is-pbi-embedded-available"></a>Dans quelles régions Azure est incorporé PBI disponible ?

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

### <a name="what-is-power-bi-embeddeds-authentication-model"></a>Nouveautés modèle d’authentification du Power BI Embedded

Power BI Embedded continue à utiliser Azure AD pour l’authentification d’utilisateur principal (utilisateur désigné Power BI Pro sous licence), ou avec [principal du service](embed-service-principal.md) pour l’authentification de l’application à l’intérieur de Power BI.  

 Un éditeur de logiciels indépendant peut implémenter sa propre authentification et autorisation pour leurs applications.

Vous pouvez utiliser votre annuaire existant si vous disposez déjà d’un locataire Azure AD. Vous pouvez également créer un locataire Azure AD pour la sécurité de contenu de votre application incorporée.

Pour obtenir un jeton AAD, vous pouvez utiliser une des [bibliothèques d’authentification Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries). Des bibliothèques clientes sont disponibles pour plusieurs plateformes.

### <a name="my-application-already-uses-aad-for-user-authentication-how-can-we-use-this-identity-when-authenticating-to-power-bi-in-a-user-owns-data-scenario"></a>My Application utilise déjà AAD pour l’authentification utilisateur. Comment utiliser cette identité pour s’authentifier auprès de Power BI dans un scénario où l’utilisateur possède les données ?

Il s’agit standard flux OAuth on-behalf-of (<https://docs.microsoft.com/azure/active-directory/develop/web-api>). Vous devez configurer votre application pour exiger des autorisations de service (avec les étendues requis) de Power BI. Une fois que vous avez un jeton d’utilisateur à votre application, vous appelez simplement pour ADAL API AcquireTokenAsync à l’aide de l’accès utilisateur du jeton et spécifiez l’URL de ressource Power BI en tant que l’ID de ressource :

```csharp
var context = new AD.AuthenticationContext(authorityUrl);
var userAssertion = new AD.UserAssertion(userAccessToken);
var clientAssertion = new AD.ClientAssertionCertificate(MyAppId, MyAppCertificate)
var authenticationResult = await context.AcquireTokenAsync(resourceId, clientAssertion, userAssertion);
```

### <a name="what-object-id-is-the-service-principal-object-id"></a>Quel objet QU'ID est l’ID d’objet principal de service ?

Le *ID d’objet* à partir de l’écran principal d’une application inscrite est l’ID d’objet pour l’application.

L’objet ID trouvé dans le *application gérée dans le répertoire local > Propriétés* section correspond à l’ID d’objet principal de service vous devez utiliser. Cet ID d’objet consiste à faire référence à un principal de service pour les opérations ou à apporter des modifications à l’objet principal de service ID. Telles que l’application un principal de service en tant qu’administrateur à un espace de travail.

### <a name="how-is-power-bi-embedded-different-from-other-azure-services"></a>En quoi Power BI Embedded est différent des autres services Azure ?

Vous devez disposer d’un compte Power BI avant d’acheter Power BI Embedded dans Azure. Votre région Power BI Embedded déployée détermine votre compte Power BI. Gérez votre ressource Power BI Embedded dans Azure aux fins suivantes :

* Augmenter/réduire la taille
* Ajouter des administrateurs de capacité
* Suspendre/reprendre le service

Utilisez PowerBI.com pour attribuer/désattribuer des espaces de travail à votre capacité Power BI Embedded.

### <a name="what-are-the-supported-deploy-regions"></a>Quelles sont prises en charge déployer régions ?

Sud-Est de l’Australie, Sud du Brésil, Canada Centre, États-Unis de l'Est 2, Inde-Ouest, Japon de l'Est, Nord du centre des États-Unis, Europe du Nord, Sud du centre des États-Unis, Sud-Est asiatique, Royaume-Uni Sud, Europe de l’Ouest, États-Unis de l'Ouest et États-Unis de l'Ouest 2.

### <a name="what-content-pack-data-types-can-you-embed"></a>Quels types de données du pack de contenu peut incorporer ?

Vous *ne peut pas* incorporer **des tableaux de bord** et **vignettes** créée à partir de jeux de données de pack de contenu. Toutefois, vous *pouvez* incorporer **rapports** créée à partir d’un jeu de données du pack de contenu.

### <a name="what-is-the-difference-between-using-row-level-security-rls-vs-javascript-filters"></a>Quelle est la différence entre l’utilisation de Visual Studio de sécurité au niveau des lignes (RLS). et les filtres JavaScript ?

Il y a souvent confusion autour de quand utiliser RLS par rapport aux filtres de JavaScript, car une méthode est sur le contrôle de ce que peut voir un utilisateur spécifique, et l’autre est sur l’optimisation de la vue.

Pour la sécurité au niveau des lignes, le développeur ISV contrôle le filtrage des données dans le cadre de la création du modèle et de la génération de jeton d’incorporation. L’utilisateur final voit uniquement ce que l’ISV l’autorise à voir. Dans ce cas, l’utilisateur peut choisir d’en voir moins que ce qui est filtré, mais il ne pourra pas contourner la configuration de sécurité au niveau des lignes et voir plus que ce qui est autorisé.

Pour le filtrage côté client (JavaScript) l’ISV peut décider de ce que l’utilisateur final voit à la vue initiale, mais ils ne peut pas contrôler les modifications de que l’utilisateur final peuvent s’appliquer à la vue proprement dite. Étant donné que l’utilisateur ou le code de client Javascript peut déclencher le filtrage sur le serveur principal des données, il ne peut pas être considérée comme sécurisée.

Pour plus d’informations, consultez [Sécurité au niveau des lignes ou filtres JavaScript](embedded-row-level-security.md#using-rls-vs-javascript-filters).

### <a name="how-do-i-manage-permissions-for-service-principals-with-power-bi"></a>Comment gérer les autorisations pour les principaux de service avec Power BI ?

Une fois que vous activez [principal du service](embed-service-principal.md) pour utiliser avec Power BI, les autorisations des applications AD n’entrent en vigueur plus. Les autorisations de l’application sont ensuite gérées par le biais du portail d’administration Power BI.

Les principaux de service héritent des autorisations de leur groupe de sécurité pour tous les paramètres du locataire Power BI. Pour limiter les autorisations, créer un groupe de sécurité dédié pour les principaux de service et l’ajouter à la **à l’exception des groupes de sécurité spécifiques** liste pour les paramètres de Power BI pertinentes, activés.

Ce cas de figure a son importance quand vous ajoutez le principal du service comme **administrateur** au nouvel espace de travail. Vous pouvez gérer cette tâche via des [API](https://docs.microsoft.com/rest/api/power-bi/groups/addgroupuser) ou avec le service Power BI.

### <a name="when-to-use-an-application-id-vs-a-service-principal-object-id"></a>Quand utiliser un ID d’application ou un ID d’objet de principal du service ?

L’ **[ID d’application](embed-sample-for-customers.md#application-id)**  est utilisé pour créer le jeton d’accès lors du passage de l’ID d’application pour l’authentification.

Pour référencer un principal du service pour des opérations ou pour faire des changements, par exemple pour appliquer un principal du service en tant qu’administrateur à un espace de travail, vous utilisez l’ **[ID d’objet de principal du service](embed-service-principal.md#how-to-get-the-service-principal-object-id)** .

### <a name="can-you-manage-an-on-premises-data-gateway-with-service-principal"></a>Est-il possible de gérer une passerelle de données locale avec un principal du service ?

Vous ne pouvez pas gérer une passerelle de données locale avec un [principal du service](embed-service-principal.md) comme vous pouvez le faire avec un compte principal.

Avec un compte principal, vous pouvez installer une passerelle de données, ajouter des utilisateurs à la passerelle, vous connecter à des sources de données et effectuer d’autres tâches d’administration.

Avec le principal du service, vous pouvez configurer [une sécurité au niveau des lignes](embedded-row-level-security.md#on-premises-data-gateway-with-service-principal-preview) en utilisant une source de données avec une connexion active locale SQL Server Analysis Services (SSAS). De cette façon, vous pouvez gérer les utilisateurs et leur accès aux données dans SSAS lors de l’intégration à **Power BI Embedded** avec un principal du service.

### <a name="can-you-sign-into-the-power-bi-service-with-service-principal"></a>Pouvez-vous vous connecter au service Power BI avec un principal du service ?

Non, vous ne pouvez pas vous connecter à Power BI avec un principal du service.

De plus, vous ne pouvez pas utiliser du contenu en tant qu’utilisateur dans des applications externes (incorporation SaaS), seulement quand vous générez un jeton d’incorporation.

### <a name="what-are-the-best-practices-to-improve-performance"></a>Quelles sont les bonnes pratiques pour améliorer les performances ?

[Performances de Power BI Embedded](embedded-performance-best-practices.md)

## <a name="licensing"></a>Licensing

### <a name="how-do-i-purchase-power-bi-embedded"></a>Comment acheter Power BI Embedded ?

Power BI Embedded est disponible via Azure.

### <a name="what-happens-if-i-already-purchased-power-bi-premium-and-now-i-want-some-power-bi-embedded-in-azure-benefits"></a>Que se passe-t-il si j’ai déjà acheté Power BI Premium et maintenant je veux que certains Power BI Embedded dans avantages Azure ?

Les clients continuent à payer pour tous les achats Power BI Premium existants jusqu'à la fin de leur contrat actuel et, à ce stade, pourront ensuite basculer leurs achats Power BI Premium en fonction des besoins.

### <a name="do-i-still-have-to-buy-power-bi-premium-to-get-access-to-power-bi-embedded"></a>Dois-je toujours acheter Power BI Premium pour accéder à Power BI Embedded ?

Non. Power BI Embedded inclut la capacité basée sur Azure dont vous avez besoin pour déployer et distribuer votre solution aux clients.

### <a name="whats-the-purchase-commitment-for-power-bi-embedded"></a>Quel est la durée d’engagement pour Power BI Embedded ?

Les clients peuvent modifier leur utilisation sur une base horaire. Il n’existe aucun engagement mensuel ou annuel pour le service Power BI Embedded.

### <a name="how-does-the-usage-of-power-bi-embedded-show-up-on-my-bill"></a>Comment s’affiche l’utilisation de Power BI Embedded sur ma facture ?

Power BI Embedded est facturé à un tarif horaire prévisible basé sur le type de nœuds déployé. Vous êtes facturé tant que votre ressource est active, même s’il n’existe aucune utilisation. Vous devez suspendre votre ressource pour arrêter la facturation.

### <a name="who-needs-a-power-bi-pro-license-for-power-bi-embedded-and-why"></a>Qui a besoin d’une licence Power BI Pro pour Power BI Embedded et pourquoi ?

Vous devez posséder une licence Power BI Pro ou [principal du service](embed-service-principal.md) à utiliser l’API REST. Pour ajouter des rapports à un espace de travail Power BI, un analyste doit une licence Power BI Pro ou un service principal. Pour gérer le locataire Power BI et la capacité, un administrateur est requis ont une licence Power BI Pro.

Étant donné que Power BI Embedded autorise l’utilisation de portail Power BI pour la gestion et la validation du contenu intégré, la licence Power BI Pro est nécessaire pour authentifier l’application à l’intérieur de PowerBI.com pour accéder aux rapports dans les dépôts appropriés.

Cependant, pour [créer/modifier des rapports incorporés](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Create-Report-in-Embed-View) au sein de votre application, l’utilisateur final n’a pas besoin d’une licence Pro, car il n’a pas besoin d’être un utilisateur Power BI.

### <a name="can-i-get-started-for-free"></a>Puis-je commencer gratuitement ?

Oui, vous pouvez utiliser vos [crédits Azure](https://azure.microsoft.com/free/) pour Power BI Embedded.

### <a name="can-i-get-a-trial-experience-for-power-bi-embedded-in-azure"></a>Puis-je me procurer un essai de Power BI Embedded dans Azure ?

Étant donné que Power BI Embedded fait partie d’Azure, il est possible d’utiliser le service avec le [crédit de 200 $ reçu lors de l’inscription pour Azure](https://azure.microsoft.com/free/).

### <a name="is-power-bi-embedded-available-for-national-clouds-us-government-germany-china"></a>Power BI Embedded est-il disponible pour les clouds nationaux (gouvernement américain, Allemagne, Chine) ?

Power BI Embedded est également disponible pour [clouds nationaux](embed-sample-for-customers-national-clouds.md).

### <a name="is-power-bi-embedded-available-for-non-profits-and-educational"></a>Power BI Embedded est-il disponible pour les organisations à but non lucratif et les établissements d’enseignement ?

Il n’existe aucun spéciale la tarification Azure pour les entités à but non lucratif et d’enseignement.

## <a name="power-bi-workspace-collection"></a>Collection d’espaces de travail Power BI

### <a name="what-is-power-bi-workspace-collection"></a>Présentation de la collection d’espaces de travail Power BI

**Power BI Workspace collections** (**Power BI Embedded** Version 1) est une solution basée sur le **Power BI Workspace collections** ressources Azure. Cette solution permet de créer des applications **Power BI Embedded** pour les clients avec du contenu Power BI sous la solution **Collection d’espaces de travail Power BI**, des API dédiées et des clés de collection d’espaces de travail permettant d’authentifier l’application sur Power BI.

### <a name="can-i-migrate-from-power-bi-workspace-collection-to-power-bi-embedded"></a>Peut-on migrer d’une collection d’espaces de travail Power BI vers Power BI Embedded ?

1. Vous pouvez utiliser l’outil de migration pour cloner le contenu de la **collection d’espaces de travail Power BI** dans Power BI : https://docs.microsoft.com/power-bi/developer/migrate-from-powerbi-embedded#content-migration.

2. Commencez par la preuve de concept d’application **Power BI Embedded** qui utilise le contenu Power BI.

3. Au moment de passer en production, achetez une capacité dédiée **Power BI Embedded** et affectez-y votre contenu Power BI (espace de travail).

    > [!Note]
    > Vous pouvez continuer à utiliser la **collection d’espaces de travail Power BI** tout en travaillant en parallèle avec une solution **Power BI Embedded**. Quand vous êtes prêt, vous pouvez déplacer votre client vers la nouvelle solution **Power BI Embedded** et mettre hors service la solution **Collection d’espaces de travail Power BI**.

Pour plus d’informations, voir [Guide pratique pour migrer le contenu d’une collection d’espaces de travail Power BI Embedded vers Power BI Embedded](https://docs.microsoft.com/power-bi/developer/migrate-from-powerbi-embedded).

### <a name="is-power-bi-workspace-collection-on-a-deprecation-path"></a>Est Power BI Workspace Collections sur un chemin d’accès de désapprobation ?

Oui, mais les clients qui utilisent déjà le **Power BI Workspace collections** solution peut continuer à l’utiliser jusqu'à ce que la désapprobation. Ils peuvent également créer de nouvelles collections d’espaces de travail et des applications **Power BI Embedded** qui utilisent encore la solution **Collection d’espaces de travail Power BI**.

Toutefois, cela signifie également que les nouvelles fonctionnalités ne sont pas ajoutées aux **Power BI Workspace collections** solutions. Nous encourageons les clients à planifier leur migration vers le nouveau **Power BI Embedded** solution.

### <a name="when-is-power-bi-workspace-collection-support-discontinued"></a>Quand se termine la prise en charge de la collection d’espaces de travail Power BI ?

Les clients qui utilisent déjà la solution **Collection d’espaces de travail Power BI** pourront continuer à s’en servir jusqu’à la fin du mois de juin 2018 ou de leur contrat de support.

### <a name="in-what-regions-can-i-create-a-pbi-workspace-collection"></a>Dans quelles régions puis-je créer une Collection d’espace de travail PBI ?

Les régions disponibles sont les suivantes : Canada Centre, États-Unis de l’Ouest, États-Unis de l’Est 2, Europe de l’Ouest, Europe du Nord, Inde de l’Ouest, Japon de l’Est, Nord du centre des États-Unis, Royaume-Uni Sud, Sud du Brésil, Sud du centre des États-Unis, Sud-Est asiatique et Sud-Est de l’Australie.

### <a name="why-should-i-migrate-from-pbi-workspace-collection-to-power-bi-embedded"></a>Pourquoi migrer d’une collection d’espaces de travail PBI vers Power BI Embedded ?

Il existe quelques nouvelles **Power BI Embedded** fonctionnalités de la solution et les fonctionnalités que vous ne pouvez pas faire avec **Power BI Workspace collections**.

En voici quelques exemples :
* Toutes les sources de données PBI sont pris en charge. Seuls deux **Power BI Workspace collections** des sources de données sont pris en charge. 
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
