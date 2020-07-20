---
title: Importer et afficher des indicateurs de performance clés (KPI)dans Power BI
description: Importation et affichage d’indicateurs de performance clés (KPI)
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: b12cc24c7ddddd0bc866a3bbeb23e0c7097711db
ms.sourcegitcommit: c83146ad008ce13bf3289de9b76c507be2c330aa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2020
ms.locfileid: "86215242"
---
# <a name="import-and-display-kpis-in-power-bi"></a>Importer et afficher des indicateurs de performance clés (KPI)dans Power BI
Avec **Power BI Desktop**, vous pouvez importer et afficher les indicateurs de performance clés (KPI, Key Performance Indicator) dans des tables, matrices et cartes.

Pour importer et afficher les indicateurs de performance clés, procédez comme suit.

1. Démarrez avec un classeur Excel disposant d’un modèle Power Pivot et de KPI. Cet exercice utilise un classeur nommé *KPIs*.

1. Importez le classeur Excel dans Power BI, en utilisant **Fichier -> Importer -> Contenu du classeur Excel**. Vous pouvez également [découvrir comment importer des classeurs](../connect-data/desktop-import-excel-workbooks.md). 

1. Après l’importation dans Power BI, votre KPI s’affiche dans le volet **Champs**, avec l’icône de ![feu de circulation](media/desktop-import-and-display-kpis/traffic.png). Pour utiliser un KPI dans votre rapport, développez son contenu, pour exposer les champs **Valeur**, **Objectif** et **État**.

    ![Capture d’écran de Power BI Desktop montrant le KPI Delta développé dans le volet Champs.](media/desktop-import-and-display-kpis/desktoppreviewfeatureon2.png)
 
1. Les KPI importés sont idéalement adaptés aux types de visualisation standard, comme le type **Table**. Power BI inclut aussi le type de visualisation **KPI**, qui ne doit être utilisé que pour la création de nouveaux KPI.
   
    ![Capture d’écran de Power BI Desktop montrant les champs Table1 sélectionnés dans le volet Champ.](media/desktop-import-and-display-kpis/desktoppreviewfeatureon3.png)

C’est tout. Vous pouvez utiliser des indicateurs de performance clés pour mettre en évidence des tendances, une progression ou d’autres indicateurs importants.
