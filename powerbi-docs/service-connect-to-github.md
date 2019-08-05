---
title: Se connecter à GitHub avec Power BI
description: GitHub pour Power BI
author: maggiesMSFT
manager: kfile
ms.reviewer: sarinas
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 07/21/2019
ms.author: maggies
LocalizationGroup: Connect to services
ms.openlocfilehash: f8091892f38f498c8072720ad1a93b0c4b07442b
ms.sourcegitcommit: 390dc3716d5c83385bedde63dd152431a77020e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2019
ms.locfileid: "68380241"
---
# <a name="connect-to-github-with-power-bi"></a>Se connecter à GitHub avec Power BI
Cet article vous guide tout au long de l’extraction de vos données à partir de votre compte GitHub à l’aide d’une application de modèle Power BI. L’application de modèle génère un espace de travail avec un tableau de bord, un ensemble de rapports et un jeu de données pour vous permettre d’explorer vos données GitHub. L’application GitHub pour Power BI vous montre un aperçu de votre référentiel GitHub (ou repo) avec des données relatives à des contributions, des problèmes, des requêtes d’extraction et des utilisateurs actifs.

Une fois l’application de modèle installée, vous pouvez modifier le tableau de bord et le rapport. Vous pouvez ensuite le distribuer en tant qu’application aux collègues de votre organisation.

Connectez-vous à [l’application de modèle GitHub](https://app.powerbi.com/groups/me/getapps/services/pbi-contentpacks.pbiapps-github) ou obtenez davantage d’informations sur l’[intégration de GitHub](https://powerbi.microsoft.com/integrations/github) avec Power BI.

Vous pouvez également essayer le [didacticiel de GitHub](service-tutorial-connect-to-github.md). Il installe des données GitHub réelles sur le référentiel public pour la documentation de Power BI.

>[!NOTE]
>L’application de modèle exige que le compte GitHub ait accès au dépôt. Vous trouverez plus d’informations sur la configuration requise ci-dessous.

## <a name="how-to-connect"></a>Comment se connecter
[!INCLUDE [powerbi-service-apps-get-more-apps](./includes/powerbi-service-apps-get-more-apps.md)]
   
3. Sélectionnez **GitHub** \> **Obtenir maintenant**.
4. Dans **Installer cette application Power BI ?** , sélectionnez**Installer**.
4. Dans le volet **Applications**, sélectionnez la vignette **GitHub**.

    ![Vignette GitHub - Power BI](media/service-connect-to-github/power-bi-github-tile.png)

6. Dans **Démarrer avec votre nouvelle application**, sélectionnez **Connecter des données**.

    ![Démarrer avec votre nouvelle application](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-connect-data.png)

5. Entrez le nom et le propriétaire du dépôt. Consultez les détails sur la [recherche de ces paramètres](#FindingParams) ci-dessous.
   
    ![Nom du dépôt GitHub - Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-connect.png)

5. Entrez vos informations d’identification GitHub (cette étape peut être ignorée si vous êtes déjà connecté avec votre navigateur). 
6. Pour la **Méthode d’authentification**, sélectionnez **oAuth2** \> **Se connecter**. 
7. Suivez les écrans d’authentification GitHub. Accordez à l’application de modèle GitHub pour Power BI l’autorisation d’accéder aux données GitHub.
   
   ![Autorisation GitHub Power BI](media/service-connect-to-github/github_authorize.png)
   
    Power BI se connecte à GitHub et à vos données.  Les données sont actualisées une fois par jour. Une fois les données importées dans Power BI, le contenu de votre nouvel espace de travail GitHub s’affiche.

## <a name="modify-and-distribute-your-app"></a>Modifier et distribuer votre application

Vous avez installé l’application de modèle GitHub. Cela signifie que vous avez également créé l’espace de travail d’application GitHub. Dans l’espace de travail, vous pouvez modifier le rapport et le tableau de bord, puis distribuez-le en tant qu’*application* aux collègues de votre organisation. 

1. Sélectionnez la flèche à côté du nom de l’espace de travail dans la barre de navigation de gauche. L’espace de travail contient un tableau de bord et un rapport.

    ![Application dans le volet de navigation de gauche](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-left-nav-expanded.png)

8. Sélectionnez le nouveau [tableau de bord GitHub](https://powerbi.microsoft.com/integrations/github).    
    ![Tableau de bord GitHub dans Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-new-dashboard.png)

3. Pour afficher tout le contenu de votre nouvel espace de travail GitHub, dans la barre de navigation gauche, sélectionnez **Espaces de travail** > **GitHub**.
 
   ![Espace de travail GitHub dans le volet de navigation de gauche](media/service-connect-to-github/power-bi-github-left-nav.png)

    Cette vue est la liste de contenu de l’espace de travail. Dans l’angle supérieur droit, vous voyez **Mettre à jour l’application**. Lorsque vous êtes prêt à distribuer votre application à vos collègues, c’est là que vous allez commencer. 

    ![Liste de contenu GitHub](media/service-connect-to-github/power-bi-github-content-list.png)

2. Sélectionnez **Rapports** et **Jeux de données** pour afficher les autres éléments dans l’espace de travail.

    En savoir plus sur [la distribution d’applications](service-create-distribute-apps.md) à vos collègues.

## <a name="whats-included-in-the-app"></a>Ce qui est inclus dans l’application
Les données suivantes sont disponibles à partir de GitHub dans Power BI :     

| Nom du tableau | Description |
| --- | --- |
| Contributions |Le tableau Contributions indique les ajouts, suppressions et validations totaux créés par le contributeur, agrégés par semaine. Les 100 premiers collaborateurs sont inclus. |
| Issues |Ce tableau répertorie tous les problèmes pour le dépôt sélectionné et contient des calculs tels que le temps total et moyen pour fermer un problème, le nombre total de problèmes ouverts et le nombre total de problèmes fermés. Ce tableau est vide si le dépôt ne contient aucun problème. |
| Pull requests |Ce tableau contient toutes les requêtes d’extraction pour le dépôt et leurs auteurs. Elle indique également le nombre de requêtes d’extraction ouvertes, fermées et totales, le temps nécessaire pour extraire les requêtes et la durée moyenne des requêtes d’extraction. Ce tableau est vide si le dépôt ne contient aucun problème. |
| Utilisateurs |Ce tableau répertorie les utilisateurs ou contributeurs GitHub qui ont collaboré, enregistré des problèmes ou résolu des requêtes d’extraction pour le dépôt sélectionné. |
| Milestones |Ce tableau recense les étapes majeures pour le dépôt sélectionné. |
| DateTable |Ce tableau, qui contient des dates sur plusieurs années dans le passé à partir de la date du jour, vous permet d’analyser vos données GitHub par date. |
| ContributionPunchCard |Ce tableau peut être utilisé comme une carte à perforer des contributions pour le dépôt sélectionné. Il indique les validations par jour de la semaine et heure de la journée. Ce tableau n’est pas connecté aux autres tableaux du modèle. |
| RepoDetails |Ce tableau fournit des détails sur le dépôt sélectionné. |

## <a name="system-requirements"></a>Configuration requise
* Compte GitHub ayant accès au dépôt.  
* Autorisation accordée à l’application Power BI pour GitHub à la première connexion. Consultez les détails ci-dessous sur la révocation de l’accès.  
* Suffisamment d’appels d’API sont disponibles pour l’extraction et l’actualisation des données.  

### <a name="de-authorize-power-bi"></a>Retirer l’autorisation à Power BI
Pour retirer à Power BI l’autorisation de se connecter à votre dépôt GitHub, vous pouvez révoquer l’accès dans GitHub. Consultez cette rubrique d’[aide GitHub](https://help.github.com/articles/keeping-your-ssh-keys-and-application-access-tokens-safe/#reviewing-your-authorized-applications-oauth) pour plus de détails.

<a name="FindingParams"></a>
## <a name="finding-parameters"></a>Recherche de paramètres
Vous pouvez déterminer le propriétaire et le dépôt en examinant le dépôt GitHub lui-même :

![Nom et propriétaire du référentiel](media/service-connect-to-github/github_ownerrepo.png)

La première partie « Azure » représente le propriétaire, tandis que la deuxième partie « azure-sdk-for-php » correspond au dépôt proprement dit.  Ces deux mêmes éléments apparaissent dans l’URL du dépôt :

    <https://github.com/Azure/azure-sdk-for-php> .

## <a name="troubleshooting"></a>Résolution des problèmes
Si nécessaire, vous pouvez vérifier vos informations d’identification GitHub.  

1. Dans une autre fenêtre de navigateur, accédez au site web GitHub et connectez-vous à GitHub. Vous pouvez voir que vous êtes connecté dans le coin supérieur droit du site GitHub.    
2. Dans GitHub, accédez à l’URL du dépôt auquel vous envisagez d’accéder dans Power BI. Par exemple : https://github.com/dotnet/corefx.  
3. Dans Power BI, essayez de vous connecter à GitHub. Dans la boîte de dialogue Configurer GitHub, utilisez les noms du dépôt et du propriétaire de ce même dépôt.  

## <a name="next-steps"></a>Étapes suivantes

* [Tutoriel : Se connecter à un référentiel GitHub à l’aide de Power BI](service-tutorial-connect-to-github.md)
* [Créer les nouveaux espaces de travail dans Power BI](service-create-the-new-workspaces.md)
* [Installer et utiliser des applications dans Power BI](consumer/end-user-apps.md)
* [Se connecter aux applications Power BI pour des services externes](service-connect-to-services.md)
* Vous avez des questions ? [Essayez d’interroger la communauté Power BI](http://community.powerbi.com/)

