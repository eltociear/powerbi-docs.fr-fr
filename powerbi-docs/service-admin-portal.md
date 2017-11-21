---
title: "Portail d’administration Power BI"
description: "Le portail d’administration permet de gérer les clients Power BI de votre organisation. Il comprend notamment des métriques d’utilisation, un accès au Centre d’administration Office 365 et des paramètres."
services: powerbi
documentationcenter: 
author: guyinacube
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 09/05/2017
ms.author: asaxton
ms.openlocfilehash: 339e3bc6f5a8acda20313e2f99e1b9b041bc2225
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2017
---
# <a name="power-bi-admin-portal"></a>Portail d’administration Power BI
Le portail d’administration permet de gérer les clients Power BI de votre organisation. Il comprend notamment des métriques d’utilisation, un accès au Centre d’administration Office 365 et des paramètres.

La gestion des clients Power BI de votre entreprise s’effectue via le portail d’administration Power BI. Le portail d’administration est accessible à tous les utilisateurs qui sont administrateurs généraux dans Office 365 ou qui sont assignés au rôle d’administrateur de Service Power BI. Pour plus d’informations sur le rôle d’administrateur de Service Power BI, voir [Présentation du rôle d’administrateur Power BI](service-admin-role.md).

Tous les utilisateurs peuvent voir **Portail d’administration** sous l’icône d’engrenage. Les non-administrateurs voient uniquement la section **Paramètres Premium** ainsi que les capacités qu’ils ont le droit de gérer.

## <a name="how-to-get-to-the-admin-portal"></a>Accès au portail d’administration
Pour obtenir l’accès au portail d’administration Power BI, votre compte doit être un compte d’**Administrateur global** dans Office 365 ou Azure Active Directory, ou doit avoir été assigné au rôle d’Administrateur de Service Power BI. Pour plus d’informations sur le rôle d’administrateur de Service Power BI, voir [Présentation du rôle d’administrateur Power BI](service-admin-role.md). Pour accéder au portail d’administration Power BI, procédez comme suit.

1. Sélectionnez l’icône des paramètres représentant une roue dentée, située en haut à droite de l’écran Power BI.
2. Sélectionnez **Portail d’administration**.

![](media/service-admin-portal/powerbi-admin-settings.png)

Le portail comporte cinq onglets. Ces onglets sont décrits ci-dessous.

* [Métriques d’utilisation](#usage-metrics)
* [Utilisateurs](#users)
* [Journaux d’audit](#audit-logs)
* [Paramètres du locataire](#tenant-settings)
* [Paramètres Premium](#premium-settings)

![](media/service-admin-portal/powerbi-admin-landing-page.png)

## <a name="usage-metrics"></a>Métriques d’utilisation
Le premier onglet du portail d’administration est **Métriques d’utilisation**. Le rapport sur les métriques d’utilisation vous donne la possibilité de surveiller l’utilisation de Power BI au sein de votre organisation. Il permet également de voir les utilisateurs et les groupes de votre organisation qui sont les plus actifs dans Power BI.

> [!NOTE]
> La première fois que vous accédez au tableau de bord ou si vous y accédez de nouveau après une longue période, un écran de chargement s’affiche probablement pendant le chargement du tableau de bord.
> 
> 

Une fois le tableau de bord chargé, vous verrez deux sections de vignettes. La première section comprend des données d’utilisation pour chacun des utilisateurs, et la deuxième section comporte des informations similaires pour les groupes de votre organisation.

Voici le détail de ce que vous verrez dans chacune d’elle :

* Le nombre de tableaux de bord, de rapports et de jeux de données de l’espace de travail utilisateur
  
    ![](media/service-admin-portal/powerbi-admin-usage-metrics-number-tiles.png)
* Le tableau de bord le plus utilisé par nombre d’utilisateurs autorisés à y accéder. Par exemple, si vous avez un tableau de bord que vous avez partagé avec trois utilisateurs et si vous l’avez également ajouté à un pack de contenu auquel sont connectés deux autres utilisateurs, le nombre d’utilisateurs s’élève à 6 (1 + 3 + 2)
  
    ![](media/service-admin-portal/powerbi-admin-usage-metrics-top-dashboards.png)
* Le contenu auquel est connecté le plus grand nombre d’utilisateurs. Il peut s’agir de tout ce que les utilisateurs peuvent obtenir via le processus Obtenir des données, autrement dit, des packs de contenu SaaS, des packs de contenu d’organisation, des fichiers ou des bases de données.
  
    ![](media/service-admin-portal/powerbi-admin-usage-metrics-top-connections.png)
* Vue des utilisateurs les plus actifs, en fonction du nombre de tableaux de bord qu’ils possèdent, à la fois ceux qu’ils ont créés eux-mêmes et ceux qui ont été partagés avec eux.
  
    ![](media/service-admin-portal/powerbi-admin-usage-metrics-top-users-dashboards.png)
* Vue des utilisateurs les plus actifs, en fonction du nombre de rapports qu’ils possèdent
  
    ![](media/service-admin-portal/powerbi-admin-usage-metrics-top-users-reports.png)

La deuxième section affiche le même type d’informations, mais pour les groupes. Vous pouvez ainsi voir les groupes de votre organisation qui sont les plus actifs et quels types d’informations ils utilisent.

Avec ces informations, vous pourrez savoir comment les employés de votre organisation utilisent Power BI et quels sont les utilisateurs et les groupes qui sont les plus actifs.

## <a name="users"></a>Users
Le deuxième onglet du portail d’administration est **Gérer les utilisateurs**. La gestion des utilisateurs Power BI s’effectue dans le Centre d’administration Office 365. Cette section vous permet d’atteindre rapidement l’emplacement où sont gérés les utilisateurs, les administrateurs et les groupes dans Office 365.

![](media/service-admin-portal/powerbi-admin-manage-users.png)

Quand vous cliquez sur **Accéder au centre d’administration O365**, vous accédez directement à la page d’accueil du centre d’administration Office 365, depuis laquelle vous pouvez gérer les utilisateurs de votre client.

![](media/service-admin-portal/powerbi-admin-o365-admin-center.png)

## <a name="audit-logs"></a>Journaux d’audit
Le troisième onglet du portail d’administration est **Journaux d’audit**. Les journaux sont situés dans le Centre de sécurité et conformité Office 365. Cette section vous permet d’accéder rapidement à cette zone dans Office 365. 

Pour plus d’informations sur les journaux d’audit, consultez [Audit de Power BI dans votre organisation](service-admin-auditing.md).

## <a name="tenant-settings"></a>Paramètres du client
Le troisième onglet du portail d’administration est **Paramètres du client**. Les paramètres client vous permettent de décider des fonctionnalités qui doivent être mises à la disposition de votre organisation. Si vous vous inquiétez pour vos données sensibles, certaines de nos fonctionnalités peuvent ne pas être adaptées à votre organisation, ou nous vous recommandons d’attribuer certaines fonctionnalités à des groupes précis. Si c’est le cas, vous pouvez les désactiver dans votre client.

![](media/service-admin-portal/powerbi-admin-tenant-settings.png)

> [!NOTE]
> L’activation ou la désactivation d’un paramètre peut prendre jusqu’à 10 minutes pour tous les utilisateurs de votre client.
> 
> 

Les fonctionnalités peuvent avoir trois états, selon votre configuration.

### <a name="disabled-for-the-entire-organization"></a>Désactivé pour toute l’organisation
Vous pouvez désactiver une fonctionnalité pour que les utilisateurs ne puissent plus l’utiliser.

![](media/service-admin-portal/powerbi-admin-tenant-settings-disabled.png)

### <a name="enabled-for-the-entire-organization"></a>Activé pour toute l’organisation
Vous pouvez activer une fonctionnalité pour toute votre organisation, ce qui permet à tous les utilisateurs d’y accéder.

![](media/service-admin-portal/powerbi-admin-tenant-settings-enabled.png)

### <a name="enabled-for-a-subset-of-the-organization"></a>Activé pour une partie de l’organisation
Vous pouvez également activer une fonctionnalité pour une partie de votre organisation. Cela peut se produire de différentes manières. Vous pouvez l’activer pour toute votre organisation à l’exception d’un groupe spécifique d’utilisateurs.

![](media/service-admin-portal/powerbi-admin-tenant-settings-enabled-except.png)

Vous pouvez également activer la fonctionnalité uniquement pour un groupe d’utilisateurs spécifique, mais également la désactiver pour un autre groupe d’utilisateurs. Vous pouvez ainsi vous assurer que certains utilisateurs n’ont pas accès à la fonctionnalité, même s’ils se trouvent dans le groupe des utilisateurs autorisés.

![](media/service-admin-portal/powerbi-admin-tenant-settings-enabled-except2.png)

## <a name="export-and-sharing-settings"></a>Paramètres d’exportation et de partage
### <a name="share-content-to-external-users"></a>Partager le contenu avec des utilisateurs externes
Les utilisateurs de l’organisation peuvent partager des tableaux de bord avec des utilisateurs externes à l’organisation.

![](media/service-admin-portal/powerbi-admin-sharing-external.png)

### <a name="publish-to-web"></a>Publication sur le web
Les utilisateurs de l’organisation peuvent publier des rapports sur le web. [En savoir plus](service-publish-to-web.md)

![](media/service-admin-portal/powerbi-admin-publish-to-web.png)

> [!NOTE]
> Ce paramètre s’applique à toute l’organisation et ne peut pas être limité à des groupes spécifiques.
> 
> 

### <a name="export-data"></a>Exporter des données
Les utilisateurs de l’organisation peuvent exporter des données depuis une vignette ou une visualisation. [En savoir plus](power-bi-visualization-export-data.md)

![](media/service-admin-portal/powerbi-admin-export-data.png)

> [!NOTE]
> La désactivation du paramètre **Exporter des données** empêche également les utilisateurs d’utiliser la fonctionnalité **Analyser dans Excel** ainsi que la connexion active au service Power BI.
> 
> 

### <a name="export-reports-as-powerpoint-presentations"></a>Exporter les rapports comme présentations PowerPoint
Les utilisateurs de l’organisation peuvent exporter des rapports Power BI sous forme de fichiers PowerPoint. [En savoir plus](service-publish-to-powerpoint.md)

![](media/service-admin-portal/powerbi-admin-powerpoint.png)

### <a name="print-dashboards-and-reports"></a>Imprimer des tableaux de bord et des rapports
Les utilisateurs de l’organisation peuvent imprimer des tableaux de bord et des rapports. [En savoir plus](service-print.md)

![](media/service-admin-portal/powerbi-admin-print-dashboard.png)

![](media/service-admin-portal/powerbi-admin-print-report.png)

## <a name="content-pack-settings"></a>Paramètres du pack de contenu
### <a name="publish-content-packs-to-the-entire-organization"></a>Publier les packs de contenu dans toute l'organisation
Les utilisateurs de l’organisation peuvent publier des packs de contenu pour toute l’organisation.

![](media/service-admin-portal/powerbi-admin-publish-entire-org.png)

### <a name="create-template-organizational-content-packs"></a>Créer des modèles de packs de contenu d’organisation
Les utilisateurs de l’organisation peuvent créer des packs de contenu modèles qui utilisent des jeux de données basés sur une même source de données dans Power BI Desktop.

## <a name="integration-settings"></a>Paramètres d’intégration
### <a name="ask-questions-about-data-using-cortana"></a>Poser des questions sur les données à l’aide de Cortana
Les utilisateurs de l’organisation peuvent poser des questions sur leurs données en utilisant Cortana.

> [!NOTE]
> Ce paramètre s’applique à toute l’organisation et ne peut pas être limité à des groupes spécifiques.
> 
> 

### <a name="use-analyze-in-excel-with-on-premises-datasets"></a>Utiliser Analyser dans Excel avec des jeux de données locaux
Les utilisateurs de l’organisation peuvent utiliser Excel pour afficher et interagir avec des jeux de données Power BI locaux. [En savoir plus](service-analyze-in-excel.md)

> [!NOTE]
> La désactivation du paramètre **Exporter des données** empêche également les utilisateurs d’utiliser la fonctionnalité **Analyser dans Excel**.
> 
> 

### <a name="user-arcgis-maps-for-power-bi-preview"></a>Utiliser ArcGIS Maps pour Power BI (préversion)
Les utilisateurs de l’organisation peuvent utiliser la visualisation ArcGIS Maps pour Power BI (préversion) fournie par Esri. [En savoir plus](power-bi-visualization-arcgis.md)

## <a name="r-visuals-settings"></a>Paramètres des visuels R
### <a name="interact-with-an-dshare-r-visuals"></a>Utiliser et partager des éléments visuels R
Les utilisateurs de l’organisation peuvent manipuler et partager des visuels créés avec des scripts R. [En savoir plus](service-r-visuals.md)

> [!NOTE]
> Ce paramètre s’applique à toute l’organisation et ne peut pas être limité à des groupes spécifiques.
> 
> 

## <a name="audit-settings"></a>Paramètres d’audit
### <a name="create-audit-logs-for-internal-activity-auditing-and-compliance"></a>Créer des journaux d’audit pour l’audit des activités internes et la vérification de la conformité
Les utilisateurs de l’organisation peuvent utiliser l’audit pour surveiller les actions effectuées dans Power BI par d’autres utilisateurs de l’organisation. [En savoir plus](service-admin-auditing.md)

Ce paramètre doit être activé pour pouvoir enregistrer les entrées du journal d’audit.

> [!NOTE]
> Ce paramètre s’applique à toute l’organisation et ne peut pas être limité à des groupes spécifiques.
> 
> 

## <a name="dashboard-settings"></a>Paramètres du tableau de bord
### <a name="data-classification-for-dashboards"></a>Classification des données des tableaux de bord
Les utilisateurs de l’organisation peuvent étiqueter les tableaux de bord avec des classifications indiquant les niveaux de sécurité des tableaux de bord. [En savoir plus](service-data-classification.md)

> [!NOTE]
> Ce paramètre s’applique à toute l’organisation et ne peut pas être limité à des groupes spécifiques.
> 
> 

## <a name="developer-settings"></a>Paramètres de développeur
### <a name="embed-content-in-apps"></a>Incorporer du contenu dans les applications
Les utilisateurs de l’organisation peuvent incorporer des tableaux de bord et des rapports Power BI dans des applications Saas (Software as a Service). La désactivation de ce paramètre empêche les utilisateurs d’utiliser les API REST pour incorporer du contenu Power BI dans leur application.

## <a name="premium-settings"></a>Paramètres Premium
L’onglet Paramètres Premium vous permet de gérer les capacités Power BI Premium souscrites pour votre organisation. Tous les utilisateurs membres de votre organisation voient l’onglet Paramètres Premium, mais ne peuvent en voir le contenu que s’ils disposent d’autorisations d’**administrateur de capacité** ou d’autorisations d’affectation. Si un utilisateur ne possède aucune autorisation, le message suivant apparaît.

![](media/service-admin-portal/premium-settings-no-access.png "Aucun accès aux paramètres Premium")

Pour plus d’informations sur la gestion des paramètres Premium, consultez [Gérer Power BI Premium](service-admin-premium-manage.md).

## <a name="next-steps"></a>Étapes suivantes
[Présentation du rôle d’administrateur Power BI](service-admin-role.md)  
[Audit de Power BI dans votre organisation](service-admin-auditing.md)  
[Gérer Power BI Premium](service-admin-premium-manage.md)  
[Administration de Power BI dans votre organisation](service-admin-administering-power-bi-in-your-organization.md)  

D’autres questions ? [Essayez d’interroger la communauté Power BI](http://community.powerbi.com/)

