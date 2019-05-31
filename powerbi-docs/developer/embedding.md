---
title: Analytique intégrée avec Power BI
description: Power BI offre des API pour utiliser l’analytique incorporée pour vos tableaux de bord et vos rapports dans des applications. Découvrez plus en détail l’incorporation avec Power BI à la fois dans un environnement PaaS et un environnement SaaS à l’aide de logiciels d’analytique intégrés, d’outils d’analytique intégrés ou d’outils d’analyse décisionnelle intégrés.
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: overview
helpviewer_keywords:
- embedded analytics
- embedding
- Power BI embedding
- app owns data
- user owns data
- Power BI APIs
ms.custom: seodec18
ms.date: 05/15/2019
ms.openlocfilehash: a212691f2af877e3b86e021a4f48644f4fa6e8e3
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66051060"
---
# <a name="embedded-analytics-with-power-bi"></a>Analytique intégrée avec Power BI

Le service Power BI (SaaS) et le service Power BI Embedded dans Azure (PaaS) comportent des API permettant d’incorporer des tableaux de bord et des rapports. Lors de l’incorporation de contenu, cela vous donne accès aux dernières fonctionnalités de Power BI telles que des tableaux de bord, les passerelles et les espaces de travail d’application.

Vous pouvez passer par l’[outil de configuration de l’incorporation](https://aka.ms/embedsetup) pour démarrer et télécharger rapidement un exemple d’application.

Choisissez la solution qui vous convient :

* [L’incorporation pour votre organisation](embedding.md#embedding-for-your-organization) vous permet d’étendre le service Power BI. Pour ce faire, vous devez implémenter le [incorporation pour votre organisation](https://aka.ms/embedsetup/UserOwnsData) solution.
* [Incorporation pour vos clients](embedding.md#embedding-for-your-customers) vous permet d’incorporer des tableaux de bord et rapports pour les utilisateurs qui n’ont pas un compte Power BI. Pour ce faire, vous devez implémenter le [incorporation pour vos clients](https://aka.ms/embedsetup/AppOwnsData) solution.

![Exemple PBIE](media/what-can-you-do/what-can-you-do-02.png)

## <a name="use-apis"></a>Utilisez des API

Il existe deux principaux scénarios pour l’incorporation de contenu Power BI :
- Incorporation pour les utilisateurs de votre organisation (disposant de licences Power BI). 
 
- Incorporation pour vos utilisateurs et les clients n’ont pas besoin de licences Power BI. 

Le [API REST Power BI](https://docs.microsoft.com/rest/api/power-bi/) aux deux scénarios.

Pour les clients et utilisateurs sans licence Power BI, vous pouvez incorporer des tableaux de bord et des rapports dans votre application personnalisée, en utilisant la même API pour votre organisation ou vos clients. Vos clients voient les données gérées par l’application. En outre, les utilisateurs de Power BI de votre organisation ont des options supplémentaires permettant d’afficher *leurs données* directement dans Power BI ou dans le contexte de l’application incorporée. Vous pouvez tirer pleinement parti des API JavaScript et REST pour vos besoins d’incorporation.

Pour comprendre le fonctionne de l’incorporation, consultez le [exemple d’incorporation JavaScript](https://microsoft.github.io/PowerBI-JavaScript/demo/).

## <a name="embedding-for-your-organization"></a>Incorporation pour votre organisation

**L’incorporation pour votre organisation** vous permet d’étendre le service Power BI. Cette incorporation requiert l’authentification des utilisateurs de votre application dans le service Power BI pour afficher le contenu. Une fois qu’un utilisateur de votre organisation est connecté, il a accès seulement aux tableaux de bord et aux rapports dont il est propriétaire, ou que quelqu’un a partagés avec lui dans le service Power BI.

Exemples incorporation d’organisation incluent des applications internes comme [SharePoint Online](https://powerbi.microsoft.com/blog/integrate-power-bi-reports-in-sharepoint-online/), [intégration Microsoft Teams (vous devez disposer de droits d’administrateur)](https://powerbi.microsoft.com/blog/power-bi-teams-up-with-microsoft-teams/), et [Microsoft Dynamics](https://docs.microsoft.com/dynamics365/customer-engagement/basics/add-edit-power-bi-visualizations-dashboard).

Pour incorporer pour votre organisation, consultez [didacticiel : Incorporer du contenu de Power BI dans une application pour votre organisation](embed-sample-for-your-organization.md).

Les fonctionnalités en libre-service, telles que la modification ou l’enregistrement, sont disponibles par le bais de [l’API JavaScript](https://github.com/Microsoft/PowerBI-JavaScript) lors de l’incorporation relative aux utilisateurs Power BI.

Vous pouvez parcourir le [outil de configuration d’incorporation](https://aka.ms/embedsetup/UserOwnsData) mise en route et télécharger un exemple d’application qui vous guide à travers l’intégration d’un rapport pour votre organisation.

## <a name="embedding-for-your-customers"></a>Incorporation pour vos clients

**Incorporation pour vos clients** vous permet d’incorporer des tableaux de bord et rapports pour les utilisateurs qui n’ont pas un compte Power BI. Cette incorporation est également appelé *Power BI Embedded*.

[Power BI Embedded](azure-pbie-what-is-power-bi-embedded.md) est un **Microsoft Azure** service qui permet de rapidement les éditeurs de logiciels indépendants (ISV) et les développeurs incorporer des visuels, rapports et tableaux de bord dans une application. Cette incorporation s’effectue via un modèle limitée selon la capacité, toutes les heures.

![Flux relatif à l’incorporation de vos clients](media/embedding/powerbi-embed-flow.png)

Power BI Embedded présente des avantages pour les éditeurs ISV, leurs développeurs et leurs clients. Par exemple, ils peuvent commencer à créer des visuels gratuitement avec Power BI Desktop. En réduisant les efforts de développement d’analyse visuelle, les éditeurs de logiciels atteindre la vitesse de mise sur le marché et démarquer de ses concurrents avec des expériences de gestion des données différenciées. Éditeurs de logiciels indépendants peuvent également choisir de paiement de frais pour la valeur supplémentaire qu’ils créent avec analytique incorporée.

Avec Power BI Embedded, vos clients n’ont pas à se soucier de Power BI. Vous pouvez utiliser deux méthodes différentes pour créer une application intégrée :
- Compte de Power BI Pro 
- Principal du service 

Le compte Power BI Pro agit en tant que compte principal de votre application (pensez de celui-ci en tant que proxy compte). Ce compte vous permet de générer les jetons qui donnent accès aux tableaux de bord Power BI et les rapports de votre application d’incorporation.

Un [principal du service](embed-service-principal.md) peut incorporer du contenu Power BI dans une application en utilisant un jeton **application uniquement**. Il vous permet également de générer les jetons qui donnent accès aux tableaux de bord Power BI et les rapports de votre application d’incorporation.

Les développeurs à l’aide de Power BI Embedded peuvent consacrer du temps sur la création de leurs applications principales fonctionnalités plutôt que dépense développer des éléments visuels sur la durée et analytique. Ils peuvent rapidement répondre aux demandes des clients rapport et tableau de bord et incorporer aisément des API entièrement documenté et kits de développement logiciel. En facilitant l’exploration de données dans les applications, les éditeurs indépendants de logiciels permettent aux clients de prendre des décisions rapides en fonction des données et du contexte, sur n’importe quel appareil.

> [!IMPORTANT]
> Lors de l’incorporation nécessite le service Power BI, vos clients n’avez pas besoin de disposer d’un compte Power BI pour afficher le contenu incorporé de votre application. 

Quand vous êtes prêt à passer en mode de production, vous devez affecter une capacité dédiée à votre espace de travail d’application. Power BI Embedded dans Microsoft Azure offre des [capacités dédiées](azure-pbie-create-capacity.md) à utiliser avec vos applications.

Pour l’incorporation d’informations, consultez [comment incorporer du contenu Power BI](embed-sample-for-customers.md).

## <a name="next-steps"></a>Étapes suivantes

Vous pouvez maintenant essayer incorporer du contenu de Power BI dans une application, ou essayer d’incorporer du contenu de Power BI pour vos clients.

> [!div class="nextstepaction"]
> [Incorporer pour votre organisation](embed-sample-for-your-organization.md)

> [!div class="nextstepaction"]
> [Qu’est-ce que Power BI Embedded ?](azure-pbie-what-is-power-bi-embedded.md)

> [!div class="nextstepaction"]
>[Incorporer pour vos clients](embed-sample-for-customers.md)

D’autres questions ? [Essayez d’interroger la communauté Power BI](http://community.powerbi.com/)
