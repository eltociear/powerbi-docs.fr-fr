---
title: Se connecter à GitHub avec Power BI
description: GitHub pour Power BI
author: maggiesMSFT
manager: kfile
ms.reviewer: sarinas
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 04/26/2019
ms.author: maggies
LocalizationGroup: Connect to services
ms.openlocfilehash: b0f2bd53f1d8b82b70072446723c2ca3723eeacd
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "65608431"
---
# <a name="connect-to-github-with-power-bi"></a>Se connecter à GitHub avec Power BI
Cet article vous guide tout au long de l’extraction de vos données à partir de votre compte GitHub à une application de modèle Power BI. Le modèle d’application génère un espace de travail avec un tableau de bord, un ensemble de rapports et un jeu de données qui vous permettent d’Explorer vos données GitHub. L’application GitHub pour Power BI affiche les informations dans votre référentiel GitHub, également appelé référentiel, avec les données relatives à des contributions, les problèmes, les demandes de tirage et les utilisateurs actifs.

Une fois que vous avez installé le modèle d’application, vous pouvez modifier le tableau de bord et rapports. Vous pouvez distribuer en tant qu’application à vos collègues dans votre organisation.

Se connecter à la [d’application du modèle GitHub](https://app.powerbi.com/getdata/services/github) ou en savoir plus sur la [GitHub integration](https://powerbi.microsoft.com/integrations/github) avec Power BI.

Vous pouvez également essayer le [GitHub didacticiel](service-tutorial-connect-to-github.md). Il installe des données réelles de GitHub sur le référentiel public pour la documentation de Power BI.

>[!NOTE]
>Le modèle d’application nécessite le compte GitHub ait accès au référentiel. Vous trouverez plus d’informations sur la configuration requise ci-dessous.

## <a name="how-to-connect"></a>Comment se connecter
[!INCLUDE [powerbi-service-apps-get-more-apps](./includes/powerbi-service-apps-get-more-apps.md)]
   
3. Sélectionnez **GitHub** \> **obtenez-le maintenant**.
4. Dans **installer cette application Power BI ?** sélectionnez **installer**.
4. Dans le **applications** volet, sélectionnez le **GitHub** vignette.

    ![Vignette GitHub - Power BI](media/service-connect-to-github/power-bi-github-tile.png)

6. Dans **prise en main votre nouvelle application**, sélectionnez **se connecter aux données**.

    ![Démarrer avec votre nouvelle application](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-connect-data.png)

5. Entrez le nom et le propriétaire du dépôt. Consultez les détails sur la [recherche de ces paramètres](#FindingParams) ci-dessous.
   
    ![Nom du dépôt GitHub - Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-connect.png)

5. Entrez vos informations d’identification GitHub (cette étape peut être ignorée si vous êtes déjà connecté avec votre navigateur). 
6. Pour la **Méthode d’authentification**, sélectionnez **oAuth2** \> **Se connecter**. 
7. Suivez les écrans d’authentification GitHub. Accordez à GitHub pour l’autorisation d’application de modèle Power BI aux données GitHub.
   
   ![Autoriser Power BI GitHub](media/service-connect-to-github/github_authorize.png)
   
    Power BI se connecte à GitHub et vos données.  Les données sont actualisées une fois par jour. Une fois que Power BI importe les données, vous consultez le contenu de votre nouvel espace de travail de GitHub.

## <a name="modify-and-distribute-your-app"></a>Modifier et distribuer votre application

Vous avez installé le modèle d’application GitHub. Cela signifie que vous avez également créé l’espace de travail GitHub. Dans l’espace de travail, vous pouvez modifier le rapport et un tableau de bord et distribuez-la comme un *application* à vos collègues de votre organisation. 

1. Dans la barre de navigation de gauche, sélectionnez la flèche en regard du nom de l’espace de travail. Vous consultez que l’espace de travail contient un tableau de bord et un rapport.

    ![Application dans le volet de navigation gauche](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-left-nav-expanded.png)

8. Sélectionnez la nouvelle [tableau de bord GitHub](https://powerbi.microsoft.com/integrations/github).    
    ![Tableau de bord GitHub dans Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-new-dashboard.png)

3. Pour afficher tout le contenu de votre nouvel espace de travail GitHub, dans la barre de navigation gauche, sélectionnez **espaces de travail** > **GitHub**.
 
   ![Espace de travail de GitHub dans le volet de navigation gauche](media/service-connect-to-github/power-bi-github-left-nav.png)

    Cette vue est la liste de contenu pour l’espace de travail. Dans le coin supérieur droit, vous voyez **mise à jour application**. Lorsque vous êtes prêt à distribuer votre application à vos collègues, c’est là que vous allez commencer. 

    ![Liste de contenu GitHub](media/service-connect-to-github/power-bi-github-content-list.png)

2. Sélectionnez **rapports** et **jeux de données** pour voir les autres éléments dans l’espace de travail.

    En savoir plus sur [distribution d’applications](service-create-distribute-apps.md) à vos collègues.

## <a name="whats-included-in-the-app"></a>Ce qui est inclus dans l’application
Les données suivantes sont disponibles à partir de GitHub dans Power BI :     

| Nom du tableau | Description |
| --- | --- |
| Contributions |Le tableau contributions indique le total ajouts, les suppressions et validations créées par le contributeur, agrégés par semaine. Les 100 premiers collaborateurs sont inclus. |
| Issues |Ce tableau répertorie tous les problèmes pour le dépôt sélectionné et contient des calculs tels que le temps total et moyen pour fermer un problème, le nombre total de problèmes ouverts et le nombre total de problèmes fermés. Ce tableau est vide si le dépôt ne contient aucun problème. |
| Pull requests |Ce tableau contient toutes les requêtes d’extraction pour le dépôt et leurs auteurs. Il contient également des calculs autour de combien de demandes de tirage ouvertes, fermées et total, temps nécessaire pour extraire les requêtes et la durée de la demande de tirage moyenne. Ce tableau est vide si le dépôt ne contient aucun problème. |
| Users |Ce tableau fournit une liste des utilisateurs de GitHub ou des contributeurs qui ont apporté des contributions, enregistré des problèmes ou résolu des requêtes d’extraction pour le dépôt sélectionné. |
| Milestones |Ce tableau recense les étapes majeures pour le dépôt sélectionné. |
| DateTable |Cette table contient des dates à partir d’aujourd'hui et depuis des années dans le passé qui vous permettent d’analyser vos données GitHub par date. |
| ContributionPunchCard |Ce tableau peut être utilisé comme une carte à perforer des contributions pour le dépôt sélectionné. Il indique les validations par jour de la semaine et heure de la journée. Ce tableau n’est pas connecté aux autres tableaux du modèle. |
| RepoDetails |Ce tableau fournit des détails sur le dépôt sélectionné. |

## <a name="system-requirements"></a>Configuration requise
* Compte GitHub ayant accès au dépôt.  
* Autorisation accordée à l’application Power BI pour GitHub à la première connexion. Consultez les détails ci-dessous sur la révocation de l’accès.  
* Suffisamment d’appels d’API sont disponibles pour l’extraction et l’actualisation des données.  

### <a name="de-authorize-power-bi"></a>Retirer l’autorisation à Power BI
Pour retirer l’autorisation Power BI de se connecter à votre référentiel GitHub, vous pouvez révoquer l’accès dans GitHub. Consultez ce [GitHub aide](https://help.github.com/articles/keeping-your-ssh-keys-and-application-access-tokens-safe/#reviewing-your-authorized-applications-oauth) pour plus d’informations.

<a name="FindingParams"></a>
## <a name="finding-parameters"></a>Recherche de paramètres
Vous pouvez déterminer le propriétaire et le dépôt en examinant le dépôt GitHub lui-même :

![Propriétaire et le nom de référentiel](media/service-connect-to-github/github_ownerrepo.png)

La première partie « Azure » représente le propriétaire, tandis que la deuxième partie « azure-sdk-for-php » correspond au dépôt proprement dit.  Ces deux mêmes éléments apparaissent dans l’URL du dépôt :

    <https://github.com/Azure/azure-sdk-for-php> .

## <a name="troubleshooting"></a>Résolution des problèmes
Si nécessaire, vous pouvez vérifier vos informations d’identification GitHub.  

1. Dans une autre fenêtre de navigateur, accédez au site web GitHub et connectez-vous à GitHub. Vous pouvez voir que vous êtes connecté dans le coin supérieur droit du site GitHub.    
2. Dans GitHub, accédez à l’URL du dépôt auquel vous envisagez d’accéder dans Power BI. Par exemple : https://github.com/dotnet/corefx.  
3. Dans Power BI, essayez de vous connecter à GitHub. Dans la boîte de dialogue Configurer GitHub, utilisez les noms du dépôt et du propriétaire de ce même dépôt.  

## <a name="next-steps"></a>Étapes suivantes

* [Tutoriel : Se connecter à un référentiel GitHub avec Power BI](service-tutorial-connect-to-github.md)
* [Créer de nouveaux espaces de travail dans Power BI](service-create-the-new-workspaces.md)
* [Installer et utiliser des applications dans Power BI](consumer/end-user-apps.md)
* [Se connecter à des applications Power BI pour les services externes](service-connect-to-services.md)
* Vous avez des questions ? [Essayez d’interroger la communauté Power BI](http://community.powerbi.com/)

