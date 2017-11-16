---
title: Notes de publication de Power BI Report Server
description: "Cette rubrique décrit des limitations et problèmes liés à Power BI Report Server."
services: powerbi
documentationcenter: 
author: guyinacube
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 11/01/2017
ms.author: asaxton
ms.openlocfilehash: ffd0d1ce38a989121225a666ca4aa924df130216
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2017
---
# <a name="power-bi-report-server-release-notes"></a>Notes de publication de Power BI Report Server
Cette rubrique décrit des limitations et problèmes liés à Power BI Report Server.

Pour télécharger Power BI Report Server et Power BI Desktop optimisé pour Power BI Report Server, accédez à la page [Rapports locaux avec Power BI Report Server](https://powerbi.microsoft.com/report-server/).

## <a name="october-2017"></a>Octobre 2017
* Prise en charge de données importées dans les rapports Power BI
* Possibilité d’afficher des classeurs Excel sur le portail web. Cela est possible en configurant Office Online Server.
* Prise en charge des nouveaux visuels de tableau et de matrice Power BI.
* Prise en charge de l’API REST

## <a name="june-2017"></a>Juin 2017
* Aucun nouvel élément pour juin 2017.

## <a name="may-2017"></a>Mai 2017
* Pour fonctionner avec Power BI Report Server, les rapports Power BI doivent être créés avec Power BI Desktop optimisé pour Power BI Report Server. Vous pouvez télécharger Power BI Desktop à partir du lien de téléchargement en haut de cette page.
* Les rapports Power BI prennent en charge uniquement les connexions en direct (tabulaires ou multidimensionnelles) à Analysis Services.
* Les visuels R ne sont pas pris en charge.

**Problème et impact sur le client :** si vous disposez de SQL Server Reporting Services et de Power BI Report Server sur le même ordinateur et désinstallez l’un d’eux, vous ne pouvez vous connecter au serveur de rapports restant avec le Gestionnaire de configuration du serveur de rapports.

**Solution de contournement** Pour contourner ce problème, vous devez effectuer les opérations suivantes après désinstallation de l’un des serveurs.

1. Lancez une invite de commandes en mode Administrateur.
2. Accédez au répertoire dans lequel est installé le serveur de rapports restant.
   
    *L’emplacement par défaut pour Power BI Report Server est C:\Program Files\Microsoft Power BI Report Server*.
   
    *L’emplacement par défaut pour SQL Server Reporting Services est C:\Program Files\Microsoft SQL Server Reporting Services*.
3. Accédez ensuite au dossier suivant. Il s’agit de *SSRS* ou de *PBIRS* selon le serveur restant.
4. Accédez au dossier WMI.
5. Exécutez la commande suivante :
   
    ```
    regsvr32 /i ReportingServicesWMIProvider.dll
    ```
   
    Vous pouvez ignorer l’erreur suivante, si elle s’affiche.
   
    ```
    The module "ReportingServicesWMIProvider.dll" was loaded but the entry-point DLLInstall was not found. Make sure that "ReportingServicesWMIProvider.dll" is a valid DLL or OCX file and then try again.
    ```

## <a name="next-steps"></a>Étapes suivantes
[Nouveautés dans Power BI Report Server](whats-new.md)  
[Manuel de l’utilisateur](user-handbook-overview.md)  
[Manuel de l’administrateur](admin-handbook-overview.md)  
[Démarrage rapide : installer Power BI Report Server](quickstart-install-report-server.md)  
[Installer le Générateur de rapports](https://docs.microsoft.com/sql/reporting-services/install-windows/install-report-builder)  
[Télécharger SQL Server Data Tools (SSDT)](http://go.microsoft.com/fwlink/?LinkID=616714)

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)

