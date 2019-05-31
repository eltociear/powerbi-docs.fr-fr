---
title: Filtrer un rapport et le partager avec vos collègues - Power BI
description: Découvrez comment filtrer un rapport Power BI et le partager avec les collègues de votre organisation.
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
featuredvideoid: 0tUwn8DHo3s
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/24/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 5f3808884e63521ec1dd775d876f1cf707bbe56b
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "64770677"
---
# <a name="filter-a-power-bi-report-and-share-it-with-coworkers"></a>Filtrer un rapport Power BI et le partager avec vos collègues
Le *partage* est une façon d’autoriser quelques utilisateurs à accéder à vos tableaux de bord et rapports. Est-il possible de partager une version filtrée d’un rapport ? Par exemple un rapport qui affiche uniquement les données relatives à une ville, un fournisseur ou un commercial spécifique. Essayez de filtrage d’un rapport et partager ou de la création d’une URL personnalisée. Le rapport est filtré quand les destinataires l’ouvrent pour la première fois. Ils peuvent supprimer le filtre en modifiant l’URL. 

Power BI propose également [d’autres façons de collaborer et de distribuer des rapports](service-how-to-collaborate-distribute-dashboards-reports.md). Avec le partage, vous et vos destinataires avez besoin d’une [licence Power BI Pro](service-features-license-type.md) ou le contenu doit être dans une [capacité Premium](service-premium-what-is.md). 

## <a name="two-ways-to-filter-a-report"></a>Deux façons de filtrer un rapport

### <a name="set-a-filter"></a>Définir un filtre

Ouvrez le rapport en [mode Édition](consumer/end-user-reading-view.md), appliquez le filtre et enregistrez le rapport.
   
Dans cet exemple, nous filtrons l’[exemple Retail Analysis](sample-tutorial-connect-to-the-samples.md) (Analyse de la vente au détail) pour présenter uniquement les valeurs où **Territory** correspond à **NC**.
   
![Volet Filtre du rapport](media/service-share-reports/power-bi-filter-report2.png)

### <a name="create-a-filter-in-the-url"></a>Créer un filtre dans l’URL

Ajoutez le code suivant à la fin de l’URL de page de rapport :
   
?filter=*tablename*/*fieldname* eq *value*
   
Le champ doit être de type nombre, date/heure ou chaîne. Les valeurs *tablename* ou *fieldname* ne peuvent pas contenir d’espaces.
   
Dans notre exemple, le nom de la table est **Store**, le nom du champ est **Territory** et la valeur que nous voulons filtrer est **NC** :
   
?filter=Store/Territory eq 'NC'
   
![URL de rapport filtré](media/service-share-reports/power-bi-filter-url3.png)
   
Comme votre navigateur ajoute des caractères spéciaux pour représenter les barres obliques, les espaces et les apostrophes, vous obtenez le résultat suivant :
   
app.powerbi.com/groups/me/reports/010ae9ad-a9ab-4904-a7a1-xxxxxxxxxxxx/ReportSection2?filter=Store%252FTerritory%20eq%20%27NC%27

Consultez l’article [filtrer un rapport à l’aide des paramètres de chaîne de requête dans l’URL](service-url-filters.md) pour beaucoup plus de détails.

## <a name="share-the-filtered-report"></a>Partager le rapport filtré

1. Lorsque vous [partager le rapport](service-share-dashboards.md), désactivez le **envoyer une notification aux destinataires de courrier électronique** case à cocher.

    ![Boîte de dialogue Partager le rapport](media/service-share-reports/power-bi-share-report-dialog.png)

4. Envoyez le lien du filtre que vous avez créé.

## <a name="next-steps"></a>Étapes suivantes
* Vous voulez donner votre avis ? Accédez au [site de la communauté Power BI](https://community.powerbi.com/) pour effectuer des suggestions.
* [Comment partager des tableaux de bord, rapports et vignettes ?](service-how-to-collaborate-distribute-dashboards-reports.md)
* [Partager un tableau de bord](service-share-dashboards.md)
* D’autres questions ? [Posez vos questions à la Communauté Power BI](http://community.powerbi.com/).

