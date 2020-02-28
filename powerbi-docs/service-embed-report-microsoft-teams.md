---
title: Incorporer un rapport avec l’onglet Power BI pour Microsoft Teams
description: Avec l’onglet Power BI pour Microsoft Teams, vous pouvez facilement incorporer des rapports interactifs dans des canaux et des conversations.
author: LukaszPawlowski-MS
ms.author: lukaszp
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
LocalizationGroup: Share your work
ms.date: 01/31/2020
ms.openlocfilehash: fb4846a777dda4787e1ed0be7de869367a616ea5
ms.sourcegitcommit: b22a9a43f61ed7fc0ced1924eec71b2534ac63f3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77530484"
---
# <a name="embed-report-with-the-power-bi-tab-for-microsoft-teams"></a>Incorporer un rapport avec l’onglet Power BI pour Microsoft Teams

Avec l’onglet Power BI mis à jour pour Microsoft Teams, vous pouvez facilement incorporer des rapports interactifs dans les canaux et les conversations Microsoft Teams.

Utilisez l’onglet Power BI pour Microsoft Teams afin d’aider vos collègues à trouver les données que votre équipe utilise et de discuter des données au sein de vos canaux d’équipe.

## <a name="requirements"></a>Configuration requise

Pour que l’**onglet Power BI pour Microsoft Teams** fonctionne, les conditions suivantes sont requises :

- Une licence Power BI Pro, ou le rapport est contenu dans une [capacité Power BI Premium (référence SKU EM ou P)](service-premium-what-is.md) avec une licence Power BI.
- Onglet Power BI pour Microsoft Teams.
- L’utilisateur doit se connecter au service Power BI pour activer sa licence Power BI afin de consommer le rapport.
- L’utilisateur doit avoir l’autorisation d’afficher le rapport.

## <a name="embed-your-report"></a>Incorporer votre rapport
Pour incorporer votre rapport dans un canal ou une conversation Microsoft Teams, ajoutez-le comme décrit ci-dessous.

1. Ouvrez le canal ou la conversation de votre choix dans Microsoft Teams, puis sélectionnez l’icône **+**.

    ![Ajouter un onglet à un canal ou à une conversation](media/service-embed-report-microsoft-teams/service-embed-report-microsoft-teams-add.png)

2. Sélectionnez l’onglet Power BI.

    ![Liste d’onglets Microsoft Teams contenant Power BI](media/service-embed-report-microsoft-teams/service-embed-report-microsoft-teams-tab.png)

3. Utilisez les options fournies pour choisir un rapport à partir d’un espace de travail, de Partagés avec moi ou d’une application Power BI

    ![Paramètres de l’onglet Power BI pour Microsoft Teams](media/service-embed-report-microsoft-teams/service-embed-report-microsoft-teams-tab-settings.png)

4. Le nom de l’onglet est automatiquement mis à jour pour correspondre au nom du rapport, mais vous pouvez le modifier. 

5. Appuyez sur **Enregistrer**.

## <a name="supported-reports"></a>Rapports pris en charge

L’onglet permet d’incorporer les rapports suivants :

- Rapports interactifs et paginés
- Rapports dans Mon espace de travail, la nouvelle expérience d’espace de travail et les espaces de travail classiques
- Rapports dans les applications Power BI


## <a name="grant-access-to-reports"></a>Accorder l’accès aux rapports

L’incorporation d’un rapport dans Microsoft Teams n’accorde pas automatiquement aux utilisateurs l’autorisation d’afficher le rapport : vous devez [autoriser les utilisateurs à afficher le rapport dans Power BI](service-share-dashboards.md). Vous pouvez utiliser un groupe Office 365 pour votre équipe afin de faciliter la tâche. 

> [!IMPORTANT]
> Veillez à passer en revue les utilisateurs qui peuvent afficher le rapport dans le service Power BI et à accorder l’accès à ceux qui ne sont pas répertoriés.

Pour garantir que tous les membres de votre équipe ont accès aux rapports que vous incorporez, vous pouvez les placer dans un seul espace de travail dans Power BI et accorder au groupe Office 365 pour votre équipe l’accès à l’espace de travail.

## <a name="known-issues-and-limitations"></a>Problèmes connus et limitations

- Power BI ne prend pas en charge les mêmes langues localisées que Microsoft Teams. Par conséquent, vous risquez de ne pas voir la localisation appropriée dans le rapport incorporé.
- Les tableaux de bord Power BI ne peuvent pas être incorporés dans l’onglet Power BI pour Microsoft Teams.
- Un utilisateur sans licence Power BI ni autorisation sur le rapport verra le message « Ce contenu n’est pas disponible ».
- Vous pouvez rencontrer des problèmes si vous utilisez Internet Explorer 10. <!--You can look at the [browsers support for Power BI](consumer/end-user-browsers.md) and for [Office 365](https://products.office.com/office-system-requirements#Browsers-section). -->
- Les [filtres d’URL](service-url-filters.md) ne sont pas pris en charge avec l’onglet Power BI pour Microsoft Teams.
- Dans les clouds nationaux, le nouvel onglet Power BI n’est pas disponible, une version plus ancienne peut ne pas prendre en charge la nouvelle expérience d’espace de travail, l’espace de travail ou les rapports dans les applications Power BI. 
- Une fois l’onglet enregistré, son nom ne peut pas être modifié par le biais des paramètres de l’onglet. Utilisez l’option Renommer pour le changer.

## <a name="next-steps"></a>Étapes suivantes
- [Partager un tableau de bord avec vos collègues et les autres utilisateurs](service-share-dashboards.md)  
- [Créer et distribuer une application dans Power BI](service-create-distribute-apps.md)  
- [Qu’est-ce que Power BI Premium ?](service-premium-what-is.md)

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
