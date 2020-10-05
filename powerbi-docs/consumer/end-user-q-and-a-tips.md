---
title: Conseils et astuces pour poser des questions avec Questions et réponses
description: Conseils et astuces pour poser des questions avec Questions et réponses dans Power BI
author: mihart
ms.reviewer: Mohammad.ali
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: how-to
ms.date: 09/23/2020
ms.author: mihart
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: 9a8486a24ab7daa23e35f762c6830e400392963f
ms.sourcegitcommit: 02b5d031d92ea5d7ffa70d5098ed15e4ef764f2a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/26/2020
ms.locfileid: "91375278"
---
# <a name="tips-for-asking-questions-in-power-bi-qa"></a>Conseils pour poser des questions dans le moteur Questions et réponses de Power BI

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-yyny.md)]

## <a name="words-and-terminology-that-qa-recognizes"></a>Mots et terminologie reconnus par Questions et réponses
La liste de mots clés affichée sur cette page n’est pas exhaustive.  La meilleure façon de voir si Power BI reconnaît un mot clé consiste à essayer de le taper dans la zone de question.  Si le mot ou le terme est grisé, Power BI ne le reconnaît pas.

La liste ci-dessous utilise le présent, mais tous les temps sont identifiés dans la plupart des cas. Par exemple, « is » comprend **are**, **was**, **were**, **will be**, **have**, **has**, **had**, **will have**, **has got**, **do**, **does**, **did**.  Et « sort » comprend **sorted** et **sorting**.  Power BI reconnaît aussi la version au singulier et au pluriel d’un mot et en tient compte. 

> [!NOTE]
> La fonctionnalité Questions et réponses est également disponible dans l’[application Microsoft Power BI pour iOS sur les appareils iPad, iPhone et iPod Touch](mobile/mobile-apps-ios-qna.md).
>  


|Catégorie  |Mots clés  |Colonne3  |
|---------|---------|---------|
|**Agrégats**     | total, sum, amount, number, quantity, count, average, most, least, fewest, largest, smallest, highest, biggest, maximum, max, greatest, lowest, littlest, minimum, min          |
|     |         |         
**Articles**     |  a, an, the              |
|     |         |         
|**Vides et booléens**     |   blank, empty, null, prefixed with "non" or "non-", empty string, empty text, true, t, false, f          |
|     |         |         |
|**Comparaisons**     |   vs, versus, compared to, compared with            |
|     |         |         |
|**Conjonctions**     |  and, or, each of, with, versus, &, and, but, nor, along with, in addition to       |         
|          |         |
|**Contractions**     |  Questions et réponses reconnaît presque toutes les contractions, faites le test.  Voici quelques exemples : didn't, haven't, he'd, he's, isn't, it's, she'll, they'd, weren't, who's, won't, wouldn't          |
|        |         |
|**Dates**     |       Power BI reconnaît la plupart des expressions de date ($$$jour, $$$semaine, $$$mois, $$$année, $$$trimestre, $$$dix dernières années, etc.) et les dates écrites dans différents formats (voir ci-dessous). Power BI reconnaît également les mots clés suivants : MonthName, Days 1-31, decade. Exemples : January 3rd of 1995, January 3rd 1995, jan 03 1995, 3 Jan 1995, the 3rd of January, January 1995, 1995 January, 1995-01, 01/1995, names of months         |
|        |         |
|**Dates relatives**     |   today, right now, current time, yesterday, tomorrow, the current, next, the coming, last, previous, ago, before now, sooner than, after, later than, from, at, on, from now, after now, in the future, past, last, previous, within, in, over, N days ago, N days from now, next, once, twice.|
|    |  Exemple : count of orders in the past 6 days.  |            |
|        |         |
|**Égalité (plage)**     |   in, equal to, =, after, is more than, in, between, before  |
|  |Exemples : Order year is before 2012? Price equals between 10 and 20? Is the age of John greater than 40? Total sales in 200-300?              |
|        |         |
|**Égalité (valeur)**     |   is, equal, equal to, in, of, for, within, is in, is on |
|   | Exemples : Quels produits sont verts ? Order date equals 2012. Is the age of John 40? Total sales that aren't equal to 200? Order date of 1/1/2016. 10 in price? Green for color? 10 in price?              |
|        |         |
|**Noms**     |       Si une colonne du jeu de données contient la phrase « name » (par exemple EmployeeName), Q&R comprend que les valeurs de cette colonne sont des noms. Vous pouvez donc poser des questions du type « which employees are named robert » (quels employés s’appellent Robert ?).          |
|        |         |
**Pronoms**  | he, him, himself, his, she, herself, her, hers, it, itself, its, they, their, them, themselves, theirs, this, these, that, those
|**Commandes de requête**     |    sorted, sort by, direction, group, group by, by, show, list, display, give me, name, just, only, arrange, rank, compare, to, with, against, alphabetically, ascending, descending, order             |
|        |         |
|**Plage**     |      greater, more, larger, above, over, >, less, smaller, fewer, below, under, <,  at least, no less than, >=, at most, no more than, <=, in, between, in the range of, from, later, earlier, sooner, after, on, at, later than, after, since, starting with, starting from, ending with           |
|        |         |
**Heure**  |am, pm, o'clock, noon, midnight, hour, minute, second, hh:mm:ss  |
|  |  Exemples : 10 pm, 10:35 pm, 10:35:15 pm, 10 o'clock, noon, midnight, hour, minute, second.  |
|  |  |
|**N premiers**     |     (ordre, classement) : top, bottom, highest, lowest, first, last, next, earliest, newest, oldest, latest, most recent, next            |
|        |         |
|**Types d’éléments visuels**     |  tous les types d’éléments visuels natifs de Power BI.  Si l’option est présente dans le volet visualisations, vous pouvez l’ajouter à votre question.  La seule exception à cette règle concerne les [visuels Power BI personnalisés](../developer/visuals/power-bi-custom-visuals.md) que vous avez ajoutés manuellement dans le volet de visualisation.  |
|  |  Exemple : show districts by month and sales total as bar chart               |
|        |         |
|**Relatifs (relation, qualification)**  | when, where, which, who, whom, how many, how much, how many times, how often, how frequently, amount, number, quantity, how long, what                |

## <a name="qa-helps-you-phrase-the-question"></a>Le moteur Questions et réponses vous aide à formuler la question
Questions et réponses fait de son mieux pour comprendre et répondre à la question posée. Il essaie de la comprendre de plusieurs façons. Pour toutes ces formulations, vous pouvez accepter l’action entièrement, partiellement ou pas du tout. Lorsque vous tapez votre question, Questions et réponses :

* complète automatiquement les mots et les questions. Diverses stratégies sont mises en œuvre, notamment la saisie semi-automatique de mots reconnaissables, les questions stockées, et les questions déjà posées ayant renvoyé des réponses correctes. Si plusieurs options de saisie semi-automatique sont disponibles, elles sont présentées dans une liste déroulante.
* Corrige l’orthographe.
* Fournit un extrait de la réponse sous forme de visuel. Le visuel se met à jour à mesure que vous tapez et modifiez la question (sans attendre que vous ayez appuyé sur Entrée).
* Utilise la suggestion automatique pour proposer des termes de remplacement provenant des classeurs sous-jacents lorsque vous replacez le curseur dans la zone Question.
* Reformule la question en fonction des données du ou des jeux de données sous-jacents. Questions et réponses remplace les mots que vous utilisez par des synonymes provenant des jeux de données sous-jacents. En lisant la reformulation, vous savez si Questions et réponses a bien compris votre question ou pas. 
* Ajoute un double souligné aux mots qu’il ne comprend pas.
* Ajoute un simple souligné aux mots qu’il comprend.
* Vous permet de contacter le propriétaire du rapport ou du tableau de bord quand votre terme est introuvable ou que votre question n’obtient pas de résultats.

## <a name="dont-stop-now"></a>Continuez sur votre lancée
Une fois que Questions et réponses a affiché vos résultats, poursuivez la conversation. Utilisez les fonctionnalités interactives du visuel et de Questions et réponses pour découvrir d’autres perspectives.

## <a name="next-steps"></a>Étapes suivantes
Revenir à [Q&R dans Power BI](end-user-q-and-a.md)  

[Power BI – Concepts de base](end-user-basic-concepts.md)  

D’autres questions ? [Posez vos questions à la communauté Power BI](https://community.powerbi.com/)

