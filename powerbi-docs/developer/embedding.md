---
title: Analytique intégrée avec Power BI
description: Power BI offre des API pour utiliser l’analytique incorporée pour vos tableaux de bord et vos rapports dans des applications. En savoir plus sur l’incorporation avec Power BI à la fois dans un environnement PaaS et un environnement SaaS à l’aide de logiciels d’analytique intégrés, d’outils d’analytique intégrés ou d’outils d’analyse décisionnelle intégrés.
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: overview
ms.custom: seodec18
ms.date: 02/05/2019
ms.openlocfilehash: ca159fb8cea26f4c707aabc99d9fa2c308a32e1a
ms.sourcegitcommit: 0abcbc7898463adfa6e50b348747256c4b94e360
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/06/2019
ms.locfileid: "55762441"
---
# <a name="embedded-analytics-with-power-bi"></a>Analytique intégrée avec Power BI

Le service Power BI (SaaS) et le service Power BI Embedded dans Azure (PaaS) comportent des API permettant d’incorporer des tableaux de bord et des rapports. Cette fonctionnalité signifie que vous avez un ensemble de fonctions et que vous accédez aux dernières fonctionnalités de Power BI (tableaux de bord, passerelles et espaces de travail d’application, par exemple) pour incorporer votre contenu.

Vous pouvez passer par l’[outil de configuration de l’incorporation](https://aka.ms/embedsetup) pour démarrer et télécharger rapidement un exemple d’application.

Choisissez la solution qui vous convient :

* [L’incorporation pour votre organisation](embedding.md#embedding-for-your-organization) vous permet d’étendre le service Power BI. Exécutez la solution [Incorporer pour votre organisation](https://aka.ms/embedsetup/UserOwnsData).
* [L’incorporation pour vos clients](embedding.md#embedding-for-your-customers) permet d’incorporer des tableaux de bord et des rapports pour les utilisateurs qui n’ont pas de compte Power BI. Exécutez la solution [Incorporer pour vos clients](https://aka.ms/embedsetup/AppOwnsData).

![Exemple PBIE](media/what-can-you-do/what-can-you-do-02.png)

## <a name="using-apis"></a>Avec des API

Les deux principaux scénarios d’incorporation de contenu Power BI sont les suivants : Incorporation pour les utilisateurs de votre organisation (disposant de licences Power BI), et incorporation pour les utilisateurs et les clients sans que ceux-ci aient besoin de licences Power BI. L’API REST Power BI est adaptée aux deux scénarios.

Pour les clients et utilisateurs sans licence Power BI, vous pouvez incorporer des tableaux de bord et des rapports dans votre application personnalisée, en utilisant la même API pour votre organisation ou vos clients. Vos clients voient les données qui sont gérées par l’application. Les utilisateurs de Power BI de votre organisation disposent quant à eux d’options supplémentaires pour afficher *leurs données* directement dans Power BI ou dans le contexte de l’application incorporée. Vous pouvez tirer pleinement parti des API JavaScript et REST pour vos besoins d’incorporation.

Reportez-vous à [Exemple de JavaScript incorporé](https://microsoft.github.io/PowerBI-JavaScript/demo/) pour consulter un exemple d’incorporation.

## <a name="embedding-for-your-organization"></a>Incorporation pour votre organisation

**L’incorporation pour votre organisation** vous permet d’étendre le service Power BI. L’incorporation pour votre organisation nécessite que les utilisateurs de votre application se connectent au service Power BI quand ils veulent voir le contenu. Une fois qu’un utilisateur de votre organisation est connecté, il a accès seulement aux tableaux de bord et aux rapports dont il est propriétaire, ou que quelqu’un a partagés avec lui dans le service Power BI.

*Des applications internes comme [SharePoint Online](https://powerbi.microsoft.com/blog/integrate-power-bi-reports-in-sharepoint-online/), [l’intégration de Microsoft Teams (vous devez disposer de droits d’administrateur)](https://powerbi.microsoft.com/blog/power-bi-teams-up-with-microsoft-teams/) et [Microsoft Dynamics](https://docs.microsoft.com/dynamics365/customer-engagement/basics/add-edit-power-bi-visualizations-dashboard) sont des exemples d’incorporation pour votre organisation.*

Pour l’incorporation s’adressant à votre organisation, consultez les procédures suivantes :

* [Intégrer un rapport à une application](embed-sample-for-your-organization.md)

Les fonctionnalités en libre-service, telles que la modification ou l’enregistrement, sont disponibles par le bais de [l’API JavaScript](https://github.com/Microsoft/PowerBI-JavaScript) lors de l’incorporation relative aux utilisateurs Power BI.

Vous pouvez accéder à [l’outil de configuration de l’incorporation](https://aka.ms/embedsetup/UserOwnsData) pour démarrer rapidement et télécharger un exemple d’application qui vous guide dans l’intégration d’un rapport pour votre organisation.

## <a name="embedding-for-your-customers"></a>Incorporation pour vos clients

**L’incorporation pour vos clients** vous permet d’incorporer des tableaux de bord et des rapports pour des utilisateurs qui n’ont pas de compte Power BI. L’incorporation pour vos clients est également appelée **Power BI Embedded**.

[Power BI Embedded](azure-pbie-what-is-power-bi-embedded.md) est un service **Microsoft Azure** qui offre aux éditeurs de logiciels indépendants et aux développeurs la possibilité d’incorporer rapidement des visuels, des rapports et des tableaux de bord dans une application via un modèle basé sur les capacités et facturé à l’heure.

![Flux relatif à l’incorporation de vos clients](media/embedding/powerbi-embed-flow.png)

Power BI Embedded présente des avantages pour les éditeurs ISV, leurs développeurs et leurs clients. Par exemple, ils peuvent commencer à créer des visuels gratuitement avec Power BI Desktop. Les éditeurs ISV peuvent réaliser une mise sur le marché plus rapide en réduisant au minimum leurs efforts de développement analytique de visuels et se démarquer de la concurrence avec des expériences avec les données qui font la différence. Ils peuvent aussi choisir de facturer un supplément pour la valeur ajoutée créée avec l’analytique incorporée.

Avec Power BI Embedded, vos clients n’ont pas à se soucier de Power BI. Vous pouvez utiliser deux méthodes différentes pour créer une application incorporée. Une option consiste à utiliser un compte Power BI Pro. Une autre option consiste à utiliser un principal du service. 

Ce compte sert de compte principal pour votre application (vous pouvez considérer qu’il s’agit d’un compte proxy). Ce compte Power BI Pro vous permet de générer les jetons d’incorporation qui donnent accès aux tableaux de bord et aux rapports au sein du service Power BI, et qui sont la propriété de votre application et gérés par elle.

Un [principal du service](embed-service-principal.md) peut incorporer du contenu Power BI dans une application en utilisant un jeton **application uniquement**. Un principal du service vous permet de générer des jetons d’incorporation qui donnent accès aux tableaux de bord et aux rapports au sein du service Power BI, et qui sont la propriété de votre application et gérés par elle.

Les développeurs utilisant Power BI Embedded peuvent consacrer du temps à la fonction première de leur application, au lieu de le passer à développer des visuels et de l’analytique. Les développeurs peuvent rapidement répondre aux demandes de rapport et de tableau de bord des clients et incorporer facilement des kits SDK et des API entièrement documentés. En facilitant l’exploration de données dans les applications, les éditeurs indépendants de logiciels permettent aux clients de prendre des décisions rapides en fonction des données et du contexte, sur n’importe quel appareil.

> [!IMPORTANT]
> Même si l’incorporation dépend du service Power BI, vos clients ne dépendent pas de Power BI. Ils n’ont pas besoin de s’inscrire à Power BI pour afficher le contenu incorporé dans votre application.

Quand vous êtes prêt à passer en mode de production, vous devez affecter une capacité dédiée à votre espace de travail d’application. Power BI Embedded dans Microsoft Azure offre des [capacités dédiées](azure-pbie-create-capacity.md) à utiliser avec vos applications.

Pour plus d’informations sur l’incorporation, consultez [Guide pratique pour incorporer du contenu Power BI](embed-sample-for-customers.md).

## <a name="next-steps"></a>Étapes suivantes

Vous pouvez maintenant essayer incorporer du contenu de Power BI dans une application, ou essayer d’incorporer du contenu de Power BI pour vos clients.

> [!div class="nextstepaction"]
> [Incorporer pour votre organisation](embed-sample-for-your-organization.md)

> [!div class="nextstepaction"]
> [Qu’est-ce que Power BI Embedded ?](azure-pbie-what-is-power-bi-embedded.md)

> [!div class="nextstepaction"]
>[Incorporer pour vos clients](embed-sample-for-customers.md)

D’autres questions ? [Essayez d’interroger la communauté Power BI](http://community.powerbi.com/)