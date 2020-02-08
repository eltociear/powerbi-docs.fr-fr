---
title: 'Tutoriel : Utiliser Analyser dans Excel'
description: Ce tutoriel utilise la page Jeux de données Power BI pour importer des jeux de données dans Excel.
author: tejaskulkarni
ms.reviewer: davidiseminger
ms.service: powerbi
ms.subservice: powerbi-service
ms.custom: connect-to-services
ms.topic: tutorial
ms.date: 01/27/2020
ms.author: tekulkar
LocalizationGroup: Connect to services
ms.openlocfilehash: a68adccec019e64e554d199d23d7dddd782f56a2
ms.sourcegitcommit: 53c2b5ea4ee1fe2659804d5ccc8e4bb445a8bcad
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76921482"
---
# <a name="tutorial-use-analyze-in-excel"></a>Tutoriel : Utiliser Analyser dans Excel

Votre organisation utilise Power BI pour partager l’accès aux données. Utilisez la fonctionnalité Analyser dans Excel pour créer des tableaux croisés dynamiques et des graphiques croisés dynamiques afin d’ajouter du contexte à vos analyses ou de réduire le temps nécessaire pour trouver et importer les jeux de données pertinents.

Pour sélectionner un jeu de données, sélectionnez « Analyser dans Excel ». Vous serez guidé pour créer un tableau croisé dynamique qui utilise les données.  

Vous trouverez d’autres jeux de données partagés par votre organisation en revenant à la page Jeux de données.

Si vous rencontrez des problèmes à une étape, sélectionnez Non à l’étape concernée dans le flux ci-dessous et indiquez vos commentaires dans le formulaire lié.  

Dans ce tutoriel, vous allez découvrir comment :

> [!div class="checklist"]
> * Téléchargez un fichier ODC sur la page Jeux de données Power BI.
> * Activez l’accès à votre jeu de données à partir d’Excel.
> * Commencez à utiliser le jeu de données pour créer des tableaux croisés dynamiques, des graphes et des feuilles de calcul.

## <a name="prerequisites"></a>Prérequis

Pour suivre ce didacticiel, vous avez besoin des éléments suivants :

* un compte Power BI. Si vous n’êtes pas inscrit à Power BI, [inscrivez-vous à un essai gratuit](https://app.powerbi.com/signupredirect?pbi_source=web) avant de commencer.

* Vérifiez que vous comprenez toutes les étapes du tutoriel [Bien démarrer avec le service Power BI](https://docs.microsoft.com/power-bi/service-get-started).

* Vous devez disposer d’un jeu de données Power BI Premium et d’une licence Power BI Pro. Pour plus d’informations, consultez [Qu’est-ce que Power BI Premium ?](https://docs.microsoft.com/power-bi/service-premium-what-is).

* Vous trouverez toute la liste des prérequis dans le document complet [Analyser dans Excel](https://docs.microsoft.com/power-bi/service-analyze-in-excel#requirements).

* Vous devez disposer d’un [abonnement Microsoft Office E5](https://www.microsoft.com/microsoft-365/business/office-365-enterprise-e5-business-software?activetab=pivot%3aoverviewtab) actif.

## <a name="get-started"></a>Commencer

À partir d’Excel, sélectionnez l’option permettant de créer des tableaux croisés dynamiques avec des données partagées Power BI et accédez à la page Jeux de données Power BI.

![Page Jeux de données](media/service-tutorial-analyze-in-excel/tutorial-analyze-in-excel-01.png)

Dans le cadre du flux de travail Analyser dans Excel, plusieurs invites vous guideront ; indiquez si vous avez effectué toutes les étapes de la progression. Si vous rencontrez des problèmes à une étape, sélectionnez **Non** et indiquez vos commentaires sur le formulaire correspondant.

![Instructions du flux de travail](media/service-tutorial-analyze-in-excel/tutorial-analyze-in-excel-02.png)

## <a name="download-and-open-the-odc-file"></a>Télécharger et ouvrir le fichier ODC

Choisissez votre jeu de données dans la liste correspondante et l’espace de travail associé, puis cliquez sur Analyser dans Excel. Power BI crée un fichier ODC et le télécharge du navigateur vers votre ordinateur.

![Sélectionner un jeu de données](media/service-tutorial-analyze-in-excel/tutorial-analyze-in-excel-03.png)

À l’ouverture du fichier dans Excel, une liste de Tableaux croisés dynamiques et de Champs vides s’affiche avec tous les tableaux, les champs et les mesures du jeu de données Power BI. Vous pouvez créer des tableaux croisés dynamiques et des graphiques, et analyser le jeu de données comme vous le feriez pour un jeu de données local dans Excel.

## <a name="enable-data-connections"></a>Activez les connexions de données

Pour analyser des données Power BI dans Excel, il peut vous être demandé d’approuver la connexion. Les administrateurs peuvent désactiver l’utilisation de la fonction Analyser dans Excel avec les jeux de données locaux sur les bases de données Analysis Services sur le Portail d’administration Power BI.

![Activer la connexion](media/service-tutorial-analyze-in-excel/tutorial-analyze-in-excel-04.png)

## <a name="install-updates-and-authenticate"></a>Installer les mises à jour et s’authentifier

Il peut également vous être demandé de vous authentifier avec votre compte Power BI la première fois que vous ouvrez un nouveau fichier ODC.  Si vous rencontrez des problèmes, consultez le document complet [Analyser dans Excel](https://docs.microsoft.com/power-bi/service-analyze-in-excel#sign-in-to-power-bi ) pour plus d’informations ou cliquez sur Non au cours du flux de travail.

![Activer la connexion](media/service-tutorial-analyze-in-excel/tutorial-analyze-in-excel-05.png)

## <a name="analyze-away"></a>Analyser

Comme pour d’autres classeurs locaux, Analyser dans Excel permet de créer des tableaux croisés dynamiques et des graphes, d’ajouter des données et de créer différentes feuilles de calcul avec des vues dans les données. Analyser dans Excel expose toutes les données de niveau de détail à tous les utilisateurs autorisés à accéder au jeu de données. Vous pouvez enregistrer ce classeur, mais vous ne pouvez pas le publier, le réimporter dans Power BI ou le partager avec d’autres utilisateurs de votre organisation. Pour plus d’informations et d’autres cas d’utilisation, consultez [Analyser dans Excel](https://docs.microsoft.com/power-bi/service-analyze-in-excel#analyze-away).

## <a name="clean-up-resources"></a>Nettoyer les ressources

Les interactions avec le service Power BI et la page Jeux de données doivent être limitées au téléchargement du fichier ODC et à la progression dans le flux de travail. Si vous rencontrez des problèmes à une étape, indiquez **Non** à l’étape concernée et indiquez vos commentaires dans le formulaire lié. Le formulaire contient un lien vers des informations supplémentaires sur le problème. Revenez sur la page Jeux de données pour retenter le processus ou sélectionnez un autre jeu de données.

## <a name="next-steps"></a>Étapes suivantes

Les articles suivants pourraient également vous intéresser :

* [Use cross-report drillthrough in Power BI Desktop](https://docs.microsoft.com/power-bi/desktop-cross-report-drill-through) (Utiliser une extraction interrapport dans Power BI Desktop)

* [Utilisation de segments Power BI Desktop](https://docs.microsoft.com/power-bi/visuals/power-bi-visualization-slicers)
