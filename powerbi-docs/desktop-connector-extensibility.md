---
title: Extensibilité des connecteurs dans Power BI
description: Fonctionnalités d’extensibilité des connecteurs, fonctionnalités, paramètres de sécurité et connecteurs certifiés
author: cpopell
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 07/25/2018
ms.author: gepopell
LocalizationGroup: Connect to data
ms.openlocfilehash: a5774fe6979516a0fe70364fea5dd91b7a2a48ae
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/15/2019
ms.locfileid: "54275729"
---
# <a name="connector-extensibility-in-power-bi"></a>Extensibilité des connecteurs dans Power BI

Dans Power BI, les clients et les développeurs peuvent étendre les sources de données auxquelles ils peuvent se connecter de diverses manières, notamment en utilisant des connecteurs existants et des sources de données génériques (telles que ODBC, OData, Oledb, Web, CSV, XML, JSON). En plus de ces sources de données, les développeurs peuvent créer des extensions de données appelées **connecteurs personnalisés** et certifier ces mêmes connecteurs pour en faire des **connecteurs certifiés**.

Actuellement, l’utilisation de **connecteurs personnalisés** est possible via un commutateur de fonctionnalité. Avant de faire passer cette fonctionnalité de la version bêta à la disponibilité générale, nous avons ajouté un menu qui vous permet de contrôler de façon sécurisée le niveau de code personnalisé que vous voulez autoriser à s’exécuter sur votre système : tous les connecteurs personnalisés, ou seulement les connecteurs certifiés et distribués par Microsoft, dans la boîte de dialogue **Obtenir les données**.

## <a name="custom-connectors"></a>Connecteurs personnalisés

Les **connecteurs personnalisés** peuvent englober un large éventail de possibilités, qu’il s’agisse de petites API critiques pour votre activité ou de services étoffés propres à un secteur d’activité pour lesquels Microsoft n’a pas publié de connecteur. De nombreux connecteurs sont distribués par les fournisseurs eux-mêmes. Si vous avez besoin d’un connecteur de données spécifique, vous devez contacter le fournisseur en question.

Pour utiliser un **connecteur personnalisé**, placez-le dans le dossier *\[Documents]\\Power BI Desktop\\Connecteurs personnalisés*, puis ajustez les paramètres de sécurité comme indiqué dans la section suivante.

Vous n’avez pas besoin d’ajuster les paramètres de sécurité pour utiliser des **connecteurs certifiés**.

## <a name="data-extension-security"></a>Sécurité des extensions de données

Pour modifier les paramètres de sécurité des extensions de données, dans **Power BI Desktop**, sélectionnez **Fichier > Options et paramètres > Options > Sécurité**.

![Déterminez si vous souhaitez pouvoir charger des connecteurs personnalisés à partir des options de sécurité des extensions de données](media/desktop-connector-extensibility/data-extension-security-1.png)

Sous **Extensions de données**, vous avez le choix entre deux niveaux de sécurité :

* (Recommandé) Autoriser uniquement le chargement des extensions certifiées
* (Non recommandé) Autoriser le chargement de toutes les extensions sans avertissement

Si vous prévoyez d’utiliser des **connecteurs personnalisés**, ou des connecteurs que vous-même ou un tiers avez développés et distribués, vous devez sélectionner **« (Non recommandé) Autoriser le chargement de toutes les extensions sans avertissement »**. Nous déconseillons ce paramètre de sécurité, sauf si vous faites entièrement confiance à vos connecteurs personnalisés, étant donné que le code qu’il implique permet de gérer les informations d’identification (y compris de les envoyer par protocole HTTP) et d’ignorer les niveaux de confidentialité.

Dans le cas du paramètre de sécurité **« (Recommandé) »**, si des connecteurs personnalisés sont présents sur votre système, une erreur s’affiche avec une description des connecteurs qui ne peuvent pas être chargés pour des raisons de sécurité.

![Une boîte de dialogue décrit les connecteurs personnalisés qui ne peuvent pas être chargés en raison des paramètres de sécurité, dans ce cas TripPin](media/desktop-connector-extensibility/data-extension-security-2.png)

Pour résoudre l’erreur et utiliser ces connecteurs, vous devez modifier vos paramètres de sécurité et choisir **« (Non recommandé) »** comme indiqué précédemment, puis redémarrer **Power BI Desktop**.

## <a name="certified-connectors"></a>Connecteurs certifiés

Un sous-ensemble limité des extensions de données est considéré comme étant **Certifié**, et ces connecteurs certifiés sont disponibles via la boîte de dialogue **Obtenir les données**, mais le développeur tiers qui a créé le connecteur reste responsable de la maintenance et du support. Même si Microsoft les distribue, nous ne sommes pas responsables de leurs performances ou de la continuité de leur bon fonctionnement.

Si vous voulez qu’un connecteur personnalisé soit certifié, demandez à votre fournisseur de contacter dataconnectors@microsoft.com.
