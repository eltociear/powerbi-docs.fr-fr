---
title: Utiliser l’authentification unique Kerberos pour l’authentification unique pour SAP BW à l’aide de CommonCryptoLib (sapcrypto.dll)
description: Configurer votre serveur SAP BW pour activer l’authentification unique à partir du service Power BI à l’aide de CommonCryptoLib (sapcrypto.dll)
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 08/01/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 6c4f2b0d8856d5e68e02b9b33cf393ca85ecb580
ms.sourcegitcommit: 7a0ce2eec5bc7ac8ef94fa94434ee12a9a07705b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71106282"
---
# <a name="use-kerberos-single-sign-on-for-sso-to-sap-bw-using-commoncryptolib-sapcryptodll"></a>Utiliser l’authentification unique Kerberos pour l’authentification unique pour SAP BW à l’aide de CommonCryptoLib (sapcrypto.dll)

Cet article explique comment configurer votre serveur SAP BW pour activer l’authentification unique à partir du service Power BI à l’aide de CommonCryptoLib (sapcrypto.dll).

> [!NOTE]
> Suivez les étapes décrites dans cet article en plus des étapes décrites [Configurer l’authentification unique Kerberos](service-gateway-sso-kerberos.md) avant d’essayer d’actualiser un rapport basé sur SAP BW qui utilise l’authentification unique Kerberos. L’utilisation de CommonCryptoLib comme bibliothèque SNC active les connexions par authentification unique à la fois aux serveurs d’applications SAP BW et aux serveurs de messages SAP BW.

## <a name="configure-sap-bw-server-to-enable-sso-using-commoncryptolib"></a>Configurer un serveur SAP BW pour activer l’authentification unique à l’aide de CommonCryptoLib

> [!NOTE]
> La passerelle de données locale est un logiciel 64 bits et requiert donc la version 64 bits de CommonCryptoLib (sapcrypto.dll). Si vous envisagez de tester la connexion par authentification unique à votre serveur SAP BW dans l’interface graphique de SAP avant de tenter une connexion par authentification unique via la passerelle (recommandé), vous aurez également besoin de la version 32 bits de CommonCryptoLib, car l’interface graphique de SAP est un logiciel 32 bits.

1. Vérifiez que votre serveur BW est correctement configuré pour l’authentification unique Kerberos avec CommonCryptoLib. Si c’est le cas, vous devriez être en mesure d’utiliser l’authentification unique pour accéder à votre serveur BW (directement ou via un serveur de messages SAP BW) avec un outil SAP, comme l’interface graphique SAP, qui a été configuré pour utiliser CommonCryptoLib. Pour plus d’informations sur les étapes de configuration, consultez [Authentification unique SAP : S’authentifier avec Kerberos/SPNEGO](https://blogs.sap.com/2017/07/27/sap-single-sign-on-authenticate-with-kerberosspnego/). Votre serveur BW doit utiliser CommonCryptoLib comme bibliothèque SNC et avoir un nom SNC commençant par « CN= », par exemple « CN=BW1 ». Pour plus d’informations sur les conditions requises pour les noms SNC, consultez [Paramètres SNC pour la configuration de Kerberos](https://help.sap.com/viewer/df185fd53bb645b1bd99284ee4e4a750/3.0/en-US/360534094511490d91b9589d20abb49a.html) (en particulier le paramètre snc/identity/as).

1. Si vous ne l’avez pas déjà fait, installez la version 64 bits du [connecteur SAP .NET](https://support.sap.com/en/product/connectors/msnet.html) sur l’ordinateur sur lequel la passerelle a été installée. Vous pouvez vérifier si le composant a été installé en tentant de vous connecter à votre serveur BW dans Power BI Desktop. Si vous ne pouvez pas vous connecter à l’aide de l’implémentation 2.0, le connecteur .NET n’est pas installé.

1. Assurez-vous que le client de connexion sécurisée SAP n’est pas en cours d’exécution sur l’ordinateur sur lequel la passerelle est installée. SLC met en cache les tickets Kerberos d’une façon pouvant interférer avec la capacité de la passerelle à utiliser Kerberos pour l’authentification unique. Si SLC est installé, désinstallez-le ou assurez-vous de quitter le client de connexion sécurisée SAP : faites un clic droit sur l’icône dans la barre d’état système et sélectionnez Se déconnecter et quitter avant de tenter une connexion SSO à l’aide de la passerelle. SLC n’est pas pris en charge pour une utilisation sur des machines Windows Server. Pour plus d’informations, consultez [SAP Note 2780475](https://launchpad.support.sap.com/#/notes/2780475) (utilisateur-s requis).

    ![Client de connexion sécurisée SAP](media/service-gateway-sso-kerberos/sap-secure-login-client.png)

    Si vous désinstallez SLC ou sélectionnez **Se déconnecter** et **Quitter**, ouvrez une fenêtre de commande et entrez `klist purge` pour effacer tous les tickets Kerberos mis en cache avant de tenter une connexion SSO via la passerelle.

1. Téléchargez CommonCryptoLib (sapcrypto.dll) 64 bits (version **8.5.25 ou ultérieure**) à partir de SAP Launchpad, puis copiez-le dans un dossier sur votre machine passerelle. Dans le même répertoire que celui où vous avez copié sapcrypto.dll, créez un fichier nommé sapcrypto.ini, avec le contenu suivant :

    ```
    ccl/snc/enable_kerberos_in_client_role = 1
    ```

    Le fichier .ini contient les informations de configuration requises par CommonCryptoLib pour activer l’authentification unique dans le scénario de passerelle.

    > [!NOTE]
    > Ces fichiers doivent être stockés au même emplacement. En d’autres termes, _/path/to/sapcrypto/_ doit contenir à la fois sapcrypto.ini et sapcrypto.dll.

    L’utilisateur du service de passerelle et l’utilisateur Active Directory (AD) dont l’utilisateur du service emprunte l’identité ont besoin des autorisations de lecture et d’exécution pour les deux fichiers. Nous vous recommandons d’accorder des autorisations aux fichiers .ini et .dll au groupe des utilisateurs authentifiés. À des fins de test, vous pouvez également accorder explicitement ces autorisations à l’utilisateur du service de passerelle et à l’utilisateur Active Directory que vous utilisez pour les tests. Dans la capture d’écran ci-dessous, nous avons accordé au groupe des utilisateurs authentifiés les autorisations **Lecture&amp; Exécuter** pour sapcrypto. dll:

    ![Utilisateurs authentifiés](media/service-gateway-sso-kerberos/authenticated-users.png)

1. Si vous n’avez pas de source de données SAP BW, sur la page **Gérer les passerelles** dans le service Power BI, ajoutez une source de données. Si vous disposez déjà d’une source de données BW associée à la passerelle au sein de laquelle vous souhaitez que la connexion SSO circule, préparez-la pour la modifier. Choisissez **SAP Business Warehouse** comme **Type de source de données** si vous souhaitez créer une connexion par authentification unique à un serveur d’applications BW. Sélectionnez **Serveur de messages SAP Business Warehouse** si vous souhaitez créer une connexion par authentification unique à un serveur de messagerie BW.

    Dans le cas d’une **bibliothèque SNC**, sélectionnez la variable d’environnement **SNC\_LIB ou SNC\_LIB\_64** ou **personnalisée**. Si vous sélectionnez l’option **SNC\_LIB**, vous devez définir la valeur de la variable d’environnement **SNC\_LIB\_64** sur la machine passerelle sur le chemin d’accès absolu de la copie 64 bits de sapcrypto.dll sur la machine passerelle, tel que C:\Users\Test\Desktop\sapcrypto.dll. Si vous choisissez **Personnalisé**, collez le chemin d’accès absolu au fichier sapcrypto.dll dans le champ Chemin d’accès personnalisé de la bibliothèque SNC qui s’affiche sur la page **Gérer les passerelles**. Pour le **Nom du partenaire SNC**, entrez le nom SNC du serveur BW. Sous **Paramètres avancés**, vérifiez que l’option **Utiliser l’authentification unique via Kerberos pour les requêtes DirectQuery** est cochée. Les autres champs doivent être remplis comme si vous établissiez une connexion par authentification Windows à partir de PBI Desktop.

1. Créez une variable d’environnement du système CCL\_PROFILE et pointez-la sur sapcrypto.ini :

    ![Variable d’environnement du système CCL\_PROFILE](media/service-gateway-sso-kerberos/ccl-profile-variable.png)

    N’oubliez pas que les fichiers sapcrypto.dll et .ini doivent se trouver au même emplacement. Dans l’exemple ci-dessus, où sapcrypto.ini se trouve sur le bureau, sapcrypto.dll doit également se trouver sur le bureau.

1. Redémarrez le service de passerelle :

    ![Redémarrez le service de passerelle](media/service-gateway-sso-kerberos/restart-gateway-service.png)

1. [Générer un rapport Power BI](service-gateway-sso-kerberos.md#run-a-power-bi-report)

## <a name="troubleshooting"></a>Résolution des problèmes

Si vous ne parvenez pas à actualiser le rapport dans le service Power BI, vous pouvez utiliser le suivi de la passerelle, le traçage CPIC et le traçage CommonCryptoLib pour aider à diagnostiquer le problème. Le traçage CPIC et CommonCryptoLib étant des produits SAP, Microsoft ne peut pas fournir de support direct pour eux. Pour les utilisateurs Active Directory disposant d’un accès SSO à BW, certaines configurations Active Directory peuvent nécessiter que les utilisateurs soient membres du groupe Administrateurs sur la machine sur lequel la passerelle est installée.

1. **Journaux de passerelle :** Il vous suffit de reproduire le problème, d’ouvrir [l’application de passerelle](https://docs.microsoft.com/data-integration/gateway/service-gateway-app), d’accéder à l’onglet **Diagnostics** et de sélectionner **Exporter les journaux** :

    ![Exporter des journaux de passerelle](media/service-gateway-sso-kerberos/export-gateway-logs.png)

1. **Traçage CPIC :** Pour activer le traçage CPIC, définissez deux variables d’environnement : CPIC\_TRACE et CPIC\_TRACE\_DIR. La première variable définit le niveau de suivi, et la deuxième variable définit le répertoire des fichiers de trace. Le répertoire doit être un emplacement dans lequel les membres du groupe des utilisateurs authentifiés peuvent écrire. Configurez CPIC\_TRACE à 3 et CPIC\_TRACE\_DIR au répertoire dans lequel vous souhaitez effectuer le suivi des fichiers écrits.

    ![Traçage CPIC](media/service-gateway-sso-kerberos/cpic-tracing.png)

    Reproduisez le problème et vérifiez que CPIC\_TRACE\_DIR contient des fichiers de trace.

1. **Traçage CommonCryptoLib :** Activez le traçage CommonCryptoLib en ajoutant deux lignes au fichier sapcrypto.ini créé précédemment :

    ```
    ccl/trace/level=5
    ccl/trace/directory=<drive>:\logs\sectrace
    ```

    Veillez à définir l’option _ccl/trace/directory_ sur un emplacement dans lequel les membres du groupe des utilisateurs authentifiés peuvent écrire. Vous pouvez également créer un nouveau fichier .ini pour modifier ce comportement. Dans le même répertoire que les fichiers sapcrypto.dll et sapcrypto.ini, créez un fichier nommé sectrace.ini, avec le contenu ci-dessous. Remplacez l’option DIRECTORY par un emplacement sur votre machine sur lequel l’utilisateur authentifié peut écrire :

    ```
    LEVEL = 5

    DIRECTORY = <drive>:\logs\sectrace
    ```

    À présent, reproduisez le problème et vérifiez que l’emplacement désigné par DIRECTORY contient des fichiers de trace. Lorsque vous avez terminé, veillez à désactiver CPIC et le traçage CCL.

    Pour plus d’informations sur le traçage CommonCryptoLib, consultez [Note SAP 2491573](https://launchpad.support.sap.com/#/notes/2491573) (utilisateur-s requis).

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur la **Passerelle de données locale** et **DirectQuery**, consultez les ressources suivantes :

* [Qu’est-ce qu’une passerelle de données locale ?](/data-integration/gateway/service-gateway-getting-started)
* [DirectQuery dans Power BI](desktop-directquery-about.md)
* [Sources de données prises en charge par DirectQuery](desktop-directquery-data-sources.md)
* [DirectQuery et SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery et SAP HANA](desktop-directquery-sap-hana.md)
