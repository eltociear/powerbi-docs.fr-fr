---
title: Créer un certificat SSL
description: Instructions de contournement pour la création manuelle des certificats pour un serveur de développement
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: tutorial
ms.date: 06/18/2019
ms.openlocfilehash: c96489e6577f4887d2f22a9e81ea50f46cc9a5a3
ms.sourcegitcommit: e2de2e8b8e78240c306fe6cca820e5f6ff188944
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71194416"
---
# <a name="create-an-ssl-certificate"></a>Créer un certificat SSL

Cet article explique comment créer un certificat SSL.

Pour générer le certificat à l’aide de l’applet de commande PowerShell `New-SelfSignedCertificate` sur Windows 8 ou version ultérieure, exécutez la commande suivante :

```cmd
pbiviz --create-cert
```

L’outil nécessite l’installation d’OpenSSL pour Windows 7. L’utilitaire OpenSSL doit être disponible à partir de la ligne de commande.

Pour installer OpenSSL, accédez au site [OpenSSL](https://www.openssl.org) ou [OpenSSL Binaries](https://wiki.openssl.org/index.php/Binaries).



## <a name="create-a-certificate-mac-os-x"></a>Créer un certificat (Mac OS X)

En règle générale, l’utilitaire OpenSSL est disponible dans le système d’exploitation Linux ou Mac OS X.

Vous pouvez également l’installer en exécutant l’une des commandes suivantes :
* À partir du gestionnaire de package *Brew* :

    ```cmd
    brew install openssl
    brew link openssl --force
    ```

* À l’aide de *MacPorts* :

    ```cmd
    sudo port install openssl
    ```

Après avoir installé l’utilitaire OpenSSL pour la génération d’un nouveau certificat, exécutez la commande suivante :

```cmd
pbiviz --create-cert
```

## <a name="create-a-certificate-linux"></a>Créer un certificat (Linux)

Si l’utilitaire OpenSSL n’est pas disponible dans votre système d’exploitation Linux, vous pouvez l’installer à l’aide de l’une des commandes suivantes :

* Pour le gestionnaire de package *APT* :

    ```cmd
    sudo apt-get install openssl
    ```

* Pour *Yellowdog Updater* :

    ```cmd
    yum install openssl
    ```

* Pour le *gestionnaire de package Redhat* :

    ```cmd
    rpm install openssl
    ```

Si l’utilitaire OpenSSL est déjà disponible dans votre système d’exploitation, générez un nouveau certificat en exécutant la commande suivante :

```cmd
pbiviz --create-cert
```

Vous pouvez aussi vous procurer l’utilitaire OpenSSL en accédant au site [OpenSSL](https://www.openssl.org) ou [OpenSSL Binaries](https://wiki.openssl.org/index.php/Binaries).

## <a name="generate-the-certificate-manually"></a>Générer le certificat manuellement

Vous pouvez spécifier que vos certificats soient générés avec n’importe quel outil.

Si l’utilitaire OpenSSL est déjà installé sur votre système, générez un nouveau certificat en exécutant les commandes suivantes :

```cmd
openssl req -x509 -newkey rsa:4096 -keyout PowerBICustomVisualTest_private.key -out PowerBICustomVisualTest_public.crt -days 365
```

Vous pouvez généralement trouver les certificats de serveur web PowerBI-visuals-tools en exécutant l’une des commandes suivantes :

* Pour l’instance globale des outils :

    ```cmd
    %appdata%\npm\node_modules\PowerBI-visuals-tools\certs
    ```

* Pour l’instance locale des outils :

    ```cmd
    <custom visual project root>\node_modules\PowerBI-visuals-tools\certs
    ```

Si vous utilisez le format PEM, enregistrez le fichier de certificat en tant que *PowerBICustomVisualTest_public.crt*, puis enregistrez PrivateKey en tant que *PowerBICustomVisualTest_public.key*.

Si vous utilisez le format PFX, enregistrez le fichier de certificat en tant que *PowerBICustomVisualTest_public.pfx*.

Si votre fichier de certificat PFX nécessite une phrase secrète, effectuez les étapes suivantes :
1. Dans le fichier de configuration, spécifiez :

    ```cmd
    \PowerBI-visuals-tools\config.json
    ```

1. Dans la section `server`, spécifiez la phrase secrète en remplaçant l’espace réservé « *YOUR PASSPHRASE* » :

    ```cmd
    "server":{
        "root":"webRoot",
        "assetsRoute":"/assets",
        "privateKey":"certs/PowerBICustomVisualTest_private.key",
        "certificate":"certs/PowerBICustomVisualTest_public.crt",
        "pfx":"certs/PowerBICustomVisualTest_public.pfx",
        "port":"8080",
        "passphrase":"YOUR PASSPHRASE"
    }
    ```
