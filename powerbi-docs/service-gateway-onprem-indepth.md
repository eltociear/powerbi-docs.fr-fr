---
title: "Informations approfondies sur la passerelle de données locale"
description: Cet article apporte des informations approfondies sur la passerelle locale. Il examine le fonctionnement du service avec Azure Active Directory et votre annuaire Active Directory local lorsque vous utilisez Analysis Services
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
ms.date: 09/06/2017
ms.author: davidi
ms.openlocfilehash: c030f1b18b654be6bba6a7bf2d10af322567c4d1
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2017
---
# <a name="on-premises-data-gateway-in-depth"></a>Informations approfondies sur la passerelle de données locale
Les utilisateurs de votre organisation peuvent accéder aux données locales (auxquelles ils ont déjà accès), mais avant qu’ils puissent se connecter à votre source de données locale, vous devez installer et configurer une passerelle de données locale. La passerelle favorise une communication rapide et sécurisée en arrière-plan entre un utilisateur dans le cloud et votre source de données locale, dans les deux sens.

La passerelle est généralement installée et configurée par un administrateur. Ces opérations peuvent nécessiter une connaissance approfondie de vos serveurs locaux et, dans certains cas, l’autorisation de l’administrateur du serveur peut être nécessaire.

Cet article ne fournit pas d’instructions détaillées quant à l’installation et la configuration de la passerelle. Pour obtenir des informations à ce sujet, consultez [Passerelle de données locale](service-gateway-onprem.md). Cet article a pour objectif d’expliquer en détail le fonctionnement de la passerelle. Il aborde également en détail les noms d’utilisateur et la sécurité dans Azure Active Directory et Analysis Services. Vous découvrirez comment le service cloud utilise l’adresse de messagerie avec laquelle un utilisateur se connecte, la passerelle et Active Directory pour se connecter en toute sécurité à vos données locales et exécuter des requêtes.

<!-- Shared Requirements Include -->
[!INCLUDE [gateway-onprem-requirements-include](./includes/gateway-onprem-how-it-works-include.md)]

<!-- Shared Install steps Include -->
[!INCLUDE [gateway-onprem-datasources-include](./includes/gateway-onprem-datasources-include.md)]

## <a name="sign-in-account"></a>Compte de connexion
Les utilisateurs doivent se connecter en utilisant un compte professionnel ou scolaire. Il s’agit du compte de votre organisation. Si vous avez souscrit une offre Office 365 et que vous n’avez pas fourni votre adresse de messagerie professionnelle, il peut ressembler à nancy@contoso.onmicrosoft.com. Votre compte, au sein d’un service cloud, est stocké dans un locataire, dans Azure Active Directory (AAD). Généralement, le nom d’utilisateur principal (ou UPN) de votre compte AAD correspond à votre adresse de messagerie.

## <a name="authentication-to-on-premises-data-sources"></a>Authentification auprès des sources de données locales
Les informations d’identification stockées sont utilisées pour la connexion aux sources de données locales à partir de la passerelle, à l’exception d’Analysis Services. Quel que soit l’utilisateur concerné, la passerelle utilise les informations d’identification stockées pour se connecter.

## <a name="authentication-to-a-live-analysis-services-data-source"></a>Authentification auprès d’une source de données Analysis Services active
Chaque fois qu’un utilisateur interagit avec Analysis Services, le nom de l’utilisateur en vigueur est transmis à la passerelle, puis à votre serveur Analysis Services local. Le nom d’utilisateur principal, qui est généralement l’adresse de messagerie utilisée pour la connexion au cloud, est celui que nous transmettons à Analysis Services en tant qu’utilisateur en vigueur. Le nom d’utilisateur principal est transmis dans la propriété de connexion EffectiveUserName. Cette adresse de messagerie doit correspondre à un nom d’utilisateur principal défini dans le domaine Active Directory local. L’UPN est une propriété de compte Active Directory. Pour avoir accès au serveur, ce compte Windows doit se trouver dans un rôle Analysis Services. La connexion échoue s’il n’existe aucune correspondance dans Active Directory.

Analysis Services peut également fournir un filtrage basé sur ce compte. Le filtrage peut se produire avec la sécurité basée sur les rôles ou au niveau des lignes.

## <a name="role-based-security"></a>Sécurité basée sur les rôles
Les modèles fournissent une solution de sécurité basée sur les rôles d’utilisateur. Les rôles sont définis pour un projet de modèle spécifique pendant la procédure de création dans SQL Server Data Tools - Business Intelligence (SSDT-BI) ou après le déploiement d’un modèle, à l’aide de SQL Server Management Studio (SSMS). Les rôles contiennent des membres définis par leurs noms d’utilisateur Windows ou par leur groupe Windows. Les rôles définissent les autorisations dont dispose un utilisateur pour interroger le modèle ou effectuer des actions sur ce dernier. La plupart des utilisateurs appartiennent à un rôle doté d’autorisations de lecture. Les autres rôles sont destinés aux administrateurs qui possèdent des autorisations pour traiter les éléments, gérer les fonctions de base de données et gérer les autres rôles.

## <a name="row-level-security"></a>Sécurité au niveau des lignes
La sécurité au niveau des lignes est propre à Analysis Services. Les modèles peuvent proposer une solution de sécurité dynamique au niveau des lignes. Contrairement au cas où les utilisateurs appartiennent à au moins un rôle, la sécurité dynamique est inutile pour tout modèle tabulaire. À un haut niveau, la sécurité dynamique définit l’accès en lecture d’un utilisateur à des données directement au niveau d’une ligne particulière dans une table donnée. Similaire aux rôles, la sécurité dynamique au niveau des lignes s’appuie sur le nom d’utilisateur Windows d’un utilisateur.

L’aptitude d’un utilisateur à interroger et à afficher les données de modèle est déterminée en premier lieu par les rôles dont son compte utilisateur Windows est membre et en second lieu par la sécurité dynamique au niveau des lignes, si elle est configurée.

La mise en œuvre d’une sécurité basée sur les rôles et dynamique au niveau des lignes dans les modèles dépasse le cadre de cet article.  Pour en savoir plus, consultez les rubriques [Rôles (SSAS Tabulaire)](https://msdn.microsoft.com/library/hh213165.aspx) et [Rôles de sécurité (Analysis Services - Données multidimensionnelles)](https://msdn.microsoft.com/library/ms174840.aspx) sur MSDN. En outre, pour approfondir au maximum votre compréhension de la sécurité des modèles tabulaires, téléchargez et lisez le livre blanc [Securing the Tabular BI Semantic Model](https://msdn.microsoft.com/library/jj127437.aspx).

## <a name="what-about-azure-active-directory"></a>Qu’en est-il d’Azure Active Directory ?
Les services cloud Microsoft utilisent [Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-whatis/) pour prendre en charge l’authentification des utilisateurs. Azure Active Directory est le locataire qui contient les groupes de sécurité et les noms d’utilisateur. En règle générale, un utilisateur se connecte avec l’adresse de messagerie qui correspond au nom d’utilisateur principal du compte.

Qu’est-ce qu’un rôle Active Directory local ?

Pour qu’Analysis Services puisse déterminer si un utilisateur se connectant à ce dernier appartient à un rôle doté d’autorisations de lecture des données, le serveur doit convertir le nom d’utilisateur en vigueur transmis depuis AAD à la passerelle, puis au serveur Analysis Services. Le serveur Analysis Services passe le nom d’utilisateur en vigueur à un contrôleur de domaine Active Directory. Ensuite, le contrôleur de domaine Active Directory confirme que le nom d’utilisateur en vigueur correspond à un UPN valide sur un compte local et renvoie le nom d’utilisateur Windows de cet utilisateur au serveur Analysis Services.

Le nom d’utilisateur en vigueur ne peut pas être utilisé sur un serveur Analysis Services non joint au domaine. Le serveur Analysis Services doit être joint à un domaine pour éviter les erreurs de connexion.

## <a name="how-do-i-tell-what-my-upn-is"></a>Comment savoir quel est mon UPN ?
Vous ne savez pas peut-être pas quel est votre UPN, et vous n’êtes peut-être pas un administrateur de domaine. Vous pouvez utiliser la commande suivante à partir de votre station de travail pour connaître l’UPN de votre compte.

    whoami /upn

Le résultat ressemblera à une adresse de messagerie, mais il s’agit de l’UPN qui se trouve sur votre compte de domaine local. Si vous utilisez une source de données Analysis Services pour les connexions actives, celle-ci doit correspondre à ce qui a été transmis à la propriété EffectiveUserName à partir de la passerelle.

## <a name="mapping-usernames-for-analysis-services-data-sources"></a>Mappage des noms d’utilisateurs pour les sources de données Analysis Services
Power BI autorise le mappage des noms d’utilisateurs pour les sources de données Analysis Services. Vous pouvez configurer des règles pour mapper un nom d’utilisateur connecté avec Power BI au nom qui a été transmis comme nom d’utilisateur en vigueur sur la connexion Analysis Services. La fonctionnalité de mappage des noms d’utilisateurs est un excellent moyen de contournement quand votre nom d’utilisateur AAD ne correspond pas à un nom d’utilisateur principal (UPN) de votre annuaire Active Directory local. Par exemple, si votre adresse e-mail est nancy@contoso.onmicrsoft.com, vous pouvez la mapper à nancy@contoso.com. Cette valeur est ensuite transmise à la passerelle. Pour en savoir plus sur le mappage des noms d’utilisateur, [cliquez ici](service-gateway-enterprise-manage-ssas.md#map-user-names).

## <a name="synchronize-an-on-premises-active-directory-with-azure-active-directory"></a>Synchroniser un service Active Directory local avec Azure Active Directory
Vous voulez que vos comptes Active Directory locaux correspondent à Azure Active Directory si vous vous apprêtez à utiliser des connexions actives Analysis Services. De même, l’UPN doit être identique pour tous les comptes.

Les services cloud reconnaissent uniquement les comptes dans Azure Active Directory. Même si vous avez ajouté un compte dans votre annuaire Active Directory local, s’il n’existe pas dans AAD, il ne peut pas être utilisé. Il existe différentes méthodes pour faire correspondre vos comptes Active Directory locaux avec Azure Active Directory.

1. Vous pouvez ajouter manuellement des comptes à Azure Active Directory.
   
   Vous pouvez créer un compte sur le portail Azure ou dans le portail d’administration Office 365. Le nom du compte correspond alors au nom d’utilisateur principal du compte Active Directory local.
2. Vous pouvez utiliser l’outil [Azure AD Connect](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect/) pour synchroniser les comptes locaux avec votre locataire Azure Active Directory.
   
   L’outil Azure AD Connect fournit des options de synchronisation des annuaires et des mots de passe. Si vous n’êtes pas un administrateur de locataire ou un administrateur de domaine local, vous devez contacter votre administrateur pour qu’il se charge de la configuration.
3. Vous pouvez configurer Active Directory Federation Services (ADFS).
   
   Vous pouvez associer votre serveur AD FS à votre locataire AAD avec l’outil [Azure AD Connect](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect/). ADFS utilise la synchronisation d’annuaires évoquée ci-dessus et autorise également l’authentification unique. Par exemple, si vous êtes dans le réseau de votre entreprise, quand vous vous connectez à un service cloud, il se peut que vous ne soyez pas invité à entrer un nom d’utilisateur ou un mot de passe. Vous devez voir avec votre administrateur si cette option est disponible pour votre organisation.

L’utilisation d’Azure AD Connect permet de vérifier que les UPN d’AAD et de votre annuaire Active Directory local correspondent.

> [!NOTE]
> La synchronisation des comptes avec l’outil Azure AD Connect crée des comptes au sein de votre client AAD.
> 
> 

## <a name="now-this-is-where-the-gateway-comes-in"></a>C’est là que la passerelle entre en scène.
La passerelle fait office de pont entre le cloud et votre serveur local. Le transfert de données entre le cloud et la passerelle est sécurisé au moyen d’[Azure Service Bus](https://azure.microsoft.com/documentation/services/service-bus/). Service Bus crée un canal sécurisé entre le cloud et votre serveur local via une connexion sortante sur la passerelle.  Vous n’avez pas besoin d’ouvrir une connexion entrante sur votre pare-feu local.

Si vous avez une source de données Analysis Services, vous devez installer la passerelle sur un ordinateur associé à la même forêt ou au même domaine que votre serveur Analysis Services.

Plus la passerelle est proche du serveur, plus la connexion est rapide. L’idéal, pour éviter toute latence du réseau entre la passerelle et le serveur, est d’utiliser la passerelle sur le même serveur que la source de données.

## <a name="what-to-do-next"></a>Que faire ensuite ?
Une fois que vous avez installé la passerelle, vous devez créer les sources de données associées. Vous pouvez ajouter des sources de données dans l’écran **Gérer les passerelles**. Pour plus d’informations, consultez les articles sur la gestion des sources de données.

[Gérer votre source de données - Analysis Services](service-gateway-enterprise-manage-ssas.md)  
[Gérer votre source de données - SAP HANA](service-gateway-enterprise-manage-sap.md)  
[Gérer votre source de données - SQL Server](service-gateway-enterprise-manage-sql.md)  
[Gérer votre source de données - Oracle](service-gateway-onprem-manage-oracle.md)  
[Gérer votre source de données - Importation/actualisation planifiée](service-gateway-enterprise-manage-scheduled-refresh.md)  

## <a name="where-things-can-go-wrong"></a>Problèmes éventuels
Parfois, l’installation de la passerelle échoue. Ou bien la passerelle semble être installée correctement, mais le service ne parvient pas à l’utiliser. Dans de nombreux cas, le problème est simple. Par exemple : une erreur de mot de passe pour les informations d’identification utilisées par la passerelle pour se connecter à la source de données.

Dans d’autres cas, il peut s’agir d’un problème au niveau du type d’adresse de messagerie avec laquelle l’utilisateur se connecte ou encore l’incapacité d’Analysis Services à résoudre un nom d’utilisateur effectif. Si vous possédez plusieurs domaines liés par des approbations et que votre passerelle figure dans l’un d’eux alors qu’Analysis Services figure dans un autre, cela entraîne parfois des problèmes.

Nous n’expliquerons pas ici comment résoudre les problèmes liés à la passerelle. Pour cela, consultez l’article [Dépannage de la passerelle de données locale](service-gateway-onprem-tshoot.md) qui contient une série de procédures de dépannage. Vous ne rencontrerez probablement aucun problème. Mais dans le cas contraire, la compréhension du fonctionnement des différents éléments et l’article de résolution des problèmes devraient vous aider.

<!-- Account and Port information -->
[!INCLUDE [gateway-onprem-accounts-ports-more](./includes/gateway-onprem-accounts-ports-more.md)]

## <a name="next-steps"></a>Étapes suivantes
[Résolution des problèmes de passerelle de données locale](service-gateway-onprem-tshoot.md)  
[Azure Service Bus](https://azure.microsoft.com/documentation/services/service-bus/)  
[Azure AD Connect](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect/)  
D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)

