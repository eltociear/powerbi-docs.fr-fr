---
title: Applets de commande PowerShell, API REST et bibliothèques clientes .NET pour les administrateurs
description: Découvrez les différentes façons d’administrer Power BI via des scripts et des API de programmation.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: e1c95c330687131a29753359f5223e096bddab1d
ms.sourcegitcommit: e9cd61eaa66eda01cc159251d7936a455c55bd84
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "86952613"
---
# <a name="powershell-cmdlets-rest-apis-and-net-client-library-for-power-bi-administration"></a>Applets de commande PowerShell, API REST et bibliothèque cliente .NET pour l’administration de Power BI
Power BI permet aux administrateurs d’écrire les tâches courantes sous forme de scripts à l’aide des applets de commande PowerShell. Il expose aussi les API REST et propose une bibliothèque cliente .NET pour développer des solutions d’administration. Cette rubrique présente une liste d’applets de commande, ainsi que les API et le point de terminaison d’API REST correspondants. Pour plus d’informations, consultez :

- [Téléchargement](https://www.powershellgallery.com/packages/MicrosoftPowerBIMgmt/) et [documentation](https://docs.microsoft.com/powershell/power-bi/overview?view=powerbi-ps) de PowerShell
- [Documentation](https://docs.microsoft.com/rest/api/power-bi/admin) des API REST
- [Téléchargement](https://www.nuget.org/packages/Microsoft.PowerBI.Api/) de la bibliothèque cliente .NET

> Les applets de commande ci-dessous doivent être appelées avec `-Scope Organization` pour fonctionner sur le locataire pour l’administration.

| **Nom de l’applet de commande** | **Alias** | **API** | **Point de terminaison d’API REST** | **Description** |
| --- | --- | --- | --- | --- |
| `Get-PowerBIDatasource` | Non applicable | `Datasets_GetDataSourcesAsAdmin` | /v1.0/myorg/admin/datasets/{datasetkey}/datasources | Obtient les sources de données d’un jeu de données déterminé. |
| `Get-PowerBIDataset` | Non applicable | `Datasets_GetDatasetsAsAdmin` | /v1.0/myorg/admin/datasets | Obtient la liste complète des jeux de données d’un locataire Power BI. |
| `Get-PowerBIWorkspace` | `Get-PowerBIGroup` | `Groups_GetGroupsAsAdmin` | /v1.0/myorg/admin/groups | Obtient la liste complète des espaces de travail d’un locataire Power BI. |
| `Add-PowerBIWorkspaceUser` | `Add-PowerBIGroupUser` | `Groups_AddUserAsAdmin` | /v1.0/myorg/admin/groups/{groupId}/users | Ajoute un utilisateur comme membre d’un espace de travail donné. |
| `Remove-PowerBIWorkspaceUser` | `Remove-PowerBIGroupUser` | `Groups_DeleteUserAsAdmin` | /v1.0/myorg/admin/groups/{groupId}/users/{user} | Supprime un utilisateur de la liste des membres d’un espace de travail donné. |
| `Restore-PowerBIWorkspace` |`Restore-PowerBIGroup` | `Groups_RestoreDeletedGroupAsAdmin` | /v1.0/myorg/admin/groups/{groupId}/restore | Restaure un espace de travail supprimé. |
| `Set-PowerBIWorkspace` |`Set-PowerBIGroup` | `Groups_UpdateGroupAsAdmin` | /v1.0/myorg/admin/groups/{groupId} | Met à jour les propriétés d’un espace de travail donné. |
| `Get-PowerBIDataset -WorkspaceId` | Non applicable | `Groups_GetDatasetsAsAdmin` | /v1.0/myorg/admin/groups/{group\_id}/datasets | Obtient les jeux de données au sein d’un espace de travail donné. |
| `Get-PowerBIReport` | Non applicable | `Reports_GetReportsAsAdmin` | /v1.0/myorg/admin/reports | Obtient la liste complète des rapports d’un locataire Power BI. |
| `Get-PowerBIDashboard` | Non applicable | `Dashboards_GetDashboardsAsAdmin` | /v1.0/myorg/admin/dashboards | Obtient la liste complète des jeux de données d’un locataire Power BI. |
| `Get-PowerBIDashboard -WorkspaceId` | Non applicable | `Groups_GetDashboardsAsAdmin` | /v1.0/myorg/admin/groups/{group\_id}/dashboards | Obtient les tableaux de bord au sein d’un espace de travail donné. |
| `Get-PowerBITile` | `Get-PowerBIDashboardTile` | `Dashboards_GetTilesAsAdmin` | /v1.0/myorg/admin/dashboards/{dashboard\_id}/tiles | Obtient les vignettes d’un tableau de bord donné. |
| `Get-PowerBIReport` | Non applicable | `Groups_GetReportsAsAdmin` | /v1.0/myorg/admin/groups/{group\_id}/reports | Obtient les rapports au sein d’un espace de travail donné. |
| `Get-PowerBIImport` | Non applicable | `Imports_GetImportsAsAdmin` | /v1.0/myorg/admin/imports | Obtient la liste complète des importations d’un locataire Power BI. |
| `Connect-PowerBIServiceAccount` | `Login-PowerBI` &  `Login-PowerBIServiceAccount` | Non applicable | Non applicable | Se connecte à Power BI et démarre une session. |
| `Disconnect-PowerBIServiceAccount` | `Logout-PowerBI` & `Logout-PowerBIServiceAccount` | Non applicable | Non applicable | Se déconnecte de Power BI et ferme la session existante. |
| `Invoke-PowerBIRestMethod`| Non applicable | Non applicable | Non applicable | Envoie des appels d’API REST arbitraires à Power BI. |
| `Get-PowerBIAccessToken`| Non applicable | Non applicable | Non applicable | Obtient le jeton d’accès Power BI dans une session. |
| `Resolve-PowerBIError`| Non applicable | Non applicable | Non applicable | Obtient des informations détaillées sur les erreurs pour les appels d’applet de commande qui n’ont pas abouti. |
