---
title: Connexion à une base de données Oracle
description: Étapes et téléchargements nécessaires pour connecter Oracle à Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/05/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: f43981121211c900b3cb4506b830ce09da3b5e20
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83295488"
---
# <a name="connect-to-an-oracle-database"></a>Se connecter à une base de données Oracle
Pour se connecter à une base de données Oracle avec Power BI Desktop, le logiciel client Oracle approprié doit être installé sur l’ordinateur exécutant Power BI Desktop. Le logiciel client Oracle que vous utilisez dépend de la version de Power BI Desktop que vous avez installée : 32 bits ou 64 bits.

Versions d’Oracle prises en charge : 
- Oracle 9 et versions ultérieures
- Logiciel client Oracle 8.1.7 et versions ultérieures

> [!NOTE]
> Si vous configurez une base de données Oracle pour Power BI Desktop, une passerelle de données locale ou Power BI Report Server, consultez les informations de l’article [Type de connexion Oracle](https://docs.microsoft.com/sql/reporting-services/report-data/oracle-connection-type-ssrs?view=sql-server-ver15). 


## <a name="determining-which-version-of-power-bi-desktop-is-installed"></a>Identification de la version installée de Power BI Desktop
Pour identifier la version installée de Power BI Desktop, sélectionnez **Fichier** > **Aide** > **À propos de**, puis regardez la ligne **Version**. L’illustration suivante indique qu’une version 64 bits de Power BI Desktop est installée :

![Version de Power BI Desktop](media/desktop-connect-oracle-database/connect-oracle-database_1.png)

## <a name="installing-the-oracle-client"></a>Installation du client Oracle
- Pour la version 32 bits de Power BI Desktop, [téléchargez et installez le client Oracle 32 bits](https://www.oracle.com/technetwork/topics/dotnet/utilsoft-086879.html).

- Pour la version 64 bits de Power BI Desktop, [téléchargez et installez le client Oracle 64 bits](https://www.oracle.com/database/technologies/odac-downloads.html).

> [!NOTE]
> Pendant l’installation du client Oracle, veillez à activer *Configurer ASP.NET sur les fournisseurs ODP.NET et/ou Oracle pour l’ensemble de l’ordinateur* en cochant la case correspondante dans l’Assistant Installation. Dans certaines versions de l’Assistant du client Oracle, elle est cochée par défaut, mais ce n’est pas le cas de toutes. Il faut qu’elle soit cochée pour que Power BI puisse se connecter à votre base de données Oracle.

## <a name="connect-to-an-oracle-database"></a>Se connecter à une base de données Oracle
Une fois que vous avez installé le pilote du client Oracle correspondant, vous pouvez vous connecter à une base de données Oracle. Pour établir la connexion, effectuez les étapes suivantes :

1. Sous l’onglet **Accueil**, sélectionnez **Obtenir les données**. 

2. Dans la fenêtre **Obtenir les de données** qui s’affiche, sélectionnez **Plus** (si nécessaire), sélectionnez **Base de données** > **Base de données Oracle**, puis sélectionnez **Se connecter**.
   
   ![Connexion à une base de données Oracle](media/desktop-connect-oracle-database/connect-oracle-database_2.png)
2. Dans la boîte de dialogue **Base de données Oracle** qui s’affiche, indiquez le nom du **serveur**, puis sélectionnez **OK**. Si un identificateur de sécurité (SID) est nécessaire, vous pouvez le spécifier dans le format suivant : *Nom_serveur/SID*, où *SID* est le nom unique de la base de données. Si le format *Nom_serveur/SID* ne fonctionne pas, utilisez *Nom_serveur/Nom_service*, où *Nom_service* est l’alias que vous utilisez pour vous connecter.


   ![Entrer le nom du serveur Oracle](media/desktop-connect-oracle-database/connect-oracle-database_3.png)

   > [!TIP]
   > Si vous ne parvenez pas à vous connecter dans cette étape, essayez en utilisant le format suivant dans le champ **Serveur** : *(DESCRIPTION=(ADDRESS=(PROTOCOL=TCP)(HOST=nom_hôte)(PORT=numéro_port))(CONNECT_DATA=(SERVICE_NAME=nom_service)))*
   
3. Si vous voulez importer des données en utilisant une requête de base de données native, placez votre requête dans la zone **Instruction SQL**, qui apparaît quand vous développez la section **Options avancées** de la boîte de dialogue **Base de données Oracle**.
   
   ![Développer Options avancées](media/desktop-connect-oracle-database/connect-oracle-database_4.png)
4. Après avoir entré les informations de votre base de données Oracle dans la boîte de dialogue **Base de données Oracle** (et éventuellement des informations facultatives comme un SID ou une requête de base de données native), sélectionnez **OK** pour vous connecter.
5. Si la base de données Oracle exige des informations d’identification d’utilisateur de base de données, entrez-les dans la boîte de dialogue quand vous y êtes invité.


## <a name="troubleshooting"></a>Résolution des problèmes

Si vous avez téléchargé Power BI Desktop à partir du Microsoft Store, vous risquez ne pas pouvoir vous connecter aux bases de données Oracle en raison d’un problème de pilote Oracle. Si vous rencontrez ce problème, le message d’erreur retourné est : *Référence d’objet non définie*. Pour résoudre ce problème, effectuez une de ces étapes :

* Téléchargez Power BI Desktop à partir du [Centre de téléchargement](https://www.microsoft.com/download/details.aspx?id=58494) au lieu du Microsoft Store.

* Si vous voulez utiliser la version du Microsoft Store : sur votre ordinateur local, copiez oraons.dll depuis _12.X.X\client_X_ vers _12.X.X\client_X\bin_, où _X_ représente les numéros de la version et du répertoire.

Si vous voyez le message d’erreur *Référence d’objet non définie* dans Power BI Gateway quand vous vous connectez à une base de données Oracle, suivez les instructions fournies dans [Gérer votre source de données - Oracle](service-gateway-onprem-manage-oracle.md).

Si vous utilisez Power BI Report Server, consultez les instructions de l’article [Type de connexion Oracle](https://docs.microsoft.com/sql/reporting-services/report-data/oracle-connection-type-ssrs?view=sql-server-ver15).
