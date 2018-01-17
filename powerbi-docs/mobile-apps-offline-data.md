---
title: "Affichage de vos données hors connexion dans les applications mobiles Power BI"
description: "Découvrez un avantage de l’affichage de Power BI dans une application mobile plutôt qu’un navigateur mobile : la possibilité de visualiser vos données même quand vous n’êtes connecté à aucun réseau."
services: powerbi
documentationcenter: 
author: maggiesMSFT
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
ms.date: 01/16/2018
ms.author: maggies
ms.openlocfilehash: 6ed6f2898fa99075c6130cd60c083f619b6ba258
ms.sourcegitcommit: 259d7689bcb1683d4d63a245a9b02becea072139
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="view-your-data-offline-in-the-power-bi-mobile-apps"></a>Affichage de vos données hors connexion dans les applications mobiles Power BI
S’applique à :

| ![iPhone](media/mobile-apps-offline-data/iphone-logo-50-px.png) | ![iPad](media/mobile-apps-offline-data/ipad-logo-50-px.png) | ![Téléphone Android](media/mobile-apps-offline-data/android-phone-logo-50-px.png) | ![Tablette Android](media/mobile-apps-offline-data/android-tablet-logo-50-px.png) | ![Windows 10](media/mobile-apps-offline-data/win-10-logo-50-px.png) |
|:--- |:--- |:--- |:--- |:--- |
| iPhone |iPad |Téléphones Android |Tablettes Android |Appareils Windows 10 |

L’affichage de Power BI dans une application mobile plutôt qu’un navigateur mobile offre l’avantage de visualiser vos données, même lorsque vous n’êtes connecté à aucun réseau. 

![Aucun message réseau](media/mobile-apps-offline-data/power-bi-iphone-no-network.png)

Par défaut, Power BI actualise fréquemment les données afin de toujours vous fournir des réponses à jour, même lorsque vous êtes en déplacement ou en itinérance.

## <a name="data-access-while-youre-offline"></a>Accès aux données hors connexion
Quand vous êtes en mode hors connexion, vous pouvez accéder à tous les tableaux de bord auxquels vous avez accédé précédemment à partir de l’application mobile.

Vous avez également accès en lecture seule à tous les rapports Power BI auxquels vous avez précédemment accédés depuis l’application mobile. Vous pouvez voir le rapport complet, mais vous ne pouvez pas filtrer, effectuer un filtrage croisé, trier ou utiliser des segments.

## <a name="background-data-refresh"></a>Actualisation des données en arrière-plan
L’actualisation en arrière-plan met à jour vos tableaux de bord favoris, ainsi que les tableaux de bord et les rapports que vous avez sélectionnés au cours des deux dernières semaines, avec les données sur le service Power BI (et pas la source de données). Si vous êtes connecté à Internet via Wi-Fi, l’actualisation en arrière-plan se met à jour toutes les 2 heures. Sinon, si vous êtes sur un réseau 3G, Power BI se met à jour toutes les 24 heures.

Vous pouvez désactiver l’actualisation en arrière-plan, par exemple pour éviter l’utilisation du réseau. Vérifiez les paramètres sur votre appareil.

> [!NOTE]
> Si vous utilisez l’application mobile Power BI sur un appareil iOS et que votre organisation a configuré Microsoft Intune MAM, l’actualisation des données en arrière-plan est désactivée. La prochaine fois que vous ouvrez l’application, Power BI actualise les données à partir du service Power BI sur le web.
> 
> En savoir plus sur la [configuration des applications mobiles Power BI avec Microsoft Intune](service-admin-mobile-intune.md). 
> 
> 

## <a name="offline-indicators"></a>Indicateurs hors connexion
Power BI fournit des indicateurs clairs lorsque vous entrez ou quittez le mode hors connexion, mais aussi en cas de tableaux de bord manquants, de rapports et de vignettes non disponibles hors connexion.

## <a name="limitations"></a>Limites
Les restrictions suivantes peuvent s’appliquer en mode hors connexion avec Power BI sur un appareil mobile :

* Power BI peut mettre en cache jusqu’à 250 Mo de données hors connexion.
* Certains types de vignette nécessitent une connexion active au serveur et ne sont donc pas disponibles hors ligne. C’est le cas des vignettes Bing ou des vignettes personnalisées par exemple.
* Les classeurs Excel entiers dans Power BI ne sont pas disponibles en mode hors connexion.
* Vous ne pouvez voir les rapports mobiles Reporting Services et les indicateurs de performance clés en mode hors connexion que si vous les avez consultés en étant connecté. Ils ne s’actualisent pas en arrière-plan. Ils s’actualisent chaque fois que vous les ouvrez. 

## <a name="next-steps"></a>Étapes suivantes
Vos commentaires nous aident à développer les futurs processus d’implémentation. N’oubliez pas de voter pour les fonctionnalités que vous aimeriez voir dans les applications mobiles Power BI. 

* [Applications Power BI pour appareils mobiles](mobile-apps-for-mobile-devices.md)
* Suivez @MSPowerBI sur Twitter
* Rejoindre la conversation de la [Communauté Power BI](http://community.powerbi.com/)
* [Prise en main de Power BI](service-get-started.md)

