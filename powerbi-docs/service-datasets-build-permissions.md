---
title: Créer et partager des jeux de données (préversion) - Power BI
description: En tant que propriétaire de jeu de données, vous pouvez créer et partager vos jeux de données afin que d’autres utilisateurs puissent les utiliser. Découvrez comment vous pouvez garder le contrôle de qui peut accéder aux données à l’aide de l’autorisation de génération.
author: maggiesMSFT
manager: kfile
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/31/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 22339b3d5062c01b3795086eede24ed6a8e7d7e7
ms.sourcegitcommit: 7c426a5209d4fdd1360fc3d0442d57991be1984d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/03/2019
ms.locfileid: "66461761"
---
# <a name="create-and-share-datasets-preview"></a>Créer et partager des jeux de données (préversion)

En tant que créateur de *modèles de données* dans Power BI Desktop, vous pouvez les partager en tant que *jeux de données* dans le service Power BI. Les créateurs de rapports peuvent alors facilement découvrir et réutiliser les jeux de données que vous avez partagés. Découvrez comment les partager et comment contrôler qui peut accéder aux données à l’aide de l’autorisation de génération.

## <a name="steps-to-sharing-your-dataset"></a>Procédure à suivre pour partager votre jeu de données

1. Vous commencez par créer un fichier .pbix avec un modèle de données dans Power BI Desktop. Si vous planifiez de proposer ce jeu de données pour que d’autres personnes génèrent des rapports, vous ne concevez même pas un rapport dans le fichier .pbix.

    Enregistrer le fichier .pbix dans un groupe Office 365 constitue une bonne pratique.

1. Publiez le fichier .pbix dans un [espace de travail de nouvelle expérience](service-create-the-new-workspaces.md) dans le service Power BI.
    
    Les autres membres de cet espace de travail peuvent déjà créer des rapports dans d’autres espaces de travail basés sur ce jeu de données.

1. Maintenant, vous pouvez [créer une application](service-create-distribute-apps.md) à partir de cet espace de travail. Dans ce cas, dans la page **Autorisations**, vous spécifiez qui dispose d’autorisations et ce qu’ils peuvent faire.

    > [!NOTE]
    > Si vous sélectionnez **Organisation entière**, personne dans l’organisation ne disposera d’autorisations de génération. Ce problème est déjà connu. Au lieu de cela, spécifiez des adresses e-mail dans **Individus ou groupes spécifiques**.  Si vous voulez que l’ensemble de votre organisation dispose d’autorisations de génération, spécifiez un alias d’e-mail pour toute l’organisation.

    ![Définir des autorisations d’application](media/service-datasets-build-permissions/power-bi-dataset-app-permissions.png)

1. Sélectionnez **Publier l’application**, ou **Mettre à jour l’application** si elle est déjà publiée.

## <a name="build-permissions-for-shared-datasets"></a>Autorisations de génération pour des jeux de données partagés

Le type d’autorisation de génération concerne uniquement les jeux de données. Il permet aux utilisateurs de générer du nouveau contenu sur un jeu de données, comme des rapports, des tableaux de bord, des vignettes épinglées à partir de Q&R et Insights Discovery. Il leur permet également de générer du nouveau contenu sur le jeu de données hors de Power BI, comme des feuilles Excel par le biais de la fonctionnalité Analyser dans Excel, XMLA et Export.

Les utilisateurs obtiennent l’autorisation de génération de différentes façons :

- Un membre de l’espace de travail où se trouve le jeu de données peut attribuer l’autorisation à des utilisateurs ou des groupes de sécurité spécifiques dans le Centre des autorisations. Sélectionnez les points de suspension (...) en regard d’un jeu de données > **Gérer les autorisations**.

    ![Sélectionner les points de suspension](media/service-datasets-build-permissions/power-bi-dataset-manage-permissions.png)

    Cette opération ouvre le Centre des autorisations pour ce jeu de données, où vous pouvez définir et modifier les autorisations.

    ![Centre des autorisations](media/service-datasets-build-permissions/power-bi-dataset-permissions.png)

- Un administrateur ou un membre de l’espace de travail où se trouve le jeu de données peut décider, pendant la publication de l’application, que les utilisateurs autorisés à accéder à l’application reçoivent également des autorisations de génération pour les jeux de données sous-jacents. Pour plus d’informations, consultez [Procédure à suivre pour partager votre jeu de données](#steps-to-sharing-your-dataset).

- Imaginons que vous disposez d’autorisations de repartage et de génération sur un jeu de données. Quand vous partagez un rapport ou un tableau de bord reposant sur ce jeu de données, vous pouvez spécifier que les destinataires obtiennent également l’autorisation de génération pour le jeu de données sous-jacent.

    ![Autorisations de génération](media/service-datasets-build-permissions/power-bi-share-report-allow-users.png)

Vous pouvez supprimer les autorisations de génération des utilisateurs pour un jeu de données. Dans ce cas, ils peuvent toujours voir le rapport généré sur le jeu de données partagé, mais ils ne peuvent plus le modifier.

## <a name="more-granular-permissions"></a>Autorisations plus granulaires

Power BI a introduit l’autorisation de génération en juin 2019 en complément des autorisations existantes : lecture et repartage. Tous les utilisateurs qui, à ce moment-là, disposaient déjà de l’autorisation de lecture pour les jeux de données par le biais des autorisations d’application, du partage ou de l’accès aux espaces de travail obtenaient aussi les autorisations de génération pour ces mêmes jeux de données. Ils obtenaient automatiquement l’autorisation de génération car l’autorisation de lecture leur accordait déjà le droit de générer du nouveau contenu basé sur le jeu de données, en utilisant la fonctionnalité Analyser dans Excel ou Export.

Avec cette autorisation de génération plus granulaire, vous pouvez choisir qui peut uniquement afficher le contenu du rapport ou du tableau de bord existant et qui peut créer du contenu connecté aux jeux de données sous-jacents.

Si votre jeu de données est actuellement utilisé par un rapport hors de l’espace de travail du jeu de données, vous ne pouvez pas supprimer ce jeu de données. Au lieu de cela, un message d’erreur s’affiche.

Vous pouvez supprimer des autorisations de génération. Si vous le faites, les personnes dont vous avez révoqué les autorisations peuvent toujours visualiser le rapport, mais elles ne peuvent plus le modifier.

## <a name="track-your-dataset-usage"></a>Effectuer le suivi de l’utilisation de votre jeu de données

Quand vous avez un jeu de données partagé dans votre espace de travail, vous devrez peut-être savoir sur quels rapports d’autres espaces de travail il repose.

1. En mode Liste de jeux de données, sélectionnez **Afficher les éléments associés**.

    ![l’icône Afficher les travaux associés](media/service-datasets-build-permissions/power-bi-dataset-view-related-to-dataset.png)

1. La boîte de dialogue **Contenu associé** affiche tous les éléments associés. Dans cette liste, vous voyez les éléments associés dans cet espace de travail et dans d’**autres espaces de travail**.
 
    ![Boîte de dialogue Contenu associé](media/service-datasets-build-permissions/power-bi-dataset-related-workspaces.png)

## <a name="next-steps"></a>Étapes suivantes

- [Utiliser des jeux de données dans des espaces de travail (préversion)](service-datasets-across-workspaces.md)
- Vous avez des questions ? [Essayez d’interroger la communauté Power BI](http://community.powerbi.com/)
