---
title: Extensibilité des connecteurs dans Power BI
description: Fonctionnalités d’extensibilité des connecteurs, fonctionnalités, paramètres de sécurité et connecteurs certifiés
author: cpopell
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 07/25/2018
ms.author: gepopell
LocalizationGroup: Connect to data
ms.openlocfilehash: c63357df043ff6a646562d398a07d8042dd5a0ee
ms.sourcegitcommit: 7fb0b68203877ff01f29724f0d1761d023075445
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/26/2018
ms.locfileid: "39256546"
---
# <a name="connector-extensibility-in-power-bi"></a>Extensibilité des connecteurs dans Power BI

Dans Power BI, les clients et les développeurs peuvent étendre les sources de données auxquelles ils peuvent se connecter de diverses manières, notamment en utilisant des connecteurs existants et des sources de données génériques (telles que ODBC, OData, Oledb, Web, CSV, XML, JSON). En plus de ces sources de données, les développeurs peuvent créer des extensions de données appelées **connecteurs personnalisés** et certifier ces mêmes connecteurs pour en faire des **connecteurs certifiés**.

Dans les versions précédentes de Power BI, l’utilisation de **connecteurs personnalisés** était possible via un commutateur de fonctionnalité. Désormais, il existe un menu qui vous permet de contrôler en toute sécurité le niveau de code personnalisé dont vous souhaitez autoriser l’exécution sur votre système : tous les connecteurs personnalisés ou seulement les connecteurs certifiés et distribués par Microsoft dans la boîte de dialogue **Obtenir les données**.

## <a name="custom-connectors"></a>Connecteurs personnalisés

Qu’il s’agisse de petites API essentielles à votre activité ou de services étoffés propres à un secteur d’activité que Microsoft n’a pas implémenté, les **connecteurs personnalisés** peuvent englober un large éventail de possibilités. La plupart des connecteurs de ce type sont distribués par les fournisseurs eux-mêmes. Si vous avez besoin d’un connecteur de données spécifique, vous devez contacter le fournisseur en question.

Pour utiliser un **connecteur personnalisé**, placez-le dans le dossier *\[Documents]\\Power BI Desktop\\Connecteurs personnalisés*, puis ajustez les paramètres de sécurité comme indiqué dans la section suivante.

Vous n’avez pas besoin d’ajuster les paramètres de sécurité pour utiliser des **connecteurs certifiés**.

## <a name="data-extension-security"></a>Sécurité des extensions de données

Pour modifier les paramètres de sécurité des extensions de données, dans **Power BI Desktop**, sélectionnez **Fichier > Options et paramètres > Options > Sécurité**.

![Déterminez si vous souhaitez pouvoir charger des connecteurs personnalisés à partir des options de sécurité des extensions de données](media/desktop-connector-extensibility/data-extension-security-1.png)

Sous **Extensions de données**, vous avez le choix entre deux niveaux de sécurité :

* (Recommandé) Autoriser uniquement le chargement des extensions certifiées
* (Non recommandé) Autoriser le chargement de toutes les extensions sans avertissement

Si vous prévoyez d’utiliser des **connecteurs personnalisés** ou des connecteurs que vous ou un tiers avez développés et distribués, vous devez sélectionner **(Non recommandé) Autoriser le chargement de toutes les extensions sans avertissement**. Nous déconseillons ce paramètre de sécurité, sauf si vous prévoyez d’exécuter des **connecteurs personnalisés**.

Dans le cas du paramètre de sécurité **(Recommandé)**, si des connecteurs personnalisés sont présents sur votre système, une erreur s’affiche avec une description des connecteurs qui ne peuvent pas être chargés pour cause de sécurité.

![Une boîte de dialogue décrit les connecteurs personnalisés qui ne peuvent pas être chargés en raison des paramètres de sécurité, dans ce cas TripPin](media/desktop-connector-extensibility/data-extension-security-2.png)

Pour résoudre l’erreur et utiliser ces connecteurs, vous devez modifier vos paramètres de sécurité et choisir **(Non recommandé)** comme indiqué précédemment, puis redémarrer **Power BI Desktop**.

## <a name="certified-connectors"></a>Connecteurs certifiés

Un sous-ensemble limité d’extensions de données est considérée comme étant **Certifié**, et les connecteurs certifiés sont disponibles via la boîte de dialogue **Obtenir les données**, mais le développeur tiers qui a créé le connecteur reste responsable de la maintenance et de l’assistance. Même si Microsoft les distribue, nous ne sommes pas responsables de leurs performances ou de leur fonctionnement dans le temps.

Si vous souhaitez qu’un connecteur personnalisé soit certifié, demandez à votre fournisseur de contacter Microsoft.
