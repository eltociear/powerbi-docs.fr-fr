---
title: Travailler avec des agrégats (somme, moyenne et ainsi de suite) dans le service Power BI
description: Découvrez comment modifier l’agrégation dans un graphique (somme, moyenne, maximum et ainsi de suite.) dans le service Power BI.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/03/2019
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Reports
ms.openlocfilehash: 7cee05df6a7d13e18bc31bc1a1f34a5f89711c0d
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "65710646"
---
# <a name="work-with-aggregates-sum-average-and-so-on-in-the-power-bi-service"></a>Travailler avec des agrégats (somme, moyenne et ainsi de suite) dans le service Power BI

## <a name="what-is-an-aggregate"></a>Qu’est qu’un agrégat ?

Vous pouvez parfois mathématiquement combiner des valeurs dans vos données. L’opération mathématique peut être somme, moyenne, maximum, nombre et ainsi de suite. Lorsque vous combinez des valeurs dans vos données, il est appelé *agrégation*. Le résultat de cette opération mathématique est une *agrégation*.

Lorsque le service Power BI et Power BI Desktop créent des visualisations, ils peuvent agréger vos données. L’agrégation peut parfois vous convenir, sauf si vous souhaitez regrouper les valeurs d’une autre manière.  Par exemple, une somme ou une moyenne. Il existe différentes façons de gérer et de modifier l’agrégat que Power BI utilise dans une visualisation.

Tout d’abord, examinons données *types* , car le type de données détermine, si et comment, Power BI peut agréger.

## <a name="types-of-data"></a>Types des données

La plupart des jeux de données ont plusieurs types de données. Niveau de base au plus, les données sont des valeurs numériques, ou il n’est pas. Power BI peut agréger des données numériques à l’aide d’une somme, moyenne, nombre, minimum, écart et bien plus encore. Le service peut même agréger des données textuelles, souvent appelées *catégorielles* données. Si vous tentez d’agréger un champ de catégorie en le plaçant dans un compartiment uniquement numérique comme **valeurs** ou **info-bulles**, Power BI sera compter les occurrences de chaque catégorie ou les occurrences distinctes de chaque catégorie. Types spéciaux de données, tels que des dates, faites que quelques leurs propres options d’agrégation : plus ancien, plus récent, premier et dernier.

Prenons l’exemple ci-dessous :

- Les colonnes **Units Sold (Unités vendues)** et **Manufacturing Price (Prix de fabrication)** contiennent des données numériques.

- **Segment**, **Country (Pays)** , **Product (Produit)** , **Month (Mois)** et **Month Name (Nom du mois)** contiennent des données catégorielles.

   ![Capture d’écran d’un jeu de données d’exemple.](media/service-aggregates/power-bi-aggregate-chart.png)

Lorsque vous créez une visualisation dans Power BI, le service regroupera les champs numériques (la valeur par défaut est *somme*) sur un champ catégoriel.  Par exemple, « unités vendues ***par produit***», « unités vendues ***par mois***» et « prix de fabrication ***par Segment***». Power BI fait référence à des champs numériques en tant que **mesures**. Il est facile d’identifier les mesures dans l’éditeur de rapport Power BI--le **champs** liste montre les mesures par le symbole ∑ à côté d’eux. Consultez [l’éditeur de rapport... visite guidée](service-the-report-editor-take-a-tour.md) pour plus d’informations.

![Capture d’écran de Power BI avec la liste de champs appelée.](media/service-aggregates/power-bi-aggregate-fields.png)

## <a name="why-dont-aggregates-work-the-way-i-want-them-to"></a>Pourquoi les agrégats ne fonctionnent pas comme je le souhaite ?

Utilisation d’agrégats dans Power BI service peut prêter à confusion. Vous disposez peut-être d’un champ numérique et Power BI ne vous permettent de modifier l’agrégation. Ou vous disposez peut-être d’un champ, comme une année, et vous ne souhaitez pas l’agréger, mais simplement compter le nombre d’occurrences.

En règle générale, le problème sous-jacent est la définition de champ dans le jeu de données. Peut-être que le propriétaire du jeu de données défini par le champ sous forme de texte, ce qui explique pourquoi Power BI ne peut pas calculer la somme ou moyenne. Malheureusement, [seul le propriétaire du jeu de données peut modifier la façon dont un champ est classé](desktop-measures.md). Par conséquent, si vous disposez des autorisations de propriétaire sur le jeu de données, soit dans Desktop ou le programme utilisé pour créer le jeu de données (par exemple, Excel), vous pouvez résoudre ce problème. Dans le cas contraire, vous devez contacter le propriétaire du jeu de données pour lui demander de l’aide.  

Il existe une section spéciale à la fin de cet article, appelée [ **considérations et résolution des problèmes**](#considerations-and-troubleshooting). Il fournit des conseils et des conseils. Si vous ne trouvez pas votre réponse, publiez votre question sur le [forum de communauté Power BI](http://community.powerbi.com). Vous obtiendrez une réponse rapide directement à partir de l’équipe Power BI.

## <a name="change-how-a-numeric-field-is-aggregated"></a>Modifier le mode d’agrégation d’un champ numérique

Supposons que vous avez un graphique qui fait la somme des unités vendues pour différents produits. Or, il s’avère que vous préfèreriez obtenir la moyenne.

1. Créer un **Histogramme groupé** qui utilise une mesure et une catégorie. Dans cet exemple, utilisez Units Sold by Product (Unités vendues par produit).  Par défaut, Power BI crée un graphique qui additionne les unités vendues (faites glisser la mesure dans le **valeur** bien) pour chaque produit (faites glisser la catégorie dans le **axe** bien).

   ![Capture d’écran du graphique, le volet visualisations et la liste de champs avec somme appelé.](media/service-aggregates/power-bi-aggregate-sum.png)

1. Dans le **visualisations** volet, avec le bouton droit de la mesure, puis sélectionnez le type d’agrégation vous avez besoin. Dans ce cas, nous sélectionnons **moyenne**. Si vous ne voyez pas l’agrégation que vous avez besoin, consultez le [ **considérations et résolution des problèmes** ](#considerations-and-troubleshooting) section.

   ![Capture d’écran de la liste d’agrégation avec moyenne sélectionné et appelé.](media/service-aggregates/power-bi-aggregate-average.png)

   > [!NOTE]
   > Les options disponibles dans la liste déroulante varient en fonction 1) le champ sélectionné et 2) de la façon le propriétaire du jeu de données classées ce champ.

1. Votre visualisation est à présent agrégée par moyenne.

   ![Capture d’écran du graphique maintenant afficher unités moyenne de vendues par produit.](media/service-aggregates/power-bi-aggregate-average-2.png)

## <a name="ways-to-aggregate-your-data"></a>Comment regrouper vos données

Voici certaines des options qui peuvent être disponibles pour l’agrégation d’un champ :

- **Ne pas résumer**. Avec cette option est sélectionnée, Power BI traite chaque valeur dans ce champ séparément et ne les synthétiser. Utilisez cette option si vous avez une colonne d’ID numérique que le service ne doit pas additionner.

- **Somme**. Additionne toutes les valeurs contenues dans le champ.

- **Moyenne**. prend une moyenne arithmétique des valeurs.

- **Minimum**. affiche la valeur la plus petite.

- **Maximum**. affiche la valeur la plus grande.

- **Nombre (non vide).** Compte le nombre de valeurs dans le champ qui ne sont pas vides.

- **Nombre (distinct).** Compte le nombre de valeurs différentes dans le champ.

- **Écart type.**

- **Écart**.

- **Médiane**.  Affiche la valeur médiane (centrale). Cette valeur a le même nombre d’éléments au-dessus et en dessous.  S’il existe deux médianes, Power BI calcule leur moyenne.

Par exemple, ces données :

| Pays | Montant |
|:--- |:--- |
| États-Unis |100 |
| Royaume-Uni |150 |
| Canada |100 |
| Allemagne |125 |
| France | |
| Japon |125 |
| Australie |150 |

donneraient les résultats suivants :

- **Ne pas synthétiser** : chaque valeur est affichée séparément

- **Somme** : 750

- **Moyenne** : 125

- **Maximum** :  150

- **Minimum** : 100

- **Nombre (non vide) :** 6

- **Nombre (distinct) :** 4

- **Écart type :** 20.4124145...

- **Variance :** 416.666...

- **Médiane :** 125

## <a name="create-an-aggregate-using-a-category-text-field"></a>Créez une agrégation à l’aide d’un champ de catégorie (texte)

Vous pouvez également agréger un champ non numérique. Par exemple, si vous avez un champ Nom de produit, vous pouvez l’ajouter comme valeur et le définir sur **Nombre**, **Nombre distinct**, **Premier** ou **Dernier**.

1. Faites glisser le **produit** champ dans le **valeurs** bien. Le **valeurs** bien est généralement utilisé pour les champs numériques. Power BI reconnaît que ce champ est un champ de texte, définit l’agrégation **ne pas résumer**et vous présente avec une seule colonne de table.

   ![Capture d’écran du champ de produit dans les valeurs bien.](media/service-aggregates/power-bi-aggregate-value.png)

1. Si vous modifiez l’agrégation à partir de la valeur par défaut **ne pas résumer** à **Count (Distinct)** , Power BI compte le nombre de produits différents. Dans ce cas, il existe quatre.
  
   ![Capture d’écran de comptage de valeurs de produits.](media/service-aggregates/power-bi-aggregate-count.png)

1. Et si vous remplacez l’agrégation par **Nombre**, Power BI compte le nombre total. Dans ce cas, il existe sept entrées pour **produit**.

   ![Capture d’écran du nombre de produits.](media/service-aggregates/power-bi-aggregate-count-2.png)

1. En faisant glisser le même champ (dans ce cas **produit**) dans le **valeurs** ainsi et en laissant l’agrégation par défaut **ne pas résumer**, Power BI décompose le nombre par produit.

   ![Capture d’écran du produit et le nombre de produits.](media/service-aggregates/power-bi-aggregate-final.png)

## <a name="considerations-and-troubleshooting"></a>Considérations et résolution des problèmes

Q :  Pourquoi est-ce que l’option **Ne pas synthétiser** ne s’affiche pas ?

R :  Le champ que vous avez sélectionné est probablement une mesure calculée ou une mesure avancée créée dans Excel ou [Power BI Desktop](desktop-measures.md). Chaque mesure calculée a sa propre formule codée en dur. Vous ne pouvez pas modifier l’agrégation qu'utilise Power BI. Par exemple, s’il s’agit d’une somme, elle peut uniquement être une somme. Le **champs** liste indique *mesures calculées* avec le symbole de calculatrice.

Q :  Mon champ **est** numérique. Pourquoi mes seuls choix sont **Nombre** et **Comptage de valeurs** ?

R1 :  L’explication la plus probable est que le propriétaire du jeu de données a *pas* classé le champ en tant que nombre. Par exemple, si un jeu de données a un **année** champ, le propriétaire du jeu de données peut le classer la valeur sous forme de texte. Il est plus probable que Power BI compte le **année** champ (par exemple, le nombre de personnes nées en 1974). Il est moins probable que Power BI sera somme ou moyenne. Si vous êtes le propriétaire, vous pouvez ouvrir le jeu de données dans Power BI Desktop et utiliser le **modélisation** onglet pour modifier le type de données.

R2 : Si le champ a une icône de calculatrice, il est donc un *mesure calculée*. Chaque mesure calculée possède sa propre formule codée en dur qui seul le propriétaire du jeu de données peut changer. Le calcul qu'utilise Power BI peut être une agrégation simple comme une moyenne ou une somme. Il peut également être quelque chose de plus compliqué, comme un « pourcentage de contribution à la catégorie parente » ou « total cumulé depuis le début de l’année ». Power BI ne va pas calculer la somme ou la moyenne des résultats. Au lieu de cela, il sera simplement recalculer (à l’aide de la formule codée en dur) pour chaque point de données.

R3 :  Il se peut également que vous ayez supprimé le champ dans un *compartiment* qui autorise uniquement les valeurs de catégorie.  Dans ce cas, les seules options proposées sont Nombre et Comptage de valeurs.

R4 :  Et une quatrième possibilité est que vous utilisez le champ pour un axe. Sur l’axe d’un histogramme par exemple, Power BI affiche une barre pour chaque valeur distincte et n’agrège pas du tout les valeurs de champ.

>[!NOTE]
>L’exception à cette règle est le graphique à nuages de points, qui *nécessite* des valeurs agrégées pour les axes X et Y.

Q :  Pourquoi je ne peux pas agréger des champs de texte pour des sources de données SQL Server Analysis Services (SSAS) ?

R :  Les connexions actives à des modèles multidimensionnels SSAS n’autorisent pas les agrégations côté client, notamment les agrégations dernier, moyenne, min, max et somme.

Q :  J’ai un graphique à nuages de points et je ne veux *pas* d’agrégation pour mon champ.  Comment faire ?

R :  Ajoutez le champ au compartiment **Détails** et pas aux compartiments des axes X ou Y.

Q :  Quand j’ajoute des champs numériques à une visualisation, la plupart de ces champs ont par défaut le type Somme, alors que d’autres sont de type Moyenne ou Nombre ou une autre agrégation.  Pourquoi l’agrégation par défaut est-elle différente à chaque fois ?

R :  Les propriétaires de jeu de données peuvent définir le résumé par défaut pour chaque champ. Si vous êtes propriétaire d’un jeu de données, modifier le résumé par défaut dans le **modélisation** onglet de Power BI Desktop.

Q :  Je suis propriétaire d’un jeu de données et je veux être certain qu’aucun champ n’est jamais agrégé.

R :  Dans Power BI Desktop, dans l’onglet **Modélisation**, définissez **Type de données** sur **Texte**.

Q :  Je ne vois pas **ne pas résumer** en tant qu’option dans la liste déroulante.

R :  Essayez de supprimer le champ puis de le rajouter.

D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)