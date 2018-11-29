---
title: Présentation des rapports paginés dans Power BI Premium (Préversion)
description: Les rapports paginés sont des rapports qui peuvent être imprimés ou partagés. Vous pouvez contrôler exactement la disposition des rapports. Ils affichent toutes les données dans une table, par exemple, même si la table s’étend sur plusieurs pages.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: report-builder
ms.topic: overview
ms.date: 11/20/2018
ms.author: maggies
ms.openlocfilehash: 7a39d7b3bdbbd592afc6481c5936efc76569ad11
ms.sourcegitcommit: 458e091a0a0bfb71ea3980d44df6408f48bab586
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2018
ms.locfileid: "52289217"
---
# <a name="what-are-paginated-reports-in-power-bi-premium-preview"></a>Présentation des rapports paginés dans Power BI Premium (Préversion)
Les rapports paginés, depuis longtemps le format standard pour les rapports dans SQL Server Reporting Services, sont désormais disponibles dans le service Power BI. Les rapports paginés sont des rapports conçus pour être imprimés ou partagés. Ils sont appelés « paginés », car ils sont mis en forme pour tenir sur une page. Ils affichent toutes les données dans une table, même si la table s’étend sur plusieurs pages. Ils sont parfois appelés « pixel parfait », car vous pouvez contrôler exactement leur mise en page. Les rapports paginés sont basés sur la technologie de rapport RDL dans SQL Server Reporting Services. Le Générateur de rapports est l’outil autonome pour la création de rapports paginés. 

Les rapports paginés peuvent avoir de nombreuses pages. Par exemple, ce rapport compte 563 pages. Chaque page est mise en page exactement, avec une page par facture et des en-têtes et pieds de page récurrents.

![Rapport paginé dans le service Power BI](media/paginated-reports-report-builder-power-bi/power-bi-paginated-wwi-report-page.png)

Vous pouvez prévisualiser votre rapport dans le Générateur de rapports, puis le publier sur le service Power BI, http://app.powerbi.com. Vous avez besoin d’une licence Power BI Pro pour publier un rapport sur le service. Vous pouvez publier et partager des rapports paginés sous Mon espace de travail ou dans les espaces de travail de l’application tant que l’espace de travail est dans une capacité Power BI Premium. Par ailleurs, un administrateur Power BI doit activer les rapports paginés dans le portail d’administration Power BI. En savoir plus sur la [configuration des charges de travail](service-admin-premium-manage.md#configure-workloads). 

## <a name="create-reports-in-report-builder"></a>Créer des rapports dans le Générateur de rapports

Les rapports paginés ont leur propre outil de conception, le Générateur de rapports. Il s’agit du même outil et de la même version que vous utilisez pour créer des rapports paginés pour Power BI Report Server ou SQL Server Reporting Services (SSRS). En fait, les rapports paginés que vous créez pour SSRS 2016 et 2017 ou localement pour Power BI Report Server sont compatibles avec le service Power BI. Le service Power BI assure la compatibilité descendante, de sorte que vous pouvez avancer vos rapports et mettre à niveau tous les rapports paginés avec une version précédente. Les fonctionnalités relatives aux rapports ne sont pas toutes disponibles au lancement. Pour plus d’informations, consultez [Considérations et limitations](#limitations-and-considerations) dans cet article.
     
## <a name="report-from-a-variety-of-data-sources"></a>Rapport basé sur diverses sources de données

Un seul rapport paginé peut avoir un certain nombre de sources de données différentes. Il n’a pas de modèle de données sous-jacent, contrairement aux rapports Power BI. Pour obtenir la version initiale de rapports paginés dans le service Power BI, vous créez des sources de données incorporées et des jeux de données dans le rapport proprement dit. Pour l’instant, vous ne pouvez pas utiliser de sources de données partagées ni de jeux de données partagés. Vous créez des rapports dans le Générateur de rapports sur votre ordinateur local. Si un rapport se connecte à des données locales, après avoir chargé le rapport sur le service Power BI, vous devez créer une passerelle et rediriger la connexion de données. Voici les sources de données auxquelles vous pouvez vous connecter pour la version initiale :

- Azure SQL Database et Data Warehouse
- SQL Server via une passerelle
- SQL Server Analysis Services via une passerelle
 
Des sources de données supplémentaires seront disponibles pendant la période de préversion.

## <a name="design-your-report"></a>Créer votre rapport  

### <a name="create-paginated-reports-with-matrix-chart-and-free-form-layouts"></a>Créer des rapports paginés avec des mises en page matricielles, graphiques et de forme libre

Créer des rapports de tableaux pour les données en colonnes, des rapports de matrices (par exemple, des rapports d’analyse croisée ou de tableaux croisés dynamiques) pour les données résumées, des rapports graphiques pour les données graphiques et des *listes* de rapports en forme libre pour tous les autres éléments, comme les factures. 
  
Vous pouvez démarrer avec un des Assistants du Générateur de rapports. Les Assistants Table, Matrice et Graphique vous guident lors de la création de la connexion de source de données incorporées et le jeu de données incorporé. Faites ensuite glisser-déplacer des champs pour créer une requête de jeu de données, sélectionnez une disposition et un style, et personnalisez votre rapport.  
  
Avec l’Assistant Carte, vous créez des rapports qui affichent des données agrégées sur un arrière-plan géographique ou géométrique. Les données cartographiques peuvent être des données spatiales issues d’une requête Transact-SQL ou un fichier de forme de l’Environmental Systems Research Institute, Inc. Vous pouvez également ajouter un arrière-plan de mosaïque Microsoft Bing.  

### <a name="add-more-to-your-report"></a>Ajouter une page à votre rapport

Modifiez vos données par filtrage, regroupement et tri des données, ou en ajoutant des formules ou des expressions. Ajoutez des graphiques, des jauges, des graphiques sparkline et des indicateurs pour résumer les données dans un format visuel.  Utilisez des paramètres et des filtres pour filtrer les données et obtenir des vues personnalisées. Incorporez ou référencez des images et d’autres ressources, y compris du contenu externe.  

Tous les éléments d’un rapport paginé, du rapport proprement dit à chaque zone de texte, image, table et graphique, a un ensemble de propriétés que vous pouvez définir pour que le rapport ait exactement l’apparence souhaitée.

## <a name="creating-a-report-definition"></a>Création d’une définition de rapport

Lorsque vous concevez un rapport paginé, vous créez vraiment une *définition de rapport*. Il ne contient pas les données. Il spécifie où obtenir les données, les données à obtenir et comment les afficher. Lorsque vous exécutez le rapport, le processeur de rapports prend la définition de rapport que vous avez spécifiée, récupère les données et les combine avec la disposition du rapport pour le générer. Vous chargez la définition de rapport sur le service Power BI, http://app.powerbi.com, sous Mon espace de travail ou dans un espace de travail partagé avec vos collègues. Si la source de données du rapport est locale, après avoir chargé le rapport, vous redirigez la connexion de la source de données à travers une passerelle. 

## <a name="view-your-paginated-report"></a>Créer votre rapport paginé
Vous affichez votre rapport paginé dans le service Power BI dans un navigateur ainsi que dans les applications mobiles Power BI. À partir du service Power BI, vous pouvez exporter le rapport dans plusieurs formats, dont HTML, MHTML, PDF, XML, CSV, TIFF, Word et Excel. Vous pouvez également le partager avec d’autres utilisateurs.  
  
## <a name="limitations-and-considerations"></a>Considérations et limitations

Voici d’autres fonctionnalités qui ne sont pas prises en charge dans la version initiale :

- Épinglage des pages de rapport ou des visuels sur des tableaux de bord Power BI.
- Fonctionnalités interactives telles que des cartes de documents et des boutons Afficher/Masquer.
- Sous-rapports et rapports d’extraction.
- Abonnements.
- Sources de données et jeux de données partagés.
- Jeux de données Power BI.
- Visuels issus de rapports Power BI.
- Rapports paginés dans des applications. Vous pouvez partager un rapport paginé à partir de l’espace de travail d’une application, mais vous ne pouvez pas l’inclure lorsque vous publiez l’application à partir de cet espace de travail.
 
## <a name="next-steps"></a>Étapes suivantes

- [Installer le Générateur de rapports à partir du centre de téléchargement Microsoft](http://go.microsoft.com/fwlink/?LinkID=734968)
- [Tutoriel : Créer un rapport paginé](paginated-reports-quickstart-aw.md)
- [Entrer des données directement dans un rapport paginé](paginated-reports-enter-data.md)

  

