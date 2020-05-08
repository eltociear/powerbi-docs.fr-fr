---
title: Filtrer et partager un rapport Power BI
description: Découvrez comment filtrer un rapport Power BI et le partager avec les collègues de votre organisation.
author: maggiesMSFT
ms.reviewer: lukaszp
featuredvideoid: 0tUwn8DHo3s
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 01/29/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 16041ebc9ba293ab166178e008b12277d94e89c3
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "76894805"
---
# <a name="filter-and-share-a-power-bi-report"></a>Filtrer et partager un rapport Power BI
Le *partage* est une façon d’autoriser quelques utilisateurs à accéder à vos tableaux de bord et rapports. Est-il possible de partager une version filtrée d’un rapport ? Vous voulez peut-être que le rapport affiche uniquement les données relatives à une ville, un commercial ou une année spécifique. Cet article explique comment filtrer un rapport et partager la version filtrée du rapport. Une autre façon de partager un rapport filtré consiste à [ajouter des paramètres de requête à l’URL du rapport](service-url-filters.md). Dans les deux cas, le rapport est filtré quand les destinataires l’ouvrent pour la première fois. Ils peuvent effacer les sélections de filtre du rapport.

![Rapport filtré](media/service-share-reports/power-bi-share-filter-pane-report.png)

Power BI propose également [d’autres façons de collaborer et de distribuer des rapports](service-how-to-collaborate-distribute-dashboards-reports.md). Avec le partage, vous et vos destinataires avez besoin d’une [licence Power BI Pro](service-features-license-type.md) ou le contenu doit être dans une [capacité Premium](service-premium-what-is.md). 

## <a name="follow-along-with-sample-data"></a>Suivre les étapes avec des exemples de données

Cet article utilise l’exemple d’application modèle Marketing et ventes. Vous voulez l’essayer ? 

1. Installez [l’exemple d’application modèle Marketing et ventes](https://appsource.microsoft.com/product/power-bi/microsoft-retail-analysis-sample.salesandmarketingsample?tab=Overview).
2. Sélectionnez l’application, puis **Explorer l’application**.

   ![Explorer les exemples de données](media/service-share-reports/power-bi-sample-explore-data.png)

3. Sélectionnez l’icône de crayon pour ouvrir l’espace de travail que vous avez installé avec l’application.

    ![Crayon d’édition de l’application](media/service-share-reports/power-bi-edit-pencil-app.png)

4. Dans la liste de contenu de l’espace de travail, sélectionnez **Rapports**, puis sélectionnez le rapport **Exemple PBIX Vente et marketing**.

    ![Ouvrir l’exemple de rapport](media/service-share-reports/power-bi-open-sample-report.png)

    Vous pouvez maintenant passer à la suite.

## <a name="set-a-filter-in-the-report"></a>Définir un filtre dans le rapport

Ouvrez un rapport en [mode Édition](consumer/end-user-reading-view.md) et appliquez un filtre.

Dans cet exemple, nous filtrons la page de catégorie chiffre d’affaires de l’application de modèle d’exemple Marketing et ventes pour afficher uniquement les valeurs où **Région** a la valeur **Central**. 
 
![Volet Filtre du rapport](media/service-share-reports/power-bi-share-report-filter.png)

Enregistrez le rapport.

## <a name="share-the-filtered-report"></a>Partager le rapport filtré

1. Sélectionnez **Partager**.

   ![Sélectionner Partager](media/service-share-reports/power-bi-share.png)

2. Désactivez **Envoyer une notification par courrier aux destinataires** pour pouvoir envoyer un lien filtré à la place. Sélectionnez **Partager le rapport avec les filtres et les segments actifs**, puis **Partager**.

    ![Partager un rapport avec des filtres](media/service-share-reports/power-bi-share-with-filters.png)

4. Sélectionnez à nouveau **Partager**.

   ![Sélectionner Partager](media/service-share-reports/power-bi-share.png)

5. Sélectionnez l’onglet **Accès**, puis **Gérer les affichages Rapport partagé**.

    ![Gérer les affichages Rapport partagé](media/service-share-reports/power-bi-manage-shared-report-views.png)

6. Cliquez avec le bouton droit sur l’URL souhaitée, puis sélectionnez **Copier le lien**.

    ![Copier le lien filtré](media/service-share-reports/power-bi-copy-filtered-link.png)

7. Si vous partagez ce lien, les destinataires verront votre rapport filtré. 


## <a name="next-steps"></a>Étapes suivantes
* [Moyens de partager votre travail dans Power BI](service-how-to-collaborate-distribute-dashboards-reports.md)
* [Partager un tableau de bord](service-share-dashboards.md)
* D’autres questions ? [Posez vos questions à la Communauté Power BI](https://community.powerbi.com/).
* Vous voulez donner votre avis ? Accédez au [site de la communauté Power BI](https://community.powerbi.com/) pour effectuer des suggestions.

