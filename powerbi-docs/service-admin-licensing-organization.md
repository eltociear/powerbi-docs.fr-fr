---
title: Gestion des licences Power BI dans votre organisation
description: Vue d’ensemble des différents types de licences disponibles dans Power BI ainsi que des modalités d’achat et de gestion des licences proposées aux administrateurs pour leur organisation.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/08/2020
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: a41e9453158c38a208fe7f4ac937b4e86a515f4b
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "81436319"
---
# <a name="power-bi-licensing-in-your-organization"></a>Gestion des licences Power BI dans votre organisation

Les fonctionnalités accessibles aux utilisateurs dans le service Power BI dépendent du type de licence par utilisateur dont ils disposent et varient selon que le contenu sur lequel ils travaillent se trouve ou non dans un espace de travail de capacité Power BI Premium. Tous les utilisateurs du service Power BI doivent disposer d’une licence.

Il existe deux moyens pour les utilisateurs d’obtenir une licence. Avec les fonctionnalités d’inscription en libre-service et leur compte professionnel ou scolaire, ils peuvent bénéficier de leur propre licence gratuite ou Pro. Sinon, les administrateurs peuvent acquérir un abonnement Power BI et affecter des licences aux utilisateurs.

Cet article porte sur l’achat de services et de licences par utilisateur du point de vue de l’administrateur. Pour savoir comment obtenir sa propre licence en tant qu’utilisateur, consultez [Inscription à Power BI à titre individuel](service-self-service-signup-for-power-bi.md).

## <a name="who-can-purchase-and-assign-licenses"></a>Achat et affectation de licences Pro

Vous devez disposer d’un rôle d’administrateur pour acheter ou affecter des licences au sein de votre organisation. Ces rôles sont attribués à l’aide du Centre d’administration Azure Active Directory ou du Centre d’administration Microsoft 365. Le tableau suivant indique le rôle requis pour effectuer des tâches liées à l’achat et à la gestion des licences. Pour plus d’informations sur les rôles d’administrateur dans Azure Active Directory, consultez [Affichage et attribution des rôles d’administrateur dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-manage-roles-portal). Pour plus d’informations sur les rôles d’administrateur dans Microsoft 365, et notamment les meilleures pratiques, consultez [À propos des rôles d’administrateur](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles?view=o365-worldwide).

| Qui peut acheter des services et des licences ? | Qui peut gérer les licences utilisateur ? |
| --------------- | --------------- |
| Administrateur de facturation | Administrateur de licence |
| Administrateur général | Administrateur d’utilisateurs |
|  | Administrateur général |

Ces rôles gèrent l’organisation. Pour plus d’informations sur les rôles d’Administrateur de service Power BI, consultez [Présentation des rôles d’Administrateur de service Power BI](service-admin-role.md).

## <a name="get-power-bi-for-your-organization"></a>Obtenir Power BI pour votre organisation

Un administrateur général ou un administrateur de facturation peut s’inscrire au service Power BI et acheter des licences pour les utilisateurs de son organisation. Si vous ne souhaitez pas passer à l’achat tout de suite, sélectionnez l’essai de Power BI Pro. Vous bénéficierez de 25 licences à utiliser pendant un mois. Pour des instructions pas à pas sur l’inscription, consultez [Souscription d’un abonnement Power BI pour une organisation](admin/service-admin-org-subscription.md).

## <a name="about-self-service-sign-up"></a>À propos de l’inscription en libre-service

Un utilisateur individuel peuvent obtenir sa propre licence Power BI en s’inscrivant avec son compte professionnel ou scolaire. Dans le cadre d’une licence gratuite, il peut explorer Power BI pour la visualisation et l’analyse des données personnelles avec Mon espace de travail, mais non entamer une collaboration avec d’autres utilisateurs. Une licence Power BI Pro est nécessaire pour partager du contenu. Les utilisateurs peuvent passer au type de licence Pro par le biais d’une mise à niveau ou s’inscrire directement à Pro, si l’organisation utilise le cloud commercial. Ni l’achat direct de Pro ni la mise à niveau vers Pro ne sont disponibles pour les établissements d’enseignement et les organisations déployées sur des instances gouvernementales ou de cloud souverain.

Si vous ne souhaitez pas que l’inscription en libre-service soit accessible aux utilisateurs de votre organisation, consultez [Activation et désactivation de l’inscription en libre-service](admin/service-admin-disable-self-service.md) pour savoir comment la désactiver.

Si vous souhaitez voir quels utilisateurs de votre organisation disposent déjà d’une licence, consultez [Affichage et gestion des licences utilisateur](admin/service-admin-manage-licenses.md) pour savoir comment procéder.

## <a name="license-types-and-capabilities"></a>Types de licences et fonctionnalités

Il existe deux types de licences Power BI par utilisateur : gratuite et Pro. Le type de licence nécessaire pour un utilisateur est déterminé par l’endroit où le contenu est stocké et par les interactions souhaitées avec ce contenu. L’emplacement de stockage dépend du [type d’abonnement](#subscription-types) de l’organisation.

Il existe un type d’abonnement, [Power BI Premium](service-admin-premium-purchase.md), qui permet aux utilisateurs disposant d’une licence gratuite d’agir sur le contenu des espaces de travail de capacité Premium. En dehors de la capacité Premium, un utilisateur disposant d’une licence gratuite ne peut utiliser la service Power BI que pour se connecter aux données et créer des rapports et des tableaux de bord dans un espace de travail personnel. Il ne peut pas partager du contenu avec d’autres personnes ni en publier sur des espaces de travail d’application.

Un abonnement Power BI standard utilise la capacité partagée. Lorsque le contenu est stocké dans une capacité partagée, les utilisateurs disposant d’une licence Power BI Pro ne peuvent collaborer qu’avec d’autres utilisateurs Power BI Pro. Ils ont la possibilité de consommer du contenu publié par d’autres personnes, de publier du contenu sur des espaces de travail d’application, de partager des tableaux de bord et de s’abonner à des tableaux de bord et à des rapports.  Lorsque les espaces de travail sont en capacité Premium, les utilisateurs Pro peuvent distribuer du contenu à des utilisateurs dépourvus de licence Power BI Pro.

Le tableau ci-dessous récapitule les fonctionnalités de base de chaque type de licence. Pour une décomposition détaillée de la disponibilité des fonctionnalités par type de licence, consultez [Fonctionnalités par type de licence](service-features-license-type.md).

| Type de licence | Fonctionnalités lorsque l’espace de travail est en capacité partagée | Fonctionnalités supplémentaires lorsque l’espace de travail est en capacité Premium |
| --------- | ----------- | ----------- |
| Power BI (gratuit) | Accès au contenu de Mon espace de travail | Consommation du contenu partagé avec l’utilisateur |
| Power BI Pro | Publication de contenu sur des espaces de travail d’application, partage de tableaux de bord, abonnement à des tableaux de bord et à des rapports, partage avec des utilisateurs disposant d’une licence Pro | Distribution de contenu aux utilisateurs disposant de licences gratuites |

## <a name="subscription-types"></a>Types d’abonnements

Tous les abonnements Microsoft de type licence commerciale basée sur l’utilisateur s’appuient sur des identités Azure Active Directory. Par conséquent, vous devez vous connecter avec une identité prise en charge par Azure Active Directory pour les licences commerciales. Il est possible d’ajouter un abonnement Power BI à n’importe quel abonnement Microsoft ayant recours à Azure Active Directory pour les services d’identité. Certains abonnements, comme Office 365 E5, incluent une licence Power BI Pro, de sorte qu’il n’est pas nécessaire de s’inscrire séparément à Power BI.

Il existe deux types d’abonnements Power BI pour les organisations : décisionnel libre-service avec Power BI Pro et analytiques avancées avec Power BI Premium.

Avec un abonnement Power BI Pro standard en libre-service, les administrateurs affectent des licences par utilisateur. Ces licences font l’objet d’un forfait mensuel par utilisateur, qui comprend la collaboration, la publication, le partage et l’analyse ad hoc. Le contenu est enregistré dans une capacité de stockage partagée entièrement gérée par Microsoft.

Un abonnement Power BI Premium alloue une capacité dédiée à une organisation. Adapté au décisionnel, à l’analytique Big Data et au reporting cloud et local des grandes entreprises, il fournit des contrôles avancés d’administration et de déploiement. Les ressources de calcul et de stockage dédiées sont gérées par les administrateurs de capacité de l’organisation. Cet environnement dédié fait l’objet d’un forfait mensuel. Entre autres avantages Premium, le contenu stocké dans une capacité Premium est accessible aux utilisateurs dépourvus de licences Power BI Pro et peut leur être distribué. La condition pour pouvoir utiliser Premium est qu’au moins un utilisateur dispose d’une licence Power BI Pro ; par ailleurs, les créateurs de contenu et les développeurs ont toujours besoin d’une licence Power BI Pro.

Les deux types d’abonnements ne s’excluent pas mutuellement. Il est possible de disposer à la fois de Power BI Premium et de Power BI Pro. Dans cette configuration, le contenu stocké dans la capacité Premium peut être partagé avec tous les utilisateurs ; la capacité partagée est également disponible. Pour plus d’informations sur les limites des capacités, consultez [Gestion du stockage de données dans les espaces de travail Power BI](service-admin-manage-your-data-storage-in-power-bi.md).

Pour comparer les fonctionnalités et les tarifs des produits, consultez [Tarifs de Power BI](https://powerbi.microsoft.com/pricing).

## <a name="guest-user-access"></a>Accès utilisateur invité

Vous pouvez distribuer du contenu à des utilisateurs extérieurs à votre organisation. Il faut pour cela les inviter à l’afficher en tant qu’invités. Ce partage avec des utilisateurs invités externes est permis par Azure Active Directory Business-to-Business (Azure AD B2B). En voici les prérequis :

- Le partage de contenu avec des utilisateurs externes doit être activé.

- L’utilisateur invité doit disposer d’une licence appropriée pour visualiser le contenu partagé.

Pour plus d’informations sur l’accès utilisateur invité, consultez [Distribution de contenu Power BI à des utilisateurs invités externes avec Azure AD B2B](service-admin-azure-ad-b2b.md).

## <a name="purchase-power-bi-pro-licenses"></a>Acheter des licences Power BI Pro

Les administrateurs achètent des licences Power BI Pro par le biais de Microsoft 365 ou d’un partenaire Microsoft. Ils les affectent ensuite aux différents utilisateurs. Pour plus d’informations, consultez [Acheter et attribuer des licences Power BI Pro](service-admin-purchasing-power-bi-pro.md).

### <a name="power-bi-pro-license-expiration"></a>Expiration de la licence Power BI Pro

Il y a une période de grâce après l’expiration d’une licence Power BI Pro. Pour les licences qui font partie d’un achat de licences en volume, la période de grâce est de 90 jours. Si vous avez acheté directement la licence, la période de grâce dure 30 jours.

L’abonnement Power BI Pro dispose du même cycle de vie qu’Office 365. Pour plus d’informations, consultez [Qu’arrive-t-il à mes données et à mon accès à la fin de mon abonnement Office 365 pour les entreprises ?](https://support.office.com/article/What-happens-to-my-data-and-access-when-my-Office-365-for-business-subscription-ends-4436582f-211a-45ec-b72e-33647f97d8a3).


## <a name="next-steps"></a>Étapes suivantes

- [Acheter et attribuer des licences Power BI Pro](service-admin-purchasing-power-bi-pro.md)
- [Documentation sur les abonnements et la facturation Microsoft 365 Business](https://docs.microsoft.com/microsoft-365/commerce/?view=o365-worldwide)
- [Trouver les utilisateurs Power BI qui se sont connectés](service-admin-access-usage.md)
- D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
