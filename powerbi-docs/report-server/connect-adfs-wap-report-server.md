---
title: Utiliser Web Application Proxy (WAP) et Active Directory Federated Services (AD FS) - Power BI Report Server
description: Découvrez comment utiliser Web Application Proxy (WAP) et Active Directory Federated Services (AD FS) pour vous connecter à Power BI Report Server et SQL Server Reporting Services (SSRS) 2016 et versions ultérieures.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: how-to
ms.date: 01/14/2020
ms.openlocfilehash: e9e2c44bdcbeabc28a95bd62bf6ba6763ae61442
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90859057"
---
# <a name="use-web-application-proxy-and-active-directory-federated-services---power-bi-report-server"></a>Utiliser Web Application Proxy (WAP) et Active Directory Federated Services (AD FS) - Power BI Report Server

Cet article explique comment utiliser Web Application Proxy (WAP) et Active Directory Federated Services (AD FS) pour se connecter à Power BI Report Server et SQL Server Reporting Services (SSRS) 2016 et versions ultérieures. Grâce à cette intégration, les utilisateurs qui se trouvent en dehors du réseau d’entreprise peuvent accéder à leurs rapports Power BI Report Server et Reporting Services depuis leurs navigateurs clients et être protégés par l’authentification AD FS. Pour les applications mobiles Power BI, vous devez également [configurer OAuth pour la connexion à Power BI Report Server et à SSRS](../consumer/mobile/mobile-oauth-ssrs.md).

## <a name="prerequisites"></a>Prérequis

### <a name="domain-name-services-dns-configuration"></a>Configuration DNS (Domain Name Services)

- Déterminez l’URL publique à laquelle l’utilisateur se connectera. Cette URL ressemble à l’exemple suivant : `https://reports.contosolab.com`.
- Configurez votre enregistrement DNS pour le nom d'hôte, `reports.contosolab.com`, par exemple, pour le pointer sur l’adresse IP publique du serveur Web Application Proxy (WAP).
- Configurez un enregistrement DNS public pour votre serveur AD FS. Par exemple, vous pouvez configurer le serveur AD FS avec l’URL suivante : `https://adfs.contosolab.com`.
- Configurez votre enregistrement DNS pour le pointer sur l’adresse IP publique du serveur Web Application Proxy (WAP), par exemple `adfs.contosolab.com`. Il est publié dans le cadre de l’application WAP.

### <a name="certificates"></a>Certificats

Vous devez configurer des certificats pour l’application WAP et le serveur AD FS. Ces certificats doivent faire partie d’une autorité de certificat valide reconnue par vos machines.

## <a name="1-configure-the-report-server"></a>1. Configurer le serveur de rapports

Nous devons nous assurer que le nom de principal du service (SPN) est valide. Le SPN valide permet l’authentification Kerberos appropriée et active le serveur de rapports pour l’authentification par négociation.

### <a name="service-principal-name-spn"></a>Nom de principal du service

Le nom de principal du service est un identificateur unique pour un service qui utilise l’authentification Kerberos. Assurez-vous de disposer d’un nom de principal du service HTTP approprié pour votre serveur de rapports.

Pour plus d’informations sur la configuration du nom de principal du service adéquat pour votre serveur de rapports, consultez [Inscrire un nom de principal du service (SPN) pour un serveur de rapports](/sql/reporting-services/report-server/register-a-service-principal-name-spn-for-a-report-server).

### <a name="enabling-negotiate-authentication"></a>Activation de l’authentification négociée

Pour autoriser un serveur de rapports à utiliser l’authentification Kerberos, vous devez définir le type d’authentification associé sur RSWindowsNegotiate. Effectuez cette configuration dans le fichier rsreportserver.config.

```
<AuthenticationTypes>

    <RSWindowsNegotiate />

    <RSWindowsNTLM />

</AuthenticationTypes>
```

Pour plus d’informations, consultez [Modifier un fichier de configuration Reporting Services](/sql/reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config) et [Configurer l’authentification Windows sur un serveur de rapports](/sql/reporting-services/security/configure-windows-authentication-on-the-report-server).

## <a name="2-configure-active-directory-federation-services-ad-fs"></a>2. Configurer Active Directory Federation Services (AD FS)

Vous devez configurer AD FS sur un serveur Windows 2016 au sein de votre environnement. Vous pouvez effectuer cette configuration dans le Gestionnaire de serveur en sélectionnant Ajouter des rôles et fonctionnalités sous Gérer. Pour plus d’informations, consultez [Active Directory Federation Services](/windows-server/identity/active-directory-federation-services).

Sur le serveur AD FS, à l’aide de l’application Gestion AD FS, effectuez les étapes suivantes.

1. Cliquez avec le bouton droit sur **Approbations de partie de confiance** > **Ajouter une approbation de partie de confiance**.

    ![Ajouter une approbation de partie de confiance](media/connect-adfs-wap-report-server/report-server-adfs-add-relying-party-trust.png)

2. Suivez les étapes de l’assistant **Ajouter une approbation de partie de confiance**.

    Choisissez l’option **Pas de prise en charge des revendications** pour utiliser la sécurité intégrée de Windows comme mécanisme d’authentification.

    ![Bienvenue dans l’assistant Ajouter une approbation de partie de confiance](media/connect-adfs-wap-report-server/report-server-adfs-add-relying-party-trust-welcome.png)

    Entrez un nom de votre choix dans le champ **Spécifier le nom d’affichage**, puis sélectionnez **Suivant**.
    Ajoutez l’identificateur d’approbation de partie de confiance : `<ADFS\_URL>/adfs/services/trust`

    Par exemple : `https://adfs.contosolab.com/adfs/services/trust`

    ![Report Server](media/connect-adfs-wap-report-server/report-server-adfs-configure-identifiers.png)

    Choisissez la **Stratégie de contrôle d’accès** répondant aux besoins de votre organisation, puis sélectionnez **Suivant**.

    ![Choisir le contrôle d’accès](media/connect-adfs-wap-report-server/report-server-adfs-choose-access-control.png)
    
    Sélectionnez **Suivant**, puis **Terminer** pour fermer l’assistant **Ajout d’approbation de partie de confiance**.

    Une fois l’opération terminée, les propriétés des approbations de partie de confiance devraient ressembler à ce qui suit.

    ![Approbations de partie de confiance](media/connect-adfs-wap-report-server/report-server-adfs-relying-party-trusts.png)

## <a name="3-configure-web-application-proxy-wap"></a>3. Configurer le proxy d'application web (WAP)

Vous devez activer le rôle Windows Proxy d’application web sur un serveur dans votre environnement. Il doit s’agir d’un serveur Windows 2016. Pour plus d’informations, consultez [Proxy d’application web dans Windows Server 2016](/windows-server/remote/remote-access/web-application-proxy/web-application-proxy-windows-server) et [Publication d’applications à l’aide de la pré-authentification AD FS](/windows-server/remote/remote-access/web-application-proxy/Publishing-Applications-using-AD-FS-Preauthentication).

### <a name="configure-constrained-delegation"></a>Configurer la délégation contrainte

Pour passer de l’authentification par formulaires à l’authentification Windows, nous devons utiliser la délégation contrainte avec la transition de protocole. Cette étape fait partie de la configuration de Kerberos. Nous avons déjà défini le nom principal de service (SPN) du serveur de rapports dans la configuration du serveur de rapports.

Nous devons configurer la délégation contrainte sur le compte du serveur WAP dans Active Directory. Vous devrez peut-être faire appel à un administrateur de domaine si vous n’avez pas de droits d’accès à Active Directory.

Pour configurer la délégation contrainte, procédez comme suit.

1. Sur un ordinateur sur lequel les outils Active Directory sont installés, lancez **Utilisateurs et ordinateurs Active Directory**.
2. Recherchez le compte correspondant à votre serveur WAP. Par défaut, il s’agit du conteneur **Ordinateurs**.
3. Cliquez avec le bouton droit sur le serveur WAP et accédez à **Propriétés**.
4. Dans l’onglet **Délégation**, sélectionnez **N’approuver cet ordinateur que pour la délégation aux services spécifiés**, puis **Utiliser tout protocole d’authentification**.

    ![Approuver cet ordinateur](media/connect-adfs-wap-report-server/report-server-adfs-delegation-use-any.png)

1. Cette option permet de configurer la délégation contrainte pour le compte du serveur WAP. Nous devons ensuite spécifier les services auxquels cet ordinateur est autorisé à déléguer.
2. Sélectionnez **Ajouter** sous la zone Services.

    ![Ajouter l’approbation AD FS](media/connect-adfs-wap-report-server/report-server-adfs-trust-add.png)

1. Sélectionnez **Utilisateurs ou ordinateurs**.
2. Entrez le compte de service que vous utilisez pour le serveur de rapports. Ce compte est le même que celui utilisé pour ajouter le nom principal de service (SPN) HTTP dans la section précédente [Configuration du serveur de rapports](#1-configure-the-report-server). 

3. Sélectionnez le SPN HTTP pour le serveur de rapports, puis choisissez **OK**.

    > [!NOTE]
    > Vous voyez peut-être uniquement le nom de principal du service NetBIOS. Les noms de principal du service NetBIOS et FQDN sont tous deux sélectionnés s’ils existent.

1. Lorsque la case à cocher **Développé** est activée, le résultat doit ressembler à l’exemple suivant.

    ![Propriétés WAP](media/connect-adfs-wap-report-server/report-server-wap-properties.png)

### <a name="add-wap-application"></a>Ajouter une application WAP

1. Sur le serveur proxy d’application web, ouvrez la console **Gestion de l’accès à distance**, puis sélectionnez **Proxy d'application web** dans le volet de navigation. 

2. Dans le volet **Tâches**, sélectionnez **Publier**.

2. Sur la page d’accueil, sélectionnez **Suivant**.

    ![Bienvenue dans la publication](media/connect-adfs-wap-report-server/report-server-welcome-publish-new-app-wizard.png)

3. Sur la page **Pré-authentification**, sélectionnez **Active Directory Federation Services (AD FS)** , puis **Suivant**.

    ![Pré-autorisation](media/connect-adfs-wap-report-server/report-server-preauthentication-new-app-wizard.png)

4. Sélectionnez la pré-authentification **Web et MSOFBA**, car nous allons configurer uniquement l’accès du navigateur au serveur de rapports, et non l’accès aux applications mobiles.

    ![Clients pris en charge](media/connect-adfs-wap-report-server/report-server-supported-clients-publish-new-app-wizard.png)

5. Ajoutez la **partie de confiance** que nous avons créée dans le serveur AD FS, comme indiqué ci-dessous, puis sélectionnez **Suivant**.

    ![Publier une partie de confiance](media/connect-adfs-wap-report-server/report-server-relying-party-publish-new-app-wizard.png)

6. Dans la section **URL externe**, saisissez l’URL accessible publiquement configurée sur le serveur WAP. Ajoutez l’URL configurée avec le serveur de rapports (Gestionnaire de configuration du serveur de rapports), comme indiqué ci-dessous dans la section **URL du serveur principal**. Ajoutez le nom de principal du service du serveur de rapports dans la section **SPN du serveur principal**.

    ![Paramètres de publication](media/connect-adfs-wap-report-server/report-server-publishing-settings-new-app-wizard.png)

7. Sélectionnez **Suivant**, puis **Publier**.
8. Exécutez la commande PowerShell suivante pour valider la configuration WAP.

    ```
    Get-WebApplicationProxyApplication "PBIRSBrowser" | FL
    ```

    ![Commande PowerShell](media/connect-adfs-wap-report-server/report-server-powershell-get-webapplication.png)

## <a name="connect-to-the-report-server-through-the-browser"></a>Se connecter au serveur de rapports via le navigateur

Vous pouvez ensuite accéder à l’URL WAP publique, par exemple, `https://reports.contosolab.com/ReportServer` pour le service Web et `https://reports.contosolab.com/Reports` pour le portail web, à partir du navigateur. Une fois authentifié, vous pouvez afficher les rapports.

![Connexion AD FS](media/connect-adfs-wap-report-server/report-server-adfs-sign-in.png)

## <a name="next-steps"></a>Étapes suivantes

* [Configurer OAuth pour la connexion à Power BI Report Server et à SSRS](../consumer/mobile/mobile-oauth-ssrs.md)
*[Présentation de Power BI Report Server](get-started.md)  

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)