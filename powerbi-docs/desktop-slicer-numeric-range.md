---
title: "Utiliser le Sélecteur de plages numériques dans Power BI Desktop"
description: "Découvrez comment utiliser un segment pour restreindre des plages numériques dans Power BI Desktop"
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
ms.date: 01/24/2018
ms.author: davidi
ms.openlocfilehash: cee6cd859507105b7fc0c7e7075478d3a876f7bb
ms.sourcegitcommit: 7249ff35c73adc2d25f2e12bc0147afa1f31c232
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="use-the-numeric-range-slicer-in-power-bi-desktop"></a>Utiliser le Sélecteur de plages numériques dans Power BI Desktop
Le **Sélecteur de plages numériques** vous permet d’appliquer toutes sortes de filtres à toute colonne numérique dans votre modèle de données. Vous pouvez choisir de filtrer les nombres compris **entre** des valeurs, des nombres **inférieurs ou égaux** à une valeur, ou des nombres **supérieurs ou égaux** à une valeur. Bien que cette fonction puisse sembler simple, elle est très utile pour filtrer vos données.

![](media/desktop-slicer-numeric-range/slicer-numeric-range_2.png)

## <a name="using-the-numeric-range-slicer"></a>Utilisation du Sélecteur de plages numériques
Vous pouvez utiliser le Sélecteur de plages numériques comme tout autre segment. Créez simplement un visuel de **segment** pour votre rapport, puis sélectionnez une valeur numérique pour **Champ**. Dans l’image suivante, le champ *UnitPrice* est sélectionné.

![](media/desktop-slicer-numeric-range/slicer-numeric-range_3.png)

Sélectionnez le signe ^ dans l’angle supérieur droit du **Sélecteur de plages numériques** pour afficher un menu.

![](media/desktop-slicer-numeric-range/slicer-numeric-range_4.png)

Pour la plage numérique, vous avez le choix entre les trois sélections suivantes :

* Entre
* Inférieur ou égal à
* Supérieur ou égal à

Lorsque vous sélectionnez **Entre** dans le menu, un curseur s’affiche qui vous permet de filtrer les valeurs numériques comprises entre les nombres définis. En plus d’utiliser la barre du curseur, vous pouvez cliquer dans chaque zone pour y entrer des valeurs. Cela est pratique lorsque vous voulez segmenter sur des nombres entiers spécifiques, car la granularité du déplacement de la barre du curseur rend difficile la sélection précise d’un nombre.

Dans l’image suivante, la page de rapport est filtrée pour les valeurs *UnitPrice* comprises entre 500 et 1 500.

![](media/desktop-slicer-numeric-range/slicer-numeric-range_5.png)

Lorsque nous sélectionnons **Inférieur ou égal à**, la poignée de gauche (valeur inférieure) de la barre du curseur disparaît, et nous ne pouvons ajuster que la limite supérieure de la barre du curseur. Dans l’image suivante, nous avons positionné la barre du curseur sur 497.17.

![](media/desktop-slicer-numeric-range/slicer-numeric-range_6.png)

Enfin, si nous sélectionnons l’option **Supérieur ou égal à**, la poignée de droite (valeur supérieure) de la barre du curseur disparaît, et nous ne pouvons ajuster que la valeur inférieure, comme illustré dans l’image suivante. À présent, seuls les articles dont la valeur *UnitPrice* est supérieure ou égale à 750.56 s’affichent dans les visuels de la page de rapport.

![](media/desktop-slicer-numeric-range/slicer-numeric-range_7.png)

## <a name="limitations-and-considerations"></a>Considérations et limitations
Les considérations et limitations suivantes s’appliquent actuellement à l’utilisation du **Sélecteur de plages numériques**.

* Le **Sélecteur de plages numériques** filtre actuellement chaque ligne sous-jacente dans les données, mais pas de valeur agrégée. Par exemple, en cas d’utilisation d’un champ *Montant des ventes*, chaque transaction basée sur un *Montant des ventes* est filtrée, mais pas la somme *Montant des ventes* pour chaque point de données d’un visuel.
* Le Sélecteur de plages numériques ne fonctionne pas avec des mesures.
* Actuellement, le **Sélecteur de plages numériques** est disponible uniquement dans **Power BI Desktop**. Si un rapport utilisant le **Sélecteur de plages numériques** est publié sur le **Service Power BI**, le filtre reste appliqué, mais apparaît comme un segment de liste.

