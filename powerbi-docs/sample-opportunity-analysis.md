---
title: 'Exemple Analyse des opportunités pour Power BI : Visite guidée'
description: 'Exemple Analyse des opportunités pour Power BI : Visite guidée'
author: maggiesMSFT
manager: kfile
ms.reviewer: amac
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 07/02/2019
ms.author: maggies
LocalizationGroup: Samples
ms.openlocfilehash: 233b4c36b5e59b38c82f5c3ccc1f0b49b70c5ac8
ms.sourcegitcommit: f05ba39a0e46cb9cb43454772fbc5397089d58b4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68523454"
---
# <a name="opportunity-analysis-sample-for-power-bi-take-a-tour"></a>Exemple Analyse des opportunités pour Power BI : Visite guidée

Le pack de contenu Exemple Analyse des opportunités contient un tableau de bord, un rapport et un jeu de données pour une société de logiciels qui a deux canaux de vente : *direct* et *partenaire*. Le directeur des ventes a créé ce tableau de bord pour suivre les opportunités et le chiffre d’affaires par région, par volume de transactions et par canal.

Cet exemple s’appuie sur 2 mesures du chiffre d’affaires :

* Chiffre d’affaires : Une estimation par un vendeur du chiffre d’affaires à venir.
* Chiffre d’affaires pondéré : Calculé selon la formule Chiffre d’affaires X Probabilité en %. Il est considéré comme une prévision plus précise du chiffre d’affaires réel. La probabilité est déterminée en fonction de l’*étape de vente* dans laquelle se trouve l’affaire :
  * Lead : 10 %  
  * Qualify : 20 %  
  * Solution : 40 %  
  * Proposal : 60 %  
  * Finalize : 80 %

![Tableau de bord pour l’Exemple Analyse des opportunités](media/sample-opportunity-analysis/opportunity1.png)

Cet exemple fait partie d’une série d’exemples qui illustre la façon dont vous pouvez utiliser Power BI avec des données, des rapports et des tableaux de bord orientés métier. Il a été créé par [obviEnce](http://www.obvience.com/) avec des données réelles qui sont présentées de façon anonyme. Les données sont disponibles dans plusieurs formats : pack de contenu, fichier .pbix Power BI Desktop ou classeur Excel. Consultez [Exemples pour Power BI](sample-datasets.md). 

Ce tutoriel explore le pack de contenu Exemple Analyse des opportunités dans le service Power BI. Les expériences d’utilisation des rapports étant similaires dans Power BI Desktop et dans le service, vous pouvez également poursuivre avec et l’exemple de fichier .pbix dans Power BI Desktop. 

Vous n’avez pas besoin d’une licence Power BI pour explorer les exemples dans Power BI Desktop. Si vous n’avez pas de licence Power BI Pro, vous pouvez enregistrer l’exemple dans votre espace Mon espace de travail du service Power BI. 

## <a name="get-the-sample"></a>Obtenir l’exemple

Avant de pouvoir utiliser l’exemple, vous devez le télécharger en tant que [pack de contenu](#get-the-content-pack-for-this-sample), [fichier .pbix](#get-the-pbix-file-for-this-sample) ou [classeur Excel](#get-the-excel-workbook-for-this-sample).

### <a name="get-the-content-pack-for-this-sample"></a>Se procurer le pack de contenu pour cet exemple

1. Ouvrez le service Power BI (app.powerbi.com), connectez-vous et ouvrez l’espace de travail où vous souhaitez enregistrer l’exemple. 

    Si vous n’avez pas de licence Power BI Pro, vous pouvez enregistrer l’exemple dans votre espace Mon espace de travail.

2. Dans le coin inférieur gauche, sélectionnez **Obtenir des données**.

    ![Sélectionner Obtenir les données](media/sample-datasets/power-bi-get-data.png)
3. Dans la page **Obtenir des données** qui s’affiche, sélectionnez **Exemples**.

4. Sélectionnez **Exemple Analyse des opportunités**, puis choisissez **Se connecter**.  

   ![Se connecter à un exemple](media/sample-opportunity-analysis/opportunity-connect.png)
5. Power BI importe le pack de contenu, puis ajoute un tableau de bord, un rapport et un jeu de données à votre espace de travail actuel.

   ![Entrée Exemple Analyse des opportunités](media/sample-opportunity-analysis/opportunity-entry.png)

### <a name="get-the-pbix-file-for-this-sample"></a>Se procurer le fichier .pbix pour cet exemple

Vous pouvez aussi télécharger l’exemple Analyse des opportunités sous forme de [fichier .pbix](http://download.microsoft.com/download/9/1/5/915ABCFA-7125-4D85-A7BD-05645BD95BD8/Opportunity%20Analysis%20Sample%20PBIX.pbix), qui est conçu pour être utilisé avec Power BI Desktop.

### <a name="get-the-excel-workbook-for-this-sample"></a>Se procurer le classeur Excel pour cet exemple

Si vous souhaitez afficher la source de données de cet exemple, elle est également disponible en tant que [classeur Excel](http://go.microsoft.com/fwlink/?LinkId=529782). Le classeur contient des feuilles Power View que vous pouvez consulter et modifier. Pour afficher les données brutes, activez les compléments Analyse de données, puis sélectionnez **Power Pivot > Gérer**. Pour plus d’informations sur l’activation des compléments Power View et Power Pivot, consultez [Affichage des exemples Excel directement dans Excel](sample-datasets.md#optional-take-a-look-at-the-excel-samples-from-inside-excel-itself).

## <a name="what-is-our-dashboard-telling-us"></a>Que nous révèle ce tableau de bord ?
Notre responsable des ventes a créé un tableau de bord pour suivre les métriques qu’elle juge les plus importantes. Quand quelque chose l’interpelle, elle peut sélectionner une vignette pour explorer les données :

- La société réalise un chiffre d’affaires de 2 milliards de dollars et un chiffre d’affaires pondéré de 461 millions de dollars.
- Le nombre d’opportunités et le chiffre d’affaires obéissent à une logique d’entonnoir bien connue où les totaux diminuent à chaque étape de la séquence.
- La plupart de nos opportunités se situent dans la région Est (« East »).
- Les opportunités importantes génèrent davantage de chiffre d’affaires que les opportunités petites ou moyennes.
- Les affaires conclues avec des partenaires importants génèrent un plus grand chiffre d’affaires : 8 millions de dollars en moyenne, contre 6 millions de dollars pour les ventes directes.

Sachant que les efforts à déployer pour décrocher un contrat sont les mêmes quelle que soit sa taille, notre société a tout intérêt à analyser les données pour en apprendre davantage sur les opportunités importantes.

1. Dans l’espace de travail où vous avez enregistré l’exemple, ouvrez l’onglet **Tableaux de bord**, puis recherchez le tableau de bord **Opportunity Analysis Sample** et sélectionnez-le.

2. Sélectionnez la vignette **Opportunity Count by Partner Driven, Sales Stage** pour ouvrir la première page du rapport Opportunity Analysis Sample. 

    ![Vignette Opportunity Count by Partner Driven, Sales Stage](media/sample-opportunity-analysis/opportunity2.png)

## <a name="explore-the-pages-in-the-report"></a>Exploration des pages du rapport

Affichez chaque page du rapport en sélectionnant les onglets des pages dans le bas.

### <a name="opportunity-count-overview-page"></a>Page Opportunity Count Overview
![Page Opportunity Count](media/sample-opportunity-analysis/opportunity3.png)

Notez les points suivants :
* L’Est est notre région la plus importante en termes de nombre d’opportunités.  
* Dans le graphique en secteurs **Opportunity Count by Region**, sélectionnez chaque région tour à tour pour filtrer la page par région. Pour chaque région, notez que les partenaires visent des opportunités bien plus importantes.   
* L’histogramme **Opportunity Count by Partner Driven and Opportunity Size** montre que la plupart des opportunités importantes sont portées par les partenaires, contrairement aux opportunités petites et moyennes.
* Dans l’histogramme **Opportunity Count by Sales Stage**, sélectionnez chaque **Sales Stage** tour à tour pour voir la différence dans les totaux par région. Notez que bien que la région East ait le plus grand nombre d’opportunités, les trois régions ont des totaux comparables dans les étapes de vente Solution, Proposal et Finalize. Cela signifie que nous concluons un pourcentage de contrats plus élevé dans les régions Central et West.

### <a name="revenue-analysis-page"></a>Page Revenue Analysis
Cette page montre les données de façon similaire, mais l’analyse porte sur le chiffre d’affaires et non pas sur le nombre d’opportunités.  

![Page Revenue Overview](media/sample-opportunity-analysis/opportunity4.png)

Notez les points suivants :
* East est notre région principale, aussi bien en termes de nombre d’opportunités que de chiffre d’affaires.  
* Si vous filtrez le graphique **Revenue by Sales Stage and Partner Driven** en sélectionnant **Yes** pour **Partner Driven**, vous voyez un chiffre d’affaires de 1,5 milliards de dollars et un chiffre d’affaires pondéré de 294 millions de dollars. Comparez ces quantités aux 644 millions de dollars et aux 166 millions de dollars pour le chiffre d’affaires « non-partenaire ». 
* Le chiffre d’affaires moyen réalisé auprès des grands comptes est supérieur et est de 8 millions si l’opportunité est portée par un partenaire, au lieu de 6 millions si elle est « non-partenaire ».  
* Pour les affaires conclues par les partenaires, le chiffre d’affaires réalisé sur les opportunités importantes représente en moyenne presque le double de celui des opportunités moyennes.  
* Le chiffre d’affaires moyen généré par les affaires de petite et moyenne taille réalisées par les partenaires est comparable à celui des non-partenaires.   

Il apparaît clairement que nos partenaires vendent mieux à nos clients que les revendeurs non-partenaires. Il pourrait être judicieux de miser davantage sur nos partenaires.

### <a name="opportunity-count-by-region-and-stage"></a>Opportunity Count by Region and Stage
Cette page du rapport présente des données similaires à celles de la page précédente, mais elle les décompose par région et par étape. 

![Page Region Stage Counts](media/sample-opportunity-analysis/opportunity5.png)

Notez les points suivants :
* Si vous sélectionnez **East** dans le graphique à secteurs **Opportunity Count by Region** pour filtrer selon la région East, vous voyez que les opportunités dans cette région sont réparties de façon quasi égale entre celles qui sont portées par les partenaires et celles portées par les « non-partenaires ».
* Les opportunités importantes sont plus courantes dans la région Central, les opportunités de petite taille sont plus courantes dans la région East et les opportunités de taille moyenne sont plus courantes dans la région West.

### <a name="upcoming-opportunities-by-month-page"></a>Page Upcoming Opportunities by Month
Pour cette page, nous nous intéressons à des facteurs similaires, mais dans une perspective portant sur les dates et la chronologie. 
 
![Page Upcoming Opportunities](media/sample-opportunity-analysis/opportunity6.png)

Notre directrice financière se sert de cette page pour gérer la charge de travail. L’analyse des opportunités de chiffre d’affaires par étape de vente et par mois lui permet de planifier en conséquence.

Notez les points suivants :
* C’est à l’étape de vente Finalize que le chiffre d’affaires moyen est le plus élevé. La priorité absolue est de conclure ces affaires.
* Si vous filtrez sur le mois (en sélectionnant le mois dans le sélecteur **Month**), vous voyez que le mois de janvier compte une grande proportion de gros contrats à l’étape de vente Finalize avec un chiffre d’affaires pondéré de 75 millions de dollars. En revanche, au mois de février, il y a principalement des contrats de taille moyenne aux étapes de vente Solution et Proposal.
* En règle générale, le chiffre d’affaires pondéré varie en fonction de l’étape de vente, du nombre d’opportunités et de la taille de contrat. Ajoutez des filtres pour ces facteurs en utilisant le volet **Filtrer** sur la droite pour découvrir d’autres insights.

## <a name="next-steps-connect-to-your-data"></a>Étapes suivantes : Vous connecter à vos données
Cet environnement est sécurisé pour y jouer, étant donné que vous pouvez choisir ne pas enregistrer vos modifications. Mais si vous les enregistrez, vous pouvez toujours sélectionner **Obtenir des données** pour obtenir une nouvelle copie de cet exemple.

Nous espérons que cette visite guidée vous a montré comment les tableaux de bord, Questions et réponses et les rapports Power BI peuvent fournir des insights sur des exemples de données. À présent, c’est votre tour : connectez-vous à vos propres données. Avec Power BI, vous pouvez vous connecter à une grande variété de sources de données. Pour en savoir plus, consultez [Prise en main du service Power BI](service-get-started.md).

