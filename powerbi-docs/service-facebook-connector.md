---
title: 'Service tiers : Connecteur Facebook pour Power BI Desktop'
description: 'Service tiers : Connecteur Facebook pour Power BI Desktop'
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: a8b37606b602a24aa4a0995e138a52a86e0f945c
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/15/2019
ms.locfileid: "54295598"
---
# <a name="facebook-connector-for-power-bi-desktop"></a>Connecteur Facebook pour Power BI Desktop
Le connecteur Facebook de **Power BI Desktop** s’appuie sur l’API Graph de Facebook. Par conséquent, les fonctionnalités et la disponibilité peuvent varier au fil du temps.

Vous pouvez consulter un [didacticiel sur le connecteur Facebook pour Power BI Desktop](desktop-tutorial-facebook-analytics.md).

La version v1.0 de l’API Graph de Facebook a expiré le 30 <sup>avril</sup> 2015. Power BI utilise l’API Graph en arrière-plan pour le connecteur Facebook, ce qui vous permet de vous connecter à vos données et de les analyser.

Les requêtes créées avant le 30 <sup>avril</sup> 2015 ne fonctionnent peut-être plus ou retournent moins de données. Depuis le 30 <sup>avril</sup> 2015, Power BI utilise la version 2.8 dans tous les appels à l’API Facebook. Si votre requête a été créée avant le 30 avril 2015 et que vous ne l’avez pas utilisée depuis, vous devrez probablement vous authentifier à nouveau afin d’approuver le nouveau jeu d’autorisations que nous vous demanderons.

Nous nous efforçons de publier des mises à jour en fonction des modifications. Toutefois, il se peut que l’API soit modifiée d’une manière qui affecte les résultats des requêtes que nous générons. Dans certains cas, certaines requêtes peuvent ne plus être prises en charge. En raison de cette dépendance, nous ne pouvons pas garantir les résultats de vos requêtes lors de l’utilisation de ce connecteur.

Pour plus d’informations sur la modification de l’API de Facebook, accédez [ici](https://developers.facebook.com/docs/apps/changelog#v2_0).

