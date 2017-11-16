---
title: "Résoudre les problèmes de démarrage de Power BI Desktop"
description: "Résoudre les problèmes de démarrage de Power BI Desktop"
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/05/2017
ms.author: davidi
ms.openlocfilehash: 80593c13adb54950efbf5ff6e12a962b557fe7a0
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2017
---
# <a name="resolve-issues-when-power-bi-desktop-will-not-launch"></a>Résoudre les problèmes empêchant le démarrage de Power BI Desktop
Dans **Power BI Desktop**, les utilisateurs ayant installé et exécuté des versions précédentes de **la passerelle de données locale Power BI** peuvent se retrouver dans l’impossibilité de démarrer Power BI Desktop. Cela est dû aux restrictions de stratégie d’administration placées par la passerelle de données locale sur les canaux nommés de l’ordinateur local. 

## <a name="resolve-issues-with-the-on-premises-data-gateway-and-power-bi-desktop"></a>Résoudre les problèmes avec la passerelle de données locale et **Power BI Desktop**
Il existe trois options pour résoudre le problème lié à la passerelle de données locale et permettre à Power BI Desktop de démarrer :

### <a name="resolution-1-install-the-latest-version-of-power-bi-on-premises-data-gateway"></a>Solution 1 : installer la dernière version de la passerelle de données locale Power BI
La dernière version de la passerelle de données locale Power BI ne place pas de restrictions sur les canaux nommés de l’ordinateur local et permet à Power BI Desktop de démarrer correctement. Si vous souhaitez continuer à utiliser la passerelle de données locale Power BI, cette solution est recommandée. Vous pouvez télécharger la dernière version de la passerelle de données locale Power BI [ici](https://go.microsoft.com/fwlink/?LinkId=698863). Notez que le lien est un lien direct vers le fichier exécutable d’installation.

### <a name="resolution-2-uninstall-or-stop-the-power-bi-on-premises-data-gateway-windows-service"></a>Solution 2 : désinstaller ou arrêter le service Windows de passerelle de données locale Power BI
Vous pouvez désinstaller la passerelle de données locale Power BI si vous n’en avez plus besoin. Vous pouvez aussi arrêter le service Windows de passerelle de données locale Power BI, ce qui supprime la restriction de stratégie et permet à Power BI Desktop de démarrer.

### <a name="resolution-3-run-power-bi-desktop-with-administrator-privilege"></a>Solution 3 : exécuter Power BI Desktop avec des privilèges d’administrateur
Vous pouvez démarrer Power BI Desktop en tant qu’administrateur, ce qui permet également à Power BI Desktop de démarrer correctement. Il est toutefois recommandé d’installer la dernière version de la passerelle de données locale Power BI, comme décrit précédemment dans cet article.

## <a name="help-with-other-issues-when-launching-power-bi-desktop"></a>Aide à la résolution des problèmes de lancement de **Power BI Desktop**
Nous nous efforçons autant que possible de résoudre les problèmes qui se produisent avec **Power BI Desktop**. Nous examinons régulièrement les problèmes qui peuvent affecter de nombreux clients afin de les inclure dans nos articles.

Si le problème avec le lancement de **Power BI Desktop** n’est pas associé à la passerelle de données locale, ou lorsque les solutions précédentes ne fonctionnent pas, vous pouvez soumettre un incident au [support Power BI](https://support.powerbi.com) (https://support.powerbi.com) pour aider à identifier et résoudre votre problème.

Si, à l’avenir, vous rencontrez d’autres problèmes avec **Power BI Desktop** (nous espérons qu’ils seront peu nombreux voire inexistants), il est utile d’activer le suivi et de collecter des fichiers journaux, pour mieux isoler et identifier le problème. Pour activer le suivi, sélectionnez **Fichier > Options et paramètres > Options**, sélectionnez **Diagnostics**, puis activez **Activer le suivi** sous *Options de diagnostic*. Nous sommes conscients que **Power BI Desktop** doit être en cours d’exécution pour définir cette option, qui est plus utile pour les problèmes futurs associés au lancement de **Power BI Desktop**.

