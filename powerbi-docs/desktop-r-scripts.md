---
title: Exécution de scripts R dans Power BI Desktop
description: Exécution de scripts R dans Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 05/02/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: acadd84fbd8d0cf7f44b23362474d08608107f24
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34286448"
---
# <a name="run-r-scripts-in-power-bi-desktop"></a>Exécuter des scripts R dans Power BI Desktop
Vous pouvez exécuter des scripts R directement dans **Power BI Desktop** et importer les jeux de données obtenus dans un modèle de données Power BI Desktop.

## <a name="install-r"></a>Installer R
Pour exécuter des scripts R dans Power BI Desktop, vous devez installer **R** sur votre ordinateur local. Vous pouvez télécharger et installer **R** gratuitement à partir de nombreux emplacements, dont les pages [Download Revolution R Open](https://mran.revolutionanalytics.com/download/) et [CRAN Repository](https://cran.r-project.org/bin/windows/base/). La version actuelle des scripts R dans Power BI Desktop prend en charge les caractères Unicode ainsi que les espaces (caractères vides) dans le chemin d’installation.

## <a name="run-r-scripts"></a>Exécuter des scripts R
Dans Power BI Desktop, quelques étapes suffisent pour exécuter des scripts R et créer un modèle de données à partir duquel vous pouvez générer des rapports et les partager sur le service Power BI. Les scripts R dans Power BI Desktop prennent maintenant en charge les formats de nombres qui contiennent des virgules (,) et des points (.).

### <a name="prepare-an-r-script"></a>Préparer un script R
Pour exécuter un script R dans Power BI Desktop, créez-le dans votre environnement de développement R local, puis assurez-vous qu’il fonctionne correctement.

Pour exécuter le script dans Power BI Desktop, assurez-vous qu’il s’exécute correctement dans un espace de travail nouveau et non modifié. Cela signifie que l’ensemble des packages et dépendances doivent être explicitement chargés et exécutés. Vous pouvez utiliser *source()* pour exécuter des scripts dépendants.

Lors de la préparation et l’exécution d’un script R dans Power BI Desktop, vous pouvez être confronté à quelques limitations :

* Seules les trames de données sont importées ; assurez-vous donc que les données que vous souhaitez importer dans Power BI sont représentées dans une trame de données
* Les colonnes qui sont de type Complexe et Vecteur ne sont pas importées et sont remplacées par des valeurs d’erreur dans la table créée
* Les valeurs marquées comme non applicables (N/A) sont converties en valeurs NULL dans Power BI Desktop
* Tous les scripts exécutés pendant plus de 30 minutes expirent
* Les appels interactifs dans le script R, comme l’attente pour l’entrée d’un utilisateur, arrêtent l’exécution du script
* Lorsque vous définissez le répertoire de travail dans le script R, vous *devez* définir un chemin d’accès complet vers le répertoire de travail, au lieu d’un chemin d’accès relatif

### <a name="run-your-r-script-and-import-data"></a>Exécuter votre script R et importer des données
1. Dans Power BI Desktop, le connecteur de données du script R se trouve dans **Obtenir des données**. Pour exécuter votre script R, sélectionnez **Obtenir des données &gt; Plus...**, puis sélectionnez **Autres &gt; Script R**, comme illustré dans l’image suivante :
   
   ![](media/desktop-r-scripts/r-scripts-1.png)
2. Si R est installé sur votre ordinateur local, la dernière version installée est sélectionnée comme votre moteur R. Copiez simplement votre script dans la fenêtre de script, puis cliquez sur **OK**.
   
   ![](media/desktop-r-scripts/r-scripts-2.png)
3. Si R n’est pas installé, n’est pas identifié ou s’il existe plusieurs installations sur votre ordinateur local, développez **Paramètres d’installation de R** pour afficher les options d’installation ou pour sélectionner l’installation pour laquelle vous souhaitez exécuter le script R.
   
   ![](media/desktop-r-scripts/r-scripts-3.png)
   
   Si R est installé mais n’est pas identifié, vous pouvez indiquer explicitement son emplacement dans la zone de texte fournie lorsque vous développez **Paramètres d’installation de R**. Dans l’illustration ci-dessus, le chemin d’accès *C:\Program Files\R\R-3.2.0* est explicitement fourni dans la zone de texte.
   
   Les paramètres d’installation de R sont centralisés dans la section des scripts R de la boîte de dialogue Options. Pour spécifier vos paramètres d’installation de R, sélectionnez **Fichier > Options et paramètres**, puis **Options > Scripts R**. Si plusieurs installations de R sont disponibles, un menu déroulant s’affiche pour sélectionner l’installation à utiliser.
   
   ![](media/desktop-r-scripts/r-scripts-4.png)
4. Sélectionnez **OK** pour exécuter le script R. Lorsque le script s’exécute correctement, vous pouvez choisir les trames de données obtenues pour les ajouter au modèle Power BI.

### <a name="refresh"></a>Actualisation
Vous pouvez actualiser un script R dans Power BI Desktop. Lorsque vous actualisez un script R, Power BI Desktop réexécute le script R dans l’environnement de Power BI Desktop.

## <a name="next-steps"></a>Étapes suivantes
Consultez les informations supplémentaires suivantes sur R dans Power BI.

* [Créer des visuels Power BI avec R](desktop-r-visuals.md)
* [Utiliser un IDE R externe avec Power BI](desktop-r-ide.md)

