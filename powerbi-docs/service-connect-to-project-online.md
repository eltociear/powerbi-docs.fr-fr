---
title: Se connecter à Project Online avec Power BI
description: Project Online pour Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 07/25/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 0978e87167f96b40082819764d7e3ae35e930a4b
ms.sourcegitcommit: a77977a43342db4399a4dffb862b96907d16de35
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2019
ms.locfileid: "69023783"
---
# <a name="connect-to-project-web-app-with-power-bi"></a>Se connecter à Project Web App avec Power BI
Microsoft Project Web App est une solution en ligne flexible pour la gestion de portefeuilles de projets et les tâches quotidiennes. Project Web App permet aux organisations de prendre en main et de hiérarchiser les investissements de portefeuilles de projets ainsi que de produire la valeur commerciale souhaitée. L’application modèle Project Web App pour Power BI vous permet d’exploiter les insights de Project Web App pour mieux gérer les projets, les portefeuilles et les ressources.

Connectez-vous à l’[application modèle Project Web App](https://appsource.microsoft.com/product/power-bi/pbi_msprojectonline.pbi-microsoftprojectwebapp) pour Power BI.

## <a name="how-to-connect"></a>Comment se connecter

1. Sélectionnez **Applications** dans le volet de navigation de gauche, puis **Obtenir des applications** en haut à droite.

    ![Obtenir des applications](media/service-connect-to-project-online/GetApps.png)

2. Dans la zone **Services**, sélectionnez **Obtenir**.
   
   ![AppSource](media/service-connect-to-project-online/AppSource.png)
3. Dans AppSource, sélectionnez l’onglet **Applications**, puis recherchez/sélectionnez **Microsoft Project Web App**.
   
4. Vous recevrez un message indiquant **Installer cette application Power BI ?** . Sélectionnez **Installer**. 

   ![Installer Project Web App](media/service-connect-to-project-online/ProjectTile.png)
5. Dans le volet **Applications**, sélectionnez la vignette **Microsoft Project Web App**. 
   
   ![Application web Microsoft Project](media/service-connect-to-project-online/getstarted.png)
6. Dans **Démarrer avec votre nouvelle application**, sélectionnez **Connecter des données**.
   
   ![Se connecter aux données](media/service-connect-to-project-online/mproject.png)
7. Dans la zone de texte **URL Project Web App**, entrez l’URL de l’application PWA (Project Web App) à laquelle vous souhaitez vous connecter.  Notez que cela peut différer de l’exemple si vous avez un domaine personnalisé. Dans la zone de texte **Langue du site PWA**, tapez le numéro qui correspond à la langue de votre site PWA. Tapez le chiffre « 1 » pour l’anglais, « 2 » pour le Français, « 3 » pour l’allemand, « 4 » pour le portugais (Brésil), « 5 » pour le portugais (Portugal) et « 6 » pour l’espagnol. 
   
   ![Se connecter à Microsoft Project Online](media/service-connect-to-project-online/params.png)
8. Pour la méthode d’authentification, sélectionnez **oAuth2** \> **Se connecter**. Quand vous y êtes invité, entrez vos informations d’identification Project Web App et suivez le processus d’authentification.

    > [!NOTE]
    > Vous devez disposer d’autorisations d’Examinateur de portefeuilles, de Responsable de portefeuilles ou d’Administrateur pour l’instance Project Web App à laquelle vous vous connectez.

9. Une notification indiquant que vos données sont en cours de chargement s’affiche. Selon la taille de votre compte, cela peut prendre un certain temps. Une fois les données importées dans Power BI, le contenu de votre nouvel espace de travail s’affiche. Vous devrez peut-être actualiser le jeu de données pour récupérer les dernières mises à jour. 

    Une fois les données importées dans Power BI, le rapport de 13 pages et le jeu de données apparaissent dans le volet de navigation de gauche. 

10. Une fois que vos rapports sont prêts, vous pouvez commencer à explorer vos données Project Web App. L’application modèle intègre 13 rapports riches et détaillés : 6 pages de rapport pour la vue d’ensemble du portefeuille, 5 pages de rapport pour la vue d’ensemble des ressources et 2 pages de rapport pour l’état du projet. 

    ![Tableau de bord Portefeuille](media/service-connect-to-project-online/report1.png)
   
    ![Disponibilité](media/service-connect-to-project-online/report3.png)
   
    ![État du projet](media/service-connect-to-project-online/report2.png)

**Et maintenant ?**

* Même si une actualisation quotidienne de votre jeu de données est planifiée, vous pouvez changer la planification de l’actualisation ou essayer d’actualiser le jeu de données à la demande à l’aide de l’option **Actualiser maintenant**.

**Développer l’application modèle**

Téléchargez le [fichier PBIT GitHub](https://github.com/OfficeDev/Project-Power-BI-Content-Packs) pour personnaliser et mettre à jour le pack de contenu.

## <a name="next-steps"></a>Étapes suivantes
[Prise en main de Power BI](service-get-started.md)

[Obtenir des données dans Power BI](service-get-data.md)

