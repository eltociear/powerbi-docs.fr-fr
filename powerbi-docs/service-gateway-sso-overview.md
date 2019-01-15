---
title: Utiliser l’authentification unique (SSO) sur des sources de données locales
description: Configurez votre passerelle pour appliquer l’authentification unique (SSO) de Power BI sur des sources de données locales.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 10/15/2018
LocalizationGroup: Gateways
ms.openlocfilehash: bfd40c991f461e57f2f1d2de8a46b3627aa7fbc1
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/15/2019
ms.locfileid: "54274211"
---
# <a name="overview-of-single-sign-on-sso-for-gateways-in-power-bi"></a>Vue d’ensemble de l’authentification unique (SSO) pour les passerelles dans Power BI

Vous pouvez vous connecter de façon fluide avec une authentification unique, qui permet la mise à jour des rapports et tableaux de bord Power BI à partir de données locales, en configurant votre passerelle de données locale avec Kerberos, une délégation contrainte ou SAML (Security Assertion Markup Language). La passerelle de données locale facilite l’authentification unique à l’aide de DirectQuery, qu’elle utilise pour se connecter à des sources de données locales.

Nous prenons en charge les sources de données suivantes :

* SQL Server ([Kerberos](service-gateway-sso-kerberos.md))
* SAP HANA ([Kerberos](service-gateway-sso-kerberos.md) et [SAML](service-gateway-sso-saml.md))
* SAP BW ([Kerberos](service-gateway-sso-kerberos.md)
* Teradata ([Kerberos](service-gateway-sso-kerberos.md))
* Spark ([Kerberos](service-gateway-sso-kerberos.md))
* Impala ([Kerberos](service-gateway-sso-kerberos.md))

Quand un utilisateur interagit avec un rapport DirectQuery dans le service Power BI, chaque opération de filtrage croisé, de découpage, de tri et de modification de rapport peut entraîner des requêtes en direct sur la source de données locale sous-jacente.  Quand l’authentification unique est configurée pour la source de données, les requêtes s’exécutent sous l’identité de l’utilisateur interagissant avec Power BI via l’expérience web ou des applications mobiles Power BI. Ainsi, chaque utilisateur voit précisément les données qu’il est autorisé à consulter dans la source de données sous-jacente. Quand l’authentification unique est configurée, il n’y a pas de mise en cache de données partagées entre les différents utilisateurs.

## <a name="query-steps-when-running-sso"></a>Étapes d’une requête durant l’exécution de l’authentification unique

Une requête exécutée avec une authentification unique comprend trois étapes, comme illustré dans le diagramme suivant.

![Étapes d’une requête durant l’exécution de l’authentification unique](media/service-gateway-sso-overview/sso-query-steps.png)

> [!NOTE]
> L’authentification unique (SSO) pour Oracle n’est pas encore activée, mais elle est en cours de développement et sera disponible bientôt.

Des détails supplémentaires concernant ces étapes figurent ci-dessous :

1. Pour chaque requête, le **service Power BI** inclut le *nom d’utilisateur principal* (UPN) lors de l’envoi d’une demande de requête à la passerelle configurée.

2. La passerelle doit mapper l’UPN Active Directory Azure à une identité Active Directory locale.

   a.  Si Azure AD DirSync (également appelé *Azure AD Connect*) est configuré, le mappage fonctionne automatiquement dans la passerelle.

   b.  Autrement, la passerelle peut rechercher et mapper l’UPN AD Azure à un utilisateur local en effectuant une recherche dans le domaine Active Directory local.

3. Le processus du service de passerelle emprunte l’identité de l’utilisateur local mappé, ouvre la connexion à la base de données sous-jacente, et envoie la requête. Il n’est pas nécessaire d’installer la passerelle sur la même machine que la base de données.

## <a name="next-steps"></a>Étapes suivantes

Les principes fondamentaux de l’authentification unique n’ayant plus de secret pour vous, vous pouvez approfondir vos connaissances sur Kerberos et SAML :

* [Authentification unique (SSO) - Kerberos](service-gateway-sso-kerberos.md)
* [Authentification unique (SSO) - SAML](service-gateway-sso-saml.md)
