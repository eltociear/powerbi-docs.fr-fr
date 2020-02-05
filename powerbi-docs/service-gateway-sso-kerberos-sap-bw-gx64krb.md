---
title: Utiliser Kerberos pour l’authentification unique avec gx64krb5
description: Configurer votre serveur SAP BW pour activer l’authentification unique à partir du service Power BI à l’aide de gx64krb5
author: arthiriyer
ms.author: arthii
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 10/10/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 6c8b62cf798d2fbbd09dab0603d216448d04487c
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/04/2020
ms.locfileid: "75000132"
---
# <a name="use-kerberos-for-single-sign-on-sso-to-sap-bw-using-gx64krb5"></a>Utiliser Kerberos pour l’authentification unique avec gx64krb5

Cet article explique comment configurer votre source de données SAP BW pour activer l’authentification unique à partir du service Power BI à l’aide de gx64krb5.

> [!NOTE]
> Vous pouvez effectuer les étapes de cet article en plus des étapes décrites dans [Configurer l’authentification unique Kerberos](service-gateway-sso-kerberos.md) pour activer l’actualisation SSO des rapports basés sur le serveur d’applications SAP BW dans le service Power BI. Toutefois, Microsoft recommande l’utilisation de CommonCryptoLib au lieu de gx64krb5 comme bibliothèque SNC. SAP ne prend plus en charge gx64krb5, et les étapes requises pour le configurer pour la passerelle sont beaucoup plus complexes qu’avec CommonCryptoLib. Consultez [Configurer SAP BW pour l’authentification unique à l’aide de CommonCryptoLib](service-gateway-sso-kerberos-sap-bw-commoncryptolib.md) pour plus d’informations sur la configuration de l’authentification unique à l’aide de CommonCryptoLib. Vous devez utiliser CommonCryptoLib _ou_ gx64krb5 comme bibliothèque SNC. N’effectuez pas les étapes de configuration pour les deux bibliothèques.

Ce guide décrit l’ensemble des étapes du processus. Si vous avez déjà effectué certaines de ces étapes, vous pouvez les ignorer. Par exemple, vous avez peut-être déjà configuré votre serveur SAP BW pour l’authentification unique à l’aide de gx64krb5.

## <a name="set-up-gx64krb5-on-the-gateway-machine-and-the-sap-bw-server"></a>Configurer gx64krb5 sur la machine de passerelle et le serveur SAP BW

> [!NOTE]
> SAP ne prend plus en charge la bibliothèque gx64krb5. Pour plus d’informations, consultez [SAP Note 352295](https://launchpad.support.sap.com/#/notes/352295). Notez que gx64krb5 n’autorise pas les connexions SSO de la passerelle de données aux serveurs de messages SAP BW. Seules les connexions aux serveurs d’applications SAP BW sont possibles. Cette restriction n’existe pas si vous utilisez [CommonCryptoLib](service-gateway-sso-kerberos-sap-bw-commoncryptolib.md) comme bibliothèque SNC. D’autres bibliothèques SNC peuvent également fonctionner pour l’authentification unique BW, mais elles ne sont pas officiellement prises en charge par Microsoft.

La bibliothèque gx64krb5 doit être utilisée par le client et par le serveur pour qu’une connexion à authentification unique puisse être établie par le biais de la passerelle. Autrement dit, le client et le serveur doivent utiliser la même bibliothèque SNC.

1. Téléchargez le fichier gx64krb5.dll à partir de la page [Note SAP 2115486](https://launchpad.support.sap.com/) (identifiant SAP s-user nécessaire). Veillez à disposer de la version 1.0.11.x au moins. Téléchargez également le fichier gsskrb5.dll (la version 32 bits de la bibliothèque) si vous souhaitez tester la connexion par authentification unique dans l’interface utilisateur graphique SAP avant d’essayer cette connexion par le biais de la passerelle (recommandé). La version 32 bits est requise pour effectuer des tests avec l’interface utilisateur graphique SAP, car cette interface est disponible uniquement en version 32 bits.

1. Placez le fichier gx64krb5.dll sur votre machine de passerelle à un emplacement accessible par l’utilisateur du service de passerelle. Si vous souhaitez tester la connexion par authentification unique à l’aide de l’interface utilisateur graphique SAP, placez également une copie de gsskrb5.dll sur la machine et définissez la variable d’environnement **SNC_LIB** de façon à ce qu’elle pointe vers cette copie. L’utilisateur du service de passerelle et les utilisateurs d’Active Directory (AD) dont l’utilisateur du service emprunte les identités ont tous besoin des autorisations de lecture et d’exécution sur la copie de gx64krb5.dll. Nous vous recommandons d’accorder des autorisations au fichier .dll au groupe des utilisateurs authentifiés. À des fins de test, vous pouvez également accorder explicitement ces autorisations à l’utilisateur du service de passerelle et à l’utilisateur Active Directory que vous utilisez pour les tests.

1. Si vous n’avez pas encore configuré votre serveur BW pour l’authentification unique avec gx64krb5.dll, placez une autre copie du fichier .dll sur votre machine serveur SAP BW à un emplacement accessible par le serveur SAP BW. 

    Pour plus d’informations sur la configuration de gx64krb5.dll en vue d’une utilisation avec un serveur SAP BW, consultez la [documentation SAP](https://launchpad.support.sap.com/#/notes/2115486) (identifiant SAP s-user nécessaire).

1. Sur les machine serveur et clientes, définissez les variables d’environnement **SNC_LIB** et **SNC_LIB_64** : 
    - Si vous utilisez gsskrb5.dll, définissez la variable **SNC_LIB** sur son chemin absolu. 
    - Si vous utilisez gx64krb5.dll, définissez la variable **SNC_LIB_64** sur son chemin absolu.

## <a name="configure-an-sap-bw-service-user-and-enable-snc-communication-on-the-bw-server"></a>Configurer un utilisateur du service SAP BW et activer la communication SNC sur le serveur BW

Effectuez les étapes de cette section si vous n’avez pas encore configuré votre serveur SAP BW pour la communication SNC (par exemple, l’authentification unique) à l’aide de gx64krb5.

> [!NOTE]
> Cette section part du principe que vous avez déjà créé un utilisateur de service pour BW et lui avez lié un nom de principal du service approprié (par exemple, un nom qui commence par *SAP/*).

1. Accordez à l’utilisateur du service l’accès à votre serveur d’applications SAP BW :

    1. Sur la machine serveur SAP BW, ajoutez l’utilisateur du service au groupe d’administrateurs local. Ouvrez le programme **Gestion des ordinateurs**, puis identifiez le groupe d’administrateurs local pour votre serveur. 

        ![Programme Gestion des ordinateurs](media/service-gateway-sso-kerberos/computer-management.png)

    1. Double-cliquez sur le groupe d’administrateurs local, puis sélectionnez **Ajouter** pour y ajouter votre utilisateur du service. 

    1. Sélectionnez **Vérifier les noms** pour vérifier que vous avez entré le nom correctement, puis sélectionnez **OK**.

1. Définissez l’utilisateur du service du serveur SAP BW en tant qu’utilisateur qui démarre le service du serveur SAP BW sur la machine serveur SAP BW :

    1. Ouvrez **Exécuter** et entrez **Services.msc**. 

    1. Recherchez le service correspondant à votre instance de serveur d’applications SAP BW, cliquez dessus avec le bouton droit, puis sélectionnez **Propriétés**.

        ![Capture d’écran de Services, avec l’option Propriétés en surbrillance](media/service-gateway-sso-kerberos/server-properties.png)

    1. Accédez à l’onglet **Connexion** et changez l’utilisateur par votre utilisateur du service SAP BW. 

    1. Entrez le mot de passe de l’utilisateur, puis sélectionnez **OK**.

1. Dans SAP Logon, connectez-vous à votre serveur et définissez les paramètres de profil suivants à l’aide de la transaction RZ10 :

    1. Définissez le paramètre de profil **snc/identity/as** sur *p:&lt;utilisateur du service SAP BW que vous avez créé&gt;*. Par exemple, *p:BWServiceUser\@MYDOMAIN.COM*. Notez que *p:* précède l’UPN de l’utilisateur du service, alors que l’UPN est précédé de *p:CN=* quand vous utilisez CommonCryptoLib comme bibliothèque SNC.

    1. Définissez le paramètre de profil **snc/gssapi\_lib** sur le *&lt;chemin de gx64krb5.dll sur le serveur BW&gt;*. Placez la bibliothèque à un emplacement accessible par le serveur d’applications SAP BW.

    1. Définissez les paramètres de profil supplémentaires suivants en changeant les valeurs en fonction de vos besoins. Les cinq dernières options permettent aux clients de se connecter au serveur SAP BW à l’aide de SAP Logon sans avoir à configurer un SNC.

        | **Paramètre** | **Valeur** |
        | --- | --- |
        | snc/data\_protection/max | 3 |
        | snc/data\_protection/min | 1 |
        | snc/data\_protection/use | 9 |
        | snc/accept\_insecure\_cpic | 1 |
        | snc/accept\_insecure\_gui | 1 |
        | snc/accept\_insecure\_r3int\_rfc | 1 |
        | snc/accept\_insecure\_rfc | 1 |
        | snc/permit\_insecure\_start | 1 |

    1. Définissez la propriété **snc/enable** sur 1.

1. Après avoir défini ces paramètres de profil, ouvrez la console de gestion SAP sur la machine serveur et redémarrez l’instance SAP BW. 

   Si le serveur ne démarre pas, vérifiez que vous avez correctement défini les paramètres de profil. Pour plus d’informations sur les paramètres de profil, consultez la [documentation SAP](https://help.sap.com/saphelp_nw70ehp1/helpdata/en/e6/56f466e99a11d1a5b00000e835363f/frameset.htm). Vous pouvez également consulter la section [Résolution des problèmes](#troubleshooting) de cet article.

## <a name="map-an-sap-bw-user-to-an-active-directory-user"></a>Mapper un utilisateur SAP BW à un utilisateur Active Directory

Si ce n’est déjà fait, mappez un utilisateur Active Directory à un utilisateur du serveur d’applications SAP BW et testez la connexion SSO dans SAP Logon.

1. Connectez-vous au serveur SAP BW à l’aide de SAP Logon. Exécutez la transaction SU01.

1. Pour **User**, entrez l’utilisateur SAP BW pour lequel vous souhaitez activer la connexion SSO. Sélectionnez l’icône **Edit** (qui représente un stylo) près de l’angle supérieur gauche de la fenêtre SAP Logon.

    ![SAP BW - Écran User maintenance](media/service-gateway-sso-kerberos/user-maintenance.png)

1. Sélectionnez l’onglet **SNC**. Dans la zone de texte « SNC name » (Nom SNC), entrez *p:&lt;utilisateur Active Directory&gt;@&lt;votre domaine&gt;*. Pour le nom SNC, *p:* doit précéder l’UPN de l’utilisateur Active Directory. Notez que l’UPN respecte la casse.

   L’utilisateur Active Directory que vous indiquez doit appartenir à la personne ou à l’organisation pour laquelle vous souhaitez activer l’accès SSO au serveur d’applications SAP BW. Par exemple, si vous voulez activer l’accès SSO pour l’utilisateur testuser\@TESTDOMAIN.COM, entrez *p:testuser\@TESTDOMAIN.COM*.

    ![SAP BW - Écran Maintain users](media/service-gateway-sso-kerberos/maintain-users.png)

1. Sélectionnez l’icône **Save** (qui représente une disquette) près de l’angle supérieur gauche de l’écran.

## <a name="test-sign-in-via-sso"></a>Tester la connexion par authentification unique

Vérifiez que vous pouvez vous connecter au serveur à l’aide de SAP Logon avec l’authentification unique en tant qu’utilisateur Active Directory pour lequel vous avez activé l’accès SSO :

1. En tant qu’utilisateur Active Directory pour lequel vous venez d’activer l’accès SSO, connectez-vous à une machine de votre domaine sur laquelle SAP Logon est installé. Lancez SAP Logon et créez une connexion.

1. Copiez le fichier gsskrb5.dll que vous avez téléchargé précédemment sur la machine à laquelle vous vous êtes connecté. Définissez la variable d’environnement **SNC_LIB** sur le chemin absolu de l’emplacement choisi.

1. Lancez SAP Logon et créez une connexion.

1. Dans l’écran **Create New System Entry** (Créer une entrée système), sélectionnez **User Specified System** (Système spécifié par l’utilisateur), puis sélectionnez **Next** (Suivant).

    ![Écran Create New System Entry](media/service-gateway-sso-kerberos/new-system-entry.png)

1. Renseignez les informations appropriées dans l’écran suivant, y compris le serveur d’applications, le numéro d’instance et l’ID du système. Ensuite, sélectionnez **Finish**.

1. Cliquez avec le bouton droit sur la nouvelle connexion, sélectionnez **Properties**, puis sélectionnez l’onglet **Network**. 

1. Dans la zone **SNC Name**, entrez *p:&lt;UPN de l’utilisateur du service SAP BW&gt;*. Par exemple, *p:BWServiceUser\@MYDOMAIN.COM*. Sélectionnez **OK**.

    ![Écran System Entry Properties](media/service-gateway-sso-kerberos/system-entry-properties.png)

1. Double-cliquez sur la connexion que vous venez de créer pour tenter une connexion SSO à votre serveur SAP BW. 

   Si cette connexion réussit, passez à la section suivante. Sinon, passez en revue les étapes antérieures de ce document pour vous assurer de les avoir effectuées correctement, ou consultez la section [Résolution des problèmes](#troubleshooting). Si vous ne réussissez pas à vous connecter au serveur SAP BW par le biais de l’authentification unique dans ce contexte, vous ne pouvez pas non plus le faire dans le contexte de la passerelle.

## <a name="add-registry-entries-to-the-gateway-machine"></a>Ajouter des entrées de Registre à la machine de passerelle

Ajoutez les entrées de registre nécessaires au registre de la machine sur laquelle la passerelle est installée et aux machines qui se connecteront à partir de Power BI Desktop. Pour ajouter ces entrées de registre, exécutez les commandes suivantes :

- ```REG ADD HKLM\SOFTWARE\Wow6432Node\SAP\gsskrb5 /v ForceIniCredOK /t REG_DWORD /d 1 /f```

- ```REG ADD HKLM\SOFTWARE\SAP\gsskrb5 /v ForceIniCredOK /t REG_DWORD /d 1 /f```

## <a name="add-a-new-sap-bw-application-server-data-source-to-the-power-bi-service-or-edit-an-existing-one"></a>Ajouter une nouvelle source de données du serveur d’applications SAP BW au service Power BI ou en modifier une existante

1. Dans la fenêtre de configuration de la source de données, entrez le **Nom d’hôte**, le **Numéro système** et l’**ID client** du serveur d’applications SAP BW que vous utilisez pour vous connecter à votre serveur SAP BW à partir de Power BI Desktop.

1. Dans le champ **Nom du partenaire SNC**, entrez *p:&lt;SPN que vous avez associé à l’utilisateur du service SAP BW&gt;*. Par exemple, si le SPN est SAP/BWServiceUser\@MYDOMAIN.COM, entrez *p:SAP/BWServiceUser\@MYDOMAIN.COM* dans le champ **Nom du partenaire SNC**.

1. Comme bibliothèque SNC, sélectionnez **SNC\_LIB** ou **SNC\_LIB\_64**. Assurez-vous que **SNC\_LIB\_64** sur la machine de passerelle pointe vers gx64krb5.dll. Vous pouvez également sélectionner l’option **Personnalisé** et fournir le chemin absolu du fichier gx64krb5.dll sur la machine de passerelle.

1. Sélectionnez **Utiliser SSO via Kerberos pour les requêtes DirectQuery**, puis sélectionnez **Appliquer**. Si le test de la connexion échoue, vérifiez que vous avez correctement effectué les étapes d’installation et de configuration précédentes.

1. [Générer un rapport Power BI](service-gateway-sso-kerberos.md#run-a-power-bi-report)

## <a name="troubleshooting"></a>Résolution des problèmes

### <a name="troubleshoot-gx64krb5-configuration"></a>Résoudre les problèmes de configuration de gx64krb5

Si vous rencontrez l’un des problèmes suivants, suivez ces étapes pour corriger l’installation de gx64krb5 et les connexions par authentification unique :

* Des erreurs se produisent quand vous effectuez les étapes de configuration de gx64krb5. Par exemple, le serveur SAP BW ne démarre pas après la modification des paramètres de profil. Consultez les journaux du serveur (…work\dev\_w0 sur la machine serveur) pour résoudre ces erreurs. 

* Vous ne pouvez pas démarrer le service SAP BW en raison d’un échec d’authentification. Vous avez peut-être fourni un mot de passe incorrect en définissant l’utilisateur SAP BW *start-as*. Vérifiez le mot de passe en vous connectant à une machine de votre environnement Active Directory en tant qu’utilisateur du service SAP BW.

* Si vous obtenez des erreurs indiquant que des informations d’identification de la source de données sous-jacente (par exemple, SQL Server) empêchent le démarrage du serveur, vérifiez que vous avez accordé à l’utilisateur du service l’accès à la base de données SAP BW.

* Vous obtenez le message suivant : *(GSS-API) La cible spécifiée est inconnue ou inaccessible*. Cette erreur indique généralement que vous avez spécifié un nom SNC incorrect. Dans l’application cliente, veillez à faire précéder l’UPN de l’utilisateur du service de *p:* uniquement et non *p:CN=*.

* Vous obtenez le message suivant : *(GSS-API) Un nom non valide a été fourni*. Vérifiez que *p:* est spécifié comme valeur du paramètre de profil d’identité SNC du serveur.

* Vous obtenez le message suivant : *(Erreur SNC) Le module spécifié est introuvable*. Cette erreur est souvent due au fait que le fichier gx64krb5.dll a été copié à un emplacement dont l’accès nécessite des privilèges élevés (droits d’administrateur).

### <a name="troubleshoot-gateway-connectivity-issues"></a>Résoudre les problèmes de connectivité de la passerelle

1. Consultez les journaux de la passerelle. Ouvrez l’application de configuration de la passerelle, puis sélectionnez **Diagnostics** et **Exporter les journaux**. Les erreurs les plus récentes apparaissent à la fin des fichiers journaux que vous examinez.

    ![Application Passerelle de données locale avec l’option Diagnostics en surbrillance](media/service-gateway-sso-kerberos/gateway-diagnostics.png)

1. Activez le suivi de SAP BW et examinez les fichiers journaux générés. Différents types de traçage SAP BW sont disponibles (par exemple, le traçage CPIC) :

   a. Pour activer le traçage CPIC, définissez deux variables d’environnement : **CPIC\_TRACE** et **CPIC\_TRACE\_DIR**.

      La première variable définit le niveau de trace, et la deuxième variable définit le répertoire des fichiers de trace. Le répertoire doit être un emplacement dans lequel les membres du groupe des utilisateurs authentifiés peuvent écrire. 
 
    b. Attribuez à **CPIC\_TRACE** la valeur *3* et définissez **CPIC\_TRACE\_DIR** sur le répertoire où seront enregistrés les fichiers de trace. Par exemple :

      ![Traçage CPIC](media/service-gateway-sso-kerberos/cpic-tracing.png)

    c. Reproduisez le problème et vérifiez que **CPIC\_TRACE\_DIR** contient des fichiers de trace. 
    
    d. Examinez le contenu des fichiers de trace pour identifier le problème de blocage. Par exemple, le fichier gx64krb5.dll n'a peut-être pas été chargé correctement, ou un utilisateur Active Directory différent de celui que vous attendiez a lancé la tentative de connexion SSO.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur la passerelle de données locale et DirectQuery, consultez les ressources suivantes :

* [Qu’est-ce qu’une passerelle de données locale ?](/data-integration/gateway/service-gateway-onprem)
* [DirectQuery dans Power BI](desktop-directquery-about.md)
* [Sources de données prises en charge par DirectQuery](desktop-directquery-data-sources.md)
* [DirectQuery et SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery et SAP HANA](desktop-directquery-sap-hana.md)
