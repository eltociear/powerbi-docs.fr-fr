---
title: Basé sur une expression de titres dans Power BI Desktop
description: Création de titres dynamiques dans Power BI Desktop qui changent en fonction des expressions par programmation, à l’aide de la mise en forme conditionnelle par programmation
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: reference
ms.date: 04/10/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: b90ef66d2c118a70f1b18ed4fe302ce1db23e45c
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "64769742"
---
# <a name="expression-based-titles-in-power-bi-desktop"></a>Basé sur une expression de titres dans Power BI Desktop

Vous pouvez créer dynamique, personnaliser les titres de vos éléments visuels Power BI. En créant des Expressions DAX (Data Analysis) basé sur les champs, les variables ou les autres éléments de programmation, les titres de vos visuels peuvent d’ajuster automatiquement en fonction des besoins. Ces modifications sont basées sur les filtres, les sélections, ou autres interactions de l’utilisateur et les configurations.

![Option de mise en forme conditionnelle de capture d’écran de Power BI Desktop](media/desktop-conditional-formatting-visual-titles/expression-based-title-01.png)

Création de titres dynamiques, parfois appelé *basée sur une expression de titres*, est simple. 

## <a name="create-a-field-for-your-title"></a>Créer un champ pour votre titre

La première étape de création d’un titre d’expression consiste à créer un champ dans votre modèle à utiliser pour le titre. 

Il existe toutes sortes de manières créatives pour que votre titre visual reflètent ce que vous voulez qu’il dise, ou ce que vous voulez express. Jetons un œil à quelques exemples.

Vous pouvez créer une expression qui modifie selon le contexte de filtre qui reçoit de l’élément visuel pour le nom de la marque du produit. L’illustration suivante montre la formule DAX pour ce champ.

![Formule de la capture d’écran de DAX](media/desktop-conditional-formatting-visual-titles/expression-based-title-02.png)

Un autre exemple est à l’aide d’un titre dynamique qui change en fonction de langage ou la culture de l’utilisateur. Vous pouvez créer des titres de spécifique à la langue dans une mesure DAX à l’aide de la `USERCULTURE()` (fonction). Cette fonction retourne le code de culture pour l’utilisateur, en fonction de leur système d’exploitation ou les paramètres du navigateur. Vous pouvez utiliser l’instruction switch DAX suivante pour sélectionner la valeur traduite correcte. 

```
SWITCH (
  USERCULTURE(),
  "de-DE", “Umsatz nach Produkt”,
  "fr-FR", “Ventes par produit”,
  “Sales by product”
)
```

Ou vous pouvez récupérer la chaîne à partir d’une table de recherche qui contient toutes les traductions. Vous placez cette table dans votre modèle. 

Voici quelques exemples que vous pouvez utiliser pour créer des titres dynamiques et basé sur une expression pour vos éléments visuels dans Power BI Desktop. Ce que vous pouvez faire avec vos titres sont limitées uniquement par votre imagination et votre modèle.


## <a name="select-your-field-for-your-title"></a>Sélectionnez le champ de titre de votre

Une fois que vous avez créé l’expression DAX pour le champ que vous créez dans votre modèle, vous devez l’appliquer au titre de votre élément visuel.

Pour sélectionner le champ et l’appliquer, accédez à la **visualisations** volet. Dans le **Format** zone, sélectionnez **titre** pour afficher les options de titre pour l’élément visuel. 

Lorsque vous cliquez sur **texte du titre**, un menu contextuel s’affiche qui vous permet de sélectionner ***fx * mise en forme conditionnelle**. Lorsque vous sélectionnez cet élément de menu, un **texte du titre** boîte de dialogue s’affiche. 

![Boîte de dialogue de capture d’écran de titre texte](media/desktop-conditional-formatting-visual-titles/expression-based-title-02b.png)

Dans cette fenêtre, vous pouvez sélectionner le champ que vous avez créé pour l’utiliser pour votre titre.

## <a name="limitations-and-considerations"></a>Considérations et limitations

Il existe quelques limitations à l’implémentation actuelle de l’expression basée les titres des visuels :

* Mise en forme basée sur l’expression n’est pas actuellement pris en charge Python visuels, les éléments visuels R ou le visuel de facteurs d’influence clés.
* Le champ que vous créez pour le titre doit être un type de données de chaîne. Mesures qui retournent des nombres ou date/heure (ou tout autre type de données) ne sont pas actuellement pris en charge.

## <a name="next-steps"></a>Étapes suivantes

Cet article décrit comment créer des expressions DAX qui convertissent les titres de vos éléments visuels dans des champs dynamiques peuvent changer quand les utilisateurs interagissent avec vos rapports. Que vous trouverez les articles suivants utiles également.

* [Utiliser l’extraction de cross-report dans Power BI Desktop](desktop-cross-report-drill-through.md)
* [Utiliser une extraction dans Power BI Desktop](desktop-drillthrough.md)