---
title: Résoudre les problèmes d’importation de fichiers Access et .XLS dans Power BI Desktop
description: Résoudre des problèmes d’importation de bases de données Access et de feuilles de calcul .XLS dans Power BI Desktop et Power Query
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/06/2019
ms.author: davidi
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 6e504d472e4fabb5c336f36e1bef50ae4920ef17
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "65239764"
---
# <a name="resolve-issues-importing-access-and-xls-files-in-power-bi-desktop"></a>Résoudre les problèmes d’importation de fichiers Access et .XLS dans Power BI Desktop
Dans **Power BI Desktop**, les **bases de données Access** et les premières versions de **classeurs Excel** (fichiers .XLS de type Excel 97-2003) utilisent le *moteur de base de données Access*. Trois situations courantes peuvent empêcher le moteur de base de données Access de fonctionner correctement :

## <a name="situation-1-no-access-database-engine-installed"></a>Situation 1 : aucun moteur de base de données Access installé
Quand le message d’erreur de Power BI Desktop indique que le moteur de base de données Access n’est pas installé, vous devez installer la version 32 bits ou 64 bits du moteur de base de données Access correspondant à votre version de Power BI Desktop. Vous pouvez installer le moteur de base de données Access à partir de la [page des téléchargements](http://www.microsoft.com/download/details.aspx?id=13255).

>[!NOTE]
>Si la version (32 bits ou 64 bits) du moteur de base de données Access installé diffère de celle de votre installation Microsoft Office, les applications Office ne pourront pas utiliser le moteur de base de données Access.

## <a name="situation-2-the-access-database-engine-bit-version-32-bit-or-64-bit-is-different-from-your-power-bi-desktop-bit-version"></a>Situation 2 : la version (32 bits ou 64 bits) du moteur de base de données Access diffère de celle de Power BI Desktop
Cette situation se produit souvent quand la version installée de Microsoft Office est 32 bits alors que la version installée de Power BI Desktop est 64 bits. L’inverse peut également se produire et l’incompatibilité de version de bits se produit dans les deux cas (si vous utilisez un abonnement Office 365, consultez la section **Cas 3** qui présente un autre problème et sa résolution). Toutes les solutions suivantes permettent de remédier à cette erreur d’incompatibilité de version de bits :

1. Modifiez la version (32 bits ou 64 bits) de Power BI Desktop de façon à ce qu’elle corresponde à la version de votre installation Microsoft Office. Pour modifier la version de Power BI Desktop, désinstallez Power BI Desktop, puis installez la version de Power BI Desktop correspondant à votre installation Office. Pour sélectionner une version de Power BI Desktop, dans la page de téléchargement pour postes de travail, sélectionnez **Options de téléchargement avancées**.
   
   ![](media/desktop-access-database-errors/desktop-access-errors-1.png)
   
   Dans la page de téléchargement qui s’affiche, choisissez votre langue, puis cliquez sur le bouton **Télécharger** . Dans l’écran qui s’affiche, cochez la case en regard de PBIDesktop.msi pour la version 32 bits, ou PBIDesktop_x64.msi pour la version 64 bits. Dans l’écran suivant, la version 64 bits est sélectionnée.
   
   ![](media/desktop-access-database-errors/desktop-access-errors-2.png)
   
   >[!NOTE]
   >Si vous utilisez la version 32 bits de Power BI Desktop, lors de la création de modèles de données très volumineux, il se peut que vous rencontriez des problèmes d’insuffisance de mémoire.
2. Modifiez la version (32 bits ou 64 bits) de Microsoft Office de façon à ce qu’elle corresponde à la version de votre installation Power BI Desktop. Pour modifier la version (32 bits ou 64 bits) de Microsoft Office, désinstallez Office, puis installez la version d’Office correspondant à votre installation Power BI Desktop.
3. Si l’erreur s’est produite lors de la tentative d’ouverture d’un fichier .XLS (classeur Excel 97-2003), vous pouvez éviter d’utiliser le moteur de base de données Access en ouvrant le fichier .XLS dans Excel, puis en l’enregistrant au format .XLSX.
4. Si les trois solutions précédentes sont irréalisables, vous pouvez installer les deux versions du moteur de base de données Access, mais cette solution de contournement n’est *pas* recommandée. L’installation des deux versions résout ce problème pour Power Query pour Excel et Power BI Desktop, mais génère des erreurs et problèmes pour toute application qui utilise automatiquement (par défaut) la version du moteur de base de données Access installée en premier lieu. Pour installer les deux versions (32 bits et 64 bits) du moteur de base de données Access, [téléchargez-les](http://www.microsoft.com/download/details.aspx?id=13255), puis exécutez-les à l’aide du commutateur */passive*. Par exemple :
   
       c:\users\joe\downloads\AccessDatabaseEngine.exe /passive
   
       c:\users\joe\downloads\AccessDatabaseEngine_x64.exe /passive

## <a name="situation-3-trouble-using-access-or-xls-files-with-an-office-365-subscription"></a>Situation 3 : problèmes d’utilisation de fichiers Access ou XLS avec un abonnement Office 365
Si vous utilisez un abonnement Office 365 (**Office 2013** ou **Office 2016**), le fournisseur de moteur de base de données Access est enregistré dans un emplacement de registre virtuel *uniquement* accessible par les processus Office. Par conséquent, le moteur d’application web hybride (qui est chargé d’exécuter les versions d’Excel et Power BI Desktop non associées à Office 365), qui n’est pas un processus Office, ne peut pas utiliser le fournisseur de moteur de base de données Access.

Pour remédier à cette situation, vous pouvez [télécharger et installer le package redistribuable de moteur de base de données Access](http://www.microsoft.com/download/details.aspx?id=13255) qui correspond à la version de bits de votre installation de Power BI Desktop (voir les sections précédentes pour plus d’informations sur les versions de bits).

## <a name="other-situations-that-cause-import-issues"></a>Autres situations qui entraînent des problèmes d’importation
Nous nous efforçons autant que possible de résoudre les problèmes qui se produisent avec les fichiers XLS ou Access. Si vous rencontrez un problème qui n’est pas abordé dans cet article, envoyez une question à son sujet au [support Power BI](https://powerbi.microsoft.com/support/). Nous examinons régulièrement les problèmes qui peuvent affecter de nombreux clients afin de les inclure dans nos articles.

