---
title: Se connecter à une page web à partir de Power BI Desktop
description: Connectez-vous facilement à une page web et utiliser les données de cette page dans Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: f2e61617e060d90a30aebd1ddc47a72b712c271c
ms.sourcegitcommit: 029aacd09061a8aa45b57f05d0dc95c93dd16a74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2020
ms.locfileid: "94559852"
---
# <a name="connect-to-webpages-from-power-bi-desktop"></a>Se connecter à des pages web à partir de Power BI Desktop

Vous pouvez vous connecter à une page web et importer ses données dans Power BI Desktop pour les utiliser ensuite dans vos visuels et vos modèles de données.

Dans Power BI Desktop, sélectionnez **Obtenir des données > Web** dans le ruban **Accueil**.

![Capture d’écran de Power BI Desktop, montrant la sélection de l’option Web.](media/desktop-connect-to-web/connect-to-web-01.png)

Une boîte de dialogue s’affiche vous demandant l’URL de la page web à partir de laquelle vous souhaitez importer les données.

![Capture d’écran de la boîte de dialogue Web, montrant le champ URL.](media/desktop-connect-to-web/connect-to-web-02.png)

Une fois que vous avez tapé ou collé l’URL, sélectionnez **OK**. Power BI Desktop vous invite à spécifier la façon dont vous souhaitez accéder au contenu web.

![Informations d’identification à utiliser lors de la connexion au web](media/desktop-connect-to-web/connect-to-web-03.png)

Power BI Desktop se connecte à la page web, puis présente les données disponibles dans cette page dans la fenêtre **Navigateur**. Lorsque vous sélectionnez un des éléments de données disponibles, comme une table de la page entière, la fenêtre **Navigateur** affiche un aperçu de ces données sur le côté droit de la fenêtre.

![Capture d’écran de la boîte de dialogue Navigateur, montrant un aperçu des données de la table sélectionnée.](media/desktop-connect-to-web/connect-to-web-04.png)

Vous pouvez utiliser le bouton **Transformer les données**, qui lance l’**Éditeur de requête**, dans lequel vous pouvez mettre en forme et transformer les données de cette page web avant de les importer dans Power BI Desktop. Vous pouvez également cliquer sur le bouton **Charger** et importer tous les éléments de données que vous avez sélectionnés dans le volet de gauche.

Lorsque vous sélectionnez **Charger**, Power BI Desktop importe les éléments sélectionnés et les place dans le volet **Champs**, à droite de la vue Rapports dans Power BI Desktop.

![Capture d’écran du volet Champs, montrant la liste des tables sélectionnées.](media/desktop-connect-to-web/connect-to-web-05.png)

Voilà comment se connecter à une page web et importer les données qu’elle contient dans Power BI Desktop.

À partir de là, vous pouvez faire glisser ces champs sur le canevas de rapport et créer toutes les visualisations que vous voulez. Vous pouvez également utiliser les données de cette page web comme vous le feriez pour d’autres données : vous pouvez les mettre en forme, vous pouvez créer des relations entre elles et d’autres sources de données de votre modèle et faire aussi ce dont vous avez besoin pour créer le rapport Power BI souhaité.

Pour voir plus d’informations sur la connexion à une page web et voir ce processus en action, consultez le [Guide de prise en main de Power BI Desktop](../fundamentals/desktop-getting-started.md).

## <a name="certificate-revocation-check"></a>Vérification de la révocation de certificat

Power BI applique la sécurité aux connexions web pour protéger vos données. Dans certains scénarios, notamment la capture de demandes web avec Fiddler, les connexions web peuvent ne pas fonctionner correctement. Pour activer de tels scénarios, vous pouvez désactiver l’option **Activer la vérification de la révocation des certificats** dans Power BI Desktop, puis redémarrer Power BI Desktop. 

Pour modifier cette option, sélectionnez **Fichier > Options**, puis sélectionnez **Sécurité** dans le volet gauche. L’illustration suivante montre la case à cocher. Si vous décochez la case, les connexions web seront moins sécurisées. 

![Activer ou désactiver la vérification de la révocation des certificats](media/desktop-connect-to-web/connect-to-web-06.png)


## <a name="next-steps"></a>Étapes suivantes
Vous pouvez connecter toutes sortes de données à l’aide de Power BI Desktop. Pour plus d’informations sur les sources de données, consultez les ressources suivantes :

* [Sources de données dans Power BI Desktop](desktop-data-sources.md)
* [Mettre en forme et combiner des données dans Power BI Desktop](desktop-shape-and-combine-data.md)
* [Se connecter à des classeurs Excel dans Power BI Desktop](desktop-connect-excel.md)   
* [Se connecter à des fichiers CSV dans Power BI Desktop](desktop-connect-csv.md)   
* [Entrer des données directement dans Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   
