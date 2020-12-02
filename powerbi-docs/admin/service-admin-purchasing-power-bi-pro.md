---
title: Acheter et attribuer des licences Power BI Pro
description: Découvrez comment acheter des licences Power BI Pro et les attribuer aux utilisateurs pour leur permettre d’accéder à du contenu et de collaborer avec d’autres personnes dans le service Power BI.
author: mihart
ms.author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 04/08/2020
ms.custom: licensing support
LocalizationGroup: Administration
ms.openlocfilehash: 5845e56bdcb2257d67d541e35d26c9285a5e9319
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96408133"
---
# <a name="purchase-and-assign-power-bi-pro-user-licenses"></a>Acheter et attribuer des licences utilisateur Power BI Pro

>[!IMPORTANT]
>Cet article est destiné aux administrateurs. Êtes-vous prêt à passer à une licence Power BI Pro ? Accédez directement à la [Prise en main de Power BI Pro](https://go.microsoft.com/fwlink/?LinkId=2106428&clcid=0x409&cmpid=pbidocs-purchasing-power-bi-pro) pour configurer votre compte.

Power BI Pro est une licence utilisateur individuelle qui permet aux utilisateurs de lire et d’interagir avec les rapports et les tableaux de bord publiés par d’autres utilisateurs sur le service Power BI. Les utilisateurs disposant de ce type de licence peuvent partager du contenu et collaborer avec d’autres utilisateurs Power BI Pro. Seuls les utilisateurs Power BI Pro peuvent publier ou partager du contenu avec d’autres utilisateurs ou consommer du contenu créé par d’autres utilisateurs, sauf si ce contenu est hébergé dans une capacité Power BI Premium. Pour plus d’informations sur les types de licences et d’abonnements disponibles, consultez [Gestion des licences Power BI dans l’organisation](service-admin-licensing-organization.md).

## <a name="purchase-power-bi-pro-user-licenses"></a>Acheter des licences utilisateur Power BI Pro

Cet article explique comment acheter des licences utilisateur Power BI Pro dans le Centre d’administration Microsoft 365. Une fois que vous avez acheté des licences, vous pouvez les affecter aux utilisateurs dans le Centre d’administration Microsoft 365 ou sur le Portail Azure.

> [!NOTE]
> À compter du 14 janvier 2020, les fonctionnalités d’achat, d’abonnement et de gestion des licences libre-service pour les produits Power Platform (Power BI, Power Apps et Power Automate) sont disponibles pour les clients cloud commerciaux. Pour plus d’informations, consultez [FAQ sur l’achat en libre-service](/microsoft-365/commerce/subscriptions/self-service-purchase-faq). Pour activer ou désactiver les fonctionnalités d’achat en libre-service, consultez [Activation et désactivation de l’inscription et de l’achat en libre-service](./service-admin-disable-self-service.md).

### <a name="prerequisites"></a>Prérequis

Pour pouvoir acheter et affecter des licences dans le Centre d’administration Microsoft 365, vous devez être membre du rôle [Administrateur général ou Administrateur de facturation](https://support.office.com/article/about-office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d) dans Microsoft 365.

Pour attribuer des licences dans le portail Azure, vous devez être propriétaire de l’abonnement Azure utilisé par Power BI pour les recherches Azure Active Directory.

### <a name="purchase-licenses-in-microsoft-365"></a>Acheter des licences dans Microsoft 365

> [!NOTE]
> Si vous achetez habituellement des licences via un contrat de licence en volume, comme un Accord Entreprise, et que vous souhaitez recevoir une facture au lieu d’acheter avec une carte de crédit ou un compte bancaire, vous devez soumettre la commande différemment. Collaborez avec votre revendeur Microsoft ou consultez le centre de gestion des licences en volume pour ajouter ou supprimer des licences. Pour plus d’informations, consultez [Gérer les licences d’abonnement](/microsoft-365/commerce/licenses/buy-licenses?view=o365-worldwide).

Suivez ces étapes pour acheter des licences Power BI Pro dans le Centre d’administration Microsoft 365 :

1. Connectez-vous au [Centre d’administration Microsoft 365](https://admin.microsoft.com).

2. Dans le menu de navigation, sélectionnez **Facturation** > **Acheter des services**.

3. Effectuez une recherche ou faites défiler la liste pour trouver l’abonnement que vous souhaitez acheter. Vous trouverez **Power BI** sous **Autres catégories susceptibles de vous intéresser** en bas de la page. Sélectionnez le lien pour afficher les abonnements Power BI disponibles pour votre organisation.

4. Sélectionnez **Power BI Pro**.

5. Sur la page **Acheter des services**, sélectionnez **Acheter**.

6. Choisissez **Paiement mensuel** ou **Paiement pour toute une année**, en fonction de vos préférences de paiement.

7. Sous **Combien d’utilisateurs voulez-vous ?** , entrez le nombre de licences que vous souhaitez acheter, puis sélectionnez **Régler maintenant** pour finaliser la transaction.

8. Pour vérifier votre achat, accédez à **Facturation** > **Produits et services** et recherchez **Power BI Pro**.

9. Pour ajouter d’autres licences ultérieurement, recherchez **Power BI Pro** sur la page **Produits et services**, puis sélectionnez **Ajouter/supprimer des licences**.


## <a name="assign-licenses-in-the-microsoft-365-admin-center"></a>Attribuer des licences dans le Centre d’administration Microsoft 365

Pour obtenir des informations sur l’attribution de licences dans le Centre d’administration Microsoft 365, consultez [Attribuer des licences aux utilisateurs](/office365/admin/manage/assign-licenses-to-users).

Pour les utilisateurs invités, consultez [Attribution de licences à des utilisateurs via la page Licences](/office365/admin/manage/assign-licenses-to-users#assign-licenses-to-users-on-the-licenses-page). Avant d’attribuer des licences Pro à des utilisateurs invités, vérifiez auprès de votre responsable de compte Microsoft que vous respectez les conditions de votre contrat avec Microsoft.

## <a name="assign-licenses-in-the-azure-portal"></a>Attribuer des licences dans le portail Azure

Suivez ces étapes pour affecter des licences Power BI Pro à des comptes d’utilisateur individuels :

1. Connectez-vous au [portail Azure](https://portal.azure.com/).

2. Recherchez et sélectionnez **Azure Active Directory**.

3. Sous **Gérer** dans le menu de ressources **Azure Active Directory**, sélectionnez **Licences**.

4. Sélectionnez **Tous les produits** dans le menu de ressources **Licences – Vue d’ensemble**, puis **Power BI Pro** pour afficher la liste des utilisateurs sous licence.

5. Dans la barre de commandes, sélectionnez **+ Attribuer**. Sur la page **Attribuer une licence**, commencez par choisir un utilisateur, puis sélectionnez **Options d’affectation** afin d’activer une licence Power BI Pro pour le compte d’utilisateur sélectionné.

## <a name="next-steps"></a>Étapes suivantes

- [Gestion des licences Power BI dans votre organisation](service-admin-licensing-organization.md)

 - [Rechercher les utilisateurs Power BI qui se sont connectés](service-admin-access-usage.md)

 - [S’inscrire à Power BI en tant qu’individu](../fundamentals/service-self-service-signup-for-power-bi.md)

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)