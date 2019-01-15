---
title: Applets de commande PowerShell, API REST et kit de développement logiciel (SDK) .NET pour les administrateurs
description: Découvrez les différentes façons d’administrer Power BI via des scripts et des API de programmation.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: overview
ms.date: 06/25/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 86a90396c82a597e8b4f535b71e029bfa21328a4
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/15/2019
ms.locfileid: "54280900"
---
# <a name="powershell-cmdlets-rest-apis-and-net-sdk-for-power-bi-administration"></a>Applets de commande PowerShell, API REST et kit SDK .NET pour l’administration de Power BI
Power BI permet aux administrateurs d’écrire les tâches courantes sous forme de scripts à l’aide des applets de commande PowerShell. Il expose aussi les API REST et propose un kit SDK .NET pour développer des solutions d’administration. Cette rubrique présente une liste d’applets de commande, ainsi que la méthode SDK et le point de terminaison d’API REST correspondants. Pour plus d’informations, consultez :

- [Téléchargement](https://www.powershellgallery.com/packages/MicrosoftPowerBIMgmt/) et [documentation](https://docs.microsoft.com/powershell/power-bi/overview?view=powerbi-ps) de PowerShell
- [Documentation](https://docs.microsoft.com/rest/api/power-bi/admin) des API REST
- [Téléchargement ](https://www.nuget.org/packages/Microsoft.PowerBI.Api/)du kit SDK .NET

> Les applets de commande ci-dessous doivent être appelées avec `-Scope Organization` pour fonctionner sur le locataire pour l’administration.

| **Nom de l’applet de commande** | **Alias** | **Méthode SDK** | **Point de terminaison d’API REST** | **Description** |
| --- | --- | --- | --- | --- |
| `Get-PowerBIDatasource` | N/A | `Datasets_GetDataSourcesAsAdmin` | /v1.0/myorg/admin/datasets/{datasetkey}/datasources | Obtient les sources de données d’un jeu de données déterminé. |
| `Get-PowerBIDataset` | N/A | `Datasets_GetDatasetsAsAdmin` | /v1.0/myorg/admin/datasets | Obtient la liste complète des jeux de données d’un locataire Power BI. |
| `Get-PowerBIWorkspace` | `Get-PowerBIGroup` | `Groups_GetGroupsAsAdmin` | /v1.0/myorg/admin/groups | Obtient la liste complète des espaces de travail d’un locataire Power BI. |
| `Add-PowerBIWorkspaceUser` | `Add-PowerBIGroupUser` | `Groups_AddUserAsAdmin` | /v1.0/myorg/admin/groups/{groupId}/users | Ajoute un utilisateur comme membre d’un espace de travail donné. |
| `Remove-PowerBIWorkspaceUser` | `Remove-PowerBIGroupUser` | `Groups_DeleteUserAsAdmin` | /v1.0/myorg/admin/groups/{groupId}/users/{user} | Supprime un utilisateur de la liste des membres d’un espace de travail donné. |
| `Restore-PowerBIWorkspace` |`Restore-PowerBIGroup` | `Groups_RestoreDeletedGroupAsAdmin` | /v1.0/myorg/admin/groups/{groupId}/restore | Restaure un espace de travail supprimé. |
| `Set-PowerBIWorkspace` |`Set-PowerBIGroup` | `Groups_UpdateGroupAsAdmin` | /v1.0/myorg/admin/groups/{groupId} | Met à jour les propriétés d’un espace de travail donné. |
| `Get-PowerBIDataset -WorkspaceId` | N/A | `Groups_GetDatasetsAsAdmin` | /v1.0/myorg/admin/groups/{group\_id}/datasets | Obtient les jeux de données au sein d’un espace de travail donné. |
| `Get-PowerBIReport` | N/A | `Reports_GetReportsAsAdmin` | /v1.0/myorg/admin/reports | Obtient la liste complète des rapports d’un locataire Power BI. |
| `Get-PowerBIDashboard` | N/A | `Dashboards_GetDashboardsAsAdmin` | /v1.0/myorg/admin/dashboards | Obtient la liste complète des jeux de données d’un locataire Power BI. |
| `Get-PowerBIDashboard -WorkspaceId` | N/A | `Groups_GetDashboardsAsAdmin` | /v1.0/myorg/admin/groups/{group\_id}/dashboards | Obtient les tableaux de bord au sein d’un espace de travail donné. |
| `Get-PowerBITile` | `Get-PowerBIDashboardTile` | `Dashboards_GetTilesAsAdmin` | /v1.0/myorg/admin/dashboards/{dashboard\_id}/tiles | Obtient les vignettes d’un tableau de bord donné. |
| `Get-PowerBIReport` | N/A | `Groups_GetReportsAsAdmin` | /v1.0/myorg/admin/groups/{group\_id}/reports | Obtient les rapports au sein d’un espace de travail donné. |
| `Get-PowerBIImport` | N/A | `Imports_GetImportsAsAdmin` | /v1.0/myorg/admin/imports | Obtient la liste complète des importations d’un locataire Power BI. |
| `Connect-PowerBIServiceAccount` | `Login-PowerBI` &  `Login-PowerBIServiceAccount` | N/A | N/A | Se connecte à Power BI et démarre une session. |
| `Disconnect-PowerBIServiceAccount` | `Logout-PowerBI` & `Logout-PowerBIServiceAccount` | N/A | N/A | Se déconnecte de Power BI et ferme la session existante. |
| `Invoke-PowerBIRestMethod`| N/A | N/A | N/A | Envoie des appels d’API REST arbitraires à Power BI. |
| `Get-PowerBIAccessToken`| N/A | N/A | N/A | Obtient le jeton d’accès Power BI dans une session. |
| `Resolve-PowerBIError`| N/A | N/A | N/A | Obtient des informations détaillées sur les erreurs pour les appels d’applet de commande qui n’ont pas abouti. |
