---
title: Structure de projets de visuels Power BI
description: L’article décrit une structure de projets de visuels
author: zBritva
ms.author: v-ilgali
ms.reviewer: ''
ms.service: powerbi
ms.topic: tutorial
ms.subservice: powerbi-custom-visuals
ms.date: 03/15/2019
ms.openlocfilehash: 728aba749f80710fdc0bb1e180b3318e63caa88c
ms.sourcegitcommit: 331ebf6bcb4a5cdbdc82e81a538144a00ec935d4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/28/2019
ms.locfileid: "75542090"
---
# <a name="power-bi-visual-project-structure"></a>Structure de projets de visuels Power BI

Après l’exécution du nouveau `<visual project name>` pbiviz, l’outil crée une structure de fichiers et de dossiers de base dans le dossier `<visual project name>`.

## <a name="visual-project-structure"></a>Structure de projets de visuels

![Structure de projets de visuels](./media/visual-project-structure.png)

* `.vscode` : contient les paramètres du projet pour VS Code. Pour configurer votre espace de travail, modifiez le fichier `.vscode/settings.json`. En savoir plus [sur les paramètres VS Code dans la documentation](https://code.visualstudio.com/docs/getstarted/settings)

* Le dossier `assets` contient uniquement le fichier `icon.png`. L’outil utilise ce fichier comme icône du visuel dans le volet Visualisation de Power BI.

    ![Volet Visualisation](./media/visualization-pane-analytics-tab.png)

* Le dossier `node_modules` contient tous les packages [installés par Node Package Manager](https://docs.npmjs.com/files/folders.html).

* Le dossier `src` contient le code source du visuel. Par défaut, l’outil crée deux fichiers :

  * `visual.ts` : code source principal du visuel.

  * `settings.ts` : code des paramètres du visuel. Les classes figurant dans le fichier simplifient l’[utilisation des propriétés du visuel](./objects-properties.md#properties).

* Le dossier `style` contient le fichier `visual.less` avec des styles pour le visuel.

* Le fichier `capabilities.json` contient les propriétés et paramètres principaux du visuel. Il permet au visuel de déclarer les fonctionnalités, les objets, les propriétés et le mappage de vues de données pris en charge.

    Découvrez-en plus [sur les fonctionnalités dans la documentation](./capabilities.md).

* `package-lock.json` est généré automatiquement pour toutes les opérations où NPM modifie l’arborescence `node_modules` ou `package.json`.

    Découvrez-en plus [sur `package-lock.json` dans la documentation officielle de NPM](https://docs.npmjs.com/files/package-lock.json).

* `package.json` décrit le package de projet. Il contient généralement des informations sur le projet, ses auteurs, sa description et ses dépendances.

    Découvrez-en plus [sur `package.json` dans la documentation officielle de NPM](https://docs.npmjs.com/files/package.json.html).

* `pbiviz.json` contient les métadonnées du visuel. Spécifiez les métadonnées du visuel dans ce fichier.

    Contenu standard du fichier :

  ```json
    {
        "visual": {
            "name": "<visual project name>",
            "displayName": "<visual project name>",
            "guid": "<visual project name>23D8B823CF134D3AA7CC0A5D63B20B7F",
            "visualClassName": "Visual",
            "version": "1.0.0",
            "description": "",
            "supportUrl": "",
            "gitHubUrl": ""
        },
        "apiVersion": "2.6.0",
        "author": { "name": "", "email": "" },
        "assets": { "icon": "assets/icon.png" },
        "externalJS": null,
        "style": "style/visual.less",
        "capabilities": "capabilities.json",
        "dependencies": null,
        "stringResources": []
    }
  ```

    where

  * `name` : nom interne du visuel.

  * `displayName` : nom du visuel dans l’interface utilisateur de Power BI.

  * `guid` : ID unique du visuel.

  * `visualClassName` : nom de la classe principale pour le visuel. Power BI crée l’instance de cette classe pour commencer à utiliser le visuel dans un rapport Power BI.

  * `version` : numéro de version du visuel.

  * `author` : contient le nom de l’auteur et l’e-mail du contact.

  * `icon` dans `assets` : chemin du fichier d’icône pour le visuel.

  * `externalJS` contient les chemins des bibliothèques JS utilisées dans le visuel.

    > [!IMPORTANT]
    > La dernière version de l’outil 3.x.x ou ultérieur n’utilise pas `externalJS`.

  * `style` est le chemin des fichiers de style.

  * `capabilities` est le chemin du fichier `capabilities.json`.

  * `dependencies` est le chemin du fichier `dependencies.json`. `dependencies.json` contient des informations sur les packages R utilisés dans les visuels basés sur R.

  * `stringResources` est un tableau de chemins des fichiers avec des localisations.

  En savoir plus [sur la localisation dans les visuels dans la documentation](./localization.md)

* `tsconfig.json` est un fichier de configuration pour TypeScript.

    En savoir plus [sur la configuration TypeScript dans la documentation officielle](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html)

    Le fichier `tsconfig.json` dans la section `files` doit contenir le chemin du fichier *.ts dans lequel la classe principale du visuel est spécifiée dans la propriété `visualClassName` du fichier `pbiviz.json`.

* Le fichier `tslint.json` contient la configuration TSLint.

    En savoir plus [sur la configuration TSLint dans la documentation officielle](https://palantir.github.io/tslint/usage/configuration/)

## <a name="next-steps"></a>Étapes suivantes

* Pour mieux comprendre comment le visuel, l’utilisateur et Power BI interagissent les uns avec les autres, consultez la rubrique relative au [concept de visuel](./power-bi-visuals-concept.md).

* Commencez à développer vos propres visuels Power BI à partir de zéro [à l’aide du Guide pas à pas](./custom-visual-develop-tutorial.md).
