---
title: Utiliser SAML sur la passerelle locale pour l’authentification unique (SSO) de Power BI à des sources de données locales
description: Configurez votre passerelle avec SAML (Security Assertion Markup Language) pour permettre l’authentification unique (SSO) de Power BI sur des sources de données locales.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-gateways
ms.topic: conceptual
ms.date: 10/10/2018
LocalizationGroup: Gateways
ms.openlocfilehash: 4fbfa38bd235d37fea730bda8d200e97530f0ce9
ms.sourcegitcommit: 2c4a075fe16ccac8e25f7ca0b40d404eacb49f6d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2018
ms.locfileid: "49474383"
---
# <a name="use-security-assertion-markup-language-saml-for-single-sign-on-sso-from-power-bi-to-on-premises-data-sources"></a>Utiliser SAML (Security Assertion Markup Language) pour l’authentification unique (SSO) de Power BI sur des sources de données locales

Utilisez [SAML (Security Assertion Markup Language)](https://www.onelogin.com/pages/saml) pour permettre une connectivité d’authentification unique fluide. L’activation de SSO permet aux rapports et tableaux de bord Power BI d’actualiser les données à partir des sources locales plus facilement.

## <a name="supported-data-sources"></a>Sources de données prises en charge

Nous prenons en charge SAP HANA avec SAML. Pour plus d’informations sur la configuration de l’authentification unique pour SAP HANA à l’aide de SAML, consultez la rubrique [SAML SSO for BI Platform to HANA](https://wiki.scn.sap.com/wiki/display/SAPHANA/SAML+SSO+for+BI+Platform+to+HANA) dans la documentation de SAP HANA.

Nous prenons en charge des sources de données supplémentaires avec [Kerberos](service-gateway-sso-kerberos.md).

## <a name="configuring-the-gateway-and-data-source"></a>Configuration de la passerelle et de la source de données

Pour utiliser SAML, vous devez générer un certificat pour le fournisseur d’identité SAML, puis associer un utilisateur Power BI à l’identité.

1. Générez un certificat. Vérifiez que vous utilisez le nom de domaine complet du serveur SAP HANA quand vous renseignez le *nom commun*. Le certificat expire au bout de 365 jours.

    ```
    openssl req -newkey rsa:2048 -nodes -keyout samltest.key -x509 -days 365 -out samltest.crt
    ```

1. Dans SAP HANA Studio, cliquez avec le bouton droit sur votre serveur SAP HANA, puis accédez à **Security** > **Open Security Console** (Ouvrir la console de sécurité) > **SAML Identity Provider** (Fournisseur d’identité SAML) > **OpenSSL Cryptographic Library** (Bibliothèque de chiffrement OpenSSL).

1. Sélectionnez **Import**, puis accédez à samltest.crt et importez-le.

    ![Fournisseurs d’identité](media/service-gateway-sso-saml/identity-providers.png)

1. Dans SAP HANA Studio, sélectionnez le dossier **Security**.

    ![Dossier Security](media/service-gateway-sso-saml/security-folder.png)

1. Développez **Users**, puis sélectionnez l’utilisateur auquel vous souhaitez associer votre utilisateur Power BI.

1. Sélectionnez **SAML**, puis **Configure**.

    ![Configurer SAML](media/service-gateway-sso-saml/configure-saml.png)

1. Sélectionnez le fournisseur d’identité que vous avez créé à l’étape 2. Pour **External Identity** (Identité externe), entrez l’UPN de l’utilisateur Power BI, puis sélectionnez **Add** (Ajouter).

    ![Sélectionner le fournisseur d’identité](media/service-gateway-sso-saml/select-identity-provider.png)

Ensuite, validez la configuration avec une *assertion SAML* en utilisant l’[outil xmlsec1](http://sgros.blogspot.com/2013/01/signing-xml-document-using-xmlsec1.html).

1. Enregistrez l’assertion ci-dessous sous le nom assertion-template.xml. Remplacez \<MyUserId\> par l’UPN de l’utilisateur Power BI que vous avez entré à l’étape 7.

    ```xml
    <?xml version="1.0" encoding="UTF-8" ?>
    <saml2:Assertion ID="Assertion12345789" IssueInstant="2015-07-16T04:47:49.858Z" Version="2.0" xmlns:saml2="urn:oasis:names:tc:SAML:2.0:assertion">
      <saml2:Issuer></saml2:Issuer> 
      <Signature xmlns="http://www.w3.org/2000/09/xmldsig#">
        <SignedInfo>
          <CanonicalizationMethod Algorithm="http://www.w3.org/TR/2001/REC-xml-c14n-20010315"/>
          <SignatureMethod Algorithm="http://www.w3.org/2000/09/xmldsig#rsa-sha1"/>
          <Reference URI="">
            <Transforms>
              <Transform Algorithm="http://www.w3.org/2000/09/xmldsig#enveloped-signature"/>
              <Transform Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"/>
            </Transforms>
            <DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1"/>
            <DigestValue />
          </Reference>
        </SignedInfo>
        <SignatureValue />
        <KeyInfo>
          <X509Data />
        </KeyInfo>
      </Signature>
      <saml2:Subject>
        <saml2:NameID Format="urn:oasis:names:tc:SAML:1.1:nameid-format:unspecified"><MyUserId></saml2:NameID>
      </saml2:Subject>
      <saml2:Conditions NotBefore="2010-01-01T00:00:00Z" NotOnOrAfter="2050-01-01T00:00:00Z"/>
    </saml2:Assertion>
    ```

1. Exécutez la commande suivante. saltest.Key et samltest.crt sont la clé et le certificat que vous avez générés à l’étape 1.

    ```
    xmlsec1 --sign --privkey-pem samltest.key, samltest.crt --output signed.xml assertion-template.xml
    ```

1. Dans SAP HANA Studio, ouvrez une fenêtre de console SQL et exécutez la commande suivante. Remplacez \<SAMLAssertion\> par le contenu XML issu de l’étape précédente.

    ```SQL
    CONNECT WITH SAML ASSERTION '<SAMLAssertion>'
    ```

Si la requête réussit, cela signifie que la configuration de l’authentification unique pour SAP HANA avec SAML s’est bien passée.

Le certificat et l’identité étant correctement configurés, vous devez convertir le certificat dans un format pfx et configurer la machine de passerelle afin qu’elle utilise le certificat.

1. Convertissez le certificat au format pfx en exécutant la commande suivante.

    ```
    openssl pkcs12 -inkey samltest.key -in samltest.crt -export -out samltest.pfx
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

    1. Ajoutez le compte de service de passerelle à la liste. Par défaut, le compte est **NT SERVICE\PBIEgwService**. Vous pouvez déterminer quel compte exécute le service de passerelle en exécutant **services.msc** et en recherchant **Service de passerelle de données locale**.

        ![Service de passerelle](media/service-gateway-sso-saml/gateway-service.png)

Enfin, suivez les étapes ci-après pour ajouter l’empreinte de certificat à la configuration de la passerelle.

1. Exécutez la commande PowerShell suivante pour lister les certificats présents sur votre ordinateur.

    ```powershell
    Get-ChildItem -path cert:\LocalMachine\My
    ```
1. Copiez l’empreinte du certificat que vous avez créé.

1. Accédez au répertoire de la passerelle, qui, par défaut, est C:\Program Files\On-premises data gateway.

1. Ouvrez PowerBI.DataMovement.Pipeline.GatewayCore.dll.config, puis recherchez la section \*SapHanaSAMLCertThumbprint\*. Collez l’empreinte que vous avez copiée.

1. Redémarrez le service de passerelle.

## <a name="running-a-power-bi-report"></a>Exécution d’un rapport Power BI

Vous pouvez désormais utiliser la page **Gérer la passerelle** dans Power BI pour configurer la source de données, puis, sous ses **Paramètres avancés**, activer l’authentification unique. Ensuite, vous pouvez publier des rapports et des jeux de données liés à cette source de données.

![Paramètres avancés](media/service-gateway-sso-saml/advanced-settings.png)

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur la **Passerelle de données locale** et **DirectQuery**, voir les ressources suivantes :

* [Passerelle de données locale](service-gateway-onprem.md)
* [DirectQuery dans Power BI](desktop-directquery-about.md)
* [Sources de données prises en charge par DirectQuery](desktop-directquery-data-sources.md)
* [DirectQuery et SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery et SAP HANA](desktop-directquery-sap-hana.md)