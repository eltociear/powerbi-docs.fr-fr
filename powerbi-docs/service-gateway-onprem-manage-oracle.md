---
title: Gérer votre source de données - Oracle
description: Gestion de la passerelle de données locale et des sources de données associées.
author: mgblythe
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: cb7856b0b5ac84684e8d0648b91e45805218cead
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73872456"
---
# <a name="manage-your-data-source---oracle"></a>Gérer votre source de données - Oracle

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Une fois que vous avez [installé la passerelle de données locale](/data-integration/gateway/service-gateway-install), vous devez [ajouter des sources de données](service-gateway-data-sources.md#add-a-data-source) qui peuvent être utilisées avec la passerelle. Cet article examine comment utiliser des passerelles et des sources de données Oracle pour l’actualisation planifiée ou pour DirectQuery.

## <a name="install-the-oracle-client"></a>Installer le client Oracle

Pour connecter la passerelle à votre serveur Oracle, vous devez installer et configurer Oracle Data Provider for .NET (ODP.NET). ODP.NET fait parti des composants d’accès aux données Oracle (ODAC, Oracle Data Access Components).

Pour les versions 32 bits de Power BI Desktop, utilisez le lien suivant pour télécharger et installer le client Oracle 32 bits :

* [Oracle Data Access Components (ODAC) 32 bits avec Oracle Developer Tools for Visual Studio (12.1.0.2.4)](https://www.oracle.com/technetwork/topics/dotnet/utilsoft-086879.html)

Pour les versions 64 bits de Power BI Desktop ou pour la passerelle de données locale, utilisez le lien suivant pour télécharger et installer le client Oracle 64 bits :

* [ODAC 12.2c Release 1 64 bits (12.2.0.1.0) pour Windows x64](https://www.oracle.com/technetwork/database/windows/downloads/index-090165.html)

Une fois le client installé, indiquez les informations de votre base de données dans votre fichier tnsnames.ora. Power BI Desktop et la passerelle se connectent au nom de service .NET (net_service_name) défini dans le fichier tnsnames.ora. Si le nom de service .NET (net_service_name) n’est pas configuré, vous ne pouvez pas vous connecter. `[Oracle Home Directory]\Network\Admin\tnsnames.ora` est le chemin par défaut du fichier tnsnames.ora. Pour plus d’informations sur la configuration des fichiers tnsnames.ora, consultez [Oracle: Local naming parameters (tnsnames.ora)](https://docs.oracle.com/cd/B28359_01/network.111/b28317/tnsnames.htm).

### <a name="example-tnsnamesora-file-entry"></a>Exemple d’entrée dans le fichier tnsnames.ora

Voici le format de base d’une entrée dans tnsname.ora :

```
net_service_name=
 (DESCRIPTION=
   (ADDRESS=(protocol_address_information))
   (CONNECT_DATA=
     (SERVICE_NAME=service_name)))
```

Voici un exemple qui montre de quelle manière les informations sur le serveur et le port sont indiquées :

```
CONTOSO =
  (DESCRIPTION =
    (ADDRESS = (PROTOCOL = TCP)(HOST = oracleserver.contoso.com)(PORT = 1521))
    (CONNECT_DATA =
      (SERVER = DEDICATED)
      (SERVICE_NAME = CONTOSO)
    )
  )
```

## <a name="add-a-data-source"></a>Ajouter une source de données

Pour plus d’informations sur la façon d’ajouter une source de données, voir [Ajouter une source de données](service-gateway-data-sources.md#add-a-data-source). Sous **Type de source de données**, sélectionnez **Oracle**.

![Ajouter la source de données Oracle](media/service-gateway-onprem-manage-oracle/data-source-oracle.png)

Après avoir sélectionné le type de source de données Oracle, renseignez les informations relatives à la source de données, notamment le **serveur** et la **base de données**. 

Sous **Méthode d’authentification**, vous pouvez choisir **Windows** ou **De base**. Choisissez **De base** si vous envisagez d’utiliser un compte créé dans Oracle plutôt que l’authentification Windows. Entrez les informations d’identification à utiliser pour cette source de données.

> [!NOTE]
> Toutes les requêtes à la source de données sont exécutées à l’aide de ces informations d’identification. Pour plus d’informations sur la façon dont les informations d’identification sont stockées, voir [Stocker des informations d’identification chiffrées dans le cloud](service-gateway-data-sources.md#store-encrypted-credentials-in-the-cloud).

![Spécification des paramètres de la source de données](media/service-gateway-onprem-manage-oracle/data-source-oracle2.png)

Une fois que vous avez renseigné toutes les valeurs,sélectionnez **Ajouter**. Vous pouvez désormais utiliser cette source de données pour l’actualisation planifiée ou DirectQuery sur un serveur Oracle local. L’indication *Connexion réussie* apparaît une fois la connexion établie.

![Affichage de l’état de la connexion](media/service-gateway-onprem-manage-oracle/datasourcesettings4.png)

### <a name="advanced-settings"></a>Paramètres avancés

Vous pouvez aussi configurer le niveau de confidentialité de votre source de données. Ce paramètre contrôle la façon dont les données peuvent être combinées. Il concerne uniquement l’actualisation planifiée. Le paramètre de niveau de confidentialité ne s’applique pas à DirectQuery. Pour plus d’informations sur les niveaux de confidentialité de votre source de données, consultez [Niveaux de confidentialité (Power Query)](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540).

![Définition du niveau de confidentialité](media/service-gateway-onprem-manage-oracle/datasourcesettings9.png)

## <a name="use-the-data-source"></a>Utiliser la source de données

Une fois la source de données créée, elle peut être utilisée avec des connexions DirectQuery ou via une actualisation planifiée.

> [!WARNING]
> Le nom du serveur et celui de la base de données doivent correspondre entre Power BI Desktop et la source de données dans la passerelle de données locale.

Le lien entre votre jeu de données et la source de données dans la passerelle est basé sur le nom de votre serveur et sur le nom de votre base de données. Ces noms doivent correspondre. Par exemple, si vous fournissez une adresse IP pour le nom du serveur dans Power BI Desktop, vous devez utiliser l’adresse IP de la source de données dans la configuration de la passerelle. Ce nom doit également correspondre à un alias défini dans le fichier tnsnames.ora. Pour plus d’informations sur le fichier tnsnames.ora, consultez [Installer le client Oracle](#install-the-oracle-client).

Cette exigence concerne DirectQuery et l’actualisation planifiée.

### <a name="use-the-data-source-with-directquery-connections"></a>Utiliser la source de données avec des connexions DirectQuery

Vérifiez que le nom du serveur et celui de la base de données correspondent entre Power BI Desktop et la source de données configurée pour la passerelle. Vous devez également vérifier que votre utilisateur est listé sous l’onglet **Utilisateurs** de la source de données pour qu’il puisse publier des jeux de données DirectQuery. Pour DirectQuery, la sélection se produit dans Power BI Desktop la première fois que vous importez des données. Pour plus d’informations sur la façon d’utiliser DirectQuery, consultez [Utiliser DirectQuery dans Power BI Desktop](desktop-use-directquery.md).

Une fois la publication effectuée, que ce soit à partir de Power BI Desktop ou de l’option **Obtenir les données**, vos rapports doivent commencer à fonctionner. Après la création de la source de données dans la passerelle, plusieurs minutes peuvent s’écouler avant que la connexion soit utilisable.

### <a name="use-the-data-source-with-scheduled-refresh"></a>Utiliser la source de données avec une actualisation planifiée

Si vous êtes listé sous l’onglet **Utilisateurs** de la source de données configurée dans la passerelle, et que le nom du serveur et celui de la base de données correspondent, la passerelle s’affiche comme option à utiliser avec l’actualisation planifiée.

![Affichage des utilisateurs](media/service-gateway-onprem-manage-oracle/powerbi-gateway-enterprise-schedule-refresh.png)

## <a name="troubleshooting"></a>Résolution des problèmes

Vous pouvez rencontrer plusieurs erreurs dans Oracle quand la syntaxe de dénomination est incorrecte ou n’est pas configurée correctement :

* ORA-12154: TNS:could not resolve the connect identifier specified. (ORA-12154 : TNS : l’identificateur de connexion indiqué n’a pas pu être résolu.)
* ORA-12514: TNS:listener does not currently know of service requested in connect descriptor. (ORA-12514 : le processus d’écoute ne connaît pas actuellement le service demandé dans le descripteur de connexion.)
* ORA-12541: TNS:no listener. (ORA-12541 : TNS : pas de processus d’écoute.)
* ORA-12170: TNS:connect timeout occurred. (ORA-12170 : TNS : une expiration de la connexion s’est produite.)
* ORA-12504: TNS:listener was not given the SERVICE_NAME in CONNECT_DATA. (ORA-12504 : le processus d’écoute n’a pas reçu SERVICE_NAME dans CONNECT_DATA.)

Ces erreurs peuvent se produire si le client Oracle n’est pas installé ou s’il n’est pas configuré correctement. S’il est installé, vérifiez que le fichier tnsnames.ora est correctement configuré et que vous utilisez le bon nom de service .NET (net_service_name). Vous devez également vérifier que le net_service_name est le même sur l’ordinateur utilisant Power BI Desktop et sur l’ordinateur qui exécute la passerelle. Pour plus d’informations, consultez [Installer le client Oracle](#install-the-oracle-client).

> [!NOTE]
> Vous pouvez également rencontrer un problème de compatibilité entre la version du serveur Oracle et la version du client Oracle. En règle générale, vous souhaitez que ces versions correspondent.

Pour plus d’informations sur le dépannage de la passerelle, consultez [Résolution des problèmes de passerelle de données locale](/data-integration/gateway/service-gateway-tshoot).

## <a name="next-steps"></a>Étapes suivantes

* [Résoudre les problèmes liés aux passerelles - Power BI](service-gateway-onprem-tshoot.md)
* [Power BI Premium](service-premium.md)

D’autres questions ? Essayez de d’interroger la [Communauté Power BI](https://community.powerbi.com/).

