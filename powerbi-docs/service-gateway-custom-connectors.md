---
title: Utiliser des connecteurs de données personnalisés avec la passerelle de données locale
description: Vous pouvez utiliser des connecteurs de données personnalisés avec la passerelle de données locale.
author: mgblythe
ms.author: mblyth
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-gateways
ms.topic: conceptual
ms.date: 08/08/2018
LocalizationGroup: Gateways
ms.openlocfilehash: 8230a1df7db7758c34bf45c5a33e991ddf08dde5
ms.sourcegitcommit: cce10e14c111e8a19f282ad6c032d802ebfec943
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39713068"
---
# <a name="use-custom-data-connectors-with-the-on-premises-data-gateway"></a>Utiliser des connecteurs de données personnalisés avec la passerelle de données locale

Les connecteurs de données pour Power BI vous permettent de vous connecter et d’accéder à des données provenant d’une application, d’un service ou d’une source de données. Vous pouvez développer des connecteurs de données personnalisés et les utiliser dans Power BI Desktop.

Pour plus d’informations sur le développement de connecteurs de données personnalisés pour Power BI, consultez notre documentation [ici](http://aka.ms/dataconnectors).

Quand vous créez des rapports dans Power BI Desktop qui utilisent des connecteurs de données personnalisés, vous pouvez utiliser la passerelle de données locale pour actualiser les rapports à partir du service Power BI.

## <a name="here-is-a-guide-on-how-to-enable-and-use-this-capability"></a>Voici un guide sur la façon d’activer et d’utiliser cette fonctionnalité.

Quand vous installez la version de juillet 2018 ou ultérieure de la passerelle de données locale, vous pouvez voir un onglet « Connecteurs » dans l’outil de configuration avec une option pour choisir un dossier à partir duquel charger les connecteurs personnalisés. Veillez à sélectionner un dossier accessible à l’utilisateur qui exécute le service de passerelle (qui est par défaut « NT SERVICE\PBIEgwService »). La passerelle charge automatiquement les fichiers des connecteurs personnalisés qui se trouvent dans ce dossier, et vous devez normalement les voir dans la liste des connecteurs de données.

![Connecteur personnalisé 1](media/service-gateway-custom-connectors/gateway-onprem-customconnector1.png)

Si vous utilisez la version personnelle de la passerelle de données locale, vous devez pouvoir à ce stade charger votre rapport Power BI dans le service Power BI et utiliser la passerelle pour l’actualiser.

Pour la version entreprise de la passerelle, vous devez toujours créer une source de données pour votre connecteur personnalisé. Dans la page des paramètres de la passerelle dans le service Power BI, vous devez voir une nouvelle option quand vous sélectionnez le cluster de passerelle pour permettre l’utilisation de connecteurs personnalisés avec ce cluster. Vérifiez que toutes les passerelles du cluster ont la version correspondant à la mise à jour de juillet 2018 ou une version ultérieure pour que cette option soit disponible. Sélectionnez maintenant cette option pour permettre l’utilisation de connecteurs personnalisés avec ce cluster.

![Connecteur personnalisé 2](media/service-gateway-custom-connectors/gateway-onprem-customconnector2.png)

Quand cette option est activée, vous voyez vos connecteurs personnalisés en tant que sources de données disponibles, que vous pouvez créer dans ce cluster de passerelle. Après avoir créé une source de données en utilisant votre nouveau connecteur personnalisé, vous pouvez actualiser des rapports Power BI en utilisant ce connecteur personnalisé dans le service Power BI.

![Connecteur personnalisé 3](media/service-gateway-custom-connectors/gateway-onprem-customconnector3.png)

## <a name="considerations-and-limitations"></a>Considérations et limitations

* Vérifiez que le dossier que vous créez est accessible par le service de passerelle d’arrière-plan. En règle générale, les dossiers sous le dossier Windows ou sous les dossiers système de l’utilisateur ne sont pas accessibles. L’outil de configuration de passerelle affiche un message si le dossier n’est pas accessible (ceci ne s’applique pas pour la version personnelle de la passerelle)
* Pour que les connecteurs personnalisés fonctionnent avec la passerelle de données locale, ils doivent implémenter une section « TestConnection » dans leur code. Ce n’est pas nécessaire lors de l’utilisation de connecteurs personnalisés avec Power BI Desktop. Vous pouvez en avoir un qui fonctionne avec la version Desktop, mais pas avec la passerelle pour cette raison. Reportez-vous à [cette documentation](https://github.com/Microsoft/DataConnectors/blob/master/docs/m-extensions.md#implementing-testconnection-for-gateway-support) pour savoir comment implémenter une section TestConnection.
* Les connecteurs personnalisés avec l’authentification OAuth ne sont pas pris en charge.
* Les connecteurs personnalisés utilisant DirectQuery ne sont pas pris en charge.

## <a name="next-steps"></a>Étapes suivantes

* [Gérer votre source de données - Analysis Services](service-gateway-enterprise-manage-ssas.md)  
* [Gérer votre source de données - SAP HANA](service-gateway-enterprise-manage-sap.md)  
* [Gérer votre source de données - SQL Server](service-gateway-enterprise-manage-sql.md)  
* [Gérer votre source de données - Oracle](service-gateway-onprem-manage-oracle.md)  
* [Gérer votre source de données - Importation/actualisation planifiée](service-gateway-enterprise-manage-scheduled-refresh.md)  
* [Informations approfondies sur la passerelle de données locale](service-gateway-onprem-indepth.md)  
* [Passerelle de données locale (mode personnel)](service-gateway-personal-mode.md)
* [Configuration des paramètres de proxy de la passerelle de données locale](service-gateway-proxy.md)  
* [Utiliser Kerberos pour l’authentification unique (SSO) de Power BI à des sources de données locales](service-gateway-kerberos-for-sso-pbi-to-on-premises-data.md)  

D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)
