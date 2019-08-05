---
title: Création du certificat SSL
description: Instructions de contournement pour la création manuelle des certificats pour un serveur de développement
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: tutorial
ms.date: 06/18/2019
ms.openlocfilehash: 3287e8a7eb1c36c3f0d8a1fc24faa0442de2dddf
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425433"
---
# <a name="creating-ssl-certificate"></a>Création du certificat SSL

Exécutez la commande suivante pour générer le certificat à l’aide de la cmdlet PowerShell New-SelfSignedCertificate sur Windows 8 ou une version ultérieure.

L’outil requiert l’installation d’OpenSSL pour **Windows** **7**. L’utilitaire `openssll` doit être disponible à partir de la ligne de commande.

Pour installer OpenSSL, visitez [https://www.openssl.org](https://www.openssl.org) ou [https://wiki.openssl.org/index.php/Binaries](https://wiki.openssl.org/index.php/Binaries)

```cmd
pbiviz --create-cert
```

## <a name="create-certificate-mac-os-x"></a>Créer un certificat (Mac OS X)

En général, les utilitaires OpenSSL sont disponibles dans les systèmes d’exploitation Linux ou Mac OS X.

Sinon, vous pouvez les installer depuis

le gestionnaire de package *Brew*

```cmd
brew install openssl
brew link openssl --force
```

ou à l’aide de *MacPorts*

```cmd
sudo port install openssl
```

Après l’installation d’OpenSSL pour la génération d’un nouveau certificat, appelez :

```cmd
pbiviz --create-cert
```

## <a name="create-certificate-linux"></a>Créer un certificat (Linux)

Les utilitaires OpenSSL ne sont pas disponibles pour votre système d’exploitation Linux. Vous pouvez les installer à l’aide des commandes suivantes.

Pour le gestionnaire de package *APT* :

```cmd
sudo apt-get install openssl
```

Pour *Yellowdog Updater* :

```cmd
yum install openssl
```

Pour le *gestionnaire de package Redhat* :

```cmd
rpm install openssl
```

Si OpenSSl est déjà disponible pour votre système d’exploitation, appelez

```cmd
pbiviz --create-cert
```

pour générer un nouveau certificat.

Sinon, obtenez-le à partir [https://www.openssl.org](https://www.openssl.org) ou [https://wiki.openssl.org/index.php/Binaries](https://wiki.openssl.org/index.php/Binaries)

## <a name="generate-certificate-manually"></a>Générer un certificat manuellement

Vous pouvez spécifier vos certificats générés avec n’importe quel outil.

Si OpenSSL est installé sur votre système, vous pouvez exécuter la commande suivante pour générer un nouveau certificat

```cmd
openssl req -x509 -newkey rsa:4096 -keyout PowerBICustomVisualTest_private.key -out PowerBICustomVisualTest_public.crt -days 365
```

Généralement, les certificats de serveur web PowerBI-visuals-tools se trouvent dans

```cmd
%appdata%\npm\node_modules\PowerBI-visuals-tools\certs
```

pour l’instance globale des outils

ou

```cmd
<custom visual project root>\node_modules\PowerBI-visuals-tools\certs
```

pour l’instance locale des outils.

Vous devriez enregistrer le fichier de certificat comme `PowerBICustomVisualTest_public.cer` et la clé privée comme `PowerBICustomVisualTest_public.key` si vous utilisez le format PEM.
Enregistrez le fichier comme `PowerBICustomVisualTest_public.pfx` si vous utilisez le format PFX.

Si votre fichier de certificat PFX nécessite une phrase secrète, vous devez la spécifier dans

```cmd
\PowerBI-visuals-tools\config.json
```

au niveau du serveur :

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
