---
title: Résolution des problèmes de développement de visuels personnalisés Power BI
description: Cet article décrit certains problèmes courants que vous pouvez rencontrer quand vous développez ou créez un visuel Power BI personnalisé.
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-developer
ms.topic: conceptual
ms.date: 11/06/2018
ms.openlocfilehash: d6f3f654574e9cca081ae2f8191fd7b9fc017afd
ms.sourcegitcommit: 02f918a4f27625b6f4e47473193ebc8219db40e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2018
ms.locfileid: "51223547"
---
# <a name="troubleshoot-power-bi-custom-visuals"></a>Résoudre les problèmes de visuels personnalisés Power BI

## <a name="debug"></a>Déboguer

**Commande Pbiviz introuvable (ou erreurs similaires)**

Quand vous exécutez `pbiviz` dans la ligne de commande de votre terminal, vous devez voir l’écran d’aide. Si ce n’est pas le cas, cela signifie qu’il n’est pas installé correctement. Assurez-vous d’avoir au moins la version 4.0 de NodeJS installée.

**Impossible de trouver le visuel de débogage sous l’onglet Visualisations**

Le visuel de débogage ressemble à une icône d’invite sous l’onglet **Visualisations**.

![Sélection du visuel](media/power-bi-custom-visuals-troubleshoot/powerbi-developer-visual-selection.png)

Si vous ne le voyez pas, assurez-vous que vous l’avez activé dans les paramètres de Power BI.

> [!NOTE]
> Le visuel de débogage est actuellement disponible uniquement dans le service Power BI, pas dans Power BI Desktop ou dans l’application mobile. Le visuel empaqueté fonctionne partout.

**Impossible de contacter le serveur de visuels**

Exécutez le serveur de visuels avec la commande `pbiviz start` dans la ligne de commande de votre terminal à partir de la racine de votre projet de visuel. Si le serveur est en cours d’exécution, vos certificats SSL n’ont probablement pas été correctement installés.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations et des réponses à vos questions, visitez [Questions fréquentes sur les visuels personnalisés Power BI](power-bi-custom-visuals-faq.md#organizational-custom-visuals).