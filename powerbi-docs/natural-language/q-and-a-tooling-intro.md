---
title: Présentation des outils Questions et réponses pour entraîner Questions et réponses Power BI (préversion)
description: Présentation des outils Questions et réponses Power BI
author: mohaali
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/17/2019
ms.author: mohaali
ms.openlocfilehash: 17d0a68782f34c09286be5ebe020668a15061ee4
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/06/2020
ms.locfileid: "73874953"
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

    ![Icône d’engrenage du visuel Questions et réponses](media/qna-visual-gear.png)

    La page Mise en route s’ouvre.  

    ![Questions et réponses - Mise en route](media/qna-tooling-dialog.png)

### <a name="review-questions"></a>Passer en revue les questions

Sélectionnez **Passer en revue les questions** pour voir la liste des jeux de données utilisés dans le service Power BI pour votre locataire. La page **Passer en revue les questions** affiche également le propriétaire, l’espace de travail et la date de dernière actualisation du jeu de données. À partir de là, vous pouvez sélectionner un jeu de données et voir les questions posées par les utilisateurs. Les données affichent également les mots qui n’ont pas été reconnus. Toutes les données affichées ici correspondent aux 28 derniers jours.

![Questions et réponses - Passer en revue les questions](media/qna-tooling-review-questions.png)

### <a name="teach-qa"></a>Entraîner Questions et réponses

La section **Enseigner à Questions et réponses** vous permet d’entraîner Questions et réponses à reconnaître des mots. Pour commencer, tapez une question contenant un ou plusieurs mots que Questions et réponses ne reconnaît pas. Questions et réponses vous invite à fournir la définition de ce terme. Entrez un filtre ou un nom de champ correspondant à ce que ce mot représente. Questions et réponses réinterprète ensuite la question d’origine. Si vous êtes satisfait des résultats, vous pouvez enregistrer votre entrée. Pour en savoir plus, consultez [Enseigner à Questions et réponses](q-and-a-tooling-teach-q-and-a.md)

![Enseigner à Questions et réponses - Aperçu des synonymes](media/qna-tooling-teach-fixpreview.png)

### <a name="manage-terms"></a>Gérer les termes

Tout ce que vous avez enregistré dans la section Enseigner à Questions et réponses apparaît ici pour vous permettre de vérifier ou de supprimer les termes que vous avez définis. Actuellement, vous ne pouvez pas modifier une définition existante. Ainsi, pour redéfinir un terme, vous devez supprimer et recréer ce terme.

![Questions et réponses - Gérer les termes](media/qna-manage-terms.png)

## <a name="other-qa-settings"></a>Autres paramètres de Questions et réponses

### <a name="bulk-synonyms"></a>Synonymes en vrac

L’onglet **Modélisation** de Power BI Desktop offre d’autres options pour améliorer l’expérience Questions et réponses. 

1. Dans Power BI Desktop, sélectionnez la vue Modélisation.

2. Sélectionnez un champ ou une table pour afficher le volet **Propriétés**.  Ce volet s’affiche sur le côté droit de la zone de dessin et liste plusieurs actions Questions et réponses. L’une de ces options est **Synonymes**. Dans la zone **Synonymes**, vous pouvez définir rapidement des alternatives pour la table ou le champ que vous sélectionnez. Vous pouvez également définir des synonymes dans la section **Enseigner à Questions et réponses** de la boîte de dialogue Outils, mais il est souvent plus rapide de définir des synonymes ici pour un grand nombre de champs dans une table.

    ![Questions et réponses - Synonymes dans le volet Modélisation](media/qna-modelling-pane-synonyms.png)

3. Pour définir plusieurs synonymes pour un même champ, utilisez des virgules pour délimiter le synonyme suivant.

### <a name="hide-from-qa"></a>Masquer dans Questions et réponses

Vous pouvez également masquer des champs et des tables pour qu’ils n’apparaissent pas dans les résultats de Questions et réponses. 

1. Dans Power BI Desktop, sélectionnez la vue Modélisation.

2. Sélectionnez un champ ou une table pour afficher le volet **Propriétés** et définissez **Est masqué** sur **Activé**.

    Questions et réponses respecte ce paramètre et garantit que ce champ ne sera pas reconnu. Par exemple, vous souhaitez peut-être masquer les champs d’ID et les clés étrangères pour éviter des champs en double inutiles portant le même nom. Même si vous masquez ce champ, vous pouvez encore l’utiliser dans Power BI Desktop dans des visuels en dehors de Questions et réponses.

### <a name="set-a-row-label"></a>Définir une étiquette de ligne

Une étiquette de ligne vous permet de définir la colonne (ou le *champ*) qui identifie le mieux une ligne individuelle dans une table. Par exemple, pour une table nommée « Client », l’étiquette de ligne est généralement « Nom d’affichage ». Le fait de fournir ces métadonnées supplémentaires permet à Questions et réponses de tracer un visuel plus utile quand les utilisateurs tapent « Afficher les ventes par client ». Au lieu de traiter « client » comme une table, il peut utiliser « Nom d’affichage » et afficher un graphique à barres indiquant les ventes de chaque client. Vous pouvez uniquement définir l’étiquette de ligne dans la vue Modélisation. 

1. Dans Power BI Desktop, sélectionnez la vue Modélisation.

2. Sélectionnez une table pour afficher le volet **Propriétés**.

3. Dans la zone **Étiquette de ligne**, sélectionnez un champ.

## <a name="configure-the-linguistic-schema-advanced"></a>Configurer le schéma linguistique (avancé)

Dans Power BI, vous pouvez entraîner et améliorer complètement le moteur de langage naturel au sein de Questions et réponses, y compris modifier le scoring et la pondération des résultats de langage naturel sous-jacents. Pour savoir comment procéder, consultez [Modifier le schéma linguistique de la fonctionnalité Questions et réponses et ajouter des formulations](q-and-a-tooling-advanced.md).

## <a name="next-steps"></a>Étapes suivantes

Il existe diverses bonnes pratiques permettant d’améliorer le moteur de langage naturel. Pour plus d’informations, consultez l’article suivant :

* [Bonnes pratiques pour Questions et réponses](q-and-a-best-practices.md)
