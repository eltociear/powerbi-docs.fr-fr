---
title: Se connecter à des données créées par des dataflows Power BI dans Power BI Desktop (préversion)
description: Se connecter et utiliser facilement des dataflows dans Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 09/10/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: f3964b96f8f282772f6d511c9c412e0caabd1d00
ms.sourcegitcommit: c51461690e8faa121a1325957ca79b7a3975e8b8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44512914"
---
# <a name="connect-to-data-created-by-power-bi-dataflows-in-power-bi-desktop-preview"></a>Se connecter à des données créées par des dataflows Power BI dans Power BI Desktop (préversion)
Dans **Power BI Desktop**, vous pouvez vous connecter à des données créées par des **dataflows Power BI** comme toute autre source de données dans Power BI Desktop.

![Se connecter à des dataflows](media/desktop-connect-dataflows/connect-dataflows_01.png)

Le connecteur **Dataflows Power BI (préversion)** vous permet d’établir des connexions à des entités créées par des dataflows dans le service Power BI. Les dataflows étant actuellement en préversion, vous devez effectuer certaines étapes pour rendre le connecteur de dataflows disponible sur votre système. 


## <a name="download-and-enable-the-power-bi-dataflows-connector-preview"></a>Télécharger et activer le connecteur Dataflows Power BI (préversion)

Vous devez télécharger une copie du connecteur **Dataflows Power BI**, puis la copier à un emplacement spécifique sur votre ordinateur. Dans une prochaine mise à jour mensuelle de Power BI Desktop, le connecteur sera inclus automatiquement dans la liste des connecteurs de données ; ces étapes ne seront alors plus nécessaires.

Vous pouvez télécharger le **connecteur Dataflows Power BI** à cet emplacement : [Connecteur Dataflows Power BI](https://visuals.azureedge.net/cds-analytics/PublicPreview/CDSA.mez)

Effectuez les étapes suivantes pour rendre le connecteur **Dataflows Power BI** (préversion) disponible sur votre ordinateur :

1. Téléchargez une copie du fichier .MEZ (le fichier de connecteur de données). Les clients de la préversion privée recevront des informations de téléchargement pour le fichier .MEZ directement de Microsoft.

2. Placez le fichier de connecteur de données téléchargé dans le dossier suivant sur votre ordinateur : **Documents > Power BI Desktop > Dossier des connecteurs personnalisés**

3. Dans Power BI Desktop, sélectionnez **Fichier > Options et paramètres > Options**, puis sélectionnez **Fonctionnalités en préversion** dans le volet gauche.

    ![Activer les connecteurs personnalisés](media/desktop-connect-dataflows/connect-dataflows_02.png)

4. Cochez la case **Connecteurs de données personnalisés** si ce n’est déjà fait. 

5. Redémarrez **Power BI Desktop** pour que le connecteur apparaisse.

## <a name="use-the-power-bi-dataflows-connector-preview"></a>Utiliser le connecteur Dataflows Power BI (préversion)
Une fois que **Power BI Desktop** a redémarré, le connecteur apparaît en tant que source de données disponible. Pour vous connecter à un pool de données, sélectionnez **Obtenir des données > Services en ligne > Dataflows Power BI (bêta)** comme illustré ci-dessous :

![Se connecter à des dataflows](media/desktop-connect-dataflows/connect-dataflows_01.png)

## <a name="considerations-and-limitations"></a>Considérations et limitations

Pour utiliser cette préversion du **connecteur Dataflows Power BI**, vous devez exécuter la version la plus récente de **Power BI Desktop**. Vous pouvez toujours [télécharger Power BI Desktop](desktop-get-the-desktop.md) et l’installer sur votre ordinateur pour être certain d’avoir la version la plus récente.  

Remarque : Quand le connecteur Dataflows Power BI apparaîtra lors d’une prochaine mise à jour mensuelle de **Power BI Desktop**, vous *devrez* supprimer ce fichier .MEZ téléchargé de votre dossier **Documents > Power BI Desktop > Connecteurs personnalisés** afin d’éviter tout conflit. 


## <a name="next-steps"></a>Étapes suivantes
Les connexions de données Power BI permettent d’effectuer toutes sortes de choses intéressantes. Il existe également des articles sur **Power BI Desktop** qui pourront vous être utiles :

* [Sources de données dans Power BI Desktop](desktop-data-sources.md)
* [Mettre en forme et combiner des données dans Power BI Desktop](desktop-shape-and-combine-data.md)
* [Entrer des données directement dans Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   

