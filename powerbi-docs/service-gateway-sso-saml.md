---
title: Utiliser SAML pour l’authentification unique sur des sources de données locales
description: Configurez votre passerelle avec SAML (Security Assertion Markup Language) pour permettre l’authentification unique de Power BI sur des sources de données locales.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 09/16/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 75641468b52d4174779b9ddd03ed7aab27b6c5d0
ms.sourcegitcommit: 7a0ce2eec5bc7ac8ef94fa94434ee12a9a07705b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71100417"
---
# <a name="use-security-assertion-markup-language-saml-for-sso-from-power-bi-to-on-premises-data-sources"></a>Utiliser SAML (Security Assertion Markup Language) pour l’authentification unique de Power BI sur des sources de données locales

Utilisez [SAML (Security Assertion Markup Language)](https://www.onelogin.com/pages/saml) pour permettre une connectivité d’authentification unique fluide. L’activation de SSO permet aux rapports et tableaux de bord Power BI d’actualiser les données à partir des sources locales plus facilement.

## <a name="supported-data-sources"></a>Sources de données prises en charge

Nous prenons en charge SAP HANA avec SAML. Pour plus d’informations sur la configuration de l’authentification unique pour SAP HANA à l’aide de SAML, consultez la rubrique [SAML SSO for BI Platform to HANA](https://wiki.scn.sap.com/wiki/display/SAPHANA/SAML+SSO+for+BI+Platform+to+HANA) dans la documentation de SAP HANA.

Nous prenons en charge des sources de données supplémentaires avec [Kerberos](service-gateway-sso-kerberos.md).

Notez que pour HANA, il est **fortement** recommandé d’activer le chiffrement avant d’établir une connexion SSO SAML (autrement dit, vous devez configurer le serveur HANA pour qu’il accepte les connexions chiffrées et également configurer la passerelle pour qu’elle utilise le chiffrement lors des communications avec votre serveur HANA). Le pilote ODBC HANA **n’est pas** en mesure de chiffrer les assertions SAML par défaut et, si le chiffrement n’est pas activé, l’assertion SAML est envoyée à partir de la passerelle au serveur HANA « en clair », pouvant alors être interceptée et réutilisée par des tiers. Pour obtenir des instructions sur l’activation du chiffrement pour Hana à l’aide de la bibliothèque OpenSSL, consultez [Activer le chiffrement pour SAP HANA](/power-bi/desktop-sap-hana-encryption).

## <a name="configuring-the-gateway-and-data-source"></a>Configuration de la passerelle et de la source de données

Pour utiliser SAML, vous devez établir une relation d’approbation entre le ou les serveurs HANA pour lesquels vous souhaitez activer l’authentification unique et la passerelle, qui sert de fournisseur d’identité SAML (IdP) dans ce scénario. Pour établir cette relation, vous pouvez, par exemple, importer le certificat x509 du fournisseur d’identité de la passerelle dans le magasin d’approbations du ou des serveurs HANA ou faire signer le certificat X509 de la passerelle par une autorité de certification racine approuvée par le ou les serveurs HANA. Nous décrivons cette dernière approche dans ce guide, mais vous pouvez utiliser une autre approche si elle est plus pratique.

Notez également que bien que ce guide utilise OpenSSL comme fournisseur de chiffrement du serveur HANA, il est recommandé d’utiliser la bibliothèque de chiffrement SAP (également appelé CommonCryptoLib ou sapcrypto) au lieu d’OpenSSL pour effectuer les étapes de configuration correspondant à l’établissement de la relation d’approbation. Pour plus d’informations, reportez-vous à la documentation officielle de SAP.

Les étapes suivantes décrivent comment établir une relation d’approbation entre un serveur HANA et le fournisseur d’identité de la passerelle en signant le certificat X509 du fournisseur d’identité de la passerelle à l’aide d’une autorité de certification racine approuvée par le serveur HANA. Vous allez créer cette autorité de certification racine.

1. Créez la clé privée et le certificat X509 de l’autorité de certification racine. Par exemple, pour créer la clé privée et le certificat X509 de l’autorité de certification racine dans le format .pem :

   ```
   openssl req -new -x509 -newkey rsa:2048 -days 3650 -sha256 -keyout CA_Key.pem -out CA_Cert.pem -extensions v3_ca
   ```

    Vérifiez que le certificat de l’autorité de certification racine est correctement sécurisé. S’il est obtenu par des tiers, il peut être utilisé pour accéder de manière non autorisé au serveur HANA. 

    Ajoutez le certificat (par exemple, CA_Cert.pem) au magasin d’approbations du serveur HANA afin que celui-ci approuve les certificats signés par l’autorité de certification racine que vous venez de créer. Vous pouvez connaître l’emplacement du magasin d’approbations de votre serveur HANA en examinant le paramètre de configuration **ssltruststore**. Si vous avez suivi la documentation SAP couvrant la configuration d’OpenSSL, il se peut que votre serveur HANA approuve déjà une autorité de certification racine réutilisable. Pour plus d’informations, consultez [How to Configure Open SSL for SAP HANA Studio to SAP HANA Server](https://archive.sap.com/documents/docs/DOC-39571) (Guide pratique pour configurer Open SSL pour les communications entre SAP HANA Studio et le serveur SAP HANA). Si vous souhaitez activer l’authentification unique SAML pour plusieurs serveurs HANA, vérifiez que chacun des serveurs fait confiance à cette autorité de certification racine.

1. Créez le certificat X509 du fournisseur d’identité de la passerelle. Par exemple, pour créer une demande de signature de certificat (IdP_Req.pem) et une clé privée (IdP_Key.pem) qui sont valides pendant un an, exécutez la commande suivante :

   ```
   openssl req -newkey rsa:2048 -days 365 -sha256 -keyout IdP_Key.pem -out IdP_Req.pem -nodes
   ```

   Signez la demande de signature de certificat à l’aide de l’autorité de certification racine dont vous avez configuré l’approbation par vos serveurs HANA. Par exemple, pour signer IdP_Req.pem à l’aide de CA_Cert.pem et CA_Key.pem (le certificat et la clé de l’autorité de certification racine), exécutez la commande suivante :

   ```
   openssl x509 -req -days 365 -in IdP_Req.pem -sha256 -extensions usr_cert -CA CA_Cert.pem -CAkey CA_Key.pem -CAcreateserial -out IdP_Cert.pem
   ```

Le certificat de fournisseur d’identité obtenu est valide pendant un an (voir l’option -days). Maintenant, importez le certificat de votre fournisseur d’identité dans HANA Studio pour créer un fournisseur d’identité SAML.

1. Dans SAP HANA Studio, cliquez avec le bouton droit sur votre serveur SAP HANA, puis accédez à **Security** > **Open Security Console** (Ouvrir la console de sécurité) > **SAML Identity Provider** (Fournisseur d’identité SAML) > **OpenSSL Cryptographic Library** (Bibliothèque de chiffrement OpenSSL).

    ![Fournisseurs d’identité](media/service-gateway-sso-saml/identity-providers.png)

1. Sélectionnez **Import**, accédez à IdP_Cert.pem, puis importez-le.

1. Dans SAP HANA Studio, sélectionnez le dossier **Security**.

    ![Dossier Security](media/service-gateway-sso-saml/security-folder.png)

1. Développez **Users**, puis sélectionnez l’utilisateur auquel vous souhaitez associer votre utilisateur Power BI.

1. Sélectionnez **SAML**, puis **Configure**.

    ![Configurer SAML](media/service-gateway-sso-saml/configure-saml.png)

1. Sélectionnez le fournisseur d’identité que vous avez créé à l’étape 2. Pour **External Identity**, entrez l’UPN de l’utilisateur Power BI (en général, l’adresse e-mail avec laquelle l’utilisateur se connecte à Power BI), puis sélectionnez **Add**. Notez que si vous avez configuré votre passerelle pour utiliser l’option de configuration *ADUserNameReplacementProperty*, vous devez entrer la valeur qui remplacera l’UPN d’origine de l’utilisateur Power BI. Par exemple, si vous définissez *ADUserNameReplacementProperty* avec la valeur **SAMAccountName**, vous devez entrer le **SAMAccountName** de l’utilisateur.

    ![Sélectionner le fournisseur d’identité](media/service-gateway-sso-saml/select-identity-provider.png)

Le certificat et l’identité de la passerelle étant maintenant configurés, convertissez le certificat dans un format pfx et configurez la machine de passerelle afin qu’elle utilise le certificat.

1. Convertissez le certificat au format pfx en exécutant la commande suivante. Notez que cette commande définit « root » comme mot de passe du fichier pfx.

    ```
    openssl pkcs12 -export -out samltest.pfx -in IdP_Cert.pem -inkey IdP_Key.pem -passin pass:root -passout pass:root
    ```

1. Copiez le fichier pfx sur la machine de passerelle :

    1. Double-cliquez sur samltest.pfx, puis sélectionnez **Ordinateur local** > **Suivant**.

    1. Entrez le mot de passe, puis sélectionnez **Suivant**.

    1. Sélectionnez **Placer tous les certificats dans le magasin suivant**, puis sélectionnez **Parcourir** > **Personnel** > **OK**.

    1. Sélectionnez **Suivant**, puis **Terminer**.

    ![Importer le certificat](media/service-gateway-sso-saml/import-certificate.png)

1. Octroyez au compte de service de passerelle l’accès à la clé privée du certificat :

    1. Sur la machine de passerelle, exécutez la console MMC (Microsoft Management Console).

        ![Exécuter MMC](media/service-gateway-sso-saml/run-mmc.png)

    1. Sous **Fichier**, sélectionnez **Ajouter/Supprimer un composant logiciel enfichable**.

        ![Ajouter un composant logiciel enfichable](media/service-gateway-sso-saml/add-snap-in.png)

    1. Sélectionnez **Certificats** > **Ajouter**, puis sélectionnez **Un compte d’ordinateur** > **Suivant**.

    1. Sélectionnez **Ordinateur local** > **Terminer** > **OK**.

    1. Développez **Certificats** > **Personnel** > **Certificats**, puis recherchez le certificat.

    1. Cliquez avec le bouton droit sur le certificat, puis accédez à **Toutes les tâches** > **Gérer les clés privées**.

        ![Gérer les clés privées](media/service-gateway-sso-saml/manage-private-keys.png)

    1. Ajoutez le compte de service de passerelle à la liste. Par défaut, le compte est **NT SERVICE\PBIEgwService**. Vous pouvez déterminer le compte qui exécute le service de passerelle en exécutant **services.msc** et en recherchant **Service de passerelle de données locale**.

        ![Service de passerelle](media/service-gateway-sso-saml/gateway-service.png)

Enfin, suivez les étapes ci-après pour ajouter l’empreinte de certificat à la configuration de la passerelle.

1. Exécutez la commande PowerShell suivante pour lister les certificats présents sur votre ordinateur.

    ```powershell
    Get-ChildItem -path cert:\LocalMachine\My
    ```

1. Copiez l’empreinte du certificat que vous avez créé.

1. Accédez au répertoire de la passerelle, qui, par défaut, est C:\Program Files\On-premises data gateway.

1. Ouvrez PowerBI.DataMovement.Pipeline.GatewayCore.dll.config, puis recherchez la section *SapHanaSAMLCertThumbprint*. Collez l’empreinte que vous avez copiée.

1. Redémarrez le service de passerelle.

## <a name="running-a-power-bi-report"></a>Exécution d’un rapport Power BI

Vous pouvez désormais utiliser la page **Gérer la passerelle** dans Power BI pour configurer la source de données SAP HANA, puis, sous ses **Paramètres avancés**, activer l’authentification unique. Ensuite, vous pouvez publier des rapports et des jeux de données liés à cette source de données.

![Paramètres avancés](media/service-gateway-sso-saml/advanced-settings.png)

## <a name="troubleshooting"></a>Résolution des problèmes

Après avoir configuré l’authentification unique, vous risquez de voir l’erreur suivante dans le portail Power BI : « Impossible d’utiliser les informations d’identification fournies pour la source SapHana. » Cette erreur indique que les informations d’identification SAML ont été refusées par SAP HANA.

Les traces d’authentification côté serveur fournissent des informations détaillées pour résoudre les problèmes d’informations d’identification sur SAP HANA. Suivez ces étapes pour configurer le traçage de votre serveur SAP HANA.

1. Sur le serveur SAP HANA, activez la trace d’authentification en exécutant la requête suivante.

    ```
    ALTER SYSTEM ALTER CONFIGURATION ('indexserver.ini', 'SYSTEM') set ('trace', 'authentication') = 'debug' with reconfigure 
    ```

1. Reproduisez le problème que vous avez rencontré.

1. Dans HANA Studio, ouvrez la console d’administration et accédez à l’onglet **Fichiers de diagnostic**.

1. Ouvrez la dernière trace du serveur d’index et recherchez SAMLAuthenticator.cpp.

    Vous devriez trouver un message d’erreur détaillé qui indique la cause racine, comme dans l’exemple suivant.

    ```
    [3957]{-1}[-1/-1] 2018-09-11 21:40:23.815797 d Authentication   SAMLAuthenticator.cpp(00091) : Element '{urn:oasis:names:tc:SAML:2.0:assertion}Assertion', attribute 'ID': '123123123123123' is not a valid value of the atomic type 'xs:ID'.
    [3957]{-1}[-1/-1] 2018-09-11 21:40:23.815914 i Authentication   SAMLAuthenticator.cpp(00403) : No valid SAML Assertion or SAML Protocol detected
    ```

1. Une fois que le problème est résolu, désactivez la trace d’authentification en exécutant la requête suivante.

    ```
    ALTER SYSTEM ALTER CONFIGURATION ('indexserver.ini', 'SYSTEM') UNSET ('trace', 'authentication');
    ```

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur la **Passerelle de données locale** et **DirectQuery**, consultez les ressources suivantes :

* [Qu’est-ce qu’une passerelle de données locale ?](/data-integration/gateway/service-gateway-onprem)
* [DirectQuery dans Power BI](desktop-directquery-about.md)
* [Sources de données prises en charge par DirectQuery](desktop-directquery-data-sources.md)
* [DirectQuery et SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery et SAP HANA](desktop-directquery-sap-hana.md)
