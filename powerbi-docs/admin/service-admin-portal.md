---
title: Portail d’administration Power BI
description: Le portail d’administration vous permet de configurer les paramètres de toute l’organisation pour Power BI. Vous pouvez afficher les métriques d’utilisation, configurer les paramètres du locataire, utiliser la capacité, afficher les espaces de travail, les visuels de l’organisation et le contenu proposé.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 10/22/2020
ms.author: kfollis
ms.custom: seodec18
LocalizationGroup: Administration
ms.openlocfilehash: 0abdaab48516b91624a0945d32c4f81ed024a468
ms.sourcegitcommit: 5bbe7725918a72919ba069c5f8a59e95453ec14c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2020
ms.locfileid: "94947248"
---
# <a name="administering-power-bi-in-the-admin-portal"></a>Administration de Power BI dans le portail d’administration

Le portail d’administration vous permet de gérer les paramètres Power BI pour votre organisation. Le portail comprend notamment des métriques d’utilisation, un accès au Centre d’administration Microsoft 365 et des paramètres de l’abonné.

Le portail d’administration complet est accessible par les administrateurs généraux et les utilisateurs qui ont le rôle d’Administrateur de service Power BI. Si vous n’appartenez pas à l’un de ces rôles, seuls les **Paramètres de capacité** s’affichent sur le portail. Pour plus d’informations sur le rôle d’administrateur de Service Power BI, voir [Présentation du rôle d’administrateur Power BI](service-admin-role.md).

## <a name="how-to-get-to-the-admin-portal"></a>Accès au portail d’administration

Vous devez être administrateur général ou administrateur de service Power BI pour accéder au portail Administrateur Power BI. Pour plus d’informations sur le rôle d’administrateur de Service Power BI, voir [Présentation du rôle d’administrateur Power BI](service-admin-role.md). Pour accéder au portail Administrateur Power BI, procédez comme suit :

1. Connectez-vous à [Power BI](https://app.powerbi.com) à l’aide des informations d’identification du compte administrateur.

1. Dans l’en-tête de page, sélectionnez **Paramètres** > **Portail Administrateur**.

    ![Paramètres du portail d’administration](media/service-admin-portal/powerbi-admin-settings.png)

Le portail d’administration contient plusieurs sections. Le reste de cet article fournit des informations sur chacune de ces sections.

![Navigation dans le portail d’administration](media/service-admin-portal/powerbi-admin-landing-page.png)

* [Métriques d’utilisation](#usage-metrics)
* [Utilisateurs](#users)
* [Journaux d’audit](#audit-logs)
* [Paramètres du locataire](#tenant-settings)
* [Paramètres de capacité](#capacity-settings)
* [Codes incorporés](#embed-codes)
* [Visuels organisationnels](organizational-visuals.md#organizational-visuals)
* [Connexions Azure (préversion)](#azure-connections-preview)
* [Espaces de travail](#workspaces)
* [Marque personnalisée](#custom-branding)
* [Mesures de protection](#protection-metrics)
* [Contenu proposé](#featured-content)

## <a name="usage-metrics"></a>Métriques d'utilisation

Les **Métriques d’utilisation** vous permettent de contrôler l’utilisation de Power BI dans votre organisation. Elles indiquent également les utilisateurs et les groupes de votre organisation qui sont les plus actifs dans Power BI.

> [!NOTE]
> La première fois que vous accédez au tableau de bord ou si vous y accédez de nouveau après une longue période, un écran de chargement s’affiche probablement pendant le chargement du tableau de bord.

Une fois le tableau de bord chargé, deux sections de mosaïques s’affichent. La première section comprend des données d’utilisation pour chacun des utilisateurs et la deuxième comporte des informations similaires pour les groupes.

Voici le détail de ce que vous pouvez voir dans chaque vignette :

* Le nombre de tableaux de bord, de rapports et de jeux de données de l’espace de travail utilisateur.
  
    ![Nombre de tableaux de bord, de rapports et de jeux de données](media/service-admin-portal/powerbi-admin-usage-metrics-number-tiles.png)


* Le tableau de bord le plus utilisé par nombre d’utilisateurs autorisés à y accéder. Par exemple : vous avez un tableau de bord partagé avec trois utilisateurs. Vous avez également ajouté le tableau de bord à un pack de contenu auquel deux utilisateurs différents se sont connectés. Le nombre du tableau de bord est de 6 (1 + 3 + 2).
  
    ![Tableaux de bord les plus utilisés](media/service-admin-portal/powerbi-admin-usage-metrics-top-dashboards.png)

* Le contenu auquel est connecté le plus grand nombre d’utilisateurs. Il peut s’agir de tout ce que les utilisateurs peuvent obtenir via le processus Obtenir des données, par exemple, des packs de contenu SaaS, des packs de contenu d’organisation, des fichiers ou des bases de données.

  
    ![Packages les plus utilisés](media/service-admin-portal/powerbi-admin-usage-metrics-top-connections.png)

* Vue des utilisateurs les plus actifs, en fonction du nombre de tableaux de bord qu’ils possèdent, à la fois ceux qu’ils ont créés eux-mêmes et ceux qui ont été partagés avec eux.
  
    ![Utilisateurs les plus actifs - tableaux de bord](media/service-admin-portal/powerbi-admin-usage-metrics-top-users-dashboards.png)

* Vue des utilisateurs les plus actifs, en fonction du nombre de rapports qu’ils possèdent.
  
    ![Utilisateurs les plus actifs - rapports](media/service-admin-portal/powerbi-admin-usage-metrics-top-users-reports.png)

La deuxième section affiche le même type d’informations, mais pour les groupes. Cette section vous permet de savoir quels sont les groupes les plus actifs dans votre organisation et le type de contenu qu’ils utilisent.

Grâce à ces informations, vous pouvez avoir un aperçu de la façon dont les personnes utilisent Power BI au sein de votre organisation.

## <a name="control-usage-metrics"></a>Contrôler les métriques d’utilisation

Les rapports de métriques d’utilisation sont une fonctionnalité que l’administrateur Power BI ou l’administrateur général peut activer ou désactiver. Les administrateurs ont un contrôle granulaire sur l’accès des utilisateurs aux métriques d’utilisation. Ils sont **Activés** par défaut pour tous les utilisateurs de l’organisation.

Les administrateurs peuvent aussi déterminer si les créateurs de contenu peuvent voir les données par utilisateur dans les métriques d’utilisation. 

Pour plus d’informations sur les rapports eux-mêmes, consultez [Superviser les métriques d’utilisation de tableaux de bord et de rapports Power BI](../collaborate-share/service-usage-metrics.md).

### <a name="usage-metrics-for-content-creators"></a>Métriques d'utilisation pour les créateurs de contenu

1. Dans le portail Administrateur, sélectionnez **Paramètres de l’abonné** > **Paramètres d’audit et d’utilisation** > **Métriques d’utilisations pour les créateurs de contenu**.

    ![Métriques d’utilisation dans les paramètres du locataire sur le portail d’administration](media/service-admin-portal/power-bi-admin-usage-metrics.png)

1. Activez (ou désactivez) les métriques d’utilisation > **Appliquer**.

    ![métriques d’utilisation activées](../collaborate-share/media/service-usage-metrics/power-bi-tenant-settings-updated.png)

### <a name="per-user-data-in-usage-metrics-for-content-creators"></a>Données par utilisateur dans les métriques d'utilisation pour les créateurs de contenu

Par défaut, les données par utilisateur sont activées pour les métriques d’utilisation et les informations sur le compte sont incluses dans le rapport des mesures. Si vous ne souhaitez pas inclure ces informations sur le compte pour tout ou partie des utilisateurs, désactivez la fonctionnalité pour des groupes de sécurité spécifiés ou pour l’ensemble de l’organisation. Les informations de compte figurent alors dans le rapport sous l’intitulé *Sans nom*.

![Données d’utilisation par utilisateur](media/service-admin-portal/power-bi-admin-per-user-usage-data.png)

### <a name="delete-all-existing-usage-metrics-content"></a>Supprimer tous le contenu des métriques d’utilisation existantes

Lors de la désactivation des métriques d’utilisation pour leur organisation toute entière, les administrateurs peuvent également choisir une ou plusieurs options pour :

- **Supprimer tout le contenu des métriques d’utilisation** pour supprimer toutes les vignettes de rapports et de tableaux de bord existantes générées à l’aide de rapports et de jeux de données des métriques d’utilisation. Cette option supprime tout accès aux données de métriques d’utilisation pour tous les utilisateurs au sein de l’organisation qui peuvent déjà les utiliser.
- **Supprimer toutes les données existantes par utilisateur dans le contenu des métriques d’utilisation actuelles** afin de supprimer tout accès aux données par utilisateur pour tous les utilisateurs de l’organisation qui les utilisent peut-être déjà.

Soyez prudent, car la suppression du contenu de métriques existantes d’utilisation et par utilisateur est irréversible.

## <a name="users"></a>Utilisateurs

Les utilisateurs, les groupes et les administrateurs Power BI sont gérés dans le Centre d’administration Microsoft 365. L’onglet **Utilisateurs** contient un lien qui donne accès au Centre Administrateur.

![Accéder au Centre d’administration Microsoft 365](media/service-admin-portal/powerbi-admin-manage-users.png)

## <a name="audit-logs"></a>Journaux d'audit

Les journaux d’audit Power BI sont gérés dans le Centre de sécurité et de conformité Office 365. L’onglet **Journaux d’audit** contient un lien qui donne accès au Centre de sécurité et de conformité. Pour en savoir plus, consultez [Suivre les activités utilisateur dans Power BI](service-admin-auditing.md).

Pour utiliser les journaux d’audit, vérifiez que le paramètre [**Créer des journaux d’audit pour l’audit et la conformité des activités internes**](#create-audit-logs-for-internal-activity-auditing-and-compliance) est activé.

## <a name="tenant-settings"></a>Paramètres du locataire

**Paramètres de l’abonné** fournit un contrôle affiné sur les fonctionnalités mises à la disposition de votre organisation. Si vous avez des inquiétudes à propos de vos données sensibles, il se peut que certaines de nos fonctionnalités ne soient pas adaptées à votre organisation. Vous pouvez aussi choisir de mettre à disposition une fonctionnalité déterminée à un groupe précis.

> [!NOTE]
> Les paramètres de l’abonné qui contrôlent la disponibilité des fonctionnalités dans l’interface utilisateur Power BI peuvent aider à établir des stratégies de gouvernance, mais ils ne constituent pas une mesure de sécurité. Par exemple, le paramètre **Exporter les données** ne limite pas les autorisations d’un utilisateur Power BI sur un jeu de données. Les utilisateurs Power BI disposant d’un accès en lecture à un jeu de données ont l’autorisation d’interroger ce jeu de données et peuvent conserver les résultats sans utiliser la fonctionnalité **Exporter les données** dans l’interface utilisateur de Power BI.

Les sections suivantes décrivent les paramètres de l’onglet **Paramètres du client**.

> [!NOTE]
> Jusqu’à 15 minutes peuvent être nécessaires à la prise en compte de la modification d’un paramètre pour tous les utilisateurs de votre organisation.

De nombreux paramètres peuvent présenter un des trois états suivants :

* **Désactivé pour toute l’organisation** : Personne dans votre organisation ne peut utiliser cette fonctionnalité.

    ![Paramètre Désactivé pour tous](media/service-admin-portal/powerbi-admin-tenant-settings-disabled.png)

* **Activé pour toute l’organisation** : Tout le monde dans votre organisation peut utiliser cette fonctionnalité.

    ![Paramètre Activé pour tous](media/service-admin-portal/powerbi-admin-tenant-settings-enabled.png)

* **Activé pour une partie de l’organisation** : certains groupes de sécurité de votre organisation sont autorisés à utiliser cette fonctionnalité.

    Vous pouvez activer la fonctionnalité pour toute votre organisation, **Excepter aux groupes de sécurité spécifiques**.

    ![Paramètre Activé pour un sous-ensemble](media/service-admin-portal/powerbi-admin-tenant-settings-enabled-except.png)

    Vous pouvez aussi combiner des paramètres afin de n’activer que la fonctionnalité pour un groupe d’utilisateurs spécifique, mais aussi la désactiver pour un autre groupe d’utilisateurs. Cette approche permet de faire en sorte que certains utilisateurs n’aient pas accès à la fonctionnalité, même s’ils se trouvent dans le groupe autorisé. Le paramètre le plus restrictif pour un utilisateur s’applique.

    ![Paramètre d’activation sélective](media/service-admin-portal/powerbi-admin-tenant-settings-enabled-except2.png)

Les sections suivantes fournissent une vue d’ensemble des différents types de paramètres de locataire.

## <a name="tenant-wide-new-look-settings"></a>Paramètres de la nouvelle apparence à l’échelle du locataire

Quand l’option **Nouvelle apparence** est désactivée, les utilisateurs de cette organisation peuvent activer et désactiver la nouvelle apparence de Power BI. Quand vous activez l’option **Nouvelle apparence**, *tous* les utilisateurs de cette organisation voient les contrôles modernes de la nouvelle apparence de Power BI tout le temps. Ils ne peuvent plus désactiver la nouvelle apparence. L’option Nouvelle apparence est activée par défaut.

:::image type="content" source="media/service-admin-portal/admin-portal-new-look-disable.png" alt-text="Capture d’écran de l’option Désactiver la nouvelle apparence dans le portail d’administration.":::

## <a name="help-and-support-settings"></a>Paramètres d’aide et de support

### <a name="publish-get-help-information"></a>Publier des informations « Obtenir de l’aide »

![Publier des informations « Obtenir de l’aide »](media/service-admin-portal/powerbi-admin-tenant-settings-gethelp.png)

Les administrateurs peuvent spécifier des URL internes pour remplacer la destination des liens dans le menu aide de Power BI et pour les mises à niveau de licence. Si des URL personnalisées sont définies, les utilisateurs de l’organisation accèdent aux ressources d’aide et de support internes au lieu des destinations par défaut. Les destinations de ressources suivantes peuvent être personnalisées :

* **Learn**. Par défaut, ce lien de menu d’aide cible une [liste de tous nos parcours d’apprentissage et modules Power BI](/learn/browse/?products=power-bi). Pour diriger ce lien vers des ressources de formation internes, définissez plutôt une URL personnalisée pour la **Documentation de formation**.

* **Communauté**. Pour transférer les utilisateurs vers un forum interne à partir du menu d’aide, plutôt que vers la [Communauté Power BI](https://community.powerbi.com/), définissez une URL personnalisée pour le **Forum de discussion**.

* **Mises à niveau des licences**. Les utilisateurs disposant d’une licence Power BI (gratuite) peuvent avoir la possibilité de mettre à niveau leur compte vers Power BI Pro lors de l’utilisation du service. Si vous spécifiez une URL interne pour les **requêtes de licences**, vous redirigez les utilisateurs vers un flux interne de requêtes et d’achats et vous empêchez l’achat en libre-service. Si vous souhaitez empêcher les utilisateurs d’acheter des licences, mais que les utilisateurs peuvent démarrer une évaluation gratuite de Power BI Pro, consultez [Autoriser les utilisateurs à essayer Power BI Pro](#allow-users-to-try-power-bi-pro) pour séparer les expériences d’achat et de test.

* **Obtenir de l’aide**. Pour transférer les utilisateurs vers un forum interne à partir du menu d’aide, plutôt que vers le [Support Power BI](https://powerbi.microsoft.com/support/), définissez une URL personnalisée pour le **Support technique**.

### <a name="receive-email-notifications-for-service-outages-or-incidents"></a>Recevoir des notifications par e-mail pour les pannes ou incidents du service

Les groupes de sécurité à extension messagerie reçoivent des notifications par e-mail si ce locataire est affecté par une panne ou un incident du service. En savoir plus sur les [notifications d’interruption de service](service-interruption-notifications.md).

### <a name="allow-users-to-try-power-bi-pro"></a>Autoriser les utilisateurs à essayer Power BI Pro

![Autoriser les utilisateurs à essayer l’interface utilisateur des paramètres Power BI Pro](media/service-admin-portal/allow-pro-trial.png)

Le paramètre **Autoriser les utilisateurs à essayer Power BI Pro** est activé par défaut. Il augmente votre contrôle sur la façon dont les utilisateurs acquièrent des licences Power BI Pro. Dans les scénarios où vous avez bloqué l’achat en libre-service, ce paramètre permet aux utilisateurs de démarrer une évaluation gratuite de Power BI Pro. L’expérience de l’utilisateur final dépend de la façon dont vous combinez les paramètres de licence. Le tableau ci-dessous montre comment l’expérience de mise à niveau de Power BI (gratuite) à Power BI Pro est affectée par différentes combinaisons de paramètres :

| Paramètre d’achat en libre-service | Autoriser les utilisateurs à essayer le paramètre Power BI Pro | Expérience de l’utilisateur final |
| ------ | ------ | ----- |
| activé | Désactivé | L’utilisateur peut acheter une licence Pro, mais ne peut pas démarrer une évaluation gratuite |
| activé | activé | L’utilisateur peut démarrer une évaluation gratuite de Pro et peut effectuer une mise à niveau vers une licence payante |
| Désactivé | Désactivé | L’utilisateur voit un message lui demandant de contacter l’administrateur informatique pour demander une licence |
| Désactivé | activé | L’utilisateur peut démarrer une évaluation gratuite de Pro, mais il doit contacter l’administrateur informatique pour obtenir une licence payante |

> [!NOTE]
> Vous pouvez ajouter une URL interne pour les demandes de licences dans [Paramètres d’aide et de support](#help-and-support-settings). Si vous définissez l’URL, elle remplace l’expérience d’achat en libre-service par défaut. Elle ne redirige pas l’inscription à un essai de la licence Power BI Pro. Les utilisateurs qui peuvent acheter une licence dans les scénarios décrits dans le tableau ci-dessus sont redirigés vers votre URL interne.

Pour en savoir plus, consultez [Activer ou désactiver l’inscription et l’achat en libre-service](service-admin-disable-self-service.md).

## <a name="workspace-settings"></a>Paramètres de l’espace de travail

Dans **Paramètres de l’abonné**, le portail Administrateur comporte deux sections pour le contrôle des espaces de travail :

- [Créer les nouvelles expériences d'espace de travail](#create-the-new-workspaces).
- [Utiliser des jeux de données entre des espaces de travail](#use-datasets-across-workspaces).
- [Bloquer la création de l’espace de travail classique](#block-classic-workspace-creation).

### <a name="create-the-new-workspaces"></a>Créer de nouveaux espaces de travail

Les espaces de travail sont des endroits où les utilisateurs collaborent sur des tableaux de bord, des rapports et d’autres contenus. Les administrateurs utilisent le paramètre **Créer des espaces de travail (nouvelle expérience d’espace de travail)** pour indiquer quels utilisateurs de l’organisation peuvent créer des espaces de travail. Les administrateurs peuvent autoriser tout le monde ou personne dans une organisation à créer des espaces de travail avec la nouvelle expérience d’espace de travail. Il peuvent également limiter la création aux membres de groupes de sécurité spécifiques. En savoir plus sur les [espaces de travail](../collaborate-share/service-new-workspaces.md)

:::image type="content" source="media/service-admin-portal/power-bi-admin-workspace-settings.png" alt-text="Créer les nouvelles expériences d'espace de travail":::

Pour les espaces de travail classiques basés sur les groupes Microsoft 365, l’administration continue à s’effectuer dans le portail d’administration Microsoft 365 et Azure Active Directory.

> [!NOTE]
> Par défaut, le paramètre **Créer des espaces de travail (nouvelle expérience d’espace de travail)** est défini pour autoriser uniquement les utilisateurs pouvant créer des groupes Microsoft 365 à créer les nouveaux espaces de travail Power BI. Veillez à définir une valeur dans le portail d’administration Power BI pour garantir que les utilisateurs appropriés peuvent les créer.

**Liste des espaces de travail**

Le portail d’administration comporte une autre section de paramètres sur les espaces de travail dans votre locataire. Dans cette section, vous pouvez trier et filtrer la liste des espaces de travail et afficher les détails de chaque espace de travail. Pour plus d’informations, consultez [Espaces de travail](#workspaces), plus loin dans cet article.

**Publier des packs de contenu et des applications**

Dans le portail d’administration, vous contrôlez également les utilisateurs qui disposent des autorisations nécessaires pour distribuer des applications à l’organisation. Consultez la section [Publier des packs de contenu et des applications pour toute l’organisation](#publish-content-packs-and-apps-to-the-entire-organization) de cet article pour plus de détails.

### <a name="use-datasets-across-workspaces"></a>Utiliser des jeux de données entre des espaces de travail

Les administrateurs peuvent contrôler les utilisateurs de l’organisation qui peuvent utiliser des jeux de données dans les espaces de travail. Quand ce paramètre est activé, les utilisateurs ont toujours besoin de l’autorisation de build requise pour un jeu de données spécifique.

:::image type="content" source="media/service-admin-portal/power-bi-admin-datasets-workspaces.png" alt-text="Utiliser des jeux de données entre des espaces de travail":::

Pour plus d’informations, consultez [Initiation aux jeux de données sur plusieurs espaces de travail](../connect-data/service-datasets-across-workspaces.md).

### <a name="block-classic-workspace-creation"></a>Bloquer la création de l’espace de travail classique

Les administrateurs peuvent contrôler si l’organisation peut créer des espaces de travail classiques. Quand ce paramètre est activé, les utilisateurs qui créent un espace de travail peuvent uniquement créer des espaces de travail d’expérience d’espace de travail. 

![Bloquer la création de l’espace de travail classique](media/service-admin-portal/power-bi-admin-block-classic-workspaces.png)

Quand ils sont activés, les nouveaux groupes Office 365 ne s’affichent pas dans la liste des espaces de travail Power BI. Les espaces de travail classiques existants continuent à être affichés dans la liste. Quand le paramètre est désactivé, tous les groupes Office 365 dont l’utilisateur est membre s’affichent dans la liste des espaces de travail. Découvrez plus d’informations sur les [nouveaux espaces de travail d’expérience d’espace de travail](../collaborate-share/service-new-workspaces.md).

## <a name="export-and-sharing-settings"></a>Paramètres d'exportation et de partage

### <a name="allow-azure-active-directory-guest-users-to-access-power-bi"></a>Autoriser les utilisateurs invités Azure Active Directory à accéder à Power BI

L’activation de ce paramètre permet aux utilisateurs invités à Azure Active Directory Business-to-Business (Azure AD B2B) d’accéder à Power BI. Si vous désactivez ce paramètre, les utilisateurs invités reçoivent une erreur lorsqu’ils tentent d’accéder à Power BI. Le désactiver pour l’ensemble de l’organisation permet également d’empêcher les utilisateurs de convier des invités à votre organisation. Utilisez l’option Groupes de sécurité spécifiques pour contrôler les utilisateurs invités qui peuvent accéder à Power BI.

![Autoriser les utilisateurs invités Azure Active Directory à accéder à Power BI](media/service-admin-portal/powerbi-admin-allow-aad-b2b-guests.png)

### <a name="invite-external-users-to-your-organization"></a>Inviter des utilisateurs externes dans votre organisation 

Le paramètre **Inviter des utilisateurs externes dans votre organisation** permet aux organisations de déterminer si de nouveaux utilisateurs externes peuvent être invités dans l’organisation par le biais des expériences d’autorisations et de partage Power BI. S’il est désactivé, il n’est pas possible d’ajouter à l’organisation un utilisateur externe qui n’est pas déjà un utilisateur invité de l’organisation par le biais de Power BI.

![Inviter des utilisateurs externes dans votre organisation](media/service-admin-portal/powerbi-admin-allow-invite-aad-b2b-guests.png)

> [!IMPORTANT]
> Ce paramètre était précédemment appelé « Partager du contenu avec des utilisateurs externes ». Le nom modifié reflète de manière plus précise l’action du paramètre.

Pour inviter des utilisateurs externes dans votre organisation, un utilisateur a également besoin du rôle Inviteur d’invités Azure Active Directory. Ce paramètre contrôle uniquement la possibilité d’inviter par le biais de Power BI. 

### <a name="allow-external-guest-users-to-edit-and-manage-content-in-the-organization"></a>Autoriser les utilisateurs invités externes à modifier et à gérer le contenu de l’organisation

Les utilisateurs invités Azure AD B2B peuvent modifier et gérer le contenu de l’organisation. [En savoir plus](service-admin-azure-ad-b2b.md)

L’image suivante présente l’option permettant d’autoriser les utilisateurs invités externes à modifier et à gérer le contenu de l’organisation.

![Autoriser les utilisateurs invités externes à modifier et à gérer le contenu de l’organisation](media/service-admin-portal/powerbi-admin-tenant-settings-b2b-guest-edit-manage.png)

Dans le portail d’administration, vous contrôlez également les utilisateurs qui disposent des autorisations nécessaires pour inviter des utilisateurs externes à l’organisation. Pour plus d’informations, consultez [Partager du contenu avec des utilisateurs externes](#export-and-sharing-settings) dans cet article.

### <a name="publish-to-web"></a>Publier sur le web

En tant qu’administrateur Power BI, le paramètre **Publier sur le web** propose des options qui vous permettent de créer des codes incorporés pour publier des rapports sur le web. Cette fonctionnalité rend le rapport et ses données accessibles à n’importe qui sur le web. Découvrez plus d’informations sur la [publication sur le web](../collaborate-share/service-publish-to-web.md).

> [!NOTE]
> Seul les administrateurs Power BI peuvent autoriser la création de codes incorporés « Publier sur le web ». Les organisations peuvent avoir des codes incorporés existants. Consultez la section [Codes incorporés](service-admin-portal.md#embed-codes) du portail d’administration pour passer en revue les rapports actuellement publiés.

L’image suivante montre le menu **Plus d’options (...)** pour un rapport quand le paramètre **Publier sur le web** est activé.

![Publier sur le web dans le menu Plus d’options](media/service-admin-portal/power-bi-more-options-publish-web.png)

Le paramètre **Publier sur le web** du portail d’administration fournit des options pour lesquelles les utilisateurs peuvent créer des codes incorporés.

![Paramètre Publier sur le web](media/service-admin-portal/powerbi-admin-publish-to-web-setting.png)

Les administrateurs peuvent définir **Publier sur le web** sur **Activé** et **Choisir le mode de fonctionnement des codes incorporés** sur **Autoriser seulement les codes incorporés existants**. Dans ce cas, les utilisateurs peuvent créer des codes incorporés, mais ils doivent contacter l’administrateur Power BI pour les y autoriser.

![Invite Publier sur le web](../collaborate-share/media/service-publish-to-web/publish_to_web_admin_prompt.png)

Les options présentées aux utilisateurs dans l’interface utilisateur varient en fonction de la nature du paramètre **Publier sur le web**.

|Caractéristique |Activée pour toute l’organisation |Désactivée pour toute l’organisation |Groupes de sécurité spécifiques   |
|---------|---------|---------|---------|
|**Publier sur le web** sous le menu **Plus d’options (...)** d’un rapport|Activée pour tous|Non visible pour tous|Visible uniquement par les utilisateurs ou groupes autorisés.|
|**Gérer les codes d’incorporation** sous **Paramètres**|Activée pour tous|Activée pour tous|Activée pour tous<br><br>Option * **Supprimer** uniquement pour les utilisateurs ou groupes autorisés.<br>* **Obtenir les codes** activé pour tous.|
|**Codes d’incorporation** au sein du portail d’administration|L’état reflète l’une des options suivantes :<br>* Actif<br>* Non pris en charge<br>* Bloqué|L’état affiche **Désactivé**|L’état reflète l’une des options suivantes :<br>* Actif<br>* Non pris en charge<br>* Bloqué<br><br>Si un utilisateur n’est pas autorisé en fonction du paramètre de locataire, l’état indique **Enfreint**.|
|Rapports publiés existants|Tout activé|Tout désactivé|Les rapports continuent à être restitués pour tous.|

### <a name="copy-and-paste-visuals"></a>Copier et coller des visuels

Les utilisateurs de l’organisation peuvent copier des visuels à partir d’un visuel de vignette ou de rapport et les coller sous forme d’images statiques dans des applications externes.

![Capture d’écran du copier-coller des visuels.](media/service-admin-portal/powerbi-admin-portal-copy-paste-visuals-setting.png)

### <a name="export-to-excel"></a>Exporter vers Excel

Les utilisateurs de l’organisation peuvent exporter les données à partir d’une visualisation dans un fichier Excel.

![Capture d’écran du paramètre Exporter vers Excel](media/service-admin-portal/powerbi-admin-portal-export-to-excel-setting.png)

### <a name="export-to-csv"></a>Exporter au format .csv

Les utilisateurs de l’organisation peuvent exporter les données d’une vignette, d’une visualisation ou d’un rapport paginé vers un fichier csv.

![Capture d’écran du paramètre Exporter au format .csv](media/service-admin-portal/powerbi-admin-portal-export-to-csv-setting.png)

### <a name="download-reports"></a>Rapports de téléchargement

Les utilisateurs de l’organisation peuvent télécharger des fichiers .pbix et des rapports paginés.

![Capture d’écran du paramètre Télécharger les rapports.](media/service-admin-portal/powerbi-admin-portal-download-reports-setting.png)

### <a name="allow-live-connections"></a>Autoriser les connexions actives

Les utilisateurs de l’organisation peuvent utiliser le service Power BI Live Connect. Cela comprend le service Analyse dans Excel.

![Capture d’écran du paramètre Autoriser les connexions actives.](media/service-admin-portal/powerbi-admin-portal-allow-live-connections-setting.png)

### <a name="export-reports-as-powerpoint-presentations-or-pdf-documents"></a>Exporter les rapports comme présentations PowerPoint ou documents PDF

Les utilisateurs de l’organisation peuvent exporter des rapports sous forme de fichiers PowerPoint ou de documents PDF.

![Capture d’écran de l’option Exporter les rapports comme présentations PowerPoint ou documents PDF](media/service-admin-portal/powerbi-admin-portal-export-pptx-pdf-setting.png)

### <a name="export-reports-as-mhtml-documents"></a>Exporter des rapports sous forme de documents MHTML

Les utilisateurs de l’organisation peuvent exporter des rapports paginés sous forme de documents MHTML.

![Capture d’écran du paramètre Exporter au format MHTML.](media/service-admin-portal/powerbi-admin-portal-export-mhtml-setting.png)

### <a name="export-reports-as-word-documents"></a>Exporter des rapports sous forme de documents Word

Les utilisateurs de l’organisation peuvent exporter des rapports paginés sous forme de documents Word.

![Capture d’écran du paramètre Exporter au format Word.](media/service-admin-portal/powerbi-admin-portal-export-word-setting.png)

### <a name="export-reports-as-xml-documents"></a>Exporter des rapports sous forme de documents XML

Les utilisateurs de l’organisation peuvent exporter des rapports paginés sous forme de documents XML.

![Capture d’écran du paramètre Exporter au format XML.](media/service-admin-portal/powerbi-admin-portal-export-xml-setting.png)

### <a name="export-reports-as-image-files-preview"></a>Exporter des rapports sous forme de fichiers image (préversion)

Les utilisateurs de l’organisation peuvent utiliser l’API Exporter le rapport vers un fichier pour exporter des rapports sous forme de fichiers image.

![Capture d’écran du paramètre Exporter au format image.](media/service-admin-portal/powerbi-admin-portal-export-as-image-setting.png)

### <a name="print-dashboards-and-reports"></a>Imprimer des tableaux de bord et des rapports


![Capture d’écran du paramètre Imprimer des tableaux de bord et des rapports.](media/service-admin-portal/powerbi-admin-portal-print-dashboards-reports-setting.png)

### <a name="certification"></a>Certification
Autorisez les utilisateurs dans cette organisation à certifier les jeux de données, les dataflows, les rapports et les applications. Pour plus d’informations, consultez [Activer la certification de contenu](service-admin-setup-certification.md).

### <a name="email-subscriptions"></a>Abonnements par e-mail
Les utilisateurs de l'organisation peuvent créer des abonnements par courrier. En savoir plus sur les [abonnements](../collaborate-share/service-publish-to-web.md).

![Activer les abonnements par courrier](media/service-admin-portal/power-bi-manage-email-subscriptions.png)

### <a name="featured-content"></a>Contenu proposé

Autorisez certains ou tous les auteurs de rapports de votre organisation à présenter leur contenu dans la section À la une de la page d’accueil Power BI. Les nouveaux utilisateurs verront le contenu proposé en haut de leur page d’accueil Power BI. Le contenu proposé descend dans la page d’accueil à mesure que les utilisateurs ajoutent des éléments **favoris**, **fréquents** et **récents**. 

Nous vous recommandons de commencer avec un ensemble réduit d’approbateurs. Permettre à l’ensemble de l’organisation de présenter du contenu dans la page d’accueil peut compliquer le suivi de tout le contenu promu. 

Une fois que vous avez activé le contenu proposé, vous pouvez également le gérer dans le portail d’administration. Consultez [Gérer le contenu proposé](#manage-featured-content) dans cet article pour en savoir plus sur le contrôle du contenu proposé dans votre domaine.

### <a name="allow-connections-to-featured-tables"></a>Autoriser les connexions aux tables proposées

Ce paramètre permet aux administrateurs Power BI de contrôler quels utilisateurs de l’organisation sont autorisés à utiliser les tables recommandées dans la galerie Types de données Excel. 

![Capture d’écran du paramètre Autoriser les connexions aux tables proposées.](media/service-admin-portal/powerbi-admin-portal-allow-connections-featured-tables-setting.png)

>[!NOTE]
>Les connexions aux tables proposées sont également désactivées si le paramètre [Autoriser les connexions actives](#allow-live-connections) est défini sur Désactivé.

En savoir plus sur [les tables Power BI dans Excel](../collaborate-share/service-excel-featured-tables.md).

### <a name="share-to-teams"></a>Partager dans Teams

Ce paramètre permet aux organisations de masquer les boutons **Partager dans Teams** dans le service Power BI. Quand l’option est désactivée, les utilisateurs ne voient pas les boutons **Partager dans Teams** dans la barre d’action ou les menus contextuels quand ils affichent des rapports et tableaux de bord dans le service Power BI.

![Capture d’écran du paramètre de locataire Partager dans Teams dans le portail d’administration Power BI](media/service-admin-portal/service-teams-share-to-teams-tenant-setting.png)

Découvrez plus d’informations sur le [partage de contenu Power BI dans Teams](../collaborate-share/service-share-report-teams.md).

## <a name="content-pack-and-app-settings"></a>Paramètres des applications et des packs de contenu

### <a name="publish-content-packs-and-apps-to-the-entire-organization"></a>Publier des packs de contenu et des applications pour toute l’organisation

Les administrateurs utilisent ce paramètre pour décider si les utilisateurs peuvent publier des packs de contenu et des applications pour toute l’organisation, plutôt que pour des groupes spécifiques. En savoir plus sur la [publication d’applications](../collaborate-share/service-create-distribute-apps.md).

L’image suivante montre l’option **Toute mon organisation** lors de la création d’un pack de contenu.

![Publier un pack de contenu vers l’organisation](media/service-admin-portal/powerbi-admin-publish-entire-org.png)

### <a name="create-template-apps-and-organizational-content-packs"></a>Créer des modèles d’applications et des packs de contenu d’organisation

Les utilisateurs peuvent créer des modèles d’applications et des packs de contenu d’organisation qui utilisent des jeux de données basés sur une même source de données dans Power BI Desktop. En savoir plus sur les [applications modèles](../connect-data/service-template-apps-create.md).

### <a name="push-apps-to-end-users"></a>Effectuer une transmission de type push des applications pour les utilisateurs finaux

Les auteurs de rapports peuvent partager directement des applications avec les utilisateurs finaux sans installation à partir d’[AppSource](https://appsource.microsoft.com). En savoir plus sur l’[installation automatique d’applications pour les utilisateurs finaux](../collaborate-share/service-create-distribute-apps.md#automatically-install-apps-for-end-users).

## <a name="integration-settings"></a>Paramètres d’intégration

### <a name="allow-xmla-endpoints-and-analyze-in-excel-with-on-premises-datasets"></a>Autoriser les points de terminaison XMLA et l’analyse dans Excel avec les jeux de données locaux

Les utilisateurs de l’organisation peuvent utiliser Excel pour afficher et interagir avec des jeux de données Power BI locaux. Cela autorise également les connexions aux points de terminaison XMLA. [En savoir plus](../collaborate-share/service-analyze-in-excel.md)

### <a name="use-arcgis-maps-for-power-bi"></a>Utiliser ArcGIS Maps for Power BI

Les utilisateurs de l’organisation peuvent utiliser la visualisation ArcGIS Maps for Power BI fournie par Esri. [En savoir plus](../visuals/power-bi-visualizations-arcgis.md)

### <a name="use-global-search-for-power-bi-preview"></a>Utiliser la recherche générale pour Power BI (préversion)

Les utilisateurs de l’organisation peuvent utiliser les fonctionnalités de recherche externe qui reposent sur le service Recherche Azure.

## <a name="r-visuals-settings"></a>Paramètres des visuels R

### <a name="interact-with-and-share-r-visuals"></a>Utiliser et partager des éléments visuels R

Les utilisateurs de l’organisation peuvent manipuler et partager des visuels créés avec des scripts R. [En savoir plus](../visuals/service-r-visuals.md)

> [!NOTE]
> Ce paramètre s’applique à toute l’organisation et ne peut pas être limité à des groupes en particulier.

## <a name="audit-and-usage-settings"></a>Paramètres d'audit et d'utilisation

### <a name="create-audit-logs-for-internal-activity-auditing-and-compliance"></a>Créer des journaux d'audit pour l'audit des activités internes et la vérification de la conformité

Les utilisateurs de l’organisation peuvent utiliser l’audit pour surveiller les actions effectuées dans Power BI par d’autres utilisateurs de l’organisation. [En savoir plus](service-admin-auditing.md)

Ce paramètre doit être activé pour pouvoir enregistrer les entrées du journal d’audit. Une fois que vous avez activé l’audit, le délai avant de pouvoir voir les données d’audit peut aller jusqu’à 48 heures. Si vous ne voyez immédiatement les données, consultez les journaux d’audit plus tard. Le délai est sensiblement le même entre le moment où vous obtenez l’autorisation de voir les journaux d’audit et le moment où vous pouvez réellement y accéder.

> [!NOTE]
> Ce paramètre s’applique à toute l’organisation et ne peut pas être limité à des groupes en particulier.

### <a name="usage-metrics-for-content-creators"></a>Métriques d'utilisation pour les créateurs de contenu

Les utilisateurs de l’organisation peuvent voir les métriques d’utilisation des tableaux de bord et des rapports qu’ils créent. [En savoir plus](../collaborate-share/service-usage-metrics.md)

### <a name="per-user-data-in-usage-metrics-for-content-creators"></a>Données par utilisateur dans les métriques d'utilisation pour les créateurs de contenu

Les métriques d'utilisation pour créateurs de contenu exposent les noms d'affichage et les adresses e-mail des utilisateurs qui accèdent à du contenu. [En savoir plus](../collaborate-share/service-usage-metrics.md)

Par défaut, les données par utilisateur sont activées pour les métriques d’utilisation et les informations des comptes de créateur de contenu sont incluses dans le rapport des métriques. Si vous ne souhaitez pas recueillir ces informations pour tous les utilisateurs, vous pouvez désactiver la fonctionnalité pour des groupes de sécurité spécifiés ou pour l’ensemble de l’organisation. Les informations de compte des utilisateurs exclus figurent alors dans le rapport sous l’intitulé *Sans nom*.

## <a name="dashboard-settings"></a>Paramètres du tableau de bord

### <a name="data-classification-for-dashboards"></a>Classification des données des tableaux de bord

Les utilisateurs de l’organisation peuvent étiqueter les tableaux de bord avec des classifications indiquant les niveaux de sécurité des tableaux de bord. [En savoir plus](../create-reports/service-data-classification.md)

> [!NOTE]
> Ce paramètre s’applique à toute l’organisation et ne peut pas être limité à des groupes en particulier.

### <a name="web-content-on-dashboard-tiles"></a>Contenu web sur les vignettes de tableau de bord

Les utilisateurs de l’organisation peuvent ajouter et afficher des vignettes de contenu web sur les tableaux de bord Power BI. [En savoir plus](../create-reports/service-dashboard-add-widget.md)

> [!NOTE]
> Cela peut exposer votre organisation à du contenu web malveillant, ce qui pose un risque pour la sécurité.

## <a name="developer-settings"></a>Paramètres de développement

### <a name="embed-content-in-apps"></a>Incorporer du contenu dans les applications

Les utilisateurs de l’organisation peuvent incorporer des tableaux de bord et des rapports Power BI dans des applications Saas (Software as a Service). La désactivation de ce paramètre empêche les utilisateurs d’utiliser les API REST pour incorporer du contenu Power BI dans leur application. [En savoir plus](../developer/embedded/embedding.md)

### <a name="allow-service-principals-to-use-power-bi-apis"></a>Autoriser les principaux de service à utiliser les API Power BI

Les applications web inscrites dans Azure Active Directory (Azure AD) utiliseront un principal de service affecté pour accéder aux API Power BI sans utilisateur connecté. Pour pouvoir autoriser une application à utiliser l'authentification du principal de service, ce dernier doit faire partie d'un groupe de sécurité autorisé. [En savoir plus](../developer/embedded/embed-service-principal.md)

> [!NOTE]
> Les principaux de service héritent des autorisations de leur groupe de sécurité pour tous les paramètres du locataire Power BI. Pour limiter les autorisations, créez un groupe de sécurité dédié pour les principaux de service et ajoutez-le à la liste « À l’exception des groupes de sécurité spécifiques » pour les paramètres Power BI pertinents activés.

## <a name="dataflow-settings"></a>Paramètres de dataflow

### <a name="create-and-use-dataflows"></a>Créer et utiliser des dataflows

Les utilisateurs de l'organisation peuvent créer et utiliser des dataflows. Pour une vue d’ensemble des dataflows, consultez [Préparation des données en libre-service dans Power BI](../transform-model/dataflows/dataflows-introduction-self-service.md). Pour activer les dataflows dans une capacité Premium, consultez [Configurer des charges de travail](service-admin-premium-workloads.md).

> [!NOTE]
> Ce paramètre s’applique à toute l’organisation et ne peut pas être limité à des groupes en particulier.

## <a name="template-apps-settings"></a>Paramètres des applications modèles

Trois paramètres contrôlent la capacité des applications modèles à publier ou installer des applications modèles.

![Paramètres des applications modèles du portail d’administration Power BI](media/service-admin-portal/power-bi-admin-portal-template-apps.png)

### <a name="publish-template-apps"></a>Publier des applications modèles

Les utilisateurs de l'organisation peuvent créer des espaces de travail d’applications modèles. Choisissez quels utilisateurs peuvent publier des applications modèles ou les distribuer à des clients extérieurs à votre organisation via [AppSource](https://appsource.microsoft.com) ou d’autres méthodes de distribution.

![Paramètre Publier des applications modèles activé pour l’ensemble de l’organisation](media/service-admin-portal/power-bi-admin-portal-template-app-settings.png)

### <a name="install-template-apps-listed-on-appsource"></a>Installer des applications modèles répertoriées sur AppSource

Les utilisateurs de l’organisation peuvent télécharger et installer des applications modèles **uniquement** depuis [AppSource](https://appsource.microsoft.com). Choisissez quels utilisateurs spécifiques ou groupes de sécurité peuvent installer des applications modèles depuis AppSource.

![Paramètre Installer des applications modèles](media/service-admin-portal/power-bi-admin-portal-template-app-settings-installer-appsource.png)

### <a name="install-template-apps-not-listed-on-appsource"></a>Installer des applications modèles non répertoriées sur AppSource

Choisissez quels utilisateurs dans l’organisation peuvent télécharger et installer des applications modèles **non répertoriées sur [AppSource](https://appsource.microsoft.com)** .

![Paramètre Installer des applications modèles qui ne figurent pas dans AppSource](media/service-admin-portal/power-bi-admin-portal-template-app-settings-installer-nonappsource.png)

## <a name="capacity-settings"></a>Paramètres de capacité

### <a name="power-bi-premium"></a>Power BI Premium

L’onglet **Power BI Premium** vous permet de gérer les capacités Power BI Premium (EM ou SKU P) achetées pour votre organisation. Tous les utilisateurs dans votre organisation peuvent voir l’onglet **Power BI Premium**, mais ne peuvent en voir le contenu que s’ils disposent d’autorisations *d’administrateur de capacité* ou d’autorisations d’affectation. Si un utilisateur ne possède aucune autorisation, le message suivant apparaît.

![Aucun accès aux paramètres Premium](media/service-admin-portal/premium-settings-no-access.png)

### <a name="power-bi-embedded"></a>Power BI Embedded

L’onglet **Power BI Embedded** vous permet d’afficher les capacités de Power BI Embedded (référence SKU A) que vous avez achetées pour votre client. Dans la mesure où vous ne pouvez acheter des références SKU A qu’à partir d’Azure, vous [gérez les capacités incorporées dans Azure](../developer/embedded/azure-pbie-create-capacity.md) depuis **le portail Azure**.

Pour plus d’informations sur la gestion des paramètres de Power BI Embedded (référence SKU A), consultez [Qu’est-ce que Power BI Embedded](../developer/embedded/azure-pbie-what-is-power-bi-embedded.md).

## <a name="embed-codes"></a>Codes incorporés

En tant qu’administrateur, vous pouvez afficher les codes incorporés générés pour votre tenant pour partager publiquement les rapports. Vous pouvez également révoquer ou supprimer des codes. [En savoir plus](../collaborate-share/service-publish-to-web.md)

![Codes incorporés au sein du portail d’administration Power BI](media/service-admin-portal/embed-codes.png)

## <a name="organizational-visuals"></a>Visuels organisationnels

Tous les paramètres d’administration d’éléments visuels Power BI, y compris les paramètres de l’abonné des éléments visuels Power BI, sont décrits dans [Gérer les paramètres d’administration des éléments visuels Power BI](organizational-visuals.md).

## <a name="azure-connections-preview"></a>Connexions Azure (préversion)

### <a name="tenant-level-storage-preview"></a>Stockage au niveau de l’abonné (préversion)

Par défaut, les données utilisées avec Power BI sont stockées dans le stockage interne offert par Power BI. Avec l’intégration entre les flux de données et Azure Data Lake Storage Gen2 (ADLS Gen2), vous pouvez stocker vos flux de données dans le compte Azure Data Lake Storage Gen2 de votre organisation. Pour plus d’informations, consultez [Flux de données et intégration à Azure Data Lake (préversion)](../transform-model/dataflows/dataflows-azure-data-lake-storage-integration.md).

### <a name="workspace-level-storage-permissions-preview"></a>Autorisations de stockage au niveau de l’espace de travail (préversion)

Par défaut, les administrateurs des espaces de travail ne peuvent pas se connecter à leur propre compte de stockage. Cette fonctionnalité d’évaluation vous permet d’activer un paramètre qui autorise les administrateurs de l’espace de travail à se connecter à leur propre compte de stockage.

## <a name="workspaces"></a>Workspaces

En tant qu’administrateur, vous pouvez afficher les espaces de travail qui existent dans votre abonné sur l’onglet **Espaces de travail**. Dans cet onglet, vous pouvez effectuer les actions suivantes :

- actualiser la liste des espaces de travail et leurs détails,
- exporter les données relatives aux espaces de travail dans un fichier .csv, 
- consulter les détails relatifs à un espace de travail, y compris son ID, ses utilisateurs et ses rôles, ainsi que ses tableaux de bord, rapports et jeux de données,
- modifier la liste des personnes qui y ont accès. Cela signifie que vous pouvez supprimer l’espace de travail. Vous pouvez vous ajouter à un espace de travail en tant qu’administrateur, puis ouvrir l’espace de travail et le supprimer.
- Modifiez les champs Nom et Description.

![Liste des espaces de travail](media/service-admin-portal/workspaces-list.png)

Les administrateurs peuvent également contrôler la capacité des utilisateurs à créer de nouveaux espaces de travail, des espaces de travail d’expérience et des espaces de travail classiques. Pour plus d’informations, consultez [Paramètres des espaces de travail](#workspace-settings), dans cet article. 

Les colonnes de la table de l’onglet **Espaces de travail** correspondent aux propriétés retournées par l’[API REST administrateur Power BI](/rest/api/power-bi/admin) pour les espaces de travail. Les espaces de travail personnels sont de type **PersonalGroup**, les espaces de travail classiques sont de type **Group**, et les nouveaux espaces de travail modernes sont de type **Workspace**. Pour plus d’informations, consultez [Organiser le travail dans les nouveaux espaces de travail](../collaborate-share/service-new-workspaces.md).

Sous l’onglet **Espaces de travail**, vous voyez l’*état* pour chaque espace de travail. Le tableau suivant fournit plus de détails sur la signification de ces états.

|État  |Description  |
|---------|---------|
| **Actif** | Un espace de travail normal. Il n’indique rien sur l’utilisation ou ce qui se trouve à l’intérieur, mais seulement le fait que l’espace de travail lui-même est « normal ». |
| **Orphelin** | Un espace de travail sans administrateur. |
| **Supprimé** | Un espace de travail supprimé. Pendant un délai pouvant atteindre 90 jours, nous conservons suffisamment de métadonnées pour restaurer l’espace de travail si nécessaire. |
| **Suppression** | Un espace de travail en cours de suppression, mais qui n’est pas encore supprimé. Les utilisateurs peuvent supprimer leurs propres espaces de travail, en plaçant les éléments en Suppression, puis en Supprimé. |

Les administrateurs peuvent également gérer et récupérer des espaces de travail à l’aide du portail d’administration ou des applets de commande PowerShell. 

![Liste des espaces de travail](media/service-admin-portal/workspaces-list.png)

## <a name="custom-branding"></a>Marque personnalisée

En tant qu’administrateur, vous pouvez personnaliser l’apparence de Power BI pour l’ensemble de votre organisation. Actuellement, il existe trois options principales :

![Options de marque personnalisée](media/service-admin-portal/power-bi-custom-branding.png)

* **Télécharger le logo** : Pour de meilleurs résultats, téléchargez un logo enregistré au format .png de 10 ko ou moins et d’au moins 200 x 30 pixels.

* **Télécharger l’image de couverture** : Pour de meilleurs résultats, téléchargez une image de couverture enregistrée au format .jpg ou .png de 1 Mo ou moins, et d’au moins 1920 x 160 pixels.

* **Sélectionner la couleur du thème** : Vous pouvez sélectionner votre thème en fonction d’une valeur hexadécimale #, RVB ou de la palette fournie.


Pour plus d’informations, consultez [Marque personnalisée pour votre organisation](https://aka.ms/orgBranding).

## <a name="protection-metrics"></a>Mesures de protection

Une fois que vous avez activé la protection des informations pour Power BI, les mesures de protection des données sont affichées dans le portail Administrateur. Le rapport montre comment les étiquettes de confidentialité contribuent à protéger votre contenu.

## <a name="manage-featured-content"></a>Gérer le contenu proposé

En tant qu’administrateur Power BI, vous pouvez gérer tous les rapports, tableaux de bord et applications qui ont été promus dans la section Proposé de la page d’accueil Power BI à l’échelle de votre organisation.

- Dans le portail d’administration, sélectionnez **Contenu proposé**.

Vous y trouverez ici une vue d’ensemble des personnes qui ont proposé le contenu, du moment où il a été proposé et de toutes les métadonnées qui s’y rapportent. Si quelque chose semble suspect ou si vous souhaitez nettoyer la section À la une, vous pouvez supprimer le contenu promu en fonction des besoins.

Consultez [Contenu proposé](#featured-content) dans cet article pour obtenir des informations sur l’activation du contenu proposé.

## <a name="next-steps"></a>Étapes suivantes

[Administration de Power BI dans votre organisation](service-admin-administering-power-bi-in-your-organization.md)  
[Présentation du rôle d’administrateur Power BI](service-admin-role.md)  
[Audit de Power BI dans votre organisation](service-admin-auditing.md)  

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
