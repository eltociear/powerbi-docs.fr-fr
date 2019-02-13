---
title: 'Exemple Ressources humaines : Visite guidée'
description: 'Exemple Ressources humaines pour Power BI : Visite guidée'
author: maggiesMSFT
manager: kfile
ms.reviewer: amac
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/26/2018
ms.author: maggies
LocalizationGroup: Samples
ms.openlocfilehash: 4b36c02abe0ca0bbd2d117559855a69edff370db
ms.sourcegitcommit: 5e83fa6c93a0bc6599f76cc070fb0e5c1fce0082
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56216651"
---
# <a name="human-resources-sample-for-power-bi-take-a-tour"></a>Exemple Ressources humaines pour Power BI : Visite guidée

## <a name="overview-of-the-human-resources-sample"></a>Présentation de l’exemple Ressources humaines
Les services de ressources humaines utilisent tous le même modèle de présentation de rapports, quels que soient le secteur d’activité et la taille des entreprises. Cet exemple s’intéresse aux nouvelles recrues, aux employés actifs et aux employés qui ont quitté l’entreprise dans le but de déceler des tendances en matière de stratégie de recrutement. Nos principaux objectifs sont répondre aux questions :

* Qui embauchons-nous ?
* Quelles sont nos tendances en matière de stratégie de recrutement ?
* Quelles sont les tendances en matière de départs volontaires ?

![](media/sample-human-resources/hr1.png)

Cet exemple fait partie d’une série d’exemples qui illustre la façon dont vous pouvez utiliser Power BI avec des données, des rapports et des tableaux de bord orientés métier. Il s’agit de données réelles provenant d’obviEnce ([www.obvience.com](http://www.obvience.com/)), présentées de façon anonyme. Les données sont disponibles dans plusieurs formats : application/pack de contenu, classeur Excel ou fichier PBIX Power BI Desktop. Pour plus d’informations, consultez la section [Jeux de données d’exemple](sample-datasets.md).

## <a name="prerequisites"></a>Conditions préalables

 Avant de pouvoir utiliser l’exemple, vous devez le télécharger en tant que [pack de contenu](https://docs.microsoft.com/power-bi/sample-human-resources#get-the-content-pack-for-this-sample), [fichier pbix](http://download.microsoft.com/download/6/9/5/69503155-05A5-483E-829A-F7B5F3DD5D27/Human%20Resources%20Sample%20PBIX.pbix) ou [classeur Excel](http://go.microsoft.com/fwlink/?LinkId=529780).

### <a name="get-the-content-pack-for-this-sample"></a>Se procurer le pack de contenu pour cet exemple

1. Ouvrez le service Power BI (app.powerbi.com), puis connectez-vous.
2. Dans le coin inférieur gauche, sélectionnez **Obtenir des données**.
   
    ![](media/sample-datasets/power-bi-get-data.png)
3. Dans la page Obtenir des données qui s’affiche, sélectionnez l’icône **Exemples**.
   
   ![](media/sample-datasets/power-bi-samples-icon.png)
4. Sélectionnez l’**exemple Ressources humaines**, puis choisissez **Se connecter**.  
   
   ![Obtenir les données](media/sample-human-resources/pbi_hr_sample_connect.png)
5. Power BI importe le pack de contenu, puis ajoute un tableau de bord, un rapport et un jeu de données à votre espace de travail. Le nouveau contenu est signalé par un astérisque jaune. 
   
   ![Astérisque](media/sample-human-resources/human-resources-sample-asterisk.png)
  
### <a name="get-the-pbix-file-for-this-sample"></a>Se procurer le fichier .pbix pour cet exemple

Vous pouvez également télécharger l’exemple en tant que fichier .pbix, qui est conçu pour une utilisation avec Power BI Desktop. 

 * [PBIX Exemple Ressources humaines](http://download.microsoft.com/download/6/9/5/69503155-05A5-483E-829A-F7B5F3DD5D27/Human%20Resources%20Sample%20PBIX.pbix)

### <a name="get-the-excel-workbook-for-this-sample"></a>Se procurer le classeur Excel pour cet exemple
Vous pouvez également [télécharger uniquement le jeu de données (classeur Excel) de cet exemple](http://go.microsoft.com/fwlink/?LinkId=529780). Le classeur contient des feuilles Power View que vous pouvez consulter et modifier. Pour afficher les données brutes, sélectionnez **Power Pivot > Gérer**.

## <a name="new-hires"></a>Nouvelles recrues
Intéressons-nous d’abord aux nouvelles recrues.

1. Dans votre espace de travail, sélectionnez l’onglet **Tableaux de bord** , puis ouvrez le tableau de bord Ressources humaines.
2. Dans le tableau de bord, sélectionnez la vignette **New Hire Count, New Hires Same Period Last Year, Actives YoY % Change** **(Nombre de nouvelles recrues, Nouvelles recrues l’année dernière à la même période, Évolution du nombre d’actifs d’une année sur l’autre (%) par mois**.  
   ![](media/sample-human-resources/hr2.png)  

   L’exemple de rapport de ressources humaines s’ouvre à la page **Nouvelles recrues** .  

   ![](media/sample-human-resources/hr3.png)

Notez les points suivants :

* Le graphique combiné **New Hire Count, New Hires Same Period Last Year, Actives YoY % Change** (Nombre de nouvelles recrues, Nouvelles recrues l’année dernière à la même période, Évolution du nombre d’actifs d’une année sur l’autre (%)) montre que nous avons embauché plus de personnes par mois cette année que l’année dernière, et ce, dans des proportions considérables pendant certains mois.
* Dans le graphique combiné **New Hire Count and Active Employee Count by Region and Ethnicity**(Nouvelles recrues et actifs par région et par origine ethnique), notez que nous embauchons moins de personnes dans la région **East** (Est).
* Le graphique en cascade **New Hires YoY Var by Age Group** (Variation des nouvelles recrues d’une année sur l’autre par tranche d’âge) montre que nous embauchons principalement des jeunes. Cela est peut-être dû au fait qu’il s’agit essentiellement de postes à temps partiel.
* Le graphique en secteurs **New Hire Count by Gender** (Nombre de nouvelles recrues par sexe) présente une parité assez homogène.

Pouvez-vous trouver d’autres informations ? Par exemple, y a-t-il une région où il n’y a pas de parité entre hommes et femmes ? Sélectionnez, dans les graphiques, les différentes tranches d’âge et les sexes pour explorer les rapports entre l’âge, le sexe, la région et l’origine ethnique.

Sélectionnez le nom du tableau de bord dans la barre de navigation supérieure pour revenir au tableau de bord.

![](media/sample-human-resources/power-bi-breadcrumbs.png)

## <a name="compare-current-active-and-former-employees"></a>Comparaison entre les employés actifs et les anciens employés
Explorons les données pour les employés actifs et les employés qui ne travaillent plus dans l’entreprise.

Dans le tableau de bord, sélectionnez la vignette **Active Employee Count by Age Group** (Nombre d’employés actifs par tranche d’âge).  
![](media/sample-human-resources/pbi_hr_sample_activepie.png)

L’exemple de rapport Ressources humaines s’ouvre à la page **Active Employees vs. Separations** (Employés actifs/cessations d’emploi).  
![](media/sample-human-resources/hr5.png)

**Points intéressants :**

* Les graphiques combinés à gauche montrent l’évolution d’une année sur l’autre pour les employés actifs et les cessations d’emploi. Nous avons davantage d’actifs cette année en raison de l’accélération du rythme d’embauches, mais il y a aussi plus de cessations d’emploi que l’année dernière.
* En août, les cessations d’emploi ont été plus nombreuses par rapport aux autres mois. Sélectionnez les différentes tranches d’âge, les sexes ou les régions pour voir si vous pouvez repérer d’autres points aberrants.
* En examinant les graphiques en secteurs, nous constatons une répartition assez équitable entre nos employés actifs par sexe et par tranche d’âge. Sélectionnez les différentes tranches d’âge pour voir la répartition des hommes et des femmes par âge. La parité entre hommes et femmes existe-t-elle dans chaque tranche d’âge ?

## <a name="reasons-for-separation"></a>Motifs de cessation d’emploi
Examinons le rapport en mode Edition. Sélectionnez **Modifier le rapport** en haut à gauche.

Modifiez les graphiques en secteurs pour afficher les données non pas des actifs, mais des personnes ayant quitté l’entreprise.

1. Sélectionnez le graphique en secteurs **Active Employee Count by Age Group** (Nombre d’employés actifs par tranche d’âge).
2. Dans **Champs**, sélectionnez la flèche en regard d’**Employees** (Employés) pour développer la table Employees (Employés). Décochez la case **Active Employee Count** (Nombre d’employés actifs) pour supprimer ce champ.
3. Cochez la case en regard de **Separation Count** (Nombre de cessations d’emploi) dans la table Employees pour l’ajouter à la zone **Values** (Valeurs) dans le champ.
4. De retour dans la zone de dessin, sélectionnez la barre **Voluntary** (Volontaire) dans le graphique à barres **Separation Count by Separation Reason** (Nombre de cessations d’emploi par motif). Cela permet de mettre en évidence le nombre de départs volontaires dans les autres éléments visuels du rapport.
5. Cliquez sur le secteur 50+ du graphique Separation Count by Age Group (Nombre de cessations d’emploi par tranche d’âge).

   Examinez le graphique en courbes Separations by Reason (Cessations d’emploi par motif) en bas à droite. Ce graphique est filtré pour afficher les départs volontaires.  
   ![](media/sample-human-resources/pbi_hr_sample_sepsover50.png)

   Avez-vous remarqué la tendance pour la tranche d’âge 50+ ? Durant la dernière partie de l’année, les employés de plus de 50 ans sont plus nombreux à quitter volontairement l’entreprise. C’est une question qui mériterait d’être analysée de manière plus approfondie avec des données supplémentaires.
6. Vous pouvez suivre les mêmes étapes pour le graphique en secteurs **Active Employee Count by Gender** (Nombre d’employés actifs par sexe) en remplaçant les employés actifs par les personnes ayant quitté l’entreprise. Examinez les données sur les départs volontaires par sexe pour voir si vous trouvez d’autres indications.
7. Cliquez sur **Power BI** dans la barre de navigation supérieure pour revenir au tableau de bord. Vous pouvez éventuellement enregistrer les modifications que vous avez apportées au rapport.

## <a name="bad-hires"></a>Erreurs de recrutement
Le dernier domaine à explorer est celui des erreurs de recrutement. Les erreurs de recrutement représentent les employés qui ne sont pas restés plus de 60 jours en poste. Nous embauchons rapidement. Recrutons-nous les bons candidats ?

1. Cliquez sur la vignette de tableau de bord **Bad Hires as % of Actives by Age Group** (Erreurs de recrutement en % d’actifs par tranche d’âge). Le rapport s’ouvre à la page 3, « Bad Hires » (Erreurs de recrutement).

   ![](media/sample-human-resources/hr7.png)  
2. Cochez la case **Northwest** (Nord-ouest) dans le segment de la région sur la gauche et la tranche **Male** (Masculin) dans le graphique en anneau Bad Hire Count by Gender (Erreurs de recrutement par sexe).  Examinez les autres graphiques de la page « Bad Hires » (Erreurs de recrutement). Les erreurs de recrutement concernent plus les hommes que les femmes et elles touchent souvent le groupe A.
   ![](media/sample-human-resources/pbi_hr_sample_badhirespage.png)  
3. En examinant le graphique en anneau **Bad Hires by Gender** (Erreurs de recrutement par sexe) et en parcourant le segment **Region** (Région), nous constatons que la région est (« East ») est la seule où les erreurs de recrutement concernent plus les femmes que les hommes.  
4. Sélectionnez le nom du tableau de bord dans la barre de navigation supérieure pour revenir au tableau de bord.

## <a name="asking-a-question-in-the-qa-box"></a>Poser une question dans la zone Q&R
La [zone Questions et réponses](power-bi-tutorial-q-and-a.md) vous permet de taper votre question dans un langage naturel. Q&R reconnaît les mots que vous tapez et cherche l’emplacement dans le jeu de données où se trouve la réponse.

1. Cliquez dans la zone de questions Q&R. Remarquez, avant même de commencer à taper, que la zone Q&R contient des suggestions :

   ![](media/sample-human-resources/pbi_hr_sample_qabox.png)
2. Vous pouvez sélectionner l’une de ces suggestions ou taper : **show age group, gender and bad hires SPLY  where region is east** (afficher le groupe d’âge, le sexe et les mauvais recrutements l’année dernière à la même période dans la région est).  

   ![](media/sample-human-resources/pbi_hr_sample_qa_answer.png)

   Notez que la plupart des femmes rentrant dans la catégorie « Erreurs de recrutement » ont moins de 30 ans.

Il s’agit d’un environnement sécurisé à explorer. Vous pouvez toujours choisir de ne pas enregistrer les modifications apportées. Si vous les enregistrez, vous pouvez toujours accéder à **Obtenir des données** pour avoir une nouvelle copie de cet exemple.

## <a name="next-steps-connect-to-your-data"></a>Étapes suivantes : Vous connecter à vos données
Nous espérons qu’à travers cette visite guidée, vous aurez cerné tout l’intérêt des tableaux de bord Power BI, de Q&R et des rapports pour tirer des informations des données de ressources humaines. À présent, c’est votre tour : connectez-vous à vos propres données. Avec Power BI, vous pouvez vous connecter à une grande variété de sources de données. En savoir plus sur [la prise en main de Power BI](service-get-started.md).  
