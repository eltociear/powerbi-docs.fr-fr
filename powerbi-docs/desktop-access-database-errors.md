---
title: Résoudre les problèmes d’importation de fichiers Access et .XLS dans Power BI Desktop
description: Résoudre des problèmes d’importation de bases de données Access et de feuilles de calcul .XLS dans Power BI Desktop et Power Query
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/21/2019
ms.author: davidi
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 83a3cc769ea9451ffa5320710bd0f04934d51393
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73878998"
---
# <a name="resolve-issues-importing-access-and-xls-files-in-power-bi-desktop"></a>Résoudre les problèmes d’importation de fichiers Access et .XLS dans Power BI Desktop

Dans Power BI Desktop, les bases de données Access et les premières versions de classeurs Excel (fichiers .XLS de type Excel 97-2003) utilisent le *moteur de base de données Access*. Trois situations courantes peuvent empêcher le moteur de base de données Access de fonctionner correctement.

## <a name="situation-1-no-access-database-engine-is-installed"></a>Situation 1 : aucun moteur de base de données Access n’est installé.

Si le message d’erreur de Power BI Desktop indique que le moteur de base de données Access n’est pas installé, vous devez installer la version 32 bits ou 64 bits du moteur de base de données Access correspondant à votre version de Power BI Desktop. Vous pouvez installer le moteur de base de données Access à partir de la [page des téléchargements](https://www.microsoft.com/download/details.aspx?id=13255).

>[!NOTE]
>Si la version (32 bits ou 64 bits) du moteur de base de données Access installé diffère de celle de votre installation Microsoft Office, les applications Office ne pourront pas utiliser le moteur de base de données Access.

## <a name="situation-2-the-access-database-engine-bit-version-32-bit-or-64-bit-is-different-from-your-power-bi-desktop-bit-version"></a>Situation 2 : la version (32 bits ou 64 bits) du moteur de base de données Access diffère de celle de Power BI Desktop.

Cette situation se produit souvent quand la version installée de Microsoft Office est 32 bits alors que la version installée de Power BI Desktop est 64 bits. L’inverse peut également se produire, entraînant une incompatibilité des versions dans les deux cas. Si vous utilisez un abonnement Office 365, reportez-vous à la [situation 3](#situation-3-trouble-using-access-or-xls-files-with-an-office-365-subscription) (problème et résolution différents). Toutes les solutions suivantes permettent de remédier à cette erreur d’incompatibilité de version de bits :

### <a name="solution-1"></a>Solution 1

Modifiez la version (32 bits ou 64 bits) de Power BI Desktop de façon à ce qu’elle corresponde à la version de votre installation Microsoft Office. 

1. Pour modifier la version de Power BI Desktop, désinstallez Power BI Desktop, puis installez la version de Power BI Desktop correspondant à votre installation Office. 

1. Pour sélectionner une version de Power BI Desktop, sélectionnez **Options de téléchargement avancées** dans la page de téléchargement de Power BI Desktop.
   
   ![Options de téléchargement avancées dans la page de téléchargement de Power BI Desktop](media/desktop-access-database-errors/desktop-access-errors-1.png)
   
1. Dans la page de téléchargement qui s’affiche, choisissez votre langue, puis cliquez sur le bouton **Télécharger** . 
 
1. Dans l’écran qui s’affiche, cochez la case en regard de PBIDesktop.msi pour la version 32 bits ou de PBIDesktop_x64.msi pour la version 64 bits. 

   Dans la capture d’écran suivante, la version 64 bits est sélectionnée.
   
   ![Choisir le type de téléchargement de Power BI Desktop](media/desktop-access-database-errors/desktop-access-errors-2.png)
   
   >[!NOTE]
   >Si vous utilisez la version 32 bits de Power BI Desktop, lors de la création de modèles de données très volumineux, il se peut que vous rencontriez des problèmes d’insuffisance de mémoire.

### <a name="solution-2"></a>Solution 2

Modifiez la version (32 bits ou 64 bits) de Microsoft Office de façon à ce qu’elle corresponde à la version de votre installation de Power BI Desktop :

1. Désinstaller Microsoft Office

2. Installez la version d’Office correspondant à votre installation de Power BI Desktop.

### <a name="solution-3"></a>Solution 3

Si l’erreur se produit quand vous tentez d’ouvrir un fichier .XLS (classeur Excel 97-2003), vous pouvez éviter d’utiliser le moteur de base de données Access en ouvrant le fichier .XLS dans Excel, puis en l’enregistrant au format .XLSX.

### <a name="solution-4"></a>Solution 4

Si les trois solutions précédentes sont irréalisables, vous pouvez installer les deux versions du moteur de base de données Access. Toutefois, cette solution de contournement n’est pas recommandée. L’installation des deux versions résout ce problème pour Power Query pour Excel et Power BI Desktop, mais génère des erreurs et des problèmes pour toute application qui utilise automatiquement (par défaut) la version du moteur de base de données Access installée en premier lieu. 

Pour installer les deux versions (32 et 64 bits) du moteur de base de données Access, effectuez les étapes suivantes :

1. Installez les deux versions (32 et 64 bits) du moteur de base de données Access à partir de la [page de téléchargement](https://www.microsoft.com/download/details.aspx?id=13255). 

1. Exécutez chaque version du moteur de base de données Access avec le commutateur */passive*. Par exemple :
   
       c:\users\joe\downloads\AccessDatabaseEngine.exe /passive
   
       c:\users\joe\downloads\AccessDatabaseEngine_x64.exe /passive

## <a name="situation-3-trouble-using-access-or-xls-files-with-an-office-365-subscription"></a>Situation 3 : problèmes d’utilisation de fichiers Access ou XLS avec un abonnement Office 365

Si vous utilisez un abonnement Office 365 (**Office 2013** ou **Office 2016**), le fournisseur de moteur de base de données Access est enregistré dans un emplacement de registre virtuel *uniquement* accessible par les processus Microsoft Office. Le moteur Mashup (qui est chargé d’exécuter les versions d’Excel et Power BI Desktop non associées à Office 365), qui n’est pas un processus Office, ne peut donc pas utiliser le fournisseur de moteur de base de données Access.

Pour remédier à cette situation, vous pouvez [télécharger et installer le package redistribuable de moteur de base de données Access](https://www.microsoft.com/download/details.aspx?id=13255) qui correspond à la version (32 ou 64 bits) de votre installation de Power BI Desktop. Consultez les sections précédentes de cet article pour plus d’informations sur les versions (32 ou 64 bits).

## <a name="other-situations-that-can-cause-import-issues"></a>Autres situations pouvant entraîner des problèmes d’importation

Nous nous efforçons autant que possible de résoudre les problèmes qui se produisent avec les fichiers XLS ou Access. Si vous rencontrez un problème qui n’est pas abordé dans cet article, envoyez une question à son sujet au [support Power BI](https://powerbi.microsoft.com/support/). Nous examinons régulièrement les problèmes qui peuvent affecter de nombreux clients afin de les inclure dans nos articles.

