---
title: Partage direct dans Microsoft Teams à partir du service Power BI
description: Vous pouvez partager des tableaux de bord et des rapports Power BI directement dans Microsoft Teams à partir du service Power BI.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
LocalizationGroup: Share your work
ms.date: 07/31/2020
ms.openlocfilehash: ae3f6b5f3026adf127b53dd07118fe05e4c06a00
ms.sourcegitcommit: 1b3a626c5ca612a7f23058f8e5cc0147a94db51c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94348079"
---
# <a name="share-directly-to-microsoft-teams-from-the-power-bi-service"></a>Partage direct dans Microsoft Teams à partir du service Power BI

Vous pouvez partager des tableaux de bord, des rapports et des visuels Power BI directement dans Microsoft Teams à partir du service Power BI. Utilisez la fonctionnalité **Partager dans Teams** pour démarrer rapidement des conversations quand vous consultez des rapports et des tableaux de bord dans le service Power BI.

## <a name="requirements"></a>Configuration requise

Pour utiliser la fonctionnalité **Partager dans Teams** dans Power BI, vérifiez le paramétrage suivant :

- Les administrateurs Power BI n’ont pas désactivé le paramètre de locataire **Partager dans Teams** dans le portail d’administration Power BI. Ce paramètre permet aux organisations de masquer les boutons **Partager dans Teams**. Consultez l’article sur le [portail d’administration Power BI](../admin/service-admin-portal.md#share-to-teams-tenant-setting) pour plus d’informations.

Pour plus d’informations sur l’interaction entre Power BI et Microsoft Teams, et notamment pour connaître d’autres conditions à remplir, consultez [Collaboration dans Microsoft Teams avec Power BI](service-collaborate-microsoft-teams.md).

## <a name="share-power-bi-content-to-microsoft-teams"></a>Partage de contenu Power BI dans Microsoft Teams

Suivez ces étapes pour partager des liens vers des rapports, des tableaux de bord et des visuels dans le service Power BI dans les conversations et canaux Microsoft Teams.

1. Sélectionnez une de ces options :

   * **Partager dans Teams** dans la barre d’action d’un tableau de bord ou d’un rapport :

       ![Capture d’écran du bouton Partager dans Teams dans la barre d’action](media/service-share-report-teams/service-teams-share-to-teams-action-bar-button.png)
    
   * **Partager dans Teams** dans le menu contextuel d’un visuel spécifique :
    
      ![Capture d’écran du bouton Partager dans Teams dans le menu contextuel d’un visuel](media/service-share-report-teams/service-teams-share-to-teams-visual-context-menu.png)

1. Dans la boîte de dialogue **Partager dans Microsoft Teams**, sélectionnez l’équipe ou le canal qui doit recevoir le lien. Vous pouvez entrer un message si vous le souhaitez. Vous serez peut-être invité à vous connecter au préalable à Microsoft Teams.

    ![Capture d’écran de la boîte de dialogue Partager dans Microsoft Teams avec les informations et le message](media/service-share-report-teams/service-teams-share-to-teams-dialog.png)

1. Sélectionnez **Partager** pour envoyer le lien.
    
1. Le lien est ajouté aux conversations existantes ou démarre une nouvelle conversation.

    ![Capture d’écran de la conversation Microsoft Teams avec un lien vers un élément Power BI](media/service-share-report-teams/service-teams-share-to-teams-deep-link.png)

1. Sélectionnez le lien pour ouvrir l’élément dans le service Power BI.

1. Si vous avez utilisé le menu contextuel pour un objet visuel spécifique, ce dernier est mis en surbrillance à l’ouverture du rapport.

    ![Capture d’écran du rapport Power BI ouvert avec un visuel spécifique mis en surbrillance](media/service-share-report-teams/service-teams-share-to-teams-spotlight-visual.png)


## <a name="known-issues-and-limitations"></a>Problèmes connus et limitations

- Un utilisateur sans licence Power BI ni autorisation d’accès pour le rapport voit un message « Ce contenu n’est pas disponible ».
- Les boutons **Partager dans Teams** peuvent ne pas fonctionner si votre navigateur utilise des paramètres de confidentialité stricts. Utilisez l’option **Vous avez une difficulté ? Essayer d’ouvrir dans une nouvelle fenêtre** si la boîte de dialogue ne s’ouvre pas correctement.
- **Partager dans Teams** n’inclut pas d’aperçu de lien.
- Les aperçus de lien et les boutons **Partager dans Teams** n’accordent pas aux utilisateurs l’autorisation d’afficher l’élément. Les autorisations doivent être gérées séparément.
- Le bouton **Partager dans Teams** n’est pas disponible dans les menus contextuels visuels quand un auteur de rapport définit **Plus d’options** sur **Désactiver** pour le visuel.
- Pour d’autres problèmes, consultez la section [Problèmes connus et limitations](service-collaborate-microsoft-teams.md#known-issues-and-limitations) de l’article « Collaborer dans Microsoft Teams ».

## <a name="next-steps"></a>Étapes suivantes

- [Collaborer dans Microsoft Teams avec Power BI](service-collaborate-microsoft-teams.md)

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
