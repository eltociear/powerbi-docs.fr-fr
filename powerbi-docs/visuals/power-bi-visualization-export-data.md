---
title: Exporter des données à partir d’une visualisation Power BI
description: Exportez des données à partir d’une visualisation de rapport et d’une visualisation de tableau de bord et affichez-les dans Excel.
author: mihart
manager: kvivek
ms.reviewer: tessa
featuredvideoid: jtlLGRKBvXY
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 11/13/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 5c2f448ff705f00bc443a6a27fa80e1b5164a901
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75757804"
---
# <a name="export-the-data-that-was-used-to-create-a-visualization"></a>Exporter les données utilisées pour créer une visualisation

Si vous souhaitez afficher les données utilisées par Power BI pour créer une visualisation, vous pouvez [le faire dans Power BI](service-reports-show-data.md). Vous pouvez également exporter ces données vers Excel sous forme de fichier *.xlsx* ou *.csv*. La possibilité d’exporter les données nécessite une licence Pro ou Premium et des autorisations de modification sur le jeu de données et le rapport. <!--If you have access to the dashboard or report but the data is classified as *highly confidential*, Power BI will not allow you to export the data.-->

Regardez Will pendant qu’il exporte les données à partir d’une des visualisations de son rapport, les enregistre au format *.xlsx* et ouvre le fichier dans Excel. Suivez ensuite les instructions détaillées sous la vidéo pour essayer vous-même.

<iframe width="560" height="315" src="https://www.youtube.com/embed/KjheMTGjDXw" frameborder="0" allowfullscreen></iframe>

## <a name="export-data-from-a-power-bi-dashboard"></a>Exporter des données à partir d’un tableau de bord Power BI

1. Sélectionnez les points de suspension (...) dans le coin supérieur droit de la visualisation.

    ![Capture d’écran d’une visualisation avec une flèche pointant vers le bouton avec des points de suspension (...).](media/power-bi-visualization-export-data/pbi-export-tile3.png)

1. Sélectionnez l’icône **Exporter les données**.

    ![Capture d’écran de la liste déroulante avec des points de suspension (...) montrant l’option Exporter les données.](media/power-bi-visualization-export-data/pbi_export_dash.png)

1. Power BI exporte les données vers un fichier *.csv*. Si vous avez filtré la visualisation, l’application filtre les données téléchargées.

1. Votre navigateur vous invite à enregistrer le fichier.  Lorsque c’est fait, ouvrez le fichier *.csv* dans Excel.

    ![Capture d’écran du fichier .csv avec les données exportées affichées.](media/power-bi-visualization-export-data/pbi-export-to-excel.png)

## <a name="export-data-from-a-report"></a>Exporter des données à partir d’un rapport

Pour effectuer cette procédure, ouvrez l’[exemple de rapport Procurement Analysis](../sample-procurement.md) (Analyse de l’approvisionnement) en mode Édition. Ajoutez une nouvelle page de rapport vierge. Puis suivez les étapes ci-dessous pour ajouter un regroupement et un filtre au niveau des visualisations.

1. Créer un **histogramme empilé**.

1. Dans le volet **Champs**, sélectionnez **Location > City** (Emplacement > Ville) et **Invoice > Discount Percent** (Facture > % de remise).  Vous devrez peut-être déplacer **Discount Percent** (% de remise) dans la zone **Valeur**.

    ![Capture d’écran de la visualisation créée avec City et Count of Discount Percent.](media/power-bi-visualization-export-data/power-bi-export-data3.png)

1. Définissez l’agrégation **Discount Percent** (% de remise) de **Nombre** à **Moyenne**. Dans la zone **Valeur**, sélectionnez la flèche à droite de **Discount Percent** (% de remise)(il se peut qu’elle indique **Nombre du pourcentage de remise**), puis choisissez **Moyenne**.

    ![Screenshot de la liste d’agrégation avec l’option Moyenne.](media/power-bi-visualization-export-data/power-bi-export-data6.png)

1. Ajoutez un filtre à **City**, sélectionnez toutes les villes, puis supprimez **Atlanta**.

    ![Screenshot du filtre City avec la case à cocher Atlanta, GA désactivée.](media/power-bi-visualization-export-data/power-bi-export-data4.png)

   Vous êtes maintenant prêt à tester les deux options d’exportation des données.

1. Sélectionnez les points de suspension (...) dans le coin supérieur droit de la visualisation. Sélectionner **Exporter des données**.

    ![Screenshot du coin supérieur droit montrant le bouton avec points de suspension (...) et l’option Exporter des données.](media/power-bi-visualization-export-data/power-bi-export-data2.png)

    Dans Power BI Online, si votre visualisation a un agrégat (par exemple, si vous avez défini **Nombre** sur *Moyenne*, *Somme* ou *Minimum*), vous avez deux options :

    - **Données résumées**

    - **Données sous-jacentes**

    Dans Power BI Desktop, vous aurez seulement l’option **Données résumées**. Pour comprendre le fonctionnement des agrégats, consultez [Agrégats dans Power BI](../service-aggregates.md).

1. À partir de **Exporter des données**, sélectionnez **Données résumées**, choisissez *.xlsx* ou *.csv*, puis sélectionnez **Exporter**. Power BI exporte les données.

    ![Capture d’écran d’Exporter des donnés avec les options Données résumées, xlsx et Exporter.](media/power-bi-visualization-export-data/power-bi-export-data5.png)

    Si vous avez appliqué des filtres à la visualisation, les données sont exportées en étant filtrées. Lorsque vous sélectionnez **Exporter**, votre navigateur vous invite à enregistrer le fichier. Lorsque c’est fait, ouvrez le fichier dans Excel.
    
    Toutes les données utilisées par la hiérarchie sont exportées, pas seulement celles utilisées pour le niveau de détail actuel du visuel. Par exemple, si la visualisation n'a pas encore été explorée au niveau du détail depuis le niveau supérieur, les données exportées incluront toutes les données de la hiérarchie, pas seulement celles utilisées pour créer le visuel à son niveau de détail actuel.

    **Données résumées** : sélectionnez cette option si vous voulez exporter les données correspondant au visuel affiché.  Ce type d’exportation contient uniquement les données (colonnes et mesures) que vous avez choisies pour créer le visuel.  Si le visuel contient un agrégat, vous exportez des données agrégées. Par exemple, si vous avez un graphique à barres affichant quatre barres, vous obtenez quatre lignes de données. Les données résumées sont disponibles aux formats *.xlsx* et *.csv*.

    Dans cet exemple, notre exportation Excel affiche un seul total par ville. Étant donné que nous avons filtré et retiré la ville d’Atlanta, celle-ci n’est pas incluse dans les résultats. La première ligne de la feuille de calcul affiche les filtres que Power BI a utilisés lors de l’extraction des données.

    ![Capture d’écran du fichier .csv avec les données exportées affichées.](media/power-bi-visualization-export-data/power-bi-export-data7.png)

1. Essayez maintenant de sélectionner **Sonnées sous-jacentes**, *.xlsx*, puis **Exporter**. Power BI exporte les données. 

    > [!NOTE]
    > En fonction des paramètres de rapport, vous pouvez ou pouvez ne pas avoir la possibilité d’exporter des données sous-jacentes.

    Si vous avez appliqué des filtres à la visualisation, les données sont exportées en étant filtrées. Lorsque vous sélectionnez **Exporter**, votre navigateur vous invite à enregistrer le fichier. Lorsque c’est fait, ouvrez le fichier dans Excel.
    
    Toutes les données utilisées par la hiérarchie sont exportées, pas seulement celles utilisées pour le niveau de détail actuel du visuel. Par exemple, si la visualisation n'a pas encore été explorée au niveau du détail depuis le niveau supérieur, les données exportées incluront toutes les données de la hiérarchie, pas seulement celles utilisées pour créer le visuel à son niveau de détail actuel.

    >[!WARNING]
    >L’exportation de données sous-jacentes permet aux utilisateurs de voir toutes les données détaillées, chaque colonne de données. Les administrateurs de service Power BI peuvent désactiver cette option pour leur organisation. Si vous êtes propriétaire d’un jeu de données, vous pouvez définir des colonnes propriétaires comme étant **masquées** afin qu’elles n’apparaissent pas dans la liste **Champ** dans le service Power BI ou dans Power BI Desktop.

    **Données sous-jacentes** : sélectionnez cette option si vous voulez afficher les données contenues dans le visuel ***et*** les autres données du modèle (voir le tableau ci-dessous pour plus de détails). Si votre visualisation contient un agrégat, celui-ci est supprimé si vous sélectionnez *Données sous-jacentes*. Lorsque vous sélectionnez **Exporter**, Power BI exporte les données sont dans un fichier *.xlsx* que votre navigateur vous invite à enregistrer. Lorsque c’est fait, ouvrez le fichier dans Excel.

    Dans cet exemple, l’exportation Excel affiche une seule ligne pour chaque ligne unique Ville de notre jeu de données, ainsi que le pourcentage de remise pour cette entrée unique. Power BI aplatit les données. Il ne les agrège pas. La première ligne de la feuille de calcul affiche les filtres que Power BI a utilisés lors de l’extraction des données.  

    ![Capture d’écran du fichier .csv avec les données exportées affichées.](media/power-bi-visualization-export-data/power-bi-export-data8.png)

## <a name="export-underlying-data-details"></a>Exporter les détails concernant les données sous-jacentes

Ce qui s’affiche à l’écran quand vous sélectionnez **Données sous-jacentes** peut varier selon le cas. L’aide de votre administrateur ou de votre service informatique peut s’avérer nécessaire pour bien comprendre ces détails. Dans Power BI Desktop ou le service Power BI, dans la vue de création de rapports, une *mesure* s’affiche dans la liste **Champs** avec une icône représentant une calculatrice ![icône affichée](media/power-bi-visualization-export-data/power-bi-calculator-icon.png). Power BI Desktop crée des mesures. Ce n’est pas le cas pour le service Power BI.

| Contenu du visuel | Contenu de l’exportation  |
|---------------- | ---------------------------|
| Agrégats | Le *premier* agrégat et les données non masquées de la table entière pour cet agrégat |
| Agrégats | Les données associées, si le visuel utilise les données d’autres tables de données *associées* à celle qui contient l’agrégat (dans la mesure où il s’agit d’une relation \*:1 ou 1:1) |
| Mesures | toutes les mesures contenues dans le visuel *et* toutes les mesures d’une table de données contenant une mesure utilisée dans le visuel |
| Mesures | toutes les données non masquées des tables qui contiennent cette mesure (dans la mesure où il s’agit d’une relation \*:1 ou 1:1) |
| Mesures | toutes les données de toutes les tables associées à une ou plusieurs tables contenant les mesures via une chaîne de \* : 1 sur 1:1 |
| Mesures uniquement | toutes les colonnes non masqués de toutes les tables associées (pour étendre la mesure) |
| Mesures uniquement | les données résumées de toutes les lignes en double pour les mesures du modèle |

### <a name="set-the-export-options"></a>Définir les options d’exportation

Les concepteurs de rapports Power BI contrôlent les types d’options d’exportation de données qui sont à la disposition de leurs clients. Les choix sont les suivants :

- Autoriser les utilisateurs finaux à exporter les données récapitulatives du service Power BI ou de Power BI Report Server

- Autoriser les utilisateurs finaux à exporter les données récapitulatives et sous-jacentes du service ou de Report Server

- Ne pas autoriser les utilisateurs finaux à exporter les données du service ou de Report Server

    > [!IMPORTANT]
    > Nous recommandons aux concepteurs de rapports de réexaminer les anciens rapports et de réinitialiser manuellement l’option d’exportation en fonction des besoins.

Pour définir ces options :

1. Démarrez dans Power BI Desktop.

1. Dans le coin supérieur gauche, sélectionnez **Fichier** > **Options et paramètres** > **Options**.

1. Sous **FICHIER ACTUEL**, sélectionnez **Paramètres du rapport**.

    ![paramètres du rapport Desktop](media/power-bi-visualization-export-data/desktop-report-settings.png)

1. Effectuez votre sélection dans la section **Exporter des données**.

Vous pouvez également mettre à jour ce paramètre dans le service Power BI.

Il est important de noter que si les paramètres du portail d’administration Power BI sont en conflit avec les paramètres du rapport des données d’exportation, les paramètres administrateur remplaceront les paramètres des données d’exportation.

## <a name="limitations-and-considerations"></a>Considérations et limitations
Ces limitations et ces considérations s’appliquent à Power BI Desktop et au service Power BI, notamment Power BI Pro et Premium.

- Pour exporter les données à partir d’un visuel, vous devez avoir [Autorisation de création pour le jeu de données sous-jacent](https://docs.microsoft.com/power-bi/service-datasets-build-permissions).

-  Le nombre maximal de lignes que **Power BI Desktop** et le **service Power BI** peuvent exporter depuis un **rapport de mode d’importation** vers un fichier *.csv* est de 30 000.

- Le nombre maximal de lignes que les applications peuvent exporter depuis un **rapport de mode d’importation** au format *.xlsx* est de 150 000.

- L’exportation à l’aide de *Données sous-jacentes* ne fonctionne pas dans les cas suivants :

  - La version est antérieure à 2016.

  - Les tables du modèle n’ont pas de clé unique.
    
  -  Un administrateur ou un concepteur de rapports a désactivé cette fonctionnalité.

- L’exportation à l’aide de *données sous-jacentes* ne fonctionne pas si vous activez l’option *Afficher les éléments sans données* pour la visualisation que Power BI est en train d’exporter.

- Lorsque vous utilisez DirectQuery, la quantité maximale de données que Power BI peut exporter est de 16 Mo de données non compressées. Un résultat inattendu peut être que vous exportez moins que le nombre maximal de lignes. C’est probable dans les cas suivants :

    - Il y a beaucoup de colonnes.

    - Certaines données sont difficiles à compresser.

    - D’autres facteurs jouent un rôle dans l’augmentation de la taille des fichiers et la diminution du nombre de lignes que Power BI peut exporter.

- Si la visualisation utilise les données de plusieurs tables de données et qu’il n’existe aucune relation pour ces tables dans le modèle de données, Power BI exporte uniquement les données de la première table.

- Les visuels personnalisés et les visuels R ne sont actuellement pas pris en charge.

- Dans Power BI, vous pouvez renommer un champ (colonne) en double-cliquant sur le champ et en tapant un nouveau nom. Power BI fait référence au nouveau nom comme à un *alias*. Il est possible qu’un rapport Power BI contienne au final des noms de champs en doublon, mais Excel n’autorise pas les doublons. Ainsi, lorsque Power BI exporte les données vers Excel, les alias de champ reprennent leur nom de champ (colonne) d’origine.  

- Si le fichier  *.csv* contient des caractères Unicode, le texte dans Excel peut ne pas s’afficher correctement. Les symboles monétaires et les mots étrangers sont des exemples de caractères Unicode. Vous pouvez ouvrir le fichier dans le bloc-notes. Unicode s’affiche alors correctement. Si vous souhaitez ouvrir le fichier dans Excel, la solution de contournement consiste à importer le fichier *.csv*. Pour importer le fichier dans Excel :

  1. Ouvrez Excel.

  1. Accédez à l’onglet **Données**.
  
  1. Sélectionnez **Obtenir des données externes** > **À partir du texte**.
  
  1. Accédez au dossier local où le fichier est stocké et sélectionnez le fichier *.csv*.

- Les administrateurs Power BI peuvent désactiver l’exportation des données.

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
