---
title: Acheter Power BI Premium
description: Découvrez comment acheter Power BI Premium et permettre à l’ensemble de votre organisation d’accéder au contenu.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-premium
ms.topic: how-to
ms.date: 11/11/2020
LocalizationGroup: Premium
ms.openlocfilehash: f74d667cd95f1fd34d97c3942ac6ab44d083d4c3
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96408386"
---
# <a name="how-to-purchase-power-bi-premium"></a>Acheter Power BI Premium

Cet article explique comment acheter de la capacité Power BI Premium pour votre organisation. L’article traite du scénario suivant :

- L’utilisation de références SKU P pour les scénarios de production classiques. Les références SKU P nécessitent un engagement mensuel ou annuel et donnent lieu à une facturation mensuelle.

Pour plus d’informations sur Power BI Premium, consultez [Qu’est-ce que Power BI Premium ?](service-premium-what-is.md) Pour connaître le tarif actuel et obtenir des informations sur la planification, consultez la [page des tarifs de Power BI](https://powerbi.microsoft.com/pricing/) et la [Calculatrice Power BI Premium](https://powerbi.microsoft.com/calculator/). Les créateurs de contenu ont toujours besoin d’une [licence Power BI Pro](service-admin-purchasing-power-bi-pro.md), même si votre organisation utilise Power BI Premium. Veillez à acheter au moins une licence Power BI Pro pour votre organisation. Avec des références SKU A, _tous les utilisateurs_ qui consomment du contenu ont également besoin d’une licence Pro.

> [!NOTE]
> Si un abonnement Premium expire, vous avez un accès total à votre capacité pendant 30 jours. Après cela, votre contenu reviendra à une capacité partagée. Les modèles de plus de 1 Go ne sont pas pris en charge dans une capacité partagée.

> [!NOTE]
> Une nouvelle version de Power BI Premium a récemment été publiée. Celle-ci, appelée **Premium Gen2**, est actuellement en préversion. Premium Gen2 vise à simplifier la gestion des capacités Premium et à réduire la charge de gestion. Pour plus d’informations, consultez [Power BI Premium Generation 2 (préversion)](service-premium-what-is.md#power-bi-premium-generation-2-preview).

## <a name="purchase-p-skus-for-typical-production-scenarios"></a>Acheter des références SKU P pour les scénarios de production classiques

Vous pouvez créer un locataire avec une référence SKU Power BI Premium P1 configurée, ou acheter une capacité Power BI Premium pour une organisation existante. Dans les deux cas, vous pouvez ensuite ajouter une capacité supplémentaire en cas de besoin.

### <a name="create-a-new-tenant-with-power-bi-premium-p1"></a>Créer un locataire avec Power BI Premium P1

Si vous ne disposez pas déjà d’un locataire et que vous voulez en créer un, vous pouvez acheter Power BI Premium en même temps. Le lien suivant vous guide lors du processus de création d’un locataire et vous permet d’acheter Power BI Premium : [Offre Power BI Premium P1](https://signup.microsoft.com/Signup?OfferId=b3ec5615-cc11-48de-967d-8d79f7cb0af1). Quand vous créez votre locataire, le rôle Administrateur général Microsoft 365 vous est automatiquement attribué pour ce locataire.

Après avoir acheté une capacité, découvrez comment [gérer les capacités](service-admin-premium-manage.md#manage-capacity) et comment [affecter des espaces de travail](service-admin-premium-manage.md#assign-a-workspace-to-a-capacity) à une capacité.

### <a name="purchase-a-power-bi-premium-capacity-for-an-existing-organization"></a>Acheter une capacité Power BI Premium pour votre organisation

Si vous avez une organisation existante (locataire), vous devez avoir le rôle Administrateur général ou Administrateur de facturation Microsoft 365 pour acheter des abonnements et des licences. Pour plus d’informations, consultez [À propos des rôles d’administrateur Microsoft 365](https://support.office.com/article/About-Office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d).

Pour acheter la capacité Premium, effectuez les étapes suivantes.

1. Dans le service Power BI, choisissez le sélecteur d’application Microsoft 365, puis sélectionnez **Administrateur**.

    ![Sélecteur d’application Microsoft 365](media/service-admin-premium-purchase/o365-app-picker.png)

    Vous pouvez également accéder au Centre d’administration Microsoft 365.

1. Sélectionnez **Facturation** > **Acheter des services**.

1. Sous **Autres offres**, recherchez les offres Power BI Premium. Celles-ci s’affichent sous les noms P1 à P3, EM3 et P1 (de mois en mois).

1. Placez le curseur sur les points de suspension  **(...)** , puis sélectionnez **Acheter maintenant**.

    ![Acheter maintenant](media/service-admin-premium-purchase/premium-purchase.png)

1. Suivez les étapes pour terminer l’achat.

Une fois l’achat terminé, la page **Acheter des services** indique que l’élément est acheté et actif.

![Achat de Power BI Premium](media/service-admin-premium-purchase/premium-purchased.png)

Après avoir acheté une capacité, découvrez comment [gérer les capacités](service-admin-premium-manage.md#manage-capacity) et comment [affecter des espaces de travail](service-admin-premium-manage.md#assign-a-workspace-to-a-capacity) à une capacité.

### <a name="purchase-additional-capacities"></a>Acheter des capacités supplémentaires

Maintenant que vous avez une capacité, vous pouvez en ajouter plus à mesure que vos besoins augmentent. Vous pouvez utiliser une combinaison de références SKU de capacité Premium (P1 à P3) au sein de votre organisation. Les différentes références fournissent différentes capacités de ressources.

1. Dans le Centre d’administration Microsoft 365, sélectionnez **Facturation** > **Acheter des services**.

1. Recherchez l’élément Power BI Premium que vous souhaitez acheter en plus grand nombre sous **Autres offres**.

1. Positionnez le curseur sur **Plus d’options** (...), puis sélectionnez **Modifier la quantité de licences**.

    ![Modifier le nombre de licences](media/service-admin-premium-purchase/premium-purchase-more.png)

1. Modifiez le nombre d’instances dont vous souhaitez disposer pour cet élément. Lorsque vous avez terminé, sélectionnez **Soumettre** une fois.

   > [!IMPORTANT]
   > La sélection de **Soumettre** débite la carte bancaire enregistrée.

La page **Acheter des services** indique ensuite le nombre d’instances dont vous disposez. Dans le portail d’administration Power BI, sous **Paramètres de capacité**, les v-cores disponibles reflètent la nouvelle capacité achetée.

![V-cores pour la capacité Power BI Premium](media/service-admin-premium-purchase/premium-capacities.png)

### <a name="cancel-your-subscription"></a>Annuler votre abonnement

Vous pouvez annuler votre abonnement à partir du Centre d’administration Microsoft 365. Pour annuler votre abonnement Premium, procédez comme suit.

1. Accédez au Centre d’administration Microsoft 365.

1. Sélectionnez **Facturation** > **Abonnements**.

1. Dans la liste, sélectionnez votre abonnement Power BI Premium.

1. Sélectionnez **Autres actions** > **Annuler l’abonnement**.

1. La page **Annuler l’abonnement** indique si vous devez régler des [frais d’arrêt anticipé](https://support.office.com/article/early-termination-fees-6487d4de-401a-466f-8bc3-c0beb5cc40d3). Cette page vous permet aussi de savoir quand les données sont supprimées de l’abonnement.

1. Lisez les informations et si vous souhaitez continuer, sélectionnez **Annuler l’abonnement**.

#### <a name="when-canceling-or-your-license-expires"></a>En cas d’annulation ou lorsque vos licence arrive à expiration

Lorsque vous annulez votre abonnement Premium ou que votre licence de capacité arrive à expiration, vous pouvez continuer à accéder à vos capacités Premium pendant une période de 30 jours à partir de la date d’annulation ou d’expiration de la licence. Après 30 jours, vous ne pourrez plus accéder à vos capacités Premium ou aux espaces de travail qui s’y trouvent.

## <a name="purchase-a-skus-for-testing-and-other-scenarios"></a>Acheter des références SKU A pour les tests et d’autres scénarios

Vous pouvez également acheter des références SKU A pour les tests et d’autres scénarios, ce qui vous permet de bénéficier d’une capacité Premium sur une base horaire. Pour obtenir plus d’informations et la procédure à suivre, consultez [Acheter Power BI Premium pour les tests](service-admin-premium-testing.md).

## <a name="next-steps"></a>Étapes suivantes

[Configurer et gérer les capacités dans Power BI Premium](service-admin-premium-manage.md)\
[Page de tarification de Power BI](https://powerbi.microsoft.com/pricing/)\
[Calculatrice Power BI Premium](https://powerbi.microsoft.com/calculator/)\
[FAQ Power BI Premium](service-premium-faq.md)\
[Planification d’un livre blanc sur le déploiement de Power BI en entreprise](https://aka.ms/pbienterprisedeploy)

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)

Introduite par Power BI, l’offre en préversion Power BI Premium Gen2 apporte les améliorations suivantes à l’expérience Power BI Premium :
* Performances
* Licences par utilisateur
* Mise à l’échelle supérieure
* Métriques améliorées
* Mise à l’échelle automatique
* Charge de gestion réduite

Pour plus d’informations sur Power BI Premium Gen2, consultez [Power BI Premium Generation 2 (préversion)](service-premium-what-is.md#power-bi-premium-generation-2-preview).