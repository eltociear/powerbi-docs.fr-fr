---
title: Se connecter à Power BI Premium de jeux de données avec les applications clientes et des outils (version préliminaire)
description: Explique comment se connecter aux jeux de données dans Power BI Premium à partir des outils et les applications clientes.
author: minewiskan
ms.author: owend
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 05/20/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: 063f43cb2345ccb3d1fec5c414100beb8ccde451
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "65941509"
---
# <a name="connect-to-datasets-with-client-applications-and-tools-preview"></a>Se connecter à des jeux de données avec les applications clientes et des outils (version préliminaire)

Prise en charge les espaces de travail et des jeux de données Premium de BI Power *en lecture seule* connexions à partir de Microsoft et les applications clientes de tiers et les outils. 

> [!NOTE]
> Cet article est destiné uniquement à vous présenter une connectivité en lecture seule aux espaces de travail Power BI Premium et jeux de données. Il *n’est pas* destiné à fournir des informations détaillées sur la programmabilité des outils spécifiques et applications, architecture et gestion de l’espace de travail et le jeu de données. Sujets décrites ici nécessitent une connaissance approfondie de l’architecture de base de données de modèle tabulaire Analysis Services et l’administration.

## <a name="protocol"></a>Protocole

Power BI Premium utilise le [XML for Analysis](https://docs.microsoft.com/bi-reference/xmla/xml-for-analysis-xmla-reference) protocole XMLA () pour les communications entre les applications clientes et le moteur qui gère vos espaces de travail et les jeux de données. Ces communications sont via ce que sont communément comme points de terminaison XMLA. XMLA est le même protocole de communication utilisé par le moteur de Microsoft Analysis Services, qui, sous le capot, exécute la gestion sémantique de modélisation, de gouvernance, de cycle de vie et de données de Power BI. 

La grande majorité des applications clientes et les outils n’explicitement communiquent pas avec le moteur à l’aide de points de terminaison XMLA. Au lieu de cela, ils utilisent des bibliothèques clientes telles que MSOLAP, ADOMD et AMO comme intermédiaire entre l’application cliente et le moteur, qui communique exclusivement à l’aide de XMLA.


## <a name="supported-tools"></a>Outils pris en charge

Ces outils prennent en charge l’accès en lecture seule pour les espaces de travail Power BI Premium et de jeux de données :

**SQL Server Management Studio (SSMS)** -requêtes prend en charge DAX, MDX, XMLA et TraceEvent. Requiert la version 18.0. Télécharger [ici](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms). 

**SQL Server Profiler** -inclus avec SSMS 18.0 (version préliminaire), cet outil fournit le suivi et débogage d’événements du serveur. Vous pouvez capturer et enregistrer des données relatives à chaque événement dans un fichier ou d’une table pour analyse ultérieure. Bien qu’officiellement déconseillé pour SQL Server, Profiler continue à être inclus dans SSMS et est pris en charge pour Analysis Services et à présent, Power BI Premium. Pour plus d’informations, consultez [SQL Server Profiler](https://docs.microsoft.com/sql/tools/sql-server-profiler/sql-server-profiler).

**DAX Studio** - Open source, outil de la Communauté pour l’exécution et analyse DAX requêtes dans Analysis Services. Requiert la version 2.8.2 ou ultérieure. Pour plus d’informations, consultez [daxstudio.org](https://daxstudio.org/).

**Tableaux croisés dynamiques Excel** -version Démarrer en un clic d’Office 16.0.11326.10000 ou ultérieure est requise.

**Tiers** : inclut les applications de visualisation de données clientes et des outils qui peuvent se connecter à, requête et consommer des jeux de données dans Power BI Premium. La plupart des outils nécessitent les dernières versions des bibliothèques clientes MSOLAP, mais certains peuvent utiliser ADOMD.

## <a name="client-libraries"></a>Bibliothèques clientes

Bibliothèques clientes sont nécessaires pour les applications clientes et des outils pour vous connecter à des espaces de travail Power BI Premium. Les mêmes bibliothèques clientes utilisées pour se connecter à Analysis Services sont également pris en charge dans Power BI Premium. Applications clientes Microsoft tels que Excel, SQL Server Management Studio (SSMS) et SQL Server Data Tools (SSDT) installent tous les trois bibliothèques clientes et les mettre à jour en même temps que les mises à jour de l’application normale. Dans certains cas, en particulier avec les applications tierces et des outils, vous devrez peut-être installer des versions plus récentes des bibliothèques clientes. Bibliothèques clientes sont mis à jour tous les mois. Pour plus d’informations, consultez [les bibliothèques clientes pour la connexion à Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-data-providers).

## <a name="connecting-to-a-premium-workspace"></a>Connexion à un espace de travail Premium

Vous pouvez vous connecter à des espaces de travail affectés à des capacités Premium dédié. Espaces de travail affectés à une capacité dédiée ont une chaîne de connexion dans le format d’URL. 

Pour obtenir la chaîne de connexion d’espace de travail dans Power BI, dans **paramètres de l’espace de travail**, dans le **Premium** sous l’onglet **connexion de l’espace de travail**, cliquez sur **copier**.

![Chaîne de connexion d’espace de travail](media/service-premium-connect-tools/connect-tools-workspace-connection.png)

Connexions de l’espace de travail utilisent le format d’URL suivant pour résoudre un espace de travail comme s’il s’agissait d’un nom de serveur Analysis Services :   
`powerbi://api.powerbi.com/v1.0/[tenant name]/[workspace name]` 

Par exemple, `powerbi://api.powerbi.com/v1.0/contoso.com/Sales Workspace`
> [!NOTE]
> `[workspace name]` distingue la casse et peut contenir des espaces. 

### <a name="to-connect-in-ssms"></a>Pour vous connecter dans SSMS

Dans **se connecter au serveur** > **Type de serveur**, sélectionnez **Analysis Services**. Dans **nom du serveur**, entrez l’URL. Dans **authentification**, sélectionnez **Active Directory - authentification universelle avec prise en charge MFA**, puis dans **nom d’utilisateur**, entrez votre ID d’utilisateur d’organisation. 

Lorsque connecté, l’espace de travail est affiché comme un serveur Analysis Services et jeux de données dans l’espace de travail est affichés sous forme de bases de données.  

![SSMS](media/service-premium-connect-tools/connect-tools-ssms.png)

### <a name="initial-catalog"></a>Catalogue initial

Certains outils, tels que SQL Server Profiler, vous devrez peut-être spécifier un *Initial Catalog*. Spécifiez un jeu de données (base de données) dans votre espace de travail. Dans **se connecter au serveur**, cliquez sur **Options**. Dans le **se connecter au serveur** boîte de dialogue, dans le **propriétés de connexion** sous l’onglet **se connecter à la base de données**, entrez le nom du jeu de données.

### <a name="duplicate-workspace-name"></a>Nom de l’espace de travail en double

Lors de la connexion à un espace de travail avec le même nom qu’un autre espace de travail, vous pouvez recevoir l’erreur suivante : **Impossible de se connecter à powerbi://api.powerbi.com/v1.0/ [Nom_client] / [nom de l’espace de travail].**

Pour contourner cette erreur, en plus du nom de l’espace de travail, spécifiez le ObjectIDGuid, ce qui peut être copié à partir de l’objectID de l’espace de travail dans l’URL. Ajoutez l’ID d’objet à l’URL de connexion. Par exemple, « powerbi://api.powerbi.com/v1.0/myorg/Contoso ventes - 9d83d204-82a9-4b36-98f2-a40099093830 »

### <a name="duplicate-dataset-name"></a>Nom du jeu de données en double

Lors de la connexion à un dataset avec le même nom qu’un autre jeu de données dans le même espace de travail, ajoutez le guid de jeu de données pour le nom du dataset. Vous pouvez obtenir le nom du jeu de données *et* guid en cas de connexion à l’espace de travail dans SSMS. 

### <a name="delay-in-datasets-shown"></a>Retards dans les jeux de données indiqué

Lors de la connexion à un espace de travail, les modifications à partir de jeux de données nouvelles, supprimées et renommées peuvent prendre jusqu'à 5 minutes pour apparaître. 

### <a name="unsupported-datasets"></a>Jeux de données non pris en charge

Les jeux de données suivants n’est pas accessibles à l’aide de points de terminaison XMLA. Ces jeux de données *ne sera pas* apparaissent sous l’espace de travail dans SSMS ou dans d’autres outils : 

- Jeux de données avec une connexion active à des modèles Analysis Services. 
- Jeux de données à transmettre des données à l’aide de l’API REST.
- Jeux de données du classeur Excel. 

Les jeux de données suivants n’est pas pris en charge dans le service Power BI :   

- Jeux de données avec une connexion active à un jeu de données Power BI.

## <a name="audit-logs"></a>Journaux d’audit 

Les applications clientes et des outils de vous connecter à un espace de travail, l’accès via les points de terminaison XMLA sont enregistrées dans les journaux d’audit de Power BI sous la **GetWorkspaces** opération. Pour plus d’informations, consultez [audit de Power BI](service-admin-auditing.md).

## <a name="see-also"></a>Voir aussi

[Références de Analysis Services](https://docs.microsoft.com/bi-reference/#pivot=home&panel=home-all)   
[SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms)   
[SQL Server Analysis Services tabulaire protocole](https://docs.microsoft.com/openspecs/sql_server_protocols/ms-ssas-t/b98ed40e-c27a-4988-ab2d-c9c904fe13cf)   
[Vues de gestion dynamique (DMV)](https://docs.microsoft.com/sql/analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services)   


D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
