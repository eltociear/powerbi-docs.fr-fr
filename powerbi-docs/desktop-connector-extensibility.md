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
ms.openlocfilehash: 7d5d743dda31d05df0beb528648c5a43ffc6b335
ms.sourcegitcommit: 32a44dd17a44ccfd4a2d86a0d235251c2fda1c5c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68702104"
---
# <a name="connector-extensibility-in-power-bi"></a>Extensibilité des connecteurs dans Power BI

Dans Power BI, les clients et développeurs peuvent étendre les sources de données auxquelles ils se connectent de nombreuses façons. Ils utilisent des connecteurs existants et des sources de données génériques (telles que ODBC, OData, OLEDB, Web, CSV, XML, JSON). Ou bien, les développeurs créent des extensions de données appelées **Connecteurs personnalisés** pour en faire des **Connecteurs certifiés**.

Actuellement, vous activez les **Connecteurs personnalisés** à l’aide d’un menu qui vous permet de contrôler en toute sécurité le niveau de code personnalisé que vous souhaitez exécuter sur votre système. Dans la boîte de dialogue **Obtenir des données**, vous pouvez choisir tous les connecteurs personnalisés ou uniquement les connecteurs certifiés et distribués par Microsoft.

## <a name="custom-connectors"></a>Connecteurs personnalisés

Les **connecteurs personnalisés** peuvent englober un vaste éventail de possibilités, qu’il s’agisse de petites API critiques pour votre activité ou de services étoffés propres à un secteur d’activité pour lesquels Microsoft n’a pas publié de connecteur. De nombreux connecteurs sont distribués par le fournisseur. Si vous avez besoin d’un connecteur de données spécifique, contactez un fournisseur.

Pour utiliser un **Connecteur personnalisé**, placez-le dans le dossier *\[Documents]\\Power BI Desktop\\Connecteurs personnalisés*, puis ajustez les paramètres de sécurité comme indiqué dans la section suivante.

Vous n’avez pas besoin d’ajuster les paramètres de sécurité pour utiliser des **connecteurs certifiés**.

## <a name="data-extension-security"></a>Sécurité des extensions de données

Pour modifier les paramètres de sécurité des extensions de données, dans **Power BI Desktop**, sélectionnez **Fichier > Options et paramètres > Options > Sécurité**.

![Contrôlez si vous souhaitez charger des connecteurs personnalisés avec des options de sécurité d’extension de données](media/desktop-connector-extensibility/data-extension-security-1.png)

Sous **Extensions de données**, vous avez le choix entre deux niveaux de sécurité :

* (Recommandé) Autoriser uniquement le chargement des extensions certifiées
* (Non recommandé) Autoriser le chargement de toutes les extensions sans avertissement

Si vous prévoyez d’utiliser des **connecteurs personnalisés**, ou des connecteurs que vous-même ou un tiers avez développés, vous devez sélectionner **« (Non recommandé) Autoriser le chargement de toutes les extensions sans avertissement »** . Nous ne recommandons pas ce paramètre de sécurité, sauf si vous avez une confiance absolue dans vos Connecteurs personnalisés. En effet, ce code peut gérer des informations d’identification, notamment les envoyer via HTTP en ignorant les niveaux de confidentialité.

Dans le paramètre de sécurité **« (Recommandé) »** , s’il existe des connecteurs personnalisés sur votre système, un message d’erreur s’affiche, indiquant que le connecteur n’a pas été certifié et qu’il n’est pas possible de vérifier si son utilisation et sécurisée, suivi d’une liste de connecteurs qui ne peuvent pas être chargés en toute sécurité.

![Une boîte de dialogue décrit les connecteurs personnalisés qui ne peuvent pas être chargés en raison des paramètres de sécurité, dans ce cas TripPin](media/desktop-connector-extensibility/data-extension-security-2.png)

Pour résoudre l’erreur sans modifier la sécurité, supprimez les connecteurs non signés de votre dossier « Connecteurs personnalisés ».

Pour résoudre l’erreur et utiliser ces connecteurs, modifiez vos paramètres de sécurité en choisissant **« (Non recommandé) Autoriser le chargement de toutes les extensions sans avertissement »** comme décrit précédemment. Ensuite, redémarrez **Power BI Desktop**.

## <a name="certified-connectors"></a>Connecteurs certifiés

Un sous-ensemble limité d’extensions de données est considéré comme **Certifié**. Accédez aux connecteurs certifiés dans la boîte de dialogue **Obtenir les données**. Toutefois, le développeur tiers qui a créé le connecteur est responsable de sa maintenance et de son support. Même si Microsoft distribue les connecteurs, elle n’est pas responsable de leurs performances ou de la continuité de leur fonctionnement.

Si vous voulez qu’un connecteur personnalisé soit certifié, demandez à votre fournisseur de contacter dataconnectors@microsoft.com.
