---
title: Générer des rapports exceptionnels à partir d’un classeur Excel dans le service Power BI
description: Cet article explique comment créer rapidement un rapport exceptionnel à partir d’un classeur Excel.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/12/2019
ms.author: maggies
LocalizationGroup: Data from files
ms.openlocfilehash: c2a4719a03e37569e40d4247939a9f2c73379e52
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73872512"
---
# <a name="from-excel-workbook-to-stunning-report-in-the-power-bi-service"></a>Générer des rapports exceptionnels à partir d’un classeur Excel dans le service Power BI
Votre responsable attend de vous un rapport présentant vos chiffres de vente les plus récents et vos dernières impressions concernant la campagne avant la fin de la journée. Vos données les plus récentes sont stockées sur différents systèmes tiers et sur des fichiers de votre ordinateur portable. Auparavant, plusieurs heures étaient nécessaires pour créer des visuels et mettre en forme un rapport. Vous êtes donc inquiet.

Tout va bien de passer. Avec Power BI, vous pouvez créer un rapport de superbe qualité sans délai.

Dans cet exemple, nous allons charger un fichier Excel à partir d’un système local, créer un rapport et le partager avec vos collègues, tout cela dans Power BI.

## <a name="prepare-your-data"></a>Préparez vos données
Prenons un simple fichier Excel comme exemple. 

1. Avant de charger votre fichier Excel dans Power BI, vous devez organiser vos données dans un « tableau plat ». Dans une table plate, chaque colonne contient le même type de données, par exemple, du texte, des dates, des chiffres ou des devises. Votre table doit comprendre une ligne d’en-tête, mais pas de colonnes ni de lignes qui affichent des totaux.

   ![Données organisées dans Excel](media/service-from-excel-to-stunning-report/pbi_excel_file.png)

2. Mettez ensuite en forme vos données sous forme de tableau : Dans Excel, sous l’onglet **Accueil**, dans le groupe **Styles**, sélectionnez **Mettre sous forme de tableau**. 

3. Sélectionnez un style de tableau à appliquer à votre feuille de calcul. 

   Votre feuille de calcul Excel peut maintenant être chargée dans Power BI.

   ![Données sous forme de table](media/service-from-excel-to-stunning-report/pbi_excel_table.png)

## <a name="upload-your-excel-file-to-the-power-bi-service"></a>Charger un fichier Excel dans le service Power BI
Le service Power BI se connecte à de nombreuses sources de données, y compris des fichiers Excel stockés sur votre ordinateur. 

 > [!NOTE] 
 > Pour suivre le reste de ce tutoriel, utilisez le [classeur Financial Sample](sample-financial-download.md).

1. Pour commencer, connectez-vous au service Power BI. Si vous n’êtes pas encore inscrit, [vous pouvez le faire gratuitement](https://powerbi.com).

2. Vous voulez créer un tableau de bord. Ouvrez **Mon espace de travail**, puis sélectionnez l’icône **Créer**.

   ![icône Créer](media/service-from-excel-to-stunning-report/power-bi-new-dash.png)

3. Sélectionnez **Tableau de bord**, entrez un nom, puis sélectionnez **Créer**. 

   Le nouveau tableau de bord s’affiche, sans données.

   ![Liste déroulante Créer](media/service-from-excel-to-stunning-report/power-bi-create-dash.png)

4. Sélectionnez **Obtenir des données** en bas du volet de navigation. 

5. Dans la page **Obtenir des données**, dans la zone **Fichiers** située sous **Créer du contenu**, sélectionnez **Récupérer**.

   ![Obtenir des données de fichiers](media/service-from-excel-to-stunning-report/pbi_get_files.png)

6. Dans la page **Fichiers**, sélectionnez **Fichier local**. Accédez au classeur Excel sur votre ordinateur, puis sélectionnez **Ouvrir** pour le charger dans le service Power BI. 

   ![fenêtre Obtenir les données > Fichiers](media/service-from-excel-to-stunning-report/pbi_local_file.png)

7. Dans la page **Fichier local**, sélectionnez **Importer**.


## <a name="build-your-report"></a>Créez votre rapport
Une fois que Power BI a importé le fichier Excel, vous pouvez commencer à créer votre rapport. 

1. Lorsque le message **Votre jeu de données est prêt** s’affiche, sélectionnez **Afficher le jeu de données**.  

   Power BI s’ouvre en mode Édition et affiche le canevas de rapport. À droite figurent les volets **Visualisations**, **Filtres** et **Champs**. Notez que les données du tableau de votre classeur Excel s’affichent dans le volet **Champs**. Sous le nom du tableau, Power BI répertorie les en-têtes de colonne en tant que champs individuels.

   ![Représentation des données Excel dans le volet Champs](media/service-from-excel-to-stunning-report/pbi_report_fields.png)

2. Vous pouvez maintenant commencer à créer des visualisations. Supposons que votre responsable veuille voir l’historique des bénéfices. Dans le volet **Champs**, faites glisser **Bénéfices** dans le canevas du rapport. 

   Par défaut, Power BI affiche un graphique à barres. 

3. Faites glisser **Date** dans le canevas du rapport. 

   Power BI met à jour le graphique à barres pour afficher les bénéfices par date.

   ![Histogramme dans l’éditeur de rapport](media/service-from-excel-to-stunning-report/pbi_report_pin-new.png)

   > [!TIP]
   > Si votre graphique ne ressemble pas à celui attendu, vérifiez vos agrégations. Par exemple, dans la zone **Valeur**, cliquez avec le bouton droit sur le champ que vous venez d’ajouter pour vérifier que les données sont agrégées comme vous le souhaitez. Dans notre exemple, nous utilisons **Somme**.
   > 

Votre responsable veut savoir quels pays sont les plus rentables. Imprimez-lui une visualisation de type Carte. 

1. Sélectionnez une zone vide dans le canevas de rapport. 

2. Dans le volet **Champs**, faites glisser les champs **Pays** et **Bénéfices** dans le canevas de rapport.

   Power BI crée un élément visuel de type Carte dont les bulles représentent les bénéfices relatifs de chaque emplacement.

   ![Visuel Carte dans l’éditeur de rapport](media/service-from-excel-to-stunning-report/pbi_report_map-new.png)

Vous voulez afficher un élément visuel montrant les ventes par produit et segment ? C’est facile. 

1. Dans le volet **Champs**, sélectionnez les champs **Vente**, **Bénéfices** et **Segment**. 
   
   Power BI crée immédiatement un graphique à barres. 

2. Modifiez le type de graphique en choisissant une icône du menu **Visualisations**. Par exemple, remplacez-le par un **histogramme empilé**. 

3. Pour trier le graphique, sélectionnez **Plus d’options** (...) > **Trier par**.

   ![Histogramme empilé dans l’éditeur de rapport](media/service-from-excel-to-stunning-report/pbi_barchart-new.png)

Épinglez tous vos visuels à votre tableau de bord. Vous êtes maintenant prêt à le partager avec vos collègues.

   ![Tableau de bord avec trois visuels épinglés](media/service-from-excel-to-stunning-report/pbi_report.png)

## <a name="share-your-dashboard"></a>Partagez votre tableau de bord
Supposons que vous vouliez partager votre tableau de bord avec votre responsable. Vous pouvez partager votre tableau de bord et le rapport sous-jacent avec vos collègues disposant d’un compte Power BI. Ceux-ci peuvent interagir avec votre rapport, mais ne peuvent pas enregistrer de modifications.

1. Pour partager votre rapport, en haut du tableau de bord, sélectionnez **Partager**.

   ![Icône de partage](media/service-from-excel-to-stunning-report/power-bi-share.png)

   Power BI affiche la page **Partager le tableau** de bord. 

2. Entrez les adresses e-mail des destinataires dans la zone **Entrer les adresses de messagerie**, puis ajoutez un message dans la zone située en dessous. 

3. Pour autoriser les destinataires à partager votre tableau de bord avec d’autres personnes, sélectionnez l’option **Autoriser les destinataires à partager votre tableau de bord**. Sélectionnez **Partager**.

   ![fenêtre Partager le tableau de bord](media/service-from-excel-to-stunning-report/power-bi-share-dash-new.png)

## <a name="next-steps"></a>Étapes suivantes

* [Prise en main du service Power BI](service-get-started.md)
* [Prise en main de Power BI Desktop](desktop-getting-started.md)
* [Fondamentaux pour les concepteurs dans le service Power BI](service-basic-concepts.md)

D’autres questions ? [Posez vos questions à la Communauté Power BI](https://community.powerbi.com/).

