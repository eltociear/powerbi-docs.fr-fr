---
title: Partager un jeu de données (préversion)
description: En tant que propriétaire de jeu de données, vous pouvez créer et partager vos jeux de données afin que d’autres utilisateurs puissent les utiliser. Apprenez à les partager.
author: maggiesMSFT
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/01/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 4114287099300c371a6b02961a968702acb98f92
ms.sourcegitcommit: a72567f26c1653c25f7730fab6210cd011343707
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83565457"
---
# <a name="share-a-dataset-preview"></a>Partager un jeu de données (préversion)

En tant que créateur de *modèles de données* dans Power BI Desktop, vous créez des *jeux de données* que vous pouvez distribuer dans le service Power BI. D'autres créateurs de rapport peuvent ensuite utiliser vos jeux de données comme base pour leurs propres rapports. Dans cet article, vous découvrirez comment partager vos jeux de données. Pour savoir comment donner et supprimer l'accès à vos jeux de données partagés, lisez la section [Autorisation de génération](service-datasets-build-permissions.md).

## <a name="steps-to-sharing-your-dataset"></a>Procédure à suivre pour partager votre jeu de données

1. Vous commencez par créer un fichier .pbix avec un modèle de données dans Power BI Desktop. Si vous planifiez de proposer ce jeu de données pour que d’autres personnes génèrent des rapports, vous ne concevez même pas un rapport dans le fichier .pbix.

    Une bonne pratique est d’enregistrer le fichier .pbix dans un groupe Microsoft 365.

1. Publiez le fichier .pbix dans un [espace de travail de nouvelle expérience](../collaborate-share/service-create-the-new-workspaces.md) dans le service Power BI.
    
    Les autres membres de cet espace de travail peuvent déjà créer des rapports dans d’autres espaces de travail basés sur ce jeu de données.

1. Vous pouvez également [publier une application](../collaborate-share/service-create-distribute-apps.md) à partir de cet espace de travail. Dans ce cas, dans la page **Autorisations**, vous spécifiez qui dispose d’autorisations et ce qu’ils peuvent faire.

    > [!NOTE]
    > Si vous sélectionnez **Organisation entière**, personne dans l’organisation ne disposera de l’autorisation de génération. Ce problème est déjà connu. Au lieu de cela, spécifiez des adresses e-mail dans **Individus ou groupes spécifiques**.  Si vous voulez que l’ensemble de votre organisation dispose de l’autorisation de génération, spécifiez un alias d’e-mail pour toute l’organisation.

    ![Définir des autorisations d’application](media/service-datasets-build-permissions/power-bi-dataset-app-permission-new-look.png)

1. Sélectionnez **Publier l’application**, ou **Mettre à jour l’application** si elle est déjà publiée.

## <a name="track-your-dataset-usage"></a>Effectuer le suivi de l’utilisation de votre jeu de données

Quand vous avez un jeu de données partagé dans votre espace de travail, vous devrez peut-être savoir sur quels rapports d’autres espaces de travail il repose.

1. En mode Liste de jeux de données, sélectionnez **Afficher les éléments associés**.

    ![l’icône Afficher les travaux associés](media/service-datasets-build-permissions/power-bi-dataset-view-related-to-dataset.png)

1. La boîte de dialogue **Contenu associé** affiche tous les éléments associés. Dans cette liste, vous voyez les éléments associés dans cet espace de travail et dans d’**autres espaces de travail**.
 
    ![Boîte de dialogue Contenu associé](media/service-datasets-build-permissions/power-bi-dataset-related-workspaces.png)

## <a name="next-steps"></a>Étapes suivantes

- [Utiliser des jeux de données dans des espaces de travail (préversion)](service-datasets-across-workspaces.md)
- Vous avez des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
