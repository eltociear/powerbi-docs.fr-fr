---
title: URL pour Power BI
description: Cet article décrit les points de terminaison qui doivent être accessibles pour les clients à l’aide de Power BI.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 10/22/2018
ms.openlocfilehash: e62d39f13e2b171456d667ec9683acd4ebdc5516
ms.sourcegitcommit: 46f1ba3f972f6e64bce05ad0fd527b27c49aedd6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52157123"
---
# <a name="power-bi-urls"></a>URL pour Power BI

**Le service en ligne Power BI**, également appelé « application SaaS Power BI », nécessite une connectivité à Internet. Les points de terminaison ci-dessous doivent être accessibles aux clients utilisant le service en ligne Power BI.

Pour utiliser le service en ligne Power BI, vous devez avoir accès à une connexion aux points de terminaison marqués **obligatoires** dans les tableaux ci-dessous et aux points de terminaison marqués **obligatoires** sur les sites liés. Si le lien vers un site externe fait référence à une section spécifique, vous devez seulement passer en revue les points de terminaison de cette section.

Les points de terminaison marqués **facultatifs** peuvent également être **placés dans la liste verte** pour que des fonctionnalités spécifiques puissent fonctionner.

Avec le service en ligne Power BI, seul le port TCP 443 doit être ouvert pour les points de terminaison listés.

Les caractères génériques (*) représentent tous les niveaux sous le domaine racine, et nous utilisons N/A quand les informations ne sont pas disponibles. La colonne **Destination(s)** est une liste avec le nom de domaine complet/les domaines et des liens vers des sites externes, qui contiennent plus d’informations sur les points de terminaison.

>[!Important]
>Les informations contenues dans les tableaux ci-dessous ne représentent pas le **cloud U.S. Government**, le **cloud Germany** ou le **cloud China**.

## <a name="authentication"></a>Authentification

Power BI dépend des points de terminaison obligatoires dans les sections relatives à l’authentification et à l’identité Office 365. Pour utiliser Power BI, vous devez être en mesure de vous connecter aux points de terminaison dans le site lié ci-dessous.

| Ligne | Objectif | Destination(s) | Port(s) |
| --- | --- | --- | --- |
| 1 | **Obligatoire :** Authentification et identité | Consultez la documentation d’Office 365 relative à [Office Online et aux URL courantes](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online).  | N/A |

## <a name="general-site-usage"></a>Utilisation générale du site

Pour l’utilisation générale de Power BI, vous devez être en mesure de vous connecter aux points de terminaison dans le tableau et les sites liés ci-dessous.

| Ligne | Objectif | Destination(s) | Port(s) |
| --- | --- | --- | --- |
| 1 | **Obligatoire :** API de backend | *.analysis.windows.net | TCP 443 |
| 2 | **Obligatoire :** Intégration Office 365 | Consultez la documentation d’Office 365 relative à [Office Online et aux URL courantes](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online). | N/A |
| 3 | **Obligatoire :** Portail | app.powerbi.com | TCP 443 |
| 4 | **Obligatoire :** Télémétrie du service | dc.services.visualstudio.com | TCP 443 |
| 5 | **Facultatif :** Messages d’information | dynmsg.modpim.com | TCP 443 |
| 6 | **Facultatif :** Enquêtes NPS | nps.onyx.azure.net | TCP 443 |
| | | |

## <a name="administration"></a>Administration

Pour effectuer des fonctions d’administration au sein de Power BI, vous devez pouvoir vous connecter aux points de terminaison dans les sites liés ci-dessous.

| Ligne | Objectif | Destination(s) | Port(s) |
| --- | --- | --- | --- |
| 1 | **Obligatoire :** Pour la gestion des utilisateurs et la consultation des journaux d’audit | Consultez la documentation d’Office 365 relative à [Office Online et aux URL courantes](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online). | N/A |
| | | |

## <a name="getting-data"></a>Obtention de données

Pour obtenir des données auprès de sources de données spécifiques, comme OneDrive, vous devez être en mesure de vous connecter aux points de terminaison dans le tableau ci-dessous. L’accès à des domaines et URL Internet supplémentaires peut être nécessaire pour les sources de données spécifiques utilisées au sein de votre organisation.

| Ligne | Objectif | Destination(s) | Port(s) |
| --- | --- | --- | --- |
| 1 | **Obligatoire :** AppSource (applications internes ou externes dans Power BI) | appsource.microsoft.com </br> *.s-microsoft.com  | TCP 443 |
| 2 | **Facultatif :** Se connecter et obtenir des données pour les packs de contenu | Dépend des packs de contenu utilisés | Dépend des packs de contenu utilisés |
| 3 | **Facultatif :** Importation de fichiers à partir de OneDrive - Personnel | Consultez le site [URL et ports nécessaires pour OneDrive](https://docs.microsoft.com/onedrive/required-urls-and-ports) | N/A |
| 4 | **Facultatif :** Vidéo du tutoriel Power BI en 60 secondes | *.doubleclick.net </br> *.ggpht.com </br> *.google.com </br> *.googlevideo.com </br> *.youtube.com </br> *.ytimg.com </br> fonts.gstatic.com | TCP 443 |
| 5 | **Facultatif :** Sources de données de streaming PubNub | Consultez la [documentation de PubNub](https://support.pubnub.com/support/solutions/articles/14000043522) | N/A |
| | | |

## <a name="dashboard-and-report-integration"></a>Intégration des tableaux de bord et des rapports

Power BI dépend de certains points de terminaison pour pouvoir prendre en charge vos tableaux de bord et vos rapports. Vous devez être en mesure de vous connecter aux points de terminaison dans le tableau et les sites liés ci-dessous.

| Ligne | Objectif | Destination(s) | Port(s) |
| --- | --- | --- | --- |
| 1 | **Obligatoire :** Intégration d’Excel | Consultez la documentation d’Office 365 relative à [Office Online et aux URL courantes](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online). | N/A |
| | | |

## <a name="custom-visuals"></a>Visuels personnalisés

Power BI dépend de certains points de terminaison pour pouvoir voir et accéder aux visuels personnalisés. Vous devez être en mesure de vous connecter aux points de terminaison dans le tableau et les sites liés ci-dessous.

| Ligne | Objectif | Destination(s) | Port(s) |
| --- | --- | --- | --- |
| 1 | **Obligatoire :** Importer un visuel personnalisé à partir de l’interface de Place de marché ou d’un fichier | *.azureedge.net </br> *.blob.core.windows.net </br> store.office.com | TCP 443 |
| 2 | **Facultatif :** Bing Maps | bing.com </br> platform.bing.com </br> *.dynamic.tiles.virtualearth.net </br> *.virtualearth.net | TCP 443 |
| 3 | **Facultatif :** PowerApps | Consultez la [section Services requis](https://docs.microsoft.com/powerapps/maker/canvas-apps/limits-and-config#required-services) sur site de la configuration système requise pour PowerApps | N/A |
| 4 | **Facultatif :** Visio | Consultez la documentation d’Office 365 relative à [Office Online et aux URL courantes](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online), ainsi qu’à [SharePoint Online et OneDrive Entreprise](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#sharepoint-online-and-onedrive-for-business). | N/A |
| | | |

## <a name="related-external-sites"></a>Sites externes connexes

Power BI établit des liaisons vers d’autres sites connexes. Ces sites incluent, entre autres, ceux liés à la documentation, au support et aux demandes de nouvelles fonctionnalités. Ces sites n’affectant pas les fonctionnalités de Power BI, vous pouvez les placer dans la liste verte si vous le souhaitez.

| Ligne | Objectif | Destination(s) | Port(s) |
| --- | --- | --- | --- |
| 1 | **Facultatif :** site de la communauté | community.powerbi.com </br> oxcrx34285.i.lithium.com | TCP 443 |
| 2 | **Facultatif :** site de la documentation | docs.microsoft.com </br> img-prod-cms-rt-microsoft-com.akamaized.net </br> statics-uhf-eas.akamaized.net </br> cdnssl.clicktale.neting-district.clicktale.net | TCP 443 |
| 3 | **Facultatif :** site de téléchargement (pour Power BI Desktop, etc.) | download.microsoft.com | TCP 443 |
| 4 | **Facultatif :** redirections externes | aka.ms </br> go.microsoft.com | TCP 443 |
| 5 | **Facultatif :** site des commentaires sur les idées| ideas.powerbi.com </br> powerbi.uservoice.com | TCP 443 |
| 6 | **Facultatif :** site Power BI ; page d’arrivée, liens vers des informations supplémentaires, site de support, liens de téléchargement, présentation des partenaires, etc. | powerbi.microsoft.com | TCP 443 |
| 7 | **Facultatif :** Centre développeurs Power BI | dev.powerbi.com | TCP 443 |
| 8 | **Facultatif :** site de support | support.powerbi.com </br> s3.amazonaws.com </br> *.olark.com </br> logx.optimizely.com </br> mscom.demdex.net </br> tags.tiqcdn.com | TCP 443 |
| | | |