---
title: "Partager des rapports Power BI avec des collègues"
description: "Découvrez comment partager des rapports Power BI, et des rapports filtrés, avec des collègues de votre organisation."
services: powerbi
documentationcenter: 
author: maggiesMSFT
manager: kfile
backup: ajayan
editor: 
tags: 
featuredvideoid: 0tUwn8DHo3s
qualityfocus: complete
qualitydate: 06/22/2016
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 11/14/2017
ms.author: maggies
ms.openlocfilehash: 022f085d12d7dc872052ca9205deca264b1c0418
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2017
---
# <a name="share-power-bi-reports-with-your-coworkers"></a>Partager des rapports Power BI avec vos collègues
Le *partage* est une façon d’autoriser quelques utilisateurs à accéder à vos tableaux de bord et rapports. Power BI offre [plusieurs façons de collaborer et de distribuer vos rapports](service-how-to-collaborate-distribute-dashboards-reports.md). Le partage en est une.

Avec le partage, vous et vos destinataires avez besoin d’une [licence Power BI Pro](service-free-vs-pro.md) ou le contenu doit être dans une [capacité Premium](service-premium.md). Vous avez des suggestions ? L’équipe Power BI est toujours intéressée par vos commentaires. Pour cela, accédez au [site de la communauté Power BI](https://community.powerbi.com/).

Vous pouvez partager un rapport avec des collègues du même domaine de messagerie que vous, à partir de votre espace de travail personnel ou d’un espace de travail d’application. Quand vous partagez un rapport, les utilisateurs avec qui vous le partagez peuvent l’afficher et interagir avec lui, mais ils ne peuvent pas le modifier. Ils voient les mêmes données que vous dans le rapport, sauf si la [sécurité au niveau des lignes](service-admin-rls.md) est appliquée. 

## <a name="share-a-power-bi-report"></a>Partager un rapport Power BI
1. Dans le service Power BI, [créez un tableau de bord](service-dashboard-create.md) contenant au moins une vignette établissant un lien vers le rapport que vous souhaitez partager. 
   
    Même si vous souhaitez uniquement partager le rapport, vous devez commencer par créer un tableau de bord établissant un lien vers le rapport, puis le partager. 

1. Dans l’angle supérieur droit du tableau de bord, sélectionnez **Partager**.

     ![Sélectionner Partager](media/service-share-reports/power-bi-share-upper-right.png)
  
2. Adressez-le aux destinataires souhaités. Si vous ne souhaitez pas leur envoyer d’e-mail concernant le tableau de bord, désactivez la case à cocher **Envoyer une notification par e-mail aux destinataires**.

     ![Désactiver la case à cocher Envoyer une notification par e-mail](media/service-share-reports/power-bi-share-dont-send-mail.png)

4. Sélectionnez **Partager**.

      Les personnes avec qui vous partagez le tableau de bord sont maintenant autorisées à afficher le rapport sous-jacent. 

1. Ouvrez le rapport dans le service Power BI, copiez l’URL de la page de rapport et envoyez-la à vos collègues. 
   
    Lorsque ceux-ci cliquent sur le lien, Power BI ouvre une version en lecture seule du rapport.

## <a name="share-a-filtered-version-of-a-report"></a>Partager une version filtrée d’un rapport
Est-il possible de partager une version filtrée d’un rapport ? Par exemple un rapport qui affiche uniquement les données relatives à une ville, un fournisseur ou un commercial spécifique. Pour ce faire, créez une URL personnalisée.

1. Ouvrez le rapport en [mode Édition](service-reading-view-and-editing-view.md), appliquez le filtre et enregistrez le rapport.
   
   Dans cet exemple, nous filtrons l’[exemple Analyse de la vente au détail](sample-tutorial-connect-to-the-samples.md) pour afficher uniquement les valeurs où **Territory (Territoire)** est égale à **NC**.
   
   ![Volet Filtre du rapport](media/service-share-reports/power-bi-filter-report2.png)
2. Ajoutez le code suivant à la fin de l’URL de page de rapport :
   
   ?filter=*tablename*/*fieldname* eq *value*
   
    Le champ doit être de type **chaîne** et ni *fieldname* ni *tablename* ne peuvent contenir d’espaces.
   
   Dans notre exemple, le nom de la table est **Store**, le nom du champ est **Territory** et la valeur que nous voulons filtrer est **NC** :
   
    ?filter=Store/Territory eq NC
   
   ![URL de rapport filtré](media/service-share-reports/power-bi-filter-url3.png)
   
   Comme votre navigateur ajoute des caractères spéciaux pour représenter les barres obliques et les espaces, vous obtenez le résultat suivant :
   
   app.powerbi.com/groups/me/reports/010ae9ad-a9ab-4904-a7a1-10a61f70f2f5/ReportSection2?filter=Store%252FTerritory%20eq%20NC
3. Envoyez cette URL à vos collègues. 
   
   Lorsque ceux-ci cliquent sur le lien, Power BI ouvre une version en lecture seule du rapport filtré.

## <a name="next-steps"></a>Étapes suivantes
* Vous voulez donner votre avis ? Accédez au [site de la communauté Power BI](https://community.powerbi.com/) pour effectuer des suggestions.
* [Comment partager des tableaux de bord, rapports et vignettes ?](service-how-to-collaborate-distribute-dashboards-reports.md)
* [Partager un tableau de bord](service-share-dashboards.md)
* D’autres questions ? [Posez vos questions à la Communauté Power BI](http://community.powerbi.com/).

