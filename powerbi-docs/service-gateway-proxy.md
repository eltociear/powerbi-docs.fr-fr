---
title: Configuration des paramètres de proxy de la passerelle de données locale
description: Informations sur la configuration des paramètres de proxy pour la passerelle de données locale.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-gateways
ms.topic: conceptual
ms.date: 11/21/2017
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 2a62623ff54f13ac3547f53275be6d144d90025d
ms.sourcegitcommit: cce10e14c111e8a19f282ad6c032d802ebfec943
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39658101"
---
# <a name="configuring-proxy-settings-for-the-on-premises-data-gateway"></a>Configuration des paramètres de proxy de la passerelle de données locale
Votre environnement de travail peut nécessiter que vous passiez par un proxy pour accéder à Internet. Cela pourrait empêcher la passerelle de données locale de se connecter au service.

## <a name="does-your-network-use-a-proxy"></a>Votre réseau utilise-t-il un proxy ?
Le billet suivant sur superuser.com explique comment vous pouvez essayer de déterminer si vous disposez d’un proxy sur votre réseau.

[Comment savoir quel serveur proxy j’utilise ? (SuperUser.com)](https://superuser.com/questions/346372/how-do-i-know-what-proxy-server-im-using)

## <a name="configuration-file-location-and-default-configuration"></a>Emplacement du fichier de configuration et configuration par défaut
Les informations de proxy sont configurées dans un fichier de configuration .NET. L’emplacement et les noms de fichiers seront différents selon la passerelle utilisée.

### <a name="on-premises-data-gateway"></a>Passerelle de données locale
Il existe deux principaux fichiers de configuration impliqués dans la passerelle de données locale.

**Configuration**

Le premier concerne les écrans de configuration qui configurent en fait la passerelle. Si vous rencontrez des problèmes lors de la configuration de la passerelle, c’est le fichier que vous devez consulter.

    C:\Program Files\On-premises data gateway\enterprisegatewayconfigurator.exe.config

**Service Windows**

La deuxième concerne le service Windows à proprement parler, qui interagit avec le service Power BI et gère les requêtes.

    C:\Program Files\On-premises data gateway\Microsoft.PowerBI.EnterpriseGateway.exe.config

## <a name="configuring-proxy-settings"></a>Configuration des paramètres de proxy
La configuration de proxy par défaut est la suivante.

    <system.net>
        <defaultProxy useDefaultCredentials="true" />
    </system.net>

La configuration par défaut fonctionne avec l’authentification Windows. Si votre proxy utilise une autre forme d’authentification, vous devez modifier les paramètres. En cas de doute, vous devez contacter votre administrateur réseau. L’authentification de proxy de base n’est pas recommandée, et tenter de l’utiliser peut provoquer des erreurs d’authentification qui empêche la configuration correcte de la passerelle. Utiliser un mécanisme d’authentification de proxy plus fort pour corriger ce problème.

En plus d’utiliser des informations d’identification par défaut, vous pouvez ajouter un élément <proxy> pour définir les paramètres du serveur proxy plus en détail. Par exemple, vous pouvez spécifier que votre passerelle de données locale doit toujours utiliser le proxy même pour des ressources locales, en définissant le paramètre bypassonlocal sur false. Ceci peut vous aider à résoudre les problèmes dans des situations où vous voulez effectuer le suivi de toutes les demandes HTTPS provenant d’une passerelle de données locale dans les fichiers journaux du proxy. L’exemple de configuration suivant spécifie que toutes les demandes doivent passer par un serveur proxy spécifique avec l’adresse IP 192.168.1.10.

    <system.net>
        <defaultProxy useDefaultCredentials="true">
            <proxy  
                autoDetect="false"  
                proxyaddress="http://192.168.1.10:3128"  
                bypassonlocal="false"  
                usesystemdefault="true"
            />  
        </defaultProxy>
    </system.net>

Pour en savoir plus sur la configuration des éléments de proxy pour les fichiers de configuration .NET, consultez [defaultProxy, élément (paramètres réseau)](https://msdn.microsoft.com/library/kd3cf2ex.aspx).

## <a name="changing-the-gateway-service-account-to-a-domain-user"></a>Remplacement du compte de service de passerelle par un utilisateur de domaine
Lorsque vous configurez les paramètres de proxy pour utiliser les informations d’identification par défaut, comme expliqué ci-dessus, vous pouvez rencontrer des problèmes d’authentification avec votre proxy. Cela est dû au fait que le compte de service par défaut est le SID de service et non un utilisateur de domaine authentifié. Vous pouvez modifier le compte de service de la passerelle pour autoriser une authentification appropriée auprès de votre proxy.

> [!NOTE]
> Nous vous recommandons d’utiliser un compte de service administré pour éviter d’avoir à réinitialiser les mots de passe. Découvrez comment créer un [compte de service administré](https://technet.microsoft.com/library/dd548356.aspx) dans Active Directory.
> 
> 

### <a name="change-the-on-premises-data-gateway-service-account"></a>Modifier le compte de service de la passerelle de données locale
1. Modifiez le compte de service Windows du **service de passerelle de données locale**.

    Le compte par défaut de ce service est *NT SERVICE\PBIEgwService*. Vous pouvez le remplacer par un compte utilisateur de domaine au sein de votre domaine Active Directory. Vous pouvez également utiliser un compte de service administré pour éviter d’avoir à réinitialiser le mot de passe.

    Vous pouvez modifier le compte sous l’onglet **Connexion** des propriétés du service Windows.
2. Redémarrez le **service de passerelle de données locale**.

    Dans une invite de commandes d’administration, exécutez les commandes suivantes.

        net stop PBIEgwService

        net start PBIEgwService
3. Démarrez **l’outil de configuration de la passerelle de données locale**. Vous pouvez sélectionner le bouton Démarrer de Windows et rechercher *Passerelle de données locale*.
4. Connectez-vous à Power BI.
5. Restaurez la passerelle à l’aide de votre clé de récupération.

    Ainsi, le nouveau compte de service est en mesure de déchiffrer les informations d’identification stockées pour les sources de données.

> [!NOTE]
> Lorsque vous modifiez le compte de service directement depuis le panneau de configuration Services, il ne met pas à jour les listes de contrôle d'accès (ACL) automatiquement. Vous devez vous assurer que le nouveau compte de service a accès au dossier et fichiers d’installation. Vous trouverez le dossier d’Installation de la passerelle sous C:\Program Files\On-premises data gateway. 
> 

## <a name="next-steps"></a>Étapes suivantes
[Passerelle de données locale (mode personnel)](service-gateway-personal-mode.md)
[Informations sur le pare-feu](service-gateway-onprem-tshoot.md#firewall-or-proxy)  
D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)

