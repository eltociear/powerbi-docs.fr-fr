---
title: Ajout de bibliothèques externes aux visuels Power BI
description: Cet article décrit comment utiliser des bibliothèques externes dans les visuels Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 02/24/2020
ms.openlocfilehash: 9df111e7545c43fe9b75784b1a95df4f37fd01e7
ms.sourcegitcommit: 2c798b97fdb02b4bf4e74cf05442a4b01dc5cbab
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80114126"
---
# <a name="adding-external-libraries"></a>Utiliser des bibliothèques externes

Cet article décrit comment utiliser des bibliothèques externes dans les visuels Power BI. Il contient des informations sur l’installation, l’importation et l’appel de bibliothèques externes à partir du code du visuel Power BI.

## <a name="javascript-libraries"></a>Bibliothèques JavaScript

1. Installez une bibliothèque JavaScript externe à l’aide de n’importe quel gestionnaire de package, par exemple *npm* ou *yarn*.
2. Importez les modules requis dans les fichiers sources à l’aide de la bibliothèque externe.

>[!NOTE]
>Si vous souhaitez ajouter des typages à votre bibliothèque JavaScript et obtenez IntelliSense et la sécurité au moment de la compilation, veillez à installer le package approprié.

### <a name="installing-the-d3-library"></a>Installation de la bibliothèque d3

Voici un exemple d’installation de la [bibliothèque d3](https://www.npmjs.com/package/d3) et du package [@types/d3](https://www.npmjs.com/package/@types/d3) à l’aide de [npm](https://www.npmjs.com/).

Pour obtenir un exemple complet, consultez le code des [visualisations Power BI](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/src/gantt.ts#L29).

1. Installez le package *d3* et le package *d3 types*.

    ```powershell
    npm install d3@5 --save
    npm install @types/d3@5 --save
    ```

2. Importez la bibliothèque *d3* dans les fichiers qui l’utilisent, par exemple `visual.ts`.

    ```typescript
    import * as d3 from "d3";
    ```

## <a name="css-framework"></a>Framework CSS

1. Installez un framework CSS externe à l’aide de n’importe quel gestionnaire de package, par exemple *npm* ou *yarn*.
2. Dans le fichier `.less` du visuel, incluez l’instruction `import`.

### <a name="installing-bootstrap"></a>Installation de bootstrap

Voici un exemple d’installation de [bootstrap](https://www.npmjs.com/package/bootstrap) à l’aide de [npm](https://www.npmjs.com/).

Pour obtenir un exemple complet, consultez le code des [visualisations Power BI](https://github.com/Microsoft/powerbi-visuals-sankey/blob/c8200da56913cd8b253be949a35fad0f4472b6de/style/visual.less#L32).

1. Installez le package *bootstrap*.

    ```powershell
    npm install bootstrap --save
    ```

2. Incluez l’instruction `import` dans `visual.less`.

    ```less
    @import (less) "node_modules/bootstrap/dist/css/bootstrap.css";
    ```
