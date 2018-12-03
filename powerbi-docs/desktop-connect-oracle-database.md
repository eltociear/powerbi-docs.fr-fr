---
title: Connexion à une base de données Oracle
description: Étapes et téléchargements nécessaires pour connecter Oracle à Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 5b5dc41ee3f4d41f2e38053470054a8f453e4fb3
ms.sourcegitcommit: 2ae660a7b70fce23eb58b159d049eca44a664f2c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2018
ms.locfileid: "52670284"
---
# <a name="connect-to-an-oracle-database"></a>Se connecter à une base de données Oracle
Pour vous connecter à une base de données Oracle avec **Power BI Desktop**, le logiciel client Oracle approprié doit être installé sur l’ordinateur exécutant Power BI Desktop. Le logiciel client Oracle que vous devez utiliser dépend de la version de Power BI Desktop que vous avez installée (la version **32 bits** ou la version **64 bits**).

**Versions prises en charge** : Oracle 9 et versions ultérieures, logiciels clients Oracle 8.1.7 et versions ultérieures.

## <a name="determining-which-version-of-power-bi-desktop-is-installed"></a>Identification de la version installée de Power BI Desktop
Pour identifier la version installée de Power BI Desktop, sélectionnez **Fichier > Aide > À propos de**, puis vérifiez la ligne **Version :**. L’illustration suivante indique qu’une version 64 bits de Power BI Desktop est installée :

![](media/desktop-connect-oracle-database/connect-oracle-database_1.png)

## <a name="installing-the-oracle-client"></a>Installation du client Oracle
Pour les versions **32 bits** de Power BI Desktop, utilisez le lien suivant pour télécharger et installer le client Oracle **32 bits** :

* [Oracle Data Access Components (ODAC) 32 bits avec Oracle Developer Tools for Visual Studio (12.1.0.2.4)](http://www.oracle.com/technetwork/topics/dotnet/utilsoft-086879.html)

Pour les versions **64 bits** de Power BI Desktop, utilisez le lien suivant pour télécharger et installer le client Oracle **64 bits** :

* [ODAC 12C Release 4 64 bits (12.1.0.2.4) pour Windows x64](http://www.oracle.com/technetwork/database/windows/downloads/index-090165.html)

## <a name="connect-to-an-oracle-database"></a>Connexion à une base de données Oracle
Une fois le pilote du client Oracle correspondant installé, vous pouvez vous connecter à une base de données Oracle. Pour établir la connexion, effectuez les étapes suivantes :

1. Dans la fenêtre Obtenir des données, sélectionnez **Base de données > Base de données Oracle**
   
   ![](media/desktop-connect-oracle-database/connect-oracle-database_2.png)
2. Dans la boîte de dialogue **Base de données Oracle** qui s’affiche, indiquez le nom du serveur, puis sélectionnez **Se connecter**. Si un identificateur de sécurité (SID) est requis, vous pouvez le spécifier dans le format suivant : *Nom_serveur/SID*, où SID est le nom unique de la base de données. Si le format *Nom_serveur/SID* ne fonctionne pas, essayez d’utiliser *Nom_serveur/Nom_service*, où Nom_service est l’alias utilisé lors de la connexion.
   
   ![](media/desktop-connect-oracle-database/connect-oracle-database_3.png)
3. Si vous voulez importer des données à l’aide d’une requête de base de données native, vous pouvez placer votre requête dans la zone **Instruction SQL**, accessible en développant la section **Options avancées** de la boîte de dialogue **Base de données Oracle**.
   
   ![](media/desktop-connect-oracle-database/connect-oracle-database_4.png)
4. Après avoir entré les informations de votre base de données Oracle dans la boîte de dialogue Base de données Oracle (et éventuellement des informations facultatives comme un SID ou une requête de base de données native), sélectionnez **OK** pour vous connecter.
5. Si la base de données Oracle exige des informations d’identification d’utilisateur de base de données, entrez-les dans la boîte de dialogue quand vous y êtes invité.

