---
title: URL pour Power BI
description: Les points de terminaison doivent être accessibles aux clients utilisant Power BI
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 08/13/2018
ms.openlocfilehash: 8e29fa0c9471bb865619102247f38776208c3d87
ms.sourcegitcommit: 8990028a348b642ba5c96f001fe3a4280f0166ee
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "40101128"
---
# <a name="power-bi-urls"></a>URL pour Power BI

**Le service en ligne Power BI**, également appelé « application SaaS Power BI », nécessite une connectivité à Internet. Les points de terminaison ci-dessous doivent être accessibles aux clients utilisant le service en ligne Power BI.

Pour utiliser le service en ligne Power BI, vous devez avoir accès à une connexion aux points de terminaison marqués **obligatoires** dans les tableaux ci-dessous et aux points de terminaison marqués **obligatoires** sur les sites liés. Si le lien vers un site externe fait référence à une section spécifique, vous devez seulement passer en revue les points de terminaison de cette section.

Les points de terminaison marqués **facultatifs** peuvent également être **placés dans la liste verte** pour que des fonctionnalités spécifiques puissent fonctionner.

Le service en ligne Power BI nécessite seulement que le port TCP 443 soit ouvert pour les points de terminaison listés.

Les caractères génériques (*) représentent tous les niveaux sous le domaine racine, et nous utilisons N/A quand les informations ne sont pas disponibles. La colonne **Destination(s)** est une liste avec le nom de domaine complet/les domaines et des liens vers des sites externes, qui contiennent plus d’informations sur les points de terminaison.

>[!Important]
>Les informations contenues dans les tableaux ci-dessous ne représentent pas le **cloud US Government**, **le cloud Germany** et **le cloud China**.

## <a name="authentication"></a>Authentification

Power BI dépend des points de terminaison obligatoires dans les sections relatives à l’authentification et à l’identité Office 365. Pour utiliser Power BI, vous devez être en mesure de vous connecter aux points de terminaison dans le site lié ci-dessous.

| Ligne | Objectif | Destination(s) | Port(s) |
|-----|-------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------|--------------|---------------------------------------------|
| 1 | **Obligatoire :** Authentification et identité | Consultez la [section Identité et authentification dans Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2#bkmk_identity) sur le site de la liste verte d’Office 365 | N/A |

## <a name="general-site-usage"></a>Utilisation générale du site

Pour l’utilisation générale de Power BI, vous devez être en mesure de vous connecter aux points de terminaison dans le tableau et les sites liés ci-dessous.

| Ligne | Objectif | Destination(s) | Port(s) |
|-----|-------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------|--------------|---------------------------------------------|
| 1 | **Obligatoire :** API de backend | *.analysis.windows.net | TCP 443 |
| 2 | **Obligatoire :** Intégration Office 365 | Consultez le [Portail et services partagés Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2#bkmk_portal-identity) sur le site de la liste verte d’Office 365 | N/A |
| 3 | **Obligatoire :** Portail | app.powerbi.com | TCP 443 |
| 4 | **Obligatoire :** Télémétrie du service | dc.services.visualstudio.com | TCP 443 |
| 5 | **Facultatif :** Messages d’information | dynmsg.modpim.com | TCP 443 |
| 6 | **Facultatif :** Enquêtes NPS | nps.onyx.azure.net | TCP 443 |

## <a name="administration"></a>Administration

Pour effectuer des fonctions d’administration au sein de Power BI, vous devez pouvoir vous connecter aux points de terminaison dans les sites liés ci-dessous.

| Ligne | Objectif | Destination(s) | Port(s) |
|-----|-------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------|--------------|---------------------------------------------|
| 1 | **Obligatoire :** Pour la gestion des utilisateurs et la consultation des journaux d’audit | Consultez le [Portail et services partagés Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2#bkmk_portal-identity) sur le site de la liste verte d’Office 365 | N/A |

## <a name="get-data"></a>Obtenir des données

Pour être en mesure d’obtenir des données auprès de sources de données spécifiques comme OneDrive, vous devez être en mesure de vous connecter aux points de terminaison dans le tableau ci-dessous.

| Ligne | Objectif | Destination(s) | Port(s) |
|-----|-------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------|--------------|---------------------------------------------|
| 1 | **Obligatoire :** AppSource (applications internes ou externes dans Power BI) | appsource.microsoft.com | TCP 443 |
| 2 | **Facultatif :** Importation de fichiers à partir de OneDrive - Personnel | Consultez le site [URL et ports nécessaires pour OneDrive](https://support.office.com/en-ie/article/required-urls-and-ports-for-onedrive-ce15d2cc-52ef-42cd-b738-d9c6f9b03f3a) | N/A |
| 3 | **Facultatif :** Vidéo du tutoriel Power BI en 60 secondes | *.doubleclick.net </br> *.ggpht.com </br> *.google.com </br> *.googlevideo.com </br> *.youtube.com </br> *.ytimg.com </br> fonts.gstatic.com | TCP 443 |
| 4 | **Facultatif :** Sources de données de streaming PubNub | Consultez la [documentation de PubNub](https://support.pubnub.com/support/solutions/articles/14000043522) | N/A |

## <a name="dashboard-and-report-integration"></a>Intégration des tableaux de bord et des rapports 

Power BI dépend de certains points de terminaison pour pouvoir prendre en charge vos tableaux de bord et vos rapports. Vous devez être en mesure de vous connecter aux points de terminaison dans le tableau et les sites liés ci-dessous.

| Ligne | Objectif | Destination(s) | Port(s) |
|-----|-------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------|--------------|---------------------------------------------|
| 1 | **Obligatoire :** Intégration d’Excel | Consultez la [section Office Online](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2#bkmk_officeonline) sur le site de la liste verte d’Office 365 | N/A |

## <a name="custom-visuals"></a>Visuels personnalisés

Power BI dépend de certains points de terminaison pour pouvoir voir et accéder aux visuels personnalisés. Vous devez être en mesure de vous connecter aux points de terminaison dans le tableau et les sites liés ci-dessous.

| Ligne | Objectif | Destination(s) | Port(s) |
|-----|-------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------|--------------|---------------------------------------------|
| 1 | **Obligatoire :** Importer un visuel personnalisé à partir de l’interface de Place de marché et d’un fichier | *.microsoft.com </br> *.bing.com </br> *.msecnd.net </br> *.osi.office.net </br> *.azureedge.net </br> ajax.aspnetcdn.com </br> nexus.ensighten.com </br> store.office.com | TCP 443 |
| 2 | **Facultatif :** Bing Maps | bing.com </br> platform.bing.com </br> *.dynamic.tiles.virtualearth.net </br> *.virtualearth.net | TCP 443 |
| 3 | **Facultatif :** PowerApps | Consultez la [section Services requis](https://docs.microsoft.com/powerapps/maker/canvas-apps/limits-and-config#required-services) sur site de la configuration système requise pour PowerApps | N/A |
| 4 | **Facultatif :** Visio | Consultez la [section Office Online](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2#bkmk_officeonline) sur le site de la liste verte d’Office 365 | N/A |