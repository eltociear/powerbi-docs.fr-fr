---
title: Acheter et attribuer des licences Power BI Pro
description: Découvrez comment acheter et attribuer des licences Power BI Pro pour permettre à vos utilisateurs d’accéder à du contenu et de collaborer avec des collègues dans le service Power BI.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: quickstart
ms.date: 10/29/2019
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: ebaf32bbf84dcbb8efd8516fd0a1ab01011f2d63
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74698483"
---
# <a name="purchase-and-assign-power-bi-pro-user-licenses"></a>Acheter et attribuer des licences utilisateur Power BI Pro

Power BI Pro est une licence utilisateur individuelle qui permet aux utilisateurs de lire et d’interagir avec des rapports et des tableaux de bord que d’autres utilisateurs ont publiés dans le service Power BI, et de partager du contenu et de collaborer avec d’autres utilisateurs Power BI Pro. Seuls les utilisateurs disposant d’une licence utilisateur Power BI Pro peuvent publier ou partager du contenu avec d’autres utilisateurs ou consommer du contenu créé par d’autres utilisateurs, sauf si ce contenu est hébergé dans une capacité Power BI Premium. Pour plus d’informations, consultez [Fonctionnalités de Power BI par type de licence](service-features-license-type.md).

## <a name="purchase-and-assign-power-bi-pro-user-licenses"></a>Acheter et attribuer des licences utilisateur Power BI Pro

Cet article explique comment acheter des licences utilisateur Power BI Pro dans le Centre d’administration Microsoft 365, puis explique deux options des administrateurs pour attribuer ces licences à des utilisateurs individuels : dans le Centre d’administration Microsoft 365 et dans le portail Azure (choisissez une option).

### <a name="prerequisites"></a>Conditions préalables

Pour acheter et attribuer des licences dans le Centre d’administration Microsoft 365, vous devez être membre du rôle **[Administrateur général ou Administrateur de facturation](https://support.office.com/article/about-office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d)** dans Microsoft 365.

Pour attribuer des licences dans le portail Azure, vous devez être propriétaire de l’abonnement Azure utilisé par Power BI pour les recherches Azure Active Directory.

### <a name="purchase-licenses-in-microsoft-365"></a>Acheter des licences dans Microsoft 365

Suivez ces étapes pour acheter des licences Power BI Pro dans le Centre d’administration Microsoft 365 :

1. Ouvrez le [Centre d’administration Microsoft 365](https://portal.office.com/adminportal/home#/homepage).

2. Dans le volet de navigation, sélectionnez **Facturation** > **Abonnements**.

    ![Volet de navigation](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-01.png)

3. Dans le coin supérieur droit de la page **Abonnements**, cliquez sur **Ajouter des abonnements**.

    ![Abonnement](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-02.png)

4. Recherchez l’offre d’abonnement souhaitée :

    Sous **Enterprise Suite**, sélectionnez **Office 365 Entreprise E5**.

    ![Abonnement Office E5](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-03.png)

    Sous **Autres forfaits**, sélectionnez **Power BI Pro**.

    ![Abonnement Power BI Pro](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-04.png)

5. Placez le curseur sur les points de suspension ( **. . .** ) pour l’abonnement souhaité et sélectionnez **Acheter maintenant**.

    ![Acheter maintenant](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-05.png)

6. Choisissez **Paiement mensuel** ou **Paiement pour toute une année**, en fonction de vos préférences de facturation.

7. Sous **Combien d’utilisateurs voulez-vous ?** , entrez le nombre de licences souhaité, puis sélectionnez **Commander maintenant** pour finaliser la transaction.

8. Vérifiez que l’abonnement acquis apparaît maintenant sur la page **Abonnements**.

   ![Abonnement acquis](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-06.png)

9. Pour ajouter d’autres licences après l’achat initial, sélectionnez **Power BI Pro** sur la page **Abonnements**, puis **Ajouter/supprimer des licences**.

### <a name="assign-licenses-in-the-microsoft-365-admin-center"></a>Attribuer des licences dans le Centre d’administration Microsoft 365

Suivez ces étapes pour affecter des licences Power BI Pro à des comptes d’utilisateur individuels :

1. Ouvrez le [Centre d’administration Microsoft 365](https://portal.office.com/adminportal/home#/homepage).

2. Dans le volet de navigation, développez **Utilisateurs**, puis sélectionnez **Utilisateurs actifs**.

    ![Utilisateurs actifs](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-05.png)

3. Sélectionnez un utilisateur puis, sous **Licences**, choisissez **Modifier**.

    ![Modifier des licences de produits](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-06.png)

4. Sous **Power BI Pro**, faites passer la valeur à **Activé**, puis sélectionnez **Enregistrer**.

    ![Licences de produits activées](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-07.png)

5. Sous **État** pour le compte sélectionné, vérifiez que la licence Power BI Pro a été affectée.

    ![Vérifier l’état de la licence](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-08.png)

### <a name="assign-licenses-in-the-azure-portal"></a>Attribuer des licences dans le portail Azure

Suivez ces étapes pour affecter des licences Power BI Pro à des comptes d’utilisateur individuels :

1. Accédez au [portail Azure](https://ms.portal.azure.com/#@microsoft.onmicrosoft.com/dashboard/private/39bc3cf7-31a4-43f6-954c-f2d69ca2f0).

2. Dans le volet de navigation, sélectionnez **Azure Active Directory**.

    ![Azure Active Directory](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-01.png)

3. Sous **Azure Active Directory**, sélectionnez **Licences**.

    ![Licences](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-02.png)

4. Sous **Licences**, sélectionnez **Tous les produits**, puis **Power BI Pro** pour afficher la liste des utilisateurs avec licence.

    ![Licences - Tous les produits](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-03.png)

5. Sélectionnez **Attribuer** pour ajouter une licence Power BI Pro à un compte d’utilisateur.

    ![Affecter une licence](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-04.png)

## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous avez affecté des licences, découvrez plus en détail Power BI Pro.

[Gestion des licences Power BI dans votre organisation](service-admin-licensing-organization.md)

[Rechercher les utilisateurs Power BI qui se sont connectés](service-admin-access-usage.md)

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
