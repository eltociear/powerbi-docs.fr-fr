---
title: Gérer les sources de données
description: Découvrez comment gérer les sources de données dans Power BI.
author: arthiriyer
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 02/21/2020
ms.author: arthii
ms.custom: seodec18
LocalizationGroup: Gateways
ms.openlocfilehash: 15b3236741eb19d9f08601f9503e0380f54a8d63
ms.sourcegitcommit: 7e845812874b3347bcf87ca642c66bed298b244a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79207456"
---
# <a name="manage-data-sources"></a>Gérer les sources de données

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Power BI prend en charge de nombreuses [sources de données locales](power-bi-data-sources.md), chacune ayant ses propres exigences. Une passerelle peut être utilisée pour une seule ou plusieurs sources de données. Pour cet exemple, nous vous montrons comment ajouter SQL Server en tant que source de données. Les étapes sont similaires pour d’autres sources de données.

La plupart des opérations de gestion des sources de données peuvent également être effectuées avec des API. Pour plus d’informations, voir [API REST (passerelles)](/rest/api/power-bi/gateways).

## <a name="add-a-data-source"></a>Ajouter une source de données

1. Dans l’angle supérieur droit du service Power BI, sélectionnez l’![icône d’engrenage Paramètres](media/service-gateway-data-sources/icon-gear.png) > **Gérer les passerelles**.

    ![Gérer les passerelles](media/service-gateway-data-sources/manage-gateways.png)

2. Choisissez une passerelle, puis sélectionnez **Ajouter une source de données**. Ou bien accédez à **Passerelles** > **Ajouter une source de données**.

    ![Ajouter une source de données](media/service-gateway-data-sources/add-data-source.png)

3. Sélectionnez le **type de source de données**.

    ![Sélectionner SQL Server](media/service-gateway-data-sources/select-sql-server.png)

4. Entrez les informations de la source de données. Pour cet exemple, indiquez le **serveur**, la **base de données** et d’autres informations. 

    ![Paramètres de la source de données](media/service-gateway-data-sources/data-source-settings.png)

5. Pour SQL Server, vous choisissez la **Méthode d’authentification** **Windows** ou **De base** (Authentification SQL). Si vous choisissez **De base**, entrez les informations d’identification de votre source de données.

6. Sous **Paramètres avancés**, vous pouvez configurer [Authentification unique (SSO)](service-gateway-sso-overview.md) pour votre source de données. 

    ![Paramètres avancés](media/service-gateway-data-sources/advanced-settings-02.png)

Vous pouvez configurer **Utiliser SSO via Kerberos pour les requêtes DirectQuery** ou **Utiliser SSO via Kerberos pour les requêtes DirectQuery et d’importation** pour les rapports basés sur DirectQuery et **Utiliser SSO via Kerberos pour les requêtes DirectQuery et d’importation** pour les rapports basés sur l’actualisation.

Si vous utilisez **Utiliser SSO via Kerberos pour les requêtes DirectQuery** et cette source de données pour un rapport basé sur DirectQuery, elle utilise l’utilisateur mappé à l’utilisateur (Azure) Active Directory qui se connecte au service Power BI. Pour un rapport basé sur l’actualisation, elle utilise les informations d’identification que vous entrez dans les champs **Nom d’utilisateur** et **Mot de passe**.

Si vous utilisez **Utiliser SSO via Kerberos pour les requêtes DirectQuery et d’importation**, vous n’avez pas besoin de fournir d’informations d’identification. Si cette source de données est utilisée pour un rapport basé sur DirectQuery, elle utilise l’utilisateur mappé à l’utilisateur (Azure) Active Directory qui se connecte au service Power BI.  Pour un rapport basé sur l’actualisation, elle utilise le contexte de sécurité du propriétaire du jeu de données.

> [!NOTE]
>L’authentification unique pour les requêtes d’importation est disponible uniquement pour la liste des sources de données SSO utilisant la [délégation Kerberos contrainte](service-gateway-sso-kerberos.md).

7. Sous **Paramètres avancés**, vous pouvez si vous le souhaitez configurer le [niveau de confidentialité](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540) de votre source de données (ne s’applique pas à [DirectQuery](desktop-directquery-about.md)).

    ![Paramètres avancés](media/service-gateway-data-sources/advanced-settings.png)

8. Sélectionnez **Ajouter**. Le message *Connexion établie* apparaît si l’opération réussit.

    ![Connexion établie](media/service-gateway-data-sources/connection-successful.png)

Vous pouvez maintenant utiliser cette source de données pour inclure des données provenant de SQL Server dans vos tableaux de bord Power BI et vos rapports.

## <a name="remove-a-data-source"></a>Supprimez une source de données.

Vous pouvez supprimer une source de données si vous ne l’utilisez plus. La suppression d’une source de données entraîne l’arrêt des éventuels tableaux de bord ou rapports qui reposent sur celle-ci.

Pour supprimer une source de données, accédez à celle-ci, puis sélectionnez **Supprimer**.

![Supprimez une source de données.](media/service-gateway-data-sources/remove-data-source.png)

## <a name="use-the-data-source-for-scheduled-refresh-or-directquery"></a>Utiliser la source de données pour une actualisation planifiée ou DirectQuery

Une fois la source de données créée, elle peut être utilisée avec des connexions DirectQuery ou via une actualisation planifiée.

> [!NOTE]
>Le nom du serveur et celui de la base de données doivent correspondre entre Power BI Desktop et la source de données dans la passerelle de données locale.

Le lien entre votre jeu de données et la source de données dans la passerelle est basé sur le nom de votre serveur et sur le nom de votre base de données. Ces noms doivent correspondre. Par exemple, si vous fournissez une adresse IP pour le nom du serveur, dans Power BI Desktop, vous devez utiliser l’adresse IP pour la source de données dans la configuration de la passerelle. Si vous utilisez *SERVEUR\INSTANCE*, dans Power BI Desktop, vous devez utiliser la même valeur dans la source de données configurée pour la passerelle.

Si vous êtes répertorié sous l’onglet **Utilisateurs** de la source de données configurée dans la passerelle, et que le nom du serveur et celui de la base de données correspondent, la passerelle s’affiche comme option à utiliser avec l’actualisation planifiée.

![Connexion à la passerelle](media/service-gateway-data-sources/gateway-connection.png)

> [!WARNING]
> Si votre jeu de données contient plusieurs sources de données, chaque source de données doit être ajoutée dans la passerelle. Si une ou plusieurs sources de données ne sont pas ajoutées à la passerelle, celle-ci n’apparaît pas comme disponible pour l’actualisation planifiée.

### <a name="limitations"></a>Limites

OAuth est un schéma d’authentification pris en charge seulement pour les connecteurs personnalisés avec la passerelle de données locale. Vous ne pouvez pas ajouter d’autres sources de données qui nécessitent OAuth. Si votre jeu de données a une source de données nécessitant OAuth et que celle-ci n’est pas un connecteur personnalisé, vous ne pouvez pas utiliser la passerelle pour une actualisation planifiée.

## <a name="manage-users"></a>Gérer les utilisateurs

Après avoir ajouté une source de données à une passerelle, vous donnez aux utilisateurs et aux groupes de sécurité activés par e-mail l’accès à la source de données spécifique (et non à l’ensemble de la passerelle). La liste des utilisateurs de la source de données contrôle uniquement les personnes autorisées à publier des rapports incluant des données provenant de la source de données. Les propriétaires des rapports peuvent créer des tableaux de bord, des packs de contenu et des apps, puis partager ces éléments avec d’autres utilisateurs.

Vous pouvez également donner aux utilisateurs et groupes de sécurité un accès administratif à la passerelle.

### <a name="add-users-to-a-data-source"></a>Ajouter des utilisateurs à une source de données

1. Dans l’angle supérieur droit du service Power BI, sélectionnez l’![icône d’engrenage Paramètres](media/service-gateway-data-sources/icon-gear.png) > **Gérer les passerelles**.

2. Sélectionnez la source de données à laquelle vous souhaitez ajouter des utilisateurs.

3. Sélectionnez **Utilisateurs**, puis entrez un utilisateur de votre organisation auquel vous souhaiter accorder l’accès à la source de données sélectionnée. Par exemple, dans l’écran suivant, vous ajoutez Maggie et Adam.

    ![Onglet Utilisateurs](media/service-gateway-data-sources/users-tab.png)

4. Sélectionnez **Ajouter**, et le nom du membre ajouté apparaît dans la zone.

    ![Ajouter un utilisateur](media/service-gateway-data-sources/add-user.png)

Rappelez-vous que vous devez ajouter des utilisateurs à chaque source de données à laquelle vous souhaitez accorder l’accès. Chaque source de données possède une liste distincte d’utilisateurs. Ajoutez des utilisateurs à chaque source de données séparément.

### <a name="remove-users-from-a-data-source"></a>Supprimer des utilisateurs d’une source de données

Sous l’onglet **Utilisateurs** de la source de données, vous pouvez supprimer des utilisateurs et des groupes de données qui peuvent utiliser cette source de données.

![Supprimer l’utilisateur](media/service-gateway-data-sources/remove-user.png)

## <a name="store-encrypted-credentials-in-the-cloud"></a>Stocker des informations d’identification chiffrées dans le cloud

Lorsque vous ajoutez une source de données à la passerelle, vous devez fournir les informations d’identification associées. Toutes les requêtes à la source de données sont exécutées à l’aide de ces informations d’identification. Les informations d’identification sont chiffrées en toute sécurité. Elle utilisent un chiffrement symétrique afin qu’il ne soit pas possible de les déchiffrer dans le cloud avant de les y stocker. Les informations d’identification sont envoyées à la machine exécutant la passerelle en local, où elles sont déchiffrées lors de l’accès aux sources de données.

## <a name="list-of-available-data-source-types"></a>Liste des types de sources de données disponibles

Pour plus d’informations sur les sources de données prises en charge par la passerelle de données locale, consultez [Sources de données Power BI](power-bi-data-sources.md).

## <a name="next-steps"></a>Étapes suivantes

* [Gérer votre source de données - Analysis Services](service-gateway-enterprise-manage-ssas.md)
* [Gérer votre source de données - SAP HANA](service-gateway-enterprise-manage-sap.md)
* [Gérer votre source de données - SQL Server](service-gateway-enterprise-manage-sql.md)
* [Gérer votre source de données - Oracle](service-gateway-onprem-manage-oracle.md)
* [Gérer votre source de données – Importation/actualisation planifiée](service-gateway-enterprise-manage-scheduled-refresh.md)
* [Conseils de déploiement d’une passerelle de données](service-gateway-deployment-guidance.md)

D’autres questions ? Essayez la [communauté Power BI](https://community.powerbi.com/).
