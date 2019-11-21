---
title: Que sont les applications modèles Power BI ?
description: Cet article présente une vue d’ensemble du programme d’applications modèles Power BI. Découvrez comment créer des applications Power BI avec peu ou pas de codage et les déployer ensuite vers n’importe quel client Power BI.
author: teddybercovitz
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/24/2019
ms.author: tebercov
ms.openlocfilehash: 4b4e32f787d2d262d604ff0745f8c028e9fff949
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73871336"
---
# <a name="what-are-power-bi-template-apps"></a>Que sont les applications modèles Power BI ?

Les nouvelles *applications modèles* Power BI permettent aux partenaires Power BI de créer des applications Power BI avec peu ou pas de codage et de les déployer ensuite vers n’importe quel client Power BI.  Cet article présente une vue d’ensemble du programme d’applications modèles Power BI.

Les applications modèles remplacent les packs de contenu de service actuels. En tant que partenaire Power BI, vous créez du contenu prêt à l’emploi pour vos clients et vous le publiez vous-même.  

Vous concevez des applications modèles qui permettent à vos clients de se connecter et d’instancier avec leurs propres comptes. En tant qu’experts dans leur domaine, les clients peuvent déverrouiller les données pour les rendre facilement consommables par leurs utilisateurs professionnels.  

Vous soumettez les applications modèles sur le portail Cloud Partner. Les applications sont ensuite mises à la disposition de tous dans la galerie d’applications Power BI (app.powerbi.com/getdata/services) et sur Microsoft AppSource (appsource.microsoft.com). Voici un aperçu général de la création d’applications modèles publiques.  

## <a name="process"></a>Processus
Le processus général de développement et de soumission d’une application modèle implique plusieurs étapes. Certaines étapes peuvent inclure plusieurs activités simultanées.


| Phase | Power BI Desktop |  |Service Power BI  |  |Portail Cloud Partner  |
|---|--------|--|---------|---------|---------|
| **Un** | Créer un modèle de données et un rapport dans un fichier .pbix |  | Créer un espace de travail. Importer le fichier .pbix. Créer un tableau de bord supplémentaire  |  | S’inscrire en tant que partenaire |
| **Deux** |  |  | Créer un package de test et effectuer la validation interne        |  | |
| **Trois** | |  | Promouvoir le package de test en préproduction pour sa validation en dehors de votre locataire Power BI, et le soumettre sur AppSource  |  | Avec le package de préproduction, créer une offre d’application modèle Power BI et démarrer le processus de validation |
| **Quatre** | |  | Promouvoir le package de préproduction en production |  | Mettre en ligne l’application modèle |

## <a name="before-you-begin"></a>Avant de commencer

Pour créer l’application modèle, vous devez avoir les autorisations de création appropriées. Pour plus d’informations, consultez Paramètres des applications modèles dans le portail d’administration Power BI. 

Pour publier une application modèle sur le service Power BI et AppSource, vous devez remplir les conditions requises pour [devenir un éditeur sur la Place de marché dans le cloud](https://docs.microsoft.com/azure/marketplace/become-publisher).
 
## <a name="high-level-steps"></a>Étapes principales

Voici les principales étapes à suivre. 

1. [Passez en revue les conditions requises](#requirements) et vérifiez que vous les remplissez. 

1. Générez un rapport dans Power BI Desktop. À l’aide des paramètres, enregistrez le rapport sous forme de fichier utilisable par tous. 

1. Créez un espace de travail pour l’application modèle dans votre locataire sur le service Power BI (app.powerbi.com). 

1. Importez votre fichier .pbix et ajoutez du contenu (comme un tableau de bord) à votre application. 

1. Créez un package de test pour tester vous-même l’application modèle dans votre organisation. 

1. Promouvez l’application de test en préproduction pour soumettre l’application sur AppSource en vue de sa validation et pour la tester en dehors de votre propre locataire. 

1. Soumettez le contenu sur la plateforme Cloud Partner en vue de sa publication. 

1. Mettez votre offre « En ligne » dans AppSource et placez votre application en production dans Power BI.
2. Vous pouvez maintenant commencer à développer la prochaine version de l’application dans le même espace de travail, en préproduction. 

## <a name="requirements"></a>Configuration requise

Pour créer l’application modèle, vous devez avoir les autorisations de création appropriées. Pour plus d’informations, consultez [Paramètres des applications modèles dans le portail d’administration](service-admin-portal.md#template-apps-settings) Power BI. 

Pour publier une application modèle sur le service Power BI et AppSource, vous devez remplir les conditions requises pour [devenir un éditeur sur la Place de marché dans le cloud](https://docs.microsoft.com/azure/marketplace/become-publisher).
 > [!NOTE] 
 > Les envois d’applications modèles sont gérés dans [Portail Cloud Partner](https://cloudpartner.azure.com). Utilisez le même compte d’inscription du Centre pour développeurs Microsoft pour vous connecter. Vous devez avoir qu’un seul compte Microsoft pour vos offres AppSource. Les comptes ne doivent pas être spécifiques à des services ou offres individuels.

## <a name="tips"></a>Conseils 

- Assurez-vous que votre application contient des exemples de données pour aider les utilisateurs à démarrer en un clic. 
- Examinez soigneusement votre application en l’installant dans votre locataire et dans un locataire secondaire. Assurez-vous que les clients voient uniquement ce que vous souhaitez leur montrer. 
- Utilisez AppSource comme magasin en ligne pour y héberger votre application. De cette manière, tout le monde pourra facilement trouver votre application à l’aide de Power BI. 
- Prévoyez de proposer plusieurs applications modèles pour répondre à différents scénarios particuliers. 
- Autorisez la personnalisation des données. Par exemple, autorisez la configuration de paramètres et de connexions personnalisés par le programme d’installation.

Consultez [Conseils pour créer des applications modèles dans Power BI](service-template-apps-tips.md) pour obtenir des suggestions supplémentaires.

## <a name="support"></a>Support
Pour bénéficier d’un support durant le développement, utilisez [https://powerbi.microsoft.com/support](https://powerbi.microsoft.com/support). Nous supervisons et gérons activement ce site. Les incidents utilisateur sont rapidement transmis à la bonne équipe.

## <a name="next-steps"></a>Étapes suivantes

[Créer une application modèle](service-template-apps-create.md)
