---
title: Utilisez l’audit au sein de votre organisation
description: Apprenez à utiliser l’audit avec Power BI pour analyser et examiner les actions effectuées. Vous pouvez utiliser le centre Sécurité et conformité ou utiliser PowerShell.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/23/2019
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Administration
ms.openlocfilehash: 559ff45974274420e2545228720000359d5fe971
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "64906775"
---
# <a name="use-auditing-within-your-organization"></a>Utilisez l’audit au sein de votre organisation

Savoir qui est effectue une action sur un élément dans votre Power BI locataire peut être essentiel en aidant votre entreprise à répondre à ses exigences, telles que la conformité aux réglementations de collaboration et de gestion des enregistrements. Utiliser Power BI l’audit pour auditer les actions effectuées par des utilisateurs, comme « Afficher le rapport » et « Afficher le tableau de bord ». Vous ne pouvez pas utiliser l’audit pour auditer les autorisations.

Utilisez l’audit dans le Centre de sécurité et de conformité Office 365 ou PowerShell. L’audit s’appuie sur des fonctionnalités d’Exchange Online, qui est automatiquement configuré de façon à prendre en charge Power BI.

Vous pouvez filtrer les données d’audit par plage de dates, utilisateur, tableau de bord, rapports, jeu de données et type d’activité. Vous pouvez également télécharger les activités dans un fichier csv (valeur séparée par des virgules) pour analyser en mode hors connexion.

## <a name="requirements"></a>Configuration requise

Vous devez respecter ces exigences suivantes pour accéder aux journaux d’audit :

* Vous devez être un administrateur global ou attribuer le rôle de journaux d’Audit ou des journaux d’Audit d’affichage seul dans Exchange en ligne pour accéder au journal d’audit. Par défaut, les groupes de rôles de gestion de la conformité et de gestion de l’organisation fournis avec ces rôles sur le **autorisations** page dans le centre d’administration Exchange.

    Pour fournir des comptes non administrateurs avec accès au journal d’audit, vous devez ajouter l’utilisateur en tant que membre de l’un de ces groupes de rôles. Si vous souhaitez faire une autre manière, vous pouvez créer un groupe de rôles personnalisés dans le centre d’administration Exchange, attribuer le rôle journaux d’Audit ou des journaux d’Audit d’Affichage seul à ce groupe, puis ajoutez le compte non administrateur pour le nouveau groupe de rôles. Pour plus d’informations, voir [Gérer les groupes de rôles dans Exchange Online](/Exchange/permissions-exo/role-groups).

    Si vous ne pouvez pas accéder au Centre d’administration Exchange à partir du centre d’administration Microsoft 365, accédez à https://outlook.office365.com/ecp et connectez-vous avec vos informations d’identification.

* Si vous avez accès au journal d’audit, mais ne sont pas un administrateur général ou un administrateur de Service Power BI, vous n’avez pas accès au portail d’administration Power BI. Dans ce cas, vous devez utiliser un lien direct vers le [Centre de sécurité et conformité Office 365](https://sip.protection.office.com/#/unifiedauditlog).

## <a name="access-your-audit-logs"></a>Accéder à vos journaux d’audit

Pour accéder aux journaux, tout d’abord veillez à activer la journalisation dans Power BI. Pour plus d’informations, consultez [Journaux d’audit](service-admin-portal.md#audit-logs) dans la documentation du portail d’administration. Il peut y avoir jusqu'à un délai de 48 heures entre le moment où que vous activez l’audit, et lorsque vous pouvez afficher les données d’audit. Si vous ne voyez immédiatement les données, consultez les journaux d’audit plus tard. Le délai est sensiblement le même entre le moment où vous obtenez l’autorisation de voir les journaux d’audit et le moment où vous pouvez réellement y accéder.

Les journaux d’audit de Power BI sont disponibles directement dans le [Centre Sécurité et conformité Office 365](https://sip.protection.office.com/#/unifiedauditlog). Il existe également un lien à partir du portail d’administration Power BI :

1. Dans Power BI, sélectionnez le **icône d’engrenage** dans le coin supérieur droit, puis sélectionnez **portail d’administration**.

   ![Capture d’écran du menu déroulant ENGRENAGE avec l’option portail Admin exigées.](media/service-admin-auditing/powerbi-admin.png)

1. Sélectionnez **Journaux d’audit**.

1. Sélectionnez **Accéder au Centre d’administration O365**.

   ![Capture d’écran du portail d’administration avec l’Audit consigne option et passez aux options du centre d’administration Microsoft Office 365 appelées.](media/service-admin-auditing/audit-log-o365-admin-center.png)

## <a name="search-only-power-bi-activities"></a>Rechercher des activités Power BI uniquement

Limitez les résultats aux seules activités Power BI en suivant ces étapes. Pour la liste des activités, consultez la liste des [activités auditées par Power BI](#activities-audited-by-power-bi) plus loin dans cet article.

1. Sur le **recherche dans les journaux d’Audit** page sous **recherche**, sélectionnez la liste déroulante pour **activités**.

2. Sélectionnez **Activités Power BI**.

   ![Recherche de journal de capture d’écran de l’Audit des activités Power BI appelé.](media/service-admin-auditing/audit-log-search-filter-by-powerbi.png)

3. Sélectionnez n’importe quel emplacement en dehors de la zone de sélection pour la fermer.

Vos recherches retournera uniquement des activités Power BI.

## <a name="search-the-audit-logs-by-date"></a>Rechercher les journaux d’audit par date

Vous pouvez rechercher dans les journaux par plage de dates à l’aide des champs **Date de début** et **Date de fin**. La sélection par défaut est au cours des sept derniers jours. L’affichage présente la date et l’heure au format de temps universel coordonné (UTC). La période maximale que vous pouvez spécifier est de 90 jours. 

Vous recevrez une erreur si la plage de dates sélectionnée est supérieure à 90 jours. Si vous utilisez la période maximale de 90 jours, sélectionnez l’heure actuelle comme **Date de début**. Sinon, vous recevez une erreur indiquant que la date de début est antérieure à la date de fin. Si vous avez activé l’audit dans les 90 derniers jours, la plage de dates ne peut pas commencer avant la date à laquelle l’audit a été activé.

![Recherche de journal de capture d’écran de l’Audit avec les options de Date de début et Date de fin indiquées.](media/service-admin-auditing/search-audit-log-by-date.png)

## <a name="search-the-audit-logs-by-users"></a>Rechercher les journaux d’audit par utilisateur

Vous pouvez rechercher des entrées du journal d’audit pour les activités effectuées par des utilisateurs spécifiques. Entrez un ou plusieurs noms d’utilisateur dans le **utilisateurs** champ. Le nom d’utilisateur ressemble à une adresse de messagerie. Il s’agit du compte que les utilisateurs se connectent à Power BI avec. Laissez cette zone vide afin de renvoyer les entrées pour tous les utilisateurs (et les comptes de service) de votre organisation.

![Rechercher par utilisateurs](media/service-admin-auditing/search-audit-log-by-user.png)

## <a name="view-search-results"></a>Afficher les résultats de recherche

Une fois que vous sélectionnez **recherche**, chargement les résultats de recherche. Après quelques instants, elles s’affichent sous **résultats**. Une fois la recherche terminée, l’affichage indique le nombre de résultats trouvés. **Recherche dans les journaux d’audit** affiche un maximum de 1 000 événements. Si plus de 1 000 événements répondent aux critères de recherche, l’application affiche les 1 000 événements plus récents.

### <a name="view-the-main-results"></a>Afficher les principaux résultats

Le **résultats** zone comporte les informations suivantes pour chaque événement retourné par la recherche. Sélectionnez un en-tête de colonne sous **Résultats** pour trier les résultats.

| **Colonne** | **Définition** |
| --- | --- |
| Date |Date et heure (au format UTC) auxquelles l’événement s’est produit. |
| Adresse IP |L’adresse IP de l’unité utilisée pour l’activité connectée. L’application affiche l’adresse IP au format d’adresse IPv4 ou IPv6. |
| Utilisateur |L’utilisateur (ou compte de service) qui a effectué l’action qui a déclenché l’événement. |
| Activité |L’activité exécutée par l’utilisateur. Cette valeur correspond aux activités que vous avez sélectionnées dans la liste déroulante **Activités**. Pour un événement du journal d’audit d’administrateur Exchange, la valeur de cette colonne est une cmdlet Exchange. |
| Article |L’objet créé ou modifié en raison de l’activité correspondante. Par exemple, le fichier affiché ou modifié, ou le compte d’utilisateur mis à jour. Seule une partie des activités a une valeur dans cette colonne. |
| Détails |Détails supplémentaires sur une activité. Là encore, pas toutes les activités ont une valeur. |

### <a name="view-the-details-for-an-event"></a>Afficher les détails d’un événement

Pour afficher plus de détails sur un événement, sélectionnez l’enregistrement d’événement dans la liste des résultats de recherche. Un **détails** page s’affiche avec les propriétés détaillées à partir de l’enregistrement d’événement. Le **détails** page affiche les propriétés en fonction du service Office 365 dans lequel l’événement se produit.

Pour afficher ces détails, sélectionnez **Plus d’informations**. Toutes les entrées Power BI ont une valeur de 20 pour la propriété RecordType. Pour plus d’informations sur les autres propriétés, consultez [Propriétés détaillées dans le journal d’audit](/office365/securitycompliance/detailed-properties-in-the-office-365-audit-log/).

   ![Capture d’écran de la boîte de dialogue Détails de l’audit avec l’option plus d’informations exigées.](media/service-admin-auditing/audit-details.png)

## <a name="export-search-results"></a>Exporter les résultats de recherche

Pour exporter le journal d’audit de Power BI dans un fichier CSV, procédez comme suit.

1. Sélectionnez **Exporter les résultats**.

1. Sélectionnez **Enregistrer les résultats chargés** ou **Télécharger tous les résultats**.

    ![Capture d’écran de l’exportation des résultats option.](media/service-admin-auditing/export-auditing-results.png)

## <a name="use-powershell-to-search-audit-logs"></a>Utiliser PowerShell pour rechercher dans les journaux d’audit

Vous pouvez aussi utiliser PowerShell pour accéder aux journaux d’audit en fonction de votre connexion. L’exemple suivant montre comment se connecter à Exchange Online PowerShell, puis utiliser la commande [Search-UnifiedAuditLog](/powershell/module/exchange/policy-and-compliance-audit/search-unifiedauditlog?view=exchange-ps/) pour extraire les entrées du journal d’audit Power BI. Pour exécuter le script, un administrateur doit vous attribuer les autorisations appropriées, comme décrit dans la [exigences](#requirements) section.

```powershell
Set-ExecutionPolicy RemoteSigned

$UserCredential = Get-Credential

$Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection

Import-PSSession $Session
Search-UnifiedAuditLog -StartDate 9/11/2018 -EndDate 9/15/2018 -RecordType PowerBI -ResultSize 1000 | Format-Table | More
```

Pour plus d’informations sur la connexion à Exchange Online, consultez [Se connecter à Exchange Online PowerShell](/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell/). Pour un autre exemple d’utilisation de PowerShell avec les journaux d’audit, consultez [Utilisation du journal d’audit Power BI et de PowerShell pour attribuer des licences Power BI Pro](https://powerbi.microsoft.com/blog/using-power-bi-audit-log-and-powershell-to-assign-power-bi-pro-licenses/).

## <a name="activities-audited-by-power-bi"></a>Activités auditées par Power BI

Les activités suivantes sont auditées par Power BI :

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
| Mettre à jour les paramètres de gouvernance des ressources de capacité      | UpdateCapacityResourceGovernanceSettings    | Absente du Centre d’administration Microsoft 365 |
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
