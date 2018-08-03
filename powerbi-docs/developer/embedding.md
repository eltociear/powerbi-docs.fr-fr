---
title: Incorporation avec Power BI
description: Power BI fournit des API pour l’incorporation de vos tableaux de bord et rapports dans des applications.
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-developer
ms.topic: overview
ms.date: 07/31/2018
ms.author: maghan
ms.openlocfilehash: 8f200450e5359124ffcc3447c68c6bd755c57896
ms.sourcegitcommit: fecea174721d0eb4e1927c1116d2604a822e4090
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2018
ms.locfileid: "39359860"
---
# <a name="embedding-with-power-bi"></a>Incorporation avec Power BI
Le service Power BI (SaaS) et le service Power BI Embedded dans Azure (PaaS) comportent des API permettant d’incorporer des tableaux de bord et des rapports. Vous avez donc accès aux dernières fonctionnalités de Power BI (tableaux de bord, passerelles et espaces de travail d’application, par exemple) pour incorporer votre contenu.

Vous pouvez passer par [l’outil d’expérience d’intégration](https://aka.ms/embedsetup) pour démarrer et télécharger rapidement un exemple d’application.

Choisissez la solution qui vous convient :

* [L’incorporation pour votre organisation](embedding.md#embedding-for-your-organization) vous permet d’étendre le service Power BI. Exécutez la solution [Incorporer pour votre organisation](https://aka.ms/embedsetup/UserOwnsData).
* [L’incorporation pour vos clients](embedding.md#embedding-for-your-customers) permet d’incorporer des tableaux de bord et des rapports pour les utilisateurs qui n’ont pas de compte Power BI. Exécutez la solution [Incorporer pour vos clients](https://aka.ms/embedsetup/AppOwnsData).

![Exemple PBIE](media/what-can-you-do/what-can-you-do-02.png)

## <a name="using-apis"></a>Avec des API
Les deux principaux scénarios d’incorporation de contenu Power BI sont les suivants :  Incorporation pour les utilisateurs de votre organisation (disposant de licences Power BI) et incorporation pour les utilisateurs et les clients sans que ceux-ci aient besoin de licences Power BI. L’API REST Power BI est adaptée aux deux scénarios.

Pour les clients et utilisateurs sans licence Power BI, vous pouvez incorporer des tableaux de bord et des rapports dans votre application personnalisée, en utilisant la même API pour votre organisation ou vos clients. Vos clients voient les données qui sont gérées par l’application. Les utilisateurs de Power BI de votre organisation, quant à eux, disposent des options supplémentaires pour afficher *leurs données* directement dans Power BI ou dans le contexte de l’application incorporée. Vous pouvez tirer pleinement parti des API JavaScript et REST pour vos besoins d’incorporation.

Reportez-vous à [Exemple de JavaScript incorporé](https://microsoft.github.io/PowerBI-JavaScript/demo/) pour consulter un exemple d’incorporation.

## <a name="embedding-for-your-organization"></a>Incorporation pour votre organisation
**L’incorporation pour votre organisation** vous permet d’étendre le service Power BI. Pour voir son contenu, l’utilisateur de votre application doit se connecter au service Power BI. Une fois qu’un utilisateur de votre organisation est connecté, il a uniquement accès aux tableaux de bord et rapports dont il est propriétaire ou qui ont été partagés avec lui dans le service Power BI.

*Une application web interne, le composant WebPart SharePoint Online et l’intégration de Microsoft Teams [sont des exemples d’incorporation pour votre organisation (vous devez disposer de droits d’administrateur)](https://powerbi.microsoft.com/en-us/blog/power-bi-teams-up-with-microsoft-teams/).*

Pour l’incorporation s’adressant à votre organisation, consultez les procédures suivantes :

* [Intégrer un rapport à une application](embed-sample-for-your-organization.md)

Les fonctionnalités en libre-service, telles que la modification ou l’enregistrement, sont disponibles par le bais de l’[API JavaScript](https://github.com/Microsoft/PowerBI-JavaScript) lors de l’incorporation relative aux utilisateurs Power BI.

Vous pouvez accéder à [l’outil d’expérience d’intégration permettant d’incorporer pour votre organisation](https://aka.ms/embedsetup/UserOwnsData) pour démarrer rapidement et télécharger un exemple d’application qui vous guide dans l’intégration d’un rapport pour votre organisation.

## <a name="embedding-for-your-customers"></a>Incorporation pour vos clients

**L’incorporation pour vos clients** permet d’incorporer des tableaux de bord et des rapports pour les utilisateurs qui n’ont pas de compte Power BI. Vos clients n’ont pas à se soucier de Power BI. Au moins un compte Power BI Pro est nécessaire pour créer une application incorporée. Ce compte sert de compte principal pour votre application. Considérez-le comme un compte proxy. Ce compte Power BI Pro vous permet également de générer les jetons d’incorporation qui offrent un accès aux tableaux de bord et rapports au sein du service Power BI qui sont gérés ou possédés par votre application.

[Power BI Embedded](azure-pbie-what-is-power-bi-embedded.md) offre aux éditeurs de logiciels indépendants (ISV) et aux développeurs la possibilité d’incorporer pour les clients afin d’ajouter rapidement des visuels, des rapports et des tableaux de bord dans les applications via un modèle basé sur les capacités et facturé à l’heure.

![Flux relatif à l’incorporation de vos clients](media/embedding/powerbi-embed-flow.png)

Power BI Embedded présente des avantages pour les éditeurs ISV, leurs développeurs et leurs clients. Par exemple, ils peuvent commencer à créer des visuels gratuitement avec Power BI Desktop. Les éditeurs ISV peuvent réaliser une mise sur le marché plus rapide en réduisant au minimum leurs efforts de développement analytique de visuels et se démarquer de la concurrence avec des expériences avec les données qui font la différence. Ils peuvent aussi choisir de facturer un supplément pour la valeur ajoutée créée avec l’analytique incorporée.

Les développeurs peuvent consacrer du temps à la fonction première de leur application plutôt que de le dépenser à développer des visuels et une analytique. Les développeurs peuvent rapidement répondre aux demandes de rapport et de tableau de bord des clients et incorporer facilement des kits SDK et des API entièrement documentés. Enfin, en facilitant l’exploration de données dans leurs applications, les éditeurs ISV permettent à leurs clients de prendre des décisions rapides en fonction des données et du contexte en toute confiance sur n’importe quel appareil.

> [!IMPORTANT]
> Même si l’incorporation dépend du service Power BI, vos clients ne dépendent pas de Power BI. Ils n’ont pas besoin de s’inscrire à Power BI pour afficher le contenu incorporé dans votre application.

Lorsque vous êtes prêt à passer en mode de production, vous devez attribuer l’espace de travail de votre application à une capacité dédiée. Power BI Embedded, au sein de Microsoft Azure, offre des capacités dédiées à utiliser avec vos applications.

Pour plus d’informations sur l’incorporation, consultez [Comment incorporer vos tableaux de bord, rapports et vignettes Power BI](embed-sample-for-customers.md).

Vous pouvez accéder à [l’outil d’expérience d’intégration](https://aka.ms/embedsetup/AppOwnsData) pour démarrer rapidement et télécharger un exemple d’application qui vous guide dans l’intégration d’un rapport dans votre application.

Si vous utilisiez le service Collection d’espaces de travail Power BI au sein d’Azure, pour plus d’informations sur la façon de migrer votre contenu, consultez [Migrer le contenu du service Azure Collection d’espaces de travail Power BI](migrate-from-powerbi-embedded.md).

## <a name="next-steps"></a>Étapes suivantes
Vous pouvez maintenant essayer incorporer du contenu de Power BI dans une application, ou essayer d’incorporer du contenu de Power BI pour vos clients.

> [!div class="nextstepaction"]
> [Qu’est-ce que Power BI Embedded ?](azure-pbie-what-is-power-bi-embedded.md)

> [!div class="nextstepaction"]
> [Incorporer pour votre organisation](embed-sample-for-your-organization.md)

> [!div class="nextstepaction"]
>[Incorporer pour vos clients](embed-sample-for-customers.md)

D’autres questions ? [Essayez d’interroger la communauté Power BI](http://community.powerbi.com/)