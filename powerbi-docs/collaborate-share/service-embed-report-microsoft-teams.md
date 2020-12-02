---
title: Incorporer des rapports Power BI dans Microsoft Teams
description: Vous pouvez facilement incorporer des rapports Power BI interactifs dans les canaux et conversations Microsoft Teams. .
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: conceptual
LocalizationGroup: Share your work
ms.date: 09/21/2020
ms.openlocfilehash: 36973d52f94b806db860b739a84f0c94b2a8945d
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96411859"
---
# <a name="embed-power-bi-content-in-microsoft-teams"></a>Incorporer du contenu Power BI dans Microsoft Teams

Vous pouvez facilement incorporer des rapports Power BI interactifs dans les canaux et conversations Microsoft Teams. 

## <a name="requirements"></a>Configuration requise

Pour utiliser l’onglet **Power BI** dans Microsoft Teams, vérifiez les éléments suivants :

- Microsoft Teams a l’onglet **Power BI**.
- Pour ajouter un rapport dans Microsoft Teams avec l’onglet **Power BI**, vous disposez au moins du rôle Lecteur dans l’espace de travail qui héberge le rapport. Pour plus d’informations sur les différents rôles, consultez [Rôles dans les nouveaux espaces de travail](service-new-workspaces.md#roles-in-the-new-workspaces).
- Pour afficher le rapport sous l’onglet **Power BI** dans Microsoft Teams, les utilisateurs doivent être autorisés à visualiser le rapport.
- Les utilisateurs doivent être des utilisateurs de Microsoft Teams ayant accès aux canaux et aux conversations.

Pour plus d’informations sur l’interaction entre Power BI et Microsoft Teams, et notamment pour connaître d’autres conditions à remplir, consultez [Collaboration dans Microsoft Teams avec Power BI](service-embed-report-microsoft-teams.md).

## <a name="embed-a-report-in-microsoft-teams"></a>Incorporer un rapport dans Microsoft Teams

Suivez ces étapes pour incorporer votre rapport dans un canal ou une conversation Microsoft Teams.

1. Ouvrez un canal ou une conversation dans Microsoft Teams, puis sélectionnez l’icône **+** .

    ![Capture d’écran de l’ajout d’un onglet à un canal ou à une conversation](media/service-embed-report-microsoft-teams/service-embed-report-microsoft-teams-add.png)

1. Sélectionnez l’onglet **Power BI**.

    ![Capture d’écran de la liste d’onglets Microsoft Teams avec mise en évidence de Power BI](media/service-embed-report-microsoft-teams/service-embed-report-microsoft-teams-tab.png)

1. Utilisez les options fournies pour sélectionner un rapport dans un espace de travail ou une application Power BI.

    ![Capture d’écran de l’onglet Power BI pour les paramètres Microsoft Teams](media/service-embed-report-microsoft-teams/service-embed-report-microsoft-teams-tab-settings.png)

1. Le nom de l’onglet est automatiquement mis à jour pour correspondre au nom du rapport, mais vous pouvez le modifier.

1. Sélectionnez **Enregistrer**.

### <a name="reports-you-can-embed-on-the-power-bi-tab"></a>Rapports que vous pouvez incorporer sous l’onglet Power BI

Vous pouvez incorporer les types de rapports suivants sur l’onglet **Power BI** :

- Rapports interactifs et paginés.
- Rapports dans **Mon espace de travail**, les nouvelles expériences d’espace de travail et les espaces de travail classiques.
- Rapports dans des applications Power BI.

## <a name="start-a-conversation"></a>Démarrer une conversation

Quand vous ajoutez un onglet de rapport Power BI dans Microsoft Teams, Microsoft Teams crée automatiquement une conversation dans un onglet pour le rapport.

- Sélectionnez l’icône **Afficher l’onglet de conversation** dans l’angle supérieur droit.

    ![Capture d’écran de l’icône Afficher l’onglet de conversation](media/service-embed-report-microsoft-teams/power-bi-teams-conversation-icon.png)

    Le premier commentaire est un lien vers le rapport. Tout le monde dans ce canal Microsoft Teams peut voir le rapport et en discuter dans la conversation.

    ![Capture d’écran de la conversation dans un onglet.](media/service-embed-report-microsoft-teams/power-bi-teams-conversation-tab.png)

## <a name="known-issues-and-limitations"></a>Problèmes connus et limitations

- Dans Microsoft Teams, lorsque vous exportez des données d’un visuel dans un rapport Power BI, elles sont automatiquement enregistrées dans votre dossier Téléchargements. Il s’agit d’un fichier Excel nommé « data (*n*).xlsx », où *n* correspond au nombre de fois où vous avez exporté des données dans le même dossier.
- Vous ne pouvez pas incorporer les tableaux de bord Power BI dans l’onglet **Power BI** pour Microsoft Teams.
- Les [filtres d’URL](service-url-filters.md) ne sont pas pris en charge avec l’onglet **Power BI** pour Microsoft Teams.
- Dans les clouds nationaux, le nouvel onglet **Power BI** n’est pas disponible. Une version plus ancienne peut être disponible, qui ne prend pas en charge la nouvelle expérience ni les rapports dans les applications Power BI.
- Une fois que vous avez enregistré l’onglet, vous ne changez pas son nom via les paramètres des onglets. Utilisez l’option **Renommer** pour le changer.
- Pour d’autres problèmes, consultez la section [Problèmes connus et limitations](service-collaborate-microsoft-teams.md#known-issues-and-limitations) de l’article « Collaborer dans Microsoft Teams ».

## <a name="next-steps"></a>Étapes suivantes

- [Collaborer dans Microsoft Teams avec Power BI](service-collaborate-microsoft-teams.md)

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
