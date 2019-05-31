---
title: Utiliser l’extraction de cross-report dans Power BI Desktop
description: Découvrez comment extraire à partir d’un rapport vers un autre dans Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/08/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 45a7cdd3c7b5324f3d618eaba4bdb3968a9549a5
ms.sourcegitcommit: 8bf2419b7cb4bf95fc975d07a329b78db5b19f81
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66375190"
---
# <a name="use-cross-report-drillthrough-in-power-bi-desktop"></a>Utiliser l’extraction de cross-report dans Power BI Desktop

Avec la fonctionnalité de cross-rapport d’extraction dans Power BI Desktop, vous pouvez passer en fonction du contexte d’un rapport vers un autre rapport. Cela est vrai, que les rapports sont dans le même espace de travail ou la même application dans le service Microsoft Power BI. Utiliser l’extraction de cross-rapports pour se connecter à deux ou plusieurs rapports qui ont contenu associé et passe le contexte de filtre, ainsi que la connexion croisée-report. Dans cet article, vous découvrez comment configurer une extraction cross-report pour les rapports Power BI, et ce que les utilisateurs rencontrent lorsqu’ils utilisent le cross-rapport d’extraction pour eux-mêmes.

![Option d’extraction de capture d’écran de Power BI Desktop](media/desktop-cross-report-drill-through/cross-report-drill-through-01.png)

Les définitions suivantes sont importantes pour comprendre, avant de commencer la configuration et à l’aide de cross-rapport d’extraction :

* **Visuel de la source :** L’élément visuel qui appelle l’action d’extraction à l’aide du menu contextuel visual.
* **Rapport de la source :** Le rapport qui contient l’élément visuel source cross-rapport d’extraction.
* **Page cible :** La page un utilisateur accède à après le lancement d’une action d’extraction.
* **Rapport cible :** Le rapport qui contient la page cible de cross-rapport d’extraction.

## <a name="enable-cross-report-drillthrough"></a>Activer l’extraction de cross-report

Pour activer un rapport à la cible d’un cross-rapport d’extraction, vous devez activer la fonctionnalité pour ce rapport dans le **Options** fenêtre. Accédez à **fichier** > **Options et paramètres** > **Options**, puis accédez à **paramètres de rapport** près de la en bas de la page sur la gauche.

Sélectionnez le **autoriser des éléments visuels dans ce rapport pour utiliser des cibles d’extraction à partir d’autres rapports** case à cocher, comme indiqué dans l’image suivante.

![Fenêtre de capture d’écran des Options, avec les paramètres de rapport mis en surbrillance](media/desktop-cross-report-drill-through/cross-report-drill-through-02.png)

Cross-rapport d’extraction est maintenant activé.

## <a name="set-up-cross-report-drillthrough"></a>Configurer l’extraction de cross-report

Configuration des cross-rapport d’extraction est similaire à la configuration d’une extraction dans un rapport. L’extraction est activée dans la page cible, ce qui permet d’autres éléments visuels cibler la page est activée pour l’extraction. Pour les étapes de création d’extraction dans un rapport unique, consultez [utiliser l’extraction dans Power BI Desktop](desktop-drillthrough.md).

Pour démarrer le processus d’installation, vous devez effectuer quelques étapes initiales :

* Configurer une page de cible d’extraction, qui est ensuite accessible à partir d’autres rapports dans l’espace de travail ou une application.
* Autoriser un rapport pour voir les pages d’extraction à partir en dehors de son propre rapport.

Trouver les options d’extraction dans le **champs** section de la **visualisations** volet, comme indiqué dans l’image suivante.

![Volet de la capture d’écran de visualisations, avec les options d’extraction mis en surbrillance](media/desktop-cross-report-drill-through/cross-report-drill-through-03.png)

Activation de l’extraction d’une page de la première étape consiste à valider les modèles de données pour les rapports source et cible. Assurez-vous que : 

* Vous souhaitez transmettre des champs existent dans les modèles de données.
* Les noms des champs et les noms des tables à laquelle ils appartiennent, sont identiques (les chaînes doivent également correspondre et respectent la casse).

Par exemple, si vous souhaitez passer d’un filtre sur le champ *pays* au sein de la table *Geography*, les deux modèles doivent avoir un *Geography* table et un *pays* champ au sein de cette table. Si ce n’est pas le cas, vous devez mettre à jour le nom du champ ou le nom de la table dans le modèle sous-jacent. Mettre à jour le nom d’affichage des champs ne fonctionnera pas correctement pour cross-rapport d’extraction. (Notez que les schémas dans chaque rapport ne doivent être identiques).

Pour vous familiariser avec le programme d’installation, vous devez préparer la page cible. Dans Power BI Desktop, accédez à la page et vérifiez que le **Cross-report** activer/désactiver l’extraction est définie sur **sur**. 

![Capture d’écran de Cross-report bouton bascule sur](media/desktop-cross-report-drill-through/cross-report-drill-through-03.png)

Ensuite, faites glisser les champs que vous souhaitez utiliser comme cible d’extraction sur le canevas. Indiquez si vous souhaitez le champ à utiliser en tant que catégorie, ou résumées comme une mesure. À ce stade, vous pouvez sélectionner si vous souhaitez désactiver la **conserver tous les filtres** bascule pour l’élément visuel. Si vous ne souhaitez pas passer autres filtres appliqués à partir de la source visual à votre d’extraction cible visual, sélectionnez **hors**.

> [!NOTE]
> Si vous utilisez la page pour l’extraction de cross-report uniquement, vous devez supprimer le **retour** bouton est ajouté automatiquement. Le **retour** bouton fonctionne uniquement pour les nagivation dans un rapport unique. 

Une fois que vous avez configuré l’élément visuel, assurez-vous que vous enregistrez le rapport si vous êtes dans le service Power BI, ou enregistrez et publiez le rapport si vous utilisez Power BI Desktop.

La section précédente a décrit comment activer l’extraction de cross-report pour Power BI Desktop (dans le **Options** fenêtre). Si vous utilisez le service Power BI pour créer une cible de cross-rapport d’extraction, pour activer l’extraction de cross-report vous devez : 

1. Sélectionnez l’espace de travail dans lequel votre rapport source et le rapport cible résident.
2. Sélectionnez **rapports**.
3. Sélectionnez le **paramètres** icône pour le rapport source.
4. Assurez-vous que le bouton bascule entre-rapport d’extraction est **sur**.
5. Enregistrer votre rapport.

Voilà. Votre rapport est prêt pour l’expérience de cross-rapport d’extraction. 

Dans la section suivante, nous examinons l’expérience de l’utilisateur.

## <a name="cross-report-drillthrough-experience"></a>Expérience de cross-rapport d’extraction

Lorsque vous configurez l’expérience de cross-rapport d’extraction pour un rapport, vous pouvez placer la fonctionnalité à utiliser.

Sélectionnez le rapport source dans le service Power BI, puis sélectionnez un élément visuel qui utilise les champs de la façon que vous avez spécifié lorsque vous configurez la page cible. Ensuite, cliquez sur un point de données pour ouvrir le menu contextuel visual et sélectionnez **extraction**.

![Capture d’écran du rapport source dans le service Power BI, avec l’extraction de la mise en surbrillance](media/desktop-cross-report-drill-through/cross-report-drill-through-01.png)

Vous verrez ensuite les résultats dans la page de cross-rapport d’extraction cible, tout comme vous les définir lors de la création de la cible. Les résultats sont filtrés en fonction des paramètres d’extraction.

> [!IMPORTANT]
> Power BI met en cache les cibles de cross-rapport d’extraction. Si vous apportez des modifications, veillez à ce que vous actualisez votre navigateur si vous ne voyez pas les cibles d’extraction comme prévu. 

Cross-report cibles sont mis en forme de la manière suivante : 

`Target Page Name [Target Report Name]`

Après avoir sélectionné la page cible à laquelle vous souhaitez extraire, Power BI accède à cette page. Il transmet le contexte de filtre en fonction des paramètres de la page cible. 

Contexte de filtre de la source visual peut être les suivants : 

* Rapport, page et des filtres de niveau visuel qui affectent l’élément visuel source. 
* Filtrage croisé et la sélection croisée qui affectent l’élément visuel source. 
* Segments dans la page et les synchroniser les segments.
* Paramètres d’URL.

Lorsque vous arrivez sur le rapport cible pour l’extraction, Power BI s’applique uniquement les filtres pour les champs pour lesquels il trouve la chaîne exacte correspond à pour nom de champ et le nom de la table. Power BI ne s’applique pas rémanentes filtres du rapport cible. Il est le cas, toutefois, appliquer votre signet personnel par défaut s’il en existe. Par exemple, si votre signet personnel par défaut inclut un filtre de rapport pour *Country = US*, Power BI s’applique ce filtre tout d’abord, avant d’appliquer le contexte de filtre du visuel de la source. 

Pour l’extraction de cross-report, Power BI transmet le contexte de filtre à toutes les pages standards dans le rapport cible. Contexte de filtre pour les pages d’info-bulle, ne remplit pas Power BI, car les pages d’info-bulle sont filtrées selon le visuel source qui appelle l’info-bulle.

Si vous souhaitez revenir au rapport source après l’action cross-rapport d’extraction, utilisez le navigateur **retour** bouton. 

## <a name="next-steps"></a>Étapes suivantes

Les articles suivants pourraient également vous intéresser :

* [Utilisation de segments Power BI Desktop](visuals/power-bi-visualization-slicers.md)
* [Utiliser une extraction dans Power BI Desktop](desktop-drillthrough.md)

