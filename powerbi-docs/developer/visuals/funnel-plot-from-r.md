---
title: Créer un tracé en entonnoir du script R au visuel R
description: Cet article explique comment créer un tracé en entonnoir à partir d’un script R vers un visuel Power BI R.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: tutorial
ms.date: 04/02/2020
ms.openlocfilehash: cbc8f6366e23aa7fbfb447bbfe56909c09f3e3fd
ms.sourcegitcommit: caf60154a092f88617eb177bc34fb784f2365962
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85354475"
---
# <a name="tutorial-build-a-funnel-plot-from-r-script-to-r-visual"></a>Tutoriel : Créer un tracé en entonnoir du script R au visuel R
Cet article explique comment créer étape par étape un tracé en entonnoir en utilisant un script R dans un visuel R.

Dans cet article, vous découvrez comment créer :

> [!div class="checklist"]
>
> * un script R pour RStudio
> * un visuel R dans Power BI
> * un visuel R *basé sur PNG* dans Power BI
> * un visuel R *basé sur HTML* dans Power BI

Le tracé en entonnoir offre un moyen simple de consommer, d’interpréter et de montrer la quantité d’une variation attendue. L’**entonnoir** est formé en utilisant des limites de confiance ; les valeurs hors norme sont montrées sous forme de points à l’extérieur de l’entonnoir.

Dans cet exemple, le tracé en entonnoir est utilisé pour comparer et analyser les différentes ensembles de données.  

> [!NOTE]
> Les fichiers sources peuvent être téléchargés pour chaque ensemble d’étapes.

## <a name="build-an-r-script-with-dataset"></a>Créer un script R avec un jeu de données

1. Téléchargez un [script R minimal](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter1_R/script_R_v1_00.r) et sa table de données, [dataset.csv](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter1_R/dataset.csv).

1. Ensuite, modifiez le script de façon à ce qu’il corresponde à [ce script](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter1_R/script_R_v1_01.r). Ceci ajoute la gestion des erreurs d’entrée et des paramètres utilisateur pour contrôler l’apparence du tracé.

## <a name="build-a-report"></a>Créer un rapport

Ensuite, modifiez le script de façon à ce qu’il corresponde à [ce script](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter2_Rvisual/script_RV_v2_00.r). Ceci charge *dataset.csv* au lieu de *read.csv* dans l’espace de travail de Power BI Desktop et crée une table **Cancer Mortality** (Mortalité par cancer). Regardez les résultats dans le [fichier PBIX](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter2_Rvisual/funnelPlot_Rvisual.pbix) suivant.

> [!NOTE]
> Le `dataset` est un nom codé en dur pour le `data.frame` en entrée de n’importe quel visuel R. 

## <a name="create-an-r-powered-visual-and-package-in-r-code"></a>Créer un visuel R et un package dans du code R

1. Avant de commencer, veillez à [installer les outils PBIVIZ](./custom-visual-develop-tutorial.md#installing-packages).

1. Exécutez la commande suivante pour créer un visuel R :

   ```bash
   pbiviz new funnel-visual -t rvisual
   cd funnel-visual
   npm install 
   pbiviz package
   ```

   Cette commande crée le dossier *funnel-visual* avec un modèle de visuel initial (`-t` pour **template**). PBIVIZ se trouve dans le dossier *dist*, et le code R dans le fichier *script.r*. Essayez de l’importer dans Power BI et voyez ce qui se passe.

1. Modifiez le fichier *script.r* et remplacez le contenu par votre script précédent.

1. Modifiez *capabilities.json* et remplacez la chaîne `Values` par `dataset`. Cela remplace le nom de « Role » dans le modèle pour qu’il soit comme dans le code R.

   ![Avant et après](./samples/funnel-plot/chapter-3/funnel-r-visual-v01/capabilities-changes.PNG)

1. *(facultatif)* Modifiez *dependencies.json* et ajoutez une section pour chaque package R requis par le script R. Ceci indique à Power BI d’importer automatiquement ces packages quand le visuel est chargé pour la première fois.

   ![Avant et après](./samples/funnel-plot/chapter-3/funnel-r-visual-v01/dependencies-changes.PNG)

1. Réempaquetez le visuel avec la commande `pbiviz package` et essayez de l’importer dans Power BI.

> [!NOTE]
> Pour télécharger, consultez [PBIX](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter3-RCustomVisual/funnelPlot_RCustomVisual.pbix) et [code source](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v01/).

## <a name="make-r-based-visual-improvements"></a>Améliorer les visuels basés sur R

Le visuel n’est pas encore convivial, car l’utilisateur doit connaître l’ordre des colonnes dans la table en entrée.

1. Divisez le champ d’entrée `dataset` en trois champs (rôles) : `Population`, `Number` et `Tooltips`

   ![CV01to02](./media/funnel-plot/diagram-one.PNG)

1. Modifiez *capabilities.json* et remplacez le rôle `dataset` par les trois nouveaux rôles, ou téléchargez [capabilities.json](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v02/capabilities.json).

   Vous devez mettre à jour les sections `dataRoles` et `dataViewMappings`, qui définissent les noms, les types, les info-bulles et le nombre maximal de colonnes pour chaque champ d’entrée.

   ![Avant et après](./samples/funnel-plot/chapter-3/funnel-r-visual-v02/capabilities-before-vs-after.png)
   
   Pour plus d’informations, consultez [fonctionnalités](./capabilities.md).

1. Modifiez *script.r* de façon à prendre en charge `Population`, `Number` et `Tooltips` en tant que dataframes en entrée au lieu de `dataset`, ou téléchargez [script.r](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v02/script.r).

   ![script](./samples/funnel-plot/chapter-3/funnel-r-visual-v02/script-r-before-vs-after.png)

   > [!TIP]
   > Pour suivre les modifications apportées au script R, recherchez des blocs de commentaires : 
   > 
   > ```r
   > #RVIZ_IN_PBI_GUIDE:BEGIN: Added to enable visual fields
   > ...
   > #RVIZ_IN_PBI_GUIDE:END: Added to enable visual fields
   > 
   > #RVIZ_IN_PBI_GUIDE:BEGIN: Removed to enable visual fields 
   > ...
   > #RVIZ_IN_PBI_GUIDE:BEGIN: Removed to enable visual fields
   > ```

1. Réempaquetez le visuel avec la commande `pbiviz package` et essayez de l’importer dans Power BI.

> [!NOTE]
> Pour télécharger, consultez [PBIX](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelPlot_RCustomVisual.pbix) et [code source](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v02).

## <a name="add-user-parameters"></a>Ajouter des paramètres utilisateur

1. Ajoutez des fonctionnalités permettant à l’utilisateur de contrôler les couleurs et les tailles des visuels, notamment des paramètres internes de l’interface utilisateur.

   ![CV02to03](./media/funnel-plot/diagram-two.PNG)

1. Modifiez *capabilities.json* et mettez à jour la section `objects`. Nous définissons ici les noms, les info-bulles et les types de chaque paramètre, et nous décidons également la répartition des paramètres dans des groupes (trois groupes dans le cas présent).

   Téléchargez [capabilities.json](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v03/capabilities.json) et consultez [Propriétés des objets](./objects-properties.md) pour plus d’informations

   ![capabilities](./samples/funnel-plot/chapter-3/funnel-r-visual-v03/capabilities-before-after.PNG)

1. Modifiez *src/settings.ts* de façon à ce qu’il corresponde à ce [fichier settings.ts](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v03/src/settings.ts). Ce fichier est écrit en TypeScript.  

   Vous trouverez ici deux blocs du code ajoutés pour :
   - Déclarer une nouvelle interface pour contenir la valeur de la propriété
   - Définir une propriété de membre et des valeurs par défaut

   ![de la source de données](./samples/funnel-plot/chapter-3/funnel-r-visual-v03/settings-ts-before-after.PNG)

1. Modifiez *script.r* de façon à ce qu’il corresponde à ce fichier [script.r](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v03/script.r). Ceci ajoute la prise en charge des paramètres dans l’interface utilisateur en ajoutant des appels `if.exists` pour chaque paramètre utilisateur.

   > [!TIP]
   > Pour suivre les modifications apportées au script R, recherchez des commentaires :
   >
   > ```r
   > #RVIZ_IN_PBI_GUIDE:BEGIN:Added to enable user parameters
   >  ...
   > #RVIZ_IN_PBI_GUIDE:END:Added to enable user parameters
   >
   > #RVIZ_IN_PBI_GUIDE:BEGIN:Removed to enable user parameters 
   >  ...
   > #RVIZ_IN_PBI_GUIDE:END:Removed to enable user parameters
   > ```

   ![Script avant et après](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v03/script_r_before_after_1.png)

   Vous pouvez décider de ne pas exposer les paramètres à l’interface utilisateur, comme nous l’avons fait.  

1. Réempaquetez le visuel avec la commande `pbiviz package` et essayez de l’importer dans Power BI.

> [!NOTE]
> Pour télécharger, consultez [PBIX](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelPlot_RCustomVisual.pbix) et [code source](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v03/).

> [!TIP]
> Nous avons ajouté ici des paramètres de plusieurs types (booléen, numérique, chaîne et couleur), tous en même temps. Pour un cas simple, consultez [cet exemple](https://github.com/Microsoft/PowerBI-visuals/blob/master/RVisualTutorial/PropertiesPane.md) qui montre comment ajouter un seul paramètre. 

## <a name="convert-visual-to-rhtml-based-visual"></a>Convertir un visuel en visuel basé sur RHTML

Étant donné que le visuel obtenu est basé sur le format PNG, il ne répond pas au pointage par la souris, il ne peut pas faire l’objet d’un zoom avant, etc. Nous devons donc le convertir en visuel HTML. Nous allons créer un modèle de visuel HTML basé sur R, puis copier certains scripts à partir du projet PNG.

1. Exécutez la commande suivante :

   ```bash
   pbiviz new funnel-visual-HTML -t rhtml
   cd funnel-visual-HTML
   npm install 
   pbiviz package
   ```

1. Ouvrez *capabilities.json* et prenez notez de la ligne `"scriptOutputType":"html"`.

1. Ouvrez *dependencies.json* et prenez note des noms des packages R listés.

1. Ouvrez *script.r* et prenez note de la structure. Vous pouvez l’ouvrir et l’exécuter dans RStudio, car il n’utilise pas d’entrée externe. 

   Ceci crée et enregistre *out.html*. Ce fichier est autonome (sans dépendances externes) et définit les graphiques à l’intérieur du widget HTML. 

   > [!IMPORTANT]
   > Pour les utilisateurs de `htmlWidgets`, des utilitaires R sont fournis dans le [dossier r_files](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01/r_files) pour faciliter la conversion d’objets `plotly` ou `widget` en HTML autonome. 
   > 
   > Cette version du visuel R prend également en charge la commande `source` (contrairement aux types de visuels précédents) pour rendre votre code plus lisible.   
 
1. Remplacez *capabilities.json* par le fichier *capabilities.json* de l’étape précédente, ou téléchargez [capabilities.json](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01/capabilities.json).

   Veillez à conserver :

   `"scriptOutputType": "html"`

1. Fusionnez la dernière version de *script.r* avec le fichier *script.r* provenant du modèle, ou téléchargez [script.r](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01/script.r).

   Le nouveau script utilise le package `plotly` pour convertir l’objet **ggplot** en objet **plotly**, puis le package `htmlWidgets` pour l’enregistrer dans un fichier HTML. 

   La plupart des fonctions utilitaires sont déplacées vers [_r_files/utils.r_](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01/r_files/utils.r) et la fonction `generateNiceTooltips` est ajoutée pour l’apparence de l’objet **plotly**.

   ![1](./samples/funnel-plot/chapter-4/RHTML-v01/script-before-after-1.PNG)
   
   ![2](./samples/funnel-plot/chapter-4/RHTML-v01/script-before-after-2.PNG)

   > [!TIP]
   > Pour suivre les modifications apportées au script R, recherchez des commentaires :
   > 
   > ```r
   > #RVIZ_IN_PBI_GUIDE:BEGIN:Added to create HTML-based 
   >  ...
   > #RVIZ_IN_PBI_GUIDE:BEGIN:Added to create HTML-based
   >
   > #RVIZ_IN_PBI_GUIDE:BEGIN:Removed to create HTML-based  
   > ...
   > #RVIZ_IN_PBI_GUIDE:BEGIN:Removed to create HTML-based
   > ```

1. Fusionnez la dernière version de *dependencies.json* avec le fichier *dependencies.json* provenant du modèle de façon à y inclure les nouvelles dépendances du package R, ou téléchargez [dependencies.json](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01/dependencies.json).

1. Modifiez *src/settings.ts* de la même façon que dans les étapes précédentes.

1. Réempaquetez le visuel avec la commande `pbiviz package` et essayez de l’importer dans Power BI.

> [!NOTE]
> Pour télécharger, consultez [PBIX et code source](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01).

## <a name="build-additional-examples"></a>Créer d’autres exemples

1. Exécutez la commande suivante pour créer un projet vide : 

   ```bash
   pbiviz new example -t rhtml
   cd example
   npm install 
   pbiviz package
   ```

1. Prenez le code de cette [démonstration](http://www.htmlwidgets.org/showcase_networkD3.html) et faites les modifications en surbrillance :

   ![Modifications en surbrillance](./media/funnel-plot/diagram-three.PNG)

1. Remplacez le fichier *script.r* de votre modèle et réexécutez `pbiviz package`. Le visuel est maintenant inclus dans votre rapport Power BI !

## <a name="tips-and-tricks"></a>Astuces et conseils

* Nous recommandons aux développeurs de modifier *pbiviz.json* pour y stocker les métadonnées correctes, comme **version**, **e-mail**, **nom**, **type de licence**, etc.

   > [!IMPORTANT]
   > Le champ **guid** est l’identificateur unique d’un visuel. Si vous créez un projet pour chaque visuel, le GUID sera également différent. C’est le même seulement quand vous utilisez un ancien projet copié dans un nouveau visuel, ce que vous ne devriez pas faire.

* Modifiez [*assets/icon.png*](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01/assets/icon.png) pour créer des icônes uniques pour votre visuel. 

* Pour déboguer le code R dans RStudio avec les mêmes données que celles de votre rapport Power BI, ajoutez ce qui suit au début du script R-script (modifiez la variable `fileRda`) :

   ```r
   #DEBUG in RStudio
   fileRda = "C:/Users/yourUserName/Temp/tempData.Rda"
   if(file.exists(dirname(fileRda)))
   {
     if(Sys.getenv("RSTUDIO")!="")
       load(file= fileRda)
     else
       save(list = ls(all.names = TRUE), file=fileRda)
   }
   ```

   Ceci enregistre l’environnement d’un rapport Power BI et le charge dans RStudio. 

* Vous n’avez pas besoin de développer des visuels R à partir de zéro grâce au code disponible sur [GitHub](https://github.com/Microsoft?utf8=%E2%9C%93&q=PowerBI&type=&language=R). Vous pouvez sélectionner le visuel à utiliser en tant que modèle, puis copier le code dans un nouveau projet.

   Par exemple, essayez d’utiliser le [visuel personnalisé spline](https://github.com/Microsoft/PowerBI-visuals-spline).

* Chaque visuel R applique l’opérateur `unique` à sa table d’entrée. Pour éviter la suppression des lignes identiques, vous pouvez ajouter un champ d’entrée supplémentaire avec un ID unique et l’ignorer dans le code R.   

* Si vous avez un compte Power BI, utilisez le service Power BI pour développer un visuel [à la volée](/PowerBI-visuals/docs/step-by-step-lab/creating-a-custom-visual/#testing-the-custom-visual) au lieu de le réempaqueter avec la commande `pbiviz package`.

### <a name="html-widgets-gallery"></a>Galerie de widgets HTML
Explorez les visuels dans la [Galerie de widgets HTML](http://gallery.htmlwidgets.org/) que vous pouvez utiliser pour votre prochain visuel. Pour faciliter les choses, nous avons créé un [dépôt de projets de visuels](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/multipleRHTML) avec plus de 20 visuels HTML interactifs !

> [!TIP]
> Pour parcourir les widgets HTML, utilisez **Format** > **Paramètres** > **Type**. Essayez-les avec [ce fichier PBIX](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/multipleRHTML/assets/sample.pbix). 

#### <a name="to-use-a-sample-for-your-visual"></a>Pour utiliser un exemple pour votre visuel

1. Téléchargez l’intégralité du dossier.
1. Modifiez *script.r* et *dependencies.json* de façon à ne conserver qu’un seul widget.
1. Modifiez *capabilities.json* et *settings.ts* pour y supprimer le sélecteur `Type`.
1. Changez `const updateHTMLHead: boolean = true;` en `false` dans *visual.ts*. *(pour de meilleures performances)*
1. Changez les métadonnées dans *pbiviz.json*, en particulier le champ `guid`.
1. Réempaquetez et continuez à personnaliser le visuel comme vous le souhaitez. 

![CV02to03](./media/funnel-plot/diagram-four.PNG)

![CV02to03](./media/funnel-plot/diagram-five.PNG)

> [!NOTE]
> Les widgets de ce projet ne sont pas tous pris en charge par le service.

## <a name="next-steps"></a>Étapes suivantes

Pour découvrir plus d’informations, consultez les tutoriels supplémentaires sur les [Visuels Power BI](./custom-visual-develop-tutorial.md) et les [Visuels R](/power-bi/visuals/service-r-visuals).

Découvrez comment [développer et soumettre des visuels](https://powerbi.microsoft.com/documentation/powerbi-developer-office-store/) au [Store Office (Galerie)](https://store.office.com/appshome.aspx?ui=en-US&rs=en-US&ad=US&clickedfilter=OfficeProductFilter%3aPowerBI&productgroup=PowerBI) ou, pour obtenir d’autres exemples, consultez la [Démonstration de scripts R](https://community.powerbi.com/t5/R-Script-Showcase/bd-p/RVisuals)
