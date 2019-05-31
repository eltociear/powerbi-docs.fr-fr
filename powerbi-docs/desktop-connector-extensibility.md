---
title: Extensibilité des connecteurs dans Power BI
description: Fonctionnalités d’extensibilité des connecteurs, fonctionnalités, paramètres de sécurité et connecteurs certifiés
author: cpopell
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/22/2019
ms.author: gepopell
LocalizationGroup: Connect to data
ms.openlocfilehash: 16b96d91a9dd37fa8a502bbcca772438c703cb63
ms.sourcegitcommit: d88cc6a87d4ba82ad2c4d496a3634f927e4ac529
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66412967"
---
# <a name="connector-extensibility-in-power-bi"></a>Extensibilité des connecteurs dans Power BI

Dans Power BI, les clients et les développeurs peuvent étendre les sources de données auxquels ils se connectent à bien des égards. Ils utilisent des connecteurs existants et les sources de données génériques (par exemple, ODBC, OData, Oledb, Web, CSV, XML, JSON). Ou, les développeurs de créent des extensions de données, appelées **connecteurs personnalisés**et les rendre **connecteurs certifiés**.

Actuellement, vous activez **des connecteurs personnalisés** à l’aide d’un menu qui vous permet en toute sécurité de contrôler le niveau de code personnalisé que vous souhaitez laisser s’exécuter sur votre système. Vous pouvez choisir tous les connecteurs personnalisés ou des connecteurs certifiés et distribués par Microsoft dans le **obtenir des données** boîte de dialogue.

## <a name="custom-connectors"></a>Connecteurs personnalisés

**Connecteurs personnalisés** peut inclure un large éventail de possibilités, allant de petits API critiques pour votre entreprise, à des services spécifiques du secteur volumineux que Microsoft n’a pas publié un connecteur pour. Nombre de connecteurs est distribué par le fournisseur. Si vous avez besoin pour un connecteur de données spécifique, vous devez contacter un fournisseur.

Pour utiliser un **un connecteur personnalisé de**, placez-le dans le  *\[Documents]\\Power BI Desktop\\connecteurs personnalisés* dossier et ajuster les paramètres de sécurité comme décrit dans la section suivante.

Vous n’avez pas besoin d’ajuster les paramètres de sécurité pour utiliser des **connecteurs certifiés**.

## <a name="data-extension-security"></a>Sécurité des extensions de données

Pour modifier les paramètres de sécurité d’extension de données, dans **Power BI Desktop** sélectionnez **fichier > Options et paramètres > Options > sécurité**.

![Contrôler si vous souhaitez charger des connecteurs personnalisés avec des options de sécurité d’Extension de données](media/desktop-connector-extensibility/data-extension-security-1.png)

Sous **Extensions de données**, vous avez le choix entre deux niveaux de sécurité :

* (Recommandé) Autoriser uniquement le chargement des extensions certifiées
* (Non recommandé) Autoriser le chargement de toutes les extensions sans avertissement

Si vous prévoyez d’utiliser **connecteurs personnalisés** ou connecteurs que vous ou un tiers ont développé, vous devez sélectionner **"(Not Recommended) autoriser n’importe quelle extension à charger sans avertissement «** . Nous ne recommandons pas ce paramètre de sécurité, sauf si vous faites absolument confiance vos connecteurs personnalisés. Parce que le code dans cet emplacement peut gérer les informations d’identification, y compris les envoyer via HTTP et ignorer les niveaux de confidentialité.

À la **« (recommandé) »** sécurité définissant, s’il existe des connecteurs personnalisés sur votre système, une erreur s’affiche qui décrit les connecteurs qui ne peut pas charger en raison de sécurité.

![Une boîte de dialogue décrit les connecteurs personnalisés qui ne peut pas charger en raison des paramètres de sécurité, dans ce cas TripPin](media/desktop-connector-extensibility/data-extension-security-2.png)

Pour résoudre l’erreur et utiliser ces connecteurs, modifiez vos paramètres de sécurité pour le **"(Not Recommended) autoriser n’importe quelle extension à charger sans avertissement «** définissant comme décrit précédemment. Ensuite, redémarrez **Power BI Desktop**.

## <a name="certified-connectors"></a>Connecteurs certifiés

Un sous-ensemble limité des extensions de données est considérée comme **certifié**. Accéder aux connecteurs certifiés dans le **obtenir des données** boîte de dialogue. Toutefois, il incombe au développeur de fournisseurs tiers qui a créé le connecteur pour sa maintenance et la prise en charge. Bien que Microsoft distribue les connecteurs, il n’est pas responsable de leurs performances ou la fonction continue.

Si vous voulez qu’un connecteur personnalisé soit certifié, demandez à votre fournisseur de contacter dataconnectors@microsoft.com.
