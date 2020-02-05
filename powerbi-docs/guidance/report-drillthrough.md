---
title: Utiliser l’extraction de page de rapport
description: Conseils d’utilisation de l’extraction de page de rapport.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/28/2019
ms.author: v-pemyer
ms.openlocfilehash: 48942b30b84706c933ccef455129c84a67ac5a1b
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76040368"
---
# <a name="use-report-page-drillthrough"></a>Utiliser l’extraction de page de rapport

Cet article s’adresse à vous en tant qu’auteur de rapports Power BI. Il fournit des suggestions et des recommandations pour créer une [extraction de page de rapport](../desktop-drillthrough.md).

Il est recommandé de concevoir votre rapport de sorte à permettre aux utilisateurs d’obtenir le flux suivant :

1. Afficher une page de rapport.
2. Identifier un visuel à analyser de façon plus approfondie.
3. Cliquer avec le bouton droit sur le visuel à extraire.
4. Effectuer une analyse complémentaire.
5. Revenir à la page de rapport source.

## <a name="suggestions"></a>Suggestions

Nous vous suggérons de considérer deux types de scénarios d’extraction :

- [Profondeur supplémentaire](#additional-depth)
- [Perspective plus large](#broader-perspective)

### <a name="additional-depth"></a>Profondeur supplémentaire

Quand votre page de rapport présente des résultats synthétisés, une page d’extraction peut orienter les utilisateurs vers des détails au niveau de la transaction. Cette approche de conception leur permet de voir les transactions connexes et ce, uniquement lorsque cela est nécessaire.

L’exemple suivant montre ce qui se produit lorsqu’un utilisateur de rapport réalise une extraction à partir d’un récapitulatif des ventes mensuelles. La page d’extraction contient la liste détaillée des commandes pendant un mois spécifique.

![Un visuel de matrice intitulé « Récapitulatif des ventes » regroupe les ventes par année et par mois dans les lignes, et par pays dans les colonnes. Une page d’extraction s’affiche également.](media/report-drillthrough/suggestion-drillthrough-add-depth.png)

### <a name="broader-perspective"></a>Perspective plus large

Une page d’extraction permet d’obtenir l’effet inverse de la profondeur supplémentaire. Ce scénario est idéal pour extraire une vue globale.

L’exemple suivant montre ce qui se produit lorsqu’un utilisateur de rapport réalise une extraction à partir d’un code postal. La page d’extraction présente des informations générales sur ce code postal.

![Un visuel de table comporte trois colonnes : Zip Code, Average of Violation Points et Average of Grade Rating. La page d’extraction s’affiche également.](media/report-drillthrough/suggestion-drillthrough-broader-perspective.png)

## <a name="recommendations"></a>Recommandations

Au moment de la conception du rapport, nous vous recommandons d’adopter les pratiques suivantes :

- **Style :** Envisagez de concevoir votre page d’extraction pour qu’elle utilise le même thème et le même style que le rapport. Ainsi, les utilisateurs ont l’impression d’être dans le même rapport.
- **Filtres d’extraction :** Définissez des filtres d’extraction afin de pouvoir voir un aperçu réaliste du résultat pendant la conception même de la page d’extraction. Veillez à supprimer ces filtres avant de publier le rapport.
- **Fonctionnalités supplémentaires :** Une page d’extraction ressemble à n’importe quelle page de rapport. Vous pouvez même l’améliorer avec des fonctionnalités interactives supplémentaires, notamment des segments ou des filtres.
- **Blancs :** Évitez d’ajouter des visuels susceptibles d’afficher BLANK ou de produire des erreurs quand des filtres d’extraction sont appliqués.
- **Visibilité de la page :** Envisagez de masquer les pages d’extraction. Si vous décidez de conserver une page d’extraction visible, veillez à ajouter un bouton qui permet aux utilisateurs de supprimer tous les filtres d’extraction précédemment définis. Affectez un [signet](../desktop-bookmarks.md) au bouton. Le signet doit être configuré pour supprimer tous les filtres.
- **Bouton Précédent :** Un [bouton](../desktop-buttons.md) Précédent est ajouté automatiquement lorsque vous affectez un filtre d’extraction. Il est judicieux de le conserver. Ainsi, les utilisateurs de votre rapport peuvent facilement revenir à la page source.
- **Découverte :** Facilitez l’accès à une page d’extraction en utilisant du texte dans une icône d’en-tête de visuel ou en ajoutant des instructions à une zone de texte. Vous pouvez également concevoir une superposition, comme décrit dans [ce billet de blog](https://alluringbi.com/2019/10/23/overlays-for-true-self-serve-reporting/).

> [!TIP]
> Il est aussi possible de configurer l’extraction vers vos rapports paginés Power BI. Pour ce faire, vous pouvez ajouter des liens vers des rapports Power BI. Ces liens peuvent définir des [paramètres d’URL](https://powerbi.microsoft.com/blog/url-parameters-for-paginated-reports-are-now-available/).

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations en rapport avec cet article, consultez les ressources suivantes :

- [Utiliser une extraction dans Power BI Desktop](../desktop-drillthrough.md)
- Vidéo Guy in a Cube : [Extraction dans Power BI Desktop](https://www.youtube.com/watch?v=2x9lLHDbtDk)
- Vous avez des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
