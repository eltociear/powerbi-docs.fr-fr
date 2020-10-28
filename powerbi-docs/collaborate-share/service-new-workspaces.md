---
title: Organiser le travail dans les nouveaux espaces de travail dans Power BI
description: Découvrez les nouveaux espaces de travail, qui sont des collections de tableaux de bord et de rapports créés pour fournir des métriques clés sur votre organisation.
author: maggiesMSFT
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/21/2020
ms.author: maggies
ms.custom: contperfq4
LocalizationGroup: Share your work
ms.openlocfilehash: 1ea5e7633fb81b2792459c3a428c9c43827a5137
ms.sourcegitcommit: fddba666c6ea90d525a1c3188bbd3c4a03410cdc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2020
ms.locfileid: "92462216"
---
# <a name="organize-work-in-the-new-workspaces-in-power-bi"></a>Organiser le travail dans les nouveaux espaces de travail dans Power BI

Les *espaces de travail* sont des espaces de collaboration qui vous permettent de créer des collections de tableaux de bord, de rapports, de jeux de données et de rapports paginés avec vos collègues. La nouvelle expérience de l’espace de travail vous permet de mieux gérer l’accès au contenu. Cet article décrit les nouveaux espaces de travail, et en quoi ils diffèrent des espaces de travail classiques.  Comme avec les espaces de travail classiques, vous les utilisez pour créer et distribuer des applications. 

Prêt à créer un espace de travail ? Lisez [Créer une nouvelle expérience d’espace de travail](service-create-the-new-workspaces.md).

:::image type="content" source="media/service-new-workspaces/power-bi-workspace-opportunity.png" alt-text="Nouvelle expérience d’espace de travail Power BI":::

Les espaces de travail nouveaux et mis à niveau peuvent coexister auprès des espaces de travail classiques existants. La nouvelle expérience d’espace de travail est le type d’espace de travail par défaut. Vous pouvez toujours créer et utiliser des [espaces de travail classiques](service-create-workspaces.md) basés sur des groupes Microsoft 365 si nécessaire. Prêt à migrer votre espace de travail classique ? Consultez [Mettre à niveau les espaces de travail classiques vers de nouveaux espaces de travail dans Power BI](service-upgrade-workspaces.md) pour plus d’informations.

## <a name="new-and-classic-workspace-differences"></a>Différences entre les espaces de travail nouveaux et classiques

Dans les nouveaux espaces de travail, certaines fonctionnalités ont été repensées. Voici les principales différences.

- **La création de ces espaces de travail ne crée pas de groupes Microsoft 365** comme le font les espaces de travail classiques. Toute la nouvelle administration des espaces de travail se fait dans Power BI et non pas dans Office 365. Vous pouvez continuer à gérer l’accès des utilisateurs au contenu via les groupes Microsoft 365, si vous le souhaitez. Il vous suffit d’ajouter un groupe Microsoft 365 dans la liste d’accès de l’espace de travail.
- **Utiliser des rôles d’espace de travail plus granulaires** , pour une gestion plus flexible des autorisations dans de nouveaux espaces de travail.  Dans les espaces de travail classiques, vous pouvez seulement ajouter des personnes individuelles aux listes de membres et d’administrateurs. 
- **Affecter des groupes d’utilisateurs aux rôles de l’espace de travail**  : Dans les nouveaux espaces de travail, vous pouvez ajouter plusieurs groupes de sécurité Active Directory, des listes de distribution ou des groupes Microsoft 365 à ces rôles, ce qui facilite la gestion des utilisateurs. 
- **Liste des contacts**  : Dans les nouveaux espaces de travail, vous pouvez spécifier qui reçoit la notification sur l’activité de l’espace de travail.
- **Créer des applications modèles**  : Vous pouvez uniquement créer des *applications de modèle* dans les nouveaux espaces de travail. Les applications de modèle sont des applications que vous pouvez distribuer aux clients en dehors de votre organisation. Ces clients peuvent ensuite se connecter à leurs propres données avec votre application de modèle. En savoir plus sur les [applications de modèle](../connect-data/service-template-apps-overview.md).
- **Partager des jeux de données**  : Pour partager un jeu de données en dehors d’un espace de travail spécifique, vous devez enregistrer le rapport qui contient le jeu de données dans l’un des nouveaux espaces de travail. Vous ne pouvez pas partager des jeux de données à partir d’espaces de travail classiques. En savoir plus sur les [jeux de données partagés](../connect-data/service-datasets-across-workspaces.md).
- **Packs de contenu professionnels**  : Vous pouvez créer et utiliser des packs de contenu d’organisation dans des espaces de travail classiques. Vous ne pouvez pas les consommer ou les créer dans les nouveaux espaces de travail. Les applications et les applications de modèle remplacent les packs de contenu d’organisation dans les nouveaux espaces de travail.

Cet article explique plus en détail ces fonctionnalités.

> [!NOTE]
> Power BI continue à lister tous les groupes Microsoft 365 dont vous êtes membre. Cela évite de modifier les flux de travail existants.

### <a name="features-that-work-differently"></a>Fonctionnalités fonctionnant différemment

Certaines fonctionnalités agissent différemment dans les nouveaux espaces de travail. Ces différences sont intentionnelles et reposent sur les commentaires que nous avons reçus des clients. Elles permettent une approche plus souple de la collaboration dans les espaces de travail.

- **Application de la gestion des licences** : La publication de rapports dans la nouvelle expérience d’espace de travail est soumise à une application des règles de gestion des licences existantes. Les utilisateurs qui collaborent dans les nouveaux espaces de travail ou partagent du contenu avec d’autres personnes dans le service Power BI ont besoin d’une licence Power BI Pro. Les utilisateurs sans licence Pro voient l’erreur « Seuls les utilisateurs avec des licences Power BI Pro peuvent publier sur cet espace de travail ».
- **Paramètre « les membres peuvent repartager »**  : Le rôle Contributeur dans les nouveaux espaces de travail remplace le paramètre « les membres peuvent repartager » dans les espaces de travail classiques.
- **Espaces de travail en lecture seule** : Le rôle Lecteur dans les nouveaux espaces de travail remplace l’octroi aux utilisateurs d’un accès en lecture seule à un espace de travail classique. Le rôle Lecteur permet un accès en lecture seule similaire au contenu dans le nouvel espace de travail.
- **Les utilisateurs sans licence Pro** peuvent accéder au nouvel espace de travail si celui-ci se trouve dans une capacité Power BI Premium, mais seulement s’ils ont le rôle Lecteur.
- **Autoriser les utilisateurs à exporter des données** : Les utilisateurs avec le rôle Lecteur dans le nouvel espace de travail peuvent exporter des données s’ils ont l’autorisation Générer sur les jeux de données dans l’espace de travail. Découvrez plus en détail l’[autorisation de génération pour les jeux de données](../connect-data/service-datasets-build-permissions.md).
- Il n’y a pas de bouton **Quitter l’espace de travail** dans les nouveaux espaces de travail.

### <a name="workspace-contact-list"></a>Liste de contacts de l’espace de travail

La nouvelle fonctionnalité **Liste de contacts** vous permet de spécifier les utilisateurs qui reçoivent une notification concernant les problèmes dans l’espace de travail. Par défaut, tout utilisateur ou groupe spécifié comme administrateur de l’espace de travail est averti. Vous pouvez ajouter des éléments à cette liste. Les utilisateurs ou les groupes de la liste de contacts sont également répertoriés dans l’interface utilisateur (IU) des nouveaux espaces de travail, de sorte que les utilisateurs finaux de l’espace de travail savent qui ils doivent contacter. 

En savoir plus sur [la création de la liste de contacts de l’espace de travail](service-create-the-new-workspaces.md#create-a-contact-list).

### <a name="workspace-onedrive"></a>OneDrive de l’espace de travail

Comme nous l’avons vu, Power BI ne crée pas de groupe Microsoft 365 en arrière-plan lorsque vous créez un des nouveaux espaces de travail. Toutefois, il peut être utile d’avoir un OneDrive associé au nouvel espace de travail. La fonctionnalité OneDrive de l’espace de travail vous permet de configurer, dans le nouvel espace de travail, un groupe Microsoft 365 dont le stockage de fichiers de la bibliothèque de documents SharePoint est accessible aux utilisateurs de l’espace de travail. Vous devez d’abord créer le groupe en dehors de Power BI.
 
Power BI ne se synchronise pas entre l’appartenance à un groupe Microsoft 365 et les autorisations pour les utilisateurs ou les groupes ayant accès au nouvel espace de travail. Vous pouvez les synchroniser : Gérez l’accès à l’espace de travail par le biais du même groupe Microsoft 365 dont vous configurez le stockage de fichiers dans ce paramètre. 

En savoir plus sur comment [définir et accéder à OneDrive pour l’espace de travail](service-create-the-new-workspaces.md#set-a-workspace-onedrive).  

## <a name="roles-in-the-new-workspaces"></a>Rôles dans les nouveaux espaces de travail

Les rôles vous permettent de gérer qui peut faire quoi dans les nouveaux espaces de travail, ce qui permet aux équipes de collaborer. Les nouveaux espaces de travail vous permettent d’affecter des rôles à des personnes individuelles et à des groupes d’utilisateurs : groupes de sécurité, groupes Microsoft 365 et listes de distribution. 

Pour accorder l’accès à un nouvel espace de travail, ajoutez des groupes d’utilisateurs ou des individus à l’un des rôles de l’espace de travail : Administrateur, Membre, Contributeur ou Lecteur. Tous les utilisateurs d’un groupe d’utilisateurs reçoivent le rôle que vous avez défini. Si une personne fait partie de plusieurs groupes d’utilisateurs, elle reçoit le niveau d’autorisation le plus élevé fourni par les rôles qui lui sont attribués. Si vous imbriquez des groupes d’utilisateurs, tous les utilisateurs qui en font partie ont les autorisations associées. Toutes ces fonctionnalités, à l’exception de l’affichage et de l’interaction, nécessitent une licence Power BI Pro. Pour plus d’informations sur la [licence](#licenses), lisez la suite de l’article.

[!INCLUDE [power-bi-workspace-roles-table](../includes/power-bi-workspace-roles-table.md)]

> [!NOTE]
> - Vous pouvez affecter des utilisateurs à des rôles, seuls ou dans un groupe, même s’ils ne peuvent pas utiliser le rôle. En d’autres termes, vous pouvez affecter des utilisateurs qui n’ont pas la licence Power BI Pro à un rôle qui requiert une licence. Pour plus d’informations, consultez [Licences](#licenses), dans cet article.
> - Pour renforcer la [sécurité au niveau des lignes (RLS)](../admin/service-admin-rls.md) pour les utilisateurs qui parcourent le contenu dans un espace de travail, utilisez le rôle Lecteur. Vous pouvez également appliquer la sécurité au niveau des lignes sans donner accès au nouvel espace de travail. [Publiez une application](service-create-distribute-apps.md) et distribuez-la à ces utilisateurs, ou utilisez le [partage pour leur distribuer du contenu](service-share-dashboards.md).

## <a name="licensing-and-administering"></a>Gestion des licences et administration

### <a name="licenses"></a>Licences
Si l’un des nouveaux espaces de travail se trouve dans une capacité partagée, toute personne que vous ajoutez doit disposer d’une licence Power BI Pro. Ces utilisateurs peuvent tous collaborer sur les tableaux de bord et les rapports dans le nouvel espace de travail. Si vous voulez distribuer du contenu à d’autres utilisateurs au sein de votre organisation, vous pouvez leur attribuer des licences Power BI Pro ou placer l’espace de travail dans une capacité Power BI Premium.

Lorsque l’espace de travail se trouve dans une capacité Power BI Premium, les utilisateurs avec le rôle Lecteur peuvent accéder à l’espace de travail même s’ils n’ont pas de licence Power BI Pro. Toutefois, si vous attribuez à ces utilisateurs un rôle supérieur comme Administrateur, Membre ou Contributeur, ils seront invités à lancer la version d’essai de Power BI Pro pour accéder à l’espace de travail. Si vous souhaitez que les utilisateurs sans licence Pro utilisent le rôle Lecteur, assurez-vous qu’ils n’ont pas d’autres rôles dans l’espace de travail, en tant qu’individus ou en tant que partie d’un groupe d’utilisateurs.

La publication de rapports dans la nouvelle expérience d’espace de travail est soumise à une application plus stricte des règles de gestion des licences existantes. Si vous tentez de publier à partir de Power BI Desktop ou d’autres outils clients sans licence Pro, vous voyez l’erreur « Seuls les utilisateurs avec des licences Power BI Pro peuvent publier sur cet espace de travail ».

> [!NOTE]
> Power BI pour le gouvernement des États-Unis n’est pas disponible sous licence gratuite. Pour plus d’informations sur les licences, consultez [Power BI pour les clients du gouvernement des États-Unis](../admin/service-govus-overview.md).

### <a name="guest-users"></a>Utilisateurs invités

Par défaut, les [utilisateurs invités B2B Azure AD](../admin/service-admin-azure-ad-b2b.md) n’ont pas accès aux espaces de travail. Les administrateurs Power BI peuvent [autoriser les utilisateurs invités externes à modifier et à gérer le contenu de l’organisation](../admin/service-admin-azure-ad-b2b.md#guest-users-who-can-edit-and-manage-content). Les utilisateurs invités peuvent accéder aux espaces de travail pour lesquels ils disposent d’une autorisation.

### <a name="administering-new-workspace-experience-workspaces"></a>Gérer des espaces de travail (nouvelle expérience d’espace de travail)

L’administration des espaces de travail avec la nouvelle expérience d’espace de travail se trouve désormais dans le portail d’administration Power BI. Les administrateurs Power BI décident de qui, dans une organisation, peut créer des espaces de travail et distribuer des applications. En savoir plus sur la [gestion de la capacité des utilisateurs à créer des espaces de travail](../admin/service-admin-portal.md#create-the-new-workspaces) dans l’article « Portail Administrateur ». 

Les administrateurs peuvent afficher l’état de tous les espaces de travail de leur organisation. Ils peuvent gérer, récupérer et même supprimer des espaces de travail. En savoir plus sur la [gestion des espaces de travail eux-mêmes](../admin/service-admin-portal.md#workspaces) dans l’article « Portail Administrateur ».

### <a name="auditing"></a>Audit

Power BI audite les activités suivantes pour les nouveaux espaces de travail.

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

**Les liens vers le contenu existant sont-ils concernés par la nouvelle expérience d’espace de travail ?**

Non. Les liens vers des éléments existants dans les espaces de travail classiques ne sont pas affectés par la nouvelle expérience de l’espace de travail. La disponibilité générale (GA) de la nouvelle expérience de l’espace de modifie change l’espace de travail par défaut que vous créez, mais ne modifie pas les espaces de travail existants. 

**Les espaces de travail existants sont-ils mis à niveau vers la nouvelle expérience de l’espace de travail avec la disponibilité générale ?**

Non. La disponibilité générale de la nouvelle expérience de l’espace de travail remplace uniquement le type d’espace de travail par défaut par la nouvelle expérience de l’espace de travail. Les espaces de travail classiques existants basés sur des groupes Microsoft 365 restent inchangés.

**Les espaces de travail sont-ils toujours créés automatiquement pour les groupes Microsoft 365 ?**

Oui. Étant donné que nous prenons en charge les deux types d’espaces de travail côte à côte, nous continuons à répertorier tous les groupes Microsoft 365 auxquels vous avez accès dans la liste des espaces de travail.

## <a name="next-steps"></a>Étapes suivantes

* [Créer les nouveaux espaces de travail dans Power BI](service-create-the-new-workspaces.md)
* [Créer les espaces de travail classiques](service-create-workspaces.md)
* [Installer et utiliser des applications dans Power BI](service-create-distribute-apps.md)
* Vous avez des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)

