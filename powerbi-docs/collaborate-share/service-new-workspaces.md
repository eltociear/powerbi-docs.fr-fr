---
title: Organiser le travail dans les nouveaux espaces de travail dans Power BI
description: Découvrez les nouveaux espaces de travail, qui sont des collections de tableaux de bord et de rapports créés pour fournir des métriques clés sur votre organisation.
author: maggiesMSFT
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/07/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 701f478ce4dd59d77c1722b1386cd79ad3fbf2a0
ms.sourcegitcommit: 250242fd6346b60b0eda7a314944363c0bacaca8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83693785"
---
# <a name="organize-work-in-the-new-workspaces-in-power-bi"></a>Organiser le travail dans les nouveaux espaces de travail dans Power BI

Les *espaces de travail* sont des espaces de collaboration qui vous permettent de créer des collections de tableaux de bord, de rapports, de jeux de données et de rapports paginés avec vos collègues. La nouvelle expérience de l’espace de travail vous permet de mieux gérer l’accès au contenu. Cet article décrit les nouveaux espaces de travail, et en quoi ils diffèrent des espaces de travail classiques.  Comme avec les espaces de travail classiques, vous les utilisez pour créer et distribuer des applications. Prêt à créer un espace de travail ? Lisez [Créer une nouvelle expérience d’espace de travail](service-create-the-new-workspaces.md).

Les espaces de travail nouveaux et mis à niveau peuvent coexister auprès des espaces de travail classiques existants. La nouvelle expérience d’espace de travail est le type d’espace de travail par défaut. Vous pouvez toujours créer et utiliser des [espaces de travail classiques](service-create-workspaces.md) basés sur des groupes Microsoft 365 si nécessaire. Prêt à migrer votre espace de travail classique ? Consultez [Mettre à niveau les espaces de travail classiques vers de nouveaux espaces de travail dans Power BI](service-upgrade-workspaces.md) pour plus d’informations.

Avec les nouveaux espaces de travail, vous pouvez :

- Affecter des rôles d’espace de travail à des groupes d’utilisateurs : groupes de sécurité, listes de distribution, groupes Microsoft 365 et personnes individuelles.
- Créer un espace de travail dans Power BI sans créer de groupe Microsoft 365 associé sous-jacent. Toute l’administration des espaces de travail se fait dans Power BI et non dans Microsoft 365.
- Continuer à gérer l’accès des utilisateurs au contenu via les groupes Microsoft 365, si vous le souhaitez. Il vous suffit d’ajouter un groupe Microsoft 365 dans la liste d’accès de l’espace de travail.
- Utiliser des rôles d’espace de travail plus granulaires, pour une gestion plus flexible des autorisations dans un espace de travail.

Power BI continue à lister tous les groupes Microsoft 365 dont vous êtes membre. Cela évite de modifier les flux de travail existants.

## <a name="new-and-classic-workspace-differences"></a>Différences entre les espaces de travail nouveaux et classiques

Dans les nouveaux espaces de travail, certaines fonctionnalités ont été repensées. Voici les principales différences.

- La création de ces espaces de travail ne crée pas de groupes Microsoft 365 comme le font les espaces de travail classiques. Toutefois, vous pouvez maintenant utiliser un groupe Microsoft 365 pour donner aux utilisateurs l’accès à votre espace de travail en lui attribuant un rôle.
- Dans les espaces de travail classiques, vous pouvez seulement ajouter des personnes individuelles aux listes de membres et d’administrateurs. Dans les nouveaux espaces de travail, vous pouvez ajouter plusieurs groupes de sécurité Active Directory, des listes de distribution ou des groupes Microsoft 365 à ces listes, ce qui facilite la gestion des utilisateurs.
- Vous pouvez créer un pack de contenu d’organisation à partir d’un espace de travail classique. Vous ne pouvez pas en créer un à partir des nouveaux espaces de travail.
- Vous pouvez consommer un pack de contenu d’organisation à partir d’un espace de travail classique. Vous ne pouvez pas en consommer un à partir des nouveaux espaces de travail.

### <a name="workspace-features-that-work-differently"></a>Fonctionnalités d’espace de travail fonctionnant différemment

Certaines fonctionnalités agissent différemment dans les nouveaux espaces de travail. Ces différences sont intentionnelles et reposent sur les commentaires que nous avons reçus des clients. Elles permettent une approche plus souple de la collaboration avec les espaces de travail.

- **Application de la gestion des licences** : La publication de rapports dans la nouvelle expérience d’espace de travail est soumise à une application des règles de gestion des licences existantes. Les utilisateurs qui collaborent dans des espaces de travail ou partagent du contenu avec d’autres personnes dans le service Power BI ont besoin d’une licence Power BI Pro. Les utilisateurs sans licence Pro voient l’erreur « Seuls les utilisateurs avec des licences Power BI Pro peuvent publier sur cet espace de travail ».
- **Les membres peuvent ou ne peuvent pas repartager** : Le rôle contributeur remplace ce paramètre.
- **Espaces de travail en lecture seule** : Au lieu d’accorder aux utilisateurs un accès en lecture seule à un espace de travail, affectez-les au rôle Lecteur. Il permet un accès en lecture seule similaire au contenu d’un espace de travail.
- **Les utilisateurs avec une licence Pro** peuvent accéder à l’espace de travail si celui-ci se trouve dans une capacité Power BI Premium, mais seulement s’ils ont le rôle Lecteur.
- **Autoriser les utilisateurs à exporter des données** : Les utilisateurs avec le rôle Lecteur peuvent exporter des données s’ils ont l’autorisation Générer sur les jeux de données dans l’espace de travail. Découvrez plus en détail l’[autorisation de génération pour les jeux de données](../connect-data/service-datasets-build-permissions.md).
- Pas de bouton **Quitter l’espace de travail**.

### <a name="workspace-contact-list"></a>Liste de contacts de l’espace de travail

La nouvelle fonctionnalité **Liste de contacts** vous permet de spécifier les utilisateurs qui reçoivent une notification concernant les problèmes qui se produisent dans l’espace de travail. Par défaut, tout utilisateur ou groupe spécifié comme administrateur de l’espace de travail est averti, mais vous pouvez personnaliser la liste. Les utilisateurs ou groupes répertoriés dans la liste de contacts seront affichés dans l’interface utilisateur (IU) pour aider les utilisateurs à obtenir de l’aide concernant l’espace de travail. 

En savoir plus sur la [définition de la liste de contacts de l’espace de travail](service-create-the-new-workspaces.md#workspace-contact-list).

### <a name="workspace-onedrive"></a>OneDrive de l’espace de travail

La fonctionnalité OneDrive de l’espace de travail vous permet de configurer un groupe Microsoft 365 dont le stockage de fichiers de la bibliothèque de documents SharePoint est accessible aux utilisateurs de l’espace de travail. Vous devez d’abord créer le groupe en dehors de Power BI.

Power BI ne synchronise pas les autorisations des utilisateurs ou des groupes qui sont configurés pour avoir accès à l’espace de travail avec l’appartenance au groupe Microsoft 365. La bonne pratique consiste à gérer l’accès à l’espace de travail par le biais du même groupe Microsoft 365 dont vous configurez le stockage de fichiers dans ce paramètre.

En savoir plus sur comment [définir et accéder à OneDrive de l’espace de travail](service-create-the-new-workspaces.md#workspace-onedrive).  

## <a name="roles-in-the-new-workspaces"></a>Rôles dans les nouveaux espaces de travail

Pour accorder l’accès à un nouvel espace de travail, ajoutez des groupes d’utilisateurs ou des individus à l’un des rôles de l’espace de travail : administrateurs, membres, contributeurs ou lecteurs. Tous les utilisateurs d’un groupe d’utilisateurs reçoivent le rôle que vous avez défini. Si une personne fait partie de plusieurs groupes d’utilisateurs, elle reçoit le niveau d’autorisation le plus élevé fourni par les rôles qui lui sont attribués.

Les rôles vous permettent de gérer qui peut faire quoi dans un espace de travail, ce qui permet aux équipes de collaborer. Les nouveaux espaces de travail vous permettent d’affecter des rôles à des personnes individuelles et à des groupes d’utilisateurs : groupes de sécurité, groupes Microsoft 365 et listes de distribution.

Quand vous affectez des rôles à un groupe d’utilisateurs, les personnes individuelles du groupe ont accès au contenu. Si vous imbriquez des groupes d’utilisateurs, tous les utilisateurs qui en font partie ont les autorisations associées.

[!INCLUDE [power-bi-workspace-roles-table](../includes/power-bi-workspace-roles-table.md)]

> [!NOTE]
> Pour appliquer la sécurité au niveau des lignes (RLS) pour les utilisateurs qui parcourent le contenu dans un espace de travail, utilisez le rôle Lecteur. Pour appliquer la sécurité au niveau des lignes sans donner accès à l’espace de travail, publiez une application Power BI pour ces utilisateurs ou utilisez le partage pour distribuer le contenu.

## <a name="licensing"></a>Licences
Toutes les personnes que vous ajoutez à un espace de travail dans la capacité partagée doivent avoir une licence Power BI Pro. Dans l’espace de travail, ces utilisateurs peuvent collaborer sur des tableaux de bord et des rapports que vous prévoyez de publier pour un public plus large, ou même pour votre organisation tout entière. 

Si vous voulez distribuer du contenu à d’autres utilisateurs au sein de votre organisation, vous pouvez leur attribuer des licences Power BI Pro ou placer l’espace de travail dans une capacité Power BI Premium.

Lorsque l’espace de travail se trouve dans une capacité Power BI Premium, les utilisateurs avec le rôle Lecteur peuvent accéder l’espace de travail même s’ils n’ont pas de licence Power BI Pro. Toutefois, si vous attribuez à ces utilisateurs un rôle supérieur comme Administrateur, Membre ou Contributeur, ils seront invités à lancer la version d’essai de Power BI Pro pour accéder à l’espace de travail. Pour utiliser le rôle Lecteur pour les utilisateurs sans licence Pro, assurez-vous qu’ils n’ont pas d’autres rôles d’espace de travail, individuellement ou par le biais d’un groupe d’utilisateurs.

> [!NOTE]
> La publication de rapports dans la nouvelle expérience d’espace de travail est soumise à une application plus stricte des règles de gestion des licences existantes. Si vous tentez de publier à partir de Power BI Desktop ou d’autres outils clients sans licence Pro, vous voyez l’erreur « Seuls les utilisateurs avec des licences Power BI Pro peuvent publier sur cet espace de travail ».

## <a name="administering-new-workspace-experience-workspaces"></a>Gérer des espaces de travail (nouvelle expérience d’espace de travail)

L’administration des espaces de travail avec la nouvelle expérience d’espace de travail se trouve désormais dans le portail d’administration Power BI. Les administrateurs Power BI décident de qui, dans une organisation, peut créer des espaces de travail et distribuer des applications. Les administrateurs peuvent voir l’état de tous les espaces de travail de leur organisation. Ils peuvent également gérer et restaurer les espaces de travail. Pour en savoir plus sur la [Création des nouveaux espaces de travail](../admin/service-admin-portal.md#create-the-new-workspaces), consultez l’article du portail d’administration.

## <a name="guest-users"></a>Utilisateurs invités

Par défaut, les [utilisateurs invités B2B Azure AD](../admin/service-admin-azure-ad-b2b.md) n’ont pas accès aux espaces de travail. Les administrateurs Power BI peuvent [autoriser les utilisateurs invités externes à modifier et à gérer le contenu de l’organisation](../admin/service-admin-azure-ad-b2b.md#guest-users-who-can-edit-and-manage-content). Les utilisateurs invités peuvent accéder aux espaces de travail pour lesquels ils disposent d’une autorisation.

## <a name="auditing"></a>Audit

Les activités suivantes sont auditées par Power BI pour les espaces de travail de la nouvelle expérience de l’espace de travail.

| Nom convivial | Nom de l’opération |
|---|---|
| Dossier Power BI créé | CreateFolder |
| Dossier Power BI supprimé | DeleteFolder |
| Dossier Power BI mis à jour | UpdateFolder |
| Accès au dossier Power BI mis à jour| UpdateFolderAccess |

En savoir plus sur [l’audit Power BI](../admin/service-admin-auditing.md).

## <a name="limitations-and-considerations"></a>Considérations et limitations

Limitations à connaître :

- Les espaces de travail peuvent contenir un maximum de 1 000 jeux de données ou 1 000 rapports par jeu de données. 
- Une personne disposant d’une licence Power BI Pro peut être membre de 1 000 espaces de travail au maximum.
- Power BI Publisher pour Excel n’est pas pris en charge.

## <a name="frequently-asked-questions"></a>Forum Aux Questions

**Les liens vers le contenu existant sont-ils affectés par la nouvelle expérience d’espace de travail**

Non. Les liens vers des éléments existants dans les espaces de travail classiques ne sont pas affectés par la nouvelle expérience de l’espace de travail. La disponibilité générale (GA) de la nouvelle expérience de l’espace de modifie change l’espace de travail par défaut que vous créez, mais ne modifie pas les espaces de travail existants. 

**Les espaces de travail existants sont-ils mis à niveau vers la nouvelle expérience de l’espace de travail avec la disponibilité générale**

Non. La disponibilité générale de la nouvelle expérience de l’espace de travail remplace uniquement le type d’espace de travail par défaut par la nouvelle expérience de l’espace de travail. Les espaces de travail classiques existants basés sur des groupes Microsoft 365 restent inchangés.

**Les espaces de travail sont-ils toujours créés automatiquement pour les groupes Microsoft 365 ?**

Oui. Étant donné que nous prenons en charge les deux types d’espaces de travail côte à côte, nous continuons à répertorier tous les groupes Microsoft 365 auxquels vous avez accès dans la liste des espaces de travail.

## <a name="next-steps"></a>Étapes suivantes

* [Créer les nouveaux espaces de travail dans Power BI](service-create-the-new-workspaces.md)
* [Créer les espaces de travail classiques](service-create-workspaces.md)
* [Installer et utiliser des applications dans Power BI](service-create-distribute-apps.md)
* Vous avez des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)

