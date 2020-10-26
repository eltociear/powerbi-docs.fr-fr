---
title: Créer des certificats SSL pour les visuels Power BI
description: Découvrez comment générer des certificats SSL à l’aide des outils visuels Power BI sur Windows, Mac ou Linux, ou manuellement.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 05/08/2020
ms.openlocfilehash: f6f458d2fe82668074d7cfb046cb5a72afa35c38
ms.sourcegitcommit: 50b21718a167c2b131313b4135c8034c6f027597
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/14/2020
ms.locfileid: "92048783"
---
# <a name="create-an-ssl-certificate"></a>Créer un certificat SSL

Cet article explique comment générer et installer des certificats de protocole SSL pour les visuels Power BI.

Pour les procédures Windows, macOS X et Linux, vous devez avoir installé le package d’outils visuels Power BI **pbiviz**. Pour plus d’informations, consultez [Configurer votre environnement pour développer un visuel Power BI](./environment-setup.md). 

## <a name="create-a-certificate-on-windows"></a>Créer un certificat sur Windows

Pour générer un certificat à l’aide de l’applet de commande PowerShell `New-SelfSignedCertificate` sur Windows 8 ou version ultérieure, exécutez la commande suivante :

```powershell
pbiviz --install-cert
```

Pour Windows 7, l’outil `pbiviz` nécessite la disponibilité de l’utilitaire OpenSSL à partir de la ligne de commande. Pour installer OpenSSL, accédez à [OpenSSL](https://www.openssl.org) ou [OpenSSL Binaries](https://wiki.openssl.org/index.php/Binaries).

Pour plus d’informations et pour obtenir des instructions sur l’installation d’un certificat, consultez [Créer et installer un certificat pour Windows](./environment-setup.md#create-and-install-a-certificate).

## <a name="create-a-certificate-on-macos-x"></a>Créer un certificat sur macOS X

L’utilitaire OpenSSL est généralement disponible dans le système d’exploitation macOS X.

Vous pouvez également installer l’utilitaire OpenSSL en exécutant l’une des commandes suivantes :

- À partir du gestionnaire de package *Brew* :
  
  ```cmd
  brew install openssl
  brew link openssl --force
  ```

- À l’aide de *MacPorts* :
  
  ```cmd
  sudo port install openssl
  ```

Après avoir installé l’utilitaire OpenSSL pour la génération d’un nouveau certificat, exécutez la commande suivante :

```cmd
pbiviz --install-cert
```

Pour plus d’informations et pour obtenir des instructions, consultez l’onglet OS X dans [Créer et installer un certificat](./environment-setup.md#create-and-install-a-certificate).

## <a name="create-a-certificate-on-linux"></a>Créer un certificat sur Linux

L’utilitaire OpenSSL est généralement disponible dans le système d’exploitation Linux.

Avant de commencer, exécutez les commandes suivantes pour vous assurer que `openssl` et `certutil` sont installés :

```sh
which openssl
which certutil
```

Si `openssl` et `certutil` ne sont pas installés, installez les utilitaires `openssl` et `libnss3`.

### <a name="create-the-ssl-configuration-file"></a>Créer le fichier de configuration SSL

Créez un fichier */tmp/openssl.cnf* qui contient le texte suivant :

```
authorityKeyIdentifier=keyid,issuer
basicConstraints=CA:FALSE
keyUsage = digitalSignature, nonRepudiation, keyEncipherment, dataEncipherment
subjectAltName = @alt_names

[ alt_names ]
DNS.1=localhost
```

### <a name="generate-root-certificate-authority"></a>Générer l’autorité de certification racine

Pour générer une autorité de certification racine (CA) pour signer les certificats locaux, exécutez les commandes suivantes :

```sh
touch $HOME/.rnd
openssl req -x509 -nodes -new -sha256 -days 1024 -newkey rsa:2048 -keyout /tmp/local-root-ca.key -out /tmp/local-root-ca.pem -subj "/C=US/CN=Local Root CA/O=Local Root CA"
openssl x509 -outform pem -in /tmp/local-root-ca.pem -out /tmp/local-root-ca.crt
```

### <a name="generate-a-certificate-for-localhost"></a>Générer un certificat pour localhost 

Pour générer un certificat pour `localhost` à l’aide de l’autorité de certification générée et *openssl.cnf*, exécutez les commandes suivantes :

```sh
PBIVIZ=`which pbiviz`
PBIVIZ=`dirname $PBIVIZ`
PBIVIZ="$PBIVIZ/../lib/node_modules/powerbi-visuals-tools/certs"
# Make sure that $PBIVIZ contains the correct certificate directory path. ls $PBIVIZ should list 'blank' file.
openssl req -new -nodes -newkey rsa:2048 -keyout $PBIVIZ/PowerBIVisualTest_private.key -out $PBIVIZ/PowerBIVisualTest.csr -subj "/C=US/O=PowerBI Visuals/CN=localhost"
openssl x509 -req -sha256 -days 1024 -in $PBIVIZ/PowerBIVisualTest.csr -CA /tmp/local-root-ca.pem -CAkey /tmp/local-root-ca.key -CAcreateserial -extfile /tmp/openssl.cnf -out $PBIVIZ/PowerBIVisualTest_public.crt
```

### <a name="add-root-certificates"></a>Ajouter des certificats racines

Pour ajouter un certificat racine à la base de données du navigateur Chrome, exécutez :

```sh
certutil -A -n "Local Root CA" -t "CT,C,C" -i /tmp/local-root-ca.pem -d sql:$HOME/.pki/nssdb
```

Pour ajouter un certificat racine à la base de données du navigateur Mozilla Firefox, exécutez :

```sh
for certDB in $(find $HOME/.mozilla* -name "cert*.db")
do
certDir=$(dirname ${certDB});
certutil -A -n "Local Root CA" -t "CT,C,C" -i /tmp/local-root-ca.pem -d sql:${certDir}
done
```

Pour ajouter un certificat racine à l’ensemble du système, exécutez :

```sh
sudo cp /tmp/local-root-ca.pem /usr/local/share/ca-certificates/
sudo update-ca-certificates
```

### <a name="remove-root-certificates"></a>Supprimer des certificats racines

Pour supprimer un certificat racine, exécutez :

```sh
sudo rm /usr/local/share/ca-certificates/local-root-ca.pem
sudo update-ca-certificates --fresh
```

## <a name="generate-a-certificate-manually"></a>Générer un certificat manuellement

Vous pouvez également générer un certificat SSL manuellement à l’aide d’OpenSSL. Vous pouvez spécifier n’importe quel outil pour générer vos certificats.

Si l’utilitaire OpenSSL est déjà installé, générez un nouveau certificat en exécutant :

```cmd
openssl req -x509 -newkey rsa:4096 -keyout PowerBIVisualTest_private.key -out PowerBIVisualTest_public.crt -days 365
```

Vous pouvez généralement trouver les certificats de serveur web `PowerBI-visuals-tools` en exécutant l’une des commandes suivantes :

- Pour l’instance globale des outils :
  
  ```cmd
  %appdata%\npm\node_modules\PowerBI-visuals-tools\certs
  ```

- Pour l’instance locale des outils :
  
  ```cmd
  <Power BI visual project root>\node_modules\PowerBI-visuals-tools\certs
  ```

### <a name="pem-format"></a>Format PEM

Si vous utilisez le format de certificat Privacy Enhanced Mail (PEM), enregistrez le fichier de certificat en tant que *PowerBIVisualTest_public.crt*, puis enregistrez la clé privée en tant que *PowerBIVisualTest_private.key*.

### <a name="pfx-format"></a>Format PFX

Si vous utilisez le format Personal Information Exchange (PFX), enregistrez le fichier de certificat en tant que *PowerBIVisualTest_public.pfx*.

Si votre fichier de certificat PFX nécessite une phrase secrète :

1. Dans le fichier de configuration, spécifiez :
   
   ```cmd
   \PowerBI-visuals-tools\config.json
   ```
   
1. Dans la section `server`, spécifiez la phrase secrète en remplaçant l’espace réservé \<YOUR PASSPHRASE> :

    ```cmd
    "server":{
        "root":"webRoot",
        "assetsRoute":"/assets",
        "privateKey":"certs/PowerBIVisualTest_private.key",
        "certificate":"certs/PowerBIVisualTest_public.crt",
        "pfx":"certs/PowerBIVisualTest_public.pfx",
        "port":"8080",
        "passphrase":"<YOUR PASSPHRASE>"
    }
    ```

## <a name="next-steps"></a>Étapes suivantes
- [Développer un visuel de carte ronde Power BI](develop-circle-card.md)
- [Exemples de visuels Power BI](samples.md)
- [Publication d’un visuel Power BI dans AppSource](office-store.md)