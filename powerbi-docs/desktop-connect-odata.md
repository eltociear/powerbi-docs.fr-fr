---
title: Se connecter à un flux OData dans Power BI Desktop
description: Se connecter à un flux OData et utiliser les données dans Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 7749953d8a913c25000c282234b3215d1741e129
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "65514270"
---
# <a name="connect-to-odata-feeds-in-power-bi-desktop"></a>Se connecter à des flux OData dans Power BI Desktop
Dans Power BI Desktop, vous pouvez vous connecter à un **flux OData** et utiliser les données sous-jacentes comme n’importe quelle autre source de données dans Power BI Desktop.

Pour vous connecter à un flux OData, sélectionnez **Obtenir des données > Flux OData** dans le ruban **Accueil** de Power BI Desktop.

![](media/desktop-connect-odata/connect-to-odata_1.png)

Dans la fenêtre **Flux OData** qui s’affiche, tapez ou collez l’URL de votre flux OData dans le champ, puis sélectionnez **OK**.

![](media/desktop-connect-odata/connect-to-odata_2.png)

Power BI Desktop se connecte au flux OData et affiche les tables disponibles et les autres éléments de données dans la fenêtre **Navigateur**. Lorsque vous sélectionnez un élément, le volet droit de la fenêtre **Navigateur** affiche un aperçu des données. Vous pouvez sélectionner autant de tables que vous le voulez. La fenêtre **Navigateur** affiche un aperçu de la table sélectionnée.

![](media/desktop-connect-odata/connect-to-odata_3.png)

Vous pouvez utiliser le bouton **Modifier**, qui lance l’**Éditeur de requête**, dans lequel vous pouvez mettre en forme et transformer les données du flux OData avant de les importer dans Power BI Desktop. Vous pouvez également cliquer sur le bouton **Charger** et importer tous les éléments de données que vous avez sélectionnés dans le volet de gauche.

Lorsque vous sélectionnez **Charger**, Power BI Desktop importe les éléments sélectionnés et affiche une fenêtre **Charger** qui présente la progression de l’importation.

![](media/desktop-connect-odata/connect-to-odata_4.png)

Une fois le chargement terminé, Power BI Desktop place les tables et les autres éléments de données sélectionnés dans le volet **Champs**, à droite de la vue *Rapports* dans Power BI Desktop.

![](media/desktop-connect-odata/connect-to-odata_5.png)

C’est tout.

Vous êtes maintenant prêt à utiliser les données importées du flux OData dans Power BI Desktop pour créer des éléments visuels et des rapports ou bien pour interagir avec toutes les autres données auxquelles vous souhaitez vous connecter et que vous voulez importer, par exemple d’autres classeurs Excel, des bases de données ou toute autre source de données.

## <a name="next-steps"></a>Étapes suivantes
Vous pouvez connecter toutes sortes de données à l’aide de Power BI Desktop. Pour plus d’informations sur les sources de données, consultez les ressources suivantes :

* [Qu’est-ce que Power BI Desktop ?](desktop-what-is-desktop.md)
* [Sources de données dans Power BI Desktop](desktop-data-sources.md)
* [Mettre en forme et combiner des données dans Power BI Desktop](desktop-shape-and-combine-data.md)
* [Se connecter à des classeurs Excel dans Power BI Desktop](desktop-connect-excel.md)   
* [Entrer des données directement dans Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   

