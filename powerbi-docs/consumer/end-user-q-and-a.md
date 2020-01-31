---
title: Questions et réponses pour les consommateurs Power BI
description: Rubrique de vue d’ensemble de la documentation pour les requêtes en langage naturel des questions et réponses Power BI.
author: mihart
ms.reviewer: mohammad ali
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 12/18/2019
ms.author: mihart
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: cc20d981e1e774eed109c614e146415ec3813601
ms.sourcegitcommit: a1409030a1616027b138128695b80f6843258168
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76709800"
---
# <a name="qa-for-power-bi-consumers"></a>Questions et réponses pour les consommateurs Power BI

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

## <a name="what-is-qa"></a>Qu’est-ce que Q&R ?
Il est parfois plus rapide d’obtenir des informations à partir de vos données en posant une question dans un langage naturel. Par exemple, « quel était le total des ventes l’année dernière ».

Utilisez l’outil Q&R pour explorer vos données à l’aide des fonctionnalités intuitives du langage naturel et recevez des réponses sous la forme de graphiques et de diagrammes. Q&R diffère d’un moteur de recherche, car il ne fournit que des résultats sur les données de Power BI.

## <a name="which-visualization-does-qa-use"></a>Quelles visualisations la fonctionnalité Q&R utilise-t-elle ?
Q&R choisit la meilleure visualisation en fonction des données affichées. Parfois les données du jeu sous-jacent sont définies en tant que type ou catégorie, ce qui aide Questions et réponses à savoir comment les afficher. Par exemple, si les données sont définies en tant que date, elles seront davantage susceptibles de s’afficher sous la forme d’un graphique en courbes. Les données appartenant à la catégorie « Ville » seront davantage susceptibles de s’afficher sous forme de carte.

Vous pouvez également indiquer à Q&R quel visuel utiliser en l’ajoutant à votre question. Gardez toutefois à l’esprit qu’il n’est pas toujours possible pour Q&R d’afficher les données avec le visuel demandé. Questions et réponses vous fournit une liste de types de visuels applicables.

## <a name="where-can-i-use-qa"></a>Où puis-je utiliser Questions et réponses ?
Vous trouverez Questions et réponses sur les tableaux de bord dans le service Power BI et en bas du tableau de bord dans Power BI Mobile. À moins que le concepteur vous ait donné des autorisations de modification, vous pouvez utiliser Questions et réponses pour explorer les données, mais vous ne pouvez pas enregistrer les visualisations créées avec cette fonctionnalité.

![zone de question](media/end-user-q-and-a/powerbi-qna.png)

Vous trouverez également des questions et réponses sur les rapports, si le *concepteur* de rapports a ajouté un [visuel de Questions et réponses](../visuals/power-bi-visualization-q-and-a.md).   

![Visuel de Questions et réponses](media/end-user-q-and-a/power-bi-q-and-a-default.png)

## <a name="qa-on-dashboards"></a>Questions et réponses sur les tableaux de bord

La fonction **Questions et réponses Power BI** est disponible avec une licence Pro ou Premium.  [Questions et réponses dans les apps mobiles Power BI](mobile/mobile-apps-ios-qna.md) et [Questions et réponses avec Power BI Embedded](../developer/qanda.md) sont traités dans différents articles. À l’heure actuelle, **Questions et réponses Power BI** prend uniquement en charge les réponses aux requêtes en langage naturel formulées en anglais, mais votre administrateur Power BI peut activer une préversion disponible en espagnol.


![treemap créé avec Questions et réponses](media/end-user-q-and-a/power-bi-treemap.png)

Les questions ne sont qu’un début.  Amusez-vous à explorer vos données, affinez ou développez vos questions, découvrez de nouvelles informations fiables et obtenez une vue d’ensemble de vos données. Vous serez ravi des informations précieuses que vous allez découvrir.

Cet outil est réellement interactif et surtout très rapide ! Grâce à son stockage en mémoire, il fournit des réponses de manière quasi instantanée.


## <a name="use-qa-on-a-dashboard-in-the-power-bi-service"></a>Utiliser Questions et réponses sur un tableau de bord dans le service Power BI
Dans le service Power BI (app.powerbi.com), un tableau de bord contient des vignettes épinglées à partir d’un ou plusieurs jeux de données. Vous pouvez donc poser des questions sur les données contenues dans un de ces jeux de données. Pour afficher les rapports et jeux de données utilisés pour créer le tableau de bord, sélectionnez **Afficher les éléments associés** à partir de la liste déroulante **Autres actions**.

![afficher les éléments associés à partir de la barre de menus](media/end-user-q-and-a/power-bi-q-and-a-view-related.png)

## <a name="how-do-i-start"></a>Comment commencer ?
Tout d’abord, familiarisez-vous avec le contenu. Examinez les visuels sur le tableau de bord et dans le rapport. Familiarisez-vous avec le type et la plage de données qui sont à votre disposition. 

Par exemple :

* Si les étiquettes et les valeurs d’axe des visuels comprennent les mots « ventes », « compte », « mois » et « opportunités », vous pouvez poser des questions telles que : « quel *compte* possède le nombre le plus élevé d’*opportunités*? » ou « afficher les *ventes* par mois sous la forme d’un graphique à barres ».

* Si vous disposez de données de performances de site web dans Google Analytics, vous pouvez interroger Questions et réponses concernant le temps passé sur une page web, le nombre de visites uniques et les taux d’engagement utilisateur. Si vous interrogez des données démographiques, vous pourriez poser des questions sur l’âge et sur les revenus par zone géographique.

Une fois que vous vous êtes familiarisé avec les données, retournez ensuite au tableau de bord et placez votre curseur dans la zone de question. Cette opération ouvre l’écran Questions et réponses.

![Écran Questions et réponses](media/end-user-q-and-a/power-bi-suggested.png) 

Avant même que vous commenciez à taper votre question, Q&R affiche dans un nouvel écran des suggestions de formulation de votre question. Vous voyez des phrases et des questions contenant le nom des tables dans les jeux de données sous-jacents et vous pouvez également voir les questions *proposées* créées par le propriétaire du jeu de données.

Vous pouvez sélectionner une d'entre elles pour les ajouter à la question et l’affiner afin de trouver une réponse spécifique. 

![Écran Questions et réponses](media/end-user-q-and-a/power-bi-result.png) 

Power BI peut aussi vous aider à poser des questions à l’aide de fonctionnalités telles que des invites, l’autocomplétion et des signaux visuels. Power BI fournit cette aide pour la fonctionnalité Questions et réponses qui est disponible dans les tableaux de bord et les rapports, ainsi que pour le visuel Questions et réponses. Nous abordons ces fonctionnalités en détail ci-dessous, dans la section [Créer un visuel Questions et réponses en tapant une requête en langage naturel](#create-a-qa-visual-by-typing-a-natural-language-query).

<!-- ![video](../visuals/media/end-user-q-and-a/qna4.gif) -->


## <a name="the-qa-visual-in-power-bi-reports"></a>Visuel Questions et réponses dans les rapports Power BI

Le visuel Questions et réponses vous permet de poser des questions en langage naturel et d’obtenir des réponses sous la forme d’un visuel. Le visuel Questions et réponses se comporte comme les autres types de visuels de rapport. Il prend en charge le filtrage croisé, la sélection croisée, les signets et les commentaires. 

Vous pouvez identifier un visuel Questions et réponses par sa zone de question dans la partie supérieure. C’est là que vous entrez ou tapez des questions en langage naturel. Le visuel Questions et réponses peut être réutilisé pour poser des questions sur vos données. Quand vous quittez le rapport, le visuel de Questions et réponses retrouve sa configuration par défaut. 

![Capture d’écran du visuel Questions et réponses par défaut](media/end-user-q-and-a/power-bi-q-and-a-default.png)


## <a name="use-qa"></a>Utiliser Questions et réponses 
Pour utiliser Questions et réponses dans un tableau de bord ou pour utiliser le visuel Questions et réponses dans un rapport, sélectionnez l’une des questions suggérées ou tapez votre propre question en langage naturel. 

### <a name="create-a-qa-visual-by-using-a-suggested-question"></a>Créer un visuel Questions et réponses à l’aide d’une question suggérée

Ici, nous avons sélectionné **top geo states by total units** (principaux États géographiques par nombre total d’unités). Power BI essaie de sélectionner le type de visuel le plus adapté pour représenter les données. Dans ce cas, il sélectionne une carte.

![Carte du visuel Questions et réponses](media/end-user-q-and-a/power-bi-q-and-a-suggested.png)

Toutefois, vous pouvez indiquer à Power BI un type de visuel spécifique à utiliser, en l’ajoutant à votre requête en langage naturel. Gardez à l’esprit que les types de visuels ne sont pas tous toujours disponibles ou adaptés pour vos données. Par exemple, la représentation de ces données dans un graphique en nuages de points ne serait pas pertinente. En revanche, l’utilisation d’une carte choroplèthe serait une bonne option.

![Visuel Questions et réponses sous forme de carte choroplèthe](media/end-user-q-and-a/power-bi-filled-map.png)

### <a name="create-a-qa-visual-by-typing-a-natural-language-query"></a>Créer un visuel Questions et réponses en tapant une requête en langage naturel


Si vous n’êtes pas sûr du type de questions à poser ou de la terminologie à employer, développez **Montrer toutes les suggestions** ou examinez les autres visuels dans le rapport. Vous pourrez ainsi vous familiariser avec les termes et le contenu du jeu de données.

1. Tapez votre question dans le champ Questions et réponses en langage naturel. À mesure que vous tapez votre question, Power BI vous aide avec l’autocomplétion, des signaux visuels et des commentaires.

    **Autocomplétion** : à mesure que vous tapez votre question, la fonctionnalité Questions et réponses de Power BI affiche des suggestions pertinentes et contextuelles qui vous aident à devenir rapidement productif avec le langage naturel. Pendant la saisie, vous recevez des commentaires et des résultats immédiats. L’expérience est similaire à la saisie dans un moteur de recherche.

    Dans cet exemple, la suggestion que nous voulons est la dernière. 

    ![Questions et réponses avec un mot souligné en bleu](media/end-user-q-and-a/power-bi-autocomplete.png)

    **Traits de soulignement rouges/bleus** : la fonctionnalité Questions et réponses de Power BI affiche des mots avec des traits de soulignement pour vous aider à voir les mots qu’a reconnus Power BI et ceux qu’il n’a pas reconnus. Un trait de soulignement bleu plein indique que Power BI a reconnu le mot. L’exemple ci-dessous montre que la fonctionnalité Questions et réponses a reconnu le mot **store** (magasin).

    ![Questions et réponses avec une liste déroulante de suggestions pour compléter la question](media/end-user-q-and-a/power-bi-blue.png)

    Sélectionnez un mot souligné en bleu pour afficher la liste déroulante des questions suggérées. 

    ![Liste déroulante « Vous pouvez également essayer : »](media/end-user-q-and-a/power-bi-try.png)


    Souvent, lorsque vous tapez un mot dans Questions et réponses, celui-ci est marqué d’un trait de soulignement rouge. Un trait de soulignement rouge peut indiquer deux problèmes potentiels. Le premier type de problème appartient à la catégorie « fiabilité faible ». Si vous tapez un mot vague ou ambigu, le champ est souligné en rouge. Le mot « Location » (Emplacement) en est un exemple. Plusieurs champs peuvent contenir le mot « Location », si bien que le système utilise un trait de soulignement rouge pour vous inviter à choisir le champ que vous souhaitez. Dans cet exemple, Power BI vous invite à sélectionner le champ que vous souhaitez utiliser pour « VanArsdel ».
    
    ![Terme souligné en rouge dans la zone de question de Questions et réponses](media/end-user-q-and-a/power-bi-q-and-a-red.png)
    
    Un autre exemple de niveau de fiabilité faible pourrait être de saisir le mot « area » (région) et d’obtenir l’affichage de la colonne « district ». La fonctionnalité Questions et réponses Power BI reconnaît les mots de même signification, grâce à son intégration à Bing et Office. Questions et réponses souligne le mot en rouge pour vous indiquer qu’il ne s’agit pas d’une correspondance directe.

    ![Questions et réponses reformule la question à l’aide d’un synonyme](media/end-user-q-and-a/power-bi-red.png)

    Le deuxième type de problème se pose quand Questions et réponses ne reconnaît pas du tout le mot. L’utilisation du mot « geography » alors qu’il ne figure pas dans les données en est un exemple. Le mot figure dans le dictionnaire anglais, mais Questions et réponses marque ce terme d’un trait de soulignement rouge. La fonctionnalité Questions et réponses de Power BI ne peut pas créer de visualisation et vous suggère de demander au concepteur de rapports d’ajouter le terme.

    ![Questions et réponses suggérant de demander au concepteur d’ajouter le mot « geography »](media/end-user-q-and-a/power-bi-geography.png)

    **Suggestions** : lorsque vous tapez la question, Power BI vous signale s’il ne la comprend pas et tente de vous aider. Dans l’exemple ci-dessous, Power BI vous demande « Vous voulez dire... » et suggère une autre formulation de votre question avec la terminologie employée dans votre jeu de données. 

    ![Visuel Questions et réponses proposant des suggestions de correction](media/end-user-q-and-a/power-bi-q-and-a-did-you-mean.png)

    Une fois la correction de Power BI sélectionnée, les résultats s’affichent sous la forme d’un graphique en courbes. 

    ![Résultats du visuel Questions et réponses sous la forme d’un graphique en courbes](media/end-user-q-and-a/power-bi-q-and-a-line.png)


    Toutefois, vous pouvez remplacer le graphique en courbes par un autre type de visuel.  

    ![Visuel Questions et réponses avec « as a column chart » (sous forme d’histogramme) ajouté à la question](media/end-user-q-and-a/power-bi-q-and-a-specify-type.png)



## <a name="considerations-and-troubleshooting"></a>Considérations et résolution des problèmes

**Question** : Je ne vois pas Questions et réponses sur ce tableau de bord.    
**Réponse 1** : Si vous ne voyez pas de zone de question, commencez par vérifier vos paramètres. Pour ce faire, sélectionnez l’icône d’engrenage en haut à droit de votre barre d’outils Power BI.   
![icône d’engrenage](media/end-user-q-and-a/power-bi-settings.png)

Choisissez ensuite **Paramètres** > **Tableaux de bord**. Vérifiez qu’il y a une coche à côté de l’option **Afficher la zone de recherche de Questions et réponses dans ce tableau de bord**.    
![Paramètres Questions et réponses pour le tableau de bord](media/end-user-q-and-a/power-bi-turn-on.png)  


**Réponse 2** : Parfois, vous n’avez pas accès aux paramètres. Si le *concepteur* du tableau de bord ou votre administrateur a désactivé Questions et réponses, vérifiez auprès d’eux s’il est possible de le réactiver.   

**Question** : Je n’obtiens pas les résultats attendus quand je tape une question.    
**Réponse** : Sélectionnez l’option permettant de contacter le propriétaire du rapport ou du tableau de bord. Vous pouvez le faire directement à partir de la page de tableau de bord Questions et réponses ou du visuel Questions et réponses. Ou bien vous pouvez rechercher le propriétaire à partir de l’en-tête Power BI.  Il y a beaucoup de choses que le concepteur peut faire pour améliorer les résultats de Questions et réponses. Par exemple, il peut renommer des colonnes dans le jeu de données pour utiliser des termes qui sont faciles à comprendre (`CustomerFirstName` au lieu de `CustFN`). Étant donné que le concepteur connaît parfaitement le jeu de données, il peut également trouver des questions utiles et les ajouter aux questions suggérées de Questions et réponses.

![Afficher les informations de contact](media/end-user-q-and-a/power-bi-q-and-a-contact.png)

## <a name="privacy"></a>Confidentialité

Microsoft est susceptible d’utiliser vos questions pour améliorer Power BI. Pour plus d’informations, consultez la [Déclaration de confidentialité Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839).

## <a name="next-steps"></a>Étapes suivantes
Pour savoir comment un visuel Questions et réponses est créé et géré par un *concepteur* de rapports, consultez [Type de visuel Questions et réponses](../visuals/power-bi-visualization-q-and-a.md).
