---
title: "Utilisation de Q&R de Power BI"
description: "Utilisation de Q&R de Power BI"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
editor: 
tags: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 09/25/2017
ms.author: mihart
ms.openlocfilehash: a6736916a4bb2e94c1f5e1e3c3c3e5339cf990ec
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2017
---
# <a name="how-to-use-power-bi-qa"></a>Utilisation de Q&R de Power BI
## <a name="ask-questions-of-your-data-using-natural-language"></a>Interroger ses données à l’aide du langage naturel
Commencez sur un tableau de bord. La zone de questions Q&R vous permet de taper votre question à l’aide du langage naturel. Q&R reconnaît les mots que vous tapez et cherche l’emplacement (le jeu de données) où se trouve la réponse. Q&R vous aide également à formuler votre question grâce à la saisie semi-automatique, à la reformulation, ainsi qu’à d’autres aides textuelles et visuelles.

![](media/service-how-to-q-and-a/powerbi-qna.png)

La réponse à votre question s’affiche comme une visualisation interactive et change quand vous modifiez votre question.

Q&R est interactif et même amusant, car une question en entraîne beaucoup d’autres au fur et à mesure que les visualisations révèlent des voies intéressantes à explorer. Regardez Amanda illustrer l’utilisation de Q&R pour créer des éléments visuels, les explorer et les épingler à des tableaux de bord.

> [!NOTE]
> La fonctionnalité Questions et réponses est également disponible dans l’[application Microsoft Power BI pour iOS sur les appareils iPad, iPhone et iPod Touch](mobile-apps-ios-qna.md).
> 
> 

<iframe width="560" height="315" src="https://www.youtube.com/embed/qMf7OLJfCz8?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

## <a name="use-natural-language-to-ask-questions-about-your-data"></a>Utiliser le langage naturel pour poser des questions sur les données
1. Placez votre curseur dans la zone de question. Avant même que vous commenciez à taper votre question, Q&R affiche dans un nouvel écran des suggestions de formulation de votre question.
   
   ![](media/service-how-to-q-and-a/powerbi-qna-cursor.png)  
   
   Cette liste contient :  
   a.  les questions utilisées pour créer les [vignettes](service-dashboard-tiles.md) qui sont déjà épinglées au tableau de bord, et  
   b.  le nom des tables des [jeux de données sous-jacents](service-get-data.md).  
   
   Vous pouvez choisir l’une de ces questions comme point de départ et continuer à affiner la question pour trouver la réponse que vous recherchez. Sinon, vous pouvez aussi utiliser un nom de table pour formuler une nouvelle question.
2. Sélectionnez une question dans la liste déroulante ou tapez votre propre question.  
   
   ![](media/service-how-to-q-and-a/powerbi-qna-list.png)
3. Pendant que vous tapez une question, Q&R de Power BI sélectionne la meilleure [visualisation](power-bi-visualization-types-for-reports-and-q-and-a.md) pour afficher la réponse, et la visualisation change de manière dynamique à mesure que vous modifiez la question. Q&R vous aide également à formuler votre question à l’aide de la saisie semi-automatique, de la reformulation de votre question et d’autres aides textuelles et visuelles.  
   ![](media/service-how-to-q-and-a/powerbi-qna-viz.png)
4. Quand vous tapez une requête, Power BI recherche une réponse dans tout jeu de données dont une vignette est affichée sur ce tableau de bord.  Si toutes les vignettes proviennent du *jeu_de_données_A*, votre réponse proviendra du *jeu_de_données_A*.  S’il existe des vignettes provenant du *jeu_de_données_A* et du *jeu_de_données_B*, Questions et réponses recherche la meilleure réponse dans ces 2 jeux de données.
   
   > [!TIP]
   > Attention : si vous disposez d’une seule vignette provenant du *jeu_de_données_A* et que vous la supprimez de votre tableau de bord, Questions et réponses n’a plus accès au *jeu_de_données_A*.
   > 
   > 
5. Quand vous êtes satisfait du résultat, [épinglez la visualisation à un tableau de bord](service-dashboard-pin-tile-from-q-and-a.md) en sélectionnant l’icône d’épingle dans l’angle supérieur droit. Si le tableau de bord a été partagé avec vous, ou fait partie d’une application, vous ne pouvez pas l’épingler.
   
   ![](media/service-how-to-q-and-a/pbi_qna_finish-typing-question.jpg)

### <a name="tell-qa-which-visualization-to-use"></a>Indiquer à Q&R la visualisation à utiliser
Grâce à Q&R, non seulement vous pouvez demander à vos données de parler d’elles-mêmes, mais vous pouvez également décider de leur affichage. Il suffit d’ajouter « sous forme de <visualization type> » à la fin de votre question.  Par exemple, « afficher le volume du stock par site sous la forme d’une carte » et « afficher le stock total sous la forme d’une carte ».  Essayez ces requêtes.

## <a name="how-does-qa-know-how-to-answer-questions"></a>Comment la fonctionnalité Q&R sait-elle répondre aux questions ?
### <a name="which-datasets-does-qa-use"></a>Quels jeux de données la fonctionnalité Q&R utilise-t-elle ?
Comment la fonctionnalité Q&R réussit-elle à répondre à des questions spécifiques aux données ? Elle s’appuie sur le nom des tables, des colonnes et des champs calculés du jeu de données sous-jacent. La façon dont vous (ou le propriétaire du jeu de données) nommez les éléments est donc très importante. 

Par exemple, supposons que vous disposiez d’un tableau Excel nommé « Ventes » et comprenant les colonnes suivantes : « Produit », « Mois », « Unités vendues », « Ventes brutes » et « Bénéfices ». Vous pouvez poser des questions sur n’importe laquelle de ces entités.  Vous pouvez demander ce qui suit : « afficher les *ventes*», « total des *bénéfices* par *mois*», « trier les *produits* par *unités vendues*» et ainsi de suite.

Q&R peut répondre aux questions qui sont basées sur la façon dont votre jeu de données est organisé. Comment cela fonctionne-t-il pour les données issues de Salesforce ? Quand vous vous connectez à votre compte salesforce.com, Power BI génère automatiquement un tableau de bord.  Avant de commencer à poser des questions, regardez les données qui s’affichent dans les visualisations du tableau de bord, ainsi que les données affichées dans la liste déroulante de Q&R.

* Si les étiquettes et les valeurs d’axe des visualisations comprennent les mots « ventes », « compte », « mois » et « opportunités », vous pouvez poser des questions telles que : « quel *compte* possède le nombre le plus élevé d’*opportunités* ? » ou « afficher les *ventes* par mois sous la forme d’un graphique à barres ».
* Si la liste déroulante inclut les mots « vendeur », « état » et « année », vous pouvez poser des questions telles que : « quel *vendeur* a obtenu les *ventes* les plus basses en *Floride* en *2013* ? »

Si vous disposez de données de performances de site web Google Analytics, vous pouvez poser une question sur le temps passé sur une page web particulière, sur le nombre de visites uniques et sur le taux d’engagement utilisateur. Si vous interrogez des données démographiques, vous pourriez poser des questions sur l’âge et sur les revenus par zone géographique.

### <a name="which-visualization-does-qa-use"></a>Quelles visualisations la fonctionnalité Q&R utilise-t-elle ?
Q&R choisit la meilleure visualisation en fonction des données affichées. Parfois les données du jeu sous-jacent sont définies en tant que type ou catégorie, ce qui aide Q&R à savoir comment les afficher. Par exemple, si les données sont définies en tant que date, elles seront davantage susceptibles de s’afficher sous la forme d’un graphique en courbes. Les données appartenant à la catégorie « Ville » seront davantage susceptibles de s’afficher sous forme de carte.

Vous pouvez également indiquer à Q&R quelle visualisation utiliser en l’ajoutant à votre question. Gardez toutefois à l’esprit qu’il n’est pas toujours possible pour Q&R d’afficher les données avec la visualisation demandée.

Pour plus d’informations sur les mots clés reconnus par Q&R, consultez [Conseils pour poser des questions](service-q-and-a-tips.md).

## <a name="next-steps"></a>Étapes suivantes
Revenir à [Q&R dans Power BI](service-q-and-a.md)  
[Didacticiel : Utiliser Q&R avec l’exemple Analyse de la vente au détail](power-bi-visualization-introduction-to-q-and-a.md)  
[Conseils de formulation des questions dans Q&R](service-q-and-a-tips.md)  
[Préparer un classeur pour Q&R](service-prepare-data-for-q-and-a.md)  
[Épingler une vignette au tableau de bord à partir de Questions et réponses](service-dashboard-pin-tile-from-q-and-a.md)  

