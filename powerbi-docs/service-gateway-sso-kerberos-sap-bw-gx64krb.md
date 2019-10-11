---
title: Utiliser Kerberos pour l’authentification unique avec gx64krb5
description: Configurer votre serveur SAP BW pour activer l’authentification unique à partir du service Power BI à l’aide de gx64krb5
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 08/01/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 4932f00fa7585c6b4f9186c29b65700d7a14fbea
ms.sourcegitcommit: 9bf3cdcf5d8b8dd12aa1339b8910fcbc40f4cbe4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2019
ms.locfileid: "71968707"
---
# <a name="use-kerberos-for-single-sign-on-sso-to-sap-bw-using-gx64krb5"></a>Utiliser Kerberos pour l’authentification unique avec gx64krb5

Cet article explique comment configurer votre source de données SAP BW pour activer l’authentification unique à partir du service Power BI à l’aide de gx64krb5.

> [!NOTE]
> Vous pouvez effectuer les étapes de cet article en plus des étapes décrites dans [Configurer l’authentification unique Kerberos](service-gateway-sso-kerberos.md) pour activer l’actualisation SSO des rapports basés sur le serveur d’applications SAP BW dans le service Power BI. Toutefois, Microsoft recommande l’utilisation de CommonCryptoLib au lieu de gx64krb5 comme bibliothèque SNC. SAP n’offre plus de prise en charge de gx64krb5, et les étapes requises pour le configurer pour une utilisation avec la passerelle sont beaucoup plus complexes par rapport à CommonCryptoLib. Consultez [Configurer SAP BW pour l’authentification unique à l’aide de CommonCryptoLib](service-gateway-sso-kerberos-sap-bw-commoncryptolib.md) pour savoir comment configurer l’authentification unique à l’aide de CommonCryptoLib. Vous devez effectuer la configuration pour CommonCryptoLib _ou_ gx64krb5. N’effectuez pas les étapes de configuration pour les deux bibliothèques.

### <a name="set-up-gx64krb5-on-gateway-machine-and-the-sap-bw-server"></a>Configurer gx64krb5 sur la machine de passerelle et le serveur SAP BW
Ce guide tente d’être aussi complet que possible. Si vous avez déjà effectué certaines étapes, vous pouvez les ignorer. Par exemple, vous avez peut-être déjà configuré votre serveur SAP BW pour l’authentification unique à l’aide de gx64krb5.

### <a name="set-up-gx64krb5-on-the-gateway-machine-and-the-sap-bw-server"></a>Configurer gx64krb5 sur la machine de passerelle et le serveur SAP BW

> [!NOTE]
> `gx64krb5` n’est plus activement pris en charge par SAP. Pour plus d’informations, consultez [SAP Note 352295](https://launchpad.support.sap.com/#/notes/352295). Notez également que `gx64krb5` n’autorise pas les connexions d’authentification unique de la passerelle de données aux serveurs de messages SAP BW. Seules les connexions aux serveurs d’applications SAP BW sont possibles. Cette restriction qui concerne uniquement le serveur d’applications n’existe pas si vous utilisez [CommonCryptoLib](service-gateway-sso-kerberos-sap-bw-commoncryptolib.md) en tant que bibliothèque SNC. D’autres bibliothèques SNC peuvent également fonctionner pour l’authentification unique BW, mais elles ne sont pas officiellement prises en charge par Microsoft.

`gx64krb5` doit être utilisé par le client et par le serveur pour établir une connexion par authentification unique via la passerelle, c’est-à-dire que le client et le serveur doivent utiliser la même bibliothèque SNC.

1. Téléchargez `gx64krb5` à partir de la page [SAP Note 2115486](https://launchpad.support.sap.com/) (compte super utilisateur SAP requis). Veillez à disposer de la version 1.0.11.x au moins. Téléchargez également `gsskrb5` (la version 32 bits de la bibliothèque) si vous souhaitez tester la connexion par authentification unique dans l’interface graphique de SAP avant de tenter la connexion par authentification unique via la passerelle (recommandé). La version 32 bits est requise pour effectuer des tests avec l’interface graphique de SAP, car elle est disponible uniquement en version 32 bits.

1. Placez `gx64krb5` sur votre machine de passerelle à un emplacement accessible par l’utilisateur du service de passerelle. Si vous souhaitez tester la connexion par authentification unique à l’aide de l’interface graphique utilisateur SAP, placez également une copie de `gsskrb5` sur la machine et définissez la variable d’environnement **SNC_LIB** de façon à ce qu’elle pointe vers cette copie. L’utilisateur du service de passerelle et les utilisateurs d’Active Directory (AD) dont l’utilisateur du service emprunte les identités ont tous besoin des autorisations de lecture et d’exécution sur la copie de `gx64krb5`. Nous vous recommandons d’accorder des autorisations au fichier .dll au groupe des utilisateurs authentifiés. À des fins de test, vous pouvez également accorder explicitement ces autorisations à l’utilisateur du service de passerelle et à l’utilisateur Active Directory que vous utilisez pour les tests.

1. Si vous n’avez pas encore configuré votre serveur BW pour l’authentification unique avec gx64krb5, placez une autre copie du fichier .dll sur votre machine serveur SAP BW à un emplacement accessible par le serveur SAP BW. Pour plus d’informations sur la configuration de gx64krb5 en vue d’une utilisation avec un serveur SAP BW, consultez la [documentation SAP](https://launchpad.support.sap.com/#/notes/2115486).

1. Sur les machines serveur et clientes, définissez les variables d’environnement `SNC_LIB` et/ou `SNC_LIB_64`. Si vous utilisez gsskrb5, définissez la variable `SNC_LIB` sur le chemin d’accès absolu de gsskrb5.dll. Si vous utilisez gx64krb5, définissez la variable `SNC_LIB_64` sur le chemin d’accès absolu de gx64krb5.dll.

### <a name="configure-an-sap-bw-service-user-and-enable-snc-communication-on-the-bw-server"></a>Configurer un utilisateur du service SAP BW et activer la communication SNC sur le serveur BW

Effectuez les étapes de cette section si vous n’avez pas encore configuré votre serveur SAP BW pour la communication SNC (par exemple l’authentification unique) à l’aide de gx64krb5.

> [!NOTE]
> Cette section part du principe que vous avez déjà créé un utilisateur de service pour BW et lui avez lié un nom de principal du service approprié (par exemple un nom qui commence par `SAP/`).

1. Accordez à l’utilisateur du service l’accès à votre serveur d’applications SAP BW :

    1. Sur la machine serveur SAP BW, ajoutez l’utilisateur du service au groupe d’administrateurs local. Ouvrez le programme Gestion des ordinateurs, puis identifiez le groupe d’administrateurs local pour votre serveur. Par exemple :

        ![Capture d’écran du programme Gestion des ordinateurs](media/service-gateway-sso-kerberos/computer-management.png)

    1. Double-cliquez sur le groupe d’administrateurs local, puis sélectionnez **Ajouter** pour y ajouter votre utilisateur du service. Sélectionnez **Vérifier les noms** pour vérifier que vous avez entré le nom correctement. Sélectionnez **OK**.

1. Définissez l’utilisateur du service du serveur SAP BW en tant qu’utilisateur qui démarre le service du serveur SAP BW sur la machine serveur SAP BW.

    1. Ouvrez **Exécuter**, puis entrez **Services.msc**. Recherchez le service correspondant à votre instance du serveur d’applications SAP BW. Cliquez dessus avec le bouton droit, puis sélectionnez **Propriétés**.

        ![Capture d’écran de Services, avec l’option Propriétés en surbrillance](media/service-gateway-sso-kerberos/server-properties.png)

    1. Accédez à l’onglet **Connexion** et changez l’utilisateur par votre utilisateur du service SAP BW. Entrez le mot de passe de l’utilisateur, puis sélectionnez **OK**.

1. Connectez-vous à votre serveur dans SAP Logon et définissez les paramètres de profil suivants à l’aide de la transaction RZ10 :

    1. Définissez le paramètre de profil **snc/identity/as** sur *p:&lt;utilisateur du service SAP BW que vous avez créé&gt;* (par exemple, *p:BWServiceUser\@MYDOMAIN.COM*). Notez la présence de « p: » avant l’UPN de l’utilisateur du service. Ce n’est pas « p:CN= » comme lorsque vous utilisez Common Crypto Lib comme bibliothèque SNC.

    1. Définissez le paramètre de profil **snc/gssapi\_lib** sur le *&lt;chemin de gx64krb5.dll sur la machine serveur BW&gt;* . N’oubliez pas de placer la bibliothèque à un emplacement accessible par le serveur d’applications SAP BW.

    1. Définissez également les paramètres de profil supplémentaires suivants, en changeant les valeurs en fonction de vos besoins. Notez que les cinq dernières options permettent aux clients de se connecter au serveur SAP BW à l’aide de SAP Logon, sans avoir besoin de configurer un SNC.

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

1. Après avoir défini ces paramètres de profil, ouvrez la console de gestion SAP sur la machine serveur et redémarrez l’instance SAP BW. Si le serveur ne démarre pas, vérifiez que vous avez correctement défini les paramètres de profil. Pour plus d’informations sur les paramètres de profil, consultez la [documentation SAP](https://help.sap.com/saphelp_nw70ehp1/helpdata/en/e6/56f466e99a11d1a5b00000e835363f/frameset.htm). Vous pouvez également consulter les informations de dépannage plus loin dans cette section si vous rencontrez des problèmes.

### <a name="map-a-sap-bw-user-to-an-active-directory-user"></a>Mapper un utilisateur SAP BW à un utilisateur Active Directory

Si vous ne l’avez pas encore fait, mappez un utilisateur Active Directory à un utilisateur du serveur d’applications SAP BW et testez la connexion SSO dans SAP Logon.

1. Connectez-vous au serveur SAP BW à l’aide de SAP Logon. Exécutez la transaction SU01.

1. Dans le champ **User** (Utilisateur), entrez l’utilisateur SAP BW pour lequel vous souhaitez activer des connexions par authentification unique (dans la capture d’écran ci-dessous, les autorisations vont être définies pour BIUSER). Sélectionnez l’icône **Modifier** (image en forme de stylo) près de l’angle supérieur gauche de la fenêtre SAP Logon.

    ![Capture de l’écran de gestion des utilisateurs SAP BW](media/service-gateway-sso-kerberos/user-maintenance.png)

1. Sélectionnez l’onglet **SNC**. Dans la zone de texte « SNC name » (Nom SNC), entrez *p:&lt;utilisateur Active Directory&gt;@&lt;votre domaine&gt;* . Notez que « p: » doit absolument précéder l’UPN de l’utilisateur Active Directory. L’utilisateur Active Directory que vous indiquez doit appartenir à la personne ou à l’organisation pour laquelle vous souhaitez activer l’accès SSO au serveur d’applications SAP BW. Par exemple, si vous voulez activer l’accès SSO pour l’utilisateur *testuser\@TESTDOMAIN.COM*, entrez *p:testuser\@TESTDOMAIN.COM*.

    ![Capture de l’écran Maintain users (Gérer les utilisateurs) de SAP BW](media/service-gateway-sso-kerberos/maintain-users.png)

1. Sélectionnez l’icône **Enregistrer** (image de disquette) près de l’angle supérieur gauche de l’écran.

### <a name="test-sign-in-via-sso"></a>Tester la connexion par authentification unique

Vérifiez que vous pouvez vous connecter au serveur à l’aide SAP Logon via l’authentification unique en tant qu’utilisateur Active Directory pour lequel vous venez d’activer l’accès SSO.

1. En tant qu’utilisateur Active Directory pour lequel vous venez d’activer l’accès SSO, connectez-vous à une machine de votre domaine sur laquelle SAP Logon est installé. Lancez SAP Logon et créez une connexion.

1. Copiez la .dll `gsskrb5` que vous avez téléchargée précédemment à un emplacement sur la machine à laquelle vous venez de vous connecter. Définissez la variable d’environnement `SNC_LIB` sur le chemin absolu de cet emplacement.

1. Lancez SAP Logon et créez une connexion.

1. Dans l’écran **Create New System Entry** (Créer une entrée système), sélectionnez **User Specified System** (Système spécifié par l’utilisateur), puis sélectionnez **Next** (Suivant).

    ![Capture de l’écran Create New System Entry](media/service-gateway-sso-kerberos/new-system-entry.png)

1. Renseignez les informations appropriées dans l’écran suivant, y compris le serveur d’applications, le numéro d’instance et l’ID du système. Ensuite, sélectionnez **Finish** (Terminer).

1. Cliquez avec le bouton droit sur la nouvelle connexion, puis sélectionnez **Properties** (Propriétés). Sélectionnez l’onglet **Réseau**. Dans la zone de texte **SNC Name** (Nom SNC), entrez *p:&lt;UPN de l’utilisateur du service SAP BW&gt;* , par exemple, *p:BWServiceUser\@MYDOMAIN.COM*. Sélectionnez ensuite **OK**.

    ![Capture de l’écran System Entry Properties](media/service-gateway-sso-kerberos/system-entry-properties.png)

1. Double-cliquez sur la connexion que vous venez de créer pour tenter une connexion SSO à votre serveur SAP BW. Si cette connexion réussit, passez à l’étape suivante. Sinon, passez en revue les étapes antérieures dans ce document pour vous assurer de les avoir effectuées correctement, ou consultez la section de dépannage ci-après. Notez que si vous ne réussissez pas à vous connecter au serveur SAP BW par le biais de l’authentification unique dans ce contexte, vous ne pouvez pas non plus le faire dans le contexte de la passerelle.

### <a name="add-registry-entries-to-the-gateway-machine"></a>Ajouter des entrées de Registre à la machine de passerelle

Ajoutez les entrées de registre nécessaires au registre de l’ordinateur sur lequel la passerelle est installée, ainsi qu’aux ordinateurs destinés à se connecter à partir de Power BI Desktop. Voici les commandes à exécuter :

1. ```REG ADD HKLM\SOFTWARE\Wow6432Node\SAP\gsskrb5 /v ForceIniCredOK /t REG_DWORD /d 1 /f```

1. ```REG ADD HKLM\SOFTWARE\SAP\gsskrb5 /v ForceIniCredOK /t REG_DWORD /d 1 /f```

### <a name="add-a-new-sap-bw-application-server-data-source-to-the-power-bi-service-or-edit-an-existing-one"></a>Ajouter une nouvelle source de données du serveur d’applications SAP BW au service Power BI ou en modifier une existante

1. Dans la fenêtre de configuration de la source de données, entrez le **Nom d’hôte**, le **Numéro système** et l’**ID client** du serveur d’applications que vous utilisez pour vous connecter à votre serveur SAP BW à partir de Power BI Desktop.

1. Dans le champ **Nom du partenaire SNC**, entrez *p:&lt;SPN que vous avez associé à l’utilisateur du service SAP BW&gt;* . Par exemple, si le SPN est **SAP/BWServiceUser\@MYDOMAIN.COM**, entrez *p:SAP/BWServiceUser\@MYDOMAIN.COM* dans le champ **Nom du partenaire SNC**.

1. Comme bibliothèque SNC, sélectionnez **SNC\_LIB** ou **SNC\_LIB\_64**. Assurez-vous que **SNC\_LIB\_64** sur la machine de passerelle pointe vers gx64krb5.dll. Vous pouvez également sélectionner l’option « Personnalisé » et fournir le chemin d’accès absolu de gx64krb5.dll (sur la machine passerelle).

1. Cochez la case **Utiliser SSO via Kerberos pour les requêtes DirectQuery**, puis sélectionnez **Appliquer**. Si le test de la connexion échoue, vérifiez que vous avez correctement effectué les étapes d’installation et de configuration précédentes.

1. [Générer un rapport Power BI](service-gateway-sso-kerberos.md#run-a-power-bi-report)

## <a name="troubleshooting"></a>Résolution des problèmes

### <a name="troubleshoot-gx64krb5-configuration"></a>Résoudre les problèmes de configuration de gx64krb5

Si vous rencontrez des problèmes, suivez ces étapes pour corriger l’installation de gx64krb5 et les connexions par authentification unique.

* Examinez les journaux du serveur (…work\dev\_w0 sur la machine serveur) pour vous aider à résoudre les erreurs rencontrées au cours des étapes de configuration de gx64krb5. En particulier, cela est utile si le serveur SAP BW ne démarre pas après la modification des paramètres de profil.

* Si vous ne parvenez pas à démarrer le service SAP BW en raison d’un échec de connexion, il est possible que vous ayez indiqué un mauvais mot de passe durant la définition de l’utilisateur qui démarre le service SAP BW. Vérifiez le mot de passe en vous connectant à une machine dans votre environnement Active Directory en tant qu’utilisateur du service SAP BW.

* Si vous obtenez des erreurs indiquant que des informations d’identification de la source de données sous-jacente (par exemple, SQL Server) empêchent le démarrage du serveur, vérifiez que vous avez accordé à l’utilisateur du service l’accès à la base de données SAP BW.

* Vous pouvez obtenir le message suivant : *(GSS-API) La cible spécifiée est inconnue ou inaccessible.* Cela signifie généralement que vous avez spécifié un nom SNC incorrect. Veillez à utiliser « p: » uniquement, et pas « p:CN= » ou autre chose dans l’application cliente que l’UPN de l’utilisateur du service.

* Vous pouvez obtenir le message suivant : *(GSS-API) Un nom non valide a été fourni.* Vérifiez que vous avez spécifié « p: » dans la valeur du paramètre de profil d’identité SNC du serveur.

* Vous pouvez obtenir le message suivant : *(Erreur SNC) Le module spécifié est introuvable.* Cette erreur se produit généralement quand vous placez `gx64krb5.dll` à un emplacement dont l’accès requiert des privilèges élevés (droits d’administrateur).

### <a name="troubleshoot-gateway-connectivity-issues"></a>Résoudre les problèmes de connectivité de la passerelle

1. Consultez les journaux de la passerelle. Ouvrez l’application de configuration de la passerelle, puis sélectionnez **Diagnostics** et **Exporter les journaux**. Les erreurs les plus récentes apparaissent en bas des fichiers journaux que vous examinez.

    ![Capture d’écran de l’application Passerelle de données locale, avec l’option Diagnostics en surbrillance](media/service-gateway-sso-kerberos/gateway-diagnostics.png)

1. Activez le suivi de SAP BW et examinez les fichiers journaux générés. Différents types de traçage SAP BW sont disponibles (par exemple, le traçage CPIC). Pour plus d’informations, consultez la documentation SAP.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur la **Passerelle de données locale** et **DirectQuery**, consultez les ressources suivantes :

* [Qu’est-ce qu’une passerelle de données locale ?](/data-integration/gateway/service-gateway-onprem)
* [DirectQuery dans Power BI](desktop-directquery-about.md)
* [Sources de données prises en charge par DirectQuery](desktop-directquery-data-sources.md)
* [DirectQuery et SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery et SAP HANA](desktop-directquery-sap-hana.md)
