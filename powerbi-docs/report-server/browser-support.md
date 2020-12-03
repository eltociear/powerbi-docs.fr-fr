---
title: Prise en charge du navigateur pour Power BI Report Server
description: Découvrez les versions de navigateur prises en charge pour la gestion et l’affichage de Power BI Report Server et les commandes de la visionneuse de rapports.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 10/24/2018
ms.openlocfilehash: 7658e1943c1f0ac85904fc7b985f2bd764451052
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96414757"
---
# <a name="browser-support-for-power-bi-report-server"></a>Prise en charge du navigateur pour Power BI Report Server
Découvrez les versions de navigateur prises en charge pour la gestion et l’affichage de Power BI Report Server et les commandes de la visionneuse de rapports.

## <a name="browser-requirements-for-the-web-portal"></a>Configuration requise pour le portail web
Voici la liste actuelle des navigateurs pris en charge pour le portail web.

**Microsoft Windows**  
*Windows 7, 8.1, 10 ; Windows Server 2008 R2, 2012, 2012 R2*

* Microsoft Edge (+)
* Microsoft Internet Explorer 11
* Google Chrome (+)
* Mozilla Firefox (+)

**Apple OS X**  
*OS X 10.9-10.11*

* Apple Safari (+)
* Google Chrome (+)
* Mozilla Firefox (+)

**Apple iOS**  
*iPhone et iPad sous iOS 10*

* Apple Safari (+)

**Google Android**  
*Téléphones et tablettes avec Android 4.4 (KitKat) ou version ultérieure*

* Google Chrome (+)
  
  **(+)**  Dernière version publiée publiquement

## <a name="browser-requirements-for-the-report-viewer-web-control-2015"></a>Configuration requise pour le contrôle web de la visionneuse de rapports (2015)
Voici la liste actuelle des navigateurs pris en charge pour le contrôle web de la visionneuse de rapports. La visionneuse de rapports prend en charge l’affichage de rapports à partir du portail web.

**Microsoft Windows**  
*Windows 7, 8.1, 10 ; Windows Server 2008 R2, 2012, 2012 R2*

* Microsoft Edge (+)
* Microsoft Internet Explorer 11
* Google Chrome (+)
* Mozilla Firefox (+)

**Apple OS X**  
*OS X 10.9-10.11*

* Apple Safari (+)
  
  **(+)**  Dernière version publiée publiquement

### <a name="authentication-requirements"></a>Conditions requises pour l’authentification
Les navigateurs prennent en charge des schémas d’authentification spécifiques qui doivent être gérés par le serveur de rapports pour que la demande du client aboutisse. Le tableau ci-dessous identifie les types d’authentifications par défaut pris en charge par chaque navigateur s’exécutant sur un système d’exploitation Windows.

| **Type de navigateur** | **Prend en charge** | **Authentification par défaut du navigateur** | **Authentification par défaut du serveur** |
| --- | --- | --- | --- |
| **Microsoft Edge** (+) |Negotiate, Kerberos, NTLM, De base |Negotiate |Oui. Les paramètres d’authentification par défaut fonctionnent avec Edge. |
| **Microsoft Internet Explorer** |Negotiate, Kerberos, NTLM, De base |Negotiate |Oui. Les paramètres d’authentification par défaut fonctionnent avec Internet Explorer. |
| **Google Chrome**(+) |Negotiate, NTLM, De base |Negotiate |Oui. Les paramètres d’authentification par défaut fonctionnent avec Chrome. |
| **Mozilla Firefox**(+) |NTLM, De base |NTLM |Oui. Les paramètres d’authentification par défaut fonctionnent avec Firefox. |
| **Apple Safari**(+) |NTLM, De base |De base |Oui. Les paramètres d’authentification par défaut fonctionnent avec Safari. |

 **(+)**  Dernière version publiée publiquement

### <a name="script-requirements-for-viewing-reports"></a>Exigences de script pour l’affichage de rapports
Pour utiliser la visionneuse de rapports, configurez votre navigateur pour exécuter des scripts.

Si l’exécution des scripts n’est pas activée, un message d’erreur similaire au suivant s’affiche lorsque vous ouvrez un rapport :

```
Your browser does not support scripts or has been configured to not allow scripts to run. Click here to view this report without scripts
```

 Si vous décidez de visionner le rapport sans prise en charge des scripts, le rapport est rendu en HTML sans les fonctionnalités de visionneuse de rapports telles que la barre d’outils Rapports et l’Explorateur de documents.

> [!NOTE]
> La barre d’outils Rapports fait partie du composant Visionneuse HTML. Par défaut, la barre d’outils apparaît en haut de chaque rapport rendu dans une fenêtre de navigateur. La visionneuse de rapports offre des fonctionnalités telles que la recherche d’informations dans le rapport, le défilement d’une page spécifique et l’ajustement de la taille de page à des fins d’affichage. Pour plus d’informations sur la barre d’outils Rapports ou la Visionneuse HTML, voir [Visionneuse HTML et barre d’outils Rapports](/sql/reporting-services/html-viewer-and-the-report-toolbar).
> 
> 

## <a name="browser-support-for-report-viewer-web-server-controls-in-visual-studio"></a>Prise en charge du navigateur pour les contrôles de serveur web de visionneuse de rapports dans Visual Studio
Le contrôle de serveur web de visionneuse de rapports est utilisé pour incorporer des fonctionnalités de rapport dans une application web ASP.NET. Pour plus d’informations sur la façon d’obtenir le contrôle Visionneuse de rapports, voir [Intégration de Reporting Services à l’aide de contrôles de visionneuse de rapports - Prise en main](/sql/reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls-get-started).

Utilisez un navigateur dans lequel la prise en charge des scripts est activée. Si le navigateur ne peut pas exécuter de scripts, vous ne pouvez pas afficher le rapport.

**Microsoft Windows**  
*Windows 7, 8.1, 10 ; Windows Server 2008 R2, 2012, 2012 R2*

* Microsoft Edge (+)
* Microsoft Internet Explorer 11
* Google Chrome (+)
* Mozilla Firefox (+)
  
  **(+)**  Dernière version publiée publiquement

## <a name="next-steps"></a>Étapes suivantes
[Vue d’ensemble de l’administrateur](admin-handbook-overview.md)  
[Installer Power BI Report Server](install-report-server.md)  
[Télécharger le Générateur de rapports](https://www.microsoft.com/download/details.aspx?id=53613)  
[Télécharger SQL Server Data Tools (SSDT)](/sql/ssdt/download-sql-server-data-tools-ssdt)

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)