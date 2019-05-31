---
title: Utiliser l’Analyseur de performances pour examiner les performances d’élément de rapport dans Power BI Desktop
description: Découvrez le fonctionnement des éléments visuels et des éléments de rapport en termes de temps de réponse et l’utilisation des ressources
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/15/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 1851e0a55bf01073a6591f64de43830a72eca89b
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "65854410"
---
# <a name="use-performance-analyzer-to-examine-report-element-performance"></a>Utiliser l’Analyseur de performances pour examiner les performances d’élément de rapport

Dans **Power BI Desktop** vous trouverez comment chacun de vos éléments de rapport, tels que les éléments visuels et des formules DAX, effectuez la sortie. À l’aide de la **Performance Analyzer**, vous pouvez voir et les journaux d’enregistrement mesurer comment chacune de vos éléments de rapport effectue lorsque les utilisateurs interagissent avec eux, et quels aspects de leurs performances sont beaucoup de ressources de la plupart des (ou moins).

![Analyseur de performances](media/desktop-performance-analyzer/performance-analyzer-01.png)

Analyseur de performances inspecte et affiche la durée nécessaire pour la mise à jour ou de l’actualisation de tous les éléments visuels qu’initier des interactions utilisateur et présente les informations afin de vous pouvez afficher, Explorer ou exporter les résultats. Analyseur de performances peut vous aider à identifier les éléments visuels qui impactent les performances de vos rapports et identifier la raison de l’impact.

## <a name="displaying-the-performance-analyzer-pane"></a>Affichage du volet de l’Analyseur de performances

Dans **Power BI Desktop** sélectionner le **vue** ruban. Dans le **afficher** zone de la **vue** ruban que vous pouvez sélectionner la case à cocher à côté **Performance Analyzer** pour afficher le volet de l’Analyseur de performances.

![Sélectionnez l’Analyseur de performances dans le ruban de la vue](media/desktop-performance-analyzer/performance-analyzer-02.png)

Une fois sélectionnée, l’Analyseur de performances s’affiche dans son propre volet, à droite du canevas du rapport.

## <a name="using-performance-analyzer"></a>Utilisation de l’Analyseur de performances

Mesures d’analyseur de performances le temps de traitement (y compris le temps pour créer ou mettre à jour un élément visuel) requis pour mettre à jour les éléments de rapport effectuées à la suite d’interaction de l’utilisateur qui résulte dans une requête en cours d’exécution. Par exemple, l’ajustement d’un segment nécessite le visuel de segment à modifier, une requête à envoyer au modèle de données et les éléments visuels concernés qui doivent être mis à jour à la suite les nouveaux paramètres. 

Pour commencer l’enregistrement Analyseur de performances, il suffit de sélectionner **démarrer l’enregistrement**

![Démarrer l’enregistrement](media/desktop-performance-analyzer/performance-analyzer-03.png)

Les actions que vous effectuez dans le rapport sont affichées et consignées dans le volet de l’Analyseur de performances, dans l’ordre que le visuel est chargé par Power BI. Par exemple, vous avez peut-être un rapport qui les utilisateurs ont dit prend beaucoup de temps à actualiser. Ou certains éléments visuels dans un rapport de prennent beaucoup de temps à afficher lorsqu’un curseur est ajusté. Analyseur de performances peut indiquer quel visuel est la cause du problème, et identifie les aspects de l’élément visuel prend la durée la plus longue à traiter. 

Une fois que vous démarrez l’enregistrement, le **démarrer l’enregistrement** bouton est grisé hors (inactif, étant donné que vous avez déjà commencé l’enregistrement) et le **arrêter** bouton est actif. 

Analyseur de performances recueille et affiche les informations de mesure des performances en temps réel. Afin que chaque fois que vous cliquez sur un élément visuel, déplacer un segment ou interagir de quelque autre manière, analyseur de performances affiche immédiatement les résultats de performances dans le volet.

Si le volet comporte des informations supplémentaires peuvent être affichés, une barre de défilement s’affiche pour accéder à des informations supplémentaires.

Chaque interaction a un identificateur de la section dans le volet, qui décrit l’action qui a lancé les entrées de journal. Dans l’image suivante, l’interaction était que les utilisateurs ont modifié un segment.

![Sections selon le type d’interaction](media/desktop-performance-analyzer/performance-analyzer-04.png)

Informations du journal de chaque visuel comprend le temps passé (durée) pour terminer les catégories de tâches suivantes :

* **Requête DAX** -si une requête DAX était requise, il s’agit de la durée entre l’élément visuel envoyant la requête et pour Analysis Services retourner les résultats.
* **Affichage visuel** -temps nécessaire pour l’élément visuel dessiner sur l’écran, y compris le temps nécessaire pour récupérer des images web ou le géocodage. 
* **Autres** -temps requis par l’élément visuel pour la préparation de requêtes en attente pour les autres éléments visuels terminer ou effectuer d’autres traitements en arrière-plan.

![éléments d’informations de journalisation](media/desktop-performance-analyzer/performance-analyzer-06.png)

Une fois que vous avez manipulé les éléments du rapport que vous souhaitez mesurer avec l’Analyseur de performances, vous pouvez sélectionner le **arrêter** bouton. Les informations de performances restent dans le volet après avoir sélectionné **arrêter** pour pouvoir les analyser.

Pour effacer les informations dans le volet de l’Analyseur de performances, sélectionnez **effacer**. Toutes les informations sont effacées et n’est pas enregistrées lorsque vous sélectionnez **clair**. Consultez la section suivante pour savoir comment enregistrer les informations dans les journaux. 

## <a name="refreshing-visuals"></a>L’actualisation des éléments visuels

Vous pouvez sélectionner **actualiser des éléments visuels** dans le volet de l’Analyseur de performances pour actualiser tous les éléments visuels de la page active du rapport et donc avoir Analyseur de performances à collecter des informations sur tous les visuels de ce type.

Vous pouvez également actualiser des éléments visuels individuels. Lors de l’enregistrement de l’Analyseur de performances, vous pouvez sélectionner **actualiser cet élément visuel** trouvé dans l’angle supérieur droit de chaque visuel, pour actualiser cet élément visuel et capturer les informations de ses performances.

![Actualiser un visuel spécifique](media/desktop-performance-analyzer/performance-analyzer-07.png)

## <a name="saving-performance-information"></a>L’enregistrement des informations sur les performances

Vous pouvez enregistrer les informations que l’Analyseur de performances crée un rapport en sélectionnant le **exporter** bouton. En sélectionnant **exporter** crée un fichier .json contenant des informations à partir du volet de l’Analyseur de performances. 

![Enregistrez le fichier journal pour l’Analyseur de performances](media/desktop-performance-analyzer/performance-analyzer-05.png)


## <a name="next-steps"></a>Étapes suivantes
Pour plus d’informations sur **Power BI Desktop** et la prise en main de cette solution, voir les articles suivants.

* [Qu’est-ce que Power BI Desktop ?](desktop-what-is-desktop.md)
* [Présentation des requêtes dans Power BI Desktop](desktop-query-overview.md)
* [Sources de données dans Power BI Desktop](desktop-data-sources.md)
* [Se connecter aux données dans Power BI Desktop](desktop-connect-to-data.md)
* [Mettre en forme et combiner des données dans Power BI Desktop](desktop-shape-and-combine-data.md)
* [Tâches courantes relatives aux requêtes dans Power BI Desktop](desktop-common-query-tasks.md)   

