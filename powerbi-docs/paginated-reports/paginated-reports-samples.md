---
title: Exemples de rapports paginés Power BI
description: Dans cet article, vous allez découvrir comment télécharger et utiliser des exemples de rapports paginés Power BI.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: swgupt
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 11/01/2020
ms.openlocfilehash: cf0e6a6e7cd40a5b8bb97560caf94b71c1b48e7a
ms.sourcegitcommit: ccf53e87ff7cba1fcd9d2cca761a561e62933f90
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/04/2020
ms.locfileid: "93324020"
---
# <a name="sample-power-bi-paginated-reports"></a>Exemples de rapports paginés Power BI


[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)]

Cet article fournit des informations et des liens vers plusieurs exemples de rapports paginés Power BI que vous pouvez télécharger et explorer. Vous allez découvrir plusieurs méthodes d’utilisation des rapports paginés.

## <a name="prerequisites"></a>Prérequis

- Vous pouvez partager ces rapports en ligne, sans aucune modification. Pour cela, vous avez besoin d’une licence Power BI Pro. Inscrivez-vous pour [essayer gratuitement une licence Power BI Pro](../fundamentals/service-self-service-signup-for-power-bi.md#sign-up-for-an-individual-trial-of-power-bi-pro).
- Vous devez également accéder à un espace de travail Power BI dans une [capacité Premium](../admin/service-premium-what-is.md).
- Pour modifier ces rapports, vous devez [installer Power BI Report Builder](https://aka.ms/pbireportbuilder) à partir du centre de téléchargement Microsoft.
- Vous êtes maintenant prêt à [télécharger ces exemples de rapports paginés](https://github.com/microsoft/Reporting-Services/tree/master/PaginatedReportSamples) sur GitHub. Vous n’avez pas besoin d’un compte GitHub. 


## <a name="invoice"></a>Facture

:::image type="content" source="media/paginated-reports-samples/paginated-report-invoice.png" alt-text="Capture d’écran d’un exemple de facture sous forme de rapport paginé Power BI.":::


Ce rapport paginé est une facture autonome. Dans notre scénario, nous voulons faire de ce rapport une facture qui soit parfaitement nette à l’impression. Elle doit montrer les ventes totales, en indiquant la description de chaque article, les quantités, les remises et les prix.

Cet exemple met en évidence des caractéristiques uniques permettant de créer des factures professionnelles, comme :  

- Un tableau matriciel (région de données sous-jacente aux tables et aux matrices). Il affiche un contenu propre à l’utilisateur et généré dynamiquement, ainsi qu’un thème.
- Une région de données rectangulaire placée sur chaque ligne du tableau matriciel dans le corps du rapport.
- Des éléments de rapport, tels que des zones de texte et des lignes.
- Un paramètre de rapport permettant de sélectionner le contenu dynamiquement. Le contenu affiché s’applique à un sujet à l’aide d’espaces réservés d’expressions. 

Source de données : Inclus dans le fichier .rdl

## <a name="labels"></a>Étiquettes

:::image type="content" source="media/paginated-reports-samples/paginated-report-labels.png" alt-text="Capture d’écran des étiquettes du rapport paginé.":::

Cet exemple correspond à un rapport paginé autonome. Il s’agit d’un rapport à plusieurs colonnes parfaitement dimensionné pour s’adapter à la mise en page du modèle d’étiquette de publipostage. 

Les rapports d’étiquettes sont simples, mais ils comportent quelques caractéristiques uniques pour la création d’étiquettes paginées :

- Un tableau matriciel avec un nombre fixe de colonnes (trois) et un espacement de colonnes défini.
- Région de données rectangulaire qui se répète sur toutes les lignes et colonnes de la page imprimée.
- Un paramètre de rapport permettant de sélectionner le contenu à afficher dans chaque région de données rectangulaire.

Source de données : Inclus dans le fichier .rdl

## <a name="mailing-letter"></a>Lettre postale

:::image type="content" source="media/paginated-reports-samples/paginated-report-letter.png" alt-text="Capture d’écran d’un exemple de lettre sous forme de rapport paginé Power BI.":::

Cet exemple de rapport paginé autonome est conçu pour créer des lettres de publipostage professionnelles. Dans notre scénario, nous voulons faire de ce rapport une lettre comprenant du contenu dynamique, qui soit parfaitement nette à l’impression.

Cet exemple présente des caractéristiques uniques, comme : 

- Une région de données rectangulaire placée dans différentes sections du corps du rapport. 
- Des images permettant de personnaliser la lettre. 
- Une région de données de tableau matriciel (région de données sous-jacente aux tables et aux matrices). Le tableau matriciel affiche un contenu propre à l’utilisateur et généré dynamiquement.
- Des éléments de rapport, tels que des zones de texte et des lignes.
- Un paramètre de rapport permettant de sélectionner le contenu dynamiquement. Le contenu affiché s’applique à un sujet à l’aide d’espaces réservés d’expressions. 

Source de données : Inclus dans le fichier .rdl

## <a name="transcript"></a>Transcription

:::image type="content" source="media/paginated-reports-samples/paginated-report-transcript.png" alt-text="Capture d’écran d’un exemple de transcription sous forme de rapport paginé Power BI.":::

Dans notre scénario, nous voulons faire de ce rapport une transcription qui soit parfaitement nette à l’impression. Il doit contenir du contenu dynamique sur la description et les dates du programme pour chaque étudiant.

Cet exemple de rapport paginé autonome présente des caractéristiques uniques, comme : 

- Une région de données de tableau matriciel (région de données sous-jacente aux tables et aux matrices). Le tableau matriciel affiche un contenu propre à l’utilisateur et généré dynamiquement, sous la forme de groupes de lignes imbriquées.
- Des régions de données rectangulaires placées dans différentes sections du corps du rapport.
- Des éléments de rapport, tels que des zones de texte et des lignes.

Source de données : Inclus dans le fichier .rdl

## <a name="sales-performance"></a>Performances des ventes

:::image type="content" source="media/paginated-reports-samples/paginated-report-sales-performance.png" alt-text="Capture d’écran d’un exemple de rapport paginé Power BI concernant les performances de ventes.":::

L’exemple « Country Sales Performance » est un rapport paginé autonome. Dans notre scénario, nous voulons faire de ce rapport une facture qui soit parfaitement nette à l’impression, et qui montre le total des ventes et informations associées. Il présente les fonctionnalités suivantes :

- Utilisation d’un paramètre pour développer les détails du tableau
- En-têtes et pieds de page
- Éléments de rapport, tels que les zones de texte, les lignes et les rectangles utilisant des espaces réservés d’expressions
- Barres de données
- Courbes de tendance
- Panneaux de jauge

Source de données : Inclus dans le fichier .rdl
  
## <a name="next-steps"></a>Étapes suivantes

[Afficher un rapport paginé dans le service Power BI](../consumer/paginated-reports-view-power-bi-service.md)

D’autres questions ? [Posez vos questions à la communauté Power BI](https://community.powerbi.com/)