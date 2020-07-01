---
title: Titres basés sur des expressions dans Power BI Desktop
description: Créer des titres dynamiques dans Power BI Desktop qui changent en fonction d’expressions de programmation à l’aide de la mise en forme de programmation conditionnelle
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 04/10/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: e3b9e4fd1fea6c1fa76077b95ba6a93225753593
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85222036"
---
# <a name="expression-based-titles-in-power-bi-desktop"></a>Titres basés sur des expressions dans Power BI Desktop

Vous pouvez créer des titres dynamiques et personnalisés pour vos visuels Power BI. En créant des expressions DAX (Data Analysis Expressions) basées sur des champs, des variables ou d’autres éléments de programmation, les titres de vos visuels peuvent s’ajuster automatiquement si nécessaire. Ces modifications sont basées sur les filtres, les sélections ou d’autres configurations et interactions de l’utilisateur.

![Capture d’écran de l’option de mise en forme conditionnelle de Power BI Desktop](media/desktop-conditional-formatting-visual-titles/expression-based-title-01.png)

La création de titres dynamiques, parfois appelés *titres basés sur des expressions* est simple. 

## <a name="create-a-field-for-your-title"></a>Créer un champ pour votre titre

La première étape de la création d’un titre basé sur une expression consiste à créer un champ dans votre modèle à utiliser pour le titre. 

Il existe toutes sortes de méthodes créatives pour que le titre du visuel reflète ce que vous souhaitez qu’il indique ou ce que vous souhaitez exprimer. Examinons quelques exemples.

Vous pouvez créer une expression qui change en fonction du contexte de filtre que le visuel reçoit pour le nom de marque du produit. L’illustration suivante montre la formule DAX pour un champ de ce type.

![Capture d’écran d’une formule DAX](media/desktop-conditional-formatting-visual-titles/expression-based-title-02.png)

Un autre exemple consiste à utiliser un titre dynamique qui change en fonction de la langue ou de la culture de l’utilisateur. Vous pouvez créer des titres propres à une langue dans une mesure DAX à l’aide de la fonction `USERCULTURE()`. Cette fonction retourne le code de culture de l’utilisateur, en fonction des paramètres de son système d’exploitation ou de son navigateur. Vous pouvez utiliser l’instruction switch DAX suivante pour sélectionner la valeur traduite correcte. 

```
SWITCH (
  USERCULTURE(),
  "de-DE", “Umsatz nach Produkt”,
  "fr-FR", “Ventes par produit”,
  “Sales by product”
)
```

Vous pouvez également récupérer la chaîne d’une table de choix contenant toutes les traductions. Vous pouvez placer cette table dans votre modèle. 

Voici quelques exemples que vous pouvez utiliser pour créer des titres dynamiques, basés sur des expressions pour vos visuels dans Power BI Desktop. Ce que vous pouvez faire avec vos titres est limité uniquement par votre imagination et votre modèle.


## <a name="select-your-field-for-your-title"></a>Sélectionner votre champ pour votre titre

Une fois que vous avez créé l’expression DAX pour le champ que vous créez dans votre modèle, vous devez l’appliquer au titre de votre visuel.

Pour sélectionner le champ et l’appliquer, accédez au volet **Visualisations**. Dans la zone **Format**, sélectionnez **Titre** pour afficher les options de titre du visuel. 

Lorsque vous cliquez avec le bouton droit sur **Texte du titre**, un menu contextuel s’affiche pour vous permettre de sélectionner **Mise en forme conditionnelle<em>fx</em>** . Lorsque vous sélectionnez cet élément de menu, une boîte de dialogue **Texte du titre** s’affiche. 

![Capture d’écran de la boîte de dialogue Texte du titre](media/desktop-conditional-formatting-visual-titles/expression-based-title-02b.png)

Dans cette fenêtre, vous pouvez sélectionner le champ que vous avez créé pour votre titre.

## <a name="limitations-and-considerations"></a>Considérations et limitations

Il existe quelques restrictions à l’implémentation actuelle des titres basés sur des expressions pour les visuels :

* La mise en forme basée sur les expressions n’est pas prise en charge actuellement sur les visuels Python ou R, ni sur les visuels d’influenceurs clés.
* Le champ que vous créez pour le titre doit correspondre à des données de type chaîne. Les mesures qui retournent des nombres ou une date/heure (ou tout autre type de données) ne sont pas prises en charge actuellement.
* Les titres basés sur les expressions ne sont pas reportés lorsque vous épinglez un visuel à un tableau de bord.

## <a name="next-steps"></a>Étapes suivantes

Cet article décrit comment créer des expressions DAX qui transforment les titres de vos visuels en champs dynamiques pouvant changer lorsque des utilisateurs interagissent avec vos rapports. Vous trouverez également utiles les articles suivants.

* [Mise en forme conditionnelle dans les tables](desktop-conditional-table-formatting.md)
* [Use cross-report drillthrough in Power BI Desktop](desktop-cross-report-drill-through.md) (Utiliser une extraction interrapport dans Power BI Desktop)
* [Utiliser une extraction dans Power BI Desktop](desktop-drillthrough.md)
