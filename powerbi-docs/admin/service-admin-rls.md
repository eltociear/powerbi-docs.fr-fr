---
title: Sécurité au niveau des lignes avec Power BI
description: Configuration de DirectQuery et de la sécurité au niveau des lignes pour les jeux de données importés dans le service Power BI
author: paulinbar
ms.author: painbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 09/17/2020
ms.custom: seodec18
LocalizationGroup: Administration
ms.openlocfilehash: f1358cbafa08c0dbb3790322c414d7a746386f0f
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96408570"
---
# <a name="row-level-security-rls-with-power-bi"></a>Sécurité au niveau des lignes avec Power BI

La sécurité au niveau des lignes avec Power BI peut être utilisée pour restreindre l’accès aux données pour certains utilisateurs. Les filtres limitent l’accès aux données au niveau des lignes, et vous pouvez définir des filtres dans des rôles. Dans le service Power BI, les membres d’un espace de travail ont accès aux jeux de données de l’espace de travail. La sécurité au niveau des lignes (SNL) ne restreint pas cet accès aux données.

Vous pouvez configurer la sécurité au niveau des lignes (SNL) pour les modèles de données importés dans Power BI avec Power BI Desktop. Vous pouvez également configurer la sécurité au niveau des lignes sur les jeux de données qui utilisent DirectQuery, tels que SQL Server. En ce qui concerne les connexions actives Analysis Services ou Azure Analysis Services, la Sécurité au niveau des lignes est configurée dans le modèle, et non dans Power BI Desktop. L’option de sécurité ne s’affiche pas pour les jeux de données d’une connexion active.

[!INCLUDE [include-short-name](../includes/rls-desktop-define-roles.md)]

Par défaut, le filtrage de sécurité au niveau des lignes utilise des filtres unidirectionnels, que les relations soient définies comme unidirectionnelles ou bidirectionnelles. Pour activer manuellement le filtrage croisé bidirectionnel avec la sécurité au niveau des lignes, sélectionnez la relation et cochez la case **Appliquer le filtre de sécurité dans les deux directions**. Sélectionnez cette option quand vous avez également implémenté, au niveau du serveur, la sécurité dynamique au niveau des lignes, qui s’appuie sur un nom d’utilisateur ou un ID de connexion.

Pour plus d’informations, consultez [Filtrage croisé bidirectionnel avec DirectQuery dans Power BI Desktop](../transform-model/desktop-bidirectional-filtering.md) et [Sécurisation du modèle sémantique BI tabulaire](https://download.microsoft.com/download/D/2/0/D20E1C5F-72EA-4505-9F26-FEF9550EFD44/Securing%20the%20Tabular%20BI%20Semantic%20Model.docx).

![Appliquer un filtre de sécurité](media/service-admin-rls/rls-apply-security-filter.png)


[!INCLUDE [include-short-name](../includes/rls-desktop-view-as-roles.md)]

## <a name="manage-security-on-your-model"></a>Gérer la sécurité sur votre modèle

Pour gérer la sécurité sur votre modèle de données, procédez comme suit :

1. Dans le service Power BI, sélectionnez le menu **Plus d’options** pour un jeu de données. Ce menu s’affiche lorsque vous pointez sur un nom de jeu de données, que vous le sélectionniez dans le menu de navigation ou sur la page de l’espace de travail.

    ![Menu Plus d’options dans l’espace de travail](media/service-admin-rls/dataset-leftnav-more-options.png)

    ![Menu Plus d’options dans le menu de navigation](media/service-admin-rls/dataset-canvas-more-options.png)

1. Sélectionnez **Sécurité**.

   ![Sélection de Sécurité dans le menu Plus d’options](media/service-admin-rls/dataset-more-options-menu.png)

En cliquant sur Sécurité, vous accédez à la page SNL, sur laquelle vous pouvez ajouter des membres à un rôle que vous avez créé dans Power BI Desktop. L’option Sécurité n’apparaît que pour les propriétaires du jeu de données. Si le jeu de données se trouve dans un groupe, seuls les administrateurs de ce groupe la verront.

Vous pouvez uniquement créer ou modifier des rôles dans Power BI Desktop.

## <a name="working-with-members"></a>Utilisation des membres

### <a name="add-members"></a>Ajouter des membres

Ajoutez un membre au rôle en entrant l’adresse e-mail ou le nom de l’utilisateur ou du groupe de sécurité. Il n’est pas possible d’ajouter des groupes créés dans Power BI. Vous pouvez ajouter des membres [externes à votre organisation](../guidance/whitepaper-azure-b2b-power-bi.md#data-security-for-external-partners).

![Ajouter un membre](media/service-admin-rls/rls-add-member.png)

Le nombre de membres du rôle est indiqué entre parenthèses à côté du nom du rôle ou de Membres.

![Membres du rôle](media/service-admin-rls/rls-member-count.png)

### <a name="remove-members"></a>Supprimer des membres

Vous pouvez supprimer des membres en cliquant sur la croix correspondant à leur nom. 

![Supprimer un membre](media/service-admin-rls/rls-remove-member.png)

## <a name="validating-the-role-within-the-power-bi-service"></a>Validation du rôle au sein du service Power BI

Vous pouvez vérifier que le rôle que vous avez défini fonctionne correctement en le testant.

1. Sélectionnez **Plus d’options** (...) en regard du rôle.
2. Sélectionnez **Tester les données comme rôle**

![Tester comme rôle](media/service-admin-rls/rls-test-role.png)

Les rapports disponibles pour ce rôle s’affichent. Les tableaux de bord n’apparaissent pas dans cette vue. Dans l’en-tête de page est indiqué le rôle en cours d’application.

![Affichage actuel en tant que <rôle>](media/service-admin-rls/rls-test-role2.png)

Testez d’autres rôles, ou une combinaison de rôles, en sélectionnant **Affichage actuel comme**.

![Tester d’autres rôles](media/service-admin-rls/rls-test-role3.png)

Vous pouvez choisir d’afficher les données comme pour une personne donnée ou sélectionner une combinaison de rôles disponibles pour vérifier qu’ils fonctionnent.

Pour revenir à l’affichage normal, sélectionnez **Retour à la sécurité au niveau des lignes**.

[!INCLUDE [include-short-name](../includes/rls-usernames.md)]

## <a name="using-rls-with-workspaces-in-power-bi"></a>Utilisation de la sécurité au niveau des lignes (SNL) avec des espaces de travail dans Power BI

Si vous publiez votre rapport Power BI Desktop dans un espace de travail du service Power BI, les rôles sont appliqués aux membres en lecture seule. Vous devez alors indiquer dans les paramètres de l’espace de travail que les membres peuvent uniquement afficher du contenu Power BI.

> [!WARNING]
> Si vous avez configuré l’espace de travail de sorte que les membres disposent d’autorisations de modification, les rôles SNL ne leur sont pas appliqués. Les utilisateurs voient toutes les données.

![Paramètres de groupe](media/service-admin-rls/rls-group-settings.png)

[!INCLUDE [include-short-name](../includes/rls-limitations.md)]

[!INCLUDE [include-short-name](../includes/rls-faq.md)]

## <a name="next-steps"></a>Étapes suivantes

- [Restreindre l’accès aux données avec la sécurité au niveau des lignes (SNL) pour Power BI Desktop](../create-reports/desktop-rls.md)
- [Aide sur la sécurité au niveau des lignes (RLS) dans Power BI Desktop](../guidance/rls-guidance.md)
- Vous avez des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
- Vous avez des suggestions ? [Envoyez-nous vos idées pour améliorer Power BI](https://ideas.powerbi.com/)
