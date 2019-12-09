---
title: Utiliser une extraction interrapport dans Power BI Desktop
description: En savoir plus sur l’extraction d’un rapport à l’autre dans Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/18/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 7189ef77446446b56b1dcb55b43b022d0fc5c057
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "73868778"
---
# <a name="use-cross-report-drillthrough-in-power-bi-desktop"></a>Utiliser une extraction interrapport dans Power BI Desktop

Avec la fonctionnalité d’extraction interrapport de Power BI Desktop, vous pouvez passer contextuellement d’un rapport à un autre. Cela est vrai tant que les rapports se trouvent dans le même espace de travail ou dans la même application dans le service Power BI. Utilisez l’extraction interrapport pour connecter deux rapports ou plus qui ont un contenu associé et transmettre le contexte de filtre avec la connexion interrapport. Dans cet article, vous allez apprendre à configurer une extraction interrapport pour les rapports Power BI, et ce que les utilisateurs observent lorsqu’ils utilisent l’extraction interrapport eux-mêmes.

![Capture d’écran de l’option d’extraction de Power BI Desktop](media/desktop-cross-report-drill-through/cross-report-drill-through-01.png)

Il est important de comprendre les définitions suivantes avant de commencer à configurer et utiliser l’extraction interrapport :

* **Élément visuel source :** L’élément visuel qui appelle l’action d’extraction à l’aide du menu contextuel de l’élément visuel.
* **Rapport source :** Le rapport qui contient l’élément visuel source pour l’extraction interrapport.
* **Page cible :** Page sur laquelle l’utilisateur arrive après l’initialisation d’une action d’extraction.
* **Rapport cible :** Le rapport qui contient la page cible pour l’extraction interrapport.


> [!NOTE]
> Avec la fonctionnalité d’extraction interrapport de Power BI Desktop, vous pouvez passer contextuellement d’un rapport à un autre. Cela est vrai tant que les rapports se trouvent dans le même espace de travail ou dans la même application dans le service Power BI. Cela ne s’applique pas lors de l’accès à des rapports partagés individuellement dans *Mon espace de travail* ([Rapports partagés avec moi](service-share-dashboards.md#share-a-dashboard-or-report)) ; à la place, vous devez accéder au rapport dans l’espace de travail à partir duquel il a été initialement partagé.


## <a name="enable-cross-report-drillthrough"></a>Activer l’extraction interrapport

Pour permettre à un rapport d’être la cible d’une extraction interrapport, vous devez activer la fonctionnalité pour ce rapport dans la fenêtre **Options**. Accédez à **Fichier** > **Options et paramètres** > **Options**, puis allez dans **Paramètres du rapport** vers le bas de la page sur la gauche.

Activez la case à cocher **Autoriser les visuels de ce rapport à utiliser des cibles d'extraction d'autres rapports**, comme indiqué dans l’image suivante.

![Capture d’écran de la fenêtre Options, avec les paramètres de rapport mis en surbrillance](media/desktop-cross-report-drill-through/cross-report-drill-through-02.png)

L’extraction interrapport est maintenant activée.

## <a name="set-up-cross-report-drillthrough"></a>Configurer l’extraction interrapport

La configuration de l’extraction interrapport est similaire à la configuration de l’extraction dans un rapport. L’extraction est activée sur la page cible, ce qui permet à d’autres visuels de cibler la page activée pour l’extraction. Pour plus d’instructions sur la création d’une extraction dans un rapport unique, consultez [Utiliser une extraction dans Power BI Desktop](desktop-drillthrough.md).

Pour démarrer le processus de configuration, vous devez effectuer deux étapes initiales :

* Configurez une page cible d’extraction, qui sera ensuite accessible à partir d’autres rapports dans l’espace de travail ou l’application.
* Autorisez un rapport à voir les pages d’extraction en dehors de son propre rapport.

Recherchez les options d’extraction dans la section **Champs** du volet **Visualisations**, comme illustré dans l’image suivante.

![Capture d’écran du volet Visualisations, avec les options d’extraction mises en surbrillance](media/desktop-cross-report-drill-through/cross-report-drill-through-03.png)

La première étape de l’activation de l’extraction d’une page consiste à valider les modèles de données pour les rapports source et cible. Assurez-vous que : 

* Les champs que vous souhaitez passer existent dans les deux modèles de données.
* Les noms des champs, ainsi que les noms des tables auxquelles ils appartiennent, sont identiques (les chaînes doivent également correspondre et respecter la casse).

Par exemple, si vous souhaitez transmettre un filtre sur le champ *Pays* dans la table *Géographie*, les deux modèles doivent avoir une table *Géographie* et un champ *Pays* dans cette table. Si ce n’est pas le cas, vous devez mettre à jour le nom du champ ou le nom de la table dans le modèle sous-jacent. Le simple fait de mettre à jour le nom d’affichage des champs ne fonctionne pas pour l’extraction interrapport. (Notez que les schémas de chaque rapport n’ont pas besoin d’être exactement identiques.)

Pour commencer la configuration, vous devez préparer la page cible. Dans Power BI Desktop, accédez à la page et assurez-vous que le bouton bascule d’extraction **Interrapport** est défini sur **Activé**. 

![Capture d’écran du bouton bascule Interrapport activé](media/desktop-cross-report-drill-through/cross-report-drill-through-03.png)

Ensuite, faites glisser les champs que vous souhaitez utiliser comme cible d’extraction sur le canevas. Indiquez si vous souhaitez que le champ soit utilisé comme catégorie, ou résumé comme une mesure. À ce stade, vous pouvez choisir de désactiver le bouton **Conserver tous les filtres** pour le visuel. Si vous ne souhaitez pas transmettre d’autres filtres appliqués du visuel source à votre visuel d’extraction cible, sélectionnez **Désactivé**.

> [!NOTE]
> Si vous utilisez la page pour l’extraction interrapport uniquement, vous devez supprimer le bouton **Retour** qui est automatiquement ajouté. Le bouton **Retour** ne fonctionne que pour la nagivation dans un rapport unique. 

Une fois que vous avez configuré le visuel, veillez à enregistrer le rapport si vous êtes dans le service Power BI, ou à enregistrer et publier le rapport si vous utilisez Power BI Desktop.

La section précédente a décrit comment activer l’extraction interrapport pour Power BI Desktop (dans la fenêtre **Options**). Si vous utilisez la service Power BI pour créer une cible d’extraction interrapport, pour activer cette dernière, vous devez faire ce qui suit : 

1. Sélectionnez l’espace de travail dans lequel votre rapport cible et votre rapport source résident.
2. Sélectionnez **Rapports**.
3. Sélectionnez l'icône **Paramètres** pour le rapport source.
4. Assurez-vous que le bouton bascule d’extraction interrapport est **activé**.
5. Enregistrez votre rapport.

Voilà. Votre rapport est prêt à utiliser l’extraction interrapport. 

Dans la section suivante, nous examinons l’expérience du point de vue de l’utilisateur.

## <a name="cross-report-drillthrough-experience"></a>Expérience d’extraction interrapport

Quand vous configurez l’expérience d’extraction interrapport pour un rapport, vous pouvez exploiter la fonctionnalité.

Sélectionnez le rapport source dans le service Power BI, puis sélectionnez un visuel qui utilise le ou les champs de la façon que vous avez spécifiée lors de la configuration de la page cible. Ensuite, cliquez avec le bouton droit sur un point de données pour ouvrir le menu contextuel du visuel, puis sélectionnez **Extraction**.

![Capture d’écran du rapport source dans le service Power BI, avec Extraction en surbrillance](media/desktop-cross-report-drill-through/cross-report-drill-through-01.png)

Vous verrez ensuite les résultats dans la page d’extraction interrapport cible, comme vous l’avez configuré lorsque vous avez créé la cible. Les résultats sont filtrés en fonction des paramètres d’extraction.

> [!IMPORTANT]
> Power BI met en cache les cibles d’extraction interrapport. Si vous apportez des modifications, veillez à actualiser votre navigateur si vous ne voyez pas les cibles d’extraction comme attendu. 

Les cibles interrapport sont mises en forme de la manière suivante : 

`Target Page Name [Target Report Name]`

Une fois que vous avez sélectionné la page cible dans laquelle vous souhaitez effectuer une extraction, Power BI accède à cette page. Il passe le contexte de filtre en fonction des paramètres de la page cible. 

Le contexte de filtre du visuel source peut inclure les éléments suivants : 

* Filtres de niveau rapport, page et visuel affectant le visuel source. 
* Filtrage et mise en surbrillance croisés qui affectent le visuel source. 
* Segments sur la page et segments synchronisés.
* Paramètres d’URL.

Lorsque vous accédez au rapport cible pour l’extraction, Power BI applique uniquement les filtres pour les champs pour lesquels il trouve des correspondances de chaîne exactes pour le nom de champ et le nom de table. Power BI n’applique pas les filtres permanents du rapport cible. Toutefois, il applique votre signet personnel par défaut s’il en existe un. Par exemple, si votre signet personnel par défaut comprend un filtre au niveau du rapport pour *Country = US*, Power BI applique d’abord ce filtre avant d’appliquer le contexte de filtre à partir du visuel source. 

Pour l’extraction interrapport, Power BI passe le contexte de filtre à toutes les pages standard du rapport cible. Power BI ne passe pas le contexte de filtre pour les pages d’info-bulle, car les pages d’info-bulle sont filtrées en fonction de l’objet visuel source qui appelle l’info-bulle.

Si vous souhaitez revenir au rapport source après l’action d’extraction interrapport, utilisez le bouton **Retour** du navigateur. 

## <a name="next-steps"></a>Étapes suivantes

Les articles suivants pourraient également vous intéresser :

* [Utilisation de segments Power BI Desktop](visuals/power-bi-visualization-slicers.md)
* [Utiliser une extraction dans Power BI Desktop](desktop-drillthrough.md)

