---
title: Comment configurer une actualisation planifiée de rapport Power BI
description: Pour actualiser les données dans votre rapport Power BI, vous devez créer un plan d’actualisation planifiée.
author: davidiseminger
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: how-to
ms.date: 06/10/2020
ms.author: davidi
ms.openlocfilehash: 7bc3b77a8badafe1c9660af347a74214176690ac
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90859034"
---
# <a name="how-to-configure-power-bi-report-scheduled-refresh"></a>Comment configurer une actualisation planifiée de rapport Power BI
Pour actualiser les données de votre rapport Power BI dans Power BI Report Server, vous devez créer un plan d’actualisation planifiée. Vous créez ce plan dans la zone *Gérer* d’un rapport Power BI sur le serveur de rapports.

![Actualisation planifiée réussie d’un rapport Power BI](media/configure-scheduled-refresh/scheduled-refresh-success.png)

## <a name="configure-data-source-credentials"></a>Configurer les informations d’identification de la source de données
Vous devez disposer des autorisations nécessaires pour créer un plan d’actualisation planifiée. Les autorisations sont définies dans les définitions de rôles du serveur de rapports. Pour plus d’informations, consultez [Définitions de rôles - Rôles prédéfinis](/sql/reporting-services/security/role-definitions-predefined-roles) dans la documentation de SQL Server Reporting Services.

Avant de créer un plan d’actualisation des données planifiée, vous devez définir les informations d’identification pour **chaque source de données** utilisée dans votre rapport Power BI.

1. Dans le portail web, cliquez avec le bouton droit sur le rapport Power BI, puis sélectionnez **Gérer**.
   
    ![Sélectionner Gérer dans le menu contextuel du rapport Power BI](media/configure-scheduled-refresh/manage-power-bi-report.png)
2. Dans le menu de gauche, sélectionnez l’onglet **Sources de données**.
3. Pour chaque source de données qui s’affiche, choisissez le type d’authentification à utiliser lors de la connexion à cette source de données. Entrez les informations d’identification appropriées.
   
    ![Informations d’identification de source de données dans l’écran de rapport Gérer](media/configure-scheduled-refresh/data-source-credentials.png)

## <a name="creating-a-schedule-refresh-plan"></a>Création d’un plan d’actualisation planifiée
Pour créer un plan d’actualisation planifiée, procédez comme suit.

1. Dans le portail web, cliquez avec le bouton droit sur le rapport Power BI, puis sélectionnez **Gérer**.
   
    ![Sélectionner Gérer dans le menu contextuel du rapport Power BI](media/configure-scheduled-refresh/manage-power-bi-report.png)
2. Dans le menu de gauche, sélectionnez l’onglet **Actualisation planifiée**.
3. Dans la page **Actualisation planifiée**, sélectionnez **Nouveau plan d’actualisation planifiée**.
   
    ![Nouveau plan d’actualisation planifiée](media/configure-scheduled-refresh/new-scheduled-refresh-plan.png)
4. Dans la page **Nouveau plan d’actualisation planifiée**, entrez une description et définissez une planification du moment où vous souhaitez que votre modèle de données soit actualisé.
5. Lorsque vous avez terminé, sélectionnez **Créer le plan d’actualisation planifiée**.
   
    ![Créer le plan d’actualisation planifiée](media/configure-scheduled-refresh/create-scheduled-refresh-plan.png)

## <a name="modifying-a-schedule-refresh-plan"></a>Modification d’un plan d’actualisation planifiée
La modification d’un plan d’actualisation planifiée est similaire à sa création.

1. Dans le portail web, cliquez avec le bouton droit sur le rapport Power BI, puis sélectionnez **Gérer**.
   
    ![Sélectionner Gérer dans le menu contextuel du rapport Power BI](media/configure-scheduled-refresh/manage-power-bi-report.png)
2. Dans le menu de gauche, sélectionnez l’onglet **Actualisation planifiée**.
3. Dans la page **Actualisation planifiée**, sélectionnez **Modifier** en regard du plan d’actualisation que vous souhaitez gérer.
   
    ![Sélectionner Modifier en regard du plan que vous souhaitez modifier](media/configure-scheduled-refresh/edit-scheduled-refresh-plan.png)
4. Dans la page **Modifier un plan d’actualisation planifiée**, entrez une description et définissez une planification du moment où vous souhaitez que votre modèle de données soit actualisé.
5. Lorsque vous avez terminé, sélectionnez **Appliquer**.
   
    ![La page Modifier le plan actualisation planifiée est similaire à l’écran de création](media/configure-scheduled-refresh/edit-scheduled-refresh-plan-page.png)

## <a name="viewing-the-status-of-schedule-refresh-plan"></a>Affichage de l’état d’un plan d’actualisation planifiée
Affichez l’état d’un plan d’actualisation planifiée dans le portail web.

1. Dans le portail web, cliquez avec le bouton droit sur le rapport Power BI, puis sélectionnez **Gérer**.
   
    ![Sélectionner Gérer dans le menu contextuel du rapport Power BI](media/configure-scheduled-refresh/manage-power-bi-report.png)
2. Dans le menu de gauche, sélectionnez l’onglet **Actualisation planifiée**.
3. Dans la page **Actualisation planifiée**, la colonne la plus à droite affiche l’état d’un plan.
   
   | **État** | **Description** |
   | --- | --- |
   | Nouveau plan d’actualisation planifiée |Le plan a été créé mais pas été exécuté. |
   | Actualisation |Le processus d’actualisation a démarré. |
   | Modèle de diffusion en continu vers Analysis Server |Copie du modèle à partir de la base de données du catalogue du serveur de rapports vers l’instance Analysis Services hébergée. |
   | Actualisation des données |Actualisation des données dans le modèle. |
   | Suppression des informations d’identification du modèle |Suppression du modèle des informations d’identification utilisées pour se connecter à la source de données. |
   | Enregistrement du modèle dans le catalogue |L’actualisation des données est terminée et le modèle actualisé est réenregistré dans la base de données du catalogue du serveur de rapports. |
   | Terminé : Actualisation des données |L’actualisation est terminée. |
   | Erreur : |Une erreur s’est produite lors de l’actualisation et s’affiche. |

La page web doit être actualisée pour afficher l’état actuel. L’état ne changera pas automatiquement.

## <a name="next-steps"></a>Étapes suivantes
Pour en savoir plus sur la création et la modification de planifications, voir [Créer, modifier et supprimer des planifications](/sql/reporting-services/subscriptions/create-modify-and-delete-schedules).

Pour plus d’informations sur la façon de résoudre les problèmes d’actualisation planifiée, voir [Résoudre les problèmes d’actualisation planifiée dans Power BI Report Server](scheduled-refresh-troubleshoot.md).

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)