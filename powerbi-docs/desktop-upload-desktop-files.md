---
title: Publier à partir de Power BI Desktop
description: Publier à partir de Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/15/2020
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 3a67c36b2594696e1c576693cc5808eb0227c1c7
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "76709600"
---
# <a name="publish-datasets-and-reports-from-power-bi-desktop"></a>Publier des jeux de données et des rapports à partir de Power BI Desktop
Quand vous publiez un fichier Power BI Desktop dans le service Power BI, vous publiez les données du modèle dans votre espace de travail Power BI. Il en va de même pour tous les rapports que vous avez créés dans la vue**Rapport**. Un nouveau jeu de données du même nom et tous les rapports seront visibles dans le navigateur de votre espace de travail.

La publication à partir de Power BI Desktop a le même effet que l’utilisation de l’option **Obtenir des données** dans Power BI pour se connecter à un fichier Power BI Desktop et le charger.

> [!NOTE]
> Tous les changements que vous apportez au rapport dans Power BI ne seront pas enregistrés dans le fichier Power BI Desktop d’origine. Cela inclut l’ajout, la suppression ou le changement des visualisations dans les rapports.
> 
> 

## <a name="to-publish-a-power-bi-desktop-dataset-and-reports"></a>Pour publier un jeu de données et des rapports Power BI Desktop
1. Dans Power BI Desktop, choisissez **Fichier** \> **Publier** \> **Publier sur Power BI** ou sélectionnez **Publier** dans le ruban.  

   ![Bouton Publier](media/desktop-upload-desktop-files/pbid_publish_publishbutton.png)

2. Connectez-vous à Power BI.
3. Sélectionnez la destination.

   ![Sélectionner la destination de la publication](media/desktop-upload-desktop-files/pbid_publish_select_destination.png)

Une fois la publication terminée, vous recevez un lien vers votre rapport. Sélectionnez ce lien pour ouvrir le rapport dans votre site Power BI.

![Boîte de dialogue de réussite de la publication](media/desktop-upload-desktop-files/pbid_publish_success.png)

## <a name="republish-or-replace-a-dataset-published-from-power-bi-desktop"></a>Republier ou remplacer un jeu de données publié à partir de Power BI Desktop
Le jeu de données et tous les rapports que vous avez créés dans Power BI Desktop sont chargés sur votre site Power BI quand vous publiez un fichier Power BI Desktop. Quand vous republiez votre fichier Power BI Desktop, le jeu de données de votre site Power BI est remplacé par le jeu de données mis à jour à partir du fichier Power BI Desktop.

Ce processus est assez simple, mais vous devez savoir un certain nombre de choses :

* Si plusieurs jeux de données dans Power BI portent le même nom que le fichier Power BI Desktop, la publication peut échouer. Veillez à ce que chaque jeu de données dans Power BI porte un nom unique. Vous pouvez également renommer le fichier et le publier, créant ainsi un jeu de données du même nom que le fichier.
* Si vous renommez ou supprimez une colonne ou une mesure, les visualisations que vous avez déjà dans Power BI avec ce champ peuvent être rompues. 
* Power BI ignore certaines modifications de format des colonnes existantes, par exemple, si vous faites passer le format d’une colonne de 0,25 % à 25 %.
* Supposons que vous avez une planification d’actualisation configurée pour votre jeu de données existant dans Power BI. Quand vous ajoutez de nouvelles sources de données à votre fichier et que vous effectuez une republication, vous devez vous connecter à ces sources avant la prochaine actualisation planifiée.
* Quand vous republiez un jeu de données publié à partir de Power BI Desktop et que vous avez défini une planification d’actualisation, une actualisation du jeu de données est démarrée dès que vous effectuez la republication. 

