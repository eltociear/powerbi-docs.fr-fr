---
title: Utiliser Kerberos pour l’authentification unique avec SAP HANA
description: Configurer votre serveur SAP HANA pour activer l’authentification unique à partir du service Power BI
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 08/01/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 9e7bdb0ae2f1e512e3e431cf69395d601cbc7b3f
ms.sourcegitcommit: 9bf3cdcf5d8b8dd12aa1339b8910fcbc40f4cbe4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2019
ms.locfileid: "71968525"
---
# <a name="use-kerberos-for-single-sign-on-sso-to-sap-hana"></a>Utiliser Kerberos pour l’authentification unique avec SAP HANA

Cet article explique comment configurer votre source de données SAP HANA pour activer l’authentification unique à partir du service Power BI.

> [!NOTE]
> Suivez les étapes décrites dans cet article en plus des étapes décrites [Configurer l’authentification unique Kerberos](service-gateway-sso-kerberos.md) avant d’essayer d’actualiser un rapport basé sur SAP HANA qui utilise l’authentification unique Kerberos.

## <a name="enable-sso-for-sap-hana"></a>Activer l’authentification unique pour SAP HANA

Pour activer l’authentification unique pour SAP HANA, suivez ces étapes :

* Vérifiez que le serveur SAP HANA exécute la version minimale requise, qui dépend du niveau de la plateforme de votre serveur SAP HANA :
  * [HANA 2 SPS 01 Rev 012.03](https://launchpad.support.sap.com/#/notes/2557386)
  * [HANA 2 SPS 02 Rev 22](https://launchpad.support.sap.com/#/notes/2547324)
  * [HANA 1 SP 12 Rev 122.13](https://launchpad.support.sap.com/#/notes/2528439)
* Sur l’ordinateur de la passerelle, installez le pilote ODBC HANA SAP le plus récent.  La version minimale est HANA ODBC 2.00.020.00 datant d’août 2017.

Assurez-vous que le serveur SAP HANA a été configuré pour l’authentification unique basée sur Kerberos. Pour plus d’informations sur la configuration de l’authentification unique pour SAP HANA à l’aide de Kerberos, consultez [Single Sign-on Using Kerberos](https://help.sap.com/viewer/b3ee5778bc2e4a089d3299b82ec762a7/2.0.03/1885fad82df943c2a1974f5da0eed66d.html) dans le Guide de sécurité SAP HANA. Consultez également les liens de cette page, notamment SAP Note 1837331 – HOWTO HANA DBSSO Kerberos/Active Directory.

Nous vous recommandons également de suivre les étapes supplémentaires ci-après, qui peuvent améliorer les performances légèrement.

1. Dans le répertoire d’installation de la passerelle, recherchez et ouvrez ce fichier de configuration : *Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config*.

2. Recherchez la propriété *FullDomainResolutionEnabled* et définissez sa valeur sur *True*.

    ```xml
    <setting name=" FullDomainResolutionEnabled " serializeAs="String">
          <value>True</value>
    </setting>
    ```

Maintenant, [générez un rapport Power BI](service-gateway-sso-kerberos.md#run-a-power-bi-report).

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur la **Passerelle de données locale** et **DirectQuery**, consultez les ressources suivantes :

* [Qu’est-ce qu’une passerelle de données locale ?](/data-integration/gateway/service-gateway-getting-started)
* [DirectQuery dans Power BI](desktop-directquery-about.md)
* [Sources de données prises en charge par DirectQuery](desktop-directquery-data-sources.md)
* [DirectQuery et SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery et SAP HANA](desktop-directquery-sap-hana.md)
