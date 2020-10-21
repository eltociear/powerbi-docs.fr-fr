---
title: Structure de projets de visuels Power BI
description: Cet article décrit la structure des dossiers et fichiers d’un projet de visuels Power BI
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 01/12/2020
ms.openlocfilehash: 74fec4e7fae2fc8630592c435adb42b34c93ef43
ms.sourcegitcommit: 50b21718a167c2b131313b4135c8034c6f027597
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/14/2020
ms.locfileid: "92049358"
---
# <a name="power-bi-visual-project-structure"></a>Structure de projets de visuels Power BI

La meilleure façon de commencer à créer un visuel Power BI consiste à utiliser l’outil Power BI [pbiviz](https://www.npmjs.com/package/powerbi-visuals-tools).

Pour créer un visuel, accédez au répertoire dans lequel vous souhaitez placer le visuel Power BI, puis exécutez la commande :

`pbiviz new <visual project name>`

L’exécution de cette commande crée un dossier de visuels Power BI contenant les fichiers suivants :

```markdown
project
├───.vscode
│   ├───launch.json
│   └───settings.json
├───assets
│   └───icon.png
├───node_modules
├───src
│   ├───settings.ts
│   └───visual.ts
├───style
│   └───visual.less
├───capabilities.json
├───package-lock.json
├───package.json
├───pbiviz.json
├───tsconfig.json
└───tslint.json
```

## <a name="folder-and-file-description"></a>Description des dossiers et fichiers

Cette section fournit des informations pour chaque dossier et fichier du répertoire créés par l’outil des visuels**pbiciz** Power BI.  

### <a name="vscode"></a>.vscode

Ce dossier contient les paramètres du projet VS Code.

Pour configurer votre espace de travail, modifiez le fichier `.vscode/settings.json`.

Pour plus d’informations, consultez [Paramètres de l’utilisateur et de l’espace de travail](https://code.visualstudio.com/docs/getstarted/settings)

### <a name="assets"></a>ressources

Ce dossier contient le fichier `icon.png`.

L’outil Power BI utilise ce fichier comme icône de nouveau visuel Power BI dans le volet de visualisation Power BI.

### <a name="src"></a>src

Ce dossier contient le code source du visuel.

Dans ce dossier, l’outil Power BI crée les fichiers suivants :
* `visual.ts` : code source principal du visuel.
* `settings.ts` : code des paramètres du visuel. Les classes du fichier fournissent une interface permettant de définir les [propriétés de votre visuel](./objects-properties.md#properties).

### <a name="style"></a>style

Ce dossier contient le fichier `visual.less`, qui définit les styles du visuel.

### <a name="capabilitiesjson"></a>capabilities.json

Ce fichier contient les propriétés et paramètres principaux (ou [fonctionnalités](./capabilities.md)) du visuel. Il permet au visuel de déclarer les fonctionnalités, les objets, les propriétés et le [mappage de vues de données](./dataview-mappings.md) pris en charge.

### <a name="package-lockjson"></a>package-lock.json

Ce ficher est généré automatiquement pour toutes les opérations où *npm* modifie l’arborescence `node_modules` ou le fichier `package.json`.

Pour plus d’informations sur ce fichier, consultez la documentation officielle [npm-package-lock.json](https://docs.npmjs.com/files/package-lock.json).

### <a name="packagejson"></a>package.json

Ce fichier décrit le package de projet. Il contient des informations sur le projet, ses auteurs, sa description et ses dépendances.

Pour plus d’informations sur ce fichier, consultez la documentation officielle [npm-package.json](https://docs.npmjs.com/files/package.json.html).

### <a name="pbivizjson"></a>pbiviz.json

Ce fichier contient les métadonnées du visuel.

Pour afficher un exemple de fichier `pbiviz.json` avec des commentaires décrivant les entrées de métadonnées, consultez la section sur les [entrées de métadonnées](#metadata-entries).

### <a name="tsconfigjson"></a>tsconfig.json

Un fichier de configuration pour [TypeScript](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html).

Ce fichier doit contenir le chemin du fichier **\*.ts** dans lequel se trouve la classe principale du visuel, comme spécifié dans la propriété `visualClassName` du fichier `pbiviz.json`.

### <a name="tslintjson"></a>tslint.json

Ce fichier contient la [configuration TSLint](https://palantir.github.io/tslint/usage/configuration/).

## <a name="metadata-entries"></a>Entrées de métadonnées

Les commentaires figurant dans la légende de code suivante du fichier `pbiviz.json` décrivent les entrées de métadonnées.

> [!NOTE]
> * À compter de la version 3.x.x de l’outil **pbiviz**, `externalJS` n’est pas pris en charge.
> * Pour la prise en charge de la localisation, [ajoutez les paramètres régionaux Power BI à votre visuel](./localization.md).

```json
{
  "visual": {
     // The visual's internal name.
    "name": "<visual project name>",

    // The visual's display name.
    "displayName": "<visual project name>",

    // The visual's unique ID.
    "guid": "<visual project name>23D8B823CF134D3AA7CC0A5D63B20B7F",

    // The name of the visual's main class. Power BI creates the instance of this class to start using the visual in a Power BI report.
    "visualClassName": "Visual",

    // The visual's version number.
    "version": "1.0.0",
    
    // The visual's description (optional)
    "description": "",

    // A URL linking to the visual's support page (optional).
    "supportUrl": "",

    // A link to the source code available from GitHub (optional).
    "gitHubUrl": ""
  },
  // The version of the Power BI API the visual is using.
  "apiVersion": "2.6.0",

  // The name of the visual's author and email.
  "author": { "name": "", "email": "" },

  // 'icon' holds the path to the icon file in the assets folder; the visual's display icon.
  "assets": { "icon": "assets/icon.png" },

  // Contains the paths for JS libraries used in the visual.
  // Note: externalJS' isn't used in the Power BI visuals tool version 3.x.x or higher.
  "externalJS": null,

  // The path to the 'visual.less' style file.
  "style": "style/visual.less",

  // The path to the `capabilities.json` file.
  "capabilities": "capabilities.json",

  // The path to the `dependencies.json` file which contains information about R packages used in R based visuals.
  "dependencies": null,

  // An array of paths to files with localizations.
  "stringResources": []
}
```

## <a name="next-steps"></a>Étapes suivantes

* Pour comprendre les interactions entre un visuel, un utilisateur et Power BI, consultez [Concept visuel Power BI](./power-bi-visuals-concept.md).

* Commencez à développer vos propres visuels Power BI à partir de zéro à l’aide du [Guide pas à pas](./develop-circle-card.md).
