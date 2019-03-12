---
title: Résolution des problèmes de développement de visuels personnalisés Power BI
description: Cet article décrit certains problèmes courants que vous pouvez rencontrer quand vous développez ou créez un visuel Power BI personnalisé.
author: sranins
ms.author: rasala
manager: kfile
ms.reviewer: maghan
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 11/06/2018
ms.openlocfilehash: cbda8cca80c32056f06788e53540d7f2d6ed972d
ms.sourcegitcommit: d0abedcf07f964418c9e5ea8d8ee3338b0b97a50
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57695009"
---
# <a name="troubleshoot-power-bi-custom-visuals"></a>Résoudre les problèmes de visuels personnalisés Power BI

## <a name="debug"></a>Déboguer

**Commande Pbiviz introuvable (ou erreurs similaires)**

Quand vous exécutez `pbiviz` dans la ligne de commande de votre terminal, vous devez voir l’écran d’aide. Si ce n’est pas le cas, cela signifie qu’il n’est pas installé correctement. Assurez-vous d’avoir au moins la version 4.0 de NodeJS installée.

**Impossible de trouver le visuel de débogage sous l’onglet Visualisations**

L’élément visuel de débogage ressemble à une icône d’invite sous l’onglet **Visualisations**.

![Sélection du visuel](media/power-bi-custom-visuals-troubleshoot/powerbi-developer-visual-selection.png)

Si vous ne le voyez pas, assurez-vous que vous l’avez activé dans les paramètres de Power BI.

> [!NOTE]
> L’élément visuel de débogage est actuellement disponible uniquement dans le service Power BI, pas dans Power BI Desktop ou dans l’application mobile. L’élément visuel empaqueté fonctionne partout.

**Impossible de contacter le serveur de visuels**

Exécutez le serveur de visuels avec la commande `pbiviz start` dans la ligne de commande de votre terminal à partir de la racine de votre projet de visuel. Si le serveur n’est pas en cours d’exécution, vos certificats SSL n’ont probablement pas été correctement installés.

N’hésitez pas à contacter le support technique des visuels personnalisés : *pbicvsupport@microsoft.com* si vous avez des questions, des commentaires ou des problèmes.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations, consultez [Questions fréquentes sur les visuels personnalisés Power BI](power-bi-custom-visuals-faq.md#organizational-custom-visuals).
