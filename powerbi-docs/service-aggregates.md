---
title: "Agrégations (somme, moyenne, maximum, etc.) dans Power BI"
description: "Modifier l’agrégation dans un graphique (somme, moyenne, maximum, etc.) dans Power BI"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: modifying
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 09/23/2017
ms.author: mihart
ms.openlocfilehash: c1b926e129e8d82edd9c329a51623908c4e7c9e0
ms.sourcegitcommit: 8f72ce6b35aa25979090a05e3827d4937dce6a0d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2017
---
# <a name="aggregates-in-power-bi"></a>Agrégats dans Power BI
## <a name="what-is-an-aggregate"></a>Qu’est qu’un agrégat ?
Vous pouvez parfois mathématiquement combiner des valeurs de lignes dans une colonne. L’opération mathématique peut être une somme, une moyenne, un maximum, un nombre, etc. La combinaison de la valeur des données des lignes d’une colonne est appelée « agrégation ». Le résultat de cette opération mathématique est une *agrégation*. 

Un champ numérique est une valeur qui est agrégée (qui fait l’objet d’une moyenne ou d’une somme par exemple) sur un champ de catégorie donné.  Par exemple, « Montant des ventes par produit » et « Nombre de défauts par région ». Les champs numériques sont souvent appelés **mesures**. Dans la liste Champs, les mesures sont assorties du symbole ∑. Pour plus d’informations, consultez [Découverte de l’éditeur de rapport](service-the-report-editor-take-a-tour.md).

Parfois, une *mesure* est en fait une *mesure calculée*. Dans Power BI, les mesures calculées sont importées avec les données (définies dans le modèle de données sur lequel votre rapport est basé). Chaque mesure calculée a sa propre formule codée en dur. Vous ne pouvez pas modifier l’agrégation utilisée ; par exemple, s’il s’agit d’une somme, il peut s’agir uniquement d’une somme. Dans la liste Champs, les *mesures calculées* sont indiquées par le symbole de calculatrice. Pour plus d’informations sur la façon dont les mesures calculées sont créées, consultez [Mesures dans Power BI Desktop](desktop-measures.md).

Les champs de catégorie ne sont pas numériques mais ils peuvent quand même être agrégés.  Lorsque les champs de catégorie sont placés dans un compartiment *numérique uniquement* comme **Valeurs** ou **Info-bulles**, Power BI peut compter les occurrences de chaque catégorie ou les occurrences distinctes de chaque catégorie.  Pour les chaînes et les dates, Power BI a quelques autres options d’agrégation : plus ancienne, plus récente, première et dernière.  

## <a name="why-dont-aggregates-work-the-way-i-want-them-to"></a>Pourquoi les agrégats ne fonctionnent pas comme je le souhaite ?
L’utilisation d’agrégats dans le service Power BI peut prêter à confusion ; vous disposez peut-être d’un champ numérique et Power BI ne vous permet pas de modifier l’agrégation. Ou vous disposez peut-être d’un champ, comme une année, et vous ne souhaitez pas l’agréger, mais simplement compter le nombre d’occurrences.

En règle générale, la source du problème est la façon dont le champ a été classé dans le jeu de données Power BI. Il se peut que le champ soit classé en tant que texte, ce qui explique pourquoi il ne peut pas faire l’objet d’une somme ou d’une moyenne. Malheureusement, [seul le propriétaire du jeu de données peut modifier la façon dont un champ est classé](desktop-measures.md).  

Pour vous aider, nous avons inclus une section spéciale à la fin de cet article, appelée **Astuces et résolution des problèmes**.  Si vous n’y trouvez pas votre réponse, publiez votre question sur le [forum de la communauté Power BI](http://community.powerbi.com) pour obtenir une réponse rapide directement de l’équipe Power BI.

## <a name="change-how-a-numeric-field-is-aggregated"></a>Modifier le mode d’agrégation d’un champ numérique
Supposons que vous avez un graphique qui fasse la somme des données de ventes des différentes régions. Or, il s’avère que vous préfèreriez obtenir la moyenne. 

1. En mode Edition, ajoutez la mesure à une visualisation.
2. Recherchez ce champ dans le volet Visualisations, cliquez avec le bouton droit, puis sélectionnez le type d’agrégation dont vous avez besoin. Si vous ne voyez pas l’agrégation dont vous avez besoin, contactez le propriétaire du jeu de données. Cela peut indiquer un problème avec la façon dont le champ a été classé par le propriétaire.  
   
   ![](media/service-aggregates/aggregate_new.png)
   
   > [!NOTE]
   > Les options disponibles dans la liste déroulante varient en fonction 1) du champ sélectionné et 2) de la façon dont le champ a été classé par le propriétaire du jeu de données.
   > 
   > 

Voici certaines des options qui peuvent être disponibles pour l’agrégation d’un champ :

* **Ne pas résumer**. si vous choisissez cette option, chaque valeur du champ en question est traitée séparément et n’est pas résumée. Cette option est souvent utilisée en présence d’une colonne d’ID numériques qui ne doivent pas être additionnés.
* **Somme**. cette option permet d’ajouter toutes les valeurs contenues dans le champ.
* **Moyenne**. prend une moyenne arithmétique des valeurs.
* **Minimum**. affiche la valeur la plus petite.
* **Maximum**. affiche la valeur la plus grande.
* **Nombre (non vide).** compte le nombre de valeurs dans le champ qui ne sont pas vides.
* **Nombre (distinct).** compte le nombre de valeurs différentes dans le champ.
* **Écart type.**
* **Écart**.
* **Médiane**.  Affiche la valeur médiane (centrale). Il s’agit de la valeur ayant le même nombre d’éléments au-dessus et au-dessous.  S’il existe 2 médianes, Power BI calcule une moyenne.

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

* **Ne pas résumer**: chaque valeur est affichée séparément
* **Somme**: 750
* **Moyenne**: 125
* **Maximum** : 150
* **Minimum**: 100
* **Nombre (non vide)** : 6
* **Nombre (distinct)** : 4
* **Écart type :** 20.4124145...
* **Écart :** 416.666...
* **Médiane :** 125

## <a name="use-a-non-aggregated-field-as-a-numeric-field"></a>Utiliser un champ non agrégée comme un champ numérique
Vous pouvez utiliser un champ non agrégée comme un champ numérique. Par exemple, si vous avez un champ Nom de produit, vous pouvez l’ajouter comme valeur et le définir sur **Nombre** ou **Nombre distinct**. 

1. Par exemple, si vous sélectionnez **Magasin > Chaîne**.
   
   ![](media/service-aggregates/count-of-chain-do_not_summarize.png)
2. Et si vous remplacez l’agrégation par défaut **Ne pas synthétiser** par **Nombre (distinct)**, Power BI compte le nombre de chaînes différentes. Dans ce cas, il y en a 2 : Fashions Direct et Lindseys.
   
   ![](media/service-aggregates/aggregates_count.png)
3. Et si vous remplacez l’agrégation par **Nombre**, Power BI compte le nombre total. Dans cet exemple, il y a 104 entrées pour **Chaîne**. En ajoutant **Chaîne** en tant que filtre, vous pouvez voir qu’il y a 37 lignes pour Fashions Direct et 67 pour Lindseys.  
   
   ![](media/service-aggregates/count_of_chain_104.png)

## <a name="tips-and-troubleshooting"></a>Conseils et résolution des problèmes
Q : Pourquoi est-ce que l’option **Ne pas synthétiser** ne s’affiche pas ?

R : Le champ que vous avez sélectionné est probablement une mesure calculée. N’oubliez pas que chaque mesure calculée a sa propre formule codée en dur. Vous ne pouvez pas modifier le calcul.

Q : Mon champ **est** numérique. Pourquoi mes seuls choix sont **Nombre** et **Comptage de valeurs** ?

R : L’explication la plus probable est que le propriétaire du jeu de données n’a *pas* classé le champ en tant que nombre, accidentellement ou volontairement. Par exemple, si un jeu de données a un champ **année**, le propriétaire du jeu de données peut le classer comme texte, car il est plus que probable que le champ **année** fasse l’objet d’un décompte (par exemple le nombre de personnes nées en 1974) et non d’une somme ou d’une moyenne. Si vous êtes le propriétaire, vous pouvez ouvrir le jeu de données dans Power BI Desktop et utiliser l’onglet **Modélisation** pour modifier le type de données.  

R : Il se peut également que vous ayez supprimé le champ dans un *compartiment* qui autorise uniquement les valeurs de catégorie.  Dans ce cas, les seules options proposées sont Nombre et Comptage de valeurs.

R : Une troisième possibilité est que vous utilisez le champ pour un axe. Sur l’axe d’un histogramme par exemple, Power BI affiche une barre pour chaque valeur distincte et n’agrège pas du tout les valeurs de champ. 

>[!NOTE]
>L’exception à cette règle est le graphique à nuages de points, qui *nécessite* des valeurs agrégées pour les axes X et Y.


Q : J’ai un graphique à nuages de points et je ne veux *pas* d’agrégation pour mon champ.  Comment faire ?

R : Ajoutez le champ au compartiment **Détails** et pas aux compartiments des axes X ou Y.

Q : Quand j’ajoute des champs numériques à une visualisation, la plupart de ces champs ont par défaut le type Somme, alors que d’autres sont de type Moyenne ou Nombre ou une autre agrégation.  Pourquoi l’agrégation par défaut est-elle différente à chaque fois ?

R : Les propriétaires du jeu de données ont la possibilité de définir le résumé par défaut pour chaque champ. Si vous êtes propriétaire d’un jeu de données, modifiez le résumé par défaut dans l’onglet **Modélisation** de Power BI Desktop.

Q : Mon champ **est** numérique. Pourquoi ne vois-je pas d’options d’agrégation dans la liste déroulante ?

R : Si le champ a une icône de calculatrice, cela signifie qu’il s’agit d’une *mesure calculée* et chaque mesure calculée possède sa propre formule codée en dur qui ne peut pas être modifiée dans le service Power BI. Le calcul utilisé peut être une agrégation simple comme une moyenne ou une somme, mais il peut également être plus complexe, comme un « pourcentage de contribution à la catégorie parente » ou « total cumulé depuis le début de l’année ». Power BI ne va pas calculer la somme ou la moyenne des résultats, mais juste recalculer (à l’aide de la formule codée en dur) chaque point de données.

Q : Je suis propriétaire d’un jeu de données et je veux être certain qu’aucun champ n’est jamais agrégé.

R : Dans Power BI Desktop, dans l’onglet **Modélisation**, définissez **Type de données** sur **Texte**.

Q : Je ne vois pas **Ne pas synthétiser** en tant qu’option dans ma liste déroulante.

R : Essayez de supprimer le champ puis de le rajouter.

D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)

