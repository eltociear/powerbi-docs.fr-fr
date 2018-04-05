---
title: Conseils et astuces pour poser des questions avec Questions et réponses dans Power BI
description: Conseils et astuces pour poser des questions avec Questions et réponses dans Power BI
services: powerbi
documentationcenter: ''
author: mihart
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
ms.date: 01/18/2018
ms.author: jastru
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: 28ebd938b1121e1d2d453a9c9e72592b1c814742
ms.sourcegitcommit: 8132f7edc6879eda824c900ba90b29cb6b8e3b21
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/03/2018
---
# <a name="tips-for-asking-questions-in-power-bi-qa"></a>Conseils pour poser des questions dans le moteur Questions et réponses de Power BI
## <a name="words-and-terminology-that-qa-recognizes"></a>Mots et terminologie reconnus par Questions et réponses
Cette liste de mots clés n’est pas exhaustive.  La meilleure façon de voir si Power BI reconnaît un mot clé consiste à essayer de le taper dans la zone de question.  Si le mot ou l’expression apparaît en gris, Power BI ne le reconnaît pas ou ne le reconnaît pas dans le contexte actuel.

La liste ci-dessous utilise le présent, mais tous les temps sont identifiés dans la plupart des cas. Par exemple, « is » comprend are, was, were, will be, have, has, had, will have, has got, do, does, did.  « sort » comprend sorted et sorting.  Power BI reconnaît aussi la version au singulier et au pluriel d’un mot et en tient compte. Par exemple, Power BI reconnaît « $$$année » et « $$$années ».

> [!NOTE]
> La fonctionnalité Questions et réponses est également disponible dans l’[application Microsoft Power BI pour iOS sur les appareils iPad, iPhone et iPod Touch](mobile-apps-ios-qna.md).
> 
> 

Si vous êtes propriétaire d’un jeu de données, ajoutez des formulations et des synonymes afin d’améliorer les résultats du moteur de Questions et réponses pour vos clients.

**Agrégat** : total, sum, amount, number, quantity, count, average, most, least, fewest, largest, smallest, highest, biggest, maximum, max, greatest, lowest, littlest, minimum, min

**Articles** : a, an, the

**Vides et booléens** : blank, empty, null, prefixed with “non” or “non-“, empty string, empty text, true, t, false, f

**Comparaisons** : vs, versus, compared to, compared with

**Conjonctions** : and, or, each of, with, versus, &, and, but, nor, along with, in addition to

**Contractions** : Q&R reconnaît presque tous les contractions, faites le test.  Voici quelques exemples : didn’t, haven’t, he’d, he’s, isn’t, it’s, she’ll, they’d, weren’t, where’ll, who’s, won’t, wouldn’t.

**Dates** : Power BI reconnaît la plupart des expressions de date ($$$jour, $$$semaine, $$$mois, $$$année, $$$trimestre, $$$dix dernières années, etc.) et les dates écrites dans différents formats (voir ci-dessous). Power BI reconnaît également les mots clés suivants : $$$MonthName, $$$Days 1-31, $$$decade.

Exemples : January 3rd of 1995, January 3rd 1995, jan 03 1995, 3 Jan 1995, the 3rd of January, January 1995, 1995 January, 1995-01, 01/1995, names of months.

**Dates relatives** : today, right now, current time, yesterday, tomorrow, the current, next, the coming, last, previous, ago, before now, sooner than, after, later than, from, at, on, from now, after now, in the future, past, last, previous, within, in, over, N days ago, N days from now, next, once, twice.

Exemple : count of orders in the past 6 days.

**Égalité (plage)** : in, equal to, =, after, is more than, in, between, before

Exemples : Order year is before 2012? Price equals between 10 and 20? Is the age of John greater than 40? Total sales in 200-300?

**Égalite (valeur)** : is, equal, equal to, in, of, for, within, is in, is on

Exemples : Which products are green? Order date equals 2012. Is the age of John 40? Total sales that is not equal to 200? Order date of 1/1/2016. 10 in price? Green for color? 10 in price?

**Noms** : si une colonne du jeu de données contient la phrase « nom (name) » (par exemple EmployeeName), Q&R comprend que les valeurs de cette colonne sont des noms. Vous pouvez donc poser des questions du type « quels employés s’appellent Robert ? ».

**Pronoms** : he, him, himself, his, she, herself, her, hers, it, itself, its, they, their, them, themselves, theirs, this, these, that, those

**Commandes de requête** : sorted, sort by, direction, group, group by, by, show, list, display, give me, name, just, only, arrange, rank, compare, to, with, against, alphabetically, ascending, descending, order

**Plage** : greater, more, larger, above, over, >, less, smaller, fewer, below, under, <,  at least, no less than, >=, at most, no more than, <=, in, between, in the range of, from, later, earlier, sooner, after, on, at, later than, after, since, starting with, starting from, ending with

**Heure** : am, pm, o'clock, noon, midnight, hour, minute, second, hh:mm:ss

Exemples : 10 pm, 10:35 pm, 10:35:15 pm, 10 oclock, noon, midnight, hour, minute, second.

**N premiers** (ordre, classement) : top, bottom, highest, lowest, first, last, next, earliest, newest, oldest, latest, most recent, next

**Types d’éléments visuels** : tous les types d’éléments visuels natifs de Power BI.  Si l’option est présente dans le volet visualisations, vous pouvez l’ajouter à votre question.  La seule exception concerne les [éléments visuels personnalisés](power-bi-custom-visuals.md) que vous avez ajoutés manuellement dans le volet de visualisation.

Exemple : show districts by month and sales total as bar chart

**Relatifs (relation, qualification)** : when, where, which, who, whom, how many, how much, how many times, how often, how frequently, amount, number, quantity, how long, what

## <a name="qa-helps-you-phrase-the-question"></a>Le moteur Questions et réponses vous aide à formuler la question
Il fait de son mieux pour s’assurer que la réponse reflète précisément la question posée. Il utilise pour cela plusieurs méthodes. Pour ces dernières, vous pouvez accepter l’action entièrement, partiellement ou pas du tout. Lorsque vous tapez votre question, Questions et réponses :

* Complète automatiquement les mots et les questions. Diverses stratégies sont mises en œuvre, notamment la saisie semi-automatique de mots reconnaissables, les questions fréquentes pour les classeurs sous-jacents et les questions déjà posées ayant renvoyé des réponses correctes. Si plusieurs options de saisie semi-automatique sont disponibles, elles sont présentées dans une liste déroulante.
* Corrige l’orthographe.
* Fournit un extrait de la réponse sous forme de visualisation. Celle-ci dernière se met à jour à mesure que vous tapez et modifiez la question (sans attendre que vous ayez appuyé sur Entrée).
* Utilise la suggestion automatique pour proposer des termes de remplacement provenant des classeurs sous-jacents lorsque vous replacez le curseur dans la zone Question.
* Reformule la question en fonction des données du ou des jeux de données sous-jacents. Vous pouvez ainsi vérifier que Questions et réponses a bien compris votre question, car l’outil remplace les mots que vous utilisez par des synonymes provenant des jeux de données sous-jacents.
* Estompe les mots incompris.

## <a name="dont-stop-now"></a>Continuez sur votre lancée
Une fois que Questions et réponses a affiché vos résultats, poursuivez la conversation. Utilisez les fonctionnalités interactives de la visualisation et de Questions et réponses pour découvrir d’autres perspectives.

## <a name="next-steps"></a>Étapes suivantes
Revenir à [Q&R dans Power BI](power-bi-q-and-a.md)  

[Power BI – Concepts de base](service-basic-concepts.md)  

D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)

