---
title: Utiliser des connecteurs de données personnalisés avec la passerelle de données locale
description: Vous pouvez utiliser des connecteurs de données personnalisés avec la passerelle de données locale.
author: mgblythe
ms.author: mblythe
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
LocalizationGroup: Gateways
ms.openlocfilehash: c76c8fdb635db7724ffeb1a5140e9095c9b2eff5
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73881741"
---
# <a name="use-custom-data-connectors-with-the-on-premises-data-gateway"></a>Utiliser des connecteurs de données personnalisés avec la passerelle de données locale

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Avec les connecteurs de données pour Power BI, vous pouvez vous connecter et accéder à des données provenant d’une application, d’un service ou d’une source de données. Vous pouvez développer des connecteurs de données personnalisés et les utiliser dans Power BI Desktop.

Pour plus d’informations sur le développement de connecteurs de données personnalisés pour Power BI, consultez la [page Data Connector SDK de GitHub](https://aka.ms/dataconnectors). Ce site comprend des informations pour démarrer et des exemples pour Power BI et Power Query.

Quand vous créez des rapports dans Power BI Desktop qui utilisent des connecteurs de données personnalisés, vous pouvez utiliser la passerelle de données locale pour actualiser ces rapports à partir du service Power BI.

## <a name="enable-and-use-this-capability"></a>Activer et utiliser cette fonctionnalité

Quand vous installez la version de juillet 2018 ou ultérieure de la passerelle de données locale, vous voyez un onglet **Connecteurs** dans l’application de passerelle de données locale. Dans la zone **Charger les connecteurs de données personnalisés à partir du dossier**, sélectionnez un dossier accessible par l’utilisateur qui exécute le service de passerelle. L’utilisateur par défaut est *NT SERVICE\PBIEgwService*. La passerelle charge automatiquement les fichiers de connecteurs personnalisés situés dans ce dossier. Ils s’affichent dans la liste des connecteurs de données.

![Connecteurs de données personnalisés](media/service-gateway-custom-connectors/gateway-onprem-customconnector1.png)

Si vous utilisez la passerelle de données locale (mode personnel), vous pouvez charger votre rapport Power BI sur le service Power BI et utiliser la passerelle pour l’actualiser.

Pour la passerelle de données locale, vous devez créer une source de données pour votre connecteur personnalisé. Dans la page des paramètres de la passerelle dans le service Power BI, vous devez voir une option quand vous sélectionnez le cluster de passerelle pour permettre l’utilisation de connecteurs personnalisés avec ce cluster. Vérifiez que toutes les passerelles du cluster ont la version correspondant à la mise à jour de juillet 2018 ou une version ultérieure pour que cette option soit disponible. Sélectionnez cette option pour permettre l’utilisation de connecteurs personnalisés avec ce cluster.

![Page Paramètres du cluster de passerelle](media/service-gateway-custom-connectors/gateway-onprem-customconnector2.png)

Quand cette option est activée, vous voyez vos connecteurs personnalisés en tant que sources de données disponibles, que vous pouvez créer dans ce cluster de passerelle. Après avoir créé une source de données qui utilise votre nouveau connecteur personnalisé, vous pouvez actualiser des rapports Power BI en utilisant ce connecteur personnalisé dans le service Power BI.

![Page Paramètres de la source de données](media/service-gateway-custom-connectors/gateway-onprem-customconnector3.png)

## <a name="considerations-and-limitations"></a>Considérations et limitations

* Vérifiez que le dossier que vous créez est accessible par le service de passerelle d’arrière-plan. En règle générale, les dossiers sous le dossier Windows ou sous les dossiers système de l’utilisateur ne sont pas accessibles. L’application de passerelle de données locale affiche un message si le dossier n’est pas accessible. Cette instruction ne concerne pas la passerelle de données locale (mode personnel).
* Pour que les connecteurs personnalisés fonctionnent avec la passerelle de données locale, ils doivent implémenter une section « TestConnection » dans leur code. Cette section n’est pas obligatoire quand vous utilisez des connecteurs personnalisés avec Power BI Desktop. Pour cette raison, vous pouvez avoir un connecteur qui fonctionne avec Power BI Desktop, mais pas avec la passerelle. Pour plus d’informations sur l’implémentation d’une section TestConnection, consultez [cette documentation](https://github.com/Microsoft/DataConnectors/blob/master/docs/m-extensions.md#implementing-testconnection-for-gateway-support).

## <a name="next-steps"></a>Étapes suivantes

* [Gérer votre source de données - Analysis Services](service-gateway-enterprise-manage-ssas.md)  
* [Gérer votre source de données - SAP HANA](service-gateway-enterprise-manage-sap.md)  
* [Gérer votre source de données - SQL Server](service-gateway-enterprise-manage-sql.md)  
* [Gérer votre source de données - Oracle](service-gateway-onprem-manage-oracle.md)  
* [Gérer votre source de données – Importation/actualisation planifiée](service-gateway-enterprise-manage-scheduled-refresh.md)
* [Configurer les paramètres de proxy de la passerelle de données locale](/data-integration/gateway/service-gateway-proxy)
* [Utiliser Kerberos pour l’authentification unique (SSO) de Power BI à des sources de données locales](service-gateway-sso-kerberos.md)  

D’autres questions ? Essayez de d’interroger la [Communauté Power BI](https://community.powerbi.com/).
