---
title: Collaborer dans Microsoft Teams avec Power BI
description: Vous pouvez facilement partager du contenu Power BI interactif et collaborer sur celui-ci dans les canaux et conversations Microsoft Teams.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
LocalizationGroup: Share your work
ms.date: 07/22/2020
ms.openlocfilehash: 17a0879dac416a98d214ed11861947cb2c311487
ms.sourcegitcommit: 65025ab7ae57e338bdbd94be795886e5affd45b4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87253989"
---
# <a name="collaborate-in-microsoft-teams-with-power-bi"></a>Collaborer dans Microsoft Teams avec Power BI

Vous disposez de plusieurs options pour partager du contenu Power BI interactif et collaborer sur celui-ci dans les canaux et conversations Microsoft Teams. 

- Avec l’onglet **Power BI** pour Microsoft Teams, vous pouvez [incorporer des rapports interactifs dans les canaux et les conversations Microsoft Teams](service-embed-report-microsoft-teams.md). L’onglet **Power BI** aide vos collègues à trouver les données de votre équipe et à discuter des données dans les canaux de votre équipe. 
- Créez un [aperçu de lien](service-teams-link-preview.md) quand vous collez un lien vers vos rapports, tableaux de bord et applications dans la boîte de message Microsoft Teams. L’aperçu de lien montre des informations sur le lien. 
- Utilisez [Partager dans Teams](service-share-report-teams.md) quand vous consultez des rapports et des tableaux de bord dans le service Power BI pour démarrer rapidement des conversations dans Teams.
 
:::image type="content" source="media/service-collaborate-microsoft-teams/power-bi-embed-teams-report.png" alt-text="Capture d’écran d’un rapport Power BI incorporé dans un canal Teams":::

## <a name="requirements"></a>Configuration requise

En général, pour que Power BI fonctionne dans Microsoft Teams, vérifiez les éléments suivants :

- Vos utilisateurs ont une licence Power BI Pro ou que le rapport est contenu dans une [capacité Power BI Premium (référence SKU EM ou P)](../admin/service-premium-what-is.md) avec une licence Power BI.
- Les utilisateurs se sont connectés au service Power BI pour activer leur licence Power BI.
- Les utilisateurs remplissent les conditions requises pour utiliser l’onglet **Power BI** dans Microsoft Teams.

Pour utiliser l’onglet **Power BI** dans Microsoft Teams, vérifiez les éléments suivants :

- Microsoft Teams a l’onglet **Power BI**.
- Pour ajouter un rapport dans Microsoft Teams avec l’onglet **Power BI**, vous disposez au moins du rôle Lecteur dans l’espace de travail qui héberge le rapport. Pour plus d’informations sur les différents rôles, consultez [Rôles dans les nouveaux espaces de travail](service-new-workspaces.md#roles-in-the-new-workspaces).
- Pour afficher le rapport sous l’onglet **Power BI** dans Microsoft Teams, les utilisateurs doivent être autorisés à visualiser le rapport.
- Les utilisateurs doivent être des utilisateurs de Microsoft Teams ayant accès aux canaux et aux conversations.

Pour utiliser la fonctionnalité **Partager dans Teams** dans Power BI, vérifiez le paramétrage suivant :

- Les administrateurs Power BI n’ont pas désactivé le paramètre de locataire **Partager dans Teams** dans le portail d’administration Power BI. Ce paramètre permet aux organisations de masquer les boutons **Partager dans Teams**. Consultez l’article sur le [portail d’administration Power BI](../admin/service-admin-portal.md#share-to-teams-tenant-setting) pour plus d’informations.

## <a name="grant-access-to-reports"></a>Accorder l’accès aux rapports

L’incorporation d’un rapport dans Microsoft Teams ou l’envoi d’un lien vers un élément n’accorde pas automatiquement aux utilisateurs l’autorisation d’afficher le rapport. Vous devez [permettre aux utilisateurs d’afficher le rapport dans Power BI](service-share-dashboards.md). Vous pouvez utiliser un groupe Microsoft 365 pour votre équipe afin de faciliter la tâche.

> [!IMPORTANT]
> Veillez à passer en revue les utilisateurs qui peuvent afficher le rapport dans le service Power BI et à accorder l’accès à ceux qui ne sont pas répertoriés.

Pour garantir que tous les membres d’une équipe ont accès aux rapports, vous pouvez les placer dans un même espace de travail et accorder au groupe Microsoft 365 pour votre équipe l’accès.

## <a name="known-issues-and-limitations"></a>Problèmes connus et limitations

- Power BI ne prend pas en charge les mêmes langues localisées que Microsoft Teams. Par conséquent, vous risquez de ne pas voir la localisation appropriée dans le rapport incorporé.
- Les tableaux de bord Power BI ne peuvent pas être incorporés dans l’onglet **Power BI** pour Microsoft Teams.
- Un utilisateur sans licence Power BI ni autorisation d’accès pour le rapport voit un message « Ce contenu n’est pas disponible ».
- Vous pourriez rencontrer des problèmes si vous utilisez Internet Explorer 10. <!--You can look at the [browsers support for Power BI](../consumer/end-user-browsers.md) and for [Microsoft 365](https://products.office.com/office-system-requirements#Browsers-section). -->
- Les [filtres d’URL](service-url-filters.md) ne sont pas pris en charge avec l’onglet **Power BI** pour Microsoft Teams.
- Dans les clouds nationaux, le nouvel onglet **Power BI** n’est pas disponible. Une version plus ancienne peut être disponible, qui ne prend pas en charge la nouvelle expérience ni les rapports dans les applications Power BI.
- Une fois que vous avez enregistré l’onglet, vous ne pouvez pas changer son nom via les paramètres des onglets. Utilisez l’option **Renommer** pour le changer.
- L’authentification unique n’est pas prise en charge pour le service d’aperçu de lien.
- Les aperçus de lien ne fonctionnent pas dans les conversations des réunions ni dans les canaux privés.

## <a name="next-steps"></a>Étapes suivantes

- [Incorporer du contenu Power BI dans Microsoft Teams](service-embed-report-microsoft-teams.md)
- [Obtenir un aperçu de lien Power BI dans Microsoft Teams](service-teams-link-preview.md)
- [Partager directement dans Teams à partir du service Power BI](service-share-report-teams.md)

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
