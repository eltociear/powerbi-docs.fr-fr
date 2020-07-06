---
title: Résolution des problèmes de partage de tableaux de bord et de rapports
description: Découvrez comment résoudre les problèmes de partage de tableaux de bord et de rapports Power BI avec des collègues qui font partie ou non de votre organisation.
author: maggiesMSFT
ms.reviewer: lukaszp
featuredvideoid: 0tUwn8DHo3s
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: troubleshooting
ms.date: 06/23/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: ef78847829ef292a16856a1597a53c95e7d20708
ms.sourcegitcommit: a453ba52aafa012896f665660df7df7bc117ade5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85486717"
---
# <a name="troubleshoot-sharing-dashboards-and-reports"></a>Résolution des problèmes de partage de tableaux de bord et de rapports

Voici quelques problèmes courants qui peuvent survenir lorsque vous partagez un tableau de bord ou un rapport, ou lorsque quelqu’un d’autre en partage avec vous. 

## <a name="dashboard-recipients-see-a-lock-icon-in-a-tile"></a>Les destinataires du tableau de bord voient une icône de verrou sur une vignette

Les destinataires du partage peuvent voir une vignette verrouillée dans un tableau de bord ou un message « Autorisation requise » lorsqu’ils tentent de consulter un rapport.

![Vignette verrouillée Power BI](media/service-share-dashboards/power-bi-locked_tile_small.png)

Dans ce cas, vous devez leur accorder l’autorisation d’accès au jeu de données sous-jacent.

1. Accédez à l’onglet **Jeux de données** dans votre liste de contenu.

1. Sélectionnez les points de suspension ( **...** ) en regard du jeu de données, puis **Gérer les autorisations**.

    ![Gérer les autorisations](media/service-share-dashboards/power-bi-sharing-manage-permissions.png)

1. Sélectionnez **Ajouter un utilisateur**.

    ![Sélectionnez Ajouter un utilisateur](media/service-share-dashboards/power-bi-share-dataset-add-user.png)

1. Entrez les adresses e-mail complètes des personnes, des groupes de distribution ou des groupes de sécurité. Vous ne pouvez pas effectuer de partage avec des listes de distribution dynamique.

    ![Ajoutez les adresses e-mail](media/service-share-dashboards/power-bi-add-user-dataset.png)

1. Sélectionnez **Ajouter**.

## <a name="i-cant-share-a-dashboard-or-report"></a>Je n’arrive pas à partager un tableau de bord ou un rapport

Pour pouvoir partager un tableau de bord ou un rapport, vous devez être autorisé à en partager le contenu sous-jacent, c’est-à-dire tous les rapports et jeux de données associés. Si un message vous indique que vous ne pouvez pas effectuer le partage, demandez à l’auteur du rapport de vous autoriser à repartager ces rapports et jeux de données.

![Message « Impossible de partager »](media/service-share-dashboards/power-bi-sharing-unable-to-share.png)

## <a name="i-dont-have-access-to-a-dashboard-or-report"></a>Je n’ai pas accès à un tableau de bord ou à un rapport

Si un message « Demander l’accès » s’affiche lorsque vous sélectionnez le lien vers un rapport ou un tableau de bord, c’est le signe que vous ne disposez pas de l’autorisation nécessaire pour l’afficher. Vous devez y [demander accès](service-request-access.md).

## <a name="next-steps"></a>Étapes suivantes

- [Partager des tableaux de bord et des rapports Power BI avec des collègues et d’autres utilisateurs](service-share-dashboards.md)
- [Comment partager des tableaux de bord, rapports et vignettes ?](service-how-to-collaborate-distribute-dashboards-reports.md)
-  [Partager un rapport Power BI filtré](service-share-reports.md)
- Vous avez des questions ? [Essayez la communauté Power BI](https://community.powerbi.com/)
