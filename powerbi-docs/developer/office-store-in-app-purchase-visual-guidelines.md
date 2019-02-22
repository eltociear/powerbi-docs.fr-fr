---
title: Un autre achat peut être requis - Marche à suivre pour les visuels Power BI
description: Découvrez comment publier votre visuel personnalisé sur AppSource pour que d’autres utilisateurs puissent le trouver et l’utiliser après l’avoir acheté.
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 11/26/2018
ms.openlocfilehash: 4cbd17a08a8cb7c7253f60f29a19341598c9800f
ms.sourcegitcommit: 654fae0af739bd599e029d692f142faeba0a502f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2019
ms.locfileid: "56426536"
---
# <a name="guidelines-for-power-bi-visuals-with-additional-purchases"></a>Marche à suivre pour les visuels Power BI avec des achats supplémentaires

Jusqu’à une date récente, la **Place de marché (AppSource)** acceptait uniquement les visuels Power BI gratuits. Nous sommes en train de changer cette stratégie pour que les visuels avec l’étiquette de prix « Un autre achat peut être requis » puissent également être soumis à **AppSource**. Les visuels de type « Un autre achat peut être requis » sont similaires aux compléments d’achat dans l’application (IAP) de l’Office Store. Les développeurs peuvent également faire certifier ces visuels une fois ceux-ci approuvés par l’équipe **AppSource** et après avoir vérifié qu’ils répondent aux critères de certification, comme décrit dans l’[article sur les visuels personnalisés certifiés](../power-bi-custom-visuals-certified.md).

> [!Note]
> Pour que le visuel soit certifié, il ne doit pas accéder à des services externes ni à des ressources externes.

> [!Note]
> Tous les visuels gratuits doivent conserver les mêmes fonctionnalités gratuites que celles proposées précédemment. Vous pouvez compléter les fonctionnalités gratuites existantes par des fonctionnalités avancées payantes facultatives. Nous vous recommandons de soumettre les visuels IAP avec les fonctionnalités avancées en tant que nouveaux visuels au lieu de mettre à jour les fonctionnalités gratuites existantes.


## <a name="whats-changing-in-the-submission-process"></a>Qu’est-ce qui change dans le processus de soumission ?

Les développeurs chargent leurs visuels IAP sur AppSource par le biais du tableau de bord du vendeur, comme pour les visuels gratuits. Pour indiquer que le visuel soumis comporte des fonctionnalités IAP, les développeurs doivent écrire la mention suivante dans les notes du tableau de bord vendeur : « Visuel avec achat dans l’application ». Les développeurs doivent également fournir un jeton ou une clé de licence pour que l’équipe chargée de la validation puisse valider les fonctionnalités IAP. Une fois le visuel validé et approuvé, l’entrée AppSource correspondant au visuel IAP indique « Un autre achat peut être requis » sous les options de prix.

## <a name="what-is-a-power-bi-visual-with-iap-features"></a>Qu’est-ce qu’un visuel Power BI avec des fonctionnalités IAP ?

Un visuel IAP est gratuit et offre des fonctionnalités gratuites, mais propose aussi des fonctionnalités avancées dont l’utilisation peut engendrer des frais supplémentaires. Les développeurs doivent signaler aux utilisateurs dans la description du visuel que certaines fonctionnalités nécessitent des achats supplémentaires. À l’heure actuelle, Microsoft ne fournit pas d’interfaces de programmation d’applications (API) natives pour prendre en charge les achats dans l’application et les compléments. Les développeurs peuvent utiliser n’importe quel système de paiement tiers pour ces achats. Reportez-vous à la [stratégie](https://docs.microsoft.com/office/dev/store/validation-policies#2-apps-or-add-ins-can-display-certain-ads) de notre Store.

> [!NOTE]
> Les filigranes ne sont pas autorisés sur les fonctionnalités gratuites. Les développeurs peuvent afficher une fenêtre indépendante ou un filigrane si les fonctionnalités payantes avancées sont utilisées sans licence valide.  

## <a name="logo-guidelines"></a>Instructions relatives aux logos

Cette section décrit les spécifications relatives à l’ajout de logos et de logotypes dans les visuels.

> [!NOTE]
> Les logos sont autorisés en mode édition uniquement. Les logos ne peuvent pas être affichés en mode affichage.

![définitions](media/office-store-in-app-purchase-visual-guidelines/definitions.png)

![things-to-keep](media/office-store-in-app-purchase-visual-guidelines/things-to-keep-in-mind.png)

![things-to](media/office-store-in-app-purchase-visual-guidelines/things-to-avoid.png)

![size-and-format ](media/office-store-in-app-purchase-visual-guidelines/size-and-format.png)

![margins-and](media/office-store-in-app-purchase-visual-guidelines/margins-and-sizes.png)

![edit-mode](media/office-store-in-app-purchase-visual-guidelines/logos-in-edit-mode.png)

## <a name="best-practices"></a>Meilleures pratiques

### <a name="visual-landing-page"></a>Page d’arrivée du visuel

Utilisez la page d’arrivée pour indiquer aux utilisateurs comment utiliser votre visuel et où se procurer la licence. N’incluez pas de vidéos qui se déclenchent automatiquement. Ajoutez uniquement des documents permettant d’améliorer l’expérience utilisateur, comme des informations ou des liens sur l’achat de la licence, et sur l’utilisation des fonctionnalités IAP.

### <a name="license-key-and-token"></a>Jeton et clé de licence

Par souci pratique pour l’utilisateur, ajoutez des champs liés au jeton ou à la clé de licence en haut du volet de format pour que les utilisateurs puissent les trouver plus facilement.

## <a name="faq"></a>FORUM AUX QUESTIONS

Pour plus d’informations et des réponses à vos questions, voir [Foire aux questions sur les visuels avec achats supplémentaires](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-faq#visuals-with-additional-purchases).

## <a name="next-steps"></a>Étapes suivantes

Découvrez comment publier votre visuel personnalisé sur [AppSource](office-store.md) pour que d’autres utilisateurs puissent le trouver et l’utiliser.
