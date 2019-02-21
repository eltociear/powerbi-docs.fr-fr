---
title: Créer des applications modèles dans Power BI (préversion)
description: Découvrez comment créer des applications modèles dans Power BI que vous pourrez ensuite distribuer à vos clients Power BI.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 02/04/2019
ms.author: maggies
ms.openlocfilehash: c08b7e60777b720aa4fc2489b02c212bdd3e7169
ms.sourcegitcommit: 8207c9269363f0945d8d0332b81f1e78dc2414b0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2019
ms.locfileid: "56249658"
---
# <a name="create-a-template-app-in-power-bi-preview"></a>Créer une application modèle dans Power BI (préversion)

Les nouvelles *applications modèles* Power BI permettent aux partenaires Power BI de créer des applications Power BI avec peu ou pas de codage et de les déployer ensuite vers n’importe quel client Power BI.  Cet article contient des instructions pas à pas pour créer une application modèle Power BI. 

Si vous créez déjà des rapports et tableaux de bord Power BI, vous pouvez devenir *concepteur d’applications modèles* pour créer vous-même du contenu analytique et l’intégrer dans une *application*. Vous pouvez ensuite déployer votre application vers d’autres locataires Power BI par le biais de n’importe quelle plateforme disponible, comme AppSource, ou en l’utilisant dans votre propre service web. En tant que concepteur, vous pouvez créer un package analytique protégé pour la distribution. 

Les administrateurs de locataires Power BI régissent et contrôlent les utilisateurs dans leur organisation qui sont autorisés à créer des applications modèles et/ou à les installer. Les utilisateurs autorisés peuvent installer votre application modèle, puis la modifier et la distribuer aux consommateurs Power BI dans leur organisation.

## <a name="prerequisites"></a>Prérequis 

Les prérequis pour créer une application modèle sont les suivants :  

- Une [licence Power BI Pro](service-self-service-signup-for-power-bi.md)
- Une [installation de Power BI Desktop](desktop-get-the-desktop.md) (facultatif)
- Une bonne connaissance des [concepts de base de Power BI ](service-basic-concepts.md)
- Les autorisations de création d’application modèle. Pour plus d’informations, consultez [Paramètres des applications modèles dans le portail d’administration](service-admin-portal.md#template-apps-settings-preview) Power BI.

## <a name="enable-app-developer-mode"></a>Activer le mode développeur d’applications

Pour créer une application modèle que vous pourrez ensuite distribuer à d’autres locataires Power BI, vous devez être en mode développeur d’applications. Sinon, l’application que vous créez pourra uniquement être utilisée par les consommateurs Power BI appartenant à votre organisation.
 
1. Ouvrez le service Power BI dans un navigateur.
2. Accédez à **Paramètres** > **Général** > **Développeur** > **Activer le mode de développement d’applications modèles**.

    ![Activer les applications modèles](media/service-template-apps-create/power-bi-dev-template-app.png)

    Si vous ne voyez pas cette option, demandez à votre administrateur Power BI qu’il vous accorde les [autorisations de développement d’applications modèles](service-admin-portal.md#template-apps-settings-preview) dans le portail d’administration.

3. Sélectionnez **Appliquer**.

## <a name="create-the-template-app-workspace"></a>Créer l’espace de travail de l’application modèle

Pour créer une application modèle que vous pourrez ensuite distribuer à d’autres locataires Power BI, vous devez la créer dans l’un des nouveaux espaces de travail d’application. 
 
1. Dans le service Power BI, sélectionnez **Espaces de travail** > **Créer un espace de travail d’application**. 
 
    ![Créer un espace de travail d’application](media/service-template-apps-create/power-bi-new-workspace.png)

3. Dans **Créer un espace de travail d’application**, dans **Afficher un aperçu des espaces de travail améliorés**, sélectionnez **Essayer maintenant**.

    ![Essayer les nouveaux espaces de travail](media/service-template-apps-create/power-bi-try-now-new-workspace.png)

5. Entrez un nom, une description (facultative) et un logo (facultatif) pour votre espace de travail d’application.

4. Sélectionnez **Développer une application modèle**.

    ![Développer une application modèle](media/service-template-apps-create/power-bi-template-app-develop.png)

5. Sélectionnez **Enregistrer**.

## <a name="create-the-content-in-your-template-app"></a>Créer le contenu dans votre application modèle

Comme avec tout espace de travail d’application Power BI standard, l’étape suivante consiste à créer le contenu dans l’espace de travail.  Dans cette préversion des applications modèles, vous pouvez créer un seul jeu de données, un seul rapport et un seul tableau de bord.

- [Créez votre contenu Power BI](power-bi-creator-landing.md) dans votre espace de travail d’application.

Si vous définissez des paramètres dans Power Query, assurez-vous d’utiliser des types de paramètre pris en charge (par exemple, Text). Les types Any et Binary ne sont pas pris en charge. 

L’article [Conseils pour créer des applications modèles dans Power BI (préversion)](service-template-apps-tips.md) liste les différents points à prendre en considération quand vous créez des rapports et des tableaux de bord pour votre application modèle.

## <a name="create-the-test-template-app"></a>Créer l’application modèle de test

Maintenant que vous avez ajouté du contenu dans votre espace de travail, vous êtes prêt à l’intégrer dans une application modèle. La première étape consiste à créer une application modèle de test, accessible uniquement au sein de votre organisation sur votre locataire.

1. Dans l’espace de travail d’application modèle, sélectionnez **Créer une application**. 

    ![Créer une application](media/service-template-apps-create/power-bi-create-app.png)
 
    Ici, vous renseignez d’autres paramètres pour votre application modèle, répartis en quatre catégories. 

    **Personnalisation**

    - Nom de l’application 
    - Description
    - Logo de l’application (facultatif)
    - Couleur de l’application 

    **Contenu** 

    - Page d’accueil de l’application (facultatif) : définissez le rapport ou le tableau de bord à utiliser comme page d’accueil de votre application.  
    
    **Contrôle** 

    Définissez les différentes limitations et restrictions d’usage du contenu de votre application par les utilisateurs. Ce contrôle vous permet de protéger les éventuels droits de propriété intellectuelle existants dans votre application.

    **Accès**

    - Dans la phase de test, déterminez quels utilisateurs dans votre organisation sont autorisés à installer et à tester votre application.

    Ne vous inquiétez pas, vous pouvez modifier tous ces paramètres à tout moment.  

2. Sélectionnez **Créer une application**. 

    Vous voyez un message indiquant que l’application de test est prête, ainsi qu’un lien à copier et à partager avec les testeurs de votre application.

    ![L’application de test est prête](media/service-template-apps-create/power-bi-template-app-test-ready.png)

    Vous avez également terminé la première étape du processus de gestion des mises en production, comme expliqué ci-dessous.

    

## <a name="manage-the-template-app-release"></a>Gérer la mise en production de l’application modèle

Avant de mettre votre nouvelle application modèle à la disposition de tous, vous devez vous assurer qu’elle est prête à l’emploi. À partir du volet Gestion des mises en production dans Power BI, vous pouvez suivre et inspecter tout le chemin de mise en production de l’application. Vous pouvez également déclencher la transition entre chaque phase. Voici les phases principales : 

- Générer l’application de test : test de l’application uniquement dans votre organisation. 
- Promouvoir le package de test en préproduction : test de l’application en dehors de votre organisation.
- Promouvoir le package de préproduction en production : version en production. 
- Supprimer un package, ou recommencer à partir d’une phase précédente. 

Examinons chacune de ces phases.

1. Dans l’espace de travail d’application modèle, sélectionnez **Gestion des mises en production**.

    ![Icône Gestion des mises en production](media/service-template-apps-create/power-bi-release-management-icon.png)

2. Sélectionnez **Créer une application**. 

    Si vous avez créé l’application de test dans la section **Créer l’application modèle de test** ci-dessus, vous voyez déjà un rond jaune à côté de la phase **Test**. Vous n’avez donc pas besoin de sélectionner **Créer une application** ici. Si vous sélectionnez cette option, vous revenez en arrière dans le processus de création de l’application modèle.
 
3. Sélectionnez **Obtenir le lien**.

    ![Créer une application, obtenir le lien](media/service-template-apps-create/power-bi-dev-template-create-app-get-link.png)
 
9. Pour tester l’expérience d’installation de l’application, copiez le lien fourni dans la fenêtre de notification et collez-le dans une nouvelle fenêtre de navigateur. 

    À partir de là, la procédure est la même que pour vos clients. Consultez [Installer et distribuer des applications modèles dans votre organisation](service-template-apps-install-distribute.md) pour leur version.
 
10. Dans la boîte de dialogue, sélectionnez **Installer**.

    Au terme de l’installation, vous voyez une notification indiquant que la nouvelle application est prête. 
 
11. Sélectionnez **Accéder à l’application**.
 
12. Dans **Bien démarrer avec votre nouvelle application**, vous voyez votre application telle qu’elle sera présentée à vos clients. 

    ![Bien démarrer avec votre nouvelle application](media/service-template-apps-create/power-bi-template-app-get-started.png)

13. Sélectionnez **Explorer l’application** pour passer en revue l’application de test avec les exemples de données.

1. Pour effectuer des modifications, revenez à l’application dans l’espace de travail d’origine. Modifiez l’application de test jusqu’à ce que vous soyez satisfait.

9. Quand vous êtes prêt à promouvoir votre application en préproduction pour la tester en dehors de votre locataire, revenez au volet **Gestion des mises en production** et sélectionnez **Promouvoir l’application** à côté de **Test**.
 
    ![Promouvoir l’application en préproduction](media/service-template-apps-create/power-bi-template-app-promote.png)

11. Sélectionnez **Promouvoir** pour confirmer votre choix. 

12. Copiez cette nouvelle URL à partager en dehors de votre locataire pour les besoins du test. Ce lien est le même que celui que vous soumettez pour commencer le processus de distribution de votre application sur AppSource.

12. Quand votre application est prête à être mise en production ou partagée via AppSource, revenez au volet **Gestion des mises en production** et sélectionnez **Promouvoir l’application** à côté de **Préproduction**.
 
11. Sélectionnez **Promouvoir** pour confirmer votre choix. 

    Votre application est maintenant en production, et prête à être distribuée.

    ![Application en production](media/service-template-apps-create/power-bi-template-app-production.png)

Pour mettre votre application à la disposition du plus grand nombre possible d’utilisateurs Power BI à travers le monde, nous vous conseillons de la soumettre sur AppSource. Pour plus d’informations, consultez [Offre d’application Power BI](https://docs.microsoft.com/azure/marketplace/cloud-partner-portal/power-bi/cpp-power-bi-offer). 

## <a name="update-your-app"></a>Mettre à jour votre application

Une fois que votre application est en production, vous pouvez recommencer la phase de test, tout en maintenant la continuité de l’application en production. 

1. Dans le volet **Gestion des mises en production**, sélectionnez **Créer une application**.

1. Revenez en arrière dans le processus de création de l’application. 
2. Après avoir défini les paramètres **Personnalisation**, **Contenu**, **Contrôle** et **Accès**, sélectionnez de nouveau **Créer une application**.
3. Sélectionnez **Fermer** et revenez au volet **Gestion des mises en production**. 

    Vous avez maintenant deux versions de l’application : la version en production, et une nouvelle version en phase de test. 

    ![Deux versions d’une application modèle](media/service-template-apps-create/power-bi-template-app-2-versions.png)

## <a name="next-steps"></a>Étapes suivantes

Découvrez de quelle manière vos clients peuvent interagir avec votre application modèle dans l’article [Installer, personnaliser et distribuer des applications modèles dans votre organisation](service-template-apps-install-distribute.md).

Pour plus d’informations sur la distribution de votre application, consultez [Offre d’application Power BI](https://docs.microsoft.com/azure/marketplace/cloud-partner-portal/power-bi/cpp-power-bi-offer).





