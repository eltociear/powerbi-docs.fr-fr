---
title: Organiser le travail dans les nouveaux espaces de travail - Power BI
description: Découvrez les nouveaux espaces de travail, qui sont des collections de tableaux de bord et rapports destinés à fournir des mesures clés pour votre organisation.
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/18/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 9f5dfaa5a23ae46fef131a52355531b5fbde3051
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "65100687"
---
# <a name="organize-work-in-the-new-workspaces-in-power-bi"></a>Organiser le travail dans les nouveaux espaces de travail dans Power BI

 *Espaces de travail* sont des environnements pour collaborer avec des collègues pour créer des collections de tableaux de bord, rapports et des rapports paginés. La nouvelle expérience de l’espace de travail vous permet de mieux gérer l’accès au contenu. Cet article décrit les nouveaux espaces de travail, et en quoi ils diffèrent des espaces de travail classiques.  Comme avec les espaces de travail classiques, vous toujours les utiliser pour créer et distribuer des applications. En savoir plus sur comment [créer une nouvelle expérience de l’espace de travail](service-create-the-new-workspaces.md).

La nouvelle expérience de l’espace de travail a atteint la disponibilité générale (GA) et est désormais l’espace de travail par défaut. Vous pouvez toujours continuer à créer et utiliser [des espaces de travail classiques](service-create-workspaces.md) basés sur des groupes Office 365. 

> [!NOTE]
> Pour appliquer une sécurité au niveau des lignes (RLS) pour Power BI Pro aux utilisateurs de naviguer dans un espace de travail, continuer à utiliser [des espaces de travail classiques](service-create-workspaces.md). Sélectionnez le **membres peuvent uniquement afficher le contenu Power BI** option. Vous pouvez également publier une application Power BI aux utilisateurs, ou utiliser le partage pour distribuer du contenu. Le rôle de visionneuse à venir permettra ce scénario dans les futures dans l’espace de travail expérience espaces de travail.

Avec les nouveaux espaces de travail, vous pouvez :

- Affecter des rôles d’espace de travail à des groupes d’utilisateurs : groupes de sécurité, listes de distribution, groupes Office 365 et personnes individuelles.
- Créer un espace de travail dans Power BI sans créer un groupe Office 365.
- Utiliser des rôles d’espace de travail plus granulaires, pour une gestion plus flexible des autorisations dans un espace de travail.

Quand vous créez un des nouveaux espaces de travail, vous ne créez pas de groupe Office 365 associé sous-jacent. Toute l’administration des espaces de travail se fait dans Power BI et non pas dans Office 365. Dans la nouvelle expérience de l’espace de travail, vous pouvez maintenant ajouter un groupe Office 365 dans la liste d’accès de l’espace de travail pour continuer à gérer l’accès au contenu via des groupes Office 365.

## <a name="administering-new-workspace-experience-workspaces"></a>Administration de nouveaux espaces de travail d’expérience d’espace de travail
Administration de nouveaux espaces de travail d’expérience d’espace de travail est désormais dans Power BI, les administrateurs Power BI décider qui dans une organisation peut créer des espaces de travail. Ils peuvent également gérer et récupérer l’espace de travail. Pour cela, qu'ils doivent utiliser le portail d’administration Power BI ou les PowerShell CmdLets. Pour les espaces de travail classiques basés sur les groupes Office 365, administration continue à se produire dans le portail d’administration Office 365 et Azure Active Directory.

Dans **paramètres de l’espace de travail** dans le portail d’administration, les administrateurs peuvent utiliser des créer espaces de travail (nouvelle expérience d’espace de travail) paramètre pour autoriser tout le monde ou personne dans une organisation pour créer des espaces de travail expérience nouvel espace de travail. Il peuvent également limiter la création aux membres de groupes de sécurité spécifiques.

> [!NOTE]
> Créer espaces de travail (nouvelle expérience d’espace de travail) définissant les valeurs par défaut pour autoriser uniquement les utilisateurs qui peuvent créer des groupes Office 365 pour créer de nouveaux espaces de travail dans Power BI. Veillez à définir une valeur dans le portail d’administration Power BI pour garantir aux utilisateurs appropriés peuvent créer le nouvel espace de travail expérience espaces de travail.

![Paramètres d’espace de travail dans le portail d’administration](media/service-new-workspaces/power-bi-workspace-admin-settings.png)

Le [liste d’espaces de travail est disponible](service-admin-portal.md#workspaces) dans le portail d’administration Power BI. 

![Liste des espaces de travail](media/service-admin-portal/workspaces-list.png)

## <a name="new-workspaces-side-by-side-with-classic-workspaces"></a>Nouveaux espaces de travail côte à côte avec des espaces de travail classiques

Nouveau, mis à niveau des espaces de travail et des espaces de travail classiques existants coexistent côte à côte, et vous pouvez créer. La nouvelle expérience de l’espace de travail est le type d’espace de travail par défaut. Power BI se poursuit répertorier tous les groupes Office 365 l’utilisateur est membre dans Power BI pour éviter de modifier le flux de travail existants. Pour savoir comment créer un nouvel espace de travail, lisez [créer de nouveaux espaces de travail](service-create-the-new-workspaces.md). Pour savoir comment créer un espace de travail classique, consultez [créer les espaces de travail classiques](service-create-workspaces.md).

## <a name="roles-in-the-new-workspaces"></a>Rôles dans les nouveaux espaces de travail

Pour accorder l’accès à un espace de travail, ajouter des groupes d’utilisateurs ou des individus à un des rôles de l’espace de travail : membres, des collaborateurs ou administrateurs. Tous les utilisateurs d’un groupe d’utilisateurs reçoivent le rôle que vous avez défini. Si une personne est dans plusieurs groupes d’utilisateurs, ils obtiennent le plus haut niveau d’autorisation fournie par les rôles qu’ils sont attribués.

Les rôles vous permettent de gérer qui peut faire quoi dans un espace de travail, ce qui permet aux équipes de collaborer. Les nouveaux espaces de travail vous permettent d’affecter des rôles à des personnes individuelles et à des groupes d’utilisateurs : groupes de sécurité, groupes Office 365 et listes de distribution. 

Quand vous affectez des rôles à un groupe d’utilisateurs, les personnes individuelles du groupe ont accès au contenu. Si vous imbriquez des groupes d’utilisateurs, tous les utilisateurs qui en font partie ont les autorisations associées. Un utilisateur qui est dans plusieurs groupes d’utilisateurs ayant des rôles différents reçoit le niveau d’autorisation le plus élevé qui leur est accordé. 

Les nouveaux espaces de travail offrent trois rôles : administrateurs, membres et contributeurs.

|Fonctionnalité   | Administrateur  | Membre  | Contributeur  | 
|---|---|---|---|
| Mettre à jour et supprimer l’espace de travail.  | X  |   |   |
| Ajouter/supprimer des personnes, y compris d’autres administrateurs.  | X  |   |   |
| Ajouter des membres ou d’autres rôles avec des autorisations inférieures.  |  X | X  |   |
| Publier et mettre à jour une application. |  X | X  |   |
| Partager un élément ou une application. |  X | X  |   |
| Permettre à d’autres utilisateurs de repartager des éléments. |  X | X  |   |
| Créer, modifier et supprimer du contenu dans l’espace de travail.  |  X | X  | X  |
| Publier des rapports sur l’espace de travail, supprimer du contenu. |  X | X  | X  |
 
 
## <a name="licensing"></a>Licensing
Toutes les personnes que vous ajoutez à un espace de travail doivent avoir une licence Power BI Pro. Dans l’espace de travail, ces utilisateurs peuvent collaborer sur des tableaux de bord et des rapports que vous prévoyez de publier pour un public plus large, ou même pour votre organisation tout entière. Si vous voulez distribuer du contenu à d’autres utilisateurs au sein de votre organisation, vous pouvez leur attribuer des licences Power BI Pro ou placer l’espace de travail dans une capacité Power BI Premium.

> [!NOTE]
> Publication de rapports à la nouvelle expérience de l’espace de travail a existant de mise en œuvre plus stricte des règles de gestion de licences. Les utilisateurs qui tentent de publier à partir de Power BI Desktop ou d’autres clients outils sans une licence Pro voient l’erreur « seuls les utilisateurs avec des licences Power BI Pro peuvent publier sur cet espace de travail. »

## <a name="how-are-the-new-workspaces-different-from-current-workspaces"></a>En quoi les nouveaux espaces de travail diffèrent-ils des espaces de travail actuels ?

Avec les nouveaux espaces de travail, nous proposons une nouvelle conception de certaines fonctionnalités. Voici les modifications que vous souhaitez être permanente. 

* Création de ces espaces de travail ne crée pas les groupes Office 365 comme des espaces de travail classiques. Toutefois, vous pouvez utiliser maintenant un groupe Office 365 pour donner aux utilisateurs l’accès à votre espace de travail en lui assignant un rôle. 
* Dans les espaces de travail classiques, vous pouvez ajouter uniquement des utilisateurs pour les membres et les listes de l’administrateur. Dans les nouveaux espaces de travail, vous pouvez ajouter plusieurs groupes de sécurité Active Directory, des listes de distribution ou des groupes Office 365 à ces listes, ce qui facilite la gestion des utilisateurs. 
- Vous pouvez créer un pack de contenu d’organisation à partir d’un espace de travail classique. Vous ne pouvez pas en créer un à partir des nouveaux espaces de travail.
- Vous pouvez utiliser un pack de contenu d’organisation à partir d’un espace de travail classique. Vous ne pouvez pas en consommer un à partir des nouveaux espaces de travail.

## <a name="workspace-contact-list"></a>Liste de contacts d’espace de travail
La nouvelle **Contact list** fonctionnalité vous permet de spécifier les utilisateurs qui reçoivent une notification concernant les problèmes qui se produisent dans l’espace de travail. Par défaut, tout utilisateur ou groupe spécifié comme un espace de travail administrateur est averti, mais vous pouvez personnaliser la liste. Les utilisateurs ou groupes répertoriés dans la liste des contacts seront affichera dans l’interface utilisateur (IU) pour aider aux utilisateurs obtiennent aide relatives à l’espace de travail. 

En savoir plus sur la [définition de la liste de contacts d’espace de travail](service-create-the-new-workspaces.md#workspace-contact-list).

## <a name="workspace-onedrive"></a>OneDrive de l’espace de travail
La fonctionnalité OneDrive de l’espace de travail vous permet de configurer un groupe Office 365 dont le stockage fichier bibliothèque de documents SharePoint est disponible aux utilisateurs de l’espace de travail. Le groupe doit être créé en dehors de Power BI. 

Power BI ne synchronise pas les autorisations des utilisateurs ou groupes qui sont configurés pour avoir accès d’espace de travail avec l’appartenance au groupe Office 365. La meilleure pratique consiste à gérer l’accès d’espace de travail via le même groupe Office 365 dont vous configurez dans ce paramètre de stockage de fichiers. 

En savoir plus sur comment [définir et accéder à OneDrive de l’espace de travail](service-create-the-new-workspaces.md#workspace-onedrive).  
   
## <a name="auditing"></a>L’audit
Les activités suivantes sont auditées par Power BI pour les nouveaux espaces de travail d’expérience d’espace de travail.

| Nom convivial |   Nom de l’opération |
|---|---|
| Dossier Power BI créé | CreateFolder |
| Dossier Power BI supprimé | DeleteFolder |
| Dossier Power BI mis à jour | UpdateFolder |
| Accès au dossier Power BI mis à jour| UpdateFolderAccess |

En savoir plus sur [l’audit de Power BI](service-admin-auditing.md#activities-audited-by-power-bi).

## <a name="limitations-and-considerations"></a>Considérations et limitations

Limitations à connaître :

- Les espaces de travail peuvent contenir un maximum de 1 000 jeux de données ou 1 000 rapports par jeu de données. 
- Une personne disposant d’une licence Power BI Pro peut être un membre d’un 1 000 espaces de travail maximale.
- Power BI publisher pour Excel n’est pas pris en charge.

## <a name="workspace-features-that-work-differently"></a>Fonctionnalités d’espace de travail fonctionnant différemment

Certaines fonctionnalités agissent différemment dans les nouveaux espaces de travail. Ces différences sont intentionnelles, en fonction de vos commentaires nous avez reçus des clients et activer une approche plus souple pour la collaboration avec des espaces de travail :

- Attribution des licences : Publication de rapports à la nouvelle expérience de l’espace de travail applique des règles de licence existantes qui nécessitent une licence Power BI Pro pour les utilisateurs de collaboration dans les espaces de travail ou le partage de contenu à d’autres personnes dans le service Power BI. Les utilisateurs sans licence Pro voient l’erreur « seuls les utilisateurs avec des licences Powre BI Pro peuvent publier sur cet espace de travail. »
- Les membres peuvent ou non repartager : remplacé par le rôle Contributeur
- Espaces de travail en lecture seule : au lieu d’accorder aux utilisateurs un accès en lecture seule à un espace de travail, vous affecterez les utilisateurs à un rôle Visiteur prochainement disponible, qui permet un accès en lecture seule similaire au contenu dans un espace de travail.
- Pas de bouton **Quitter l’espace de travail**.

## <a name="frequently-asked-questions"></a>Forum Aux Questions

**Sont des liens vers du contenu existant affectés par l’espace de travail expérience GA**

Non. Des liens vers des éléments existants dans les espaces de travail classiques ne sont pas affectés par la nouvelle expérience de l’espace de travail. La disponibilité générale (GA) de la nouvelle expérience de l’espace de travail change l’espace de travail par défaut, vous créez, mais ne modifiez pas les espaces de travail existants. 

**Sont des espaces de travail mis à niveau vers la nouvelle expérience d’espace de travail avec la disponibilité générale**

Non. L’agent invité de nouvel espace de travail expérience modifie uniquement le type d’espace de travail par défaut à la nouvelle expérience de l’espace de travail. Espaces de travail classiques existants sont basées sur les groupes Office 365 restent inchangés.

**Espaces de travail sont toujours automatiquement créés pour les groupes Office 365**

Oui. Étant donné que nous prenons en charge les deux types d’espaces de travail côte à côte, nous continuons à répertorier tous les groupes Office 365 l’utilisateur a accès à dans la liste des espaces de travail.

## <a name="next-steps"></a>Étapes suivantes
* [Créer de nouveaux espaces de travail dans Power BI](service-create-the-new-workspaces.md)
* [Créer les espaces de travail classiques](service-create-workspaces.md)
* [Installer et utiliser des applications dans Power BI](service-create-distribute-apps.md)
* Vous avez des questions ? [Essayez d’interroger la communauté Power BI](http://community.powerbi.com/)
