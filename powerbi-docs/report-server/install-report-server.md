---
title: Installer Power BI Report Server
description: Découvrez comment installer Power BI Report Server.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: how-to
ms.date: 01/16/2020
ms.openlocfilehash: 049f6f563c9ac6e7494b0680b69e0df8909304d4
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90861886"
---
# <a name="install-power-bi-report-server"></a>Installer Power BI Report Server

Découvrez comment installer Power BI Report Server.

## <a name="download-power-bi-report-server"></a>Télécharger Power BI Report Server

Dans la page [Rapports locaux avec Power BI Report Server](https://powerbi.microsoft.com/report-server/), sélectionnez **Téléchargez une version d’évaluation gratuite**.

Quand vous exécutez le fichier PowerBIReportServer.exe, vous sélectionnez l’essai gratuit ou vous entrez la clé de produit. Lisez la suite pour plus de détails.

## <a name="before-you-install"></a>Avant l’installation

Avant d’installer Power BI Report Server, il est recommandé de lire l’article [Configurations matérielle et logicielle requises pour installer Power BI Report Server](system-requirements.md).

 > [!IMPORTANT]
 > Même si vous pouvez installer Power BI Report Server dans un environnement disposant d’un contrôleur de domaine en lecture seule (RODC), pour fonctionner correctement, Power BI Report Server doit avoir accès à un contrôleur de domaine en lecture-écriture. Si Power BI Report Server a accès uniquement à un RODC, il se peut que vous rencontriez des erreurs lors de la tentative d’administrer le service.

### <a name="power-bi-report-server-product-key"></a>Clé de produit Power BI Report Server

Vous pouvez obtenir la clé de produit de Power BI Report Server à partir de deux sources différentes :

- Power BI Premium
- SQL Server Entreprise Software Assurance (SA)

Lisez la suite pour plus de détails.

#### <a name="power-bi-premium"></a>Power BI Premium

Si vous avez acheté Power BI Premium, vous pouvez accéder à la clé de produit de votre instance de Power BI Report Server sous l’onglet **Paramètres Premium** du portail d’administration Power BI. Le portail d’administration est réservé aux administrateurs généraux ou aux utilisateurs qui ont le rôle Administrateur de service Power BI.

![Paramètres Premium](../report-server/media/install-report-server/pbirs-product-key.png "Clé Power BI Report Server dans les paramètres Premium")

Si vous sélectionnez **Clé de Power BI Report Server**, une boîte de dialogue contenant votre clé de produit s’affiche. Copiez-la pour l’utiliser lors de l’installation.

![Clé de produit](../report-server/media/install-report-server/pbirs-product-key-dialog.png "Clé de produit Power BI Report Server")

#### <a name="sql-server-enterprise-software-assurance-sa"></a>SQL Server Entreprise Software Assurance (SA)

Si vous disposez d’un contrat SQL Server Entreprise SA, vous pouvez vous procurer votre clé de produit auprès du [Centre de gestion des licences en volume](https://www.microsoft.com/Licensing/servicecenter/).

## <a name="install-your-report-server"></a>Installer votre serveur de rapports

L’installation de Power BI Report Server est très simple. Quelques étapes suffisent pour installer les fichiers.

Il n’est pas nécessaire de disposer d’un moteur de base de données Microsoft SQL Server au moment de l’installation. En revanche, il vous en faudra un pour configurer Reporting Services après l’installation.

1. Trouvez le programme d’installation PowerBIReportServer.exe, puis exécutez-le.

2. Sélectionnez **Installer Power BI Report Server**.

    ![Installer Power BI Report Server](media/install-report-server/pbireportserver-install.png)
3. Choisissez l’édition à installer, puis sélectionnez **suivant**.

    ![Choisir une édition](media/install-report-server/pbireportserver-choose-edition.png)

    Choisissez l’édition Évaluation ou Développeur.

    ![Édition 2](media/install-report-server/pbireportserver-choose-edition2.png)

    Sinon, entrez la clé de produit obtenue à partir du service Power BI ou du Centre MVLS. Pour plus d’informations sur l’obtention de votre clé de produit, consultez la section [Avant l’installation](#before-you-install) ci-dessus.
4. Lisez et acceptez les termes du contrat de licence, puis sélectionnez **Suivant**.

    ![Termes du contrat de licence](media/install-report-server/pbireportserver-eula.png)
5. Pour stocker la base de données du serveur de rapports, vous avez besoin d’un moteur de base de données. Sélectionnez **Suivant** pour installer uniquement le serveur de rapports.

    ![Installer uniquement les fichiers](media/install-report-server/pbireportserver-install-files-only.png)
6. Spécifiez l’emplacement d’installation du serveur de rapports. Sélectionnez **Installer** pour continuer.

    ![Spécifier le chemin d’accès à l’installation](media/install-report-server/pbireportserver-install-file-path.png)

    Le chemin d’accès par défaut est C:\Program Files\Microsoft Power BI Report Server.

7. Une fois l’installation effectuée, sélectionnez **Configurer Report Server** pour lancer le Gestionnaire de configuration de Reporting Services.

    ![Configurer le serveur de rapports](media/install-report-server/pbireportserver-configure.png)

## <a name="configure-your-report-server"></a>Configurer votre serveur de rapports

Lorsque vous sélectionnez **Configurer Report Server** dans le programme d’installation, le Gestionnaire de configuration de Reporting Services s’affiche. Pour plus d’informations, voir [Gestionnaire de configuration de Reporting Services](/sql/reporting-services/install-windows/reporting-services-configuration-manager-native-mode).

Pour achever la configuration initiale de Reporting Services, vous [créez une base de données de serveur de rapports](/sql/reporting-services/install-windows/ssrs-report-server-create-a-report-server-database). Pour effectuer cette étape, un serveur de base de données SQL Server est requis.

### <a name="creating-a-database-on-a-different-server"></a>Création d’une base de données sur un autre serveur

Si vous créez la base de données du serveur de rapports sur un serveur de base de données installé sur un autre ordinateur, changez le compte de service du serveur de rapports avec des informations d’identification reconnues sur le serveur de base de données. 

Par défaut, le serveur de rapports utilise le compte de service virtuel. Si vous tentez de créer une base de données sur un autre serveur, vous pouvez rencontrer l’erreur suivante à l’étape d’application des droits de connexion.

`System.Data.SqlClient.SqlException (0x80131904): Windows NT user or group '(null)' not found. Check the name again.`

Pour corriger cette erreur, vous pouvez modifier le compte de service en Service réseau ou en un compte de domaine. La modification du compte de service en Service réseau applique des droits dans le contexte du compte d’ordinateur pour le serveur de rapports.

![Configurer un compte de service pour le serveur de rapports](media/install-report-server/pbireportserver-configure-account.png)

Pour plus d’informations, voir [Configurer le compte de service du serveur de rapports](/sql/reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager).

## <a name="windows-service"></a>Service Windows

Un service Windows créé dans le cadre de l’installation. Il s’affiche en tant que **Power BI Report Server**. Le nom du service est **PowerBIReportServer**.

![Service Windows du serveur de rapports](media/install-report-server/pbireportserver-windows-service.png)

![Propriétés du service Windows du serveur de rapports](media/install-report-server/pbireportserver-windows-service2.png)

## <a name="default-url-reservations"></a>Réservations d’URL par défaut

Les réservations d’URL se composent d’un préfixe, d’un nom d’hôte, d’un port et d’un répertoire virtuel :

| Partie | Description |
| --- | --- |
| Préfixe |Le préfixe par défaut est HTTP. Si vous avez installé précédemment un certificat SSL (Secure Sockets Layer), le programme d’installation tente de créer des réservations d’URL utilisant le préfixe HTTPS. |
| Nom d’hôte |Le nom d’hôte par défaut est un caractère générique fort (+). Il indique que le serveur de rapports accepte toute demande HTTP sur le port désigné pour tout nom d’hôte correspondant à l’ordinateur, dont `https://<computername>/reportserver`, `https://localhost/reportserver` ou`https://<IPAddress>/reportserver.` |
| Port |Le port par défaut est 80. Si vous utilisez un port autre que le port 80, vous devez ajouter celui-ci explicitement à l’URL lorsque vous ouvrez le portail web dans une fenêtre de navigateur. |
| Répertoire virtuel |Par défaut, les répertoires virtuels créés sont ReportServer pour le service Web Report Server et Reports pour le portail web. Pour le service Web Report Server, le répertoire virtuel par défaut est **reportserver**. Pour le portail web, le répertoire virtuel par défaut est **reports**. |

Voici un exemple de chaîne URL complète :

* `https://+:80/reportserver`, donne accès au serveur de rapports.
* `https://+:80/reports`, donne accès au portail web.

## <a name="firewall"></a>Pare-feu

Si vous accédez au serveur de rapports à partir d’un ordinateur distant, veillez à avoir configuré des règles de pare-feu si un pare-feu est présent.

Ouvrez le port TCP que vous avez configuré pour l’URL du service web et l’URL du portail web. Par défaut, elles sont configurées sur le port TCP 80.

## <a name="additional-configuration"></a>Configuration supplémentaire

* Pour configurer l’intégration avec le service Power BI afin de pouvoir épingler des éléments de rapport à un tableau de bord Power BI, voir [Intégration de Power BI Report Server](/sql/reporting-services/install-windows/power-bi-report-server-integration-configuration-manager).
* Pour configurer le courrier pour le traitement des abonnements, voir [Paramètres du courrier](/sql/reporting-services/install-windows/e-mail-settings-reporting-services-native-mode-configuration-manager) et [Remise du courrier dans un serveur de rapports](/sql/reporting-services/subscriptions/e-mail-delivery-in-reporting-services).
* Pour configurer le portail web de façon à pouvoir y accéder sur un ordinateur de rapport pour afficher et gérer les rapports, voir [Configurer un pare-feu pour l’accès au serveur de rapports](/sql/reporting-services/report-server/configure-a-firewall-for-report-server-access) et [Configurer un serveur de rapports pour l’administration à distance](/sql/reporting-services/report-server/configure-a-report-server-for-remote-administration).
* Pour plus d’informations sur la définition des propriétés système du serveur de rapports dans SQL Server Management Studio, consultez la [page avancée Propriétés du serveur](/sql/reporting-services/tools/server-properties-advanced-page-reporting-services). Sauf indication contraire, les options s’appliquent à la fois à Power BI Report Server et à SQL Server Reporting Services.

## <a name="next-steps"></a>Étapes suivantes

[Vue d’ensemble de l’administrateur](admin-handbook-overview.md)  
[Trouver la clé de produit de votre serveur de rapports](find-product-key.md)  
[Installer Power BI Desktop optimisé pour Power BI Report Server](install-powerbi-desktop.md)  
[Vérifier une installation de Reporting Services](/sql/reporting-services/install-windows/verify-a-reporting-services-installation)  
[Configurer le compte de service du serveur de rapports](/sql/reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager)  
[Configurer les URL du serveur de rapports](/sql/reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager)  
[Configurer la connexion de base de données d’un serveur de rapports](/sql/reporting-services/install-windows/configure-a-report-server-database-connection-ssrs-configuration-manager)  
[Initialiser un serveur de rapports](/sql/reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server)  
[Configurer des connexions SSL sur un serveur de rapports](/sql/reporting-services/security/configure-ssl-connections-on-a-native-mode-report-server)  
[Configurer des autorisations et des comptes de service Windows](/sql/database-engine/configure-windows/configure-windows-service-accounts-and-permissions)  
[Prise en charge du navigateur pour Power BI Report Server](browser-support.md)

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)