---
title: Présentation des outils Questions et réponses pour entraîner Questions et réponses Power BI (préversion)
description: Présentation des outils Questions et réponses Power BI
author: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/17/2020
ms.author: maggies
ms.openlocfilehash: aaa31851f338832a8c4f4fffb38f12414c859610
ms.sourcegitcommit: 13c4bec679313f2951f1833033316cb8176da8a1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2020
ms.locfileid: "88937467"
---
# <a name="intro-to-qa-tooling-to-train-power-bi-qa-preview"></a>Présentation des outils Questions et réponses pour entraîner Questions et réponses Power BI (préversion)

Avec les *outils* Questions et réponses Power BI, vous pouvez améliorer l’expérience de vos utilisateurs en matière de langage naturel. En tant que concepteur ou administrateur, vous interagissez avec le moteur de langage naturel et apportez des améliorations dans trois domaines : 

- Vous examinez les questions que vos utilisateurs ont posées.
- Vous enseignez à Questions et réponses à comprendre les questions.
- Vous gérez les termes que vous avez enseignés à Questions et réponses.

En plus de ces fonctionnalités d’outils dédiées, l’onglet **Modélisation** dans Power BI Desktop offre plus d’options :  

- Synonymes
- Étiquettes de ligne
- Masquer dans Questions et réponses
- Configuration du schéma linguistique (avancé)

## <a name="get-started-with-qa-tooling"></a>Bien démarrer avec les outils Questions et réponses

Les outils Questions et réponses sont disponibles uniquement dans Power BI Desktop et ne prennent actuellement en charge que le mode d’importation.

1. Ouvrez Power BI Desktop et utilisez Questions et réponses pour créer un visuel. 
2. Dans l’angle du visuel, sélectionnez l’icône d’engrenage. 

    ![Icône d’engrenage du visuel Questions et réponses](media/q-and-a-tooling-intro/qna-visual-gear.png)

    La page Mise en route s’ouvre.  

    ![Questions et réponses - Mise en route](media/q-and-a-tooling-intro/qna-tooling-dialog.png)

### <a name="field-synonyms"></a>Synonymes de champ

Sélectionnez **Synonymes de champ** pour afficher toutes les tables et colonnes qui appartiennent au modèle. Cette vue vous permet d’ajouter d’autres noms pour les faire correspondre aux colonnes pour aider les utilisateurs. Vous pouvez également choisir si une colonne ou une table doit être masquée de Questions et réponses.

![Accueil synonymes de champ Questions et réponses](media/q-and-a-tooling-intro/qna-tooling-field-synonyms-home.png)

Cliquez sur une des tables à développer pour afficher une boîte de dialogue semblable à celle ci-dessous.

![Synonymes de champ Questions et réponses développés](media/q-and-a-tooling-intro/qna-tooling-field-synonyms-expanded.png)

La boîte de dialogue affiche toutes les colonnes et tables, ainsi que leurs termes/synonymes respectifs que les utilisateurs peuvent utiliser pour poser des questions sur le jeu de données. Vous pouvez rapidement voir tous les termes dans un même emplacement et ajouter ou supprimer des termes pour plusieurs colonnes. 

- Ajouter des termes : Si vous avez un champ appelé ventes, vous pouvez décider d’ajouter un terme « chiffre d’affaires » pour qu’un utilisateur puisse utiliser ce terme sans avoir à utiliser le mot ventes. Cliquez sur le signe Ajouter pour ajouter rapidement un nouveau terme

- Inclure dans Questions et réponses : cette option permet d’omettre une colonne ou une table de Questions et réponses, ce qui signifie qu’elle ne sera pas affichée et qu’aucun résultat ne pourra être affiché avec cette colonne. Une situation dans laquelle vous pouvez décider de ne pas inclure une colonne est lorsque vous traitez des dates. S’il existe de nombreux champs de date, ou de clés étrangères, vous pouvez décider de supprimer tous les champs de date sauf un, afin que la colonne de date correcte soit choisie lorsqu’un utilisateur pose une question relative à la date.

- Termes suggérés : Questions et réponses vous recommande également les termes suggérés récupérés à partir de notre moteur de suggestions pour vous aider à ajouter rapidement des termes/synonymes. Si les suggestions ne sont pas ajoutées, elles continuent de fonctionner, mais donnent à l’utilisateur une ligne en pointillés orange indiquant que Questions et réponses pense avoir une réponse, sans en avoir la certitude. Si le synonyme suggéré est correct, cliquez sur l’icône + pour qu’il puisse être utilisé comme synonyme. Si la suggestion est incorrecte, cliquez sur le x, ce qui supprime le terme et vous assurez qu’il ne sera pas utilisé comme terme/synonyme et ne fonctionnera pas au sein de Questions et réponses. Les suggestions sont alimentées par le dictionnaire Office et proviennent également de renommages dans un rapport

### <a name="review-questions"></a>Passer en revue les questions

Sélectionnez **Passer en revue les questions** pour voir la liste des jeux de données utilisés dans le service Power BI pour votre locataire. La page **Passer en revue les questions** affiche également le propriétaire, l’espace de travail et la date de dernière actualisation du jeu de données. À partir de là, vous pouvez sélectionner un jeu de données et voir les questions posées par les utilisateurs. Les données affichent également les mots qui n’ont pas été reconnus. Toutes les données affichées ici correspondent aux 28 derniers jours.

![Questions et réponses - Passer en revue les questions](media/q-and-a-tooling-intro/qna-tooling-review-questions.png)

### <a name="teach-qa"></a>Entraîner Questions et réponses

La section **Enseigner à Questions et réponses** vous permet d’entraîner Questions et réponses à reconnaître des mots. Pour commencer, tapez une question contenant un ou plusieurs mots que Questions et réponses ne reconnaît pas. Questions et réponses vous invite à fournir la définition de ce terme. Entrez un filtre ou un nom de champ correspondant à ce que ce mot représente. Questions et réponses réinterprète ensuite la question d’origine. Si vous êtes satisfait des résultats, vous pouvez enregistrer votre entrée. Pour en savoir plus, consultez [Enseigner à Questions et réponses](q-and-a-tooling-teach-q-and-a.md)

![Enseigner à Questions et réponses - Aperçu des synonymes](media/q-and-a-tooling-intro/qna-tooling-teach-fixpreview.png)

### <a name="manage-terms"></a>Gérer les termes

Tout ce que vous avez enregistré dans la section Enseigner à Questions et réponses apparaît ici pour vous permettre de vérifier ou de supprimer les termes que vous avez définis. Actuellement, vous ne pouvez pas modifier une définition existante. Ainsi, pour redéfinir un terme, vous devez supprimer et recréer ce terme.

![Questions et réponses - Gérer les termes](media/q-and-a-tooling-intro/qna-manage-terms.png)

### <a name="suggest-questions"></a>Suggérer des questions

> [!NOTE]
> Les questions suggérées s’affichent pour toutes les instances du visuel Questions et réponses. Il n’est pas possible de créer un ensemble distinct de suggestions pour chaque visuel Questions et réponses.
> 
> 

Si vous n’avez pas effectué de configuration, le visuel Questions et réponses suggère plusieurs questions pour commencer. Ces questions sont générées automatiquement en fonction de votre modèle de données. Dans **Suggérer des questions**, vous pouvez remplacer ces questions générées automatiquement par vos propres questions.

Pour commencer, tapez la question que vous souhaitez ajouter dans la zone de texte. La section Aperçu montre le résultat obtenu dans le visuel Questions et réponses. 

:::image type="content" source="media/q-and-a-tooling-intro/power-bi-qna-suggest-questions.png" alt-text="Suggérer des questions Questions et réponses":::
 
Sélectionnez le bouton **Ajouter** pour ajouter cette question à **Vos suggestions de questions**. Chaque question supplémentaire est ajoutée à la fin de cette liste. Les questions s’affichent dans le visuel Questions et réponses dans le même ordre que dans cette liste. 

:::image type="content" source="media/q-and-a-tooling-intro/power-bi-qna-save-suggest-questions.png" alt-text="Enregistrer les suggestions de questions":::
 
Pensez à sélectionner **Enregistrer** pour afficher votre liste de suggestions de questions dans le visuel Questions et réponses. 

## <a name="other-qa-settings"></a>Autres paramètres de Questions et réponses

### <a name="set-a-row-label"></a>Définir une étiquette de ligne

Une étiquette de ligne vous permet de définir la colonne (ou le *champ*) qui identifie le mieux une ligne individuelle dans une table. Par exemple, pour une table nommée « Client », l’étiquette de ligne est généralement « Nom d’affichage ». Le fait de fournir ces métadonnées supplémentaires permet à Questions et réponses de tracer un visuel plus utile quand les utilisateurs tapent « Afficher les ventes par client ». Au lieu de traiter « client » comme une table, il peut utiliser « Nom d’affichage » et afficher un graphique à barres indiquant les ventes de chaque client. Vous pouvez uniquement définir l’étiquette de ligne dans la vue Modélisation. 

1. Dans Power BI Desktop, sélectionnez la vue Modélisation.

2. Sélectionnez une table pour afficher le volet **Propriétés**.

3. Dans la zone **Étiquette de ligne**, sélectionnez un champ.

## <a name="configure-the-linguistic-schema-advanced"></a>Configurer le schéma linguistique (avancé)

Dans Power BI, vous pouvez entraîner et améliorer complètement le moteur de langage naturel au sein de Questions et réponses, y compris modifier le scoring et la pondération des résultats de langage naturel sous-jacents. Pour savoir comment procéder, consultez [Modifier le schéma linguistique de la fonctionnalité Questions et réponses et ajouter des formulations](q-and-a-tooling-advanced.md).

## <a name="next-steps"></a>Étapes suivantes

Il existe diverses bonnes pratiques permettant d’améliorer le moteur de langage naturel. Pour plus d’informations, consultez [Meilleures pratiques de Questions et réponses](q-and-a-best-practices.md).
