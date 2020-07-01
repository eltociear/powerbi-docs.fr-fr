---
title: Informations approfondies sur la passerelle de données locale
description: Cet article apporte des informations approfondies sur la passerelle locale. Il examine le fonctionnement du service avec Azure Active Directory et votre annuaire Active Directory local lorsque vous utilisez Analysis Services
author: arthiriyer
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: how-to
ms.date: 07/15/2019
ms.author: arthii
LocalizationGroup: Gateways
ms.openlocfilehash: 34cf796db212112baa8083f5b4cbf1796b465cba
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85237566"
---
# <a name="on-premises-data-gateway-in-depth"></a>Informations approfondies sur la passerelle de données locale

[!INCLUDE [gateway-rewrite](../includes/gateway-rewrite.md)]

Nous avons déplacé les informations de cet article vers plusieurs autres articles dans des documents d’ordre général ou consacrés à Power BI. Suivez les liens sous chaque titre pour trouver le contenu approprié.

## <a name="how-the-gateway-works"></a>Fonctionnement de la passerelle

Consultez [Architecture de la passerelle de données locale](/data-integration/gateway/service-gateway-onprem-indepth).

## <a name="list-of-available-data-source-types"></a>Liste des types de sources de données disponibles

Consultez [Gérer les sources de données](service-gateway-data-sources.md).

## <a name="authentication-to-on-premises-data-sources"></a>Authentification auprès des sources de données locales

Consultez [Authentification auprès des sources de données locales](/data-integration/gateway/service-gateway-onprem-indepth#authentication-to-on-premises-data-sources).

## <a name="authentication-to-a-live-analysis-services-data-source"></a>Authentification auprès d’une source de données Analysis Services active

Consultez [Authentification auprès d’une source de données Analysis Services active](service-gateway-enterprise-manage-ssas.md#authentication-to-a-live-analysis-services-data-source).

## <a name="role-based-security"></a>Sécurité basée sur les rôles

Consultez [Sécurité basée sur les rôles](service-gateway-enterprise-manage-ssas.md#role-based-security).

## <a name="row-level-security"></a>Sécurité au niveau des lignes

Consultez [Sécurité au niveau des lignes](service-gateway-enterprise-manage-ssas.md#row-level-security).

## <a name="what-about-azure-active-directory"></a>Qu’en est-il d’Azure Active Directory ?

Consultez [Azure Active Directory](/data-integration/gateway/service-gateway-onprem-indepth#azure-active-directory).

## <a name="how-do-i-tell-what-my-upn-is"></a>Comment savoir quel est mon UPN ?

Consultez [Comment savoir quel est mon UPN ?](/data-integration/gateway/service-gateway-onprem-indepth#how-do-i-tell-what-my-upn-is).

## <a name="map-user-names-for-analysis-services-data-sources"></a>Mapper des noms d’utilisateurs pour les sources de données Analysis Services

Voir [Mapper des noms d’utilisateurs pour les sources de données Analysis Services](service-gateway-enterprise-manage-ssas.md#map-user-names-for-analysis-services-data-sources).

## <a name="synchronize-an-on-premises-active-directory-with-azure-active-directory"></a>Synchroniser un service Active Directory local avec Azure Active Directory

Consultez [Synchroniser un service Active Directory local avec Azure Active Directory](/data-integration/gateway/service-gateway-onprem-indepth#synchronize-an-on-premises-active-directory-with-azure-active-directory).

## <a name="what-to-do-next"></a>Que faire ensuite ?

Consultez les articles sur les sources de données :

[Gérer les sources de données](service-gateway-data-sources.md)
[Gérer votre source de données - Analysis Services](service-gateway-enterprise-manage-ssas.md)  
[Gérer votre source de données - SAP HANA](service-gateway-enterprise-manage-sap.md)  
[Gérer votre source de données - SQL Server](service-gateway-enterprise-manage-sql.md)  
[Gérer votre source de données - Oracle](service-gateway-onprem-manage-oracle.md)  
[Gérer votre source de données - Importation/actualisation planifiée](service-gateway-enterprise-manage-scheduled-refresh.md)  

## <a name="where-things-can-go-wrong"></a>Problèmes éventuels

Consultez [Résoudre les problèmes de passerelle de données locale](/data-integration/gateway/service-gateway-tshoot) et [Résoudre les problèmes des passerelles - Power BI](service-gateway-onprem-tshoot.md).

## <a name="sign-in-account"></a>Compte de connexion

Consultez [Compte de connexion](/data-integration/gateway/service-gateway-onprem-indepth#sign-in-account).

## <a name="windows-service-account"></a>Compte de service Windows

Consultez [Modifier le compte de service de la passerelle de données locale](/data-integration/gateway/service-gateway-service-account).

## <a name="ports"></a>Ports

Consultez [Ports](/data-integration/gateway/service-gateway-communication#ports).

## <a name="forcing-https-communication-with-azure-service-bus"></a>Forcer les communications HTTPS avec Azure Service Bus

Consultez [Forcer des communications HTTPS avec Azure Service Bus](/data-integration/gateway/service-gateway-communication#force-https-communication-with-azure-service-bus).

## <a name="support-for-tls-12"></a>Prise en charge de TLS 1.2

Consultez [TLS 1.2 pour le trafic d’une passerelle](/data-integration/gateway/service-gateway-communication#tls-12-for-gateway-traffic).

## <a name="how-to-restart-the-gateway"></a>Comment redémarrer la passerelle

Consultez [Redémarrer une passerelle](/data-integration/gateway/service-gateway-restart).

## <a name="next-steps"></a>Étapes suivantes

[Qu’est-ce que la passerelle de données locale ?](service-gateway-onprem.md)

D’autres questions ? [Posez vos questions à la communauté Power BI](https://community.powerbi.com/)