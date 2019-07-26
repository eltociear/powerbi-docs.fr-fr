---
title: Gérer votre source de données - SAP HANA
description: Gestion de la passerelle de données locale et des sources de données associées. Cet article est propre à SAP HANA.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: b61d794701d18fd25ab9acb5d5208ae289376eb6
ms.sourcegitcommit: 277fadf523e2555004f074ec36054bbddec407f8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68271740"
---
# <a name="manage-your-data-source---sap-hana"></a>Gérer votre source de données - SAP HANA

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Une fois que vous avez [installé la passerelle de données locale](/data-integration/gateway/service-gateway-install), vous devez [ajouter des sources de données](service-gateway-data-sources.md#add-a-data-source) qui peuvent être utilisées avec la passerelle. Cet article explique comment travailler avec des passerelles et des sources de données SAP HANA utilisées pour l’actualisation planifiée ou pour DirectQuery.

## <a name="add-a-data-source"></a>Ajouter une source de données

Pour plus d’informations sur l’ajout d’une source de données, consultez [Ajouter une source de données](service-gateway-data-sources.md#add-a-data-source). Sélectionnez SAP HANA comme **Type de source de données**.

![Ajouter la source de données SAP HANA](media/service-gateway-enterprise-manage-sap/datasourcesettings2-sap.png)

Après avoir sélectionné le type de source de données SAP HANA, vous renseignez les informations **Serveur**, **Nom d’utilisateur** et **Mot de passe** pour la source de données.

> [!NOTE]
> Toutes les requêtes à la source de données sont exécutées à l’aide de ces informations d’identification. Pour plus d’informations sur la façon dont les informations d’identification sont stockées, consultez [Stockage d’informations d’identification chiffrées dans le cloud](service-gateway-data-sources.md#storing-encrypted-credentials-in-the-cloud).

![Spécification des paramètres de la source de données](media/service-gateway-enterprise-manage-sap/datasourcesettings3-sap.png)

Sélectionnez **Ajouter** après avoir renseigné toutes les informations. Vous pouvez à présent utiliser cette source de données pour l’actualisation planifiée ou DirectQuery sur un serveur SAP HANA local. L’indication *Connexion réussie* apparaît une fois la connexion établie.

![Affichage de l’état de la connexion](media/service-gateway-enterprise-manage-sap/datasourcesettings4.png)

### <a name="advanced-settings"></a>Paramètres avancés

Vous pouvez aussi configurer le niveau de confidentialité de votre source de données. Ceci contrôle la façon dont les données peuvent être combinées. Cette option concerne uniquement l’actualisation planifiée ; elle ne s’applique pas à DirectQuery. Pour plus d’informations sur les niveaux de confidentialité de votre source de données, consultez [Niveaux de confidentialité (Power Query)](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540).

![Définition du niveau de confidentialité](media/service-gateway-enterprise-manage-sap/datasourcesettings9.png)

## <a name="using-the-data-source"></a>Utilisation de la source de données

Une fois la source de données créée, elle peut être utilisée avec des connexions DirectQuery ou via une actualisation planifiée.

> [!NOTE]
> Le nom du serveur et celui de la base de données doivent correspondre entre Power BI Desktop et la source de données dans la passerelle de données locale.

Le lien entre votre jeu de données et la source de données dans la passerelle est basé sur le nom de votre serveur et sur le nom de votre base de données. Ils doivent correspondre. Par exemple, si vous fournissez une adresse IP pour le nom du serveur, dans Power BI Desktop, vous devez utiliser l’adresse IP de la source de données dans la configuration de la passerelle. Si vous utilisez *SERVEUR\INSTANCE*, dans Power BI Desktop, vous devez utiliser la même valeur dans la source de données configurée pour la passerelle.

C’est le cas pour DirectQuery et pour l’actualisation planifiée.

### <a name="using-the-data-source-with-directquery-connections"></a>Utilisation de la source de données avec des connexions DirectQuery

Vous devez vérifier que le nom du serveur et celui de la base de données correspondent entre Power BI Desktop et la source de données configurée pour la passerelle. Vous devez également vérifier que votre utilisateur est listé sous l’onglet **Utilisateurs** de la source de données pour qu’il puisse publier des jeux de données DirectQuery. Pour DirectQuery, la sélection se produit dans Power BI Desktop la première fois que vous importez des données. Pour plus d’informations sur l’utilisation de DirectQuery, consultez [Utiliser DirectQuery dans Power BI Desktop](desktop-use-directquery.md).

Une fois la publication effectuée, que ce soit à partir de Power BI Desktop ou de l’option **Obtenir les données**, vos rapports doivent commencer à fonctionner. Après la création de la source de données dans la passerelle, plusieurs minutes peuvent être nécessaires pour que la connexion puisse être utilisée.

### <a name="using-the-data-source-with-scheduled-refresh"></a>Utilisation de la source de données avec une actualisation planifiée

Si vous êtes listé sous l’onglet **Utilisateurs** de la source de données configurée dans la passerelle, et que le nom du serveur et celui de la base de données correspondent, la passerelle s’affiche comme option à utiliser avec l’actualisation planifiée.

![Affichage des utilisateurs](media/service-gateway-enterprise-manage-sap/powerbi-gateway-enterprise-schedule-refresh.png)

## <a name="next-steps"></a>Étapes suivantes

* [Résolution des problèmes de passerelle de données locale](/data-integration/gateway/service-gateway-tshoot)
* [Résoudre les problèmes liés aux passerelles - Power BI](service-gateway-onprem-tshoot.md)  

D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)

