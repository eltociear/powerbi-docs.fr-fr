---
title: Échantillon de suivi COVID-19 pour les gouvernements régionaux et d’État des États-Unis
description: Téléchargez et modifiez l’échantillon de rapport avec les données d’État et régionales des États-Unis pour la pandémie de COVID-19.
author: LukaszPawlowski-MS
ms.reviewer: maggies
ms.custom: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/28/2020
ms.author: lukaszp
LocalizationGroup: Samples
ms.openlocfilehash: 8cdc4a9a78c20c7c4e6986b63a3af61a319df1b6
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82584926"
---
# <a name="covid-19-tracking-sample-for-us-state-and-local-governments"></a>Échantillon de suivi COVID-19 pour les gouvernements régionaux et d’État des États-Unis

L’équipe de Power BI a créé un échantillon de suivi COVID-19 qui permet aux gouvernements régionaux et d’État des États-Unis de publier ou de personnaliser un rapport interactif sur le COVID-19. À l’aide de Power BI Desktop, ils peuvent analyser et visualiser les données sur le COVID-19 pour informer leurs communautés au niveau de la ville, du comté, de l’État et national. Puis, à l’aide de Power BI Publier sur le web, ils peuvent partager le rapport publiquement pour informer les citoyens. L’article offre différentes options pour l’utilisation de visualisations interactives Power BI dans votre propre blog, site web ou récit public.

:::image type="content" source="media/sample-covid-19-us/covid-19-us-tracking-sample.png" alt-text="Échantillon COVID-19 avec données américaines":::

Cet article explique comment effectuer les tâches suivantes :

- Copiez le code incorporé et placez le sur votre propre site. 
- Effectuez des personnalisations telles que la mise en forme d’un état spécifique.
- Publiez sur le service Power BI.
- Publier sur le web. 
- Modifiez ces données avec les données d’une autre source. 

## <a name="prerequisites"></a>Prérequis

Avant de prendre en main Power BI pour raconter votre histoire, vous avez besoin des conditions préalables suivantes :

- Télécharger l’application gratuite [Power BI Desktop](https://powerbi.microsoft.com/desktop/).
- Inscrivez-vous au [service Power BI](https://powerbi.microsoft.com/get-started/).

## <a name="option-1-pre-built-embed-code"></a>Option 1 : Code incorporé pré-intégré

Microsoft a publié l’échantillon de rapport et créé un code incorporé de publication sur le web. Vous pouvez utiliser le code incorporé pour incorporer l’échantillon complet, y compris la vue nationale, et accéder au niveau de l’État et du comté dans votre propre site web. Avant de publier ces données, nous recommandons l’évaluation des [exclusions](#disclaimers) dans cet article.

Pour inclure le graphique interactif sur votre site, copiez et collez le code incorporé suivant dans l’emplacement où vous souhaitez que le graphique apparaisse sur votre page web.  

```
<iframe width="1600" height="900" src="https://app.powerbi.com/view?r=eyJrIjoiMmI2ZjExMzItZTcwNy00YmUwLWFlMTAtYTUxYzVjODZmYjA5IiwidCI6ImMxMzZlZWMwLWZlOTItNDVlMC1iZWFlLTQ2OTg0OTczZTIzMiIsImMiOjF9" frameborder="0" allowFullScreen="true"></iframe>
```

Le code incorporé est un élément HTML iFrame que vous pouvez insérer dans toute page HTML. Ajustez la largeur et la hauteur de l’iFrame fournies pour qu’il s’ajuste à votre site. L’échantillon de rapport est créé dans des proportions 16:9. Sélectionnez donc une taille qui préserve cette dimension. En cas de mise en œuvre correcte, le graphique s’affiche sans les bordures grises supplémentaires. Il est utile d’[évaluer les conseils et astuces de dimensionnement d’iFrame](../service-publish-to-web.md#tips-for-iframe-height-and-width) lors de l’apport de ces modifications.

## <a name="option-2-customize-the-sample-power-bi-file"></a>Option 2 : Personnaliser l’échantillon de fichier de Power BI

Le fichier Power BI contient les données et le graphique interactif dans un format de fichier .pbix que vous pouvez modifier dans Power BI Desktop.  

Une personnalisation classique consiste à filtrer le rapport à un état spécifique, puis à créer votre propre code incorporé de publication sur le web pour votre rapport personnalisé.

Les données USAFacts sont fournies sous la licence Creative Commons qui exige une attribution. Avant de publier ces données, consultez les [exclusions](#disclaimers).

Pour démarrer, [télécharger le fichier .pbix (ici)](https://go.microsoft.com/fwlink/?linkid=2125058).

### <a name="update-your-report"></a>Mettre à jour votre rapport 

1. Téléchargez la version la plus récente de l’application gratuite, [Power BI Desktop](https://powerbi.microsoft.com/desktop/), si vous ne l’avez pas déjà fait. 

2. Téléchargez le [fichier .pbix](https://go.microsoft.com/fwlink/?linkid=2125058) si vous ne l’avez pas déjà fait, et ouvrez-le dans Power BI Desktop.

3. Pour filtrer votre rapport à un état spécifique, sélectionnez la flèche pour développer le volet Filtres.

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-filters-pane.png" alt-text="Développer le volet Filtres":::

4. Sélectionnez un état qui vous intéresse. 

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-filter-selection.png" alt-text="Sélectionner un état":::

5. Sélectionnez **Fichier** > **Enregistrer** pour enregistrer votre fichier. 

### <a name="refresh-your-report"></a>Actualiser votre rapport 

1. Sélectionnez le bouton **Actualiser**.

    :::image type="content" source="media/sample-covid-19-us/power-bi-desktop-refresh-button.png" alt-text="Bouton Actualiser":::

2. Sélectionnez **Anonyme** > **Connecter**. 

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-azure-blob.png" alt-text="Sélectionner Anonyme":::

 
3. Sélectionnez **Ignorer les niveaux de confidentialité**, s’ils sont affichés > **Enregistrer**. 

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-privacy-levels.png" alt-text="Sélectionner les niveaux de confidentialité":::

### <a name="publish-your-report-to-the-power-bi-service"></a>Publier votre rapport dans le service Power BI

Une fois que vous avez personnalisé votre rapport à votre convenance, [suivez les étapes décrites ici pour publier votre rapport](../desktop-upload-desktop-files.md) dans le service Power BI.

### <a name="configure-scheduled-refresh"></a>Configurer une actualisation planifiée

Pour tenir à jour les données du rapport, vous pouvez [configurer l’actualisation planifiée](../refresh-scheduled-refresh.md) après la publication du rapport.

Lorsque vous suivez les étapes, choisissez les options suivantes :

1. Méthode d’authentification des informations d’identification de la source de données : Anonyme
2. Paramètre du niveau de confidentialité pour cette source de données : Public

Pour tester votre paramètre d’actualisation, sélectionnez l’option [Actualiser maintenant](../refresh-data.md#data-refresh) disponible à partir de l’élément de jeu de données.

Les données actualisées sont chargées à chaque exécution de la planification. Les données sous-jacentes sont fournies par USAFacts et peuvent ne pas être mises à jour aussi fréquemment que votre planification d’actualisation. Consultez le [site web USAFacts](https://usafacts.org/visualizations/coronavirus-covid-19-spread-map/) pour savoir quand les données sous-jacentes ont été mises à jour pour la dernière fois. 

Si vous tentez de publier le rapport personnalisé sur votre site web, il est recommandé de configurer votre actualisation planifiée pour qu’elle s’exécute au moins aussi souvent que les mises à jour de données USAFacts. Puisque USAFacts peut actualiser ses données à différents moments de la journée chaque jour, vous pouvez souhaiter configurer plusieurs actualisations chaque jour. 

### <a name="create-a-publish-to-web-embed-code"></a>Créer un code incorporé de publication sur le web 

Pour incorporer votre rapport personnalisé dans votre propre site web, suivez les instructions relatives à la [création de votre propre code incorporé de publication sur le web](../service-publish-to-web.md#create-embed-codes-with-publish-to-web).

Une fois que vous avez publié votre code incorporé, vous utilisez l’iFrame dans la boîte de dialogue de confirmation pour l’incorporer dans votre site web.

Si vous apportez des modifications au rapport dans Power BI Desktop, vous pouvez publier et remplacer le rapport existant dans le service Power BI. Le code incorporé ne change pas. Les modifications du rapport ou des données actualisées mettent environ 1 heure pour s’afficher sur votre site web. 

## <a name="option-3-mash-up-data-from-another-source"></a>Option 3 : Modifier des données à partir d’une autre source 

Vous pouvez également modifier les données de ce rapport avec les données d’une autre source. L’exemple suivant est basé sur les données de [l’Université Johns Hopkins](https://github.com/CSSEGISandData/COVID-19). Avant de publier ces données, nous recommandons l’évaluation des [exclusions](#disclaimers) dans cet article.

1. Sélectionnez **Obtenir des données** > **Web**.

    :::image type="content" source="media/sample-covid-19-us/power-bi-desktop-get-data.png" alt-text="Bouton Obtenir des données":::

2. Entrer l’URL suivante :

    ```
    https://raw.githubusercontent.com/CSSEGISandData/COVID-19/master/csse_covid_19_data/csse_covid_19_time_series/time_series_covid19_confirmed_global.csv
    ```

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-from-web.png" alt-text="Sélectionner les données du web":::

3. Sélectionnez **OK**. 

    > [!NOTE]
    > Le lien publié par l’Université Johns Hopkins peut changer. Pour obtenir les informations les plus récentes, consultez la [page Johns Hopkins GitHub](https://github.com/CSSEGISandData/COVID-19).

4. Sélectionnez **Charger** pour charger le jeu de données pour le nombre total de cas confirmés dans le monde entier.  

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-load-data.png" alt-text="Charger des données du web":::

    Cet article, [Se connecter à des pages web à partir de Power BI Desktop](../desktop-connect-to-web.md), fournit plus d’informations sur le chargement de données à partir du web.
    
Vous pouvez ensuite utiliser Power BI Desktop pour visualiser les données. Finalement, utilisez les étapes dans **Option 2 :** [Publiez votre rapport dans le service Power BI](#publish-your-report-to-the-power-bi-service) pour publier le rapport et créer un code incorporé personnalisé. 

## <a name="option-4-use-the-covid-19-us-tracking-template-app"></a>Option 4 : Utiliser l’application modèle de suivi du COVID-19 aux États-Unis

Une autre option est disponible. L’équipe de Power BI a créé une *application modèle* de suivi du COVID-19 aux États-Unis pour vous aider à démarrer immédiatement. Les applications modèles sont des bundles constitués de rapports, de tableaux de bord et de jeux de données pour une source de données spécifique. Vous pouvez les télécharger à partir d’AppSource, les utiliser ou les modifier en fonction de vos besoins, puis les distribuer à vos collègues. 

Cette application modèle de suivi du COVID-19 aux États-Unis contient un rapport prédéfini de métriques COVID-19. Vous pouvez l’utiliser en l’état, le personnaliser directement dans le service Power BI ou le télécharger pour ajouter d’autres sources de données. Découvrez comment installer l’[application modèle de suivi du COVID-19 aux États-Unis](../connect-data/service-connect-to-covid-19-tracking.md) et comment devenir rapidement opérationnel.

## <a name="about-the-data-source-for-this-report"></a>À propos de la source de données pour ce rapport
Ce rapport interactif agrège les données des centres pour le contrôle et la prévention des maladies (CDC), ainsi que les organismes de santé publique au niveau de l’État et au niveau local. Les données au niveau de la région sont confirmées en référençant les organismes locales et d’État directement (lien).

Les données sont fournies par USAFacts. En raison de la fréquence des mises à jour des données, elles peuvent ne pas refléter les chiffres exacts signalés par les organismes gouvernementaux ou les médias d’information. Pour plus d’informations ou pour télécharger les données, visitez le [site web USAFacts](https://usafacts.org/visualizations/coronavirus-covid-19-spread-map/). 

## <a name="disclaimers"></a>Clauses d’exclusion de responsabilité

Ce rapport et les données sont fournis « en l’état », « avec tous les défauts » et sans aucune garantie. Microsoft n’offre aucune garantie expresse et décline expressément toute garantie implicite, y compris en matière de qualité marchande, d’adéquation à un usage particulier et de non-violation de la loi.

Les données USAFacts sont disponibles sous une licence Creative Commons. Pour l’utiliser, citez USAFacts comme fournisseur de données et liez-le à nouveau à USAFacts. Pour connaître les étapes d’attribution exactes, consultez la section **#MadewithUSAFacts** de la page USAFacts, [Coronavirus aux États-Unis : Mappage de l’apparition du COVID-19 dans les États et les régions](https://usafacts.org/visualizations/coronavirus-covid-19-spread-map/).

Les données de l’Université Johns Hopkins sont un copyright de l’Université Johns Hopkins 2020, tous droits réservés. Elles sont fournies au public exclusivement à des fins de recherche éducative et universitaire. Voici l’intégralité des [Conditions d’utilisation](https://github.com/CSSEGISandData/COVID-19/blob/master/README.md) des données présentées dans l’exemple de mashup. Des informations supplémentaires sont disponibles sur le [site web de l’Université Johns Hopkins](https://coronavirus.jhu.edu/map-faq.html).

## <a name="next-steps"></a>Étapes suivantes

[Obtenir des échantillons pour Power BI](../sample-datasets.md)