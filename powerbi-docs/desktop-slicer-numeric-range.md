---
title: Utiliser le Sélecteur de plages numériques dans Power BI Desktop
description: Découvrez comment utiliser un segment pour restreindre des plages numériques dans Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 05/07/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 1e380a6821db7207d14e719fa5e070af38196b97
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
---
# <a name="use-the-numeric-range-slicer-in-power-bi-desktop"></a>Utiliser le Sélecteur de plages numériques dans Power BI Desktop
Le **Sélecteur de plages numériques** vous permet d’appliquer toutes sortes de filtres à toute colonne numérique dans votre modèle de données. Vous pouvez choisir de filtrer les nombres compris **entre** des valeurs, des nombres **inférieurs ou égaux** à une valeur, ou des nombres **supérieurs ou égaux** à une valeur. Bien que cette fonction puisse sembler simple, elle est très utile pour filtrer vos données.

![Visuel avec sélecteur de plages numériques](media/desktop-slicer-numeric-range/desktop-slicer-numeric-range-0.png)

## <a name="using-the-numeric-range-slicer"></a>Utilisation du Sélecteur de plages numériques
Vous pouvez utiliser le Sélecteur de plages numériques comme tout autre segment. Créez simplement un visuel de **segment** pour votre rapport, puis sélectionnez une valeur numérique pour **Champ**. Dans l’image suivante, le champ *LineTotal* est sélectionné.

![Créer un sélecteur de plages numériques](media/desktop-slicer-numeric-range/desktop-slicer-numeric-range-1-create.png)

Sélectionnez la flèche pointant vers le bas dans l’angle supérieur droit du **sélecteur de plages numériques** pour afficher un menu.

![Menu du sélecteur de plages numériques](media/desktop-slicer-numeric-range/desktop-slicer-numeric-range-2-between.png)

Pour la plage numérique, vous avez le choix entre les trois sélections suivantes :

* Entre
* Inférieur ou égal à
* Supérieur ou égal à

Lorsque vous sélectionnez **Entre** dans le menu, un curseur s’affiche qui vous permet de filtrer les valeurs numériques comprises entre les nombres définis. En plus d’utiliser la barre du curseur, vous pouvez cliquer dans chaque zone pour y entrer des valeurs. C’est pratique quand vous souhaitez segmenter sur des nombres spécifiques, car la granularité du déplacement de la barre du curseur rend difficile la sélection précise d’un nombre.

Dans l’image suivante, la page de rapport est filtrée pour les valeurs *LineTotal* comprises entre 2500.00 et 6000.00.

![Sélecteur de plages numériques avec Entre](media/desktop-slicer-numeric-range/desktop-slicer-numeric-range-3-between-range.png)

Lorsque nous sélectionnons **Inférieur ou égal à**, la poignée de gauche (valeur inférieure) de la barre du curseur disparaît, et nous ne pouvons ajuster que la limite supérieure de la barre du curseur. Dans l’image suivante, nous avons positionné la valeur maximale de la barre du curseur sur 5928.19.

![Sélecteur de plages numériques avec Inférieur à](media/desktop-slicer-numeric-range/desktop-slicer-numeric-range-4-less-than.png)

Enfin, si nous sélectionnons l’option **Supérieur ou égal à**, la poignée de droite (valeur supérieure) de la barre du curseur disparaît, et nous ne pouvons ajuster que la valeur inférieure, comme illustré dans l’image suivante. À présent, seuls les articles dont la valeur *LineTotal* est supérieure ou égale à 4902.99 s’affichent dans les visuels de la page de rapport.

![Sélecteur de plages numériques avec Supérieur à](media/desktop-slicer-numeric-range/desktop-slicer-numeric-range-5-greater-than.png)

## <a name="snap-to-whole-numbers-with-the-numeric-range-slicer"></a>Aligner sur des nombres entiers avec le sélecteur de plages numériques

Un sélecteur de plages numériques s’aligne sur des nombres entiers, sauf s’il s’agit d’une plage décimale. avec précision sur des nombres entiers. 


## <a name="limitations-and-considerations"></a>Considérations et limitations
Les considérations et limitations suivantes s’appliquent actuellement à l’utilisation du **sélecteur de plages numériques** :

* Le **Sélecteur de plages numériques** filtre actuellement chaque ligne sous-jacente dans les données, mais pas de valeur agrégée. Par exemple, en cas d’utilisation d’un champ *Montant des ventes*, chaque transaction basée sur un *Montant des ventes* est filtrée, mais pas la somme *Montant des ventes* pour chaque point de données d’un visuel.
* Il ne fonctionne pas avec des mesures.
