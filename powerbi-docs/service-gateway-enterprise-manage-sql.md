---
title: Gérer votre source de données - SQL
description: Gestion de la passerelle de données locale et des sources de données associées.
author: mgblythe
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 66e9b53761fa154fe76cefea99cb5c88345b97aa
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73881635"
---
# <a name="manage-your-data-source---sql-server"></a>Gérer votre source de données - SQL Server

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Une fois que vous avez [installé la passerelle de données locale](/data-integration/gateway/service-gateway-install), vous pouvez [ajouter des sources de données](service-gateway-data-sources.md#add-a-data-source) qui peuvent être utilisées avec la passerelle. Cet article examine comment travailler avec des passerelles et des sources de données SQL Server utilisées pour l’actualisation planifiée ou pour DirectQuery.

## <a name="add-a-data-source"></a>Ajouter une source de données

Pour plus d’informations sur la façon d’ajouter une source de données, voir [Ajouter une source de données](service-gateway-data-sources.md#add-a-data-source). Sous **Type de source de données**, sélectionnez **SQL Server**.

![Sélectionner la source de données SQL Server](media/service-gateway-enterprise-manage-sql/datasourcesettings2.png)

> [!NOTE]
> Quand vous utilisez DirectQuery, la passerelle prend en charge uniquement **SQL Server 2012 SP1** et ultérieur.

Renseignez ensuite les informations relatives à la source de données, notamment le **Serveur** et la **Base de données**. 

Sous **Méthode d’authentification**, choisissez **Windows** ou **De base**. Choisissez **De base** si vous envisagez d’utiliser l’authentification SQL plutôt que l’authentification Windows. Entrez les informations d’identification à utiliser pour cette source de données.

> [!NOTE]
> Toutes les requêtes adressées à la source de données utilisent ces informations d’identification, sauf si une authentification unique (SSO) Kerberos est configurée et activée pour la source de données. Avec l’authentification unique, les jeux de données d’importation utilisent les informations d’identification stockées, mais les jeux de données DirectQuery se servent de l’utilisateur Power BI actif pour exécuter les requêtes à l’aide de l’authentification unique. Pour plus d’informations sur la façon dont les informations d’identification sont stockées, voir [Stocker des informations d’identification chiffrées dans le cloud](service-gateway-data-sources.md#store-encrypted-credentials-in-the-cloud). Ou consultez l’article qui explique comment [utiliser Kerberos pour l’authentification unique (SSO) de Power BI à des sources de données locales](service-gateway-sso-kerberos.md).

![Spécification des paramètres de la source de données](media/service-gateway-enterprise-manage-sql/datasourcesettings3.png)

Une fois que vous avez renseigné toutes les valeurs,sélectionnez **Ajouter**. Vous pouvez à présent utiliser cette source de données pour l’actualisation planifiée ou DirectQuery sur un serveur SQL Server local. L’indication *Connexion réussie* apparaît une fois la connexion établie.

![Affichage de l’état de la connexion](media/service-gateway-enterprise-manage-sql/datasourcesettings4.png)

### <a name="advanced-settings"></a>Paramètres avancés

Vous pouvez aussi configurer le niveau de confidentialité de votre source de données. Ce paramètre contrôle la façon dont les données peuvent être combinées. Il concerne uniquement l’actualisation planifiée. Le paramètre de niveau de confidentialité ne s’applique pas à DirectQuery. Pour plus d’informations sur les niveaux de confidentialité de votre source de données, consultez [Niveaux de confidentialité (Power Query)](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540).

![Définition du niveau de confidentialité](media/service-gateway-enterprise-manage-sql/datasourcesettings9.png)

## <a name="use-the-data-source"></a>Utiliser la source de données

Une fois la source de données créée, elle peut être utilisée avec des connexions DirectQuery ou via une actualisation planifiée.

> [!NOTE]
> Le nom du serveur et celui de la base de données doivent correspondre entre Power BI Desktop et la source de données dans la passerelle de données locale.

Le lien entre votre jeu de données et la source de données dans la passerelle est basé sur le nom de votre serveur et sur le nom de votre base de données. Ces noms doivent correspondre. Par exemple, si vous fournissez une adresse IP pour le nom du serveur dans Power BI Desktop, vous devez utiliser l’adresse IP de la source de données dans la configuration de la passerelle. Si vous utilisez *SERVEUR\INSTANCE*, dans Power BI Desktop, vous devez utiliser la même valeur dans la source de données configurée pour la passerelle.

Cette exigence concerne DirectQuery et l’actualisation planifiée.

### <a name="use-the-data-source-with-directquery-connections"></a>Utiliser la source de données avec des connexions DirectQuery

Vérifiez que le nom du serveur et celui de la base de données correspondent entre Power BI Desktop et la source de données configurée pour la passerelle. Vous devez également vérifier que votre utilisateur est listé sous l’onglet **Utilisateurs** de la source de données pour qu’il puisse publier des jeux de données DirectQuery. Pour DirectQuery, la sélection se produit dans Power BI Desktop la première fois que vous importez des données. Pour plus d’informations sur la façon d’utiliser DirectQuery, consultez [Utiliser DirectQuery dans Power BI Desktop](desktop-use-directquery.md).

Une fois la publication effectuée, que ce soit à partir de Power BI Desktop ou de l’option **Obtenir les données**, vos rapports doivent commencer à fonctionner. Après la création de la source de données dans la passerelle, plusieurs minutes peuvent s’écouler avant que la connexion soit utilisable.

### <a name="use-the-data-source-with-scheduled-refresh"></a>Utiliser la source de données avec une actualisation planifiée

Si vous êtes listé sous l’onglet **Utilisateurs** de la source de données configurée dans la passerelle, et que le nom du serveur et celui de la base de données correspondent, la passerelle s’affiche comme option à utiliser avec l’actualisation planifiée.

![Affichage des utilisateurs](media/service-gateway-enterprise-manage-sql/powerbi-gateway-enterprise-schedule-refresh.png)

## <a name="next-steps"></a>Étapes suivantes

* [Se connecter à des données locales dans SQL Server](service-gateway-sql-tutorial.md)
* [Résolution des problèmes de passerelle de données locale](/data-integration/gateway/service-gateway-tshoot)
* [Résoudre les problèmes liés aux passerelles - Power BI](service-gateway-onprem-tshoot.md)
* [Utiliser Kerberos pour l’authentification unique (SSO) de Power BI à des sources de données locales](service-gateway-sso-kerberos.md)

D’autres questions ? Essayez de d’interroger la [Communauté Power BI](https://community.powerbi.com/).

