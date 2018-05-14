---
title: Utilisation des étiquettes de hiérarchie incluses dans Power BI Desktop
description: Utilisation des étiquettes de hiérarchie incluses dans Power BI Desktop
services: powerbi
documentationcenter: ''
author: davidiseminger
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 05/02/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 974194cb04701e2dc21814a0945227ad9c4b770c
ms.sourcegitcommit: f679c05d029ad0765976d530effde744eac23af5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="use-inline-hierarchy-labels-in-power-bi-desktop"></a>Utilisation des étiquettes de hiérarchie incluses dans Power BI Desktop
**Power BI Desktop** prend en charge l’utilisation des **étiquettes de hiérarchie incluses**, la première des deux fonctionnalités visant à améliorer l’exploration hiérarchique. La deuxième fonctionnalité, qui est en cours de développement, est la possibilité d’utiliser des étiquettes de hiérarchie imbriquées (revenez régulièrement, nous mettons à jour le contenu fréquemment).   

## <a name="how-inline-hierarchy-labels-work"></a>Fonctionnement des étiquettes de hiérarchie incluses
Avec les étiquettes de hiérarchie incluses, vous pouvez voir les étiquettes de la hiérarchie lorsque vous développez des éléments visuels à l’aide de la fonctionnalité **Développer tout**. Un grand avantage de pouvoir voir ces étiquettes de hiérarchie est que vous pouvez également choisir de **trier** avec les différentes étiquettes de hiérarchie lorsque vous développez vos données hiérarchiques.

### <a name="using-the-built-in-expand-all-feature-without-sorting-by-hierarchy-labels"></a>Avec la fonctionnalité Développer tout intégrée (sans trier par étiquettes de hiérarchie)
Avant de voir les étiquettes de hiérarchie incluses en action, nous allons maintenant examiner le comportement par défaut de la fonctionnalité **Développer tout**. Cela nous aidera à comprendre (et apprécier) l’utilité des étiquettes de hiérarchie incluses.

L’image suivante montre un graphique à barres de ventes annuelles. Lorsque vous cliquez avec le bouton droit dessus, vous pouvez choisir **Développer tout**.

![](media/desktop-inline-hierarchy-labels/inlinehierarchy_4.png)

Une fois que vous sélectionnez **Développer tout**, l’élément visuel développe la hiérarchie de dates *d’année* à *trimestre*, comme illustré dans l’image suivante.

![](media/desktop-inline-hierarchy-labels/inlinehierarchy_5.png)

Notez que les étiquettes *Année* et *Trimestre* sont présentées incluses ensemble... ce schéma d’étiquetage continue lorsque vous utilisez **Développer tout** jusqu’au bas de la hiérarchie.

![](media/desktop-inline-hierarchy-labels/inlinehierarchy_6.png)

C’est ainsi que se comporte la hiérarchie *Date*, associée aux champs présentant un type de données *date/heure*. Passons à la section suivante, et découvrons comment la fonctionnalité d’étiquettes de hiérarchie incluses diffère.

### <a name="using-inline-hierarchy-labels"></a>Utilisation des étiquettes de hiérarchie incluses
Regardons maintenant un graphique différent, avec des données ayant une hiérarchie informelle. Dans l’élément visuel suivant, nous avons un graphique à barres avec le **Montant des ventes**, et *Couleur* en tant qu’axe. Dans ces données, *Couleur* et *Classe* forment une hiérarchie informelle. De là, vous pouvez sélectionner à nouveau *Développer tout* pour explorer la hiérarchie.

![](media/desktop-inline-hierarchy-labels/inlinehierarchy_7.png)

Sélectionner **Développer tout** affiche le prochain niveau avec l’affichage intégré d’étiquettes de hiérarchie. Par défaut, les hiérarchies incluses sont triées par la valeur de mesure, dans ce cas, **SalesAmount**. Avec les étiquettes de hiérarchie incluses activées, vous pouvez aussi choisir de trier ces données par hiérarchie, en sélectionnant le bouton de points de suspension dans le coin supérieur droit (le **...**), puis en sélectionnant **Trier par > Classe Couleur** comme indiqué dans l’image suivante.

![](media/desktop-inline-hierarchy-labels/inlinehierarchy_8.png)

Une fois la **Classe Couleur** sélectionnée, les données sont triées en fonction de la sélection de hiérarchie informelle, comme illustré dans l’image suivante.

![](media/desktop-inline-hierarchy-labels/inlinehierarchy_9.png)

> [!NOTE]
> La fonctionnalité d’étiquettes de hiérarchie incluses n’autorise pas encore le tri de la hiérarchie de temps intégrée par valeur, le tri se fait uniquement par ordre hiérarchique.
> 
> 

## <a name="troubleshooting"></a>Résolution des problèmes
Il est possible que vos éléments visuels soient coincés dans un état de niveau de hiérarchie inclus développé. Dans certains cas, vous constaterez que certains de vos éléments visuels sont bloqués dans le mode dans lequel ils ont été développés, auquel cas l’exploration ascendante ne fonctionne pas. Cela peut se produire si vous avez effectué les étapes suivantes (la solution à ce problème est données *après* ces étapes) :

Les étapes qui peuvent bloquer vos éléments visuels dans un état développé :

1. Vous activez la fonctionnalité **Étiquette de hiérarchie incluse**
2. Vous créez des éléments visuels avec des hiérarchies
3. Ensuite, vous utilisez **Développer tout** et enregistrez votre fichier
4. Vous *désactivez* alors la fonctionnalité **d’étiquettes de hiérarchie incluses** et redémarrez Power BI Desktop
5. Vous rouvrez ensuite votre fichier

Si vous avez accidentellement suivi ces étapes et que vos éléments visuels sont bloqués en mode développé, vous pouvez corriger le problème de la façon suivante :

1. Réactivez la fonctionnalité **d’étiquettes de hiérarchie incluses** et redémarrez Power BI Desktop
2. Rouvrez votre fichier et explorez à nouveau vos éléments visuels affectés vers le haut de la hiérarchie
3. Enregistrez votre fichier
4. Désactivez la fonctionnalité **d’étiquettes de hiérarchie incluses** et redémarrez Power BI Desktop
5. Rouvrez votre fichier

Vous pouvez également simplement effacer votre élément visuel et le recréer.

