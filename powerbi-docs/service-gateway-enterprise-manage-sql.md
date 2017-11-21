---
title: "Gérer votre source de données - SQL"
description: "Gestion de la passerelle de données locale et des sources de données associées."
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: powerbi
ms.date: 11/02/2017
ms.author: davidi
ms.openlocfilehash: 644078dc61a69cf27cb93b29409546d61e1706f2
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2017
---
# <a name="manage-your-data-source---sql-server"></a>Gérer votre source de données - SQL Server
Une fois que vous avez installé la passerelle de données locale, vous pouvez ajouter des sources de données utilisables avec la passerelle. Cet article décrit comment utiliser les passerelles et les sources de données. Vous pouvez utiliser la source de données SQL Server pour l’actualisation planifiée ou DirectQuery.

## <a name="download-and-install-the-gateway"></a>Télécharger et installer la passerelle
Vous pouvez télécharger la passerelle à partir du service Power BI. Sélectionnez **Téléchargements** > **Passerelle de données** ou accédez à la [page de téléchargement de la passerelle](https://go.microsoft.com/fwlink/?LinkId=698861).

![](media/service-gateway-enterprise-manage-sql/powerbi-download-data-gateway.png)

## <a name="add-a-gateway"></a>Ajouter une passerelle
Pour ajouter une passerelle, [téléchargez](https://go.microsoft.com/fwlink/?LinkId=698861) et installez la passerelle sur un serveur de votre environnement. Une fois la passerelle installée, elle apparaît dans les listes de passerelles sous **Gérer les passerelles**.

> [!NOTE]
> **Gérer les passerelles** n’apparaît pas si vous n’êtes pas administrateur d’au moins une passerelle. Cela se produit lorsque vous êtes ajouté en tant qu’administrateur à une passerelle, ou installez et configurez une passerelle vous-même.
> 
> 

## <a name="remove-a-gateway"></a>Supprimez une passerelle
La suppression d’une passerelle entraîne celle de toutes les sources de données associées.  Elle entraîne également l’arrêt des éventuels tableaux de bord et rapports qui reposent sur ces sources de données.

1. Sélectionnez l’icône Engrenage ![](media/service-gateway-enterprise-manage-sql/pbi_gearicon.png) en haut à droite > **Gérer les passerelles**.
2. Passerelle > **Supprimer**
   
   ![](media/service-gateway-enterprise-manage-sql/datasourcesettings7.png)

## <a name="add-a-data-source"></a>Ajouter une source de données
Pour ajouter une source de données, sélectionnez une passerelle, puis cliquez sur **Ajouter une source de données**, ou accédez à Passerelle > **Ajouter une source de données**.

![](media/service-gateway-enterprise-manage-sql/datasourcesettings1.png)

Vous pouvez ensuite sélectionner le **type de source de données** dans la liste.

![](media/service-gateway-enterprise-manage-sql/datasourcesettings2.png)

> [!NOTE]
> Lorsque vous utilisez DirectQuery, la passerelle prend en charge uniquement **SQL Server 2012 SP1** et versions ultérieures.
> 
> 

Vous devez ensuite renseigner les informations relatives à la source de données, notamment le **serveur** et la **base de données**.  

Vous devez également choisir une **méthode d’authentification**.  Ce peut être **Windows** ou **De base**.  Choisissez **De base** si vous comptez utiliser l’authentification SQL plutôt que l’authentification Windows. Entrez les informations d’identification qui seront utilisées pour cette source de données.

> [!NOTE]
> Toutes les requêtes adressées à la source de données utilisent ces informations d’identification, sauf si une authentification unique (SSO) Kerberos est configurée et activé pour la source de données. Avec l’authentification unique, les jeux de données d’importation utilisent les informations d’identification stockées, mais les jeux de données DirectQuery se servent de l’utilisateur Power BI actif pour exécuter les requêtes à l’aide de l’authentification unique. Pour plus d’informations, voir l’article sur passerelle de données locale principale expliquant comment les [informations d’identification](service-gateway-onprem.md#credentials) sont stockées, ou l’article décrivant comment [Utiliser Kerberos pour l’authentification unique (SSO) de Power BI à des sources de données locales](service-gateway-kerberos-for-sso-pbi-to-on-premises-data.md).
> 
> 

![](media/service-gateway-enterprise-manage-sql/datasourcesettings3.png)

Vous pouvez cliquer sur **Ajouter** après avoir renseigné toutes les informations.  Vous pouvez à présent utiliser cette source de données pour l’actualisation planifiée ou DirectQuery sur un serveur SQL Server local. L’indication *Connexion réussie* apparaît une fois la connexion établie.

![](media/service-gateway-enterprise-manage-sql/datasourcesettings4.png)

### <a name="advanced-settings"></a>Paramètres avancés
Vous pouvez configurer le niveau de confidentialité de votre source de données pour contrôler le mélange (« mashup ») des données. Cette option concerne uniquement l’actualisation planifiée ; elle ne s’applique pas à DirectQuery. [En savoir plus](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540)

![](media/service-gateway-enterprise-manage-sql/datasourcesettings9.png)

## <a name="remove-a-data-source"></a>Supprimez une source de données.
La suppression d’une source de données entraîne l’arrêt des éventuels tableaux de bord ou rapports qui reposent sur la source de données en question.  

Pour supprimer une source de données, accédez à Source de données > **Supprimer**.

![](media/service-gateway-enterprise-manage-sql/datasourcesettings6.png)

## <a name="manage-administrators"></a>Gérer les administrateurs
Sous l’onglet Administrateurs de la passerelle, vous pouvez ajouter et supprimer des utilisateurs (ou des groupes de sécurité) qui peuvent administrer la passerelle.

![](media/service-gateway-enterprise-manage-sql/datasourcesettings8.png)

## <a name="manage-users"></a>Gérer les utilisateurs
Sous l’onglet Utilisateurs, pour la source de données, vous pouvez ajouter et supprimer des utilisateurs ou des groupes de données qui peuvent utiliser cette passerelle.

> [!NOTE]
> La liste des utilisateurs contrôle uniquement les personnes autorisées à publier des rapports. Les propriétaires des rapports peuvent créer des tableaux de bord ou des packs de contenu et les partager avec d’autres utilisateurs.
> 
> 

![](media/service-gateway-enterprise-manage-sql/datasourcesettings5.png)

## <a name="using-the-data-source"></a>Utilisation de la source de données
Une fois la source de données créée, elle peut être utilisée avec des connexions DirectQuery ou via une actualisation planifiée.

> [!NOTE]
> Le nom du serveur et celui de la base de données doivent correspondre entre Power BI Desktop et la source de données dans la passerelle de données locale.
> 
> 

Le lien entre votre jeu de données et la source de données dans la passerelle est basé sur le nom de votre serveur et sur le nom de votre base de données. Ils doivent correspondre. Par exemple, si vous fournissez une adresse IP pour le nom du serveur, dans **Power BI Desktop**, vous devez utiliser l’adresse IP de la source de données dans la configuration de la passerelle. Si vous utilisez *SERVEUR\INSTANCE*, dans Power BI Desktop, vous devez utiliser la même valeur dans la source de données configurée pour la passerelle.

C’est le cas pour DirectQuery et pour l’actualisation planifiée.

### <a name="using-the-data-source-with-directquery-connections"></a>Utilisation de la source de données avec des connexions DirectQuery
Vous devez vérifier que le nom du serveur et celui de la base de données correspondent entre **Power BI Desktop** et la source de données configurée pour la passerelle. Vous devez également vérifier que votre utilisateur est répertorié sous l’onglet **Utilisateurs** de la source de données afin de publier des jeux de données DirectQuery. Pour DirectQuery, la sélection se produit dans Power BI Desktop la première fois que vous importez des données. [En savoir plus](desktop-use-directquery.md)

Une fois la publication effectuée, que ce soit à partir de Power BI Desktop ou de l’option **Obtenir les données**, vos rapports doivent commencer à fonctionner. Après la création de la source de données dans la passerelle, plusieurs minutes peuvent être nécessaires pour que la connexion puisse être utilisée.

### <a name="using-the-data-source-with-scheduled-refresh"></a>Utilisation de la source de données avec une actualisation planifiée
Si vous êtes répertorié sous l’onglet **Utilisateurs** de la source de données configurée dans la passerelle, et que le nom du serveur et celui de la base de données correspondent, la passerelle s’affiche comme option à utiliser avec l’actualisation planifiée.

![](media/service-gateway-enterprise-manage-sql/powerbi-gateway-enterprise-schedule-refresh.png)

## <a name="next-steps"></a>Étapes suivantes
* [Passerelle de données locale](service-gateway-onprem.md)  
* [Informations approfondies sur la passerelle de données locale](service-gateway-onprem-indepth.md)  
* [Résolution des problèmes de passerelle de données locale](service-gateway-onprem-tshoot.md)
* [Utiliser Kerberos pour l’authentification unique (SSO) de Power BI à des sources de données locales (préversion)](service-gateway-kerberos-for-sso-pbi-to-on-premises-data.md). 
* D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)

