---
title: Gérer votre source de données – Importation/Actualisation planifiée
description: Gestion de la passerelle de données locale et des sources de données associées. Cet article porte spécifiquement sur les sources de données qui peuvent être utilisées avec les fonctions d’importation et d’actualisation planifiée.
author: arthiriyer
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: how-to
ms.date: 11/17/2020
ms.author: arthii
LocalizationGroup: Gateways
ms.openlocfilehash: bb61f752891205a0e8997592d522efb2022a562b
ms.sourcegitcommit: 5240990f998851c4854eb565de681099264c5a61
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94719026"
---
# <a name="manage-your-data-source---importscheduled-refresh"></a>Gérer votre source de données – Importation/Actualisation planifiée

[!INCLUDE [gateway-rewrite](../includes/gateway-rewrite.md)]

Une fois que vous avez [installé la passerelle de données locale](/data-integration/gateway/service-gateway-install), vous devez [ajouter des sources de données](service-gateway-data-sources.md#add-a-data-source) qui peuvent être utilisées avec la passerelle. Cet article examine comment travailler avec des passerelles et des sources de données utilisées pour l’actualisation planifiée, et non pas avec des connexions actives ou DirectQuery.

## <a name="add-a-data-source"></a>Ajouter une source de données

Pour plus d’informations sur la façon d’ajouter une source de données, voir [Ajouter une source de données](service-gateway-data-sources.md#add-a-data-source). Sélectionnez un type de source de données.

Tous les types de sources de données répertoriées peuvent être utilisés à des fins d’actualisation planifiée avec la passerelle de données locale. Vous pouvez utiliser Analysis Services, SQL Server et SAP HANA pour l’actualisation planifiée ou des connexions actives/DirectQuery.

![Sélectionner la source de données](media/service-gateway-enterprise-manage-scheduled-refresh/datasourcesettings2.png)

Ensuite, renseignez les informations relatives à la source de données, notamment les informations sur la source et les informations d’identification utilisées pour accéder à la source de données.

> [!NOTE]
> Toutes les requêtes à la source de données sont exécutées à l’aide de ces informations d’identification. Pour plus d’informations sur la façon dont les informations d’identification sont stockées, voir [Stocker des informations d’identification chiffrées dans le cloud](service-gateway-data-sources.md#store-encrypted-credentials-in-the-cloud).

![Spécification des paramètres de la source de données](media/service-gateway-enterprise-manage-scheduled-refresh/datasourcesettings3-oracle.png)

Pour obtenir la liste des types de sources de données qui peuvent être utilisées avec l’actualisation planifiée, consultez [Liste des types de sources de données disponibles](service-gateway-data-sources.md#list-of-available-data-source-types).

Une fois que vous avez renseigné toutes les valeurs,sélectionnez **Ajouter**. Vous pouvez à présent utiliser cette source de données pour l’actualisation planifiée avec vos données locales. L’indication *Connexion réussie* apparaît une fois la connexion établie.

![Affichage de l’état de la connexion](media/service-gateway-enterprise-manage-scheduled-refresh/datasourcesettings4.png)

### <a name="advanced-settings"></a>Paramètres avancés

Vous pouvez aussi configurer le niveau de confidentialité de votre source de données. Ce paramètre contrôle la façon dont les données peuvent être combinées. Il concerne uniquement l’actualisation planifiée. Pour plus d’informations sur les niveaux de confidentialité de votre source de données, consultez [Niveaux de confidentialité (Power Query)](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540).

![Définition du niveau de confidentialité](media/service-gateway-enterprise-manage-scheduled-refresh/datasourcesettings9.png)

## <a name="use-the-data-source-for-scheduled-refresh"></a>Utiliser la source de données pour une actualisation planifiée

Une fois la source de données créée, elle peut être utilisée avec des connexions DirectQuery ou via une actualisation planifiée.

> [!NOTE]
> Le nom du serveur et celui de la base de données doivent correspondre entre Power BI Desktop et la source de données dans la passerelle de données locale.

Le lien entre votre jeu de données et la source de données dans la passerelle est basé sur le nom de votre serveur et sur le nom de votre base de données. Ces noms doivent correspondre. Par exemple, si vous fournissez une adresse IP pour le nom du serveur dans Power BI Desktop, vous devez utiliser l’adresse IP de la source de données dans la configuration de la passerelle. Si vous utilisez *SERVEUR\INSTANCE*, dans Power BI Desktop, vous devez utiliser la même valeur dans la source de données configurée pour la passerelle.

Si vous êtes listé sous l’onglet **Utilisateurs** de la source de données configurée dans la passerelle, et que le nom du serveur et celui de la base de données correspondent, la passerelle s’affiche comme option à utiliser avec l’actualisation planifiée.

![Affichage des utilisateurs](media/service-gateway-enterprise-manage-scheduled-refresh/powerbi-gateway-enterprise-schedule-refresh.png)

> [!IMPORTANT]
> Après republication, le propriétaire du jeu de données doit réassocier le jeu de données à une passerelle et à la source de données correspondante. L’association précédente n’est pas conservée après la republication. 

> [!WARNING]
> Si votre jeu de données contient plusieurs sources de données, chaque source de données doit être ajoutée au sein de la passerelle. Si une ou plusieurs sources de données ne sont pas ajoutées à la passerelle, celle-ci n’apparaît pas comme disponible pour l’actualisation planifiée.

## <a name="next-steps"></a>Étapes suivantes

* [Résolution des problèmes de passerelle de données locale](/data-integration/gateway/service-gateway-tshoot)
* [Résoudre les problèmes liés aux passerelles - Power BI](service-gateway-onprem-tshoot.md)

D’autres questions ? Essayez la [communauté Power BI](https://community.powerbi.com/).
