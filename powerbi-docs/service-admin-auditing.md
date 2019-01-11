---
title: Utilisation de l’audit dans votre organisation
description: Apprenez à utiliser l’audit avec Power BI pour analyser et examiner les actions effectuées. Vous pouvez utiliser le centre Sécurité et conformité ou utiliser PowerShell.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 11/16/2018
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Administration
ms.openlocfilehash: d9cf6255cfa57790c13ee1fc9d3201860552863b
ms.sourcegitcommit: c09241803664643e1b2ba0c150e525e1262ca466
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54072356"
---
# <a name="using-auditing-within-your-organization"></a>Utilisation de l’audit dans votre organisation

Il est important de savoir qui effectue une action sur un élément donné de votre abonné Power BI, afin de permettre à votre entreprise de répondre à ses exigences, notamment en matière de conformité réglementaire et de gestion des enregistrements. Utilisez l’audit Power BI pour auditer les actions effectuées par les utilisateurs, comme « Voir le rapport » et « Voir le tableau de bord ». Vous ne pouvez pas utiliser l’audit pour auditer les autorisations.

Utilisez l’audit dans le Centre de sécurité et de conformité Office 365 ou PowerShell. L’audit s’appuie sur des fonctionnalités d’Exchange Online, qui est automatiquement configuré de façon à prendre en charge Power BI.

Vous pouvez filtrer les données d’audit par période, utilisateur, tableau de bord, rapport, jeu de données et type d’activité. Vous pouvez également télécharger les activités dans un fichier .csv (valeurs séparées par des virgules) pour les analyser hors connexion.

## <a name="requirements"></a>Configuration requise

Vous devez respecter ces exigences suivantes pour accéder aux journaux d’audit :

* Vous devez être administrateur général ou avoir le rôle Journaux d’audit ou Journaux d’audit en affichage seul dans Exchange Online pour pouvoir accéder au journal d’audit. Par défaut, ces rôles sont affectés aux groupes de rôles Gestion de la conformité et Gestion de l’organisation sur la page **Autorisations** du Centre d’administration Exchange.

    Pour donner accès au journal d’audit à des comptes non administrateurs, vous devez ajouter l’utilisateur à la liste des membres de l’un de ces groupes de rôles. L’autre possibilité consiste à créer un groupe de rôles personnalisé dans le Centre d’administration Exchange, à affecter à ce groupe le rôle Journaux d’audit ou Journaux d’audit en affichage seul, puis à ajouter le compte non administrateur au nouveau groupe de rôles. Pour plus d’informations, voir [Gérer les groupes de rôles dans Exchange Online](/Exchange/permissions-exo/role-groups).

    Si vous ne pouvez pas accéder au Centre d’administration Exchange à partir du Centre d’administration Office 365, accédez à https://outlook.office365.com/ecp et connectez-vous avec vos informations d’identification.

* Si vous avez accès au journal d’audit, mais que vous n’êtes ni un administrateur général ni un administrateur de service Power BI, vous n’avez pas accès au portail d’administration de Power BI. Dans ce cas, vous devez utiliser un lien direct vers le [Centre de sécurité et conformité Office 365](https://sip.protection.office.com/#/unifiedauditlog).

## <a name="accessing-your-audit-logs"></a>Accès à vos journaux d’audit

Pour accéder aux journaux, commencez par vérifier que la journalisation est activée dans Power BI. Pour plus d’informations, consultez [Journaux d’audit](service-admin-portal.md#audit-logs) dans la documentation du portail d’administration. Une fois que vous avez activé l’audit, le délai avant de pouvoir voir les données d’audit peut aller jusqu’à 48 heures. Si vous ne voyez immédiatement les données, consultez les journaux d’audit plus tard. Le délai est sensiblement le même entre le moment où vous obtenez l’autorisation de voir les journaux d’audit et le moment où vous pouvez réellement y accéder.

Les journaux d’audit de Power BI sont disponibles directement dans le [Centre Sécurité et conformité Office 365](https://sip.protection.office.com/#/unifiedauditlog). Vous trouverez également un lien dans le portail d’administration Power BI :

1. Dans Power BI, sélectionnez l’icône d’**engrenage** en haut à droite, puis **Portail d’administration**.

   ![Portail d’administration](media/service-admin-auditing/powerbi-admin.png)

1. Sélectionnez **Journaux d’audit**.

1. Sélectionnez **Accéder au Centre d’administration O365**.

   ![Accéder au Centre d’administration O365](media/service-admin-auditing/audit-log-o365-admin-center.png)

## <a name="search-only-power-bi-activities"></a>Rechercher des activités Power BI uniquement

Limitez les résultats aux seules activités Power BI en suivant ces étapes. Pour la liste des activités, consultez la [liste des activités auditées par Power BI](#list-of-activities-audited-by-power-bi) plus loin dans cet article.

1. Dans la page **Recherche dans le journal d’audit**, sous **Recherche**, sélectionnez la liste déroulante **Activités**.

2. Sélectionnez **Activités Power BI**.

   ![Recherche dans le journal d’audit](media/service-admin-auditing/audit-log-search-filter-by-powerbi.png)

3. Sélectionnez n’importe quel emplacement en dehors de la zone de sélection pour la fermer.

Vos recherches sont maintenant filtrées aux seules activités Power BI.

## <a name="search-the-audit-logs-by-date"></a>Rechercher les journaux d’audit par date

Vous pouvez rechercher dans les journaux par plage de dates à l’aide des champs **Date de début** et **Date de fin**. Les sept derniers jours sont sélectionnés par défaut. La date et l’heure sont présentées au format UTC (temps universel coordonné). La période maximale que vous pouvez spécifier est de 90 jours. 

Une erreur s’affiche si la période sélectionnée est supérieure à 90 jours. Si vous utilisez la période maximale de 90 jours, sélectionnez l’heure actuelle comme **Date de début**. Sinon, vous recevez une erreur indiquant que la date de début est antérieure à la date de fin. Si vous avez activé l’audit dans les 90 derniers jours, la plage de dates ne peut pas commencer avant la date à laquelle l’audit a été activé.

![Rechercher par date](media/service-admin-auditing/search-audit-log-by-date.png)

## <a name="search-the-audit-logs-by-users"></a>Rechercher les journaux d’audit par utilisateur

Vous pouvez rechercher des entrées du journal d’audit pour les activités effectuées par des utilisateurs spécifiques. Pour ce faire, entrez un ou plusieurs noms d’utilisateur dans le champ **Utilisateurs**. Le nom d’utilisateur ressemble à une adresse e-mail ; il s’agit du compte avec lequel les utilisateurs se connectent à Power BI. Laissez cette zone vide afin de renvoyer les entrées pour tous les utilisateurs (et les comptes de service) de votre organisation.

![Rechercher par utilisateurs](media/service-admin-auditing/search-audit-log-by-user.png)

## <a name="view-search-results"></a>Afficher les résultats de recherche

Une fois que vous avez sélectionné **Rechercher**, les résultats de recherche se chargent et s’affichent quelques secondes plus tard sous **Résultats**. Lorsque la recherche est terminée, le nombre de résultats s’affiche. Un maximum de 1 000 événements s’affichent. Si plus de 1 000 événements correspondent aux critères de recherche, les 1 000 événements les plus récents apparaissent.

### <a name="view-the-main-results"></a>Afficher les principaux résultats

La zone **Résultats** contient les informations suivantes sur chaque événement retourné par la recherche. Sélectionnez un en-tête de colonne sous **Résultats** pour trier les résultats.

| **Colonne** | **Définition** |
| --- | --- |
| Date |Date et heure (au format UTC) auxquelles l’événement s’est produit. |
| Adresse IP |L’adresse IP de l’appareil utilisé lors de l’enregistrement de l’activité. L’adresse IP est affichée au format d’adresse IPv4 ou IPv6. |
| Utilisateur |L’utilisateur (ou compte de service) qui a effectué l’action qui a déclenché l’événement. |
| Activité |L’activité exécutée par l’utilisateur. Cette valeur correspond aux activités que vous avez sélectionnées dans la liste déroulante **Activités**. Pour un événement du journal d’audit d’administrateur Exchange, la valeur de cette colonne est une cmdlet Exchange. |
| Élément |L’objet créé ou modifié à la suite de l’activité correspondante. Par exemple, le fichier affiché ou modifié ou le compte utilisateur mis à jour. Seule une partie des activités a une valeur dans cette colonne. |
| Détails |Détails supplémentaires sur une activité. Là encore, seule une partie des activités a une valeur. |

### <a name="view-the-details-for-an-event"></a>Afficher les détails d’un événement

Vous pouvez afficher plus de détails sur un événement en cliquant sur l’enregistrement de l’événement dans la liste des résultats de recherche. La page **Détails** qui s’affiche contient les propriétés détaillées de l’enregistrement de l’événement. Les propriétés affichées dépendent du service Office 365 dans lequel l’événement se produit. 

Pour afficher ces détails, sélectionnez **Plus d’informations**. Toutes les entrées Power BI ont une valeur de 20 pour la propriété RecordType. Pour plus d’informations sur les autres propriétés, consultez [Propriétés détaillées dans le journal d’audit](/office365/securitycompliance/detailed-properties-in-the-office-365-audit-log/).

   ![Détails de l’audit](media/service-admin-auditing/audit-details.png)

## <a name="export-search-results"></a>Exporter les résultats de recherche

Pour exporter le journal d’audit Power BI dans un fichier .csv, suivez ces étapes.

1. Sélectionnez **Exporter les résultats**.

1. Sélectionnez **Enregistrer les résultats chargés** ou **Télécharger tous les résultats**.

    ![Exporter les résultats](media/service-admin-auditing/export-auditing-results.png)

## <a name="use-powershell-to-search-audit-logs"></a>Utiliser PowerShell pour rechercher dans les journaux d’audit

Vous pouvez aussi utiliser PowerShell pour accéder aux journaux d’audit en fonction de votre connexion. L’exemple suivant montre comment se connecter à Exchange Online PowerShell, puis utiliser la commande [Search-UnifiedAuditLog](/powershell/module/exchange/policy-and-compliance-audit/search-unifiedauditlog?view=exchange-ps/) pour extraire les entrées du journal d’audit Power BI. Pour exécuter le script, vous devez avoir les autorisations nécessaires, qui sont décrites dans la section [Exigences](#requirements).

```powershell
Set-ExecutionPolicy RemoteSigned

$UserCredential = Get-Credential

$Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection

Import-PSSession $Session
Search-UnifiedAuditLog -StartDate 9/11/2018 -EndDate 9/15/2018 -RecordType PowerBI -ResultSize 1000 | Format-Table | More
```

Pour plus d’informations sur la connexion à Exchange Online, consultez [Se connecter à Exchange Online PowerShell](/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell/). Pour un autre exemple d’utilisation de PowerShell avec les journaux d’audit, consultez [Utilisation du journal d’audit Power BI et de PowerShell pour attribuer des licences Power BI Pro](https://powerbi.microsoft.com/blog/using-power-bi-audit-log-and-powershell-to-assign-power-bi-pro-licenses/).

## <a name="activities-audited-by-power-bi"></a>Activités auditées par Power BI

Les activités suivantes sont auditées par Power BI.

| Nom convivial                                     | Nom de l’opération                              | Notes                                  |
|---------------------------------------------------|---------------------------------------------|------------------------------------------|
| Source de données ajoutée à la passerelle Power BI             | AddDatasourceToGateway                      |                                          |
| Accès au dossier Power BI ajouté                      | AddFolderAccess                             | Non utilisée actuellement                       |
| Membres ajoutés au groupe Power BI                      | AddGroupMembers                             |                                          |
| Compte de stockage de dataflow attaché au locataire par l’administrateur | AdminAttachedDataflowStorageAccountToTenant | Non utilisée actuellement                       |
| Jeu de données Power BI analysé                         | AnalyzedByExternalApplication               |                                          |
| Rapport Power BI analysé                          | AnalyzeInExcel                              |                                          |
| Jeu de données Power BI lié à la passerelle                | BindToGateway                               |                                          |
| État de la capacité modifié                            | ChangeCapacityState                         |                                          |
| Affectation d’utilisateurs de capacité modifiée                  | UpdateCapacityUsersAssignment               |                                          |
| Connexions de jeu de données Power BI modifiées              | SetAllConnections                           |                                          |
| Administrateurs de passerelle Power BI modifiés                   | ChangeGatewayAdministrators                 |                                          |
| Modification des utilisateurs de la source de données de la passerelle Power BI        | ChangeGatewayDatasourceUsers                |                                          |
| Pack de contenu d’organisation Power BI créé      | CreateOrgApp                                |                                          |
| Application Power BI créée                              | CreateApp                                   |                                          |
| Tableau de bord Power BI créé                        | CreateDashboard                             |                                          |
| Dataflow Power BI créé                         | CreateDataflow                              |                                          |
| Jeu de données Power BI créé                          | CreateDataset                               |                                          |
| Abonnement à l’e-mail Power BI créé               | CreateEmailSubscription                     |                                          |
| Dossier Power BI créé                           | CreateFolder                                |                                          |
| Passerelle Power BI créée                          | CreateGateway                               |                                          |
| Groupe Power BI créé                            | CreateGroup                                 |                                          |
| Rapport Power BI créé                           | CreateReport                                |                                          |
| Dataflow migré vers un compte de stockage externe     | DataflowMigratedToExternalStorageAccount    | Non utilisée actuellement                       |
| Autorisations de dataflow ajoutées                        | DataflowPermissionsAdded                    | Non utilisée actuellement                       |
| Autorisations de dataflow supprimées                      | DataflowPermissionsRemoved                  | Non utilisée actuellement                       |
| Pack de contenu d’organisation Power BI supprimé      | DeleteOrgApp                                |                                          |
| Commentaire Power BI supprimé                          | DeleteComment                               |                                          |
| Tableau de bord Power BI supprimé                        | DeleteDashboard                             | Non utilisée actuellement                       |
| Dataflow Power BI supprimé                         | DeleteDataflow                              | Non utilisée actuellement                       |
| Jeu de données Power BI supprimé                          | DeleteDataset                               |                                          |
| Abonnement à l’e-mail Power BI supprimé               | DeleteEmailSubscription                     |                                          |
| Dossier Power BI supprimé                           | DeleteFolder                                |                                          |
| Accès au dossier Power BI supprimé                    | DeleteFolderAccess                          | Non utilisée actuellement                       |
| Passerelle Power BI supprimée                          | DeleteGateway                               |                                          |
| Groupe Power BI supprimé                            | DeleteGroup                                 |                                          |
| Rapport Power BI supprimé                           | DeleteReport                                |                                          |
| Sources de données de jeu de données Power BI détectées          | GetDatasources                              |                                          |
| Rapport Power BI téléchargé                        | DownloadReport                              |                                          |
| Autorisation de certification Power BI modifiée          | EditCertificationPermission                 | Non utilisée actuellement                       |
| Tableau de bord Power BI modifié                         | EditDashboard                               | Non utilisée actuellement                       |
| Jeu de données Power BI modifié                           | EditDataset                                 |                                          |
| Propriétés du jeu de données Power BI modifiées                | EditDatasetProperties                       | Non utilisée actuellement                       |
| Rapport Power BI modifié                            | EditReport                                  |                                          |
| Dataflow Power BI exporté                        | ExportDataflow                              |                                          |
| Données des visuels de rapport Power BI exportées              | ExportReport                                |                                          |
| Données de vignette Power BI exportées                       | ExportTile                                  |                                          |
| Échec de l’ajout d’autorisations de dataflow                | FailedToAddDataflowPermissions              | Non utilisée actuellement                       |
| Échec de la suppression d’autorisations de dataflow             | FailedToRemoveDataflowPermissions           | Non utilisée actuellement                       |
| Jeton SAS de dataflow Power BI généré             | GenerateDataflowSasToken                    |                                          |
| Jeton d’incorporation Power BI généré                    | GenerateEmbedToken                          |                                          |
| Fichier importé dans Power BI                         | Importer                                      |                                          |
| Application Power BI installée                            | InstallApp                                  |                                          |
| Espace de travail migré vers une capacité                  | MigrateWorkspaceIntoCapacity                |                                          |
| Commentaire Power BI publié                           | PostComment                                 |                                          |
| Tableau de bord Power BI imprimé                        | PrintDashboard                              |                                          |
| Page de rapport Power BI imprimée                      | PrintReport                                 |                                          |
| Rapport Power BI publié sur le web                  | PublishToWebReport                          |                                          |
| Secret de dataflow Power BI reçu du coffre de clés  | ReceiveDataflowSecretFromKeyVault           | Non utilisée actuellement                       |
| Source de données supprimée de la passerelle Power BI         | RemoveDatasourceFromGateway                 |                                          |
| Membres supprimés du groupe Power BI                    | DeleteGroupMembers                          |                                          |
| Espace de travail supprimé d’une capacité                 | RemoveWorkspacesFromCapacity                |                                          |
| Tableau de bord Power BI renommé                        | RenameDashboard                             |                                          |
| Actualisation demandée du dataflow Power BI               | RequestDataflowRefresh                      | Non utilisée actuellement                       |
| Actualisation demandée du jeu de données Power BI                | RefreshDataset                              |                                          |
| Espaces de travail Power BI récupérés                     | GetWorkspaces                               |                                          |
| Actualisation planifiée sur le dataflow Power BI définie        | SetScheduledRefreshOnDataflow               |                                          |
| Actualisation planifiée sur le jeu de données Power BI définie         | SetScheduledRefresh                         |                                          |
| Tableau de bord Power BI partagé                         | ShareDashboard                              |                                          |
| Rapport Power BI partagé                            | ShareReport                                 |                                          |
| Essai gratuit étendu de Power BI démarré                   | OptInForExtendedProTrial                    | Non utilisée actuellement                       |
| Essai Power BI démarré                            | OptInForProTrial                            |                                          |
| Prise de contrôle d’une source de données Power BI                   | TakeOverDatasource                          |                                          |
| Prise de contrôle d’un jeu de données Power BI                        | TakeOverDataset                             |                                          |
| Application Power BI dépubliée                          | UnpublishApp                                |                                          |
| Mettre à jour les paramètres de gouvernance des ressources de capacité      | UpdateCapacityResourceGovernanceSettings    | Actuellement pas présent dans le portail d’administration Office 365 |
| Administrateur de capacité mis à jour                            | UpdateCapacityAdmins                        |                                          |
| Nom d’affichage de capacité mis à jour                     | UpdateCapacityDisplayName                   |                                          |
| Paramètres Power BI de l’organisation mis à jour          | UpdatedAdminFeatureSwitch                   |                                          |
| Application Power BI mise à jour                              | UpdateApp                                   |                                          |
| Dataflow Power BI mis à jour                         | UpdateDataflow                              |                                          |
| Sources de données de jeu de données Power BI mises à jour             | UpdateDatasources                           |                                          |
| Paramètres de jeu de données Power BI mis à jour               | UpdateDatasetParameters                     |                                          |
| Abonnement à l’e-mail Power BI mis à jour               | UpdateEmailSubscription                     |                                          |
| Dossier Power BI mis à jour                           | UpdateFolder                                |                                          |
| Accès au dossier Power BI mis à jour                    | UpdateFolderAccess                          |                                          |
| Informations d’identification de la source de données de passerelle Power BI mises à jour  | UpdateDatasourceCredentials                 |                                          |
| Tableau de bord Power BI affiché                         | ViewDashboard                               |                                          |
| Dataflow Power BI affiché                          | ViewDataflow                                |                                          |
| Rapport Power BI affiché                            | ViewReport                                  |                                          |
| Vignette Power BI affichée                              | ViewTile                                    |                                          |
| Métriques d’utilisation de Power BI affichées                     | ViewUsageMetrics                            |                                          |
|                                                   |                                             |                                          |

## <a name="next-steps"></a>Étapes suivantes

[Présentation de l’administration de Power BI](service-admin-administering-power-bi-in-your-organization.md)  

[Portail d’administration Power BI](service-admin-portal.md)  

D’autres questions ? [Essayez d’interroger la communauté Power BI](http://community.powerbi.com/)
