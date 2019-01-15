---
title: Partager un rapport Power BI filtré avec des collègues
description: Découvrez comment filtrer un rapport Power BI et le partager avec les collègues de votre organisation.
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
featuredvideoid: 0tUwn8DHo3s
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 12/21/2018
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 05bdb9ccca7715b74cb18462f215f7d1bf640526
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/15/2019
ms.locfileid: "54279746"
---
# <a name="share-a-filtered-power-bi-report-with-your-coworkers"></a>Partager un rapport Power BI filtré avec des collègues
Le *partage* est une façon d’autoriser quelques utilisateurs à accéder à vos tableaux de bord et rapports. Power BI propose également [d’autres façons de collaborer et de distribuer des rapports](service-how-to-collaborate-distribute-dashboards-reports.md).

Avec le partage, vous et vos destinataires avez besoin d’une [licence Power BI Pro](service-features-license-type.md) ou le contenu doit être dans une [capacité Premium](service-premium.md). 

Vous pouvez partager un rapport avec vos collègues du même domaine de courrier que vous, à différents endroits du service Power BI : Favoris, Récents, Partagés avec moi (si le propriétaire le permet), Mon espace de travail ou d’autres espaces de travail. Quand vous partagez un rapport avec des collègues, ces derniers peuvent le voir et le manipuler, mais ils ne peuvent pas le modifier. Ils voient les mêmes données que vous dans le rapport, sauf si la [sécurité au niveau des lignes](service-admin-rls.md) est appliquée. 

Est-il possible de partager une version filtrée d’un rapport ? Par exemple un rapport qui affiche uniquement les données relatives à une ville, un fournisseur ou un commercial spécifique. Essayez de créer une URL personnalisée. Le rapport est filtré quand les destinataires l’ouvrent pour la première fois. Ils peuvent supprimer le filtre en modifiant l’URL.

## <a name="filter-and-share-a-report"></a>Filtrer et partager un rapport

1. Ouvrez le rapport en [mode Édition](consumer/end-user-reading-view.md), appliquez le filtre et enregistrez le rapport.
   
   Dans cet exemple, nous filtrons l’[exemple Retail Analysis](sample-tutorial-connect-to-the-samples.md) (Analyse de la vente au détail) pour présenter uniquement les valeurs où **Territory** correspond à **NC**.
   
   ![Volet Filtre du rapport](media/service-share-reports/power-bi-filter-report2.png)
2. Ajoutez le code suivant à la fin de l’URL de page de rapport :
   
   ?filter=*tablename*/*fieldname* eq *value*
   
    Le champ doit être de type **chaîne**. Les valeurs *tablename* ou *fieldname* ne peuvent pas contenir d’espaces.
   
   Dans notre exemple, le nom de la table est **Store**, le nom du champ est **Territory** et la valeur que nous voulons filtrer est **NC** :
   
    ?filter=Store/Territory eq 'NC'
   
   ![URL de rapport filtré](media/service-share-reports/power-bi-filter-url3.png)
   
   Comme votre navigateur ajoute des caractères spéciaux pour représenter les barres obliques, les espaces et les apostrophes, vous obtenez le résultat suivant :
   
   app.powerbi.com/groups/me/reports/010ae9ad-a9ab-4904-a7a1-xxxxxxxxxxxx/ReportSection2?filter=Store%252FTerritory%20eq%20%27NC%27

3. [Partagez le rapport](service-share-dashboards.md), mais décochez la case **Envoyer un e-mail de notification aux destinataires**. 

    ![Boîte de dialogue Partager le rapport](media/service-share-reports/power-bi-share-report-dialog.png)

4. Envoyez le lien du filtre que vous avez créé.

## <a name="next-steps"></a>Étapes suivantes
* Vous voulez donner votre avis ? Accédez au [site de la communauté Power BI](https://community.powerbi.com/) pour effectuer des suggestions.
* [Comment partager des tableaux de bord, rapports et vignettes ?](service-how-to-collaborate-distribute-dashboards-reports.md)
* [Partager un tableau de bord](service-share-dashboards.md)
* D’autres questions ? [Posez vos questions à la Communauté Power BI](http://community.powerbi.com/).

