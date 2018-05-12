---
title: Publier à partir de Power BI Desktop
description: Publier à partir de Power BI Desktop
services: powerbi
documentationcenter: ''
author: davidiseminger
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: get-started-article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 05/02/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: f70088d4b6b064a72603bc59e6ba1e07cdb5e1b0
ms.sourcegitcommit: f679c05d029ad0765976d530effde744eac23af5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="publish-from-power-bi-desktop"></a>Publier à partir de Power BI Desktop
Lorsque vous publiez un fichier **Power BI Desktop** vers le **service Power BI**, les données du modèle et des rapports que vous avez créés dans la vue **Rapport** sont publiées dans votre espace de travail Power BI. Un nouveau jeu de données du même nom et tous les rapports seront visibles dans le navigateur de votre espace de travail.

La publication à partir de **Power BI Desktop** a le même effet que l’utilisation de l’option **Obtenir des données** dans Power BI pour se connecter à un fichier **Power BI Desktop** et le charger.

> [!NOTE]
> Aucune des modifications que vous apportez au rapport Power BI, comme le fait d’ajouter, de supprimer ou de modifier des visualisations dans les rapports, n’est enregistrée dans le fichier **Power BI Desktop** d’origine.
> 
> 

## <a name="to-publish-a-power-bi-desktop-dataset-and-reports"></a>Pour publier un jeu de données et des rapports Power BI Desktop
1. Dans Power BI Desktop\>**Fichier**\>**Publier**\>**Publier sur Power BI** ou cliquez sur**Publier** dans le ruban.  
   ![](media/desktop-upload-desktop-files/pbid_publish_publishbutton.png)
2. Connectez-vous à Power BI.

Une fois terminé, vous obtiendrez un lien pour ouvrir votre rapport dans votre site Power BI.  
    ![](media/desktop-upload-desktop-files/pbid_publish_success.png)

## <a name="re-publish-or-replace-a-dataset-published-from-power-bi-desktop"></a>Republier ou remplacer un jeu de données publié à partir de Power BI Desktop
Lorsque vous publiez un fichier **Power BI Desktop**, le jeu de données et les rapports que vous avez créés dans **Power BI Desktop** sont chargés sur votre site Power BI. Lorsque vous republiez votre fichier **Power BI Desktop**, le jeu de données de votre site Power BI est remplacé par le jeu de données mis à jour à partir du fichier **Power BI Desktop**.

Tout cela est assez simple, mais il y a quelques éléments à connaître :

* Si vous avez déjà plusieurs jeux de données dans Power BI avec le même nom que le fichier **Power BI Desktop**, la publication peut échouer. Veillez à ce que chaque jeu de données dans Power BI porte un nom unique. Vous pouvez également renommer le fichier et le publier, créant ainsi un jeu de données du même nom que le fichier.
* Si vous renommez ou supprimez une colonne ou une mesure, les visualisations que vous avez déjà dans Power BI avec ce champ peuvent être rompues. 
* Power BI ignore certaines modifications de format des colonnes existantes, par exemple, si vous faites passer le format d’une colonne de 0,25 à 25 %.
* Si vous avez configuré une planification de l’actualisation pour votre jeu de données existant dans Power BI, que vous ajoutez de nouvelles sources de données à votre fichier et que vous le republiez, vous devez vous connecter à ces sources dans *Gérer les sources de données* avant la prochaine actualisation planifiée.

